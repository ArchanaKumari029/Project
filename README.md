electribill.java :-

import javax.swing.*;
import java.awt.event.*;
import java.awt.*;
import java.sql.*;
import java.net.*;
import java.io.*;

public class electricbill implements ActionListener
{
 JFrame f1,f3,f4,f5;
 JPanel p1,p3,p4,p5;
GridBagLayout g1,g2;
GridBagConstraints gbc,gbc1;
 JButton b1,b2,b3,b4,b5,b6,b7,b8,b9,b10,b11,b12,b13;
JButton b14,b15,b16,b17,b18,b19,b20,b21,b22,b23,b24;
 JFrame f2;
JComboBox cb1,cb2;
JLabel im1;
 JPanel p2;
 JLabel l1,l2,l3,l4,l5,l6,l7,l8,l9,l10,l11,l12,l13,l14,l15,l16,l17,l18,l19,l20;
 JTextField t1,t2,t3,t4,t5,t6,t7,t8,t9,t10,t11,t12,t13,t14,t15,t16,t17,t18,t19,t20;
 JTable ta1;
int i,j;
public electricbill()
{
 
f1=new JFrame("Electricity Bill");
f1.addWindowListener(new WindowAdapter() {
public void windowClosing(WindowEvent e) {System.exit(0);}});

p1=new JPanel();
p1.setBackground(Color.CYAN);
b1=new JButton("NewUser");
b1.addActionListener(this);
p1.add(b1);

b2= new JButton("Modify");
b2.addActionListener(this);
p1.add(b2);

b5= new JButton("BillEntry");
b5.addActionListener(this);
p1.add(b5);

b8= new JButton("Billsubmit");
b8.addActionListener(this);
p1.add(b8);

b11= new JButton("All Customer");
b11.addActionListener(this);
p1.add(b11);

b19= new JButton("View By Con.No");
b19.addActionListener(this);
p1.add(b19);

b20= new JButton("View By Name");
b20.addActionListener(this);
p1.add(b20);

b12= new JButton("PaidBill");
b12.addActionListener(this);
p1.add(b12);

b14= new JButton("UnPaidBill");
b14.addActionListener(this);
p1.add(b14);

b15= new JButton("DiscUser");
b15.addActionListener(this);
p1.add(b15);

b16= new JButton("DiscUserList");
b16.addActionListener(this);
p1.add(b16);

Icon p= new ImageIcon("D:\\java\\bin\\CON_ANI.gif");
im1 = new JLabel(p);
p1.add(im1);

f1.getContentPane().add(p1);
f1.setBounds(0,0,800,600);
f1.setVisible(true);

}
public static void main(String[]ag)
{
  new electricbill();
}

public void reg()
{
g1= new GridBagLayout();
gbc= new GridBagConstraints();
f2=new JFrame("Entry Form of Bill");

p2=new JPanel();
p2.setBackground(Color.PINK);
p2.setLayout(g1);


l1= new JLabel(" Consumer No:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=1;
g1.setConstraints(l1,gbc);
p2.add(l1);

t1=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=1;
g1.setConstraints(t1,gbc);
p2.add(t1);

l2=new JLabel("Name:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=5;
g1.setConstraints(l2,gbc);
p2.add(l2);

t2=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=5;
g1.setConstraints(t2,gbc);
p2.add(t2);

l3=new JLabel("Address:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=10;
g1.setConstraints(l3,gbc);
p2.add(l3);

t3=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=10;
g1.setConstraints(t3,gbc);
p2.add(t3);

l4=new JLabel("Meter No:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=15;
g1.setConstraints(l4,gbc);
p2.add(l4);

t4=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=15;
g1.setConstraints(t4,gbc);
p2.add(t4);


b3=new JButton("Submit");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=30;
g1.setConstraints(b3,gbc);
b3.addActionListener(this);
p2.add(b3);

f2.getContentPane().add(p2);
f2.setBounds(150,150,500,350);
f2.setVisible(true);

try
	{
	String s1;
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");          
        PreparedStatement stat = con.prepareStatement("select max(consumerno) from emain");
                  ResultSet result=stat.executeQuery();
	  while(result.next())
	{
	s1=result.getString(1);	
	t1.setText(String.valueOf(Integer.parseInt(s1)+1));
	}
	}
catch(Exception e)
 	{
	  JOptionPane.showMessageDialog(p2,"Error in connection");
	}
	

}

public void billent()
{

g1= new GridBagLayout();
gbc= new GridBagConstraints();
f2=new JFrame("Entry Form of Bill");

p2=new JPanel();
p2.setBackground(Color.PINK);
p2.setLayout(g1);

 String s1[]={"Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sept","Oct","Nov","Dec"};

l1= new JLabel("Bill No:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=1;
g1.setConstraints(l1,gbc);
p2.add(l1);

t1=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=1;
g1.setConstraints(t1,gbc);
p2.add(t1);



l2=new JLabel("Con. No");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=5;
g1.setConstraints(l2,gbc);
p2.add(l2);


t2=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=5;
g1.setConstraints(t2,gbc);
p2.add(t2);

b18 = new JButton("OK");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =100;
gbc.gridy=5;
g1.setConstraints(b18,gbc);
b18.addActionListener(this);
p2.add(b18);

l3=new JLabel("Name");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=10;
g1.setConstraints(l3,gbc);
p2.add(l3);

t3=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=10;
g1.setConstraints(t3,gbc);
p2.add(t3);

l4=new JLabel("Address");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=15;
g1.setConstraints(l4,gbc);
p2.add(l4);

t4=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=15;
g1.setConstraints(t4,gbc);
p2.add(t4);

l10=new JLabel("Meter No");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=20;
g1.setConstraints(l10,gbc);
p2.add(l10);

t10=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=20;
g1.setConstraints(t10,gbc);
p2.add(t10);

l11=new JLabel("Old Reading");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=25;
g1.setConstraints(l11,gbc);
p2.add(l11);

t11=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=25;
g1.setConstraints(t11,gbc);
p2.add(t11);

l12=new JLabel("New Reading");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=30;
g1.setConstraints(l12,gbc);
p2.add(l12);

t12=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=30;
g1.setConstraints(t12,gbc);
p2.add(t12);

l13=new JLabel("Unit");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=35;
g1.setConstraints(l13,gbc);
p2.add(l13);

t13=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=35;
g1.setConstraints(t13,gbc);
p2.add(t13);

l14=new JLabel("Ext. Charge");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=40;
g1.setConstraints(l14,gbc);
p2.add(l14);

t14=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=40;
g1.setConstraints(t14,gbc);
p2.add(t14);

l15=new JLabel("Amount");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=45;
g1.setConstraints(l15,gbc);
p2.add(l15);

t15=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=45;
g1.setConstraints(t15,gbc);
p2.add(t15);

l16=new JLabel("Bill Type");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=50;
g1.setConstraints(l16,gbc);
p2.add(l16);

String s2[]= {" Avg. Bill","Reading Bill"};
cb2=new JComboBox(s2);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=50;
g1.setConstraints(cb2,gbc);
p2.add(cb2);

l18=new JLabel("Due date");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=60;
g1.setConstraints(l18,gbc);
p2.add(l18);

t18=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=60;
g1.setConstraints(t18,gbc);
p2.add(t18);

l19=new JLabel("Bill Month");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=65;
g1.setConstraints(l19,gbc);
p2.add(l19);

cb1=new JComboBox(s1);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=65;
g1.setConstraints(cb1,gbc);
p2.add(cb1);

l20=new JLabel("Paid");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=70;
g1.setConstraints(l20,gbc);
p2.add(l20);

t20=new JTextField("NP");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=70;
g1.setConstraints(t20,gbc);
p2.add(t20);

b17=new JButton("Submit");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=75;
g1.setConstraints(b17,gbc);
b17.addActionListener(this);
p2.add(b17);

f2.getContentPane().add(p2);
f2.setBounds(150,150,500,350);
f2.setVisible(true);

try
	{
	String s22;
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");       


           PreparedStatement stat = con.prepareStatement("select max(billno) from tran");
                  ResultSet result=stat.executeQuery();
	  while(result.next())
	{
	s22=result.getString(1);	
	t1.setText(String.valueOf(Integer.parseInt(s22)+1));
	}
	}
catch(Exception e)
 	{
	  JOptionPane.showMessageDialog(p2,"Error in connection");
	}
}


/****************************BILL SUBMIT*********************************************************/


public void billsub()
{

g1= new GridBagLayout();
gbc= new GridBagConstraints();
f2=new JFrame("Entry Form of Bill Submission");

p2=new JPanel();
p2.setBackground(Color.PINK);
p2.setLayout(g1);



l1= new JLabel("Bill No:");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=1;
g1.setConstraints(l1,gbc);
p2.add(l1);

t1=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=1;
g1.setConstraints(t1,gbc);
p2.add(t1);

b21 = new JButton("OK");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =100;
gbc.gridy=5;
g1.setConstraints(b21,gbc);
b21.addActionListener(this);
p2.add(b21);

l2=new JLabel("Con. No");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=5;
g1.setConstraints(l2,gbc);
p2.add(l2);


t2=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=5;
g1.setConstraints(t2,gbc);
p2.add(t2);


l3=new JLabel("Name");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=10;
g1.setConstraints(l3,gbc);
p2.add(l3);

t3=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=10;
g1.setConstraints(t3,gbc);
p2.add(t3);

l4=new JLabel("Address");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=15;
g1.setConstraints(l4,gbc);
p2.add(l4);

t4=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=15;
g1.setConstraints(t4,gbc);
p2.add(t4);

l10=new JLabel("Meter No");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=20;
g1.setConstraints(l10,gbc);
p2.add(l10);

t10=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=20;
g1.setConstraints(t10,gbc);
p2.add(t10);

l11=new JLabel("Old Reading");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=25;
g1.setConstraints(l11,gbc);
p2.add(l11);

t11=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=25;
g1.setConstraints(t11,gbc);
p2.add(t11);

l12=new JLabel("New Reading");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=30;
g1.setConstraints(l12,gbc);
p2.add(l12);

t12=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=30;
g1.setConstraints(t12,gbc);
p2.add(t12);

l13=new JLabel("Unit");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=35;
g1.setConstraints(l13,gbc);
p2.add(l13);

t13=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=35;
g1.setConstraints(t13,gbc);
p2.add(t13);

l14=new JLabel("Ext. Charge");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=40;
g1.setConstraints(l14,gbc);
p2.add(l14);

t14=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=40;
g1.setConstraints(t14,gbc);
p2.add(t14);

l15=new JLabel("Amount");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=45;
g1.setConstraints(l15,gbc);
p2.add(l15);

t15=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=45;
g1.setConstraints(t15,gbc);
p2.add(t15);

l16=new JLabel("Bill Type");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=50;
g1.setConstraints(l16,gbc);
p2.add(l16);

t16=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=50;
g1.setConstraints(t16,gbc);
p2.add(t16);

l18=new JLabel("Due date");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=60;
g1.setConstraints(l18,gbc);
p2.add(l18);

t18=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=60;
g1.setConstraints(t18,gbc);
p2.add(t18);

l19=new JLabel("Bill Month");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=65;
g1.setConstraints(l19,gbc);
p2.add(l19);

t19=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=65;
g1.setConstraints(t19,gbc);
p2.add(t19);

l20=new JLabel("Paid");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=70;
g1.setConstraints(l20,gbc);
p2.add(l20);

t20=new JTextField("PA");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=70;
g1.setConstraints(t20,gbc);
p2.add(t20);

l17=new JLabel("Paid Date");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=75;
g1.setConstraints(l17,gbc);
p2.add(l17);

t17=new JTextField(20);
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =5;
gbc.gridy=75;
g1.setConstraints(t17,gbc);
p2.add(t17);

b22=new JButton("Submit");
gbc.anchor=GridBagConstraints.NORTHWEST;
gbc.gridx =1;
gbc.gridy=80;
g1.setConstraints(b22,gbc);
b22.addActionListener(this);
p2.add(b22);

f2.getContentPane().add(p2);
f2.setBounds(150,150,500,400);
f2.setVisible(true);

}


/***********************SEARCH BY CONSUMER NO****************************************************/


public void ve1()
{     
   f3 = new JFrame("View By Cons. No");
   p3= new JPanel();
   g2= new GridBagLayout();
   gbc1= new GridBagConstraints();
    p3.setBackground(Color.PINK);
    p3.setLayout(g2);
   
    l5=new JLabel("Con. No");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=1;
   g2.setConstraints(l5,gbc1);
    p3.add(l5);

    t5= new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=1;
    g2.setConstraints(t5,gbc1);
    p3.add(t5);

     l6= new JLabel("Customer Name");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=5;
   g2.setConstraints(l6,gbc1);
     p3.add(l6);

     t6=new JTextField(20);
     gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=5;
   g2.setConstraints(t6,gbc1);
     p3.add(t6);

     l7= new JLabel("Customer Address");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=10;
   g2.setConstraints(l7,gbc1);
     p3.add(l7);

     t7=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=10;
   g2.setConstraints(t7,gbc1);
     p3.add(t7);
	
     l8= new JLabel("Meter No");
gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=20;
   g2.setConstraints(l8,gbc1);
     p3.add(l8);

     t8=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=20;
    g2.setConstraints(t8,gbc1);
    p3.add(t8);

	
    b6= new JButton("Ok");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=35;
   g2.setConstraints(b6,gbc1);
   b6.addActionListener(this);
    p3.add(b6);

    f3.getContentPane().add(p3);
    f3.setBounds(150,150,500,350);
    f3.setVisible(true);

}
public void desc()
{
   f3 = new JFrame("Connection Disconnect Entry");
   p3= new JPanel();
   g2= new GridBagLayout();
   gbc1= new GridBagConstraints();
    p3.setBackground(Color.PINK);
    p3.setLayout(g2);
   
    l5=new JLabel("Con. No");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=1;
   g2.setConstraints(l5,gbc1);
    p3.add(l5);

    t5= new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=1;
    g2.setConstraints(t5,gbc1);
    p3.add(t5);

     l6= new JLabel("Customer Name");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=5;
   g2.setConstraints(l6,gbc1);
     p3.add(l6);

     t6=new JTextField(20);
     gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=5;
   g2.setConstraints(t6,gbc1);
     p3.add(t6);

     l7= new JLabel("Customer Address");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=10;
   g2.setConstraints(l7,gbc1);
     p3.add(l7);

     t7=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=10;
   g2.setConstraints(t7,gbc1);
     p3.add(t7);
	
     l8= new JLabel("Meter No");
gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=20;
   g2.setConstraints(l8,gbc1);
     p3.add(l8);

     t8=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=20;
    g2.setConstraints(t8,gbc1);
    p3.add(t8);

	
    b23= new JButton("Ok");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=35;
   g2.setConstraints(b23,gbc1);
   b23.addActionListener(this);
    p3.add(b23);

    b24= new JButton("Disconnect");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =100;
    gbc1.gridy=35;
   g2.setConstraints(b24,gbc1);
   b24.addActionListener(this);
    p3.add(b24);

    f3.getContentPane().add(p3);
    f3.setBounds(150,150,500,350);
    f3.setVisible(true);

}




public void ve2()
{     
   f3 = new JFrame("View By Personal  No");
   p3= new JPanel();
   g2= new GridBagLayout();
   gbc1= new GridBagConstraints();
   p3.setBackground(Color.BLUE);
    p3.setLayout(g2);
   
    l5=new JLabel("Personal No");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=1;
   g2.setConstraints(l5,gbc1);
    p3.add(l5);

    t5= new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=1;
    g2.setConstraints(t5,gbc1);
    p3.add(t5);

     l6= new JLabel("Person Name");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=5;
   g2.setConstraints(l6,gbc1);
     p3.add(l6);

     t6=new JTextField(20);
     gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=5;
   g2.setConstraints(t6,gbc1);
     p3.add(t6);

     l7= new JLabel("Person  Address");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=10;
   g2.setConstraints(l7,gbc1);
     p3.add(l7);

     t7=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=10;
   g2.setConstraints(t7,gbc1);
     p3.add(t7);
	
     l8= new JLabel("Phone No");
gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=20;
   g2.setConstraints(l8,gbc1);
     p3.add(l8);

     t8=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=20;
    g2.setConstraints(t8,gbc1);
    p3.add(t8);
	
     l9= new JLabel("Email");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=25;
   g2.setConstraints(l9,gbc1);
     p3.add(l9);

     t9=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=25;
    g2.setConstraints(t9,gbc1);
    p3.add(t9);

    b7= new JButton("Ok");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=35;
   g2.setConstraints(b7,gbc1);
   b7.addActionListener(this);
    p3.add(b7);

f3.getContentPane().add(p3);
    f3.setBounds(150,150,500,300);
    f3.setVisible(true);

}


/****************************************mODIFICATION****************************************************/

public void ve3()
{     
   f3 = new JFrame("Record Modification");
   p3= new JPanel();
   g2= new GridBagLayout();
   gbc1= new GridBagConstraints();
    p3.setBackground(Color.PINK); 
  
    p3.setLayout(g2);

    l5=new JLabel("Consumer No");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=1;
   g2.setConstraints(l5,gbc1);
    p3.add(l5);

    t5= new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=1;
    g2.setConstraints(t5,gbc1);
    p3.add(t5);

     l6= new JLabel("Name");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=5;
   g2.setConstraints(l6,gbc1);
     p3.add(l6);

     t6=new JTextField(20);
     gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=5;
   g2.setConstraints(t6,gbc1);
     p3.add(t6);

     l7= new JLabel("Address");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=10;
   g2.setConstraints(l7,gbc1);
     p3.add(l7);

     t7=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=10;
   g2.setConstraints(t7,gbc1);
     p3.add(t7);
	
     l8= new JLabel("Meter No");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=20;
   g2.setConstraints(l8,gbc1);
     p3.add(l8);

     t8=new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=20;
    g2.setConstraints(t8,gbc1);
    p3.add(t8);
	


    b9= new JButton("Ok");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=35;
    g2.setConstraints(b9,gbc1);
    b9.addActionListener(this);
    p3.add(b9);

    b10= new JButton("Save");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =10;
    gbc1.gridy=35;
    g2.setConstraints(b10,gbc1);
    b10.addActionListener(this);
    p3.add(b10);

  f3.getContentPane().add(p3);
    f3.setBounds(150,150,500,350);
  f3.setVisible(true);

}

/***********************DISPLAY ALL RECORDS****************************************************/

public void ve4()
{
   f3 = new JFrame("All the Records");
   p3= new JPanel();

   ta1=new JTable(10,4);
   JScrollPane scrollpane= new JScrollPane(ta1);

try
{
   	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain ");
	ResultSet result=stat.executeQuery();
	i=0;
	j=0;
	while(result.next())
	{
	 	ta1.setValueAt(result.getString(1),i,j);
		j++;
		ta1.setValueAt(result.getString(2),i,j); 	
		j++;
		ta1.setValueAt(result.getString(3),i,j);
		j++;
		ta1.setValueAt(result.getString(4),i,j);
		
		i++;
		j=0;
		
	}
    }
  catch(Exception e)
 {
	System.out.println("Error" +e);
}
   f3.getContentPane().add(p3);
  f3.getContentPane().add(scrollpane);
   f3.setBounds(150,150,500,350);
   f3.setVisible(true);

}


/**********************************UNPAID BILL RECORDS****************************************************/

public void ve14()
{
   f3 = new JFrame("All Unpaid Records");
   p3= new JPanel();

   ta1=new JTable(10,6);
   JScrollPane scrollpane= new JScrollPane(ta1);

try
{
   	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select billno,consno,cname,address,amount,billmonth from tran where paid='NP' ");
	ResultSet result=stat.executeQuery();
	i=0;
	j=0;
	while(result.next())
	{
	 	ta1.setValueAt(result.getString(1),i,j);
		j++;
		ta1.setValueAt(result.getString(2),i,j); 	
		j++;
		ta1.setValueAt(result.getString(3),i,j);
		j++;
		ta1.setValueAt(result.getString(4),i,j);
		j++;
		ta1.setValueAt(result.getString(5),i,j);
		j++;
		ta1.setValueAt(result.getString(6),i,j);
		
		i++;
		j=0;
		
	}
    }
  catch(Exception e)
 {
	System.out.println("Error" +e);
}
   f3.getContentPane().add(p3);
  f3.getContentPane().add(scrollpane);
   f3.setBounds(150,150,500,350);
   f3.setVisible(true);

}


/**********************************PAID BILL RECORDS****************************************************/

public void ve15()
{
   f3 = new JFrame(" All paid Records");
   p3= new JPanel();

   ta1=new JTable(10,6);
   JScrollPane scrollpane= new JScrollPane(ta1);

try
{
   	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select billno,consno,cname,address,amount,billmonth from tran where paid='PA' ");
	ResultSet result=stat.executeQuery();
	i=0;
	j=0;
	while(result.next())
	{
	 	ta1.setValueAt(result.getString(1),i,j);
		j++;
		ta1.setValueAt(result.getString(2),i,j); 	
		j++;
		ta1.setValueAt(result.getString(3),i,j);
		j++;
		ta1.setValueAt(result.getString(4),i,j);
		j++;
		ta1.setValueAt(result.getString(5),i,j);
		j++;
		ta1.setValueAt(result.getString(6),i,j);
		
		i++;
		j=0;
		
	}
    }
  catch(Exception e)
 {
	System.out.println("Error" +e);
}
   f3.getContentPane().add(p3);
  f3.getContentPane().add(scrollpane);
   f3.setBounds(150,150,500,350);
   f3.setVisible(true);

}


/**********************************SEARCH BY NAME****************************************************/


public void ve5()
{
   f4 = new JFrame("View By Name");
   p4= new JPanel();
   g2= new GridBagLayout();
   gbc1= new GridBagConstraints();
   p4.setBackground(Color.PINK);
    p4.setLayout(g2);

    l5=new JLabel("Customer Name");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=1;
   g2.setConstraints(l5,gbc1);
    p4.add(l5);

    t5= new JTextField(20);
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =5;
    gbc1.gridy=1;
    g2.setConstraints(t5,gbc1);
    p4.add(t5);
   
    b13= new JButton("Ok");
    gbc1.anchor=GridBagConstraints.NORTHWEST;
    gbc1.gridx =1;
    gbc1.gridy=35;
    g2.setConstraints(b13,gbc1);
    b13.addActionListener(this);
    p4.add(b13);

   f4.getContentPane().add(p4);
    f4.setBounds(150,150,500,350);
    f4.setVisible(true);

}
  public void actionPerformed(ActionEvent ev)
  {
    Object obj;
    obj=ev.getSource();
    if(obj==b3)
    {
	String a = t1.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Consumer No ");
		return;
	}
	
	 a = t2.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill  Name ");
		return;
	}
	 a = t3.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill  Address");
		return;
	}
	 a = t4.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Meter No ");
		return;
	}
	
	
	try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("insert into emain values(?,?,?,?)");
	stat.setString(1,t1.getText());
	stat.setString(2,t2.getText());
	stat.setString(3,t3.getText());
	stat.setString(4,t4.getText());
	stat.executeUpdate();
	JOptionPane.showMessageDialog(p2,"Value Inserted");
	}
               catch(Exception e)
 	{
		System.out.println("Error " +e);
	}
   }
/*************************************************************************************************************/
   if(obj==b1) // Entry Program
   {
       reg();
   }
 if (obj==b2)
 {
   ve3();
 }
if (obj == b6)
 {
	  
try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain where consumerno=?");
	stat.setString(1,t5.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t6.setText(result.getString(2));	 	
		t7.setText(result.getString(3));
		t8.setText(result.getString(4));
	}

	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}
}
if (obj==b5)
{
billent();
}
if(obj==b8)
{
  billsub();
}

if(obj==b7)
{
             try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from customer where pno=?");
	stat.setString(1,t5.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t6.setText(result.getString(2));	 	
		t7.setText(result.getString(3));
		t8.setText(result.getString(4));
		t9.setText(result.getString(5));
	}

	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}


}

