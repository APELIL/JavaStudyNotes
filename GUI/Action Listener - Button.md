# Action Listener - Button

**Event listener - what happens when the is key pressed** 

**Example 1** - one button 

```java
package com.LILRICH.lesson2;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class listener01 {
    public static void main(String[] args) {
        Frame frame = new Frame();
        Button button = new Button("Test");
        Listener mylistener = new Listener();
        button.addActionListener(mylistener);
        frame.add(button);
        frame.pack();
        frame.setVisible(true);
        cl(frame);
    }
  //close window
    private static void cl(Frame frame){
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
// using interface to realize action listener
class MyListener implements ActionListener{
    @Override
    public void actionPerformed(ActionEvent e) {
      // do "System.out.println("Button test");" when press button
        System.out.println("Button test");
    }
}
```

**Example2** - two button

```java
package com.LILRICH.lesson2;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class listener02 {
    public static void main(String[] args) {
        Frame frame = new Frame();
        Button button1 = new Button("B1");
        Button button2 = new Button("B2");

        Listener myListener = new Listener();
        button1.addActionListener(myListener);
//        button1.setActionCommand("xx");
        button2.addActionListener(myListener);

        frame.setLayout(new BorderLayout());
        frame.add(button1,BorderLayout.WEST);
        frame.add(button2,BorderLayout.EAST);
        frame.pack();
        frame.setVisible(true);
    }
}
class Listener implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e) {
      //get information of button
        System.out.println(e.getActionCommand());
    }
}

```

