---
title: javascript中获取url参数
date: 2009-01-06 02:28:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)javascript中获取url参数  
function   getUrlParam(name){  
          var   reg   =   new   RegExp("(^|&)"+   name   +"=([^&]*)(&|$)");     
          var   r   =   window.location.search.substr(1).match(reg);     
          if   (r!=null)   return   unescape(r[2]);   return   null;     
}  

---
title: javascript中获取url参数
date: 2009-01-06 02:28:00
tags: 
categories: 
---
![](http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif)![](http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif)javascript中获取url参数  
function   getUrlParam(name){  
          var   reg   =   new   RegExp("(^|&)"+   name   +"=([^&]*)(&|$)");     
          var   r   =   window.location.search.substr(1).match(reg);     
          if   (r!=null)   return   unescape(r[2]);   return   null;     
}  

