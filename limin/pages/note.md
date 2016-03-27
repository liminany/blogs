# 笔记
##2016-03-25 晚 EGO 广州分会成立会议
今晚不容易，到现场已经七点半了，迟到了半小时，今天是周五，刚下班就过来了，非常堵！
EGO这个组织总体感觉不错，虽然入会要收钱，而且还不少，管他呢，以后在广州多举办免费公开课就可以了。
今晚的主题主要是：
* EGO广州分会成立仪式，
* 广州创科委 钟斌 讲了下广州的创业、创新方面的人才、团队、企业激励计划和政策，其实就是个人和团队或者企业组织可以去申请资金，通过评审后可以获得奖励或者投资
* 酷狗音乐的CTO做了演讲，主要是关于 技术人员如何去预判需求和趋势，这是CEO的基本能力，叫洞察力！
* 原CSDN总编辑 韩磊，从他自己的经历---将兴趣爱好做成极致，最终影响到其人生，使得更成功，果然是大年！境界真高！还有 韩大大 果然是媒体人，总是不忘加广告！

具体介绍如下：
[广州高端技术人的组织EGO来啦！——记EGO广州分会成立Party](https://mp.weixin.qq.com/s?__biz=MzA4NTU2MTg3MQ==&mid=406380858&idx=1&sn=801b54e2b8f5ffd16a8fbbed0b0a5117&scene=1&srcid=0326pzI7aQSjlauVrt2lYBGm&from=groupmessage&isappinstalled=0&pass_ticket=yrcT0wo%2B2MphMZTtoXxqFZiZrIK1VTiRVjzs6xtH%2BAvyPLbt4cSIAI6GqddwNrZl)
现场图片：
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_205541.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_205634.jpg)

![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_205734.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_210621.jpg)

![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_210820.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_211204.jpg)

![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_211245.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_211724.jpg)

![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_212059.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_212445.jpg)

![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_212628.jpg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/IMG_20160325_212628.jpg)


##2016-03-21 SARA 分析方法
近年来正被行业积极采纳的、高效的需求分析方法——SARA方法（音 [´særə] ，Structured  Approaches for Requirements Analysis ）方法是一套结构化的需求分析过程，它以场景为中心，以用户目标为聚焦，用例驱动，强调需求语言的统一性，增量和迭代，是构建正确软件系统的一种非常有效的方式。SARA借鉴了很多国内外优秀的一线实践，具有非常好的可操作性和易用性，思想通用性强，它既能适合复杂系统、复杂环境的需求分析，同时也可作为团队需求沟通和协作的一个基础性的工具。SARA方法已经在很多前端行业的软件开发过程中被引入，如互联网、信息通信技术、金融科技等领域.如下图：

