# DSA-important-code

## Stack using array

```java
public class Main
{
    private int stack[];
    private int top;
    
    public Main(int size){
        stack = new int[size];
        top = -1;
    }
    
    public void push(int data){
        if(top == stack.length-1){
            System.out.print("Stack overflow...");
            return;
        }
        stack[++top] = data;
    }
    
    public int pop(){
        if(top == -1){
            System.out.println("Stack is empty...");
            return -1;
        }
        return stack[top--];
    }
    
    public int peek(){
        if(top == -1){
            System.out.println("Stack is empty...");
            return -1;
        }
        return stack[top];
    }
    
    public void display() {
        if (top == -1) {
            System.out.println("Stack is empty...");
            return;
        }
        
        for (int i = top; i >= 0; i--) { 
            System.out.print(stack[i] + " ");
        }
        System.out.println();
    }
    
	public static void main(String[] args) {
	    int n;
	    Scanner sc = new Scanner(System.in);
	    System.out.print("Enter a size of stack : ");
	    n = sc.nextInt();
	    int data;
		Main s = new Main(n);
		for(int i=0; i<n; i++){
		    System.out.print("Enter "+ (i+1) + "data : ");
		    data = sc.nextInt();
		    s.push(data);
		}

        s.display();

        System.out.println("Popped: " + s.pop());

        s.display();
	}
}
```

## Stack using LinkedList

```java
public class Main{
    
    static class Node{
        int data;
        Node next;
        
        Node(int data){
            this.data = data;
            this.next = null;
        }
    }
    
    static class stack{
        public static Node head;
        
        public static boolean isEmpty(){
            return head == null;
        }
        
        public static void push(int data){
            Node newNode = new Node(data);
            if(isEmpty()){
                head = newNode;
                return;
            }
            newNode.next = head;
            head = newNode;
        }
        
        public static int pop(){
            if(isEmpty()){
                System.out.print("Stack is empty....");
                return -1;
            }
            int top = head.data;
            head = head.next;
            return top;
        }
        
        public static int peek(){
            if(isEmpty()){
                return -1;
            }
            return head.data;
        }
        
        public static void display(){
            if (isEmpty()) {
                System.out.println("Stack is empty....");
                return;
            }

            Node temp = head;
            System.out.print("Stack: ");
            while (temp != null) {
                System.out.print(temp.data + " ");
                temp = temp.next;
            }
            System.out.println();
        }
    }
    
    
    public static void main(String args[]){
        stack.push(10);
        stack.push(20);
        stack.push(30);

        stack.display();   // Output: Stack: 30 20 10

        System.out.println("Peek: " + stack.peek());  // 30

        System.out.println("Pop: " + stack.pop());    // 30

        stack.display();   // Output: Stack: 20 10
    }
}
```
## Queue using array

```java
public class Main{
    
    static class Queue{
        static int arr[];
        static int size;
        static int rear = -1;
        Queue(int size){
            arr = new int[size];
            this.size = size;
        }
        
        public static boolean isEmpty(){
            return rear == -1;
        }
        
        public static void add(int data){
            if(rear == size-1){
                System.out.println("Full....");
                return;
            }
            rear++;
            arr[rear] = data;
        }
        
        public static int remove(){
            if(isEmpty()){
                System.out.print("Empty queue...");
                return -1;
            }
            int front = arr[0];
            for(int i=0; i<rear; i++){
                arr[i] = arr[i+1];
            }
            rear--;
            return front;
        }
        
        public static int peek(){
            if(isEmpty()){
                System.out.print("Empty queue...");
                return -1;
            }
            return arr[0];
        }
        
        public static void display(){
            if(isEmpty()){
                System.out.print("Empty queue...");
                return;
            }
            for(int i=0; i<=rear; i++){
                System.out.print(arr[i] + " ");
            }
            System.out.println();
        }
    }
    
    public static void main(String args[]){
        Queue q = new Queue(5);
        q.add(2);
        q.add(3);
        q.add(4);
        q.add(6);
        q.add(9);
        q.add(4);
        q.display();
        int p = q.peek();
        System.out.println("peek -> "+p);
        int r = q.remove();
        q.display();
    }
}

```

## Queue using LinkedList

