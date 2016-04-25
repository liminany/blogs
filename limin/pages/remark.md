# 工作笔记、备忘，包括技术、管理等

## 2016-04-25 SequoiaDB_分布式数据库 ppt 知识点分析
[来源: SequoiaDB_分布式数据库_王涛_微软MVP ppt](http://pan.baidu.com/s/1qXOAOmo) 

### 1.关于数据库设计--范式与反范式设计思考 [参考：范式与反范式的设计](http://www.daniel-journey.com/archives/519)

#### 反范式设计使用场景：对不可改变数据的反模式设计，如 将多张表合并成一张
#### 正范式设计使用场景：即传统的范式化设计，折表，范式化节省了存储空间，但存储空间却很便宜；范式化简化了更新，但读更普遍

### 2.关于MPP数据库 [参考：MPP数据库 技术浅析](http://database.ctocio.com.cn/326/12953326.shtml)   [数据仓库技术中的MPP](http://www.dedecms.com/knowledge/data-base/generalized/2012/0703/2510.html)
#### 数据仓库世界里面的 massively parallel processing 大概定义：
　　MPP 是将任务并行的分散到多个服务器和节点上，在每个节点上计算完成后，将各自部分的结果汇总在一起得到最终的结果。
　　首先MPP 必须消除手工切分数据的工作量。 这是MySQL 在互联网应用中的主要局限性。
　　另外MPP 的切分必须在任何时候都是平均的 ， 不然某些节点处理的时间就明显多于另外一些节点。
　 　对于工作负载是不是要平均分布有同种和异种之分，同种就是所有节点在数据装载的时候都同时转载，异种就是可以指定部分节点专门用来装载数据（逻辑上的不 是物理上） ， 而其他所有节点用来负责查询。 Aster Data 和Greenplum 都属于这种。 两者之间并没有明显的优势科研，同种的工作负载情况下，需要软件提供商保证所有节点的负载是平衡的。 而异种的工作负载可以在你觉得数据装载很慢的情况下手工指定更多节点装载数据
#### MPP数据库解决的问题与分布式数据库类似，从发展历程来说分布式数据库是从MPP演进而来的，特征如下：
- 任务并行执行;
- 数据分布式存储(本地化);
- 分布式计算;
- 私有资源;
- 横向扩展;
-  Shared Nothing架构，不共享资源

## 2016-04-15 关于ABP、EF、MySQL的实践-有一个新项目，比较合适用ABP开发，但遇到一些问题，这里记录一下如何解决的

[关于ABP-博客园ABP专题](http://www.cnblogs.com/farb/p/ABPTheory.html)      [ABP总体介绍](http://www.cnblogs.com/mienreal/p/4528641.html)  

- 目标：基于现有数据库，通过工具生成DbContext、EF实体和实体映射，因为想生成干净的实体，试过很多方法，最终还是采用CodeSmith达成目标了。
- 数据为中心：因为国内大都是采用数据为中心的开发模式，即项目一上来就是设计数据库，鲜有以模型为中心，采用OO的方式来做分析和设计的.
- Model First：其实采用这种方式可以用Model First的方式，即 数据库->EDMX->T4模析(VS自带)->代码 来生成实体、映射和上下文代码。这种方式生成的实体映射是Data Annotations 的方式(特性来映射)，而不是二次的实体，想自己改T4模板又比较麻烦，T4模板想编辑要装一个VS插件才比较顺手，有智能感应，调试，但是收费的，最终放弃。
- [EF 5.x DbContext Fluent Generator for C#](https://visualstudiogallery.msdn.microsoft.com/5d663b99-ed3b-481d-b7bc-b947d2457e3c/)： 然后狂抓Github,发现一款t4 模板,可以通过EDMX模型文件生成 实体、映射、上下文代码---[EF 5.x DbContext Fluent Generator for C#](https://visualstudiogallery.msdn.microsoft.com/5d663b99-ed3b-481d-b7bc-b947d2457e3c/)坑爹的是这个比较旧了，不支持EF6 和VS2013、2015，然后通过上面的评论看到有人移植到EF6了 [下载地址](http://sdrv.ms/1dN6c5S),弄下来后，vs2013要改下里面的引用的VS版本（VS120COMNTOOLS）,VS2013是12，vs2015是15.一切弄好了，连上数据库（先得装[MYSQL驱动](http://dev.mysql.com/downloads/connector/net/)和[MYSQL FOR VS TOOLS](http://dev.mysql.com/downloads/windows/visualstudio/)）,这套t4模板勉强能用，缺陷就是依赖EDMX，类名和字段名按规则生成需要改模板。最终还是放弃。
- [EF Power tools](https://visualstudiogallery.msdn.microsoft.com/72a60b14-1581-4b9b-89f2-846072eff19d)：然后继续找，发现工具[EF Power tools](https://visualstudiogallery.msdn.microsoft.com/72a60b14-1581-4b9b-89f2-846072eff19d)有个反向工程的功能-通过右键项目->Entity Framework->Reverse Engine Code First->连接MySQL数据(需安装MYSQL驱动和VS工具) 来生成代码（但是不支持VS2015，[在评论中有人已经适配好](http://1drv.ms/1RWxOsb)），但是 无法自定义模板，虽然有另外一个菜单 Customize Reverse Engineer Templates 会生成t4模板到项目中，但还是然并卵，无法直接生成代码(报错，可能是模板的HOST与VS的HOST不一样)，查资料也不找到相关说明，最终还是放弃！
- [EntityFramework Reverse POCO Code First Generator](https://github.com/sjh37/EntityFramework-Reverse-POCO-Code-First-Generator)：继续抓Github，发现一款插件：[EntityFramework Reverse POCO Code First Generator](https://github.com/sjh37/EntityFramework-Reverse-POCO-Code-First-Generator),这个工具挺好的，但是但是 不支持MySQL，只支持MSSQL、SQLCE！坑！看了下代码，发下读取DB Schema是作者自己写的，又重复造轮子了。[于是给提了个问题](https://github.com/sjh37/EntityFramework-Reverse-POCO-Code-First-Generator/issues/26)，不知啥时候才支持其他库,最终放弃。
- [Code Smith](www.codesmithtools.com): 最后突发奇想，看看CodeSmith行不行，一找，我去，CodeSmith果然强大啊，不但能生成，而且支持所有主流数据库，都有源码可以修改，模板也非常好修改（添加注释，添加MYSQL支持，其实原来就支持，只是做了些修整），虽然不是t4,总之是非常的方便。最后最后 最新版还可以破解！爽！Code Smith下载：[CSDN绿色版](http://download.csdn.net/detail/yashua839/8608875),注意，最好去官方下载MSI安装包，在用下载包里面的破解工具激活，亲测试可用（千万要注意不要运行绿色版的程序，运行安装后的程序！），因为还有VS插件，与VS集成好后生成代码非常方便！正好清明假期，研究了下模板，最后成功生成漂亮的代码！模板文件晚些时候传到GitHub上去！CodeSmith在使用的过程中，有个小问题，在配置的地方把某些字段排除后(如ID，因为ID主键和其他通用的属性和映射会放在ABP基类)，会导致ID属性不生成，EF的导航属性生成会受影响！

- 总结：最后，如果能用标准的Code First方式来开发项目，也是非常不错的，这种方式个人觉得需要引入敏捷开发流程，以领域为中心的分析与设计模式，才能执行下去。但是这种方式对开发人员的要求稍高，必须一个经验丰富的Team Leader引导并主导设计过程！理想情况：识别目标、范围、价值、关键干系人->分析主要业务流程->流程需要的所有服务(单步的、组合的，或业务服务、基础设施服务)->从服务中识别领域->分析领域之间的关系->丰富领域属性状态->设计类图->分析领域行为->完整的领域模型(属性、状态、行为)->实体模型 

## 2016-04-15 领域分析方法-即DDD的战术分析
- 1 领域建模项目通常包括以下步骤(业务分析时)：
   - 首先为业务流程建模并文档化。 
   - 选择一个候选的业务流程，与业务领域专家一起使用通用语言来文档化业务流 程。 
   - 识别候选业务流程需要的所有服务。这些服务本质上可以是原子的（单步的） 或组合好的（多步的，有无工作流皆可）。它们也可以是业务（比如承保或资 金）或基础设施（比如电子邮件或工作调度）。对上一步识别的服务所使用的对象，确定并文档化其状态和行为。 一开始关注业务领域核心元素的时候，就将模型保持在高水平是非常重要的。

- 2 真实的 DDD 实现项目和其它软件开发项目所包含的阶段是一 样的。这些阶段包括：
    - 对领域进行建模 ,识别核心领域模型->识别服务(属于三种类型的哪种?)->模型状态(变化及场景)->关联模型(包含和组合)->相关的值对象->细化属性
    - 设计 
    - 开发 
    - 单元测试和集成测试 
    - 基于设计和开发来完善、重构领域模型（模型概念的持续集成（CI））。 
    - 使用更新的领域模型重复上述步骤（领域实现的 CI）。

- 3 业务规则
    - 是业务领域中的重要部分。它们定义了数据验证和其它的约束规则，这些规则 需要应用于特定业务流程场景中的领域对象。业务规则通常分为下面几类：
    - 数据验证
    - 数据转换
    - 商业决策 
    - 流程流向（工作流逻辑）