![[gimmick:({width:550px})]](https://github.com/liminany/myimgs/raw/master/blog-imgs/Screenshot_2016-03-22-00-27-42.jpeg)
![](https://github.com/liminany/myimgs/raw/master/blog-imgs/Screenshot_2016-03-22-21-00-26.jpeg)

关于敏捷需求分析的文章：
[敏捷过程中的需求分析](http://wenku.baidu.com/link?url=2MoMYOghM0zmb7xO1rvzzHnVu_UYwOoBZ0zrJ50PIaoddLFGy9Udfuu0RfYHGmWliRoomC2UxGW590HJF4ro5G3uDmjEiwtV01KmH5tZNQ_)
[需求分析敏捷方法论](http://wenku.baidu.com/link?url=aOnz_c9pfRc5RtTCMhLyzeXjvQo_H9wkQulK8iELEn76twBjSsEcbYspXORwBGrqEvmvdcuP4Pi4xc6VeuoJjLR0SswRIQO4yt0X6vlffbC)
## 2016-03-20 BDD与TFS集成

####基于Net的BDD相关工具
 - SpecLog
 - SpecRun,SpecFlow
 - xUnit,nUnit
 - 
#### BDD 与 TFS如何集成
 与TFS集成目测现在只能通过在工作项中添加链接或者附件的形式，把Feture文件添加到故事中。这种方式集成度不好，最好的方式是在TFS中可以直接添加，在测试时直接通过Feture生成SpecFlow测试。另外SpecLog好像可以通过Feture文件生成活文档。目前还未找到与TFS2015的集成文章，以下是相关资料：
 - [Behavior Driven Testing with Specflow and TFS Lab Management/SCVmm](https://www.linkedin.com/pulse/behavior-driven-testing-specflow-tfs-lab-roshan-george)
 - [youtube VS2013 SpecFlow使用视频](https://www.youtube.com/watch?v=4-lVKXpBm9U)
 - [leaveraging bdd with VSO/TFS - 2014-08](http://blog.thavo.com/2014/08/leaveraging-bdd-with-microsoft-azure.html)
 - [在ATDD中使用SpecFlow - 2013-12](https://blogs.msdn.microsoft.com/qingsongyao/2013/09/15/acceptance-testing-driven-development-atdd-use-specflow/)
 - [在TFS生成时如何运行Specflow测试 - 2013-9](http://stackoverflow.com/questions/18845733/running-specflow-tests-in-tfs-build)
 - [Managing BDD features in our project (using TFS) - 2010-12](http://www.marcusoft.net/2010/12/managing-bdd-features-in-your-project.html)

## 2016-03-20 在vs2015中编辑MD文件

需要下载一个插件，这个插件支持Visual Studio2015, 2013, 2010。可以通过可视化的方式来编辑MD文件，挺方便的。
不过目前发现一个BUG，在预览时中文会乱码！下载地址：[Markdown Mode](https://visualstudiogallery.msdn.microsoft.com/0855e23e-4c4c-4c82-8b39-24ab5c5a7f79/) 

## 2016-03-20 采用MDWIKI搭建轻博客、笔记

看了好多，觉得还是用MDWiki最简单.


## 2016-03-19 参加 公开课讲座 《社会创新模式如何引领众创时代》

关于 [《社会创新模式如何引领众创时代》](http://www.huodongxing.com/event/6325363787900)：
 是南方都市报举办的一场免费的讲座，主题是：全球性的挑战次第呈现，传统创新模式显得力不从心。什么是社会创新？创新方式如何社会化？如何构建社会创新平台？就上述问题，黄亚生教授经过系统研究，倡导一种众人参与、多元开放、由下而上的自发的社会创新模式，并对中国的产业转型与社会创新提出自己的展望。3月19日，南都公众论坛将邀请MIT斯隆管理学院终身教授黄亚生先生与您畅谈社会创新模式如何引领众创时代.

十点半才到的，迟到了半个小时。开始还以为是讲万众创新、创业相关的，到那听了之后才知道 是讲 行为金融学，讲得最多的还是炒股。

####总的来说还是有收获的:
 - 风险管理，不仅仅是金融投资中风险是第一位的，其实生活、工作、创业中的风险管理也是非常非常重要的
 - 哲学基础，每个人都应该有一种信仰，而且应该坚定不移

 * 最后推荐了一本书：**《海龟交易法则》** --TODO：找到电子书

其他零散的点 

 - 人类的行为是负反馈 金融市场也是负反馈 但大部分是正反馈
 - 有效市场假说 行为金融学 金融加速器 社会大都是正反馈 冠性效应
 - 追涨杀跌 损失厌恶 非理性偏差 波普尔，不确定性，确定风险
 - 静坐 冥想 东方哲学 道家哲学 哲学信念
 - 底限原则，不赔了底裤 投机不是问题，借钱投机是问题 借少是可以，不能搞得翻不了身 止损
 - 三级投资水平 哲学是二级 三级心理素质
 - 西梦思 数学家 量化交易 趋势跟踪 投资技术 基本面

下周25号据说还有，走得太，没听清主题。