if(obj==b9)
{
		  
           try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain where consumerno=?");
	stat.setString(1,t5.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t6.setText(result.getString(2));	 	
		t7.setText(result.getString(3));
		t8.setText(result.getString(4));
		
	}
	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}
    }
if(obj==b10)
{
	try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("delete from emain where consumerno=?");
	stat.setString(1,t5.getText());
	stat.executeUpdate();
	 stat = con.prepareStatement("insert into emain values(?,?,?,?)");
	stat.setString(1,t5.getText());
	stat.setString(2,t6.getText());
	stat.setString(3,t7.getText());
	stat.setString(4,t8.getText());
	stat.executeUpdate();
	JOptionPane.showMessageDialog(p2,"Value Modified");
	}
               catch(Exception e)
 	{
		System.out.println("Error " +e);
	}

}
if(obj==b11)
  {
      ve4();
  }
 if(obj==b12)
 {
   ve15();
 }
if(obj==b13)
{
   f5 = new JFrame("Reocrds By Name");
   p5= new JPanel();

   ta1=new JTable(10,4);
   JScrollPane scrollpane= new JScrollPane(ta1);

           try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain where custname=?");
	stat.setString(1,t5.getText());
	ResultSet result=stat.executeQuery();
	i=0;
	j=0;
	while(result.next())
	{
	 	ta1.setValueAt(result.getString(1),i,j);
		j++;
		ta1.setValueAt(result.getString(2),i,j); 	
		j++;
		ta1.setValueAt(result.getString(3),i,j);
		j++;
		ta1.setValueAt(result.getString(4),i,j);
		i++;
		j=0;
	}
	}
	catch(Exception e)
	{
		System.out.println("Error" +e)	;
	}

      f5.getContentPane().add(p5);
  f5.getContentPane().add(scrollpane);
   f5.setBounds(150,150,500,350);
   f5.setVisible(true);

}
  if(obj==b17)
    {
	String a = t1.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Bill No ");
		return;
	}
	
	 a = t2.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Con No. ");
		return;
	}
	 a = t3.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please Name");
		return;
	}
	 a = t4.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Address ");
		return;
	}
	
 	a = t10.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Meter No");
		return;
	}
	
	 a = t11.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Old reading");
		return;
	}
	
	 a = t12.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill New Reading");
		return;
	}	
	
	 a = t13.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill the unit");
		return;
	}
	
	 a = t14.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill extra charge");
		return;
	}

	 a = t15.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill amount");
		return;
	}

	
	 a = t18.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Due Date");
		return;
	}

	a = t20.getText();
	if(a.length()==0)
        	{ 
		System.out.println("Please fill Paid");
		return;
	}
