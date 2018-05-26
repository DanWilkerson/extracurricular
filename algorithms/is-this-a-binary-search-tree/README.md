# [Trees: Is This a Binary Search Tree? (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-is-binary-search-tree/problem) 

## Challenge Text
For the purposes of this challenge, we define a binary search tree to be a binary tree with the following ordering properties:

The  value of every node in a node's left subtree is less than the data value of that node.
The  value of every node in a node's right subtree is greater than the data value of that node.
Given the root node of a binary tree, can you determine if it's also a binary search tree?

Complete the function in your editor below, which has  parameter: a pointer to the root of a binary tree. It must return a boolean denoting whether or not the binary tree is a binary search tree. You may have to write one or more helper functions to complete this challenge.

## Solution

```java
/* Hidden stub code will pass a root argument to the function below. Complete the function to solve the challenge. Hint: you may want to write one or more helper functions.  

The Node class is defined as follows:
    class Node {
        int data;
        Node left;
        Node right;
     }
*/
    class StoredNode {
        
        public Node node;
        public int max;
        public int min;
        
        // constructor
        public StoredNode(Node node, int max, int min) {
            
            this.node = node;
            this.max = max;
            this.min = min;
            
        }
        
    }
    
    boolean checkBST(Node root) {
        
        Deque<StoredNode> stack = new ArrayDeque<>();
        List<Integer> exists = new ArrayList<Integer>();
        Node curr = null;
        int max = 10001;
        int min = -1;
        StoredNode stored = new StoredNode(root, max, min);
        
        stack.add(stored);
        
        while(stack.size() > 0) {
            
            if (curr == null) {
                
                stored = stack.pop();
                curr = stored.node;
                max = stored.max;
                min = stored.min;
                
            }
            
            if (exists.indexOf(curr.data) > -1) {

                return false;

            }

            exists.add(curr.data);

            if (!checkNode(curr, max, min)) {
                
                return false;
                
            }
            
                        
            if (curr.right != null) {
                
                stack.add(new StoredNode(curr.right, max, curr.data));
                
            }
            
            if (curr.left != null) {
                
                max = curr.data;
                curr = curr.left;
                
            } else {
                
                stored = stack.pop();
                curr = stored.node;
                max = stored.max;
                min = stored.min;
                
            }
            
        }
        
        return true;
        
    }
/*
 Check the node's children 
*/
    boolean checkNode(Node node, int max, int min) {

        if (node.left != null) {
            
            if (node.left.data > node.data) {

                return false;
                
            }
            
            if (node.left.data > max) {
                
                return false;
                
            }
            
            if (node.left.data < min) {

                return false;
              
            }

        }

        if (node.right != null) {
            
            if (node.right.data < node.data) {

                return false;
                
            }
            
            if (node.right.data > max) {
                
                return false;
                
            }
            
            if (node.right.data < min) {
                
                return false;
                
            }

            
        }
        
        return true;
        
    }

```

