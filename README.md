# Test
//test1和test2分别为两种方法
package string;

import java.io.IOException;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

public class StringTest {
	private static Integer a;
	private static Integer b;
	private static Integer c;
	private static Integer d;
	private static Integer index;
	
	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
//		test1();
//		test2();
		myserver();
	}

	private static void myserver() {
		// TODO Auto-generated method stub
		try {
			//创建一个http server ，监听端口80
			ServerSocket server=new ServerSocket(80);
			//循环监听客户端的请求
			Socket s=null;
			while((s=server.accept())!=null){
				
			 new HTTPThread(s).start();
			
			}
			server.close();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
	class MyThread extends Thread{
		@Override
		public void run() {
			// TODO Auto-generated method stub
			super.run();
		}
	}
	class HTTPThread extends Thread{
		private Socket socket;
		public  HTTPThread(Socket socket) {
			this.socket=socket;
		} 
		
		@Override
		public void run() {
			// TODO Auto-generated method stub
			
			try {
				PrintWriter writer=new PrintWriter(socket.getOutputStream());
				//输出当前系统时间
				writer.println("<html>");
				writer.println("<body>");
				writer.println("HELLO 当前的时间是："+new Date()+"");
				writer.println("<body>");
				writer.println("<html>");
				writer.flush();
				writer.close();
				socket.close();
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}finally{
				
			}
		}
		
	}

	private static void test2() {
		// TODO Auto-generated method stub
		String ip="1.7.3.4";
		String[] strs=ip.split("\\.");
		for (String str: strs) {
			
			System.out.println(str);
		}
		List<Integer> newIntegers = new ArrayList<Integer>();
		StringBuilder str=new StringBuilder();
		
		for (int i = 0; i < strs.length; i++) {
			index=i;
			a=Integer.valueOf(strs[index%4]);
			index++;
			b=Integer.valueOf(strs[index%4]);
			index++;
			c=Integer.valueOf(strs[index%4]);
			d=a*b*c;
			System.out.println(a*b*c);
			newIntegers.add(d);
			str=i == strs.length-1?str.append(d+""):str.append(d+",");
//			System.out.println(1);
		}
		System.out.println(str);
		
	}

	private static void test1() {
		// TODO Auto-generated method stub
		int [] arr=new int[]{1,7,3,4};
		List<Integer> newIntegers = new ArrayList<Integer>();
		StringBuilder str=new StringBuilder();
		for (int i = 0; i < arr.length; i++) {
			
			System.out.println(arr[i]);
		}
		for (int i = 0; i < arr.length; i++) {
			index=i;
			a=arr[index%4];
			index++;
			b=arr[index%4];
			index++;
			c=arr[index%4];
			d=a*b*c;
			System.out.println(a*b*c);
			newIntegers.add(d);
			str=i == arr.length-1?str.append(d+""):str.append(d+",");
//			System.out.println(1);
		}
		System.out.println(newIntegers);
		System.out.println(str);

	}

}
