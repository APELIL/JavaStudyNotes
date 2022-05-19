# TCP Chat

#### Client

```java
package TCP;

import com.sun.jmx.snmp.SnmpNull;

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetAddress;
import java.net.Socket;
import java.net.UnknownHostException;

public class TcpClientDemo01 {
    public static void main(String[] args) {
        Socket socket = null;
        OutputStream os = null;
        //1. when you want to send something, you need to know IP and Port
        try {
            InetAddress serverIP = InetAddress.getByName("127.0.0.1");
            int port = 9999;
            //2. create a socket connection
            socket = new Socket(serverIP, port);
            //3.send message I/O flow (output)
            os = socket.getOutputStream();
            os.write("Hi there!".getBytes());
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (os!=null){
                try {
                    os.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (socket!= null){
                try {
                    socket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

#### Server

```java
package TCP;

import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class TcpServerDemo01 {

    public static void main(String[] args) {
        ServerSocket serverSocket = null;
        Socket socket = null;
        InputStream is = null;
        ByteArrayOutputStream baos = null;
        try{
            //1. create an address
            serverSocket = new ServerSocket(9999);
           //2. waiting for connection of client
            socket = serverSocket.accept();
            //3.read message from client
            is = socket.getInputStream();
            baos = new ByteArrayOutputStream();
            byte[] buffer = new byte[1024];
            int len;
            while((len=is.read(buffer))!=-1){
                baos.write(buffer,0,len);
        }
            System.out.println(baos.toString());
        }
        catch(IOException e){
            e.printStackTrace();
        } finally {
            if (baos!=null){
                try {
                    baos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (is!=null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (socket!=null){
                try {
                    socket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (serverSocket!=null){
                try {
                    serverSocket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }

        }


    }
}
```

