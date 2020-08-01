# Utils

## LinkedList

```java
LinkedList<Integer> list = new LinkedList<>();

// add
list.add(el)
list.add(idx, el)
list.addFirst(el)
list.addLast(el)

// get
list.get(idx)
list.getFirst()
list.getLast()
```

## Stack

```java
Stack<Integer> st = new Stack<>();

// add
st.push(el)

// pop
st.pop()

// top
st.peek()

// empty
st.empty()
```

## Queue

```java
Queue<Integer> q = new LinkedList<>();

// add
list.add(el)
list.offer(el)

// get head
list.peek()

// remove head
list.poll()
```

## Heap

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);

// add
heap.offer(el)
heap.add(el)

// remove el
heap.remove(el)

// remove head
heap.poll()

// get head
heap.peek()
```

## String

```java
String s = "";
String s = new String(char[]);

// get by idx
s.charAt(idx)

// to char array
s.toCharArray()

// lowercase
s.toLowerCase()

// uppercase
s.toUpperCase()

// replace
s.replace(regex, newVal)
```

## StringBuilder

```java
StringBuilder sb = new StringBuilder();

// append
sb.append(str);

// update
sb.setCharAt(idx, ch)

// insert
sb.insert(offset, str)
```

## Arrays

```java
// sort
Arrays.sort(el[]);

// fill
Arrays.fill(el[], val);
```

## Collections

```java
Collections.sort(list) // asc
Collections.sort(list, (a, b) -> b - a); // desc
```

# DSA (easy)

## Array

* Rotate image

```java
/*
x1 x2 x3
x4 x5 x6
x7 x8 x9

x3 = x1
x9 = x3
x7 = x9
x1 = x7 
*/
```

## Linked List

* Delete given node in O(1)

```java
public void deleteNode(Node node) {
  node.val = node.next.val;
  node.next = node.next.next;
}
```

* Remove nth node from end

```java
public ListNode removeNthFromEnd(ListNode head, int n) {
    int count = 1;
    ListNode high = head.next, low = head;
    while (count < n + 1 && high != null) {
        high = high.next;
        count++;
    }
    
    if (count < n + 1) {
        return head.next;
    }
    
    while (high != null) {
        low = low.next;
        high = high.next;
    }
    
    low.next = low.next.next;
    return head;
}
```

* Reverse list

```java
public ListNode reverseList(ListNode head) {
    ListNode t = null, next, p = head;
    while (p != null) {
        next = p.next;
        p.next = t;
        t = p;
        p = next;
    }
    return t;
}
```

* Detect cycle

```java
public boolean hasCycle(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (fast == slow)
            break;
    }
    
    return fast != null && fast.next != null && fast == slow;
}
```

## Tree

* Validate BST

```java
/*
Idea: a node valid when node.val >= maxLeft.val && node.val <= minRight.val
*/
public Result check(TreeNode root) {
    Result rs = new Result();
    if (root == null) {
        rs.isValid = true;
        return rs;   
    }
    
    Result leftRs = check(root.left);
    if (!leftRs.isValid || leftRs.max >= root.val) {
        rs.isValid = false;
        return rs;
    }
    
    Result rightRs = check(root.right);
    if (!rightRs.isValid || rightRs.min <= root.val) {
        rs.isValid = false;
        return rs;
    }
    
    rs.isValid = true;
    rs.min = Math.min(Math.min(leftRs.min, rightRs.min), root.val);
    rs.max = Math.max(Math.max(leftRs.max, rightRs.max), root.val);
    return rs;
}
```

* Symmetric tree

```java
/*
Idea: parallel preorder(left) and preorder(right)
*/

public boolean check(TreeNode left, TreeNode right) {
    if (left == null && right == null) {
        return true;
    }
    if (left == null || right == null) {
        return false;
    }
    if (left.val != right.val) {
        return false;
    }
    return check(left.left, right.right) && check(left.right, right.left);
}
```

* Level order traversal

```java
/*
Idea: preorder traversal with level info -> map.put(level, node.val)
*/

public void solve(TreeNode root, int level, Map<Integer, List<Integer>> itemsMap) {
    if (root == null)
        return;
    List<Integer> items = itemsMap.get(level);
    if (items == null) {
        items = new ArrayList<>();
        itemsMap.put(level, items);
    }
    items.add(root.val);
    solve(root.left, level + 1, itemsMap);
    solve(root.right, level + 1, itemsMap);
}
```

* Convert sorted array to BST

```java
/*
Idea: preorder with l, r (l <= r) and assign node.val = array[floor((l+r)/2)]
*/