try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("insert into tran (billno,consno,cname,address,meterno,oldreading,newreading,unitcon,extracharge,amount,billtype,billmonth,duedate,paid) values(?,?,?,?,?,?,?,?,?,?,?,?,?,?)");
	stat.setString(1,t1.getText());
	stat.setString(2,t2.getText());
	stat.setString(3,t3.getText());
	stat.setString(4,t4.getText());
	stat.setString(5,t10.getText());
	stat.setString(6,t11.getText());
	stat.setString(7,t12.getText());
	stat.setString(8,t13.getText());
	stat.setString(9,t14.getText());
	stat.setString(10,t15.getText());
	stat.setString(11,String.valueOf(cb2.getSelectedItem()));
	String pos;
	pos=String.valueOf(cb1.getSelectedItem());
	stat.setString(12,pos);
	stat.setString(13,t18.getText());
	stat.setString(14,t20.getText());
	stat.executeUpdate();
	JOptionPane.showMessageDialog(p2,"Value Inserted");
	}
               catch(Exception e)
 	{
		System.out.println("Error " +e);
	}
   }
if(obj==b18)
{
           try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain where consumerno=?");
	stat.setString(1,t2.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t3.setText(result.getString(2));	 	
		t4.setText(result.getString(3));
		t10.setText(result.getString(4));
		
	}
	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}


}
if(obj==b14)
{
  ve14();
}

