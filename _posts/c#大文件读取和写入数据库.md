---
title: c#大文件读取和写入数据库
date: 2007-11-01 14:56:00
tags: 
categories: 
---
c#大文件读取和写入数据库（带进度条的源代码）  



最近一个项目需要将大文件写入和读取到数据库，觉得可能很多人也需要相关得东西，所以就将代码帖出来

protected int state = 0;
//表示进度条当前处理的事件类型，1表读取word,2表写入word，3表doc转pdf，4表txt转pdf

private System.Windows.Forms.Form getDialog(string
strFormName,System.Drawing.Icon ico,string strShowContent)  
  {  
   System.Windows.Forms.Form frm = new Form();  
   //初始化窗体  
   frm.Text = strFormName;  
   frm.Icon = ico;  
   frm.MaximizeBox = false;  
   frm.MinimizeBox = false;  
   frm.TopMost = true;  
   frm.ShowInTaskbar = false;  
   frm.Height = 168;  
   frm.Width = 544;  
   frm.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;

   //添加控件  
   System.Windows.Forms.Label lblContent = new Label();  
   lblContent.Text = strShowContent;  
            lblContent.Left = 30;  
   lblContent.Top = 20;  
   lblContent.Text = strShowContent;  
   frm.Controls.Add(lblContent);  
              
            System.Windows.Forms.ProgressBar prgLoader = new ProgressBar();  
   prgLoader.Left=30;  
   prgLoader.Top = lblContent.Top + lblContent.Height + 5;  
   prgLoader.Width = frm.Width - 2 * 30;  
   frm.Controls.Add(prgLoader);  
     
   System.Windows.Forms.Label lblShowPercent = new Label();  
   lblShowPercent.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
   lblShowPercent.Left = prgLoader.Width + 30 - lblShowPercent.Width;  
   lblShowPercent.Top = prgLoader.Height + prgLoader.Top + 5;  
            lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
   lblShowPercent.Name = "lblShowPercent";  
   frm.Controls.Add(lblShowPercent);

   System.Windows.Forms.Button btnOK = new Button();  
   btnOK.Text = "取消";  
   btnOK.Left = prgLoader.Width + 30 - btnOK.Width;  
   btnOK.Top = frm.Height - 30 - btnOK.Height;  
   btnOK.Click +=new EventHandler(btnOk_Click);  
   frm.Controls.Add(btnOK);  
              
   return frm;  
  }

  private void btnOk_Click(object sender,System.EventArgs e)  
  {  
     //获取控件信息  
   System.Windows.Forms.Button btnOk = (System.Windows.Forms.Button)sender;  
     System.Windows.Forms.Form frm = (System.Windows.Forms.Form)btnOk.Parent;  
   System.Windows.Forms.ProgressBar prgLoader = null;  
   foreach(System.Windows.Forms.Control control in frm.Controls)  
   {  
    if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
    {  
     prgLoader = (System.Windows.Forms.ProgressBar)control;  
    }  
   }  
   //判断当前的完成情况  
   if(prgLoader.Value == 100)  
   {  
    frm.Close();  
   }  
   else  
   {  
    System.Windows.Forms.DialogResult dr = MessageBox.Show(frm,"是否停止当前操作?","提示",System.Windows.Forms.MessageBoxButtons.YesNo,  
     System.Windows.Forms.MessageBoxIcon.Warning);  
    if(dr == System.Windows.Forms.DialogResult.Yes)  
    {   
     state = 0;  
     frm.Close();      
    }

   }  
  }