public TreeNode buildTree(int[] nums, int l, int r) {
    if (nums.length == 0 || l > r) {
        return null;
    }
    
    int m = l + (r - l) / 2;
    TreeNode node = new TreeNode(nums[m]);
    node.left = buildTree(nums, l, m - 1);
    node.right = buildTree(nums, m + 1, r);
    return node;
}
```

## Sorting and Searching

* Get middle without overflow

```java
int m = l + (r - l) / 2;
```

## Dynamic programing

* Climbing stairs

```java
steps[i] = steps[i - 1] + steps[i - 2];
```

* Max profit

```java
if (price < minPrice)
  minPrice = price;
else
  maxProfit = Math.max(maxProfit, price - minPrice);
```

* Max subarray sum

```java
sum = Math.max(a[i], sum + a[i])
ret = Math.max(ret, sum);
```

* House robber

```java
/*
lo = val offset 2
hi = max(hi, lo + nums[i])
*/
```

## Design

* Min stack

```java
/*
store val and min of [pos, bottom]
stack.push([val, min(head.min, val)])
*/
```

* Primes table

```java
/*
start from i = 2, flags all multiple of i = false
check flags[i] == true -> prime 
*/

boolean[] isPrime = new boolean[n + 1];
isPrime[0] = false;

for (int i = 2; i*i < n; i++) {
  if (isPrime[i]) {
    for (int j = i; i*j < n; j++) {
      isPrime[i*j] = false;
    }
  }
}
```

* Roman number

```java
/*
start from tail -> head if a[i] < a[i + 1] ? ret -= a[i] : ret += a[i]
*/
```

## Bitwise

```java
(num & (1 << idx)) >>> idx // get bit at idx

// swap
x = x ^ y
y = y ^ x
x = x ^ y
```

* reverse bits

```java
int ret = 0;
int mask = 1 << 31;
for (int i = 0; i < 32; i++) {
  ret |= ((n & mask) != 0 ? 1 : 0) << i;
  mask >>>= 1;
}
return ret;
```

## Others

* Pascal triangle

```java
if (j == 0 || j == i)
  row[i][j] = 1;
else
  row[i][j] = row[i - 1][j - 1] + row[i - 1][j];
```

* Valid parentheses

```java
if (ch == '(')
  st.push(ch)
else 
  if (ch.empty())
    return false;
  else
    ch.pop(); 
```

# DSA (medium)

## Array

* two sum

```java
Arrays.sort(arr);
while (l < r)
  sum = arr[l] + arr[r]
  if (sum == x)
    return [l, r]
  else if (sum < x)
    l++;
  else
    r--;
```

* anagram

```java
map.put(sort(anagram), list(anagram))
```

* longest substring without repeating

```java
for (int i = 0; i < s.length(); i++) {
  char c = s.charAt(i);
  int pos = map.getOrDefault(c, -1);
  if (c != -1) {
    map.remove(c);
    from = Math.max(from, pos + 1);
  }

  map.put(c, i);
  ret = Math.max(ret, i - from + 1);
}
```

* longest palindromic substring

```java
/*
char[i] == char[j] && (i - 1 == j || dp[j + 1][i - 1])
*/
```

* increasing triplet subsequence

```java
min1 = MAX_INT, min2 = MAX_INT;
for (num : nums) {
  if (num > min2)
    return true;
  if (num < min2 && num > min1)
    min2 = num;
  else if (num < min1)
    min1 = num;
}
return false;
```

# Linked List

* intersection of two linked list

```java

while (pa != null && pb != null && pa != pb)
  pa = headA -> null -> lastA = pa, pa = headB
  pb = headB -> null -> lastB = pb, pb = headA

  if (lastB != lastA)
    return null;

return pa;
```

# Tree and graphs

* contruct a binary tree from preorder and inorder

```java
idxMap = map(val: idx) of inorder
i = 0; // global

buildTree(l, r)
  if (l > r)
    return null;
  m = idxMap.get(preorder[i]);
  node.val = preorder[i++];
  node.left = buildTree(l, m - 1);
  node.right = buildTree(m + 1, r);
  return node;
```

* contruct a binary tree from postorder and inorder

```java
idxMap = map(val: idx) of inorder
i = n - 1; // global

buildTree(l, r)
  if (l > r)
    return null;
  m = idxMap.get(postorder[i]);
  node.val = postorder[i--];
  node.right = buildTree(m + 1, r);
  node.left = buildTree(l, m - 1);
  return node;
