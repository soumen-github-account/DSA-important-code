# LinkedList all functions

```java
import java.util.*;

public class Main {

public static class ll{
    public int size;
    public int count;
    public class Node{
        int data;
        Node next;
        Node(int data){
            this.data = data;
            this.next = null;
        }
    }
    
    ll(int size){
        this.size = size;
        this.count = -1;
    }
    
    public Node head;
    
    public boolean isFull(){
        return count == size-1;
    }
    
    public boolean isEmpty(){
        return count == -1;
    }
    
    public void insertInFirst(int data){
        Node newNode = new Node(data);
        
        if(isFull()){
            System.out.print("Full...");
            return;
        }
        
        if(head == null){
            head = newNode;
            count++;
            return;
        }
        newNode.next = head;
        head = newNode;
        count++;
    }
    
    public void insertAtEnd(int data){
        Node newNode = new Node(data);
        Node temp = head;
        while(temp.next != null){
            temp = temp.next;
        }
        temp.next = newNode;
    }
    
    public void insertAtIndex(int data, int index){
        Node newNode = new Node(data);
        int c = 0;
        Node temp = head;
        while(c < index-1){
            temp = temp.next;
            c++;
        }
        Node n = temp.next;
        temp.next = newNode;
        newNode.next = n;
    }
    
    public void deleteFromFirst(){
        if(head == null){
            System.out.println("List is EMPTY...");
            return;
        }
        head = head.next;
        count--;
    }
    
    public void deleteFromLast() {
        if (isEmpty()) {
            System.out.println("List is EMPTY...");
            return;
        }
        
        if (head.next == null) {
            head = null;
            count--;
            return;
        }
        
        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }
    
        temp.next = null; 
        count--;
    }

    
    public void display(){
        if(head == null){
            System.out.print("Empty...");
            return;
        }
        Node temp = head;
        while(temp != null){
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("Null");
    }
}

    public static void main(String args[]) {
        ll l = new ll(6);
        l.insertInFirst(2);
        l.insertInFirst(8);
        l.insertAtEnd(6);
        l.insertAtEnd(4);
        l.insertAtEnd(9);
        l.insertAtIndex(7, 3);
        l.display();
        l.deleteFromFirst();
        l.deleteFromLast();
        l.display();
    }
}
```
