# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Create a singly linked list by inserting nodes containing integer values.
2. Read the value val that needs to be removed from the list.
3. Skip all matching nodes at the beginning and update the head to the first non-matching node.
4. Traverse the list; whenever current.next.data == val, bypass that node by linking current.next = current.next.next.
5. Return and display the updated head of the modified linked list.

## Program:
```
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: VAISHNAVIDEVI V
RegisterNumber:  212223040230
```
```

public class RemoveNodesFromList {

    // Node class
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    Node head;

    // Insert at end
    public void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) {
            temp = temp.next;
        }
        temp.next = newNode;
    }

    // Remove nodes equal to val
    public void removeValue(int val) {
        // Remove matching nodes at head
        while (head != null && head.data == val) {
            head = head.next;
        }

        Node temp = head;
        // If list becomes empty after removals
        if (temp == null) return;

        // Remove matching nodes in remaining list
        while (temp.next != null) {
            if (temp.next.data == val) {
                temp.next = temp.next.next;
            } else {
                temp = temp.next;
            }
        }
    }

    // Display list
    public void display() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    // Main
    public static void main(String[] args) {
        RemoveNodesFromList list = new RemoveNodesFromList();

        list.insert(10);
        list.insert(20);
        list.insert(20);
        list.insert(30);
        list.insert(20);
        list.insert(40);

        int val = 20;

        System.out.println("Original List:");
        list.display();

        list.removeValue(val);

        System.out.println("List After Removing " + val + ":");
        list.display();
    }
}


```

## Output:

<img width="1919" height="622" alt="image" src="https://github.com/user-attachments/assets/750c4093-fdd2-431e-861b-c89df0f29a7f" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
