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


