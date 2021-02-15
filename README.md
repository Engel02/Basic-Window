# Basic-Window
The program shows a basic design window on Java, with buttons and a texArea
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;


public class MyWindow extends JFrame implements ActionListener {


    //features of the frame
    private static final int FRAME_WIDTH = 650;
    private static final int FRAME_HEIGHT = 400;
    private static final int FRAME_X_ORIGIN = 150;
    private static final int FRAME_Y_ORIGIN = 20;

    //features of the buttons
    private static final int BUTTON_WIDTH = 110;
    private static final int BUTTON_HEIGHT = 30;
    //
    private JMenu myMenu;
    //
    public JMenuBar menuBar;
    //
    public JButton button1;
    public JButton button2;
    public JButton button3;
    public JButton button4;
    //
    public JTextArea textArea;
    //
    public JLabel image;
    //

    Container contentPane;

/*---------------------
Main
 ---------------------*/

    public static void main(String[] args) {

        MyWindow  frame = new MyWindow();
        frame.setVisible(true);


    }//end main


/*---------------------
Constructor
 ---------------------*/

    public MyWindow(){

        contentPane = getContentPane();

        //

        //Title
        setTitle("TEAMS VS TEAMS");
        setResizable(false);
        setSize(FRAME_WIDTH, FRAME_HEIGHT);
        setLocation(FRAME_X_ORIGIN, FRAME_Y_ORIGIN);

        //
        contentPane.setLayout(null);
        contentPane.setBackground(Color.lightGray);
        //


        //Area that we can type
        textArea = new JTextArea();
        textArea.setBounds(170, 70, 300, 170);
        textArea.setEditable(true);
        contentPane.add(textArea);

        //
        createButtons();
        //
        createMenu();
        //

        //Menu Bar
        menuBar = new JMenuBar();
        setJMenuBar(menuBar);
        menuBar.add(myMenu);
        //

        //Image
        image = new JLabel(new ImageIcon("GvsK.jpg"));
        image.setBounds(170, 5, 300, 80);
        contentPane.add(image);


        setDefaultCloseOperation(EXIT_ON_CLOSE);

    }//end MyWindow constructor


/*---------------------
Action Performed
 ---------------------*/

    public void actionPerformed(ActionEvent event){

        String clickButton;
        clickButton = event.getActionCommand();

        if(clickButton.equals("Exit")){

            JOptionPane.showMessageDialog(null, "Good bye!");

            System.exit(0);
        }else{

            textArea.append("You selected " + clickButton + " Button" + '\n');

        }//end else

    }//end actionPerformed


/*---------------------

 ---------------------*/

    public void createButtons(){

        button1 = new JButton("Adventage");
        button1.setBounds(30, 270, BUTTON_WIDTH, BUTTON_HEIGHT);
        button1.setBackground(Color.PINK);
        button1.addActionListener(this);
        contentPane.add(button1);

        button2 = new JButton("Handicap");
        button2.setBounds(170, 270, BUTTON_WIDTH, BUTTON_HEIGHT);
        button2.setBackground(Color.cyan);
        button2.addActionListener(this);
        contentPane.add(button2);

        button3 = new JButton("History");
        button3.setBounds(360, 270, BUTTON_WIDTH, BUTTON_HEIGHT);
        button3.setBackground(Color.ORANGE);
        button3.addActionListener(this);
        contentPane.add(button3);

        button4 = new JButton("Result");
        button4.setBounds(500, 270, BUTTON_WIDTH, BUTTON_HEIGHT);
        button4.setBackground(Color.GRAY);
        button4.addActionListener(this);
        contentPane.add(button4);

    }//end createButtons


    public void createMenu(){

        JMenuItem item;

        myMenu = new JMenu("Menu");

        item = new JMenuItem("Open");
        item.addActionListener(this);
        myMenu.add(item);

        item = new JMenuItem("Save");
        item.addActionListener(this);
        myMenu.add(item);

        myMenu.addSeparator();

        item = new JMenuItem("Exit");
        item.addActionListener(this);
        myMenu.add(item);

    }//end Menu



}

