# 工作笔记、备忘，包括技术、管理等

## 2016-04-09 关于ABP、EF、MySQL的实践

[关于ABP-博客园ABP专题](http://www.cnblogs.com/farb/p/ABPTheory.html)

[ABP总体介绍](http://www.cnblogs.com/mienreal/p/4528641.html)  

有一个新项目，比较合适用ABP开发，但遇到一些一，这里记录一下如何解决的。
目标：基于现有数据库，通过工具生成DbContext、EF实体和实体映射，因为想生成干净的实体，试过很多方法，最终还是采用CodeSmith达成目标了。
关于Model First的一些牢骚：因为国内大都是采用数据为中心的开发模式，即项目一上来就是设计数据库，鲜有以模型为中心，采用OO的方式来做分析和设计的.
其实采用这种方式可以用Model First的方式，即 数据库->EDMX->T4模析(VS自带)->代码 来生成代码。
这种方式生成的实体映射是Data Annotations 的方式(特性来映射)。所有采用了

