---
title: 如何让控件不闪烁呢？打开Control.DoubleBuffered
date: 2006-11-22 09:01:00
tags: 
categories: 
---
如何让控件不闪烁呢？打开Control.DoubleBuffered,即双倍缓冲区！  
如何打开呢？一般控件都从Control集成此DoubleBuffered属性，所以只要重写控件就可以了。  
以ListView为例：  
  

![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif) public class
NewLisetView : System.Windows.Forms.ListView  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void setDoubleBuffer()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
DoubleBuffered = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//一般控件都从Control集成此DoubleBuffered属性，所以只要重写控件就可以了。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
protected override bool DoubleBuffered  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
get  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return base.DoubleBuffered;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
set  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
base.DoubleBuffered = value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}

---
title: 如何让控件不闪烁呢？打开Control.DoubleBuffered
date: 2006-11-22 09:01:00
tags: 
categories: 
---
如何让控件不闪烁呢？打开Control.DoubleBuffered,即双倍缓冲区！  
如何打开呢？一般控件都从Control集成此DoubleBuffered属性，所以只要重写控件就可以了。  
以ListView为例：  
  

![](http://www.cnblogs.com/Images/OutliningIndicators/None.gif) public class
NewLisetView : System.Windows.Forms.ListView  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
public void setDoubleBuffer()  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
DoubleBuffered = true;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
//一般控件都从Control集成此DoubleBuffered属性，所以只要重写控件就可以了。  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
protected override bool DoubleBuffered  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
get  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
return base.DoubleBuffered;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
set  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedSubBlock.gif)
![](http://www.cnblogs.com/Images/dot.gif){  
![](http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif)
base.DoubleBuffered = value;  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif)
}  
![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif)
}