if(obj==b19)
{
   ve1();
}

if(obj==b20)
{
   ve5();
}

if(obj==b21)
{

           try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select billno,consno,cname,address,meterno,oldreading,newreading,unitcon,extracharge,amount,billtype,billmonth,duedate,PAID  from tran where billno=?");
	stat.setString(1,t1.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t2.setText(result.getString(2));	 	
		t3.setText(result.getString(3));
		t4.setText(result.getString(4));
		t10.setText(result.getString(5));
		t11.setText(result.getString(6));	 	
		t12.setText(result.getString(7));
		t13.setText(result.getString(8));
		t14.setText(result.getString(9));
		t15.setText(result.getString(10));	 		 		
		t16.setText(result.getString(11));	 	 		 	
		t19.setText(result.getString(12));	 	
		t18.setText(result.getString(13));	 	
		t20.setText(result.getString(14));	 	
	 	
		
	}
	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}

}

if(obj==b22)
{
try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("update tran set paid='PA' , paiddate=? where billno=?");
		stat.setString(1,t17.getText());
		stat.setString(2,t1.getText());
			stat.executeUpdate();
	JOptionPane.showMessageDialog(p2,"Value Inserted");
	}
	catch(Exception e)
	{
		System.out.println(" Error" +e);
	}

}
if(obj==b23)
{
try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from emain where consumerno=?");
	stat.setString(1,t5.getText());
	ResultSet result=stat.executeQuery();
	while(result.next())
	{
	 	t6.setText(result.getString(2));	 	
		t7.setText(result.getString(3));
		t8.setText(result.getString(4));
	}
		
	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}
}

