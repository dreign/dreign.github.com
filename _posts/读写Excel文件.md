---
title: 读写Excel文件
date: 2006-04-19 06:59:00
tags: 
categories: 
---
先要引用这些命名空间. 不明白的地方可以在msdn中找到.

using System.Data.OleDb;  
using Excel;  
using System.Reflection; // For Missing.Value and BindingFlags  

/// <summary>  
  /// 读取Excel表格  
  /// </summary>  
  /// <param name="path">excel文件全名</param>  
  /// <param name="id">放到DataSet中的表名</param>  
  public void readexcel(string path,string id)  
  {  
   try  
   {  
    string strCon = " Provider = Microsoft.Jet.OLEDB.4.0 ; Data Source = " +  
     path + " ; Extended Properties=Excel 8.0" ;  
    OleDbConnection myConn = new OleDbConnection ( strCon ) ;  
    string strCom = " SELECT * FROM [sheet1$]";  
    myConn.Open ( ) ;  
    OleDbDataAdapter myCommand = new OleDbDataAdapter ( strCom , myConn ) ;  
    myCommand.Fill (this.dataSet1,id) ;  
    myConn.Close ( ) ;  
    int ii=this.dataSet1.Tables[id].Rows.Count;  
    }  
   catch(System.Exception op)  
   {  
    MessageBox.Show("发生错误 "+op.Message);  
   }  
  }

     首先将excel.exe copy 到 ..\Microsoft Visual Studio .NET 2003\SDK\v1.1\Bin目录下,利用.net 中带的工具在命令提示符下执行tlbimp excel.exe.这样就不会因为你的Excel是xp或2000的不同要去找不同的*.olb文件，还有一点就是因为在2000以后的版本中没有了excel9.olb这个文件了。通过执行tlbimp excel.exe后我们会得到excel.dll文件。在工程中引用这个文件就可以了.

/// <summary>  
  /// 写入并保存Excel文件  
  /// </summary>  
  /// <param name="path">保存文件的全文件名</param>  
  /// <param name="id">DataSet中的表名</param>  
  private void wexcel2(string path ,string id)  
  {  
   int count = this.dataSet1.Tables[id].Rows.Count;  
   int column = this.dataSet1.Tables[id].Columns.Count;

   Excel.ApplicationClass excelApp = new Excel.ApplicationClass();  
   // Make Excel Visible  
   excelApp.Visible = false;  
   Excel.Workbook workbook =  
    excelApp.Workbooks.Open(fileName,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing);  
    
   excelApp.Cells[1,1] = this.dataSet1.Tables[id].Rows[xx].ItemArray[0];

//.................................

//添加写表的语句.xx,yy,x,y这几个是示意性的变量.  
   excelApp.Cells[x,y] = this.dataSet1.Tables[id].Rows[yy].ItemArray[5];  
       
   string tname = "c:\\\test.xls";  
workbook.SaveAs(tname,Missing.Value,Missing.Value,Missing.Value,Missing.Value,Missing.Value,  
    Excel.XlSaveAsAccessMode.xlNoChange,  
    Missing.Value,Missing.Value,Missing.Value,Missing.Value,Missing.Value);  
     
   try  
   {  
    workbook.Saved = true;  
    excelApp.UserControl = false;  
    excelApp.Quit();  
   }  
   catch (System.Exception op)//(COMException)  
   {  
    MessageBox.Show(op.Message +" \n User closed Excel manually, so we don't have to do that");  
   }  
  }  

---
title: 读写Excel文件
date: 2006-04-19 06:59:00
tags: 
categories: 
---
先要引用这些命名空间. 不明白的地方可以在msdn中找到.

using System.Data.OleDb;  
using Excel;  
using System.Reflection; // For Missing.Value and BindingFlags  

/// <summary>  
  /// 读取Excel表格  
  /// </summary>  
  /// <param name="path">excel文件全名</param>  
  /// <param name="id">放到DataSet中的表名</param>  
  public void readexcel(string path,string id)  
  {  
   try  
   {  
    string strCon = " Provider = Microsoft.Jet.OLEDB.4.0 ; Data Source = " +  
     path + " ; Extended Properties=Excel 8.0" ;  
    OleDbConnection myConn = new OleDbConnection ( strCon ) ;  
    string strCom = " SELECT * FROM [sheet1$]";  
    myConn.Open ( ) ;  
    OleDbDataAdapter myCommand = new OleDbDataAdapter ( strCom , myConn ) ;  
    myCommand.Fill (this.dataSet1,id) ;  
    myConn.Close ( ) ;  
    int ii=this.dataSet1.Tables[id].Rows.Count;  
    }  
   catch(System.Exception op)  
   {  
    MessageBox.Show("发生错误 "+op.Message);  
   }  
  }

     首先将excel.exe copy 到 ..\Microsoft Visual Studio .NET 2003\SDK\v1.1\Bin目录下,利用.net 中带的工具在命令提示符下执行tlbimp excel.exe.这样就不会因为你的Excel是xp或2000的不同要去找不同的*.olb文件，还有一点就是因为在2000以后的版本中没有了excel9.olb这个文件了。通过执行tlbimp excel.exe后我们会得到excel.dll文件。在工程中引用这个文件就可以了.

/// <summary>  
  /// 写入并保存Excel文件  
  /// </summary>  
  /// <param name="path">保存文件的全文件名</param>  
  /// <param name="id">DataSet中的表名</param>  
  private void wexcel2(string path ,string id)  
  {  
   int count = this.dataSet1.Tables[id].Rows.Count;  
   int column = this.dataSet1.Tables[id].Columns.Count;

   Excel.ApplicationClass excelApp = new Excel.ApplicationClass();  
   // Make Excel Visible  
   excelApp.Visible = false;  
   Excel.Workbook workbook =  
    excelApp.Workbooks.Open(fileName,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
    Type.Missing, Type.Missing);  
    
   excelApp.Cells[1,1] = this.dataSet1.Tables[id].Rows[xx].ItemArray[0];

//.................................

//添加写表的语句.xx,yy,x,y这几个是示意性的变量.  
   excelApp.Cells[x,y] = this.dataSet1.Tables[id].Rows[yy].ItemArray[5];  
       
   string tname = "c:\\\test.xls";  
workbook.SaveAs(tname,Missing.Value,Missing.Value,Missing.Value,Missing.Value,Missing.Value,  
    Excel.XlSaveAsAccessMode.xlNoChange,  
    Missing.Value,Missing.Value,Missing.Value,Missing.Value,Missing.Value);  
     
   try  
   {  
    workbook.Saved = true;  
    excelApp.UserControl = false;  
    excelApp.Quit();  
   }  
   catch (System.Exception op)//(COMException)  
   {  
    MessageBox.Show(op.Message +" \n User closed Excel manually, so we don't have to do that");  
   }  
  }  

