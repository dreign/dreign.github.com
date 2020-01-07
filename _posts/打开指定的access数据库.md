---
title: 打开指定的access数据库
date: 2006-06-27 04:00:00
tags: 
categories: 
---
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedBlock.gif)
/**//// <summary>  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
打开指定的access数据库  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
<param name="spath">access数据库名</param>  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockEnd.gif)
/// <param name="dataname">access数据库中的表名</param>  
![](https://www.cnblogs.com/images/OutliningIndicators/None.gif)        public
bool readdata(string spath, string dataname)  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
try  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedSubBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//创建一个 OleDbConnection对象  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
string strCon = " Provider = Microsoft.Jet.OLEDB.4.0 ; Data Source = " +
spath;  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
OleDbConnection myConn = new OleDbConnection(strCon);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
// string strCom = " SELECT * FROM " + dataname + " ORDER BY  id";  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//string strCom = " SELECT * FROM " + dataname ;  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
string strCom = "SELECT [" + dataname + "].* FROM [" + dataname + "]";  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//创建一个 DataSet对象  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myConn.Open();  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
OleDbDataAdapter myCommand = new OleDbDataAdapter(strCom, myConn);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myCommand.Fill(this.dataSet1, dataname);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myConn.Close();  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
return true;  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
catch (Exception e)  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedSubBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
MessageBox.Show("连接数据库发生错误：" + e.ToString(), "错误！", MessageBoxButtons.OK,
MessageBoxIcon.Error);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
return false;  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockEnd.gif)
}

---
title: 打开指定的access数据库
date: 2006-06-27 04:00:00
tags: 
categories: 
---
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedBlock.gif)
/**//// <summary>  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
打开指定的access数据库  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
</summary>  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)        ///
<param name="spath">access数据库名</param>  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockEnd.gif)
/// <param name="dataname">access数据库中的表名</param>  
![](https://www.cnblogs.com/images/OutliningIndicators/None.gif)        public
bool readdata(string spath, string dataname)  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
try  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedSubBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//创建一个 OleDbConnection对象  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
string strCon = " Provider = Microsoft.Jet.OLEDB.4.0 ; Data Source = " +
spath;  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
OleDbConnection myConn = new OleDbConnection(strCon);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
// string strCom = " SELECT * FROM " + dataname + " ORDER BY  id";  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//string strCom = " SELECT * FROM " + dataname ;  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
string strCom = "SELECT [" + dataname + "].* FROM [" + dataname + "]";  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
//创建一个 DataSet对象  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myConn.Open();  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
OleDbDataAdapter myCommand = new OleDbDataAdapter(strCom, myConn);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myCommand.Fill(this.dataSet1, dataname);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
myConn.Close();  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
return true;  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
catch (Exception e)  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockStart.gif)![](https://www.cnblogs.com/images/OutliningIndicators/ContractedSubBlock.gif)
![](https://www.cnblogs.com/images/dot.gif){  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
MessageBox.Show("连接数据库发生错误：" + e.ToString(), "错误！", MessageBoxButtons.OK,
MessageBoxIcon.Error);  
![](https://www.cnblogs.com/images/OutliningIndicators/InBlock.gif)
return false;  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](https://www.cnblogs.com/images/OutliningIndicators/ExpandedBlockEnd.gif)
}

