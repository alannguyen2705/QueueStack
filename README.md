# QueueStack
package Assignment2;
import java.util.Scanner;
public class Main{
	public static Stack stack;
	public static Queue queue;
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int choiceNumber;
		queue = new Queue();
		stack = new Stack();
        Scanner scanner = new Scanner(System.in);
        
        do {
        	System.out.println("Gửi tin nhắn đến khách hàng");
            System.out.println("1. Điền nội dung ");
            System.out.println("2. Gửi tin nhắn ");
            System.out.println("3. Xem tin nhắn ");
            System.out.println("4. Thoát ra");
            
            	System.out.println("Bấm số để chọn (1/2/3/4): ");
            	choiceNumber = scanner.nextInt();
            
            	System.out.println();
                
                switch (choiceNumber) {
                case 1:
                	inputMessage();
                	break;
                case 2:
                	sendMessage();
                	break;
                case 3:
                	viewMessage();
                	break;
                case 4:
                	System.exit(0);
                	break;
                }

            } while(choiceNumber!=4);
        }
	public static void inputMessage() {
		// TODO Auto-generated method stub
        Scanner scanner = new Scanner(System.in);
        System.out.println("Nhập ít hơn 250 ký tự");
        String str = scanner.nextLine();
       
        if(str.length()< 250) {
        	queue.enqueue(str);
        //	System.out.println("Tin nhắn muốn gửi đi là: " + message);
        } else {
        	System.out.println("Chuỗi lớn hơn 250 ký tự");
        }		        
	}
	
	public static void sendMessage() {
		// TODO Auto-generated method stub
		try {
			while(!queue.isEmpty()){
				String message = (String) queue.dequeue();
				stack.push(message);
				}
			System.out.println("Succesfully sent");
		}catch (Exception e)
		{
			e.printStackTrace();
		}
		
	}

	private static void viewMessage() {
		// TODO Auto-generated method stub
		while(!stack.isEmpty()) {
			String message = (String) stack.pop();
			System.out.println(message);
		}
		
	}
