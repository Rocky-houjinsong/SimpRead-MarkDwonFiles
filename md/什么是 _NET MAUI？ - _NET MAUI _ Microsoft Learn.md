> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [learn.microsoft.com](https://learn.microsoft.com/zh-cn/dotnet/maui/what-is-maui?view=net-maui-7.0)

> .NET 多平台应用 UI (.NET MAUI) 是一个跨平台框架，用于使用 C# 和 XAML 创建本机移动和桌面应用。

什么是 .NET MAUI？
==============

*   项目
*   2023/01/31
*   3 个参与者

反馈

本文内容
----

1.  [.NET MAUI 适用于谁](#who-net-maui-is-for)
2.  [.NET MAUI 的工作原理](#how-net-maui-works)
3.  [.NET MAUI 提供的内容](#what-net-maui-provides)

.NET 多平台应用 UI (.NET MAUI) 是一个跨平台框架，用于使用 C# 和 XAML 创建本机移动和桌面应用。

使用 .NET MAUI，可从单个共享代码库开发可在 Android、iOS、macOS 和 Windows 上运行的应用。

![](https://learn.microsoft.com/zh-cn/dotnet/maui/media/what-is-maui/maui-overview.png?view=net-maui-7.0)

.NET MAUI 是开源的，是 Xamarin.Forms 的演变，从移动方案扩展到桌面方案，UI 控件从头开始重新生成，以确保性能和扩展性。 如果以前使用 Xamarin.Forms 生成跨平台用户界面，你会注意到与 .NET MAUI 的许多相似之处。 但也有一些差异。 使用 .NET MAUI，可以使用单个项目创建多平台应用，但可以根据需要添加特定于平台的源代码和资源除了共享代码,可以针对特定平台进行定制开发。 .NET MAUI 的主要目的之一是使你能够在单个代码库中实现尽可能多的应用逻辑和 UI 布局。

[](#who-net-maui-is-for)

.NET MAUI 适用于谁
--------------

.NET MAUI 适用于想要：

*   从 Visual Studio 中的单个共享代码库使用 XAML 和 C# 编写跨平台应用。
*   跨平台共享 UI 布局和设计。
*   跨平台共享代码、测试和业务逻辑。

[](#how-net-maui-works)

.NET MAUI 的工作原理
---------------

.NET MAUI 将 Android、iOS、macOS 和 Windows API 统一到单个 API 中，提供 “编写一次就能在任何地方运行” 的开发人员体验，同时还提供了对每个原生平台各个方面的深入访问如何访问每一个平台的原生API。

.NET 6 或更高版本提供一系列特定于平台的框架用于创建应用：.NET for Android、.NET for iOS、.NET for macOS 和 Windows UI 3 (WinUI 3) 库。 这些框架都有权访问同一个 .NET 基类库 (BCL) 。 此库从代码中抽象出基础平台的详细信息。 BCL 依赖于 .NET 运行时来为代码提供执行环境。 对于 Android、iOS 和 macOS，环境由 Mono 实现，这是 .NET 运行时的实现。 在 Windows 上，.NET CoreCLR 提供执行环境。

虽然 BCL 允许在不同平台上运行的应用共享通用业务逻辑，但各种平台具有不同的方法来定义应用的用户界面，并且它们提供不同的模型来指定用户界面元素的通信和互操作方式。 可以使用适用于 Android 的相应平台特定框架 (.NET、适用于 iOS 的 .NET、适用于 macOS 的 .NET 或 WinUI 3) 单独为每个平台创建 UI，但此方法随后需要为每个设备系列维护基本代码。

.NET MAUI 提供单个框架，用于为移动和桌面应用生成 UI。 下图显示了 .NET MAUI 应用的体系结构的高级视图：

![](https://learn.microsoft.com/zh-cn/dotnet/maui/media/what-is-maui/architecture-diagram.png?view=net-maui-7.0)

在 .NET MAUI 应用中，可以编写主要与 .NET MAUI API (1) 进行交互的代码。 然后，.NET MAUI 直接使用本机平台 API (3) 。 此外，如果需要，应用代码可以直接使用平台 API (2) 。

.NET MAUI 应用可以在电脑或 Mac 上编写，并编译为本机应用包：

*   使用 .NET MAUI 生成的 Android 应用从 C# 编译为中间语言 (IL) 然后在应用启动时实时 (JIT) 编译为本机程序集。安卓是启动运行前,实时编译
*   使用 .NET MAUI 生成的 iOS 应用完全领先 (AOT) 从 C# 编译为本机 ARM 程序集代码预编译。
*   使用 .NET MAUI 构建的 macOS 应用使用 Mac Catalyst，这是 Apple 提供的一种解决方案，可将使用 UIKit 构建的 iOS 应用引入桌面，并根据需要使用其他 AppKit 和平台 API 对其进行扩充。
*   使用 .NET MAUI 生成的 Windows 应用使用 Windows UI 3 (WinUI 3) 库创建面向 Windows 桌面的本机应用。 有关 WinUI 3 的详细信息，请参阅 [Windows UI 库](/zh-cn/windows/apps/winui/)。

备注

生成适用于 iOS 和 macOS 的应用需要 Mac。

[](#what-net-maui-provides)

.NET MAUI 提供的内容
---------------

.NET MAUI 提供可用于显示数据、启动操作、指示活动、显示集合、选取数据等的控件集合。 除了控件集合外，.NET MAUI 还提供：

*   用于设计页面的精心布局引擎。
*   用于创建丰富导航类型的多种页类型，如抽屉。
*   支持数据绑定，实现更简洁、更易维护的开发模式。
*   自定义处理程序以增强 UI 元素呈现方式的功能。
*   用于访问本机设备功能的跨平台 API。 这些 API 使应用能够访问设备功能，例如 GPS、加速计以及电池和网络状态。 有关详细信息，请参阅 [设备功能的跨平台 API](#cross-platform-apis-for-device-features)。
*   跨平台图形功能，提供支持绘制形状和图像、合成操作和图形对象转换的绘图画布。
*   使用多目标面向 Android、iOS、macOS 和 Windows 的单个项目系统。 有关详细信息，请参阅 [.NET MAUI 单一项目](#single-project)。
*   .NET 热重载，以便在应用运行时同时修改 XAML 和托管源代码，然后观察修改结果，而无需重新生成应用。 有关详细信息，请参阅 [.NET 热重载](#hot-reload)。

[](#cross-platform-apis-for-device-features)

### 适用于设备功能的跨平台 API

.NET MAUI 为本机设备功能提供跨平台 API。 .NET MAUI 提供的用于访问设备功能的功能示例包括：

*   访问设备上的传感器，例如加速计、指南针和陀螺仪。
*   能够检查设备的网络连接状态并检测更改。
*   提供有关运行应用的设备的信息。
*   在应用之间将文本复制并粘贴到系统剪贴板。
*   从设备中选择一个或多个文件。
*   将数据安全地存储为键 / 值对。
*   利用内置的文本转语音引擎从设备读取文本。
*   启动基于浏览器的身份验证流，这些流侦听对特定应用注册 URL 的回调。

[](#single-project)

### 单个项目

.NET MAUI 单一项目采用开发应用时通常遇到的特定于平台的开发体验，并将其抽象化为可面向 Android、iOS、macOS 和 Windows 的单个共享项目。

无论面向的平台如何，.NET MAUI 单一项目都提供简化且一致的跨平台开发体验。 .NET MAUI 单个项目提供以下功能：

*   可面向 Android、iOS、macOS 和 Windows 的单个共享项目。
*   用于运行 .NET MAUI 应用的简化调试目标选择。
*   单个项目中的共享资源文件。
*   单个应用清单，指定应用标题、ID 和版本。
*   根据需要访问特定于平台的 API 和工具。
*   单个跨平台应用入口点。

使用多目标启用 .NET MAUI 单一项目，并使用 SDK 样式项目。 有关 .NET MAUI 单一项目的详细信息，请参阅 [.NET MAUI 单项目](https://learn.microsoft.com/zh-cn/dotnet/maui/fundamentals/single-project?view=net-maui-7.0)。

[](#hot-reload)

### 热重载

.NET MAUI 包括对 .NET 热重载的支持，使你可以在应用运行时修改托管源代码，而无需手动暂停或命中断点。 然后，无需重新编译即可将代码编辑应用于正在运行的应用。

.NET MAUI 还包括对 XAML 热重载的支持，这使你无需重新编译即可保存 XAML 文件并查看正在运行的应用中反映的更改。 此外，还会保留导航状态和数据，使你能够在 UI 上快速迭代，而不会失去应用中的位置。