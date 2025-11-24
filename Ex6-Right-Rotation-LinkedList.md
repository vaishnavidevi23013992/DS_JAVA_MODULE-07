# Ex6 Right Rotation LinkedList
## DATE:
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1. Create the singly linked list by inserting nodes one by one.
2. Count the total number of nodes (length) and connect the last node to the head to form a circular list.
3. Reduce rotations using k = k % length to avoid extra rotations.
4. Traverse to the (length - k)th node and mark it as the new tail.
5. Set newHead = newTail.next, break the circular link, and display the rotated linked list.  

## Program:
```

Program to  Right Rotation LinkedList
Developed by: VAISHNAVIDEVI V
RegisterNumber: 212223040230

```
```
import java.util.Scanner;
class RotateLinkedList {
    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
    public static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0) 
            return head;

        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }
        temp.next = head;
        k = k % length;
        int skip = length - k;

        Node newTail = head;
        for (int i = 1; i < skip; i++) {
            newTail = newTail.next;
        }

        Node newHead = newTail.next;
        newTail.next = null; 

        return newHead;
    }
    public static void display(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        Node head = null;
        Node tail = null;

        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            int val = sc.nextInt();
            Node newNode = new Node(val);

            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

        System.out.print("Enter k (rotate by k positions): ");
        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.println("Rotated Linked List:");
        display(head);

        sc.close();
    }
}

```

## Output:
<img width="454" height="181" alt="image" src="https://github.com/user-attachments/assets/f3f592c8-eed9-494e-9cd4-355915e355ea" />



## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.