```

* contruct a binary tree from preorder and postorder

```java
idXMap = map(val: idx) of postorder
i = 0; // global

buildTree(l, r)
  if (l > r)
    return null;
  node.val = preorder[i++];
  m = idxMap.get(preorder[i])
  node.left = buildTree(l, m);
  node.right = buildTree(m + 1, r - 1)
```

## Backtracking

* Generate parentheses

```java

private List<String> ret;
private int max;

public void generate(String state, int open, int close) {
  if (state.length() == max * 2) {
    ret.add(state);
    return;
  }

  if (open < max)
    generate(state + "(", open + 1, close);
  if (close < open)
    generate(state + ")", open, close + 1);
}
```

* Permutations

```java

private List<List<Integer>> ret;
private int[] nums;
private boolean[] used;

public void generate(List<Integer> per, int k) {
  if (k == nums.length) {
    ret.add(new ArrayList<>(per));
  }

  for (int i = 0; i < nums.length; i++) {
    if (!used[i]) {
      used[i] = true;
      per.set(k, nums[i]);
      generate(per, k + 1);
      used[i] = false;
    }
  }
}
```

* Subsets

```java
/*
Solution 1: use bit from 1 -> n
Solution 2: backtracking
*/

// Solution 1
int n = nums.length;
int m = 1 << n;
List<List<Integer>> ret = new ArrayList<>();
for (int i = 0; i < m; i++) {
  int mask = 1;
  List<Integer> subset = new ArrayList<>();
  for (int j = 0; j < n; j++) {
    if (i & mask != 0) {
      subset.add(nums[n - 1 - j]);
    }
    mask <<= 1;
  }
}

// Solution 2
private List<List<Integer>> ret;
private int[] nums;
private boolean[] used;

public void generate(Lits<Integer> subset, int i) {
  for (int j = i; j < nums.length; j++) {
    List<Integer> subset_ = new ArrayList<>(subset);
    subset_.add(nums[j]);
    ret.add(subset_);
    used[j] = true;
    generate(subset_, i + 1);
    used[j] = false;
  }
}
```

## Sorting and Searching

* Kth largest element in an array

```java
/*
store a min heap of max elements
*/

PriorityQueue<Integer> minHeap = new PriorityQueue<>();
for (int i = 0; i < nums.length; i++) {
  if (minHeap.size() < k) {
    minHeap.add(nums[i]);
  } else if (nums[i] > minHeap.peek()) {
    minHeap.remove();
    minHeap.add(nums[i]);
  }
}
return minHeap.peek();
```

* Search a 2D matrix 

```java
int n = matrix.length;
int m = matrix[0].length;
int i = 0;
int j = n - 1;

while (i < n && j >= 0) {
  if (matrix[i][j] == target)
    return true;
  else if (matrix[i][j] > target)
    j--;
  else
    i++;
}

return false;
```

## Dynamic programing

* Unique paths

```java
int[][] dp = new int[m][n];
dp[0][0] = 1;

for (int i = 0; i < m; i++) {
  for (int j = 0; j < n; j++) {
    if (i - 1 >= 0) {
      dp[i][j] = Math.max(dp[i][j], dp[i - 1][j] + 1);
    }

    if (j - 1 >= 0) {
      dp[i][j] = Math.max(dp[i][j], dp[i][j - 1] + 1);
    }
  }
}

return dp[m - 1][n - 1];
```

* Coin change 1: given an array, and amount find the minimum number of coins to make up that amount

```java
int[] dp = new int[amount + 1];
dp[0] = 0;

for (int i = 1; i <= amount; i++) {
  dp[i] = -1;
  for (int j = 0; j < coins.length; j++) {
    if (coins[j] <= amount && dp[i - coins[j]] != -1) {
      dp[i] = Math.min(dp[i], dp[i - coins[j]] + 1);
    }
  }
}

return dp[amount];
```

* Coin change 2: given an array, and amount find all the way to make up that amount

```java
int[][] dp = new int[coins.length + 1][amount + 1];
dp[0][0] = 1;

for (int i = 1; i <= coins.length; i++) {
  int coin = coins[i - 1];
  for (int j = 0; j <= amount; j++) {
    dp[i][j] = dp[i - 1][j];
    if (j - coin >= 0) {
      dp[i][j] += dp[i][j - coin];
    }
  }
}

return dp[coins.length][amount];
```

* Longest increasing subsequence

```java
int[] dp = new int[nums.length];
int max = 0;

