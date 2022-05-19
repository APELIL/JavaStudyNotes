# Action Listener - Practice(simple calculator) 

**Example 1 - Process oriented programming**

```java
package com.LILRICH.lesson2;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class CalOPP {
    public static void main(String[] args) {
        new OppFrame();
    }
}

//Frame
class OppFrame extends Frame{
    public OppFrame() {
        //1. TextField
        TextField num1 = new TextField(10);
        TextField num2 = new TextField(10);
        TextField num3 = new TextField(20);

        //2. Label
        Label label = new Label("+");

        //3. Button & action listener
        Button button = new Button("=");
        OppListener oppListener = new OppListener(num1, num2, num3);
        button.addActionListener(oppListener);
        //Layout - Flowlayout
        setLayout(new FlowLayout());

        //add
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);

        //Set it to visible
        pack();
        setVisible(true);
    }
}
//Listener
class OppListener implements ActionListener{
//    pass num1,2,3 from another class
    private TextField num1, num2, num3;
    public OppListener(TextField num1, TextField num2, TextField num3){
        this.num1 = num1;
        this.num2 = num2;
        this.num3 = num3;
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        // 1. get num1, num2, num3
        int n1 = Integer.parseInt(num1.getText());
        int n2 = Integer.parseInt(num2.getText());
        // 2. put num3 into third block
        num3.setText(""+(n1+n2));
        // 3. delete num1 and num2
        num1.setText("");
        num2.setText("");
    }
}
```

**Example 2 - Object oriented programming**

```java
package com.LILRICH.lesson2;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class CalOOP {
    public static void main(String[] args) {
        new OopFrame().loadFrame();
    }
}

//Frame
class OopFrame extends Frame{
    //1. attribute
    TextField num1, num2, num3;
    //2. method
    public void loadFrame(){
        //1. TextField
        num1 = new TextField(10);
        num2 = new TextField(10);
        num3 = new TextField(20);
        //2. Label
        Label label = new Label("+");
        //3. Button & action listener
        Button button = new Button("=");
        OopListener oopListener = new OopListener(this);
        button.addActionListener(oopListener);
        //Layout - Flowlayout
        setLayout(new FlowLayout());

        //add
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);

        //Set it to visible
        pack();
        setVisible(true);
    }
}
//Listener
class OopListener implements ActionListener{
    //   get object
    OopFrame oopFrame = null;
    public OopListener(OopFrame oopFrame){
     this.oopFrame = oopFrame;
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        // 1. get num1, num2, num3
        // 2. put num3 into third block
        // 3. delete num1 and num2
        int n1 = Integer.parseInt(oopFrame.num1.getText());
        int n2 = Integer.parseInt(oopFrame.num2.getText());
        oopFrame.num3.setText(""+(n1+2));
    }
}
```

**Example 3 - Inner Class**

**Benefit of Inner class** - Unobstructed to access attributes and methods of external

```java
package com.LILRICH.lesson2;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class CalInClass {
    public static void main(String[] args) {
        new InCal().loadCal();
    }
}
class InCal extends Frame{
    //1.Attributes
    TextField num1, num2, num3;

    //2.Method
    public void loadCal(){
        num1 = new TextField(10);
        num2 = new TextField(10);
        num3 = new TextField(20);
        Label label = new Label("+");
        Button button = new Button("=");
        //Listener
        InListener inListener = new InListener();
        button.addActionListener(inListener);
        cl(this);//close the window
        //set layout
        setLayout(new FlowLayout());

        //add
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);

        //set it to visible
        pack();
        setVisible(true);
    }
    //method to close window
    public void cl(Frame frame){
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
            System.exit(0);
            }
        });
    }
    private class InListener implements ActionListener{
        @Override
        public void actionPerformed(ActionEvent e) {
            int n1 = Integer.parseInt(num1.getText());
            int n2 = Integer.parseInt(num2.getText());
            num3.setText(""+(n1+n2));
        }
    }
}

```

