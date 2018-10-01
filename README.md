/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package dance.academy;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JPasswordField;
import javax.swing.JRadioButton;
import javax.swing.JTextField;
import static sun.security.jgss.GSSUtil.login;

/**
 *
 * @author miss ladu
 */
public class DanceAcademy {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
      //creating login Frame and Panel  
     JFrame myframe=new JFrame("Login");
     JPanel mypanel=new JPanel();
     JLabel namelabel=new JLabel("Username");
     JLabel b=new JLabel("password");
     JTextField username=new JTextField();     
     JPasswordField password=new JPasswordField();
     username.setColumns(20);
     password.setColumns(20);
     JButton login=new JButton("login");
     JButton Cancel=new JButton("Cancel");
     mypanel.add(namelabel);
     mypanel.add(username);
     mypanel.add(b);
     mypanel.add(password);
     mypanel.add(login);
     mypanel.add(Cancel);
     myframe.add(mypanel);
     myframe.setSize(800,400);
     myframe.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
     myframe.setVisible(true);
     
     login.addActionListener(new action());
 
        
    }
        
       
    //button action listener
    static class action implements ActionListener{
        public void actionPerformed(ActionEvent a){
       JFrame myframe=new JFrame("Add user");
        JPanel mypanel=new JPanel () ;
        JLabel namelabel=new JLabel("First Name:");
        JLabel b=new JLabel("Last Name:");
        JLabel c=new JLabel("Telephone");
        JLabel d=new JLabel("Date of Birth");
        JLabel gender=new JLabel("Gender");
        JTextField firstname=new JTextField();
        JTextField lastname=new JTextField();
        JTextField telephone=new JTextField();
        JTextField dateofbirth=new JTextField();
        namelabel.setBounds(100,150,120,150);
        b.setBounds(100,150,120,150);
        c.setBounds(100,150,120,150);
        d.setBounds(100,150,120,150);
        gender.setBounds(100,150,120,150);
        firstname.setColumns(20);
        lastname.setColumns(20);
        telephone.setColumns(20);
        dateofbirth.setColumns(20);
        JRadioButton Male=new JRadioButton("Male");
        JRadioButton Female=new JRadioButton("Female");    JButton saveuser=new JButton ("Save User");
        JButton cancel=new JButton("cancel");
        mypanel.add(namelabel);
        mypanel.add(firstname);
        mypanel.add(b);
        mypanel.add(lastname);
        mypanel.add(c);
        mypanel.add(telephone);
        mypanel.add(d);
        mypanel.add(dateofbirth);
        mypanel.add(gender);
        mypanel.add(Male);
        mypanel.add(Female);
        mypanel.add(saveuser);
        mypanel.add(cancel);
        myframe.add(mypanel);
        myframe.setSize(900,900);
        myframe.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myframe.setVisible(true);
        
        
         
    }
    }
}
package dance.academy;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

/**
 *
 * @author miss ladu
 */
public class databaseconnect {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        try{
        //connection to database
            Connection conn=DriveManager.getConnection("jdbc:mysql://localhost/ddbaseacad","root","");
            System.out.println("Connection Established..");
            Statement st=conn.createStatement();
            ResultSet rs=st.executeQuery("Select*from users");
            while(rs.next())
            {
                System.out.println(rs.getString(1));
                System.out.println(rs.getString(2));
                System.out.println(rs.getString(3));
                System.out.println(rs.getString(4));
            }
        }catch(Exception e){
            System.out.println("Error");
        }
    }
    
}