for (int i = 0; i < nums.length; i++) {
  dp[i] = 1;
  for (int j = 0; j < i; j++) {
    if (nums[j] < nums[i]) {
      dp[i] = Math.max(dp[i], dp[j] + 1);
      max = Math.max(max, dp[i]);
    }
  }
}

return max;
```

## Math

* Factorial Trailing zeroes

```java
public int countTrailingZeroes(long n) {
  int count = 0;
  for (long i = 5; n / i >= 1; i *= 5) {
    count += n / i;
  }
  return count;
}
```

* Excel sheet column number

```java
int ret = 0, offset = 1;
char[] chars = s.toCharArray();
for (int i = chars.length - 1; i >= 0; i--) {
  ret += (chars[i] - 'A' + 1) * offset;
  offset *= 26;
}
return ret;
```

* Pow(x, n)

```java
private double calcPow(double x, int n) {
  if (n == 0)
    return 1;
  int t = calcPow(x, n / 2);
  return t * t * (x % 2 == 1 ? x : 1);
}

public double pow(double x, int n) {
  if (n < 0) {
    x = 1 / x;
  }
  return calcPow(x, n);
}
```

* Sqrt(x)

```java
public int sqrt(int x) {
  long l = 0, r = (x / 2) + 1;
  int ret = 0;
  while (l <= r) {
    int m = l + (r - l) / 2;
    if (m*m > x) {
      r = m - 1;
    } else {
      ret = (int)m;
      l = m + 1;
    }
  }
  return ret;
}
```

## Others

* Evaluate Reverse Polish Notation

```java
/*
if number -> stack.push(number), else stack.push(2th peek op 1th peek)
*/
```

# DSA (hard)

## Array

* Spiral matrix

```java

l1 = 0, r1 = n - 1;
l2 = 0, r2 = m - 1;

while l1 <= r1 && l2 <= r2:
  found = false
  for i = l2 -> r2:
    ret.add(matrix[l1][i])
    found = true
  
  if found:
    for i = l1 + 1 -> r1
      ret.add(matrix[i][r2])
      found = true
  
  if found:
    for i = r2 - 1 -> l2
      ret.add(matrix[r1][i])
      found = true
  
  if found:
    for i = r1 - 1 -> l1 + 1
      ret.add(matrix[i][l2])
      found = true

  l1++; r1--; l2++; r2--;
```

* Container with most water

```java
public int maxArea(int[] heights) {
  int l = 0, r = heights.length - 1;
  int ret = 0;
  while (l < r) {
    ret = Math.max(ret, Math.max(heights[l], heights[r]) * (r - l));
    if (heights[l] < heights[r]) {
      l++;
    } else {
      r--;
    }
  }
  return ret;
}
```

* Find duplicate number

```java
int slow, fast;
slow = fast = nums[0];
do {
  slow = nums[slow];
  fast = nums[nums[fast]];
} while (slow != fast);

// find entrance
slow = nums[0];
while (slow != fast) {
  slow = nums[slow];
  fast = nums[fast];
}

return slow;
```

## Tree and graphs

* Lowest common ancestor

```java
private TreeNode ret;

public boolean lca(TreeNode root, TreeNode a, TreeNode b) {
  if (root == null)
    return false;

  boolean foundCurrent = root == a || root == b;
  boolean foundLeft = lca(root.left, a, b);
  boolean foundRight = lca(root.right, a, b);

  if ((foundCurrent && (foundLeft || foundRight)) || (foundLeft && foundRight)) {
    ret = root;
  }

  return foundCurrent || foundLeft || foundRight;
}
```

* Max path sum

```java
private int ret = Integer.MIN_VALUE;

public int maxPathSum(TreeNode root) {
  if (root == null)
    return 0;

  int leftSum = maxPathSum(root.left);
  int rightSum = maxPathSum(root.right);

  int max = root.val;
  max = Math.max(max, leftSum);
  max = Math.max(max, rightSum);

  ret = Math.max(ret, max);
  ret = Math.max(ret, root.val + leftSum + rightSum);

  return max;
}
```

* Detect cycle of matrix

```java
public boolean dfs(Edge[] edges, int u) {
  if (flags[u] == VISITED)
    return true;
  else if (flags[u] == DELETED)
    return false;
  
  flags[u] = VISITED;
  for (Edge edge : edges) {
    if (edge.src == u) {
      if (dfs(egdes, edge.dest)) {
        return true;
      }
    }
  }
  flags[u] = DELETED;
  return false;
}
```