> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [learn.microsoft.com](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation?pivots=windows)

> 本文说明如何将存储单个便笺的 Xamarin.Forms Shell 应用程序转换为能够存储多个便笺的应用程序。

1.  [Learn](https://learn.microsoft.com/zh-cn/)
2.  [Xamarin](https://learn.microsoft.com/zh-cn/xamarin)
3.  [开始使用](https://learn.microsoft.com/zh-cn/xamarin/get-started/)
4.  [快速入门](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/)

1.  [Learn](https://learn.microsoft.com/zh-cn/)
2.  [Xamarin](https://learn.microsoft.com/zh-cn/xamarin)
3.  [开始使用](https://learn.microsoft.com/zh-cn/xamarin/get-started/)
4.  [快速入门](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/)

使用英语阅读 添加 目录 使用英语阅读 添加 打印 Twitter LinkedIn Facebook 电子邮件 目录

在 Xamarin.Forms 应用程序中执行导航
=========================

*   项目
*   2022/09/21
*   1 个参与者

反馈

选择开发环境  Visual Studio  Visual Studio for Mac 

本文内容
----

1.  [使用 Visual Studio 更新应用](#update-the-app-with-visual-studio)
2.  [后续步骤](#next-steps)
3.  [相关链接](#related-links)

 [![](https://learn.microsoft.com/zh-cn/xamarin/media/shared/download.png) 下载示例](/zh-cn/samples/xamarin/xamarin-forms-samples/getstarted-notes-navigation/)

在本快速入门中，你将了解如何：

*   向 Xamarin.Forms Shell 应用程序添加更多页面。
*   在页面之间执行导航。
*   使用数据绑定在用户界面元素与其数据源之间同步数据。

本快速入门演练如何将能够存储单个便笺的跨平台 Xamarin.Forms Shell 应用程序转换为能够存储多个便笺的应用程序。 最终的应用程序如下所示：

[![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/screenshots1-sml.png)](navigation-images/screenshots1.png#lightbox "Notes Page")[![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/screenshots2-sml.png)](navigation-images/screenshots2.png#lightbox "Note Entry Page")

[](#prerequisites)

### 先决条件

在尝试本快速入门之前，应成功完成[上一个快速入门](app)。 或者，下载[上一个快速入门示例](/zh-cn/samples/xamarin/xamarin-forms-samples/getstarted-notes-app/)并将它用作本快速入门的起点。

[](#update-the-app-with-visual-studio)

使用 Visual Studio 更新应用
---------------------

1.  启动 Visual Studio。 在开始窗口中，单击最近使用的项目 / 解决方案列表中的 “Notes” 解决方案，或单击 “打开项目或解决方案”，然后在“打开项目 / 解决方案” 对话框中，选择 “Notes” 项目的解决方案文件：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/open-solution.png)
    
2.  在 “解决方案资源管理器” 中，右键单击 “Notes” 项目，并依次选择“添加”>“新文件夹”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/add-new-folder.png)
    
3.  在 “解决方案资源管理器” 中，将新文件夹命名为“Models”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/name-folder.png)
    
4.  在 “解决方案资源管理器” 中选择 “Models” 文件夹，右键单击，然后选择“添加”>“类...”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/add-new-models-file.png)
    
5.  在 “添加新项” 对话框中，选择 “Visual C# 项”>“类”，将新文件命名为“Note”，然后单击“添加” 按钮：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/add-note-class.png)
    
    这会将名为 Note 的类添加到 “Notes” 项目的 “Models” 文件夹中。
    
6.  在 Note.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    
    namespace Notes.Models
    {
        public class Note
        {
            public string Filename { get; set; }
            public string Text { get; set; }
            public DateTime Date { get; set; }
        }
    }
    ```
    
    此类定义一个 `Note` 模型，该模型将在应用程序中存储有关每个便笺的数据。
    
    通过按 Ctrl+S，保存对 Note.cs 所做的更改。
    
7.  在 “解决方案资源管理器” 的“Notes”项目中，选择 “Views” 文件夹，右键单击，然后选择 “添加”>“新建项...”。在“添加新项” 对话框中，选择 “Visual C# 项”>“Xamarin.Forms”>“内容页”，将新文件命名为“NoteEntryPage”，然后单击“添加” 按钮：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vs/add-note-entry-page.png)
    
    这会将名为 “NoteEntryPage” 的新页添加到项目的 “Views” 文件夹中。 此页将用于便笺输入。
    
8.  在 NoteEntryPage.xaml 中，删除所有模板代码并将其替换为以下代码：
    
    XAML 复制
    
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="Notes.Views.NoteEntryPage"
                 Title="Note Entry">
        <!-- Layout children vertically -->
        <StackLayout Margin="20">
            <Editor Placeholder="Enter your note"
                    Text="{Binding Text}"
                    HeightRequest="100" />
            <!-- Layout children in two columns -->
            <Grid ColumnDefinitions="*,*">
                <Button Text="Save"
                        Clicked="OnSaveButtonClicked" />
                <Button Grid.Column="1"
                        Text="Delete"
                        Clicked="OnDeleteButtonClicked"/>
            </Grid>
        </StackLayout>
    </ContentPage>
    ```
    
    该代码以声明的方式定义页面的用户界面，它包含一个用于文本输入的 [`Editor`](/zh-cn/dotnet/api/xamarin.forms.editor)，以及两个指示应用程序保存或删除文件的 [`Button`](/zh-cn/dotnet/api/xamarin.forms.button) 对象。 这两个 `Button` 实例水平放置在 [`Grid`](/zh-cn/dotnet/api/xamarin.forms.grid) 中，而 `Editor` 和 `Grid` 垂直放置在 [`StackLayout`](/zh-cn/dotnet/api/xamarin.forms.stacklayout) 中。 此外，`Editor` 使用数据绑定来绑定到 `Note` 模型的 `Text` 属性。 有关数据绑定的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[数据绑定](deepdive#data-binding)。
    
    通过按 Ctrl+S，保存对 NoteEntryPage.xaml 所做的更改。
    
9.  在 NoteEntryPage.xaml.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.IO;
    using Notes.Models;
    using Xamarin.Forms;
    
    namespace Notes.Views
    {
        [QueryProperty(nameof(ItemId), nameof(ItemId))]
        public partial class NoteEntryPage : ContentPage
        {
            public string ItemId
            {
                set
                {
                    LoadNote(value);
                }
            }
    
            public NoteEntryPage()
            {
                InitializeComponent();
    
                // Set the BindingContext of the page to a new Note.
                BindingContext = new Note();
            }
    
            void LoadNote(string filename)
            {
                try
                {
                    // Retrieve the note and set it as the BindingContext of the page.
                    Note note = new Note
                    {
                        Filename = filename,
                        Text = File.ReadAllText(filename),
                        Date = File.GetCreationTime(filename)
                    };
                    BindingContext = note;
                }
                catch (Exception)
                {
                    Console.WriteLine("Failed to load note.");
                }
            }
    
            async void OnSaveButtonClicked(object sender, EventArgs e)
            {
                var note = (Note)BindingContext;
    
                if (string.IsNullOrWhiteSpace(note.Filename))
                {
                    // Save the file.
                    var filename = Path.Combine(App.FolderPath, $"{Path.GetRandomFileName()}.notes.txt");
                    File.WriteAllText(filename, note.Text);
                }
                else
                {
                    // Update the file.
                    File.WriteAllText(note.Filename, note.Text);
                }
    
                // Navigate backwards
                await Shell.Current.GoToAsync("..");
            }
    
            async void OnDeleteButtonClicked(object sender, EventArgs e)
            {
                var note = (Note)BindingContext;
    
                // Delete the file.
                if (File.Exists(note.Filename))
                {
                    File.Delete(note.Filename);
                }
    
                // Navigate backwards
                await Shell.Current.GoToAsync("..");
            }
        }
    }
    ```
    
    此代码将 `Note` 实例（表示单个便笺）存储在页面的 [`BindingContext`](/zh-cn/dotnet/api/xamarin.forms.bindableobject.bindingcontext#xamarin-forms-bindableobject-bindingcontext) 中。 该类用 `QueryPropertyAttribute` 进行修饰，在导航过程中，可以通过查询参数将数据传入页面。 `QueryPropertyAttribute` 的第一个参数指定将接收数据的属性的名称，第二个参数指定查询参数 ID。因此，上述代码中的 `QueryParameterAttribute` 指定 `ItemId` 属性将接收从 `GoToAsync` 方法调用中指定的 URI 传入 `ItemId` 查询参数的数据。 然后，`ItemId` 属性调用`LoadNote` 方法，从设备上的文件中创建一个 `Note` 对象，并将页面的 `BindingContext` 设置为 `Note` 对象。
    
    按 “保存”[`Button`](/zh-cn/dotnet/api/xamarin.forms.button) 时，会执行 `OnSaveButtonClicked` 事件处理程序，它会将 `Editor` 的内容保存到具有随机生成的文件名的新文件，或者保存到现有文件（如果正在更新便笺）。 在这两种情况下，文件都存储在应用程序的本地应用程序数据文件夹中。 然后该方法会导航回上一页。 按 “删除”`Button` 时，会执行 `OnDeleteButtonClicked` 事件处理程序，它会删除文件（前提是它存在）并导航回上一页。 有关导航的详细信息，请参阅 [Xamarin.Forms Shell 快速入门深入探讨](deepdive)中的[导航](deepdive#navigation)。
    
    通过按 Ctrl+S，保存对 NoteEntryPage.xaml.cs 所做的更改。
    
    警告
    
    由于在后续步骤中将修复一些错误，暂时不会生成应用程序。
    
10.  在 “解决方案资源管理器” 的“Notes”项目中，打开 “Views” 文件夹中的“NotesPage.xaml” 。
    
11.  在 NotesPage.xaml 中，删除所有模板代码并将其替换为以下代码：
    
    XAML 复制
    
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="Notes.Views.NotesPage"
                 Title="Notes">
        <!-- Add an item to the toolbar -->
        <ContentPage.ToolbarItems>
            <ToolbarItem Text="Add"
                         Clicked="OnAddClicked" />
        </ContentPage.ToolbarItems>
    
        <!-- Display notes in a list -->
        <CollectionView x:
                        Margin="20"
                        SelectionMode="Single"
                        SelectionChanged="OnSelectionChanged">
            <CollectionView.ItemsLayout>
                <LinearItemsLayout Orientation="Vertical"
                                   ItemSpacing="10" />
            </CollectionView.ItemsLayout>
            <!-- Define the appearance of each item in the list -->
            <CollectionView.ItemTemplate>
                <DataTemplate>
                    <StackLayout>
                        <Label Text="{Binding Text}"
                               FontSize="Medium"/>
                        <Label Text="{Binding Date}"
                               TextColor="Silver"
                               FontSize="Small" />
                    </StackLayout>
                </DataTemplate>
            </CollectionView.ItemTemplate>
        </CollectionView>
    </ContentPage>
    ```
    
    此代码以声明方式定义页面的用户界面，该界面由 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview) 和 [`ToolbarItem`](/zh-cn/dotnet/api/xamarin.forms.toolbaritem) 组成。 `CollectionView` 使用数据绑定来显示应用程序检索到的任何便笺。 选择便笺会导航到 `NoteEntryPage`，在那里可以修改便笺。 或者，可以通过按 `ToolbarItem` 来创建新便笺。 有关数据绑定的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[数据绑定](deepdive#data-binding)。
    
    通过按 Ctrl+S，保存对 NotesPage.xaml 所做的更改。
    
12.  在 “解决方案资源管理器” 的“Notes”项目中，展开 “Views” 文件夹中的“NotesPage.xaml”，并打开“NotesPage.xaml.cs” 。
    
13.  在 NotesPage.xaml.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Linq;
    using Notes.Models;
    using Xamarin.Forms;
    
    namespace Notes.Views
    {
        public partial class NotesPage : ContentPage
        {
            public NotesPage()
            {
                InitializeComponent();
            }
    
            protected override void OnAppearing()
            {
                base.OnAppearing();
    
                var notes = new List<Note>();
    
                // Create a Note object from each file.
                var files = Directory.EnumerateFiles(App.FolderPath, "*.notes.txt");
                foreach (var filename in files)
                {
                    notes.Add(new Note
                    {
                        Filename = filename,
                        Text = File.ReadAllText(filename),
                        Date = File.GetCreationTime(filename)
                    });
                }
    
                // Set the data source for the CollectionView to a
                // sorted collection of notes.
                collectionView.ItemsSource = notes
                    .OrderBy(d => d.Date)
                    .ToList();
            }
    
            async void OnAddClicked(object sender, EventArgs e)
            {
                // Navigate to the NoteEntryPage, without passing any data.
                await Shell.Current.GoToAsync(nameof(NoteEntryPage));
            }
    
            async void OnSelectionChanged(object sender, SelectionChangedEventArgs e)
            {
                if (e.CurrentSelection != null)
                {
                    // Navigate to the NoteEntryPage, passing the filename as a query parameter.
                    Note note = (Note)e.CurrentSelection.FirstOrDefault();
                    await Shell.Current.GoToAsync($"{nameof(NoteEntryPage)}?{nameof(NoteEntryPage.ItemId)}={note.Filename}");
                }
            }
        }
    }
    ```
    
    此代码定义 `NotesPage` 的功能。 显示该页面时，会执行 `OnAppearing` 方法，该方法使用从本地应用程序数据文件夹中检索到的任何便笺填充 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview)。 按 [`ToolbarItem`](/zh-cn/dotnet/api/xamarin.forms.toolbaritem) 时，会执行 `OnAddClicked` 事件处理程序。 此方法导航到 `NoteEntryPage`。 选择 `CollectionView` 中的项时，会执行 `OnSelectionChanged` 事件处理程序。 此方法导航到 `NoteEntryPage`，前提是选中了 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview) 中的一个项，将选中的 `Note` 的 `Filename` 属性作为查询参数传递给页面。 有关导航的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[导航](deepdive#navigation)。
    
    通过按 Ctrl+S，保存对 NotesPage.xaml.cs 所做的更改。
    
    警告
    
    由于在后续步骤中将修复一些错误，暂时不会生成应用程序。
    
14.  在 “解决方案资源管理器” 的“Notes”项目中，展开“AppShell.xaml”，然后打开“AppShell.xaml.cs” 。 然后将现有代码替换为以下代码：
    
    C# 复制
    
    ```
    using Notes.Views;
    using Xamarin.Forms;
    
    namespace Notes
    {
        public partial class AppShell : Shell
        {
            public AppShell()
            {
                InitializeComponent();
                Routing.RegisterRoute(nameof(NoteEntryPage), typeof(NoteEntryPage));
            }
        }
    }
    ```
    
    此代码为在 Shell 视觉层次结构 (AppShell.xaml) 中未表示的 `NoteEntryPage` 注册了一个路由。 然后，可以使用 `GoToAsync` 方法导航此页以使用基于 URI 的导航。
    
    通过按 Ctrl+S，保存对 AppShell.xaml.cs 所做的更改。
    
15.  在 “解决方案资源管理器” 的“Notes”项目中，展开“App.xaml”，然后打开“App.xaml.cs” 。 然后将现有代码替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.IO;
    using Xamarin.Forms;
    
    namespace Notes
    {
        public partial class App : Application
        {
            public static string FolderPath { get; private set; }
    
            public App()
            {
                InitializeComponent();
                FolderPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData));
                MainPage = new AppShell();
            }
    
            protected override void OnStart()
            {
            }
    
            protected override void OnSleep()
            {
            }
    
            protected override void OnResume()
            {
            }
        }
    }
    ```
    
    此代码为 `System.IO` 命名空间添加命名空间声明，并为类型为 `string` 的静态 `FolderPath` 属性添加声明。 `FolderPath` 属性用于存储在设备上存储便笺数据的路径。 此外，该代码会在 `App` 构造函数中初始化 `FolderPath` 属性，并将 [`MainPage`](/zh-cn/dotnet/api/xamarin.forms.application.mainpage#xamarin-forms-application-mainpage) 属性初始化为已设置子类的 `Shell` 对象。
    
    通过按 Ctrl+S，保存对 App.xaml.cs 所做的更改。
    
16.  在每个平台上生成并运行项目。 有关详细信息，请参阅[生成快速入门](app#building-the-quickstart)。
    
    在 NotesPage 上，按 “添加” 按钮以导航到 NoteEntryPage 并输入便笺。 保存便笺之后，应用程序会导航回 NotesPage。
    
    输入一些不同长度的便笺，以观察应用程序行为。 关闭应用程序并重新启动它，以确保你输入的笔记已保存到设备。
    

[](#update-the-app-with-visual-studio-for-mac)

使用 Visual Studio for Mac 更新应用
-----------------------------

1.  启动 Visual Studio for Mac。 在开始窗口单击 “打开”，然后在对话框中选择“Notes” 项目的解决方案文件：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/open-solution.png)
    
2.  在 “Solution Pad” 中，右键单击 “Notes” 项目，并依次选择“添加”>“新建文件夹”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/add-new-folder.png)
    
3.  在 “新建文件夹” 对话框中，将新文件夹命名为“Models”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/name-folder.png)
    
4.  在 “Solution Pad” 中选择 “Models” 文件夹，右键单击，然后选择“添加”>“新建类...”：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/add-new-models-file.png)
    
5.  在 “新建文件” 对话框中，选择 “常规”>“空类”，将新文件命名为“Note”，然后单击“新建” 按钮：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/add-note-class.png)
    
    这会将名为 Note 的类添加到 “Notes” 项目的 “Models” 文件夹中。
    
6.  在 Note.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    
    namespace Notes.Models
    {
        public class Note
        {
            public string Filename { get; set; }
            public string Text { get; set; }
            public DateTime Date { get; set; }
        }
    }
    ```
    
    此类定义一个 `Note` 模型，该模型将在应用程序中存储有关每个便笺的数据。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 Note.cs 所做的更改。
    
7.  在 “Solution Pad” 中，选择 “Notes” 项目，然后右键单击并选择 “添加”>“新建文件...”。在“新建文件” 对话框中，选择 “窗体”>“窗体 ContentPage Xaml”，将新文件命名为“NoteEntryPage”，然后单击“新建” 按钮：
    
    ![](https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation-images/vsmac/add-note-entry-page.png)
    
    这会将名为 “NoteEntryPage” 的新页添加到项目的 “Views” 文件夹中。 此页将用于便笺输入。
    
8.  在 NoteEntryPage.xaml 中，删除所有模板代码并将其替换为以下代码：
    
    XAML 复制
    
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="Notes.Views.NoteEntryPage"
                 Title="Note Entry">
        <!-- Layout children vertically -->
        <StackLayout Margin="20">
            <Editor Placeholder="Enter your note"
                    Text="{Binding Text}"
                    HeightRequest="100" />
            <!-- Layout children in two columns -->
            <Grid ColumnDefinitions="*,*">
                <Button Text="Save"
                        Clicked="OnSaveButtonClicked" />
                <Button Grid.Column="1"
                        Text="Delete"
                        Clicked="OnDeleteButtonClicked"/>
            </Grid>
        </StackLayout>
    </ContentPage>
    ```
    
    该代码以声明的方式定义页面的用户界面，它包含一个用于文本输入的 [`Editor`](/zh-cn/dotnet/api/xamarin.forms.editor)，以及两个指示应用程序保存或删除文件的 [`Button`](/zh-cn/dotnet/api/xamarin.forms.button) 对象。 这两个 `Button` 实例水平放置在 [`Grid`](/zh-cn/dotnet/api/xamarin.forms.grid) 中，而 `Editor` 和 `Grid` 垂直放置在 [`StackLayout`](/zh-cn/dotnet/api/xamarin.forms.stacklayout) 中。 此外，`Editor` 使用数据绑定来绑定到 `Note` 模型的 `Text` 属性。 有关数据绑定的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[数据绑定](deepdive#data-binding)。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 NoteEntryPage.xaml 所做的更改。
    
9.  在 NoteEntryPage.xaml.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.IO;
    using Notes.Models;
    using Xamarin.Forms;
    
    namespace Notes.Views
    {
        [QueryProperty(nameof(ItemId), nameof(ItemId))]
        public partial class NoteEntryPage : ContentPage
        {
            public string ItemId
            {
                set
                {
                    LoadNote(value);
                }
            }
    
            public NoteEntryPage()
            {
                InitializeComponent();
    
                // Set the BindingContext of the page to a new Note.
                BindingContext = new Note();
            }
    
            void LoadNote(string filename)
            {
                try
                {
                    // Retrieve the note and set it as the BindingContext of the page.
                    Note note = new Note
                    {
                        Filename = filename,
                        Text = File.ReadAllText(filename),
                        Date = File.GetCreationTime(filename)
                    };
                    BindingContext = note;
                }
                catch (Exception)
                {
                    Console.WriteLine("Failed to load note.");
                }
            }
    
            async void OnSaveButtonClicked(object sender, EventArgs e)
            {
                var note = (Note)BindingContext;
    
                if (string.IsNullOrWhiteSpace(note.Filename))
                {
                    // Save the file.
                    var filename = Path.Combine(App.FolderPath, $"{Path.GetRandomFileName()}.notes.txt");
                    File.WriteAllText(filename, note.Text);
                }
                else
                {
                    // Update the file.
                    File.WriteAllText(note.Filename, note.Text);
                }
    
                // Navigate backwards
                await Shell.Current.GoToAsync("..");
            }
    
            async void OnDeleteButtonClicked(object sender, EventArgs e)
            {
                var note = (Note)BindingContext;
    
                // Delete the file.
                if (File.Exists(note.Filename))
                {
                    File.Delete(note.Filename);
                }
    
                // Navigate backwards
                await Shell.Current.GoToAsync("..");
            }
        }
    }
    ```
    
    此代码将 `Note` 实例（表示单个便笺）存储在页面的 [`BindingContext`](/zh-cn/dotnet/api/xamarin.forms.bindableobject.bindingcontext#xamarin-forms-bindableobject-bindingcontext) 中。 该类用 `QueryPropertyAttribute` 进行修饰，在导航过程中，可以通过查询参数将数据传入页面。 `QueryPropertyAttribute` 的第一个参数指定将接收数据的属性的名称，第二个参数指定查询参数 ID。因此，上述代码中的 `QueryParameterAttribute` 指定 `ItemId` 属性将接收从 `GoToAsync` 方法调用中指定的 URI 传入 `ItemId` 查询参数的数据。 然后，`ItemId` 属性调用`LoadNote` 方法，从设备上的文件中创建一个 `Note` 对象，并将页面的 `BindingContext` 设置为 `Note` 对象。
    
    按 “保存”[`Button`](/zh-cn/dotnet/api/xamarin.forms.button) 时，会执行 `OnSaveButtonClicked` 事件处理程序，它会将 `Editor` 的内容保存到具有随机生成的文件名的新文件，或者保存到现有文件（如果正在更新便笺）。 在这两种情况下，文件都存储在应用程序的本地应用程序数据文件夹中。 然后该方法会导航回上一页。 按 “删除”`Button` 时，会执行 `OnDeleteButtonClicked` 事件处理程序，它会删除文件（前提是它存在）并导航回上一页。 有关导航的详细信息，请参阅 [Xamarin.Forms Shell 快速入门深入探讨](deepdive)中的[导航](deepdive#navigation)。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 NoteEntryPage.xaml.cs 所做的更改。
    
    警告
    
    由于在后续步骤中将修复一些错误，暂时不会生成应用程序。
    
10.  在 “Solution Pad” 的“Notes”项目中，打开 “Views” 文件夹中的“NotesPage.xaml” 。
    
11.  在 NotesPage.xaml 中，删除所有模板代码并将其替换为以下代码：
    
    XAML 复制
    
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="Notes.Views.NotesPage"
                 Title="Notes">
        <!-- Add an item to the toolbar -->
        <ContentPage.ToolbarItems>
            <ToolbarItem Text="Add"
                         Clicked="OnAddClicked" />
        </ContentPage.ToolbarItems>
    
        <!-- Display notes in a list -->
        <CollectionView x:
                        Margin="20"
                        SelectionMode="Single"
                        SelectionChanged="OnSelectionChanged">
            <CollectionView.ItemsLayout>
                <LinearItemsLayout Orientation="Vertical"
                                   ItemSpacing="10" />
            </CollectionView.ItemsLayout>
            <!-- Define the appearance of each item in the list -->
            <CollectionView.ItemTemplate>
                <DataTemplate>
                    <StackLayout>
                        <Label Text="{Binding Text}"
                               FontSize="Medium"/>
                        <Label Text="{Binding Date}"
                               TextColor="Silver"
                               FontSize="Small" />
                    </StackLayout>
                </DataTemplate>
            </CollectionView.ItemTemplate>
        </CollectionView>
    </ContentPage>
    ```
    
    此代码以声明方式定义页面的用户界面，该界面由 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview) 和 [`ToolbarItem`](/zh-cn/dotnet/api/xamarin.forms.toolbaritem) 组成。 `CollectionView` 使用数据绑定来显示应用程序检索到的任何便笺。 选择便笺会导航到 `NoteEntryPage`，在那里可以修改便笺。 或者，可以通过按 `ToolbarItem` 来创建新便笺。 有关数据绑定的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[数据绑定](deepdive#data-binding)。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 NotesPage.xaml 所做的更改。
    
12.  在 “Solution Pad” 的“Notes”项目中，展开 “Views” 文件夹中的“NotesPage.xaml”，并打开“NotesPage.xaml.cs” 。
    
13.  在 NotesPage.xaml.cs 中，删除所有模板代码并将其替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Linq;
    using Notes.Models;
    using Xamarin.Forms;
    
    namespace Notes.Views
    {
        public partial class NotesPage : ContentPage
        {
            public NotesPage()
            {
                InitializeComponent();
            }
    
            protected override void OnAppearing()
            {
                base.OnAppearing();
    
                var notes = new List<Note>();
    
                // Create a Note object from each file.
                var files = Directory.EnumerateFiles(App.FolderPath, "*.notes.txt");
                foreach (var filename in files)
                {
                    notes.Add(new Note
                    {
                        Filename = filename,
                        Text = File.ReadAllText(filename),
                        Date = File.GetCreationTime(filename)
                    });
                }
    
                // Set the data source for the CollectionView to a
                // sorted collection of notes.
                collectionView.ItemsSource = notes
                    .OrderBy(d => d.Date)
                    .ToList();
            }
    
            async void OnAddClicked(object sender, EventArgs e)
            {
                // Navigate to the NoteEntryPage, without passing any data.
                await Shell.Current.GoToAsync(nameof(NoteEntryPage));
            }
    
            async void OnSelectionChanged(object sender, SelectionChangedEventArgs e)
            {
                if (e.CurrentSelection != null)
                {
                    // Navigate to the NoteEntryPage, passing the filename as a query parameter.
                    Note note = (Note)e.CurrentSelection.FirstOrDefault();
                    await Shell.Current.GoToAsync($"{nameof(NoteEntryPage)}?{nameof(NoteEntryPage.ItemId)}={note.Filename}");
                }
            }
        }
    }
    ```
    
    此代码定义 `NotesPage` 的功能。 显示该页面时，会执行 `OnAppearing` 方法，该方法使用从本地应用程序数据文件夹中检索到的任何便笺填充 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview)。 按 [`ToolbarItem`](/zh-cn/dotnet/api/xamarin.forms.toolbaritem) 时，会执行 `OnAddClicked` 事件处理程序。 此方法导航到 `NoteEntryPage`。 选择 `CollectionView` 中的项时，会执行 `OnSelectionChanged` 事件处理程序。 此方法导航到 `NoteEntryPage`，前提是选中了 [`CollectionView`](/zh-cn/dotnet/api/xamarin.forms.collectionview) 中的一个项，将选中的 `Note` 的 `Filename` 属性作为查询参数传递给页面。 有关导航的详细信息，请参阅 [Xamarin.Forms 快速入门深入探讨](deepdive)中的[导航](deepdive#navigation)。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 NotesPage.xaml.cs 所做的更改。
    
    警告
    
    由于在后续步骤中将修复一些错误，暂时不会生成应用程序。
    
14.  在 “Solution Pad” 的“Notes”项目中，展开“AppShell.xaml”，然后打开“AppShell.xaml.cs” 。 然后将现有代码替换为以下代码：
    
    C# 复制
    
    ```
    using Notes.Views;
    using Xamarin.Forms;
    
    namespace Notes
    {
        public partial class AppShell : Shell
        {
            public AppShell()
            {
                InitializeComponent();
                Routing.RegisterRoute(nameof(NoteEntryPage), typeof(NoteEntryPage));
            }
        }
    }
    ```
    
    此代码为在 Shell 视觉层次结构中未表示的 `NoteEntryPage` 注册了一个路由。 然后，可以使用 `GoToAsync` 方法导航此页以使用基于 URI 的导航。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 AppShell.xaml.cs 所做的更改。
    
15.  在 “Solution Pad” 的“Notes”项目中，展开“App.xaml”，然后打开“App.xaml.cs” 。 然后将现有代码替换为以下代码：
    
    C# 复制
    
    ```
    using System;
    using System.IO;
    using Xamarin.Forms;
    
    namespace Notes
    {
        public partial class App : Application
        {
            public static string FolderPath { get; private set; }
    
            public App()
            {
                InitializeComponent();
                FolderPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData));
                MainPage = new AppShell();
            }
    
            protected override void OnStart()
            {
            }
    
            protected override void OnSleep()
            {
            }
    
            protected override void OnResume()
            {
            }
        }
    }
    ```
    
    此代码为 `System.IO` 命名空间添加命名空间声明，并为类型为 `string` 的静态 `FolderPath` 属性添加声明。 `FolderPath` 属性用于存储在设备上存储便笺数据的路径。 此外，该代码会在 `App` 构造函数中初始化 `FolderPath` 属性，并将 [`MainPage`](/zh-cn/dotnet/api/xamarin.forms.application.mainpage#xamarin-forms-application-mainpage) 属性初始化为已设置子类的 `Shell` 对象。
    
    通过选择 “文件”>“保存”（或按 ⌘ + S），保存对 App.xaml.cs 所做的更改。
    
16.  在每个平台上生成并运行项目。 有关详细信息，请参阅[生成快速入门](app#building-the-quickstart)。
    
    在 NotesPage 上，按 “添加” 按钮以导航到 NoteEntryPage 并输入便笺。 保存便笺之后，应用程序会导航回 NotesPage。
    
    输入一些不同长度的便笺，以观察应用程序行为。 关闭应用程序并重新启动它，以确保你输入的笔记已保存到设备。
    

[](#next-steps)

后续步骤
----

在此快速入门中，读者学习了如何：

*   向 Xamarin.Forms Shell 应用程序添加更多页面。
*   在页面之间执行导航。
*   使用数据绑定在用户界面元素与其数据源之间同步数据。

继续学习下一个快速入门教程，修改应用程序以便它将其数据存储在本地 SQLite.NET 数据库中。

[下一页](database)

[](#related-links)

相关链接
----

*   [便笺（示例）](/zh-cn/samples/xamarin/xamarin-forms-samples/getstarted-notes-navigation/)
*   [Xamarin.Forms Shell 快速入门深入探讨](deepdive)

* * *

建议的内容
-----

*   [
    
    ### Xamarin.Forms 图像教程 - Xamarin
    
    ](/zh-cn/xamarin/get-started/tutorials/image/?source=recommendations)
    
    了解如何使用 Xamarin.Forms 图像视图在页面上显示图像。
    
*   [
    
    ### Xamarin.Forms 编辑器教程 - Xamarin
    
    ](/zh-cn/xamarin/get-started/tutorials/editor/?source=recommendations)
    
    了解如何使用 Xamarin.Forms 编辑器视图接受多行文本输入。
    
*   [
    
    ### 弹出菜单 - Xamarin
    
    ](/zh-cn/xamarin/android/user-interface/controls/popup-menu?source=recommendations)
    
    如何添加定位到特定视图的弹出菜单。
    
*   [
    
    ### Xamarin.Forms 标签教程 - Xamarin
    
    ](/zh-cn/xamarin/get-started/tutorials/label/?source=recommendations)
    
    了解如何使用 Xamarin.Forms 标签视图在单行和多行中显示文本。
    
*   [
    
    ### Xamarin.Forms 弹出项教程 - Xamarin
    
    ](/zh-cn/xamarin/get-started/tutorials/pop-ups/?source=recommendations)
    
    了解如何使用 Xamarin.Forms 显示警报和操作工作表，向用户询问简单问题，以及指导用户完成任务。
    
*   [
    
    ### 在 Xamarin.Android 中使用 ListView - Xamarin
    
    ](/zh-cn/xamarin/android/user-interface/layouts/list-view/?source=recommendations)
    
    ListView 是 Android 应用程序的重要 UI 组件; 它随处使用，从菜单选项的简短列表到联系人或 Internet 收藏夹的长列表。 它提供了一种简单的方式来显示可使用内置样式设置格式或自定义的行的滚动列表。
    
*   [
    
    ### CardView - Xamarin
    
    ](/zh-cn/xamarin/android/user-interface/controls/card-view?source=recommendations)
    
    Cardview 小组件是一个 UI 组件，在类似于卡片的视图中显示文本和图像内容。 本指南介绍如何在 Xamarin.Android 应用程序中使用和自定义 CardView，同时保持与早期版本的 Android 的向后兼容性。
    

显示更多

* * *

其他资源
----

[中文 (简体)](/zh-cn/locale?target=https://learn.microsoft.com/zh-cn/xamarin/get-started/quickstarts/navigation) 主题

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