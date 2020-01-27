# Binary Tree Inorder Traversal 🌲
## https://leetcode.com/problems/binary-tree-inorder-traversal
Given a binary tree, return the inorder traversal of its nodes' values.

```
Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```
**Follow up: Recursive solution is trivial, could you do it iteratively?**

# Inorder Traversal :
![Binary Tree](binary-tree.PNG?raw=true "Binary Tree")

Note that node 75 doesn't have left child and node 29 doesn't have right child.

The inorder traversal for above binary tree will be **[21, 35, 20, 67, 75, 30, 70, 50, 29, 43, 60, 24, 65]**

## Implementation : Recursive

```java
import java.util.ArrayList;
import java.util.List;

public class App {

	public static void main(String[] args) {
		TreeNode root = new TreeNode(70);
		root.left = new TreeNode(67); root.right = new TreeNode(43);
		
		root.left.left = new TreeNode(35); root.left.right = new TreeNode(75); 
		
		root.left.left.left = new TreeNode(21); root.left.left.right = new TreeNode(20);
		
		root.left.right.right = new TreeNode(30);
		
		root.right.left = new TreeNode(29); root.right.left.left = new TreeNode(50);
		
		root.right.right = new TreeNode(24); 
		
		root.right.right.left = new TreeNode(60); root.right.right.right = new TreeNode(65);
		System.out.println(inorderTraversal(root));
	}
	
	
	// Definition for a binary tree node.
	static public class TreeNode {
	      int val;
	      TreeNode left;
	      TreeNode right;
	      TreeNode(int x) { val = x; }
	}
	 
	
	public static List <Integer> inorderTraversal(TreeNode root) {
            List <Integer> res = new ArrayList<Integer>();
            helper(root, res);
            return res;
        }

       public static void helper(TreeNode root, List <Integer> res) {
	    if (root != null) {
		  helper(root.left, res);
		  res.add(root.val);
		  helper(root.right, res);
	      }
       }
}

```
## Implementation : Iterative

```java
public List <Integer> inorderTraversal(TreeNode root) {
      List <Integer> res = new ArrayList<Integer>();
      Stack<TreeNode> stack = new Stack();
      TreeNode curr = root;

      // if current node is null and stack is also empty, we're done
      while (!stack.empty() || curr != null) {
          // if current node is not null, push it to the stack (defer it)and move to its left child
            if (curr != null) {
                stack.push(curr);
                curr = curr.left;
            } else {
                // else if current node is null, we pop an element from stack,
                // print it and finally set current node to its right child
                curr = stack.pop();
                res.add(curr.val);
                curr = curr.right;
            }
      }
  return res;
}
```

# References :
1. https://leetcode.com/problems/binary-tree-inorder-traversal/solution
2. https://www.youtube.com/watch?v=50v1sJkjxoc (Iterative Approach using Stack)

