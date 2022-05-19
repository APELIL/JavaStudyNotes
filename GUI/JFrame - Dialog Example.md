# JFrame - Dialog Example

```java
package com.LILRICH.lesson4;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class JFDio {
    public static void main(String[] args) {
    new DioFrame().init();
    }

}

class DioFrame extends JFrame{
    public void init(){
        setSize(200,200);
        setVisible(true);
        Container contentPane = getContentPane();
        contentPane.setBackground(Color.gray);
        contentPane.setLayout(null);
        JButton testButton = new JButton("Test for Diagram");

        //actionListener
        testButton.addActionListener(new AL());
        testButton.setBounds(20,20,300,50);

        contentPane.add(testButton);

        //closing
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    private class AL implements ActionListener{
        @Override
        public void actionPerformed(ActionEvent e) {
            System.out.println("Test");
            new TD();
        }
    }
}

//Dialog
class TD extends JDialog{
    public TD() {
//        setSize(200,200);
        setBounds(20,20,200,50);
        setVisible(true);
        Container container = getContentPane();
        container.setBackground(Color.yellow);
        container.add(new Label("This is a test of dialog"));
    }
}

```