```java
public class Main{
    
    static class Node{
        int data;
        Node next;
        Node(int data){
            this.data = data;
            this.next = null;
        }
    }
    
    static class Queue{
        static Node head = null;
        static Node tail = null;
        
        public static boolean isEmpty(){
            return head == null;
        }
        
        public static void add(int data){
            Node newNode = new Node(data);
            if(isEmpty()){
                tail = head = newNode;
                return;
            }
            tail.next = newNode;
            tail = newNode;
        }
        
        public static int remove(){
            if(isEmpty()){
                System.out.println("Queue is empty...");
                return -1;
            }
            int front = head.data;
            if(head == tail){
                tail = null;
            }
            head = head.next;
            return front;
        }
        
        public static int peek(){
            if(isEmpty()){
                System.out.println("Queue is empty...");
                return -1;
            }
            int front = head.data;
            return front;
        }
        
        public static void display(){
            if(isEmpty()){
                System.out.println("Queue is empty...");
                return;
            }
            Node temp = head;
            while(temp != null){
                System.out.print(temp.data + " ");
                temp = temp.next;
            }
            System.out.println();
        }
    }
    
    public static void main(String args[]){
        Queue q = new Queue();
        q.add(5);
        q.add(5);
        q.add(9);
        q.add(7);
        
        q.display();
        int r = q.remove();
        q.display();
        int p = q.peek();
        
    }
}
```
## Queue using Two Stack

```java
public class Main{
    
    static class Queue{
        static Stack<Integer> s1 = new Stack<>();
        static Stack<Integer> s2 = new Stack<>();
        
        public static boolean isEmpty(){
            return s1.isEmpty();
        }
        
        public static void add(int data){
            while(!s1.isEmpty()){
                s2.push(s1.pop());
            }
            
            s1.push(data);
            
            while(!s2.isEmpty()){
                s1.push(s2.pop());
            }
        }
        
        public static int remove(){
            return s1.pop();
        }
        
        public static int peek(){
            return s1.peek();
        }
        
    }
    
    public static void main(String args[]){
        Queue q = new Queue();
        
        q.add(1);
        q.add(2);
        q.add(3);
        
        while(!q.isEmpty()){
            System.out.print(q.peek() + " ");
            q.remove();
        }
    }
}

```

## Stack using Queue 

```java
public class Main{
    
    static class Stack{
        static Queue<Integer> q1 = new LinkedList<>();
        static Queue<Integer> q2 = new LinkedList<>();
        
        public static boolean isEmpty(){
            return q1.isEmpty();
        }
        
        public static void push(int data){
            while(!q1.isEmpty()){
                q2.add(q1.remove());
            }
            
            q1.add(data);
            
            while(!q2.isEmpty()){
                q1.add(q2.remove());
            }
        }
        
        public static int pop(){
            return q1.remove();
        }
        
        public static int peek(){
            return q1.peek();
        }
        
    }
    
    public static void main(String args[]){
        Stack s = new Stack();
        
        s.push(1);
        s.push(2);
        s.push(3);
        
        while(!s.isEmpty()){
            System.out.print(s.peek() + " ");
            s.pop();
        }
    }
}

```

## CircularQueue using array
```java
public class Main {

    static class CreateCircularQueue {
        int size;
        int front, rear;
        int arr[];

        // constructor
        CreateCircularQueue(int size) {
            this.size = size;
            arr = new int[size];
            front = -1;
            rear = -1;
        }

        // check if queue is full
        public boolean isFull() {
            return (front == (rear + 1) % size);
        }

        // check if queue is empty
        public boolean isEmpty() {
            return (front == -1);
        }

        // insert element
        public void enqueue(int val) {
            if (isFull()) {
                System.out.println("Queue is FULL!");
                return;
            }

            rear = (rear + 1) % size;

            if (front == -1) {
                front = 0;
            }

            arr[rear] = val;
            System.out.println(val + " inserted");
        }

        // delete element
        public int dequeue() {
            if (isEmpty()) {
                System.out.println("Queue is EMPTY!");
                return -1;
            }

            int removed = arr[front];

            if (front == rear) {
                // queue becomes empty
                front = rear = -1;
            } else {
                front = (front + 1) % size;
            }

            return removed;
        }

        // peek front element
        public int peek() {
            if (isEmpty()) {
                System.out.println("Queue is EMPTY!");
                return -1;
            }
            return arr[front];
        }

        // display all elements
        public void display() {
            if (isEmpty()) {
                System.out.println("Queue is EMPTY!");
                return;
            }

            System.out.print("Queue: ");
            int i = front;

            while (true) {
                System.out.print(arr[i] + " ");
                if (i == rear)
                    break;

                i = (i + 1) % size;
            }
            System.out.println();
        }
    }

    public static void main(String args[]) {
        CreateCircularQueue q = new CreateCircularQueue(5);

        q.enqueue(10);
        q.enqueue(20);
        q.enqueue(30);
        q.enqueue(40);

        q.display();

        System.out.println("Dequeued: " + q.dequeue());
        System.out.println("Dequeued: " + q.dequeue());

        q.display();

        q.enqueue(50);
        q.enqueue(60);
        q.enqueue(70); // will wrap around circularly

        q.display();

        System.out.println("Peek: " + q.peek());
    }
}

```