if(obj==b24)
{

try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("delete from emain where consumerno=?");
	stat.setString(1,t5.getText());
	stat.executeUpdate();
	stat = con.prepareStatement("insert into disc (consno,name,address,meterno) values(?,?,?,?)");
	stat.setString(1,t5.getText());
	stat.setString(2,t6.getText());
	stat.setString(3,t7.getText());
	stat.setString(4,t8.getText());
	stat.executeUpdate();
	JOptionPane.showMessageDialog(p2,"Value Inserted in DESC");
	}
	catch(Exception e)
	{
	System.out.println("Error "+e);
	}

}
if(obj==b15)
{
  desc();
}
if(obj==b16)
{
   f5 = new JFrame("Dis Connected User List");
   p5= new JPanel();

   ta1=new JTable(10,4);
   JScrollPane scrollpane= new JScrollPane(ta1);

           try
	{
	 Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
	  Connection con;
	  con= DriverManager.getConnection("jdbc:odbc:sai3","","");
	PreparedStatement stat = con.prepareStatement("select * from disc ");
	ResultSet result=stat.executeQuery();
	i=0;
	j=0;
	while(result.next())
	{
	 	ta1.setValueAt(result.getString(1),i,j);
		j++;
		ta1.setValueAt(result.getString(2),i,j); 	
		j++;
		ta1.setValueAt(result.getString(3),i,j);
		j++;
		ta1.setValueAt(result.getString(4),i,j);
		i++;
		j=0;
	}
	}
	catch(Exception e)
	{
		System.out.println("Error" +e)	;
	}

      f5.getContentPane().add(p5);
  f5.getContentPane().add(scrollpane);
   f5.setBounds(150,150,500,350);
   f5.setVisible(true);

}

}//close of action performed
}//Close of Class
