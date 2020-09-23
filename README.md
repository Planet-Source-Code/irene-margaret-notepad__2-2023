<div align="center">

## Notepad


</div>

### Description

simple notepad application in java2.used advance awt datatransfer class

to do cut,copy and paste. if there is any mistake please feel free to correct me

please test it before using it!.... it is a program by beginner only

Irene Margaret
 
### More Info
 
please first check and then save your existing file.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Irene Margaret](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/irene-margaret.md)
**Level**          |Beginner
**User Rating**    |3.3 (10 globes from 3 users)
**Compatibility**  |Java \(JDK 1\.2\)
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__2-64.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/irene-margaret-notepad__2-2023/archive/master.zip)





### Source Code

```
/*-----------------------------------------------------
simple notepad application in java2.used advance awt datatransfer class
to do cut,copy and paste. if there is any mistake please feel free to correct me
please test it before using it!.... it is a program by beginner only
Irene Margaret
------------------------------------------------------*/
import java.awt.event.*;
import java.awt.*;
import java.applet.*;
import java.awt.datatransfer.*;
import java.awt.datatransfer.Clipboard;
import java.io.*;
class mframe extends Frame{
//String s=" ";
TextArea ta;
mframe(String title){
super(title);
ta=new TextArea(5,50);
add(ta);
MenuBar mbar=new MenuBar();
setMenuBar(mbar);
Menu file=new Menu("File");
MenuItem item1,item2,item3,itemSaveas,itemSave;
file.add(item1=new MenuItem("New"));
file.add(item2=new MenuItem("Open"));
file.add(itemSave=new MenuItem("Save"));
file.add(itemSaveas=new MenuItem("SaveAs..."));
file.add(item3=new MenuItem("Close"));
mbar.add(file);
Menu edit=new Menu("Edit");
MenuItem item4,item5,item6;
edit.add(item4=new MenuItem("Cut"));
edit.add(item5=new MenuItem("Copy"));
edit.add(item6=new MenuItem("Paste"));
mbar.add(edit);
Menu format=new Menu("Format");
MenuItem item7,item8,item9;
format.add(item7=new MenuItem("Bold"));
format.add(item8=new MenuItem("Italic"));
format.add(item9=new MenuItem("Plain"));
Menu font =new Menu("Font",true);
MenuItem item10,item11,item12,item13;
//font.add(item10=new MenuItem("Arial"));
font.add(item11=new MenuItem("MonoSpaced"));
font.add(item12=new MenuItem("Dialog"));
font.add(item13=new MenuItem("Serif"));
Menu size=new Menu("Font Size",true);
MenuItem item14,item15,item16,item17,item18,item19;
size.add(item14=new MenuItem("8"));
size.add(item15=new MenuItem("10"));
size.add(item16=new MenuItem("12"));
size.add(item17=new MenuItem("14"));
size.add(item18=new MenuItem("16"));
size.add(item19=new MenuItem("18"));
Menu color=new Menu("Font Color",true);
MenuItem item21,item22,item23,item24;
color.add(item21=new MenuItem("Red"));
color.add(item22=new MenuItem("Blue"));
color.add(item23=new MenuItem("Green"));
color.add(item24=new MenuItem("Black"));
format.add(font);
format.add(size);
format.add(color);
mbar.add(format);
Menu About1=new Menu("Help");
MenuItem About;
About1.add(About=new MenuItem("About"));
mbar.add(About1);
mymenuhandler h=new mymenuhandler(this);
item1.addActionListener(h);
item2.addActionListener(h);
itemSave.addActionListener(h);
itemSaveas.addActionListener(h);
item3.addActionListener(h);
item4.addActionListener(h);
item5.addActionListener(h);
item6.addActionListener(h);
item7.addActionListener(h);
item8.addActionListener(h);
item9.addActionListener(h);
//item10.addActionListener(h);
item11.addActionListener(h);
item12.addActionListener(h);
item13.addActionListener(h);
item14.addActionListener(h);
item15.addActionListener(h);
item16.addActionListener(h);
item17.addActionListener(h);
item18.addActionListener(h);
item19.addActionListener(h);
//item20.addActionListener(h);
item21.addActionListener(h);
item22.addActionListener(h);
item23.addActionListener(h);
item24.addActionListener(h);
About.addActionListener(h);
mywindowadapter mw=new mywindowadapter(this);
addWindowListener(mw);
}
/*public void paint (Graphics g){
g.drawString(s,100,100);
}*/
}
class mywindowadapter extends WindowAdapter{
mframe f;
public mywindowadapter (mframe f){
this.f=f;
}
public void windowClosing(WindowEvent we){
System.exit(0);
}
}
class mymenuhandler implements ActionListener{
mframe f;
public mymenuhandler (mframe f){
this.f=f;
}
public void actionPerformed(ActionEvent e){
Clipboard clipb;
clipb=Toolkit.getDefaultToolkit().getSystemClipboard();
String arg=(String)e.getActionCommand();
	if(arg.equals("New"))
	{
		f.ta.setText("");
		lastfile="new";
	}
		else if (arg.equals("Open"))
		{
			FileDialog fd=new FileDialog(f,"menu",FileDialog.LOAD);
			fd.setVisible(true);
			String fil=fd.getFile();
			f.ta.setText("");
			lastfile=fil;
			try
			{
				FileReader fr = new FileReader(fil);
				BufferedReader br = new BufferedReader(fr);
				String str;
				str=br.readLine();
				f.ta.append(str);
				br.skip(1);
				while((str=br.readLine())!=null) {
					f.ta.append("\n"+str);
				}
			fr.close();
			}
			catch(Exception eb){ }
	}
	else if (arg.equals("Save"))
		{
		if(lastfile.equals("new"))
		{
			FileDialog fd=new FileDialog(f,"menu",FileDialog.SAVE);
			fd.setVisible(true);
			lastfile=fd.getFile();
		}
		try{
			FileWriter fw=new FileWriter(lastfile);
			fw.write(f.ta.getText());
			fw.close();
		}
		catch(Exception fe){}
	}
	else if (arg.equals("SaveAs..."))
		{
		FileDialog fd=new FileDialog(f,"menu",FileDialog.SAVE);
		fd.setVisible(true);
		String lastfile=fd.getFile();
		try{
			FileWriter fw=new FileWriter(lastfile);
			fw.write(f.ta.getText());
			fw.close();
		}
		catch(Exception fe){}
		}
	else if (arg.equals("Close"))
			System.exit(0);
	else if(arg.equals("Copy"))
	{
		cut=f.ta.getSelectedText();
		if(cut.equals("")) cut=f.ta.getText();
		StringSelection sel=new StringSelection(cut);
		clipb.setContents(sel,null);
	}
	else if(arg.equals("Paste"))
	{
		String cuta;
		clipb=Toolkit.getDefaultToolkit().getSystemClipboard();
		Transferable cont=clipb.getContents(this);
		//if(cont==null)return;
		try
		{
			cuta=(String)(cont.getTransferData(DataFlavor.stringFlavor));
			System.out.println(cuta);
			f.ta.append(cuta);
		}
		catch(Exception fe){
		f.ta.append("error"+fe);
		}
	}
	else if(arg.equals("Cut"))
	{
		cut=f.ta.getSelectedText();
		if(cut.equals("")) cut=f.ta.getText();
		StringSelection sel=new StringSelection(cut);
		clipb.setContents(sel,null);
		int sa=f.ta.getSelectionStart();
		int la=f.ta.getSelectionEnd();
		f.ta.replaceRange("",sa,la);
	}
	else if(arg.equals("Bold"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),Font.BOLD,f.ta.getFont().getSize()));
	else if(arg.equals("Plain"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),Font.PLAIN,f.ta.getFont().getSize()));
	else if(arg.equals("Italic"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),Font.ITALIC,f.ta.getFont().getSize()));
	else if(arg.equals("MonoSpaced"))
	f.ta.setFont(new Font("MonoSpaced",f.ta.getFont().getStyle(),f.ta.getFont().getSize()));
	else if(arg.equals("Dialog"))
	f.ta.setFont(new Font("Dialog",f.ta.getFont().getStyle(),f.ta.getFont().getSize()));
	else if(arg.equals("Serif"))
	f.ta.setFont(new Font("Serif",f.ta.getFont().getStyle(),f.ta.getFont().getSize()));
	else if(arg.equals("8"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),8));
	else if(arg.equals("10"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),10));
	else if(arg.equals("12"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),12));
	else if(arg.equals("14"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),14));
	else if(arg.equals("16"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),16));
	else if(arg.equals("18"))
	f.ta.setFont(new Font(f.ta.getFont().getName(),f.ta.getFont().getStyle(),18));
	else if(arg.equals("Red"))
	f.ta.setForeground(java.awt.Color.red);
	else if(arg.equals("Blue"))
	f.ta.setForeground(java.awt.Color.blue);
	else if(arg.equals("Green"))
	f.ta.setForeground(java.awt.Color.green);
	else if(arg.equals("Black"))
	f.ta.setForeground(java.awt.Color.black);
	else if(arg.equals("About")){
	for(int i=0;i<=3000;i++)
	{
		f.setTitle("Note Editor - Irene. Margaret");
	}
		f.setTitle("Note Editor");
	}
}
	String lastfile="new";
	String cut;
	//int i;
	//String s="";
	//String r="";
}
public class noteeditor{
	public static void main (String args[]){
		Frame f;
		f=new mframe("Note Editor");
		f.setSize(300,300);
		f.setVisible(true);
	}
}
```

