# ObjectARX 和 Managed .NET
## ObjectARX：开发人员指南
### ObjectARX 初步概念
#### ObjectARX 概述
ObjectARX® 是 AutoCAD®-运行时扩展编程环境，其中包含了 C++ 库，可以用来开发 AutoCAD 应用程序、扩展 AutoCAD 类和协议，并创建与内置 AutoCAD 命令相同方式运行的新命令。您可以添加新类并将其导出供其他程序使用。您还可以通过在现有 AutoCAD 类中添加函数来在运行时扩展 ObjectARX 协议。

ObjectDBX™ 是 ObjectARX 和 RealDWG® SDK 的基础。

本节定义了这些术语，提供了一些重要的 ObjectARX 和 ObjectDBX 类组的概述，并提供了有关开始使用 ObjectARX 的信息。ObjectARX 开发人员指南假定您熟悉 C++、面向对象编程和 AutoCAD。
##### ObjectARX 编程环境
ObjectARX® 编程环境提供了一个面向对象的C++应用程序编程接口，供开发人员使用、定制和扩展 AutoCAD®。一个 ObjectARX      应用程序是一个动态链接库(DLL)，共享 AutoCAD 的地址空间，并直接调用 AutoCAD 的函数。

ObjectARX 库包括一个多功能的工具集，供应用程序开发人员利用 AutoCAD 的开放式体系结构，直接访问 AutoCAD 数据库结构、图形系统和本地命令定义。此外，这些库还设计为与以下技术相结合使用：

AutoLISP 和 Visual LISP
.NET 框架(仅限Windows)
ActiveX® 自动化和 COM(仅限Windows)
以下术语描述了与 ObjectARX 密切相关的技术：

ObjectDBX™
ObjectARX 的数据库相关子集，包括支持自定义对象和实体。这些 API 不包括与 AutoCAD 编辑器交互或提供用户界面功能的类。

RealDWG®
一款单独授权的 SDK，用于开发使用ObjectDBX在没有AutoCAD的情况下读写DWG和DXF文件的主机应用程序。有关RealDWG SDK的更多信息，请参见autodesk.com开发人员中心。

对象使能器
一个模块，具有.dbx扩展名，使用ObjectARX SDK的ObjectDBX部分定义自定义DWG和DXF数据库对象和实体。对象使能器不依赖于AutoCAD，并且可以在任何RealDWG主机应用程序中加载。

作为开发人员，您可以使用ObjectARX完成以下任务：

访问AutoCAD数据库
与AutoCAD编辑器交互
支持多文档界面(MDI)
创建自定义类
构建复杂应用程序
与其他编程环境交互
使用Microsoft®Foundation Classes(MFC)(仅限Windows)创建用户界面
使用Cocoa(仅限Mac)创建用户界面
###### 访问 AutoCAD 数据库
AutoCAD绘图文件是存储在数据库中的对象集合。这些对象不仅代表图形实体，还包括符号表和字典等内部结构。ObjectARX为您的应用程序提供对这些数据库结构的访问权限。此外，您还可以为特定的应用程序创建新的数据库对象。
###### 与 AutoCAD 编辑器交互
ObjectARX提供了用于与AutoCAD编辑器进行交互的类和成员函数。您可以向AutoCAD注册命令，这些命令将被视为内置命令。您的应用程序可以接收并响应有关AutoCAD内发生的各种事件的通知。
###### 使用 MFC 创建用户界面
ObjectARX 应用程序可以使用与 AutoCAD 共享的动态链接 MFC 库来构建标准的 Microsoft Windows 图形用户界面 (GUI)。
###### 支持 MDI
使用ObjectARX，您可以创建支持AutoCAD多文档界面的应用程序，并确保您的应用程序与Microsoft Windows环境中的其他应用程序正确交互。
###### 创建自定义类
ObjectARX支持开发复杂的应用程序，并提供以下功能：

通知机制：您可以注册以接收关于在AutoCAD中发生的各种事件的通知，从而可以对这些事件做出响应。

事务管理：您可以创建和管理用于修改AutoCAD数据库的事务。此功能可确保在对数据库进行修改时可以回滚，以便恢复到之前的状态。

深度克隆：深度克隆使您能够在数据库中创建实例的完全相同的副本，而不会影响原始实例。

引用编辑：您可以编辑图形对象的引用路径，包括更改其指向的对象，这些对象可以是图形实体，块参照或其他对象。

协议扩展：您可以扩展AutoCAD中的现有对象，以添加自己的自定义功能。

代理对象支持：代理对象是与数据库实体相关联的对象，可用于跨应用程序共享和保护数据的安全。
###### 构建复杂应用程序
您可以利用ObjectARX层次结构中的类来创建自己的自定义类。此外，在创建自定义类时，您可以利用ObjectARX的广泛图形库。
###### 与其他环境交互
ObjectARX提供了托管的包装类，使您可以使用Microsoft .NET Framework并使用其他编程语言（如VB.NET和C#）编写程序。 ObjectARX应用程序可以与其他编程接口进行通信，例如Visual LISP，ActiveX® Automation和COM。此外，ObjectARX应用程序可以与Internet进行交互，通过将URL与实体关联，以及从Web加载和保存绘图文件。
###### 保护 ObjectARX 应用程序的安全性
网络安全攻击是知识产权和生产力损失的主要原因之一。

自2013年发布产品以来，Autodesk一直在投资于加强和保护基于AutoCAD的产品，通过引入以下功能和其他功能来实现：

安全模式-限制自定义应用程序的加载
可信的应用程序位置和域-限制AutoCAD基于产品可以加载自定义应用程序的位置
支持并验证数字签名应用程序-确定编写/发布自定义应用程序的公司以及文件是否在发布后被修改
在开发过程中扫描易受攻击的模块-在产品发布之前进行检查，以验证是否使用了最新版本的开发库
为了真正保护基于AutoCAD的应用程序，必须保护所有入口点，包括自定义和第三方应用程序。您应执行以下任务以帮助确保您编写和分发的应用程序安全：

使用与安全相关的编译器标志
/GS-为应用程序启用堆栈缓冲区溢出检测功能，以帮助最小化外壳代码尝试利用缓冲区溢出。
/NXCOMPAT-启用Windows数据执行预防功能，使数据难以执行。
/DYNAMICBASE-启用地址空间布局随机化（ASLR）的使用，该功能会生成一个可执行图像，在加载时可以进行随机重定位。
/SAFESEH-为32位可执行文件启用异常处理程序保护。只分派PE头中列出地址的异常处理程序。
/SDL-启用安全开发生命周期（SDL）检查，其中包括额外的安全代码生成功能和额外的安全相关警告。
添加#define _SDL_BANNED_RECOMMENDED
包括banned.h
支持结构化异常处理程序重写保护（SEHOP）-每个可执行文件（EXE）注册表条目，可帮助防止异常链破坏，而无需重建EXE文件
对所有可执行文件（DLL / EXE / JS / ...）进行数字签名
在使用输入之前验证任何输入
使用HTTPS协议访问网络上的信息
在使用第三方和开源库时，请确保应用程序使用的是最新版本，并且库正在维护中
使用内置于Microsoft Visual Studio或第三方实用程序（例如Micro Focus DevPartner for Visual C++ / BoundsChecker Suite和TeamBLUE PurifyPlus）检查任何内存泄漏
测试您的应用程序，以确保它们使用以下设置的默认值正常工作：
LEGACYCODESEARCH = 0-控制是否在搜索可执行文件时包括程序启动的文件夹。
SECURELOAD = 1-控制AutoCAD是否基于它们是否在受信任的文件夹中加载可执行文件。