/// <summary>  
        /// 写入word到数据库  
        /// </summary>  
        /// <param name="sqlcon">sql连接类</param>  
        /// <param name="strTargetInsert">直接将目标内容写入数据库的sql，"insert into 表名(目标列名) values (@block)"</param>  
        /// <param name="strTargetHandle">获取目标内容的句柄的sql，"select @content=textptr(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTableName">目标表名</param>  
        /// <param name="strColumnName">目标列名</param>  
        /// <param name="strPath">要读取word的路径</param>  
        /// <param name="intSetBlock">定义块大小</param>  
  /// <param name="bolShowDialog">是否显示进度条</param>  
  /// <param name="strFormName">窗体名称</param>  
  /// <param name="ico">窗体图标</param>  
  /// <param name="strShowContent">显示内容</param>  
        /// <returns>true表成功</returns>  
  public bool WriteWordDocument(System.Data.SqlClient.SqlConnection
sqlcon,string strTargetInsert,string strTargetHandle,string
strTableName,string strColumnName,string strPath,int intSetBlock,bool
bolShowDialog,string strFormName,System.Drawing.Icon ico,string
strShowContent)  
  {  
   //初始化SqlCommand  
   System.Data.SqlClient.SqlCommand sqlcmd = new
System.Data.SqlClient.SqlCommand();  
   sqlcmd.Connection = sqlcon;  
   sqlcmd.CommandType = System.Data.CommandType.Text;

   int intBlock = intSetBlock; //块大小  
   int intCount = 0; //分快数  
   int intLength = 0; //获取文件内容的长度  
   string strSelect = ""; //要执行的sql查询语句  
   byte []bytContent = null; //定义内容数组  
   //比例  
      int intPercent = 0;  
   //建立要输入的文件流  
            System.IO.FileStream fs = null;  
   //建立二进制读取  
   System.IO.BinaryReader br = null;  
   try  
   {  
    fs = new FileStream(strPath,System.IO.FileMode.Open);  
   }  
   catch  
   {  
    return false;  
   }  
   br = new BinaryReader((Stream)fs);  
            //为关键参数赋值  
   try  
   {  
    //是否显示进度  
    if(bolShowDialog)  
    {  
     //获取精度窗体，引用窗体中的进度条和按钮控件  
     System.Windows.Forms.Form frmProgress = getDialog(strFormName,ico,strShowContent);  
     System.Windows.Forms.ProgressBar prgLoader = null;  
     System.Windows.Forms.Button btnOk = null;  
     System.Windows.Forms.Label lblShowPercent = null;  
     foreach(System.Windows.Forms.Control control in frmProgress.Controls)  
     {  
      if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
      {  
       prgLoader = (System.Windows.Forms.ProgressBar)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Button")  
      {  
       btnOk = (System.Windows.Forms.Button)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Label" && control.Name == "lblShowPercent")  
      {  
       lblShowPercent = (System.Windows.Forms.Label)control;  
      }  
     }  
       
     frmProgress.Show();  
     //启动转换  
     state = 2;

     if(fs.Length > 2147483647 || fs.Length == 0) //因为image列最多只能存储2,147,483,647个字节，所以这里做限定  
     {  
      return false;  
     }  
     intLength = (int)fs.Length;  
     intCount = intLength / intBlock;

     if(intCount == 0)  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intLength];  
      bytContent = br.ReadBytes(intLength);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.ExecuteNonQuery();

     }  
     else  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intBlock];  
      bytContent = br.ReadBytes(intBlock);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.Parameters.Add("@length",System.Data.SqlDbType.Int).Value = 0;  
      sqlcmd.ExecuteNonQuery();  
              
      int i = 1;  
      while(i != intCount)  
      {  
       if(state == 0)  
       {  
        strSelect = "delete from " + strTableName + strTargetHandle.Substring(strTargetHandle.LastIndexOf(" where "));  
        sqlcmd.CommandText = strSelect;  
        sqlcmd.ExecuteNonQuery();  
        bytContent = null;  
        fs.Close();  
        return false;  
       }  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";  
         
       bytContent = br.ReadBytes(intBlock);

       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = i * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();  
         
       intPercent = (int)(((double)(i * intBlock)) / ((double)intLength) * 100);  
       prgLoader.Value = intPercent;  
       lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
       ++i;  
       Application.DoEvents();  
      }

      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";

       bytContent = new byte[intResidual];  
       bytContent = br.ReadBytes(intResidual);  
                      
       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = intCount * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();      
      }  
     }  
     prgLoader.Value = 100;  
     lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
     btnOk.Text = "关闭";

    }  
    else  
    {  
     if(fs.Length > 2147483647 || fs.Length == 0) //因为image列最多只能存储2,147,483,647个字节，所以这里做限定  
     {  
      return false;  
     }  
     intLength = (int)fs.Length;  
     intCount = intLength / intBlock;

     if(intCount == 0)  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intLength];  
      bytContent = br.ReadBytes(intLength);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.ExecuteNonQuery();  
     }  
     else  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intBlock];  
      bytContent = br.ReadBytes(intBlock);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.Parameters.Add("@length",System.Data.SqlDbType.Int).Value = 0;  
      sqlcmd.ExecuteNonQuery();  
      
      int i = 1;  
      while(i != intCount)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";  
         
       bytContent = br.ReadBytes(intBlock);

       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = i * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();  
       ++i;  
      }

      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";

       bytContent = new byte[intResidual];  
       bytContent = br.ReadBytes(intResidual);  
                      
       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = intCount * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();      
      }  
     }  
    }  
    bytContent = null;  
    fs.Close();  
   }  
   catch  
   {  
    state = 0;  
    bytContent = null;  
    fs.Close();  
    return false;  
   }  
   state = 0;  
   return true;  
  }

        /// <summary>  
        /// 从数据库读取word  
        /// </summary>  
        /// <param name="sqlcon">sql连接类</param>  
        /// <param name="strTargetSelect">直接获取目标内容的sql，"select 目标列名 from 目标表名 where 条件"</param>  
        /// <param name="strTargetLength">获取目标内容的长度的sql，"select datalength(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTargetHandle">获取目标内容的句柄的sql，"select @content=textptr(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTableName">目标表名</param>  
        /// <param name="strColumnName">目标列名</param>  
        /// <param name="strPath">要导出并保存的word的路径</param>  
        /// <param name="intSetBlock">定义块大小</param>  
  /// <param name="bolShowDialog">是否显示进度条</param>  
  /// <param name="strFormName">窗体名称</param>  
  /// <param name="ico">窗体图标</param>  
  /// <param name="strShowContent">显示内容</param>  
        /// <returns>true表成功</returns>  
  public bool ReadWordDocument(System.Data.SqlClient.SqlConnection
sqlcon,string strTargetSelect,string strTargetLength,string
strTargetHandle,string strTableName,string strColumnName,string strPath,int
intSetBlock,bool bolShowDialog,string strFormName,System.Drawing.Icon
ico,string strShowContent)  
  {  
   //初始化SqlCommand  
            System.Data.SqlClient.SqlCommand sqlcmd = new System.Data.SqlClient.SqlCommand();  
            sqlcmd.Connection = sqlcon;  
   sqlcmd.CommandType = System.Data.CommandType.Text;

   int intBlock = intSetBlock; //块大小  
   int intCount = 0; //分快数  
   int intLength = 0; //获取的image列中的内容的长度  
   string strSelect = ""; //要执行的sql查询语句  
   byte []bytContent = null; //定义内容数组  
   int intPercent = 0; //获取读取的比例  
   //建立要输出的文件流  
   System.IO.FileStream fs = new
FileStream(strPath,System.IO.FileMode.Create);

   try  
   {  
    //获取指定image列中的内容长度  
    sqlcmd.CommandText = strTargetLength;  
    intLength = (int)sqlcmd.ExecuteScalar();  
    //如果长度为0  
    if(intLength == 0)  
    {  
     return false;  
    }  
    //获得分快数  
    intCount = intLength / intBlock;

                //是否显示精度  
    if(bolShowDialog)  
    {  
     //获取精度窗体，引用窗体中的进度条和按钮控件  
     System.Windows.Forms.Form frmProgress = getDialog(strFormName,ico,strShowContent);  
     System.Windows.Forms.ProgressBar prgLoader = null;  
     System.Windows.Forms.Button btnOk = null;  
     System.Windows.Forms.Label lblShowPercent = null;  
     foreach(System.Windows.Forms.Control control in frmProgress.Controls)  
     {  
      if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
      {  
       prgLoader = (System.Windows.Forms.ProgressBar)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Button")  
      {  
       btnOk = (System.Windows.Forms.Button)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Label" && control.Name == "lblShowPercent")  
      {  
       lblShowPercent = (System.Windows.Forms.Label)control;  
      }  
     }  
       
     frmProgress.Show();  
     //启动转换  
     state = 1;  
     if(intCount == 0)  
     {  
      strSelect = strTargetSelect;  
      sqlcmd.CommandText = strSelect;  
      bytContent = new byte[intLength];  
      bytContent = sqlcmd.ExecuteScalar() as byte[];  
      fs.Write(bytContent,0,intLength);  
      prgLoader.Value = 100;  
      lblShowPercent.Text = prgLoader.Value + "%";  
      btnOk.Text = "关闭";  
        
     }  
     else  
     {  
      int i = 0;  
      bytContent = new byte[intBlock];  
      while(i < intCount)  
      {  
       if(state == 0)  
       {  
        bytContent = null;  
        System.IO.File.Delete(strPath);  
        fs.Close();  
        return false;  
       }  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       if(i == 0)  
       {  
        //添加@start和@count变量，分别表偏移变量和取的长度  
        sqlcmd.Parameters.Add("@start",System.Data.SqlDbType.Int).Value = 0;   
        sqlcmd.Parameters.Add("@count",System.Data.SqlDbType.Int).Value = intBlock;  
       }  
       else  
       {  
        sqlcmd.Parameters["@start"].Value = i * intBlock;  
        sqlcmd.Parameters["@count"].Value = intBlock;  
       }  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intBlock);  
       intPercent = (int)(((double)(i * intBlock)) / (double)(intLength) * 100);  
       prgLoader.Value = intPercent;  
       lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
       Application.DoEvents();  
       ++i;  
      }  
      //将剩余的字节写入流  
      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       bytContent = new byte[intResidual];  
       sqlcmd.Parameters["@start"].Value = intCount * intBlock;  
       sqlcmd.Parameters["@count"].Value = intResidual;  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intResidual);  
         
      }  
      prgLoader.Value = 100;  
      lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
      btnOk.Text = "关闭";  
     }  
    }  
    else  
    {  
     if(intCount == 0)  
     {  
      strSelect = strTargetSelect;  
      sqlcmd.CommandText = strSelect;  
      bytContent = new byte[intLength];  
      bytContent = sqlcmd.ExecuteScalar() as byte[];  
      fs.Write(bytContent,0,intLength);  
     }  
     else  
     {  
      int i = 0;  
      bytContent = new byte[intBlock];  
      while(i < intCount)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       if(i == 0)  
       {  
        //添加@start和@count变量，分别表偏移变量和取的长度  
        sqlcmd.Parameters.Add("@start",System.Data.SqlDbType.Int).Value = 0;   
        sqlcmd.Parameters.Add("@count",System.Data.SqlDbType.Int).Value = intBlock;  
       }  
       else  
       {  
        sqlcmd.Parameters["@start"].Value = i * intBlock;  
        sqlcmd.Parameters["@count"].Value = intBlock;  
       }  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intBlock);  
       ++i;

      }  
      //将剩余的字节写入流  
      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       bytContent = new byte[intResidual];  
       sqlcmd.Parameters["@start"].Value = intCount * intBlock;  
       sqlcmd.Parameters["@count"].Value = intResidual;  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intResidual);

      }  
     }

    }  
     bytContent = null;  
     fs.Close();  
   }  
   catch  
   {  
      state = 0;  
      System.IO.File.Delete(strPath);  
                  bytContent = null;  
                  fs.Close();  
      return false;  
   }  
   state = 0;  
   return true;  
  }

  
  

