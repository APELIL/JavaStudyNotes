# Action Listener - Text Field

**Example**

```java
package com.LILRICH.lesson2;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class listener03 {
    public static void main(String[] args) {
    new MyFrame();
    }
}
class MyFrame extends Frame {
    public MyFrame(){
        TextField textField = new TextField();
        TextListener textListener = new TextListener();
        textField.addActionListener(textListener);

        textField.setEchoChar('*');//password simulation
        add(textField);
        setSize(200,200);
        setVisible(true);

        //closing window
        addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });

    }
}

class TextListener implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e) {
        TextField text = (TextField)e.getSource();

        //show input value in control window
        System.out.println(text.getText());
        //delete input content after press return
        text.setText("");
    }
}
```

