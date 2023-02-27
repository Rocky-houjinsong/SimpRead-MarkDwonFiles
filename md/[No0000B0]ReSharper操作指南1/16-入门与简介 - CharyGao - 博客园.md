> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.cnblogs.com](https://www.cnblogs.com/Chary/p/No0000B0.html)

> 安装指南 在安装之前，您可能需要检查系统要求。 ReSharper是一个VisualStudio扩展。它支持VisualStudio2010,2012,2013,2015和2017.安装完成后，您将在

**安装指南**

在安装之前，您可能需要检查系统要求。

ReSharper 是一个 VisualStudio 扩展。它支持 VisualStudio2010,2012,2013,2015 和 2017. 安装完成后，您将在 VisualStudio 的主菜单中找到新的 **ReSharper** 条目。大多数 ReSharper 命令都可以在这个菜单中找到。但是，许多功能都集成在编辑器，解决方案资源管理器和其他 VisualStudio 窗口中。大多数 ReSharper 命令也可以通过[键盘快捷键进行操作](https://www.jetbrains.com/help/resharper/2017.3/Reference__Keyboard_Shortcuts.html)。

从 ReSharper9.0 开始，所有 JetBrains.NET 产品都作为 ReSharperUltimate 在统一安装程序中提供。在安装程序中，您可以选择要安装和更新的产品。只需点击几下鼠标即可完成新的安装。但是，如果您从以前的版本升级（特别是版本 8.2 或更低版本），则某些细节可能不明显。默认情况下，JetBrains.NET 产品已安装到[当前的用户配置文件中](https://www.jetbrains.com/help/resharper/2017.3/Installation_Guide.html?keymap=vs)，但您也可以[为所有用户](https://www.jetbrains.com/help/resharper/2017.3/Installation_Guide.html?keymap=vs)安装特定的工具配置。本主题将帮助您简化安装过程。

处理以前的版本
-------

ReSharper 不允许你在同一台机器上的 VisualStudio 版本中安装不同的版本。但是，可以在不同的 VisualStudio 版本中安装几个不同的版本。

同样重要的是要注意，如果您安装多个 JetBrainsdotNet 产品，某些版本可能不兼容。例如，在同一个 VisualStudio 版本中安装 ReSharper9.0 和 dotTrace5.0 是不可能的。例如，如果您有 ReSharper8.2 和 dotCover2.5，然后决定在相同的 VisualStudio 版本中将 dotCover 升级到版本 3.0，则安装程序不仅会删除 dotCover2.5，还会删除 ReSharper8.2。

如果您的计算机上安装了先前版本的 ReSharper，安装程序将自动删除冲突版本（以前在同一 VisualStudio 版本中安装）。如有必要，安装程序还可以删除无冲突的版本。

如果安装程序检测到任何 JetBrainsdotNet 产品的先前安装，则**显示详细信息**链接将出现在安装程序窗口的右上角。点击此链接检查现有版本并查看安装程序将如何处理它们。

例如，在下面的插图中，只有一个版本冲突。ReSharper9.0 没有冲突，因为它安装在 VisualStudio2013 中，而当前安装的目标是 VisualStudio2012 和 2015. 在 VisualStudio2012 和 2015 中的以前安装应该被删除，因此 **Skip** 旁边的选项被禁用。

![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161059542-1110595788.png)

执行自定义安装
-------

*   运行安装程序文件。
*   点击**选项**在安装程序对话框的底部。
*   在安装向导的此页面上，单击**重新启动**。安装程序将以提升的权限重新启动。
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161103402-332401440.png)
*   安装程序重新启动后，再次单击**选项**。
*   选择**管理模式**或**所有用户**复选框，然后单击**返回**。
*   阅读并接受许可协议，然后单击**下一步**。
*   如果您选择了**所有用户**模式，则所选产品将安装到 " 程序文件 " 文件夹中。
*   如果您选择了**管理**模式，则在打开的向导页面上，您将能够复制其中一个安装命令，或者单击**计划安装**以准备将机器范围的安装安装到当前计算机上的用户配置文件。
    
    安装目录
    ----
    
    从 ReSharper9.0，dotCover3.0，dotTrace6.0 和 dotPeek1.3 开始，JetBrainsdotNet 产品默认安装在以下目录中：
    
    _％LOCALAPPDATA％\JetBrains 公司 \ 安装_
    
    如果您已经使用 All 用户模式安装了 ReSharper，安装目录是：
    
    _％PROGRAMFILES（x86）％__\JetBrains\Installations_for64 位系统和  
    _％PROGRAMFILES％__\JetBrains\Installations_for32 位系统。
    
    安装到 VisualStudio 实验实例中的产品目录将实验实例名称作为后缀。
    
    第一步
    ===
    
    ReSharper 是一款以键盘为中心的产品。它的大部分操作都具有默认的键盘快捷方式，如有必要，您可以为其任何命令分配自定义快捷方式。
    
    因此，当 ReSharper 准备就绪时，它会提示您选择[两种默认键盘快捷方式之一](https://www.jetbrains.com/help/resharper/2017.3/Reference__Keyboard_Shortcuts.html)：
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161103574-323333822.png)
    
    在学习此帮助时，请使用帮助页面顶部的**快捷方式**选择器根据您的首选快捷方式在文本中显示快捷方式。
    
    Environment|Keyboard&Menus 设置；
    
    有关更多信息，请参阅[配置键盘快捷键](https://www.jetbrains.com/help/resharper/2017.3/Configuring_Keyboard_Shortcuts.html)
    
    快速入门
    ----
    
    在 VisualStudio 中安装 ReSharper 时，您将看到以下更改：
    
*   出现在 VisualStudio 菜单栏中的 **ReSharper** 菜单包含除了仅在上下文中可用的所有命令，例如[上下文操作](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Context_Actions.html)或[快速修复](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Quick-Fixes.html)。
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161103714-409512079.png)
*   请注意，仅当 JetBrainsdotCover 和 JetBrainsdotTrace 与 ReSharper 一起安装时，**Cover** 和 **Profile** 子菜单才会出现。
*   特定命令之后出现的许多[工具窗口](https://www.jetbrains.com/help/resharper/2017.3/Reference__Windows.html)。所有 ReSharper 工具窗口在 **ReSharper|Windows** **设置**。
*   ReSharper 的命令在编辑器，解决方案资源管理器和其他 VisualStudio 窗口的上下文菜单中可用。  
    请注意，默认情况下，ReSharper 还会在这些菜单中隐藏重写的 VisualStudio 项目（例如重构和导航命令）。如果要保留原始的 VisualStudio 菜单项，请清除 **HideoverriddenVisualStudiomenuitems，在 Environment|Keyboard&Menus** **设置**。
*   [VisualStudio 选项](https://www.jetbrains.com/help/resharper/2017.3/Reference__VS_Options_Page.html)，允许您随时暂停和恢复 ReSharper。通常情况下，你不需要这样做。但是，如果在处理大型解决方案时遇到性能问题，暂停 ReSharper 可能有助于提高性能。
    
    在 VisualStudio 选项中，您可以将快捷方式绑定到该 **ReSharper_ToggleSuspended** 命令，并使用此快捷方式快速挂起 / 恢复 ReSharper。
    
*   编辑器和状态栏中的很多变化：
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161104324-738730024.png)
*   [状态指示器](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Status_Indicator.html)可帮助您立即查看当前文件是否有错误或警告。
*   修复弹出窗口显示为非导入类型。按下 Alt+Enter 或单击此弹出窗口就足够了，ReSharper 会为文件中的所有类型添加缺少的指令。有关更多信息，请参阅[导入缺少命名空间](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Importing_Namespaces.html)。
*   低优先级代码问题（在这种情况下，与未使用的公共成员相关的建议）呈灰色。
*   一个中等优先级的代码问题（在这种情况下，符号名称不符合命名风格的警告）用蓝色下划线突出显示。
*   对应于建议问题（3）的[标记栏上](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Status_Indicator.html)。
*   在标记栏上显示与错误问题（8）对应的标记。
*   如果 ReSharper 有任何建议，可以在插入符号的左侧出现一个[动作指示符](https://www.jetbrains.com/help/resharper/2017.3/Actions_List.html)。
*   高优先级代码问题（在这种情况下，与未解决的符号和不正确的返回类型有关的错误）用红色文本和红色下划线突出显示。
*   标记栏上显示与警告问题（4）相对应的标记。
*   通过按下或点击动作指示器（7）打开的[动作列表](https://www.jetbrains.com/help/resharper/2017.3/Actions_List.html) Alt+Enter 包含针对该问题的[快速修正](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Quick-Fixes.html)列表。
*   状态栏中会显示插入符号处的问题简短说明。您也可以将鼠标悬停在突出显示的代码上或标记栏上的问题标记上查看代码问题的说明（5,6,9）
*   如果启用了[解决方案范围分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis.html)，则 ReSharper 允许您查看更多代码问题。在这个例子中，它检测到未使用的公共成员（3）并通知解决方案的其他文件中的错误。您可以单击解决方案范围的分析图标来浏览检测到的问题。
*   您也可以使用**快速启动**框查找并执行 ReSharper 命令：
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161104496-286836058.png)
    
    浏览和搜索
    -----
    
    ReSharper 提供了很多[导航和搜索功能](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Index.html)。
    
    ### 跳到声明
    
    按下 Ctrl 键并将鼠标悬停在代码上。你会看到在其他地方定义的所有符号在聚焦时都会被加下划线。您可以在按住 Ctrl 键的同时单击任何符号直接导航到其声明。如果符号是在当前解决方案中定义的，则 ReSharper 会打开相应的文件并将该插入符号添加到声明中。如果符号是在编译的库中定义的，则 ReSharper 根据您的[首选项](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigating_to_External_Sources.html)打开它。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161104621-672046009.png)
    
    有关更多信息，请参阅[转到声明](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Declaration.html)。
    
    ### 寻找用法
    
    要以相反方向导航，即查找使用符号的解决方案中的所有位置，请按 Shift+F12。ReSharper 将快速查找并显示符号的所有用法。有关更多信息，请参见[查找用法](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages.html)。
    
    ### 检查可用的导航操作
    
    另一个方便的导航快捷方式是 Alt+`。当您在任何符号上按下它时，ReSharper 会向您显示所有可用的导航选项：
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161104808-712572501.png)
    
    有关更多信息，请参阅[导航至](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigate_from_Here.html)。
    
    ### 在解决方案中找到任何东西
    
    如果您需要在解决方案中找到任何内容，请按 Ctrl+T。只要您调用此功能，就会立即显示建议列表，并且最初包含您最近的文件和导航项目。您可以开始输入以查找类型，符号，文件，最近的编辑，最近的文件和最近查看的方法。有关更多信息，请参阅[全部](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Type.html) / 类型。
    
    ### 在解决方案树中查找当前文件
    
    当导航命令将您带入新文件时，您可能想要查看它在解决方案资源管理器中的位置。只需按下 Shift+Alt+L，解决方案资源管理器就会滚动到当前文件并突出显示它。有关更多信息，请参阅[在](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Locating_a_File_in_Solution_Explorer.html) Solution/AssemblyExplorer 中查找当前文档
    
    在编辑器中编码
    -------
    
    当你在编辑器中工作时，一大堆[代码编辑助手](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Index.html)就在你的手中。这里有几个。
    
    ### 代码完成（IntelliSense）
    
    所有完成功能都支持 CamelHumps- 也就是说，您只需输入大写字母即可完成任何项目。
    
    ReSharper 以更高级的功能补充和扩展了 VisualStudio 的本地代码完成（IntelliSense）。例如，它会根据您的输入缩小建议列表的范围，自动导入选定的类型和扩展方法，在完成方法名称时添加括号，根据类型指定变量和字段名称等等。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161104980-1887002040.png)
    
    如有必要，您可以通过 **Environment|IntelliSense|General** 设置，始终返回到本机 VisualStudio 智能感知。
    
    无论您喜欢自动完成，您都可以在您键入内容之后，或者甚至不用键入，就可以显式调用 ReSharper 的代码完成功能：只要允许任何有意义的代码：
    
    所有 ReSharper 完成快捷方式都可以连续按几次。在这种情况下，ReSharper 在完成列表中增加了更多的建议。有关更多信息，请参阅 DoubleCompletion
    
*   按下 Ctrl+Alt+Space 调用[智能完成](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Code_Completion__Smart.html)，根据表达式的预期类型提供更多智能建议。
*   按将 Shift+Alt+Space 调用[导入符号完成](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Code_Completion__Type_Name.html)，该显示与给定前缀匹配的所有类型，而不管它们属于哪个名称空间，还会在必要时向当前文件插入适当的名称空间导入指令。
    
    ### 选择和移动代码块
    
    无论您身处何处，请尝试按 Ctrl+Alt+Right/Ctrl+Alt+Left。这些快捷方式允许您连续选择符号，行或代码块，以便您可以轻松地选择任何所需的表达式进行复制，剪切或移动。有关更多信息，请参阅[延长](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Extend_Shrink_Selection.html) / 缩小选择。
    
    如果您需要移动选定的代码块，请按 Ctrl+Shift+Alt，然后使用箭头键将该块移到任何允许的位置。有关更多信息，请参阅[重新排列代码元素](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Moving_Code_Elements.html)
    
    Alt+Enter
    ---------
    
    很多时候，您会在编辑器的左侧看到许多不同的[动作指示器](https://www.jetbrains.com/help/resharper/2017.3/Actions_List.html)中的一个。您可以按下 Alt+Enter 查看 ReSharper 在当前插入位置所建议的内容：
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161105308-1157836715.png)
    
*   如果您看到红色灯泡![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161105730-777716776.png)或黄色灯泡![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106105-1729609349.png)图标，甚至建议按下，Alt+Enter 因为[这些动作指示器](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Quick-Fixes.html)告诉您 ReSharper 检测到错误或其他代码问题，并且知道如何解决该问题。
*   如果你看到一个锤子![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106511-940592956.png)图标，除非你想修改插入符号，否则你可以忽略它。如果您想进行更改，按下 Alt+Enter 可能会有所帮助。ReSharper 的提供[数百个](https://www.jetbrains.com/help/resharper/2017.3/Reference__Options__Languages__CSharp__Context_Actions.html)的[情况下行动](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Context_Actions.html)能，例如，快速改变符号可见，添加遍历集合，和更多的代码。
*   Alt+Enter 如果没有行动指标，您也可以按下。在这种情况下，您可以开始键入以快速[查找并执行](https://www.jetbrains.com/help/resharper/2017.3/Navigating_to_Action.html)任何 ReSharper 操作。
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106636-1384739232.png)
    
    重构代码
    ----
    
    ReSharper 的[重构](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Index.html)集远远超过了 VisualStudio 提供的关于数量，可用性和应用范围。
    
    学习和记住 ReSharper 提供的几十次重构并不容易。但是，您可以按 Ctrl+Shift+R 代码中的任何符号，然后查看哪些重构可用。
    
    生成代码
    ----
    
    ReSharper 可以通过提供大量用于自动生成样板代码的功能帮助您专注于不重要的任务。例如，您可以调用一个不存在的方法，ReSharper 会根据使用情况创建此方法，并考虑返回类型和参数类型。
    
    ### 生成类型成员
    
    如果您的脱字符号位于类型声明的任何位置，请按 Alt+Insert。在打开的弹出式菜单中，您可以选择要为类型生成的项目。ReSharper 可以创建构造函数，属性，覆盖成员等等。有关更多信息，请参阅[代码生成](https://www.jetbrains.com/help/resharper/2017.3/Code_Generation__Index.html)。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106746-688223035.png)
    
    ### 应用代码模板
    
    当你要写一个典型的代码块，如'for'或'foreach'循环，一个安全的类型转换，一个断言等，按下 Ctrl+E,L 并选择相应的活动模板。有关更多信息，请参阅[使用实时模板创建源代码](https://www.jetbrains.com/help/resharper/2017.3/Templates__Applying_Templates__Creating_Source_Code_Using_Live_Templates.html)。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106855-587156990.png)
    
    使用类似的技术，可以用典型的代码结构包围现有的代码块，如'if...else'，'try...catch'等。在这种情况下，按 Ctrl+E,U 或 Alt+Enter 选择。有关更多信息，请参阅[使用模板围绕代码片段](https://www.jetbrains.com/help/resharper/2017.3/Templates__Applying_Templates__Surrounding_Code_Fragments_with_Templates.html)。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161106980-1643734454.png)
    
    如果您发现 ReSharper 的代码模板有用，您可能也有兴趣[添加新的表单模板文件](https://www.jetbrains.com/help/resharper/2017.3/Templates__Applying_Templates__Creating_Files_from_Templates.html)并[创建您自己的代码模板](https://www.jetbrains.com/help/resharper/2017.3/Templates__Creating_and_Editing_Templates.html)。
    
    代码风格很重要
    -------
    
    使用 ReSharper，您可以控制代码中的大多数样式方面：[命名标准](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Naming_Style.html)，[格式化规则](https://www.jetbrains.com/help/resharper/2017.3/Enforcing_Code_Formatting_Rules.html)，[文件和类型布局](https://www.jetbrains.com/help/resharper/2017.3/File_and_Type_Layout.html)，[文件标题样式](https://www.jetbrains.com/help/resharper/2017.3/File_Header_Style.html)以及许多其他小事情（例如[修饰符的顺序](https://www.jetbrains.com/help/resharper/2017.3/Modifiers_Style.html)或[是否使用](https://www.jetbrains.com/help/resharper/2017.3/Using_var_Keyword_in_Declarations.html)'var'关键字）。
    
    ReSharper 代码样式功能的默认值是根据 Microsoft 准则和众多最佳实践选择的。同时，代码风格的每个微小方面都可以改变，以适应您的个人或企业偏好。
    
    要应用代码样式规则，请按 Ctrl+E,C。ReSharper 会提示您选择两个默认[代码清理](https://www.jetbrains.com/help/resharper/2017.3/Code_Cleanup__Index.html)配置文件之一：重新设置代码的格式或在选定范围内应用多个代码样式规则。
    
    下一步
    ---
    
    您可以查看 GitHub 上的 ReSharperWorkshop。这是一个 VisualStudio 解决方案，为导航，编辑，检查，重构等提供了一步一步的代码练习。
    
    快速启动技巧
    ======
    
    您可以使用交互式教程（**ReSharper|Help|Tutorials**）开始使用 ReSharper 的功能，或者熟悉新版本中的功能。
    
    外观和感觉
    -----
    
*   您可以更改 ReSharper 带入 VisualStudio 编辑器的所有颜色。转到 **Tools|Options|Environment|FontsandColors** 并查找以 **ReSharper**。开头的项目。
*   您可以更改 ReSharper 键盘绑定以进行任何操作：转到 **Tools|Options|Environment|Keyboard** 和查找项目 **ReSharper**。
*   在 VisualStudio2012 和更高版本中，您可以使用[快速启动](https://blogs.msdn.microsoft.com/cdnstudents/2013/12/16/visual-studio-tips-and-tricks-quick-launch-where-was-that-optionmenu-item/)功能来搜索和执行 ReSharper 命令。
*   在编辑器中，按 Alt+Enter，然后开始键入要执行的 ReSharper 命令的名称（[更多](https://www.jetbrains.com/help/resharper/2017.3/Navigating_to_Action.html)...）。
*   试图学习 ReSharper 快捷键？首先，确定[两个默认快捷方式中的](https://www.jetbrains.com/help/resharper/2017.3/Reference__Keyboard_Shortcuts.html)哪一个对您更方便。然后，使用此页面右上角的选择器切换帮助中的快捷方式; 或下载并打印 PDF 版本的 VisualStudio 方案或 ReSharper2.x/IntelliJIDEA 方案。
    
    在编辑器中编码
    -------
    
*   只要您键入方法签名，例如 **publicvoidFoo(stringinput** 按下 Ctrl+Shift+Enter 即可插入应遵循的所有语法元素，并进入可继续输入的位置（[更多](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Complete_Statement.html)...）。
*   你想围绕一些代码 **try...catch**？[选择一个逻辑代码块](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Extend_Shrink_Selection.html)用 Ctrl+Alt+Right，按 Alt+Enter，然后选择下一个模板**的环绕****...**。
*   您可以选择一个代码块并使用 Ctrl+Shift+Alt+ 箭头键移动该块（[更多](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Moving_Code_Elements.html)...）。
*   您可以查看最近的剪贴板条目，Ctrl+Shift+V 然后选择要粘贴的条目（[更多](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Multiple_Entries_Clipboard.html)...）。
*   如果您打开[参数信息弹出窗口](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Parameter_Info.html)（Ctrl+Shift+Space），则可以使用 Ctrl+Shift+Space/Ctrl+Shift+Alt+Space 跳转到下一个 / 上一个签名。
*   枚举完成将自动插入 Enum 类型作为前缀。不需要拼出来！
*   枚举完成是由 CamelHumps 驱动的。尝试打字 **StringComparisonc=oic**。
*   使用 **String.Format**，您可以在光标位置添加占位符。只需点击 Alt+Enter 并选择**插入格式参数**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__String_Formatting_Methods.html)...）。
*   如果字符串文字太长，点击 Enter 并且 ReSharper 会自动将它的一部分放到下一行并插入 **+** 符号。删除 **+** 和字符串部分将重新合并（[更多](https://www.jetbrains.com/help/resharper/2017.3/Splitting_Lines_with_String_Literals.html)...）。
*   使用剪切 / 粘贴将属性移动 3 行？有一种更简单的方法：将光标放在属性上，按下 Ctrl+Shift+Alt 并使用向上箭头键。
*   查看其他[打字辅助功能](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance_Typing_Assistance.html)。
    
    分析代码
    ----
    
*   甚至在运行代码之前使用 [NotNull] 和 [CanBeNull] 属性可以帮助您找到 **NullReferenceException**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Detect_possible_NullReferenceExceptions.html)...）。
*   右键单击解决方案资源管理器中的文件，项目，解决方案文件夹或整个解决方案，然后选择**查找代码问题**以查看所选项目的错误，警告和建议（[更多](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)...）。
*   困扰突出的代码问题？Alt+Enter 在突出显示的代码处按下并选择**检查** **[检查名称]**，然后您可以选择[使用注释或属性](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)来[抑制问题，](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)或者[禁用相应的代码检查](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)。
*   您可以[使用单个注释](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)标记代码来[抑制所有检查](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html) - 标记代码与 **//ReSharperdisableAll**ReSharper 不会抱怨什么，直到它符合相应的 **//ReSharperrestoreAll**。
*   ReSharper 的[解决方案范围分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis__Solution-Wide_Code_Inspections.html)解决了可见性问题：您会看到是否在组件外部使用内部成员，并且永远不会错过单个未使用的非私有成员。
*   您可以在 **ReSharper|** **中的**代码分析中[通过掩码排除文件](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)**选项** **| 代码检查 | 设置 |** **跳过的元素**。
*   按 / 可以[转到文件中的下一个](https://www.jetbrains.com/help/resharper/2017.3/Design_time_Inspection.html) / 上一个代码问题。Alt+PageDownAlt+PageUp
*   要在您的解决方案中查找所有可本地化的字符串，请在相关项目的属性中设置 **Localizable=Yes** 和 **LocalizableInspection=Pessimistic**，然后找到任何此类 sting，用下划线突出显示，按下 Alt+Enter 并选择 **Inspection'ElementisLocalizable'|** **查找类似的问题**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Localization_Inspection.html)...）。
    
    遍历代码
    ----
    
*   您可以按 Ctrl+T 快速查找类型，方法或基本[所有内容](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Type.html)，同时 Ctrl+Shift+T 让您找到[文件](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_File.html)。
*   将您的光标放在 **using**（或者 **import** 如果您使用 VB.NET）指令并按下 Shift+F12。ReSharper 将显示这个命名空间的使用位置（[查找符号的用法](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages__Finding_Usages_of_a_Symbol.html)）。
*   忘记你刚才在编辑的地方？[转到最后编辑位置](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigating_to_Recent_Locations.html)用 Ctrl+Shift+Backspace。
*   想要定位[当前符号的](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Declaration.html)真实位置？按 F12 或右键单击该符号。
*   [转到包含声明](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Containing_Declaration.html)（Ctrl+[）可与被用于 Shift 以[选择整个声明](https://www.jetbrains.com/help/resharper/2017.3/Selecting_Containing_Declarations.html)
*   在定位 **CustomerServicesTest** 使用 Ctrl+T 或任何其他[导航命令时](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Search.html)，您不需要键入整个事物。只需使用 CamelHumps 并键入 **cst**。
*   Alt+Home 将您[引导](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Inheritor.html)至[基本类型](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Base.html)并将 Alt+End 您[引导](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Inheritor.html)至当前类型的[继承者](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Inheritor.html)。
*   你想转到班级中的下一个成员吗？Alt+Down 会带你到那里;Alt+Up 会带你回来（[更多](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Next_Previous_Member.html)...）。
*   搜索任何东西（[用法](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages__Finding_Usages_of_a_Symbol.html)，[实现](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Implementation.html)，[范围外部的代码](https://www.jetbrains.com/help/resharper/2017.3/Finding_Usages_of_External_Symbols.html)等）都会提取到[查找结果窗口](https://www.jetbrains.com/help/resharper/2017.3/Reference__Windows__Find_Results_Window.html)。然后使用它在搜索结果与 F8/Shift+F8（more...）之间导航。
*   在源代码中，Shift+Alt+L 在解决方案资源管理器中选择当前文件; 在反编译的源代码中，它会打开关注当前类型的 AssemblyExplorer 窗口（[更多](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Locating_a_File_in_Solution_Explorer.html)...）。
*   要[浏览](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigating_to_Exception.html)当前在剪贴板中[的堆栈跟踪](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigating_to_Exception.html)，只需按 Ctrl+E,T。
*   开始在 ReSharper 工具窗口中输入，内容将缩小到匹配的项目。CamelHumps 匹配工作在那里。
*   使用 GoToFile（Ctrl+Shift+T）在解决方案资源管理器中查找特定项目 - 只需选择一个_.csproj_ 文件。
*   在查找类型时 Ctrl+T，可以使用通配符。想要所有的 ViewModels？键入 ***ViewModel**（more...）。
    
    转换代码
    ----
    
*   您可以在 **ReSharper|** **中**定义要使用的[上下文操作](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Context_Actions.html)**选项** **| 代码编辑 |[语言]|** **上下文操作**。
*   你在同一个文件中有多个类吗？快速修复它。按下 Ctrl+Shift+R 解决方案资源管理器中的文件，然后选择**将类型移入匹配文件**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Move_Types_into_Matching_Files.html)...）。
*   随时随地[重命名](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Rename.html)任何东西 Ctrl+R,R。即使用更少的步骤也可以做到 - 只需输入一个新名称并点击即可 Alt+Enter。
*   您可以使用一段代码[提取方法](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Extract_Method.html) Ctrl+R,M。
*   想要将字符串文字移动到资源文件？按 Ctrl+Shift+R 字符串上的任意位置并选择**移动到资源**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Resources__Refactorings__Move_to_Resource.html)...）。
*   输入新的方法签名（更改参数的数量或类型，更改返回类型），签名用灰色框突出显示时，点击 Alt+Enter 应用[更改签名重构](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Change_Signature.html)。
*   把你的光标放在一个属性上，你可以按 Alt+Enter 它将它从自动属性改变为具有后台字段的属性，反之亦然（[更多](https://www.jetbrains.com/help/resharper/2017.3/Using_Auto_Properties.html)...）。
*   按 Ctrl+R,S 以[更改签名](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Change_Signature.html)的方法，看到一个预览应用之前。ReSharper 会完成剩下的工作！
*   认为你的代码需要一个很好的清洗？使用 Ctrl+E,C 并运行**完整清理**配置文件（[更多](https://www.jetbrains.com/help/resharper/2017.3/Code_Cleanup__Index.html)...）。
    
    生成代码
    ----
    
*   使用 Generate 命令（Alt+Insert）在几秒钟内生成各种类成员。
*   您可以通过 **ReSharper|** 将版权标题添加到所有文件**选项** **| 代码编辑 |** **文件头文本**，然后[运行代码清理](https://www.jetbrains.com/help/resharper/2017.3/Code_Cleanup__Index.html)整个解决方案（[更多](https://www.jetbrains.com/help/resharper/2017.3/File_Header_Style.html)...）。
*   Alt+Insert 在解决方案资源管理器可以从您的[文件模板](https://www.jetbrains.com/help/resharper/2017.3/Reference__Templates_Explorer__File_Templates.html)创建文件.. 和文件夹。
*   输入 **class** 并点击 TAB。默认情况下需要公开还是内部？更改[相应的实时模板](https://www.jetbrains.com/help/resharper/2017.3/Reference__Templates_Explorer__Live_Templates_CSHARP.html)（[更多](https://www.jetbrains.com/help/resharper/2017.3/Templates__Creating_and_Editing_Templates__Editing_a_Template.html)...）。
*   您可以将任何[成员生成命令](https://www.jetbrains.com/help/resharper/2017.3/Generating_Type_Members.html)绑定到其自己的快捷方式。转到**工具** **| 选项 | 环境 |** **键盘**并查找以开头的命令 **ReSharper_Generate**。
*   使用 Alt+Insert 并选择 **Generateeventsubscriptions** 在 XAML/ASP.NETWebForms/VB.NET 中创建**事件订阅**。
*   如果您将插入符号放在构造函数的参数中并点击 Alt+Enter，ReSharper 可以创建一个字段或属性并为您初始化它。
*   输入 **foreach** 并点击 TAB。ReSharper 将为类型和名称建议（[更多](https://www.jetbrains.com/help/resharper/2017.3/Templates__Applying_Templates__Creating_Source_Code_Using_Live_Templates.html)...）启动[智能循环生成](https://www.jetbrains.com/help/resharper/2017.3/Reference__Templates_Explorer__Live_Templates_CSHARP.html)的[实时模板](https://www.jetbrains.com/help/resharper/2017.3/Reference__Templates_Explorer__Live_Templates_CSHARP.html)。
    
    单元测试
    ----
    
*   使用 Ctrl+U,L 解决方案中的运行所有的单元测试（[更多](https://www.jetbrains.com/help/resharper/2017.3/Unit_Testing_in_Solution.html)...）。
*   想要运行一些特定的测试？在编辑器中选择它们，右键单击并选择**运行单元测试**（[更多](https://www.jetbrains.com/help/resharper/2017.3/Unit_Testing_in_Document.html)...）。
*   开始在[单元测试资源管理器窗口中](https://www.jetbrains.com/help/resharper/2017.3/Reference__Windows__Unit_Test_Explorer.html)输入，按名称过滤测试。
*   在[单元测试会话窗口中](https://www.jetbrains.com/help/resharper/2017.3/Reference__Windows__Unit_Test_Sessions.html)运行时筛选失败的测试，以便在它们通过时看到它们愉快地消失（[更多](https://www.jetbrains.com/help/resharper/2017.3/Using_Unit_Test_Sessions.html)...）。
    
    ASP.NET 和 ASP.NETMVC
    --------------------
    
*   在 ASP.NETMVC 应用程序中，输入 **returnView("** 并按下 Ctrl+Space。智能感知会列出所有可用的视图。
*   键入 **rta** 并按下 TAB。填入控制器，然后填入动作参数。现在它应该按照 IntelliSense 正确的顺序！
*   想要检查 ASP.NETMVC 中丢失的视图吗？打开[解决方案范围的分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis__Enabling_Solution-Wide_Analysis.html)。**View("Login")** 如果 _Login.aspx_ 不存在，将显示为红色。
*   您也可以在 ASPX/Config 文件中使用 " 转到文件成员 " 命令。按下 Alt+\ 并查找它！
*   在 ASPX 页面中，使用[导航到相关文件](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Go_to_Related_Files.html)（CSS，JavaScipt，用户控件等）Ctrl+Alt+F7。
    
    处理不同的语言版本
    =========
    
    随着编程语言的发展，用新的语言特性改进代码是很自然的。另一方面，可能有些因素会阻止您升级到最新的语言版本。
    
    ReSharper 知道不同的语言版本。它[分析代码](https://www.jetbrains.com/help/resharper/2017.3/Finding_Code_Issues.html)并根据当前语言版本应用其自己的功能。每种语言都会自动检测语言版本，但您可以按照以下说明为某些语言手动设置版本。
    
    C＃
    --
    
    ReSharper 完全支持所有 C＃版本，默认情况下，ReSharper 根据关联的编译器自动检测 C＃版本。但是，您可以在 VisualStudio 的 " 属性 " 窗口中使用 **C****＃语言级别**属性（**View|PropertiesWindow**）来显式指定目标 C＃版本。
    
    VB.NET
    ------
    
    ReSharper 完全支持所有 VB.NET 版本，默认情况下，ReSharper 会根据关联的编译器自动检测 VB.NET 版本。但是，您可以通过在**解决方案资源管理器中**选择项目并使用 VisualStudio 的 " 属性 " 窗口中的 **VB.NET** **语言级别**属性（**View|PropertiesWindow**）来显式指定目标 VB.NET 版本。
    
    TypeScript
    ----------
    
    如果 TypeScript 版本是自动检测的（默认情况下是这样），并且在您的解决方案中有几个不同 TypeScript 版本的项目，ReSharper 将使用整个解决方案的最高版本。
    
    ReSharper 完全支持所有 TypeScript 版本。ReSharper**<TypeScriptToolsVersion>** 根据 VisualStudio 项目文件中的属性自动检测 TypeScript 版本。但是您可以使用 **CodeEditing|TypeScript|Inspections** 上的 **TypeScript** **语言级别**选择器明确指定目标 TypeScript 版本
    
    JavaScript 的
    ------------
    
    ReSharper 完全支持 JavaScript 到 ECMAScript，包括实验性功能，如 async/await，指数运算符和对象文字 / 解构 literals/destructuring，rest/spread。jQuery 和 JSX 语法也被支持。
    
    默认情况下，[代码检查](https://www.jetbrains.com/help/resharper/2017.3/ReSharper_by_Language__JavaScript__Code_Analysis_and_Coding_Assistance.html)和其他 ReSharper 功能根据通用支持的 ECMAScript5 标准分析 JavaScript 代码。如果您在项目中使用更高级的 JavaScript 代码，则可以在 **CodeEditing|JavaScript|Inspections**。
    
    C++
    ---
    
    C++ 支持可以通过 ReSharperC++ 获得 - 这是一种专用产品，您可以单独安装，也可以与 ReSharper 或 ReSharperUltimate 一起安装。
    
    ReSharper 支持 C，C++，ReSharper 根据平台工具集（项目属性中的 **General|PlatformToolset**）/std 开关
    
    CSS
    ---
    
    ReSharper 支持 CSS。实际上，CSS 版本远不如由不同 web 浏览器支持的 CSS 功能集重要。因此，ReSharper 可以让您针对特定 Web 浏览器的特定版本调整[其](https://www.jetbrains.com/help/resharper/2017.3/ReSharper_by_Language__CSS__Code_Analysis_and_Coding_Assistance.html) CSS 代码检查。您可以在 **CodeEditing|CSS|Inspections**。
    
    加速 ReSharper（和 VisualStudio）
    ============================
    
    在 VisualStudio 中安装 ReSharper 有两个主要的性能问题源：
    
*   您的系统不符合[要求](https://www.jetbrains.com/resharper/download/system_requirements.html)。在这种情况下，我们建议升级您的系统作为处理问题的第一步。  
    我们经常确保 ReSharper 在现代硬件以及大中型解决方案中都能正常工作，无需任何调整。我们相信 VisualStudio 开发人员正在努力实现同样的目标。  
    通过禁用某些功能来加快 ReSharper 在过时硬件上的速度，您将剥夺自己的优秀工具来加速您的开发性能。
*   VisualStudio 和 ReSharper 共享相同的 32 位进程，将您的系统推向极限。通常情况下，这将在大型解决方案上发生，并且在 VisualStudio2015 中安装了 ReSharper。  
    在这种情况下，如果您的系统符合要求，下面的检查列表将帮助您解决大多数情况下的性能问题。
    
    首次开放大型解决方案需要花费大量时间（长达几分钟）并不是问题的标志。ReSharper 构建和缓存解决方案的模型，然后将其用于几乎所有的功能 - 不仅用于[代码分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Index.html)，还用于[导航和搜索](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Index.html)，[代码完成](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Code_Completion.html)，[单元测试](https://www.jetbrains.com/help/resharper/2017.3/Unit_Testing__Index.html)等。  
    此解决方案的后续打开不会导致任何重大延迟，因为索引结果已经缓存在硬盘上。  
    请注意，由于 ReSharper 在首次启动时处理程序集注释，即使[清理](https://www.jetbrains.com/help/resharper/2017.3/Configuring_Caches_Location.html) ReSharper 缓存，后续任何启动都会更快。
    
    先试试这个
    -----
    
    性能问题的最常见原因可以通过以下措施来消除：
    
*   转到 **ReSharper|Options|Environment|PerformanceGuide** 检查并快速修复[影响性能的](https://www.jetbrains.com/help/resharper/2017.3/Reference__Options__Environment__Performance_Guide.html) ReSharper 和 VisualStudio 首选项。
*   如果您不使用[解决方案范围分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis.html)，请将其禁用或考虑在解决方案范围分析中禁用警告。即使它被禁用，您也可以随时通过[对整个解决方案](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)运行[代码检查](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)来查找解决方案中的所有代码问题。要配置解决方案范围的分析
*   在 VisualStudio 选项中，转到 **SourceControl|Plug-inSelection**：为源代码管理插件选择**无**。这将关闭 Git 或其他 VCS 提供程序并提高整体性能。
    
    硬件检查
    ----
    
*   确保没有硬件中断和 DPC（通常由坏的驱动程序和 / 或虚拟化引起）。
*   确保你的硬盘没有碎片。
*   确保页面文件至少为 1GB。
*   确保您至少有 15％的可用磁盘空间（MFT 碎片 / 空间不足风险）。
*   确保你至少有 4GB 的 RAM 空闲。
*   将解决方案和 ReSharper 高速缓存存储在 SSD 上会有所帮助，而 RAMDisk 不会产生重大影响。
    
    推荐的系统软件调整
    ---------
    
*   使用 Microsoft 当前支持的 Windows 版本
*   保持 Windows 更新
*   使用 64 位操作系统
*   将 _devenv.exe_，_msbuild.exe_ 和您的代码文件夹添加到 WindowsDefender（和其他防病毒软件）的忽略列表中。
*   停止不必要的服务和流程
    
    VisualStudio
    ------------
    
    在开始调整 VisualStudio 设置之前，请检查是否安装了最新的 VisualStudioupdate/servicepack/hotfixes。
    
    ### 配置 VisualStudio 首选项
    
    打开 VisualStudio 选项（**Tools|Options**）并配置首选项，如下所示：
    
    这里描述的首选项的位置对应于 VisualStudio2015。
    
*   **Environment|General**：禁用 **Automaticallyadjustvisualexperiencebasedonclientperformance** **基于客户端性能自动调整视觉体验**，禁用 **Enablerichclientvisualexperience** **启用富客户端视觉体验**，启用 **Usehardwaregraphicsaccelerationifavailable** **使用硬件图形加速（如果可用）**。这些调整将减少 UI 滞后并提高整体性能。
*   **SourceControl|Plug-inSelection**：为源代码管理插件选择 **None** **无**。这将关闭 Git 或其他 VCS 提供程序并提高整体性能。
*   **Environment|Startup**：选择在启动时显示空白环境并禁用下载内容。关闭起始页面和新闻频道可能会节省启动时间。
*   **Environment|AutoRecover**：禁用 **SaveAutoRecoverinformation** **保存自动恢复信息**。尽管不断复制已打开文档的当前状态可能对崩溃很有用，但它可能会以 UI 价格冻结的大型解决方案（例如，请参阅[此处](https://blogs.msdn.microsoft.com/saraford/2008/02/14/did-you-know-where-visual-studio-saves-auto-recovered-files-in-the-case-of-an-unexpected-shutdown-151/)的注释）。因此，我们建议禁用此功能并养成在重大更改后保存文件的习惯。
*   **TextEditor|General**：禁用 **Trackchanges** **跟踪更改**。当 " 跟踪更改 " 启用时，VisualStudio 会为编辑的行添加阴影突出显示。如果当前文件中的编辑过多，编辑器可能会变慢，因为这些突出显示通常需要计算。  
    尽管这是一个有用的功能，但我们建议禁用它，特别是在处理大文件时。
*   **TextEditor|AllLanguages|ScrollBars**：禁用 **Showannotationsoververticalscrollbar** **在垂直滚动条上显示注释**。ReSharper 广泛使用正确的排水槽或垂直滚动​​条来显示[设计时检查通知](https://www.jetbrains.com/help/resharper/2017.3/Design_time_Inspection.html)，[结构搜索和替换结果](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Structural_Search_and_Replace.html)，[待办事项](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Navigating_Between_To_do_Items.html)以及[文件中符号的用法](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages__Highlighting_Usages_in_File.html)。VisualStudio 也会在滚动条上显示大量通知，有时 VisualStudio 和 ReSharper 报告显示两次的相同错误，而且滚动条通常会变得杂乱无章。  
    如果您更喜欢 ReSharper 标记，则可以完全或部分禁用 VisualStudio 注释，并通过不呈现它们来获得一些性能优势。  
    或者，您可以禁用滚动条上的 ReSharper 标记 - 转到 **ReSharper|Options|Editor|EditorAppearance** 并选择 **Donotshowmarkerbar**.
*   **TextEditor|AllLanguages|CodeLens**：禁用 CodeLens。CodeLens 是[大型解决方案的](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)[性能考虑之一，](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)因为 _"IDE 在滚动到屏幕上时基本上为每种方法执行 " 查找所有引用 "_ _操作_。因此，我们建议您在发现任何滞后时禁用它。  
    CodeLens 的一些功能由 ReSharper 提供 - 例如，您可以快速获取[符号的](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages__Finding_Usages_of_a_Symbol.html)[用法](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Finding_Usages__Finding_Usages_of_a_Symbol.html)（Shift+F12）。
*   **Debugging|Just-In-Time**：禁用**脚本**的实时调试。这将加快构建和调试。
*   **WebFormsDesigner|General**：禁用 Web 窗体设计器。这将减少 UI 和编辑滞后。
*   **XAMLDesigner|General**：禁用 XAML 设计器。VisualXAML 设计器是[一个非常耗费资源的功能](https://visualstudio.uservoice.com/forums/121579-visual-studio-ide/suggestions/2204137-improve-the-xaml-designer-performance)。因此，如果您可以不使用 XAML 的直观表示的情况下[使用](https://www.jetbrains.com/help/resharper/2017.3/ReSharper_by_Language__XAML.html) XAML 代码，则强烈建议禁用 XAML 设计器。
*   **TextEditor|[Language]|Formatting**：禁用所有自动格式首选项。如果您使用 ReSharper 的[格式化帮助](https://www.jetbrains.com/help/resharper/2017.3/Enforcing_Code_Formatting_Rules.html)，这将阻止您的代码重新格式化两次，并减少编辑器滞后。
*   **TextEditor|C#**：如果使用 " 文件结构 " 窗口，则可能不会使用编辑器顶部的导航栏，并且可以在此选项页面上安全地禁用它。
*   **TextEditor|C/C++|Advanced**：如果您使用 C/C++ 代码，请设置 **IntelliSense|DisableSemantic** **禁用语义着色**优选 **True**。这将改善[大文件内](https://developercommunity.visualstudio.com/content/problem/172309/c-semantic-colorization-in-vs-155-is-very-slow-on.html)[打字体验](https://developercommunity.visualstudio.com/content/problem/172309/c-semantic-colorization-in-vs-155-is-very-slow-on.html)。
*   **Environment|Synchronizedsettings**：禁用设置同步。这将改善整体表现。
    
    ### 配置 Roslyn
    
    在大多数已报告的性能问题中，ReSharper 安装在 VisualStudio 中。这并不奇怪：当您的 VisualStudio 解决方案变大时，两个代码分析引擎（ReSharper 和 Roslyn）可同时工作，以达到 32 位进程的内存限制他们分享。  
    虽然没有官方的方法来禁用 Roslyn，但您可以查看[本文](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/suggestions/12304638-enable-turning-off-roslyn-code-fixes)以找到一些替代解决方案。  
    您还可以查看[大型解决方案的](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions) Roslyn 性能考虑事项。
    
    ### 其他 VisualStudio 调整
    
*   从 VisualStudio 中卸载未使用的包和扩展
*   如果您不在某些项目上工作，则可以从 VisualStudio 中卸载它们，并在需要时重新加载它们。右键单击解决方案资源管理器中的项目或解决方案文件夹，然后选择**解除**解决方案文件夹中的**卸载项目**或**卸载项目** - 这将提高整体性能。
    
    ReSharper 的
    -----------
    
    在开始调整 ReSharper 之前，请检查您是否正在运行[最新版本](https://www.jetbrains.com/resharper/whatsnew/)，如果没有，请考虑更新。
    
    ### 配置 ReSharper 首选项
    
    ReSharper 提供了许多不同的功能，如有必要，您可以在 ReSharper 选项中禁用大部分功能。因此，这里的一般规则是：如果您有任何性能问题，请禁用不使用的功能。
    
    打开 ReSharper 选项（**ReSharper|Options**）并配置首选项，如下所示：
    
*   **CodeInspection|Settings**：在此选项页面上，您可以禁用[代码检查的](https://www.jetbrains.com/help/resharper/2017.3/Finding_Code_Issues.html)各个方面。以下是您可以禁用的内容，从最小的禁用功能开始：
*   在 VisualStudio 中，清除 **"DonotshowVisualStudiobulb..."** 复选框。默认情况下，ReSharper 将 Roslyn 操作显示在其自己的[操作列表中](https://www.jetbrains.com/help/resharper/2017.3/Actions_List.html)。这看起来更好，因为编辑器不那么杂乱，但这是昂贵的性能方面的，因为 ReSharper 必须从 Roslyn 请求可用的操作，这可能导致 CPU 和内存使用率的增加。  
    虽然所有对 Roslyn 的请求都是在后台线程中完成的，但如果存在明显的性能问题，您可能需要禁用此选项。
*   如果您不使用[解决方案范围分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis.html)，请将其禁用或考虑在解决方案范围分析中禁用警告。即使它被禁用，您也可以随时通过[对整个解决方案](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)[代码检查](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)来查找解决方案中的所有代码问题。
*   如果解决方案中有任何源代码不需要分析，[请将相应的文件和文件夹添加到忽略列表中](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Configuring_Warnings.html)。
    
    按下，可以将当前文件添加到忽略列表 Ctrl+Shift+Alt+8。再次按快捷键将重新启用此文件的检查。如果要为此操作绑定不同的快捷方式，请 **ReSharper_EnableDaemon** 在 VisualStudio 选项中查找该命令。
    
*   最后一步是清除 **Enablecodeanalysis** **启用代码分析**复选框。这将禁用[设计时检查](https://www.jetbrains.com/help/resharper/2017.3/Design_time_Inspection.html)，但您仍然可以[在所需的范围内运行代码检查](https://www.jetbrains.com/help/resharper/2017.3/Inspecting_Code_in_Specific_Scope.html)。
*   **Environment|Products&Features**：在这里您可以禁用您不使用的 ReSharper 功能。例如，清除 **UnitTesting** **单元测试**复选框将禁用所有 ReSharper 单元测试功能并保存一些内存。
*   **Environment|General**：在 **Storesolutioncachesin****：**选择器中，选择 " 系统温度 " 或任何自定义文件夹。如果您的解决方案不在 VCS 下，您也可以选择 " 解决方案文件夹 "。不建议选择 " 用户本地设置文件夹 "（_％__LOCALAPPDATA__％_）此文件夹的问题在于，每次 ReSharper 写入此文件夹时都会触发 VisualStudio 的目录观察器，这经常发生。
*   **Environment|IntelliSense**：如果您的打字速度变慢，您可能需要进行配置。与代码检查类似，您可以禁用 ReSharperIntelliSense 的特定部分，或将其完全关闭并回退到本机 VisualStudio 的 IntelliSense。以下是您可以禁用的内容，从最小的禁用功能开始：
*   **Environment|IntelliSense|CompletionAppearance**：清除 **Showmembersignatures**,**Showsymboltypes**,**Showsummary**. **显示成员签名**，**显示符号类型**，**显示摘要**。这将简化建筑物完成清单。
*   **Environment|IntelliSense|General**：关闭特定语言的 ReSharperIntelliSense（**CustomIntelliSense** **自定义智能感知**）或完全关闭它（**VisualStudio**）。
*   **Environment|Editor|EditorBehavior**：禁用 **Auto-formatonsemicolon** **分号自动格式**和 **Auto-formatonclosingbrace** **右大括号自动格式**来避免[代码重新格式化](https://www.jetbrains.com/help/resharper/2017.3/Enforcing_Code_Formatting_Rules.html)，同时输入; 也禁用 **Correctcommonlanguage-specifictypos** **正确的公共语言特定的拼写错误**，这将关闭[一些打字辅助功能](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance_Typing_Assistance.html)。清除这些复选框将加速打字。  
    如果您使用 C++，则还可以禁用 **Show import items in basic completion** **基本完成中显示导入项目**偏好 - 这将简化完成列表，从而减少可能的打字延误。
    
    C++ 支持可以通过 ReSharperC++ 获得 - 这是一种专用产品，您可以单独安装，也可以与 ReSharper 或 ReSharperUltimate 一起安装。
    
*   **Environment|Editor|EditorBehavior**：禁用 **Highlight current line**, **Highlight matching delimiters**. **高亮显示当前行**，**突出显示匹配分隔符**。这可能会减少 UI 和编辑器滞后的机会。
*   **Environment | Extension Manager**：禁用您不使用的 ReSharper 扩展。
*   **Tools | Build**：启用 **ReSharper** **构建**。ReSharper 的[增量构建](https://www.jetbrains.com/help/resharper/2017.3/Building_Solution.html)可以大大缩短构建时间，特别是对于大型解决方案。
*   **Code Editing | Context Actions**：在这里您可以禁用对您无用的[上下文操作](https://www.jetbrains.com/help/resharper/2017.3/Coding_Assistance__Context_Actions.html)。
*   **Code Editing | JavaScript | Inspections**：如果您使用 JavaScript 并遇到一些性能问题，请不要 **Analyse properties' context when inspecting code** **在检查代码时分析属性的上下文**。
*   **Code Editing | Third-Party Code**：在这里您可以添加 C++，JavaScript，TypeScript，CSS，HTML 和 JSON 文件，文件夹和通配符，将其视为 " 跳过 " 或 " 库 "。ReSharper 将完全忽略 " 跳过 " 的文件，并将'library'文件视为只读文件 - 用于[导航](https://www.jetbrains.com/help/resharper/2017.3/Navigation_and_Search__Search.html)索引，但没有[检查](https://www.jetbrains.com/help/resharper/2017.3/Finding_Code_Issues.html)，[快速修复](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Quick-Fixes.html)和[重构](https://www.jetbrains.com/help/resharper/2017.3/Refactorings__Index.html)。
*   **Code Editing | Language Injections**：在此页面上，您可以禁用不感兴趣的[自动语言注入](https://www.jetbrains.com/help/resharper/2017.3/Language_Injections.html)。
    
    ### 不要过度使用复杂的 UI 控件
    
*   关闭未使用的[单元测试会话](https://www.jetbrains.com/help/resharper/2017.3/Using_Unit_Test_Sessions.html)。
*   关闭未使用的[类型](https://www.jetbrains.com/help/resharper/2017.3/Exploring_Type_Dependency_Graph.html)，[项目](https://www.jetbrains.com/help/resharper/2017.3/Architecture__Project_Dependencies_Exploration.html)和[程序集](https://www.jetbrains.com/help/resharper/2017.3/Exploring_Assembly_Dependency_Diagram.html)依赖关系图。
*   如果启用[解决方案范围分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Solution-Wide_Analysis.html)，则可以关闭 " 解决方案 " 窗口中的错误 / 警告，因为无论如何您都会看到状态栏中的错误 / 警告数量。
    
    ### 其他调整
    
*   要加快[扩展代码模板](https://www.jetbrains.com/help/resharper/2017.3/Templates__Creating_and_Editing_Templates__Editing_a_Template.html)，可以关闭您使用的模板的**重新格式化**和 **Shorten qualified references** **缩短限定引用**选项：
*   ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161107136-423105442.png)
*   不使用它时关闭 ProcessExplorer 窗口。
    
    ### 如果没有帮助
    
    如果您尝试了上述所有内容并且性能仍然不佳，您可以暂时禁用 ReSharper 并检查是否是造成速度放慢的原因。要禁用 / 启用 ReSharper，请转至 **Tools | Options | ReSharper Ultimate** ，然后单击 **Suspend Now**/**Resume Now**。
    
    如果暂停 ReSharper 有助于提高性能，但您仍然希望偶尔使用它来进行[代码分析](https://www.jetbrains.com/help/resharper/2017.3/Code_Analysis__Index.html)，[代码清理](https://www.jetbrains.com/help/resharper/2017.3/Code_Cleanup__Index.html)或[重新格式化代码](https://www.jetbrains.com/help/resharper/2017.3/Enforcing_Code_Formatting_Rules.html)，则可能需要一个可快速切换 ReSharper 的快捷方式。以下是如何操作：转到 **Tools | Options | Environment | Keyboard** 并找到该 **ReSharper_ToggleSuspended** 命令，然后按您选择的快捷方式并单击**分配**。
    
    ![](https://images2017.cnblogs.com/blog/572188/201803/572188-20180305161107308-1485163760.png)
    
    已知的性能问题
    -------
    
    如果您最近更新了 ReSharper，并观察使用先前版本打开的解决方案的性能下降情况，则可以尝试通过清除 ReSharper 缓存并删除解决方案_.suo_ 文件来加快速度。
    
    要清除缓存，请转至 **ReSharper | Options | Environment | General** 并单击 "
    
    **Clear Caches**. **清除缓存 "**。
    
    已知的兼容性问题
    --------
    
    ### 其他 VisualStudio 扩展
    
    使用以下产品已经观察到主要兼容性问题：
    
*   DevExpress CodeRush/Refactor Pro (incompatible)
*   Telerik JustCode (incompatible)
*   Whole Tomato Visual Assist
*   Productivity Power Tools
    
    使用以下产品观察到性能下降：
    
*   Some versions of the StyleCop ReSharper plug-in
*   PowerCommands for Visual Studio
    
    还有关于 WebEssentials 的报告导致编辑_.cshtml_ 文件时性能低下。如果您受到此问题的影响，请考虑转到 **Tools | Options | Web Essentials** 并**在** **Enter** **上**设置 **Auto-format HTML on Enter** 为 **False**。
    
    ### ParallelsDesktopforMac
    
    如果您使用 ParallelsDesktop 在 Mac 上的 Windows 虚拟机中运行 VisualStudio，则 ReSharperIntelliSense 列表渲染速度可能会非常慢。
    
    如果在您的设置中发生这种情况，请考虑从 " 连贯 " 模式切换到 " 全屏 " 模式。有关在两种模式之间切换的指导原则，请参阅此 Parallels 知识库条目。