Trackback: http://tb.blog.csdn.net/TrackBack.aspx?PostId=1537246

---
title: c#大文件读取和写入数据库
date: 2007-11-01 14:56:00
tags: 
categories: 
---
c#大文件读取和写入数据库（带进度条的源代码）  



最近一个项目需要将大文件写入和读取到数据库，觉得可能很多人也需要相关得东西，所以就将代码帖出来

protected int state = 0;
//表示进度条当前处理的事件类型，1表读取word,2表写入word，3表doc转pdf，4表txt转pdf

private System.Windows.Forms.Form getDialog(string
strFormName,System.Drawing.Icon ico,string strShowContent)  
  {  
   System.Windows.Forms.Form frm = new Form();  
   //初始化窗体  
   frm.Text = strFormName;  
   frm.Icon = ico;  
   frm.MaximizeBox = false;  
   frm.MinimizeBox = false;  
   frm.TopMost = true;  
   frm.ShowInTaskbar = false;  
   frm.Height = 168;  
   frm.Width = 544;  
   frm.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;

   //添加控件  
   System.Windows.Forms.Label lblContent = new Label();  
   lblContent.Text = strShowContent;  
            lblContent.Left = 30;  
   lblContent.Top = 20;  
   lblContent.Text = strShowContent;  
   frm.Controls.Add(lblContent);  
              
            System.Windows.Forms.ProgressBar prgLoader = new ProgressBar();  
   prgLoader.Left=30;  
   prgLoader.Top = lblContent.Top + lblContent.Height + 5;  
   prgLoader.Width = frm.Width - 2 * 30;  
   frm.Controls.Add(prgLoader);  
     
   System.Windows.Forms.Label lblShowPercent = new Label();  
   lblShowPercent.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
   lblShowPercent.Left = prgLoader.Width + 30 - lblShowPercent.Width;  
   lblShowPercent.Top = prgLoader.Height + prgLoader.Top + 5;  
            lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
   lblShowPercent.Name = "lblShowPercent";  
   frm.Controls.Add(lblShowPercent);

   System.Windows.Forms.Button btnOK = new Button();  
   btnOK.Text = "取消";  
   btnOK.Left = prgLoader.Width + 30 - btnOK.Width;  
   btnOK.Top = frm.Height - 30 - btnOK.Height;  
   btnOK.Click +=new EventHandler(btnOk_Click);  
   frm.Controls.Add(btnOK);  
              
   return frm;  
  }

  private void btnOk_Click(object sender,System.EventArgs e)  
  {  
     //获取控件信息  
   System.Windows.Forms.Button btnOk = (System.Windows.Forms.Button)sender;  
     System.Windows.Forms.Form frm = (System.Windows.Forms.Form)btnOk.Parent;  
   System.Windows.Forms.ProgressBar prgLoader = null;  
   foreach(System.Windows.Forms.Control control in frm.Controls)  
   {  
    if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
    {  
     prgLoader = (System.Windows.Forms.ProgressBar)control;  
    }  
   }  
   //判断当前的完成情况  
   if(prgLoader.Value == 100)  
   {  
    frm.Close();  
   }  
   else  
   {  
    System.Windows.Forms.DialogResult dr = MessageBox.Show(frm,"是否停止当前操作?","提示",System.Windows.Forms.MessageBoxButtons.YesNo,  
     System.Windows.Forms.MessageBoxIcon.Warning);  
    if(dr == System.Windows.Forms.DialogResult.Yes)  
    {   
     state = 0;  
     frm.Close();      
    }

   }  
  }

