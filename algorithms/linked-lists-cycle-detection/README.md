# [Linked Lists: Detect a Cycle (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem) 

## Challenge Text

A linked list is said to contain a cycle if any node is visited more than once while traversing the list.

Complete the function provided in the editor below. It has one parameter: a pointer to a Node object named  that points to the head of a linked list. Your function must return a boolean denoting whether or not there is a cycle in the list. If there is a cycle, return true; otherwise, return false.

## Solution

```java
/*
Detect a cycle in a linked list. Note that the head pointer may be 'null' if the list is empty.

A Node is defined as: 
    class Node {
        int data;
        Node next;
    }
*/

boolean hasCycle(Node head) {

    if (head == null) {

        return false;
        
    }
    ArrayList hasSeen = new ArrayList();
    Node next = head.next;
    
    while (next != null) {
        
        int code = next.hashCode();
        if (hasSeen.indexOf(code) > -1) {
            
            return true;
            
        }
        hasSeen.add(code);
        next = next.next;
        
    }
    
    return false;    
    
}

```

