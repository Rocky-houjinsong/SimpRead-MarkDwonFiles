> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [learn.microsoft.com](https://learn.microsoft.com/zh-cn/powershell/scripting/samples/viewing-object-structure--get-member-?view=powershell-7.3)

> Get-Member 是一种功能强大的工具，借助它可查看 PowerShell 中对象的类型和结构。

1.  [Learn](https://learn.microsoft.com/zh-cn/?view=powershell-7.3)
2.  [PowerShell](https://learn.microsoft.com/zh-cn/powershell?view=powershell-7.3)
3.  [脚本编写](https://learn.microsoft.com/zh-cn/powershell/scripting/?view=powershell-7.3)

1.  [Learn](https://learn.microsoft.com/zh-cn/?view=powershell-7.3)
2.  [PowerShell](https://learn.microsoft.com/zh-cn/powershell?view=powershell-7.3)
3.  [脚本编写](https://learn.microsoft.com/zh-cn/powershell/scripting/?view=powershell-7.3)

使用英语阅读 Added 目录 使用英语阅读 Added 打印 Twitter LinkedIn Facebook 电子邮件 目录

查看对象结构
======

*   项目
*   2023/02/07
*   3 个参与者

反馈

本文内容
----

由于对象在 PowerShell 中扮演了如此重要的角色，因此存在几个用于处理任意对象类型的本机命令。 最重要的一个是 `Get-Member` 命令。

分析命令返回的对象的最简单方法是通过管道将该命令的输出传递到 `Get-Member` cmdlet。 `Get-Member` cmdlet 向你显示对象类型的正式名称及其成员的完整列表。 有时返回的元素数目可能非常巨大。 例如，一个进程对象可以拥有 100 多个成员。

使用以下命令，可以通过输出查看 Process 对象和页面的所有成员。

PowerShell 复制

```
Get-Process | Get-Member | Out-Host -Paging
```

Output 复制

```
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

我们可以通过筛选想要查看的元素，让这个冗长的信息列表更易于使用。 `Get-Member` 命令仅允许你列出属性成员。 属性的形式有数种。 cmdlet 使用值为 `Properties` 的 MemberType 参数显示类型的属性。 生成的列表仍会很长，但较之前更易于管理：

PowerShell 复制

```
Get-Process | Get-Member -MemberType Properties
```

Output 复制

```
TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

备注

MemberType 的允许值有 AliasProperty、CodeProperty、Property、NoteProperty、ScriptProperty、Properties、PropertySet、Method、CodeMethod、ScriptMethod、Methods、ParameterizedProperty、MemberSet 以及 All。

一个进程有 60 多个属性。 默认情况下，PowerShell 使用存储在以 `.format.ps1xml` 结尾的 XML 文件中的信息来决定某种对象类型的显示方式。 进程对象的格式设置定义存储在 `DotNetTypes.format.ps1xml` 中。

如果需要查看 PowerShell 默认显示的属性之外的属性，可使用 `Format-*` cmdlet 对输出进行格式设置。

* * *

建议的内容
-----

*   [
    
    ### 直接操作项 - PowerShell
    
    ](/zh-cn/powershell/scripting/samples/manipulating-items-directly?source=recommendations)
    
    PowerShell 提供了多个 cmdlet，可帮助管理本地和远程计算机上的项。 项是由 PowerShell 提供程序公开的对象，如文件系统、注册表、证书等。
    
*   [
    
    ### Windows PowerShell 语言规范 3.0 - PowerShell
    
    ](/zh-cn/powershell/scripting/lang-spec/chapter-01?source=recommendations)
    
    此语言规范描述 PowerShell 语言的语法、语义和行为。
    
*   [
    
    ### 格式设置, 别名, 提供程序, 比较 - PowerShell
    
    ](/zh-cn/powershell/scripting/learn/ps101/05-formatting-aliases-providers-comparison?source=recommendations)
    
    本章介绍输出格式设置、命令别名、提供程序和比较操作的概念。
    
*   [
    
    ### 附录 A - 帮助语法 - PowerShell
    
    ](/zh-cn/powershell/scripting/learn/ps101/appendix-a?source=recommendations)
    
    本文介绍如何阅读和理解 Get-Help 提供的 cmdlet 的语法。
    
*   [
    
    ### 流量控制 - PowerShell
    
    ](/zh-cn/powershell/scripting/learn/ps101/06-flow-control?source=recommendations)
    
    PowerShell 提供了一些方法，用于创建循环、制定决策以及以逻辑方式控制脚本中的代码流。
    
*   [
    
    ### 准确描述和管道 - PowerShell
    
    ](/zh-cn/powershell/scripting/learn/ps101/04-pipelines?source=recommendations)
    
    PowerShell 单行命令是一个用于完成单个任务的连续管道，其中包含多个命令。
    
*   [
    
    ### 脚本模块 - PowerShell
    
    ](/zh-cn/powershell/scripting/learn/ps101/10-script-modules?source=recommendations)
    
    脚本模块是将脚本和函数打包为可重复使用的工具的一种简单方法。
    
*   [
    
    ### 词法结构 - PowerShell
    
    ](/zh-cn/powershell/scripting/lang-spec/chapter-02?source=recommendations)
    
    本规范使用词法文法和句法文法介绍 PowerShell 语言的语法。
    

显示更多

* * *

其他资源
----

[中文 (简体)](/zh-cn/locale?target=https://learn.microsoft.com/zh-cn/powershell/scripting/samples/viewing-object-structure--get-member-?view=powershell-7.3) 主题

*   亮
*   暗
*   高对比度

*   管理 Cookie
*   [早期版本](/zh-cn/previous-versions/)
*   [博客](https://techcommunity.microsoft.com/t5/microsoft-learn-blog/bg-p/MicrosoftLearnBlog)
*   [参与](/zh-cn/contribute/)
*   [隐私](https://go.microsoft.com/fwlink/?LinkId=521839)
*   [使用条款](/zh-cn/legal/termsofuse)
*   [商标](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/EN-US.aspx)
*   © Microsoft 2023