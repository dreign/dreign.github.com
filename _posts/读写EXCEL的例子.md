---
title: 读写EXCEL的例子
date: 2006-11-29 02:52:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  private void
process1()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_database.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择导入数据库！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_moban.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择模版文件！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_out.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择输出路径！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string str1 = "InterRoll";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string str2 = "FileContent";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.readdata(this.textBox_database.Text, str1, "FileRollNo");//案卷题名数据库，以案卷号排序  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//this.readdata(this.textBox_database.Text, str2, "FileNo");//内容项数据库，以案卷号排序  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//遍历题名数据库  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count1 = this.dataSet1.Tables[str1].Rows.Count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Blue;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷分目录生成开始：\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (Directory.Exists(this.textBox_out.Text))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Directory.CreateDirectory(this.textBox_out.Text);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count1; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string[] head = new
string[this.dataSet1.Tables[str1].Rows[i].ItemArray.Length];//案卷分目录题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int k = 0; k < this.dataSet1.Tables[str1].Rows[i].ItemArray.Length; k++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
head[k] = this.dataSet1.Tables[str1].Rows[i].ItemArray[k].ToString();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileNo1 = head[1].Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string seach = "seach1";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.searchdata(this.textBox_database.Text, str2, " FileNo = '" + FileNo1 +
"'", seach);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count2 = this.dataSet1.Tables[seach].Rows.Count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string fileName = this.textBox_moban.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (count2 != 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int finger = count2;//15行的循环计数标示  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int line = 0;       //当前行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.ApplicationClass excelApp = new Excel.ApplicationClass();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Make Excel Visible  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Visible = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// excelApp.Visible = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.Workbook workbook =  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Workbooks.Open(fileName,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.Range range3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int xx = 3;//excel文件的行列  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int yy = 6;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
object[,] array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int line_count = 15;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FLAG:  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (finger > line_count)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[4, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "案卷题名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = head[2];//案卷题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 4] = "档           号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "";//档号(案卷号)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 4] = "编 制 日 期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 5] = head[3];//编制日期  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 4] = "保 管 期 限";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 5] = "永久";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//array3[3, 4] = "共  xx  册    第  nn  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[3, 4] = "共  " + count1.ToString() + "  册    第  " + (i + 1).ToString() +
"  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 5;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += line_count + 1;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[line_count, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
worksheet = (Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < line_count; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int nn = 0; nn < 8; nn++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, nn] = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < line_count; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//*  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "顺序号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = "文 件  编 号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 2] = "责任者";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 3] = "文    件    材    料    题    名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "日    期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 6] = "页      次";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 7] = "备      注";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
*/  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 0] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[2].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 1] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[3].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 2] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[4].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 3] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[5].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 5] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[6].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 6] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[7].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 7] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[8].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
finger -= line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 17;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += 6;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
goto FLAG;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[4, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "案卷题名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = head[2];//案卷题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 4] = "档           号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "";//档号(案卷号)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 4] = "编 制 日 期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 5] = head[3];//编制日期  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 4] = "保 管 期 限";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 5] = "永久";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//array3[3, 4] = "共  xx  册    第  nn  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[3, 4] = "共  " + count1.ToString() + "  册    第  " + (i + 1).ToString() +
"  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 5;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[line_count, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
worksheet = (Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < 15; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int nn = 0; nn < 8; nn++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, nn] = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < finger; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 0] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[2].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 1] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[3].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 2] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[4].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 3] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[5].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 5] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[6].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 6] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[7].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 7] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[8].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
finger = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 17;//表格指向最后一行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += 2;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除多余的表格,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet2 =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet2.get_Range("A" + xx.ToString(), "H484");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//range3.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Delete(Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//excel 2000/xp  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string savename = this.textBox_out.Text + "\\\" + FileNo1 + ".xls";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (File.Exists(savename))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(savename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook._SaveAs(savename, Missing.Value, Missing.Value, Missing.Value,
Missing.Value, Missing.Value,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.XlSaveAsAccessMode.xlNoChange,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Missing.Value, Missing.Value, Missing.Value, Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook.Saved = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook.Close(Missing.Value, Missing.Value, Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.UserControl = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Quit();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Green;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷号：" + FileNo1 + " 添加成功！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Red;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷号：" + FileNo1 + " 对应的内容项不存在！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Blue;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷分目录生成成功！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  

---
title: 读写EXCEL的例子
date: 2006-11-29 02:52:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  private void
process1()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_database.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择导入数据库！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_moban.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择模版文件！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (this.textBox_out.Text == "")  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
MessageBox.Show("请选择输出路径！", "系统信息", MessageBoxButtons.OK,
MessageBoxIcon.Information);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string str1 = "InterRoll";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string str2 = "FileContent";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.readdata(this.textBox_database.Text, str1, "FileRollNo");//案卷题名数据库，以案卷号排序  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//this.readdata(this.textBox_database.Text, str2, "FileNo");//内容项数据库，以案卷号排序  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//遍历题名数据库  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count1 = this.dataSet1.Tables[str1].Rows.Count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Blue;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷分目录生成开始：\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (Directory.Exists(this.textBox_out.Text))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Directory.CreateDirectory(this.textBox_out.Text);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int i = 0; i < count1; i++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string[] head = new
string[this.dataSet1.Tables[str1].Rows[i].ItemArray.Length];//案卷分目录题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int k = 0; k < this.dataSet1.Tables[str1].Rows[i].ItemArray.Length; k++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
head[k] = this.dataSet1.Tables[str1].Rows[i].ItemArray[k].ToString();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string FileNo1 = head[1].Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string seach = "seach1";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.searchdata(this.textBox_database.Text, str2, " FileNo = '" + FileNo1 +
"'", seach);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int count2 = this.dataSet1.Tables[seach].Rows.Count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string fileName = this.textBox_moban.Text;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (count2 != 0)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int finger = count2;//15行的循环计数标示  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int line = 0;       //当前行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.ApplicationClass excelApp = new Excel.ApplicationClass();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//Make Excel Visible  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Visible = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
// excelApp.Visible = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.Workbook workbook =  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Workbooks.Open(fileName,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing, Type.Missing, Type.Missing,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Type.Missing, Type.Missing);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.Range range3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int xx = 3;//excel文件的行列  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int yy = 6;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
object[,] array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
int line_count = 15;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
FLAG:  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (finger > line_count)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[4, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "案卷题名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = head[2];//案卷题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 4] = "档           号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "";//档号(案卷号)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 4] = "编 制 日 期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 5] = head[3];//编制日期  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 4] = "保 管 期 限";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 5] = "永久";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//array3[3, 4] = "共  xx  册    第  nn  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[3, 4] = "共  " + count1.ToString() + "  册    第  " + (i + 1).ToString() +
"  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 5;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += line_count + 1;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[line_count, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
worksheet = (Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < line_count; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int nn = 0; nn < 8; nn++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, nn] = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < line_count; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
/**//*  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "顺序号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = "文 件  编 号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 2] = "责任者";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 3] = "文    件    材    料    题    名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "日    期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 6] = "页      次";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 7] = "备      注";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
*/  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 0] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[2].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 1] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[3].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 2] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[4].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 3] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[5].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 5] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[6].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 6] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[7].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 7] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[8].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
finger -= line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 17;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += 6;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
goto FLAG;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[4, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 0] = "案卷题名";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 1] = head[2];//案卷题名  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 4] = "档           号";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[0, 5] = "";//档号(案卷号)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 4] = "编 制 日 期";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[1, 5] = head[3];//编制日期  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 4] = "保 管 期 限";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[2, 5] = "永久";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//array3[3, 4] = "共  xx  册    第  nn  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[3, 4] = "共  " + count1.ToString() + "  册    第  " + (i + 1).ToString() +
"  册";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 5;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3 = new object[line_count, 8];  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
worksheet = (Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet.get_Range("A" + xx.ToString(), "H" + yy.ToString());  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < 15; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int nn = 0; nn < 8; nn++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, nn] = "";  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
for (int mm = 0; mm < finger; mm++)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 0] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[2].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 1] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[3].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 2] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[4].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 3] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[5].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 5] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[6].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 6] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[7].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
array3[mm, 7] = this.dataSet1.Tables[seach].Rows[line +
mm].ItemArray[8].ToString().Trim();  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Value2 = array3;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
line += line_count;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
finger = 0;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
xx += 17;//表格指向最后一行  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
yy += 2;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//删除多余的表格,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel._Worksheet worksheet2 =
(Excel._Worksheet)workbook.Worksheets.get_Item(1);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3 = worksheet2.get_Range("A" + xx.ToString(), "H484");  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//range3.Clear();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
range3.Delete(Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//excel 2000/xp  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
string savename = this.textBox_out.Text + "\\\" + FileNo1 + ".xls";  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
if (File.Exists(savename))  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
File.Delete(savename);  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook._SaveAs(savename, Missing.Value, Missing.Value, Missing.Value,
Missing.Value, Missing.Value,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Excel.XlSaveAsAccessMode.xlNoChange,  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
Missing.Value, Missing.Value, Missing.Value, Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook.Saved = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
workbook.Close(Missing.Value, Missing.Value, Missing.Value);  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.UserControl = false;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
excelApp.Quit();  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Green;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷号：" + FileNo1 + " 添加成功！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
else  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Red;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷号：" + FileNo1 + " 对应的内容项不存在！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.SelectionColor = Color.Blue;  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
this.richTextBox1.AppendText("案卷分目录生成成功！\n");  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif)  