/// <summary>  
        /// 写入word到数据库  
        /// </summary>  
        /// <param name="sqlcon">sql连接类</param>  
        /// <param name="strTargetInsert">直接将目标内容写入数据库的sql，"insert into 表名(目标列名) values (@block)"</param>  
        /// <param name="strTargetHandle">获取目标内容的句柄的sql，"select @content=textptr(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTableName">目标表名</param>  
        /// <param name="strColumnName">目标列名</param>  
        /// <param name="strPath">要读取word的路径</param>  
        /// <param name="intSetBlock">定义块大小</param>  
  /// <param name="bolShowDialog">是否显示进度条</param>  
  /// <param name="strFormName">窗体名称</param>  
  /// <param name="ico">窗体图标</param>  
  /// <param name="strShowContent">显示内容</param>  
        /// <returns>true表成功</returns>  
  public bool WriteWordDocument(System.Data.SqlClient.SqlConnection
sqlcon,string strTargetInsert,string strTargetHandle,string
strTableName,string strColumnName,string strPath,int intSetBlock,bool
bolShowDialog,string strFormName,System.Drawing.Icon ico,string
strShowContent)  
  {  
   //初始化SqlCommand  
   System.Data.SqlClient.SqlCommand sqlcmd = new
System.Data.SqlClient.SqlCommand();  
   sqlcmd.Connection = sqlcon;  
   sqlcmd.CommandType = System.Data.CommandType.Text;

   int intBlock = intSetBlock; //块大小  
   int intCount = 0; //分快数  
   int intLength = 0; //获取文件内容的长度  
   string strSelect = ""; //要执行的sql查询语句  
   byte []bytContent = null; //定义内容数组  
   //比例  
      int intPercent = 0;  
   //建立要输入的文件流  
            System.IO.FileStream fs = null;  
   //建立二进制读取  
   System.IO.BinaryReader br = null;  
   try  
   {  
    fs = new FileStream(strPath,System.IO.FileMode.Open);  
   }  
   catch  
   {  
    return false;  
   }  
   br = new BinaryReader((Stream)fs);  
            //为关键参数赋值  
   try  
   {  
    //是否显示进度  
    if(bolShowDialog)  
    {  
     //获取精度窗体，引用窗体中的进度条和按钮控件  
     System.Windows.Forms.Form frmProgress = getDialog(strFormName,ico,strShowContent);  
     System.Windows.Forms.ProgressBar prgLoader = null;  
     System.Windows.Forms.Button btnOk = null;  
     System.Windows.Forms.Label lblShowPercent = null;  
     foreach(System.Windows.Forms.Control control in frmProgress.Controls)  
     {  
      if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
      {  
       prgLoader = (System.Windows.Forms.ProgressBar)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Button")  
      {  
       btnOk = (System.Windows.Forms.Button)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Label" && control.Name == "lblShowPercent")  
      {  
       lblShowPercent = (System.Windows.Forms.Label)control;  
      }  
     }  
       
     frmProgress.Show();  
     //启动转换  
     state = 2;

     if(fs.Length > 2147483647 || fs.Length == 0) //因为image列最多只能存储2,147,483,647个字节，所以这里做限定  
     {  
      return false;  
     }  
     intLength = (int)fs.Length;  
     intCount = intLength / intBlock;

     if(intCount == 0)  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intLength];  
      bytContent = br.ReadBytes(intLength);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.ExecuteNonQuery();

     }  
     else  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intBlock];  
      bytContent = br.ReadBytes(intBlock);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.Parameters.Add("@length",System.Data.SqlDbType.Int).Value = 0;  
      sqlcmd.ExecuteNonQuery();  
              
      int i = 1;  
      while(i != intCount)  
      {  
       if(state == 0)  
       {  
        strSelect = "delete from " + strTableName + strTargetHandle.Substring(strTargetHandle.LastIndexOf(" where "));  
        sqlcmd.CommandText = strSelect;  
        sqlcmd.ExecuteNonQuery();  
        bytContent = null;  
        fs.Close();  
        return false;  
       }  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";  
         
       bytContent = br.ReadBytes(intBlock);

       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = i * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();  
         
       intPercent = (int)(((double)(i * intBlock)) / ((double)intLength) * 100);  
       prgLoader.Value = intPercent;  
       lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
       ++i;  
       Application.DoEvents();  
      }

      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";

       bytContent = new byte[intResidual];  
       bytContent = br.ReadBytes(intResidual);  
                      
       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = intCount * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();      
      }  
     }  
     prgLoader.Value = 100;  
     lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
     btnOk.Text = "关闭";

    }  
    else  
    {  
     if(fs.Length > 2147483647 || fs.Length == 0) //因为image列最多只能存储2,147,483,647个字节，所以这里做限定  
     {  
      return false;  
     }  
     intLength = (int)fs.Length;  
     intCount = intLength / intBlock;

     if(intCount == 0)  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intLength];  
      bytContent = br.ReadBytes(intLength);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.ExecuteNonQuery();  
     }  
     else  
     {  
      strSelect = strTargetInsert;  
      bytContent = new byte[intBlock];  
      bytContent = br.ReadBytes(intBlock);  
      sqlcmd.CommandText = strSelect;  
      sqlcmd.Parameters.Add("@block",System.Data.SqlDbType.Image).Value = bytContent;  
      sqlcmd.Parameters.Add("@length",System.Data.SqlDbType.Int).Value = 0;  
      sqlcmd.ExecuteNonQuery();  
      
      int i = 1;  
      while(i != intCount)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";  
         
       bytContent = br.ReadBytes(intBlock);

       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = i * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();  
       ++i;  
      }

      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) ";  
       strSelect += strTargetHandle;  
       strSelect += " updatetext " + strTableName + "." + strColumnName + " @content @length 0 @block";

       bytContent = new byte[intResidual];  
       bytContent = br.ReadBytes(intResidual);  
                      
       sqlcmd.Parameters["@block"].Value = bytContent;  
       sqlcmd.Parameters["@length"].Value = intCount * intBlock;  
       sqlcmd.CommandText = strSelect;  
       sqlcmd.ExecuteNonQuery();      
      }  
     }  
    }  
    bytContent = null;  
    fs.Close();  
   }  
   catch  
   {  
    state = 0;  
    bytContent = null;  
    fs.Close();  
    return false;  
   }  
   state = 0;  
   return true;  
  }

        /// <summary>  
        /// 从数据库读取word  
        /// </summary>  
        /// <param name="sqlcon">sql连接类</param>  
        /// <param name="strTargetSelect">直接获取目标内容的sql，"select 目标列名 from 目标表名 where 条件"</param>  
        /// <param name="strTargetLength">获取目标内容的长度的sql，"select datalength(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTargetHandle">获取目标内容的句柄的sql，"select @content=textptr(目标列名) from 目标表名 where 条件"</param>  
        /// <param name="strTableName">目标表名</param>  
        /// <param name="strColumnName">目标列名</param>  
        /// <param name="strPath">要导出并保存的word的路径</param>  
        /// <param name="intSetBlock">定义块大小</param>  
  /// <param name="bolShowDialog">是否显示进度条</param>  
  /// <param name="strFormName">窗体名称</param>  
  /// <param name="ico">窗体图标</param>  
  /// <param name="strShowContent">显示内容</param>  
        /// <returns>true表成功</returns>  
  public bool ReadWordDocument(System.Data.SqlClient.SqlConnection
sqlcon,string strTargetSelect,string strTargetLength,string
strTargetHandle,string strTableName,string strColumnName,string strPath,int
intSetBlock,bool bolShowDialog,string strFormName,System.Drawing.Icon
ico,string strShowContent)  
  {  
   //初始化SqlCommand  
            System.Data.SqlClient.SqlCommand sqlcmd = new System.Data.SqlClient.SqlCommand();  
            sqlcmd.Connection = sqlcon;  
   sqlcmd.CommandType = System.Data.CommandType.Text;

   int intBlock = intSetBlock; //块大小  
   int intCount = 0; //分快数  
   int intLength = 0; //获取的image列中的内容的长度  
   string strSelect = ""; //要执行的sql查询语句  
   byte []bytContent = null; //定义内容数组  
   int intPercent = 0; //获取读取的比例  
   //建立要输出的文件流  
   System.IO.FileStream fs = new
FileStream(strPath,System.IO.FileMode.Create);

   try  
   {  
    //获取指定image列中的内容长度  
    sqlcmd.CommandText = strTargetLength;  
    intLength = (int)sqlcmd.ExecuteScalar();  
    //如果长度为0  
    if(intLength == 0)  
    {  
     return false;  
    }  
    //获得分快数  
    intCount = intLength / intBlock;

                //是否显示精度  
    if(bolShowDialog)  
    {  
     //获取精度窗体，引用窗体中的进度条和按钮控件  
     System.Windows.Forms.Form frmProgress = getDialog(strFormName,ico,strShowContent);  
     System.Windows.Forms.ProgressBar prgLoader = null;  
     System.Windows.Forms.Button btnOk = null;  
     System.Windows.Forms.Label lblShowPercent = null;  
     foreach(System.Windows.Forms.Control control in frmProgress.Controls)  
     {  
      if(control.GetType().ToString() == "System.Windows.Forms.ProgressBar")  
      {  
       prgLoader = (System.Windows.Forms.ProgressBar)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Button")  
      {  
       btnOk = (System.Windows.Forms.Button)control;  
      }  
      if(control.GetType().ToString() == "System.Windows.Forms.Label" && control.Name == "lblShowPercent")  
      {  
       lblShowPercent = (System.Windows.Forms.Label)control;  
      }  
     }  
       
     frmProgress.Show();  
     //启动转换  
     state = 1;  
     if(intCount == 0)  
     {  
      strSelect = strTargetSelect;  
      sqlcmd.CommandText = strSelect;  
      bytContent = new byte[intLength];  
      bytContent = sqlcmd.ExecuteScalar() as byte[];  
      fs.Write(bytContent,0,intLength);  
      prgLoader.Value = 100;  
      lblShowPercent.Text = prgLoader.Value + "%";  
      btnOk.Text = "关闭";  
        
     }  
     else  
     {  
      int i = 0;  
      bytContent = new byte[intBlock];  
      while(i < intCount)  
      {  
       if(state == 0)  
       {  
        bytContent = null;  
        System.IO.File.Delete(strPath);  
        fs.Close();  
        return false;  
       }  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       if(i == 0)  
       {  
        //添加@start和@count变量，分别表偏移变量和取的长度  
        sqlcmd.Parameters.Add("@start",System.Data.SqlDbType.Int).Value = 0;   
        sqlcmd.Parameters.Add("@count",System.Data.SqlDbType.Int).Value = intBlock;  
       }  
       else  
       {  
        sqlcmd.Parameters["@start"].Value = i * intBlock;  
        sqlcmd.Parameters["@count"].Value = intBlock;  
       }  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intBlock);  
       intPercent = (int)(((double)(i * intBlock)) / (double)(intLength) * 100);  
       prgLoader.Value = intPercent;  
       lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
       Application.DoEvents();  
       ++i;  
      }  
      //将剩余的字节写入流  
      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       bytContent = new byte[intResidual];  
       sqlcmd.Parameters["@start"].Value = intCount * intBlock;  
       sqlcmd.Parameters["@count"].Value = intResidual;  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intResidual);  
         
      }  
      prgLoader.Value = 100;  
      lblShowPercent.Text = prgLoader.Value.ToString() + "%";  
      btnOk.Text = "关闭";  
     }  
    }  
    else  
    {  
     if(intCount == 0)  
     {  
      strSelect = strTargetSelect;  
      sqlcmd.CommandText = strSelect;  
      bytContent = new byte[intLength];  
      bytContent = sqlcmd.ExecuteScalar() as byte[];  
      fs.Write(bytContent,0,intLength);  
     }  
     else  
     {  
      int i = 0;  
      bytContent = new byte[intBlock];  
      while(i < intCount)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       if(i == 0)  
       {  
        //添加@start和@count变量，分别表偏移变量和取的长度  
        sqlcmd.Parameters.Add("@start",System.Data.SqlDbType.Int).Value = 0;   
        sqlcmd.Parameters.Add("@count",System.Data.SqlDbType.Int).Value = intBlock;  
       }  
       else  
       {  
        sqlcmd.Parameters["@start"].Value = i * intBlock;  
        sqlcmd.Parameters["@count"].Value = intBlock;  
       }  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intBlock);  
       ++i;

      }  
      //将剩余的字节写入流  
      int intResidual = intLength % intBlock;  
      if(intResidual > 0)  
      {  
       strSelect = "declare @content varbinary(16) "; //再sql中声明获取目标image列内容的句柄变量  
       strSelect += strTargetHandle; //获取句柄  
       //锁定并读取指定长度的数据  
       strSelect += " readtext " + strTableName + "." + strColumnName + " @content @start @count HOLDLOCK";  
       bytContent = new byte[intResidual];  
       sqlcmd.Parameters["@start"].Value = intCount * intBlock;  
       sqlcmd.Parameters["@count"].Value = intResidual;  
       sqlcmd.CommandText = strSelect;  
       bytContent = sqlcmd.ExecuteScalar() as byte[];  
       fs.Write(bytContent,0,intResidual);

      }  
     }

    }  
     bytContent = null;  
     fs.Close();  
   }  
   catch  
   {  
      state = 0;  
      System.IO.File.Delete(strPath);  
                  bytContent = null;  
                  fs.Close();  
      return false;  
   }  
   state = 0;  
   return true;  
  }

  
  

Trackback: http://tb.blog.csdn.net/TrackBack.aspx?PostId=1537246

