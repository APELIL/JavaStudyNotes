# JFrame - Introduction

**Example - Using of JFrame**

```java 
package com.LILRICH.lesson4;

import javax.swing.*;
import java.awt.*;

public class JF1 {
    public static void main(String[] args) {
    new MyJF1().init();
    }
}
class MyJF1 extends JFrame{
    public void init(){

        JLabel jLabel = new JLabel("Test JFrame");
        jLabel.setHorizontalAlignment(SwingConstants.CENTER);
        add(jLabel);

        setSize(200,200);
        pack();
        setVisible(true);
        //get a container
        Container container = this.getContentPane();
        //set color
        container.setBackground(Color.gray);

        //closing event
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
}

```

