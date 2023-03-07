> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.cnblogs.com](https://www.cnblogs.com/peterYong/p/12767465.html)

> 在. Net Core 下，没有可以支持跨平台的 Drawing 类库，官网提供的 Common.Drawing 只能在 Windows 下使用，那么在. Net Core 下该如何处理图片呢？其实有很多第三方提供了解决

[Xamarin.Forms 中的 SkiaSharp](https://www.cnblogs.com/peterYong/p/12767465.html)
===============================================================================

**目录**

*   [一、SkiaSharp 是什么？](#_label0)
    *   [1.Skia 介绍](#_label0_0)
    *   [2.SkiaSharp 介绍](#_label0_1)
    *   [3. 预备知识](#_label0_2)
*   [二、SkiaSharp Drawing Basics](#_label1)
    *   [1、绘制圆圈](#_label1_0)
    *   [2、与 Xamarin.Forms 集成](#_label1_1)
    *   [3、像素和独立于设备的单位](#_label1_2)
    *   [4、将文本和图形集成](#_label1_3)
    *   [5、Bitmap Basics](#_label1_4)
*   [三、SkiaSharp 线和路径](#_label2)
    *   [1、Lines and Stroke Caps](#_label2_0) 
    *   [2、Path Basics in SkiaSharp](#_label2_1)
    *    [3、The Path Fill Types](#_label2_2)
    *   [4、折线和参数方程式](#_label2_3)
    *   [5、点和短划线](#_label2_4)
    *   [6、手指画图](#_label2_5)
*   [四、SkiaSharp Transforms](#_label3)
    *   [1、The Translate Transform](#_label3_0)
    *   [2、The Scale Transform](#_label3_1)
    *   [3、The Rotate Transform](#_label3_2)
*   [更多参考](#_label4)

**正文**

在. Net Core 下，没有可以支持跨平台的 Drawing 类库，官网提供的 Common.Drawing 只能在 Windows 下使用，那么在. Net Core 下该如何处理图片呢？其实有很多第三方提供了解决方案，而我比较喜欢用的是 Mono 团队提供的 SkiaSharp，原因是稳定而且支持的也很好，性能上也还好。

[回到顶部](#_labelTop)

一、SkiaSharp 是什么？
----------------

### 1.Skia 介绍

Skia 是 Google 旗下的 2D 图形处理库，下面是援引百科中的词条：

> skia 是个 2D 向量图形处理函数库，包含字型、坐标转换，以及点阵图都有高效能且简洁的表现。不仅用于 Google Chrome 浏览器，新兴的 Android 开放手机平台也采用 skia 作为绘图处理，搭配 OpenGL/ES 与特定的硬件特征，强化显示的效果。

[Skia 官网](https://skia.org/)中是这样介绍的：

> Skia is an open source 2D graphics library which provides common APIs that work across a variety of hardware and software platforms. It serves as the graphics engine for Google Chrome and Chrome OS, Android, Mozilla Firefox and Firefox OS, and many other products.

### 2.SkiaSharp 介绍

SkiaSharp 故名思义，就是在. net 下使用 Skia API 的库，是 SkiaSharp 是由 mono 团队开发并进行持续维护，至今已经多年了。目前的最新版本是 1.68.1.1，当前支持. net 下的：

*   .NET Standard 1.3
*   .NET Core
*   Tizen
*   Xamarin.Android
*   Xamarin.iOS
*   Xamarin.tvOS
*   Xamarin.watchOS
*   Xamarin.Mac
*   Windows Classic Desktop (Windows.Forms / WPF)
*   Windows UWP (Desktop / Mobile / Xbox / HoloLens)

SkiaSharp 项目：[https://github.com/mono/SkiaSharp](https://github.com/mono/SkiaSharp)

以下参考：[Xamarin.Forms 中的 SkiaSharp Graphics](https://docs.microsoft.com/zh-cn/xamarin/xamarin-forms/user-interface/graphics/skiasharp/)

### 3. 预备知识

SkiaSharp for Xamarin.Forms 打包为 NuGet 软件包。在 Visual Studio 或 Visual Studio for Mac 中创建 Xamarin.Forms 解决方案之后，可以使用 NuGet 包管理器搜索 SkiaSharp.Views.Forms 包并将其添加到解决方案中。

如果您的 Xamarin.Forms 应用程序以 iOS 为目标，请使用项目属性页将最低部署目标更改为 iOS 8.0。

在任何使用 SkiaSharp 的 C＃页面中，您都希望为 SkiaSharp 名称空间包含 using 指令，该指令包含您将在图形编程中使用的所有 SkiaSharp 类，结构和枚举。您还需要针对 Xamarin.Forms 特定类的 SkiaSharp.Views.Forms 命名空间使用 using 指令。这是一个较小的名称空间，最重要的类是 SKCanvasView，该类派生自 Xamarin.Forms View 类，并承载您的 SkiaSharp 图形输出

注：SkiaSharp.Views.Forms 命名空间还包含一个 SKGLView 类，该类派生自 View，但使用 OpenGL 渲染图形。 为简单起见，本指南将自身限制为 SKCanvasView，但使用 SKGLView 却非常相似。

**SkiaSharp 绘图基础**  
您可以使用 SkiaSharp 绘制的一些最简单的图形是圆形，椭圆形和矩形。在显示这些图形时，您将了解 SkiaSharp 的坐标，大小和颜色。文本和位图的显示更为复杂，但是这些文章还介绍了这些技术。

**SkiaSharp 线和路径**  
图形路径是一系列连接的直线和曲线。路径可以是描边，填充或两者兼有。本文涵盖了线条绘制的许多方面，包括笔划结束和连接以及虚线和虚线，但在曲线几何形状方面停滞不前。

**SkiaSharp 转换**  
变换允许图形对象均匀地平移，缩放，旋转或倾斜。本文还说明了如何使用标准的 3×3 变换矩阵创建非仿射变换并将变换应用于路径。

**SkiaSharp 曲线和路径**  
通过向路径对象添加曲线以及利用其他强大的路径功能，继续探索路径。您将看到如何在简洁的文本字符串中指定整个路径，如何使用路径效果以及如何深入研究路径内部。

**SkiaSharp 位图 Bitmaps**  
位图是与显示设备的像素相对应的位的矩形阵列。本系列文章展示了如何加载，保存，显示，创建，绘制，动画化和访问 SkiaSharp 位图的位。

**SkiaSharp 特效**  
效果是会改变图形正常显示的属性，包括线性和圆形渐变，位图平铺，混合模式，模糊等。

[回到顶部](#_labelTop)

二、SkiaSharp Drawing Basics
--------------------------

### 1、绘制圆圈

 _including canvases（画布） and paint objects（绘制对象）_

一些对象：

SKCanvasView 类似 StackLayout 等 view。 可以将 SKCanvasView 与其他 Xamarin.Forms View 派生词组合

PaintSurface 事件处理程序是您绘制所有图形的地方

SKImageInfo 结构包含有关绘图表面的信息，最重要的是其宽度和高度（以像素为单位）。

SKSurface 对象代表绘图表面本身，最重要属性是 SKCanvas 类型的 Canvas。此类是用于执行实际绘图的图形绘图上下文，SKCanvas 对象封装了图形状态，其中包括图形转换和裁剪。

SKPaint 对象只不过是图形绘制属性的集合，这些对象是轻量级的。 您可以像该程序一样重复使用 SKPaint 对象，也可以为图形属性的各种组合创建多个 SKPaint 对象。 您可以在 PaintSurface 事件处理程序之外创建和初始化这些对象，也可以将它们另存为页面类中的字段。

SKPaintStyle

*   [Fill](https://docs.microsoft.com/en-us/dotnet/api/skiasharp.skpaintstyle#SkiaSharp_SKPaintStyle_Fill)
*   [Stroke](https://docs.microsoft.com/en-us/dotnet/api/skiasharp.skpaintstyle#SkiaSharp_SKPaintStyle_Stroke)
*   [StrokeAndFill](https://docs.microsoft.com/en-us/dotnet/api/skiasharp.skpaintstyle#SkiaSharp_SKPaintStyle_StrokeAndFill)

The default is `Fill 填充`.，Stroke 为 划线（轮廓），StrokeAndFill 为 描边线条，并用相同的颜色填充内部。

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
public partial class SimpleCirclePage : ContentPage
    {
        /// <summary>
        /// 绘制一个圆圈，
        /// 创建一个SKCanvasView对象来承载图形，处理PaintSurface事件以及使用SKPaint对象来指定颜色和其他图形属性。
        /// </summary>
        public SimpleCirclePage()
        {
            InitializeComponent();

            Title = "Simple Circle";

            //SKCanvasView类似StackLayout等view。 可以将SKCanvasView与其他Xamarin.Forms View派生词组合
            SKCanvasView canvasView = new SKCanvasView();
            canvasView.WidthRequest = 100;
            canvasView.HeightRequest = 100;
            canvasView.PaintSurface += OnCanvasViewPaintSurface;
            Content = canvasView;
        }

        /// <summary>
        /// PaintSurface事件处理程序是您绘制所有图形的地方。 程序运行时，可以多次调用此方法【例如旋转屏幕】，因此它应保留重新创建图形显示所需的所有信息：
        /// </summary>
        /// <param ></param>
        /// <param ></param>
        void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
        {
            //SKPaintSurfaceEventArgs 有两个重要的属性：Info和Surface
           
            //SKImageInfo结构包含有关绘图表面的信息，最重要的是其宽度和高度（以像素为单位）。 
            
            //SKSurface对象代表绘图表面本身。 在此程序中，绘图表面是视频显示，但在其他程序中，SKSurface对象也可以表示您使用SkiaSharp进行绘图的 Bitmaps位图。
            //SKSurface的最重要属性是SKCanvas类型的Canvas。此类是用于执行实际绘图的图形绘图上下文，SKCanvas对象封装了图形状态，其中包括图形转换和裁剪。

            SKImageInfo info = args.Info;
            SKSurface surface = args.Surface;
            SKCanvas canvas = surface.Canvas;

            //Clear方法使用透明颜色清除画布。 重载使您可以为画布指定背景色。
            canvas.Clear();

            //绘制一个半径为100像素的圆。 圆的轮廓为红色，圆的内部为蓝色。
            //因为此特定的图形图像包含两种不同的颜色，所以该工作需要分两个步骤完成。 第一步是绘制圆的轮廓，要指定线条的颜色和其他特征，请创建并初始化SKPaint对象：
            SKPaint paint = new SKPaint
            {
                Style = SKPaintStyle.Stroke, //划 线
                Color = Color.Red.ToSKColor(),
                StrokeWidth = 50   //线的粗细，50像素
            };
            //相对于显示表面的左上角指定坐标。 X坐标向右增加，Y坐标向下增加。 在讨论图形时，通常使用数学符号（x，y）表示一个点。 点（0，0）是显示表面的左上角，通常称为原点。
            //DrawCircle的前两个参数指示圆心的X和Y坐标。 将它们分配给显示表面宽度和高度的一半，以将圆心置于显示表面的中心。 第三个参数指定圆的半径，最后一个参数是SKPaint对象。
            canvas.DrawCircle(info.Width / 2, info.Height / 2, 200, paint);

            //要填充圆的内部，可以更改SKPaint对象的两个属性，然后再次调用DrawCircle。
            paint.Style = SKPaintStyle.Fill; //填充
            paint.Color = SKColors.Blue;
            canvas.DrawCircle(info.Width / 2, info.Height / 2, 170, paint);
        }

    }
```

View Code

### 2、与 Xamarin.Forms 集成

SkiaSharp 图形可以几种方式与 Xamarin.Forms 的其余部分集成。

您可以在同一页面上组合 SkiaSharp 画布和 Xamarin.Forms 元素，甚至将 Xamarin.Forms 元素放置在 SkiaSharp 画布的顶部：

在 Xamarin.Forms 中创建交互式 SkiaSharp 图形的另一种方法是通过触摸，通过轻按切换两种方式绘制一个简单的圆圈（无填充和有填充）。

示例：TapToggleFillPage 类显示如何响应用户输入来更改 SkiaSharp 图形。

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
/// <summary>
        /// 单击事件
        /// </summary>
        /// <param ></param>
        /// <param ></param>
        private void TapGestureRecognizer_Tapped(object sender, EventArgs e)
        {
            showFill = !showFill;
            //通知画布需要重新绘制自己
            //对InvalidateSurface的调用有效地生成了对PaintSurface处理程序的调用
            (sender as SKCanvasView).InvalidateSurface();
        }
```

View Code

示例：ColorExplorepage  演示了如何将 SkiaSharp 图形与其他 Xamarin.Forms 元素集成在一起【文字位于图像上】，并演示了两种在 SkiaSharp 中定义颜色的替代方法之间的区别。 静态 SKColor.FromHsl 方法基于 Hue-Saturation-Lightness 模型创建一个 SKColor 值：

```
public static SKColor FromHsl (Single h, Single s, Single l, Byte a)
public static SKColor FromHsv (Single h, Single s, Single v, Byte a)
```

在这两种情况下，h 参数的范围都是 0 到 360。s，l 和 v 参数的范围是 0 到 100。a（字母或不透明度）参数的范围是 0 到 255。

### 3、像素和独立于设备的单位

探索 SkiaSharp 坐标和 Xamarin 之间的差异。您可以获取在两个坐标系之间进行转换的信息，还可以绘制填充特定区域的图形：

默认情况下，SkiaSharp 以像素为单位绘制，而 Xamarin.Forms 则以由基础平台建立的与设备无关的单位作为坐标和尺寸。 （有关 Xamarin.Forms 坐标系的更多信息，[请参见第 5 章](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/creating-mobile-apps-xamarin-forms/summaries/chapter05)。）

示例：SurfaceSizePage 使用 SkiaSharp 文本输出来显示来自三个不同来源的显示表面的尺寸：

*   SKCanvasView 对象的常规 Xamarin.Forms Width 和 Height 属性。
*   SKCanvasView 对象的 CanvasSize 属性。
*   SKImageInfo 值的 Size 属性，该属性与前两页中使用的 Width 和 Height 属性一致。

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427102039259-2027556168.png)

如您所见，SKCanvasView 的 CanvasSize 属性和 SKImageInfo 值的 Size 属性在报告像素尺寸方面是一致的。 SKCanvasView 的 Height 和 Width 属性是 Xamarin.Forms 属性，它们以平台定义的独立于设备的单位报告视图的大小。

SurfaceSizePage 类显示如何显示这些值。 构造函数将 SKCanvasView 对象保存为字段，因此可以在 PaintSurface 事件处理程序中对其进行访问：

DrawText 最简单的一个方法：

```
public void DrawText (String text, Single x, Single y, SKPaint paint)
```

您指定文本字符串，文本开始处的 X 和 Y 坐标以及 SKPaint 对象。 **X 坐标指定文本左侧的位置【左下角】**，但请注意：Y 坐标指定文本基线的位置。 如果您曾经用手写纸写过，则基线是字符所在的行，而下降的行（例如字母 g，p，q 和 y 的下降行）则位于该行的下方。

SKPaint 对象使您可以指定文本的颜色，字体系列和文本大小。 默认情况下，TextSize 属性的值为 12，这会在诸如电话之类的高分辨率设备上生成微小的文本。 在除最简单的应用程序之外的任何应用程序中，您还需要一些有关所显示文本大小的信息。 SKPaint 类定义了 FontMetrics 属性和几个 MeasureText 方法，但是为了减少花哨的需求，FontSpacing 属性提供了用于间隔连续文本行的建议值（只读）。

iOS 7 模拟器每个独立于设备的像素有两个像素，Android Nexus 5 每个单位具有三个像素。这就是前面显示的简单圆圈在不同平台上具有不同大小的原因。

如果您希望完全以独立于设备的单位进行工作，可以通过将 SKCanvasView 的 IgnorePixelScaling 属性设置为 true 来实现。但是，您可能不喜欢这个结果，SkiaSharp 将图形渲染在较小的设备表面上，其像素大小等于独立于设备的视图大小。 （例如，SkiaSharp 将在 Nexus 5 上使用 360 x 512 像素的显示表面。）然后按比例放大该图像，从而导致明显的位图锯齿。

为了保持相同的图像分辨率，更好的解决方案是编写自己的简单函数以在两个坐标系之间进行转换。

除 DrawCircle 方法外，SKanvas 还定义了两个绘制椭圆的 DrawOval 方法。 椭圆由两个半径而不是单个半径定义。 这些被称为长半径和短半径。 DrawOval 方法绘制一个椭圆，其两个半径平行于 X 和 Y 轴。 （如果需要绘制不与 X 和 Y 轴平行的轴的椭圆，则可以使用如[《旋转变换》](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/transforms/rotate)一文中讨论的旋转变换或如《绘制弧的三种方式》中所讨论的图形路径。 ）。 DrawOval 方法的重载命名两个半径参数 rx 和 ry，以指示它们与 X 和 Y 轴平行：

```
public void DrawOval (Single cx, Single cy, Single rx, Single ry, SKPaint paint)
```

参数：x、y 的中心点，垂直半径、水平半径。

是否可以绘制 填充显示表面的椭圆形？EllipseFillPage 演示了如何进行，从 xRadius 和 yRadius 值中减去笔触宽度的一半，以使整个椭圆及其轮廓适合显示表面：

另一种方式： 绘制椭圆去填充矩形

```
//SKRect rect = new SKRect(0, 0, info.Width, info.Height);
            SKRect rect = new SKRect(strokeWidth/2, strokeWidth/2, info.Width-strokeWidth/2, info.Height-strokeWidth/2);
            canvas.DrawOval(rect, paint);
```

### 4、将文本和图形集成

示例 `FramedTextPage`  在页面上居中放置一个短文本字符串，并用由一对圆角矩形组成的框架包围它。 

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200424163133520-147856072.png)

在 SkiaSharp 中，您可以使用 SKPaint 类来设置文本和字体属性，但也可以使用它来获取呈现的文本大小。

SKRect 对象：// 存储一组四个浮点数，这些浮点数代表矩形的左上角和右下角。【使用它来画边框】

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
public partial class FramedTextPage : ContentPage
    {
        /// <summary>
        /// 在页面上居中放置一个短文本字符串，并用由一对圆角矩形组成的框架包围它
        /// </summary>
        public FramedTextPage()
        {
            InitializeComponent();

            Title = "Framed Text";

            SKCanvasView canvasView = new SKCanvasView();
            canvasView.PaintSurface += OnCanvasViewPaintSurface;
            Content = canvasView;
        }

        private void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
        {
            SKImageInfo info = args.Info;
            SKSurface surface = args.Surface;
            SKCanvas canvas = surface.Canvas;

            canvas.Clear();

            string str = "Hello SkiaSharp!";

            // Create an SKPaint object to display the text
            SKPaint textPaint = new SKPaint
            {
                Color = SKColors.Chocolate
            };

            //第一个MeasureText调用具有一个简单的字符串参数，并根据当前字体属性返回文本的像素宽度。 
            //然后，程序将根据渲染的宽度，当前的TextSize属性和显示区域的宽度，计算SKPaint对象的新TextSize属性。 此计算旨在设置TextSize，以使文本字符串以屏幕宽度的90％呈现：
            float textWidth = textPaint.MeasureText(str); //测量
            textPaint.TextSize = 0.9f * info.Width * textPaint.TextSize / textWidth;

            //如果只需要在屏幕上居中放置一些文本，则可以在不测量文本的情况下大致完成。 而是将SKPaint的TextAlign属性设置为枚举成员SKTextAlign.Center。 
            //然后，您在DrawText方法中指定的X坐标指示文本水平中心的位置。 如果将屏幕的中点传递给DrawText方法，则文本将水平居中且几乎垂直居中，因为基线将垂直居中。


            //第二个MeasureText调用具有SKRect参数，因此它同时获得了呈现文本的宽度和高度。 此SKRect值的Height属性取决于文本字符串中是否存在大写字母，升序和降序。
            //例如，对于文本字符串“ mom”，“ cat”和“ dog”，报告了不同的Height值。

            //如果通过DrawText调用以X和Y位置为0显示文本，则SKRect结构的Left和Top属性指示所渲染文本的左上角的坐标。例如，当此程序在iPhone上运行时 在7个模拟器中，作为对MeasureText的第一次调用之后的计算结果，TextSize被分配了值90.6254。 从第二次调用MeasureText获得的SKRect值具有以下属性值：
            SKRect textBounds = new SKRect(); //存储一组四个浮点数，这些浮点数代表矩形的左上角和右下角。
            textPaint.MeasureText(str, ref textBounds);

            // Calculate offsets to center the text on the screen[以使文本居中显示在屏幕上]
            float xText = info.Width / 2 - textBounds.MidX;  //MidX和MidY值指示矩形中心的坐标。
            float yText = info.Height / 2 - textBounds.MidY;
            //或者
            //float xText = info.Rect.MidX - textBounds.MidX;
            //float yText = info.Rect.MidY - textBounds.MidY;

            // And draw the text..
            canvas.DrawText(str, xText, yText, textPaint);


            //对DrawRoundRect的两个调用，这两个调用都需要SKRect的参数。 此SKRect值基于从MeasureText方法获得的SKRect值，但不能相同。 
            //首先，它需要更大一些，以使圆角矩形不会在文本的边缘上绘制。 
            //其次，它需要在空间上移动，以使“左”和“上”值与要放置矩形的左上角相对应。 这两个作业是通过SKRect定义的Offset和Inflate方法完成的：

            // Create a new SKRect object for the frame around the text
            SKRect frameRect = textBounds;
            frameRect.Offset(xText, yText);
            frameRect.Inflate(10, 10);  //扩大

            //为边框创建另一个SKPaint对象，并两次调用DrawRoundRect。 
            //第二个调用使用一个矩形，该矩形再膨胀10个像素。 第一次调用将角半径指定为20个像素。 第二个的角半径为30像素，因此它们似乎是平行的：
            SKPaint framePaint = new SKPaint
            {
                Style = SKPaintStyle.Stroke,
                StrokeWidth = 5,
                Color = SKColors.Blue
            };
            // Draw one frame。
            canvas.DrawRoundRect(frameRect, 20, 20, framePaint);

            // Inflate the frameRect and draw another
            frameRect.Inflate(10, 10);
            framePaint.Color = SKColors.DarkBlue;
            canvas.DrawRoundRect(frameRect, 30, 30, framePaint);
        }
    }
```

View Code

### 5、Bitmap Basics

#### **1、显示位图**

**加载位图**

从各种来源加载位图并显示它们。

SkiaSharp 中对位图的支持非常广泛。 以下 如何加载位图以及如何显示位图：

SkiaSharp 位图是 SKBitmap 类型的对象。 创建位图的方法有很多，但是本文将其自身限制为 SKBitmap.Decode 方法，该方法从. NET Stream 对象加载位图。

示例：BasicBitmapsPage 演示了如何从三个不同的来源加载位图：

*   通过互联网
*   从可执行文件中嵌入的资源
*   来自用户的照片库

静态 SKBitmap.Decode 方法负责解码位图文件，它可以处理 JPEG，PNG 和 GIF 位图格式，并将结果以内部 SkiaSharp 格式存储。

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
public partial class BasicBitmapsPage : ContentPage
    {
        SKCanvasView canvasView;

        HttpClient httpClient = new HttpClient();

        /// <summary>
        /// 从Web加载的位图
        /// </summary>
        SKBitmap webBitmap;
        SKBitmap resourceBitmap;
        SKBitmap libraryBitmap;


        public BasicBitmapsPage()
        {
            InitializeComponent();

            Title = "Basic Bitmaps";

            canvasView = new SKCanvasView();
            canvasView.PaintSurface += OnCanvasViewPaintSurface;
            Content = canvasView;


            // 加载项目中的位图资源，图片属性设置为 嵌入的资源
            string resourceID = "SkiaSharpDemo.Media.monkey.png";
            Assembly assembly = GetType().GetTypeInfo().Assembly;
            using (Stream stream = assembly.GetManifestResourceStream(resourceID))
            {
                resourceBitmap = SKBitmap.Decode(stream);
            }

            ////暂不实现
            //// Add tap gesture recognizer
            //TapGestureRecognizer tapRecognizer = new TapGestureRecognizer();
            //tapRecognizer.Tapped += async (sender, args) =>
            //{
            //    // Load bitmap from photo library
            //    IPhotoLibrary photoLibrary = DependencyService.Get<IPhotoLibrary>();

            //    using (Stream stream = await photoLibrary.PickPhotoAsync())
            //    {
            //        if (stream != null)
            //        {
            //            libraryBitmap = SKBitmap.Decode(stream);
            //            canvasView.InvalidateSurface();
            //        }
            //    }
            //};
            //canvasView.GestureRecognizers.Add(tapRecognizer);
        }

        private void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
        {
            SKImageInfo info = args.Info;
            SKSurface surface = args.Surface;
            SKCanvas canvas = surface.Canvas;

            canvas.Clear();

            if (webBitmap != null)
            {
                float x = (info.Width - webBitmap.Width) / 2;
                float y = (info.Height / 3 - webBitmap.Height) / 2;
                canvas.DrawBitmap(webBitmap, x, y);
            }

            if (resourceBitmap != null)
            {
                canvas.DrawBitmap(resourceBitmap,
                    new SKRect(0, info.Height / 3, info.Width, 2 * info.Height / 3));
            }

            if (libraryBitmap != null)
            {
                float scale = Math.Min((float)info.Width / libraryBitmap.Width,
                                       info.Height / 3f / libraryBitmap.Height);

                float left = (info.Width - scale * libraryBitmap.Width) / 2;
                float top = (info.Height / 3 - scale * libraryBitmap.Height) / 2;
                float right = left + scale * libraryBitmap.Width;
                float bottom = top + scale * libraryBitmap.Height;
                SKRect rect = new SKRect(left, top, right, bottom);
                rect.Offset(0, 2 * info.Height / 3);

                canvas.DrawBitmap(libraryBitmap, rect);
            }
            else
            {
                using (SKPaint paint = new SKPaint())
                {
                    paint.Color = SKColors.Blue;
                    paint.TextAlign = SKTextAlign.Center;
                    paint.TextSize = 48;

                    canvas.DrawText("Tap to load bitmap",
                        info.Width / 2, 5 * info.Height / 6, paint);
                }
            }
        }


        /// <summary>
        /// 由于将await运算符与HttpClient一起使用最方便，因此无法在BasicBitmapsPage构造函数中执行代码。 
        /// 因此放在 OnAppearing 中执行。 此处的URL指向Xamarin网站上带有一些示例位图的区域，网站上的一个程序包允许附加一个规范以将位图调整为特定的宽度：
        /// </summary>
        protected override async void OnAppearing()
        {
            base.OnAppearing();

            // 从Web 加载位图
            string url = "https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2197602503,3264180697&fm=26&gp=0.jpg?width=480";

            try
            {

                using (var stream = await httpClient.GetStreamAsync(url))
                using (MemoryStream memoryStream = new MemoryStream())
                {
                    await stream.CopyToAsync(memoryStream);
                    memoryStream.Seek(0, SeekOrigin.Begin);

                    //当在SKBitmap.Decode方法中使用从GetStreamAsync返回的Stream时，Android操作系统引发异常，因为它在主线程上执行冗长的操作。 
                    //因此，使用CopyToAsync将位图文件的内容复制到MemoryStream对象。

                    //静态SKBitmap.Decode方法负责解码位图文件。 它可以处理JPEG，PNG和GIF位图格式，并将结果存储在内部SkiaSharp格式中。 
                    //此时，需要使SKCanvasView InvalidateSurface，以允许PaintSurface处理程序更新显示。
                    webBitmap = SKBitmap.Decode(memoryStream);
                    canvasView.InvalidateSurface();
                }

            }
            catch (Exception)
            {

            }
        }
    }
```

View Code

**以像素尺寸显示**  
Canvas 类定义了四个 DrawBitmap 方法， 这些方法允许以两种根本不同的方式显示位图：

*   指定 SKPoint 值（或单独的 x 和 y 值）将以其像素尺寸显示位图，位图的像素直接映射到视频显示器的像素。
*   指定矩形会导致位图拉伸到矩形的大小和形状。

您可以使用具有 SKPoint 参数的 DrawBitmap 或具有单独的 x 和 y 参数的 DrawBitmap 在其像素尺寸中显示位图：

```
DrawBitmap(SKBitmap bitmap, SKPoint pt, SKPaint paint = null)
DrawBitmap(SKBitmap bitmap, float x, float y, SKPaint paint = null)
```

这两种方法在功能上是相同的，指定的点指示位图的左上角相对于画布的位置。 由于移动设备的像素分辨率很高，因此较小的位图通常在这些设备上显得很小。

可选的 SKPaint 参数允许您使用透明度显示位图。 为此，请创建一个 SKPaint 对象，并将 Color 属性设置为 alpha 通道小于 1 的任何 SKColor 值。例如：

```
paint.Color = new SKColor(0, 0, 0, 0x80);
```

作为最后一个参数传递的 0x80 表示 50％的透明度。 您还可以在一种预定义的颜色上设置 Alpha 通道：

```
paint.Color = SKColors.Red.WithAlpha(0x80);
```

但是，颜色本身无关紧要。 在 DrawBitmap 调用中使用 SKPaint 对象时，仅检查 Alpha 通道。

使用混合模式或滤镜效果显示位图时，SKPaint 对象也起作用。 在 [SkiaSharp compositing and blend modes](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/effects/blend-modes/) and [SkiaSharp image filters](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/effects/image-filters). 文中对此进行了演示。

示例 PixelDimensionsPag 显示的位图资源宽 320 像素，高 240 像素：

PaintSurface 处理程序通过基于显示表面的像素尺寸和位图的像素尺寸计算 x 和 y 值来使位图居中：

如果应用程序希望在其左上角显示位图，则只需传递（0，0）坐标。

**拉伸以填充矩形**  
SKCanvas 类还定义了将位图呈现为矩形的 DrawBitmap 方法，以及将位图的矩形子集呈现为矩形的另一个 DrawBitmap 方法：

```
DrawBitmap(SKBitmap bitmap, SKRect dest, SKPaint paint = null)
DrawBitmap(SKBitmap bitmap, SKRect source, SKRect dest, SKPaint paint = null)
```

在这两种情况下，位图都被拉伸以填充名为 dest 的矩形。

在第二种方法中，源矩形允许您选择位图的子集，源矩形是相对于位图的【想显示位图的哪一部分】，dest 矩形（目标矩形）相对于输出设备； 。

FillRectanglePage 通过在与画布大小相同的矩形中显示先前示例中使用的相同位图，演示了这两种方法中的第一种：

拉伸，这通常不是您想要的，通过在水平和垂直方向上不同地拉伸，图像会失真。 当以除像素大小以外的其他方式显示位图时，通常需要保留位图的原始宽高比。

不过可以 保留 纵横比 去拉伸。[参考](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/bitmaps/displaying#stretching-while-preserving-the-aspect-ratio)

**多功能的位图显示功能**  
基于 XAML 的编程环境（例如 UWP 和 Xamarin.Forms）具有在保留位图长宽比的同时扩展或缩小位图大小的功能。 尽管 SkiaSharp 不包含此功能，但是您可以自己实现。 

可以填充显示、拉伸显示（保留纵横比）、对齐显示（开始、居中、结尾）

#### **2、在 SkiaSharp 位图上创建和绘图**

您已经了解了应用程序如何从 Web，应用程序资源以及用户的图片库加载位图。 也可以在您的应用程序中创建新的位图。 最简单的方法涉及 SKBitmap 的构造函数之一：

```
SKBitmap bitmap = new SKBitmap(width, height);
```

width 和 height 参数是整数，用于指定位图的像素尺寸。 此构造函数创建一个全彩色位图，每个像素有四个字节：红色，绿色，蓝色和 alpha（不透明度）分量各一个字节。

创建新的位图后，需要在位图的表面上放置一些东西。 通常，您可以通过以下两种方式之一执行此操作：

*   使用标准的 Canvas 绘制方法在位图上进行绘制。
*   直接访问像素位。

本文演示了第一种方法：在访问 SkiaSharp 位图像素一文中讨论了第二种方法。

**在位图上绘图**  
位图表面上的绘制与视频显示器上的绘制相同。 要在视频显示上进行绘制，请从 PaintSurface 事件参数获取 SKCanvas 对象。

要在位图上绘制，请使用 SKCanvas 构造函数创建一个 SKCanvas 对象：

```
SKCanvas canvas = new SKCanvas(bitmap);
```

在位图上完成绘制后，you can dispose of the `SKCanvas` object.。 因此，通常在 using 语句中调用 SKCanvas 构造函数：

```
using (SKCanvas canvas = new SKCanvas(bitmap))
{
    ··· // call drawing function
}
```

然后可以显示位图【由另一个 SKCanvas 调用 DrawBitmap 来显示】。 程序可以基于相同的位图创建一个新的 SKCanvas 对象，并在其上进行更多绘制。

示例中 HelloBitmapPage 上将写入文本 “Hello，Bitmap！”。 在位图上，然后多次显示该位图。

HelloBitmapPage 的构造函数首先创建一个 SKPaint 对象以显示文本。 它确定文本字符串的尺寸，并使用这些尺寸创建位图。 然后，它基于该位图创建一个 SKCanvas 对象，调用 Clear，然后调用 DrawText。 用新的位图调用 Clear 总是一个好主意，因为新创建的位图可能包含随机数据。

构造函数通过创建一个 SKCanvasView 对象以显示位图：

canvas.Clear(SKColors.Aqua);  // 该参数为显示表面的背景着色：

注：您也可以在现有位图上绘制，而不必创建新的位图以在其上进行绘制。 

**3、将 SkiaSharp 位图保存到文件**

SkiaSharp 应用程序创建或修改了位图后，该应用程序可能希望将位图保存到用户的照片库中。

*   将 SkiaSharp 位图转换为特定文件格式的数据，例如 JPEG 或 PNG。
*   使用平台特定的代码将结果保存到照片库。

**文件格式和编解码器**  
当今大多数流行的位图文件格式都使用压缩来减少存储空间。压缩技术的两大类称为有损和无损。这些术语指示压缩算法是否导致数据丢失。

最受欢迎的有损格式是由联合图像专家组开发的，称为 JPEG。 JPEG 压缩算法使用称为离散余弦变换的数学工具来分析图像，并尝试删除对保持图像的视觉保真度不重要的数据。压缩程度可以通过通常称为质量的设置来控制。较高的质量设置将导致较大的文件。

相比之下，无损压缩算法分析图像的重复和像素模式，可以减少数据但不会导致任何信息丢失的方式进行编码。原始位图数据可以完全从压缩文件中恢复。当前使用的主要无损压缩文件格式是可移植网络图形（PNG）。

通常，JPEG 用于照片，而 PNG 用于手动或算法生成的图像。任何减少某些文件大小的无损压缩算法都必须增加其他文件的大小。幸运的是，大小的增加通常仅发生在包含大量随机（或看似随机）信息的数据上。

压缩算法非常复杂，足以保证两个描述压缩和解压缩过程的术语：

*   解码—读取位图文件格式并解压缩
*   编码—压缩位图并写入位图文件格式

SKBitmap 类包含几个名为 Decode 的方法，这些方法从压缩源创建 SKBitmap，所需要做的就是提供文件名，流或字节数组。解码器可以确定文件格式，并将其交给适当的内部解码功能。

另外，SKCodec 类有两个名为 Create 的方法，可以从压缩源创建 SKCodec 对象，并使应用程序更多地参与解码过程。 （SKCodec 类在 “动画 SkiaSharp 位图动画” 中与解码动画 GIF 文件有关显示。）

对位图进行编码 Encode 时，需要更多信息：编码器必须知道应用程序要使用的特定文件格式（JPEG 或 PNG 或其他格式）。如果需要有损格式，则编码器还必须知道所需的质量级别。

SKBitmap 类使用以下语法定义一个 Encode 方法：

```
public Boolean Encode (SKWStream dst, SKEncodedImageFormat format, Int32 quality)
```

编码的位图被写入可写流（SKWStream 中的 “W” 代表“可写”。）第二和第三个参数指定文件格式，并且（对于有损格式）指定所需的质量，范围为 0 到 100。

此外，SKImage 和 SKPixmap 类还定义了 Encode 方法，该方法在某种程度上更加通用，您可能会更喜欢。

您可以使用静态 SKImage.FromBitmap 方法从 SKBitmap 对象轻松创建 SKImage 对象，您可以使用 PeekPixels 方法从 SKBitmap 对象获取 SKPixmap 对象。

SKImage 定义的没有参数的 Encode 方法，并自动保存为 PNG 格式，该无参数方法非常易于使用。

**保存**

将 SKBitmap 对象编码为特定的文件格式时，通常会留下某种流对象或数据数组。一些 Encode 方法（包括 SKImage 定义的无参数的方法）返回一个 SKData 对象，可以使用 ToArray 方法将其转换为字节数组【包含已编码为特定文件格式，如 JPEG 或 PNG 的位图的字节数组】，然后将这些数据保存到文件中。

保存到应用程序本地存储中的文件非常容易，因为您可以为该任务使用标准的 System.IO 类和方法。结合使 Mandelbrot 集的一系列位图动画化的文章 [Animating SkiaSharp Bitmaps](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/bitmaps/animating#bitmap-animation) 位图动画中对此技术进行了演示。

如果要与其他应用程序共享文件，则必须将其保存到用户的照片库中。此任务需要特定于平台的代码并使用 Xamarin.Forms DependencyService。

**探索图像格式**  
这又是 SKImage 的 Encode 方法：

```
public Boolean Encode (SKWStream dst, SKEncodedImageFormat format, Int32 quality)
```

SKEncodedImageFormat 是一个枚举，其中的成员引用了 11 种位图文件格式，其中某些格式相当晦涩：

Astc - 自适应可伸缩纹理压缩  
Bmp-Windows 位图  
Dng-Adobe Digital Negative  
Gif —图形交换格式  
Ico — Windows 图标图像  
Jpeg —联合摄影专家组  
Ktx — OpenGL 的 Khronos 纹理格式  
Pkm —神奇宝贝保存文件  
Png —便携式网络图形  
Wbmp —无线应用协议位图格式（每个像素 1 位）  
Webp-Google WebP 格式  
很快您将看到，SkiaSharp 实际上仅支持其中三种文件格式（Jpeg，Png 和 Webp）。对于所有其他格式，Encode 方法不向流中写入任何内容，结果字节数组为空。

要将名为 bitmap 的 SKBitmap 对象保存到用户的照片库，您还需要 SKEncodedImageFormat 枚举的一个成员，该成员名为 imageFormat 和（对于有损格式）整数质量变量。 您可以使用以下代码将该位图保存到文件夹文件夹中名称为 filename 的文件中：

[![](http://common.cnblogs.com/images/copycode.gif)](javascript:void(0); "复制代码")

```
using (MemoryStream memStream = new MemoryStream())
using (SKManagedWStream wstream = new SKManagedWStream(memStream))
{
    bitmap.Encode(wstream, imageFormat, quality);
    byte[] data = memStream.ToArray();

    // Check the data array for content!

    bool success = await DependencyService.Get<IPhotoLibrary>().SavePhotoAsync(data, folder, filename);

    // Check return value for success!
}
```

[![](http://common.cnblogs.com/images/copycode.gif)](javascript:void(0); "复制代码")

SKManagedWStream 类派生自 SKWStream（代表 “可写流”）。 Encode 方法将编码的位图文件写入该流。 该代码中的注释涉及您可能需要执行的一些错误检查。

“保存文件格式” 页面使用类似的代码，使您可以尝试以各种格式保存位图。

**Saving finger-paint art**

位图的一种常见用法是在绘图程序中，在这里它起着称为阴影位图的作用。 所有图形都保留在位图上，然后由程序显示，位图也很方便保存图形。

SkiaSharp 中的 “[手指画](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/paths/finger-paint)” 中的文章演示了如何 使用触摸跟踪来实现原始的手指画程序。该程序仅支持一种颜色和一种笔划宽度，但是将整个图形保留在一组 SKPath 对象中。

示例中的 FingerPaintSavePage 还将整个图形保留在 SKPath 对象的集合中，但也将图形呈现在位图上，然后可以将其保存到您的照片库中。

该程序大部分与原始的 FingerPaint 程序相似。 一种增强功能是 XAML 文件现在实例化了标记为 “清除” 和“保存”的按钮：

隐藏代码的维护着一个名为 saveBitmap 的 SKBitmap 类型的字段。 每当显示表面的大小发生更改时，就会在 PaintSurface 处理程序中创建或重新创建此位图。 如果需要重新创建位图，则将现有位图的内容复制到新位图，以便无论显示表面尺寸如何变化，所有内容都将保留：

[回到顶部](#_labelTop)

三、SkiaSharp 线和路径
----------------

使用 SkiaSharp 绘制线条和图形路径（_graphics paths_）

上一节演示了 SkiaSharp SKCanvas 类包括几种绘制圆形，椭圆形，矩形，圆角矩形，文本和位图的方法。 本节和后续各节介绍与创建和渲染图形路径有关的各种类。

图形路径是 SkiaSharp 中绘制线条和曲线的最通用方法。 本节介绍如何使用 SKPath 对象绘制直线，并使用一组微小的直线（称为多段线 _polyline_）绘制可以通过算法定义的曲线。 关于 SkiaSharp 曲线和路径的下一节将讨论 SKPath 支持的各种曲线。

### 1、Lines and Stroke Caps 

线和行程。了解如何使用 SkiaSharp 绘制具有不同笔划帽的线

在 SkiaSharp 中，渲染一条直线与渲染一系列连接的直线非常不同。 但是，即使绘制单条线，也经常需要为线赋予特定的笔划宽度。 随着这些线变宽，线的末端的外观也变得重要，The appearance of the end of the line is called the _stroke cap_:

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427110633368-1399708359.png)

 对于绘制单条线，SKanvas 定义了一个简单的 DrawLine 方法，该方法的参数使用 SKPaint 对象指示线的起点和终点：

```
canvas.DrawLine (x0, y0, x1, y1, paint);
```

默认情况下，新实例化的 SKPaint 对象的 StrokeWidth 属性为 0，与呈现 1 像素粗细的线时，其值为 1 的效果相同。在诸如电话之类的高分辨率设备上，这看起来很薄，因此您可能需要将 StrokeWidth 设置为更大的值。

但是一旦开始绘制粗细的线条，就会引出另一个问题：应该如何渲染这些粗线的起点和终点？

线的起点和终点的外观称为线帽。在这种情况下，“帽子” 一词指的是一种帽子 - 位于行尾的东西。您将 SKPaint 对象的 StrokeCap 属性设置为 SKStrokeCap 枚举的以下成员之一：

*   `Butt` (the default)
*   `Square`
*   `Round`

示例：StrokeCapsPage 定义了一个 PaintSurface 事件处理程序，该处理程序循环遍历 SKStrokeCap 枚举的三个成员，同时显示枚举成员的名称并使用该笔划帽画一条线。

如您所见，Square 和 Round 笔划帽有效地将线的长度延长到了线的起点和终点的一半。 当需要确定渲染图形对象的尺寸时，此扩展很重要。

SKCanvas 类还包括另一种绘制多条线的方法，该方法有些特殊：

```
DrawPoints (SKPointMode mode, points, paint)
```

points 参数是 SKPoint 值的数组，而 mode 是 SKPointMode 枚举的成员，该枚举具有三个成员：

*   Points：渲染单个点
*   Lines：连接每对点的线
*   Polygon：连接所有连续点的多边形

### 2、Path Basics in SkiaSharp

探索 SkiaSharp SKPath 对象以组合连接的直线和曲线

图形路径最重要的功能之一就是能够定义何时应连接多条线以及何时不应该连接多条线，差异可能是显着的，以下这两个三角形的顶部表明：

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427112635360-4554744.png)

图形路径由 SKPath 对象封装。路径是一个或多个轮廓（_contours_）的集合。每个轮廓都是连接的直线和曲线的集合。轮廓没有相互连接，但是它们可能在视觉上重叠。有时，单个轮廓可以重叠。

轮廓通常始于以下 SKPath 方法的调用：

*   MoveTo 开始一个新的轮廓

该方法的参数是单个点，您可以将其表示为 SKPoint 值或单独的 X 和 Y 坐标。 MoveTo 调用在轮廓的起点和初始当前点建立一个点。

您可以调用以下方法，以一条直线或一条曲线从当前点到该方法中指定的点继续轮廓，然后该轮廓将成为新的当前点：

*   LineTo 在路径上添加一条直线
*   ArcTo 添加圆弧，即圆或椭圆圆周上的一条线
*   CubicTo 添加三次贝塞尔曲线样条
*   QuadTo 添加二次贝塞尔曲线样条
*   ConicTo 添加有理二次贝塞尔曲线样条，可以精确地渲染圆锥截面（椭圆，抛物线和双曲线）

这五种方法均未包含描述直线或曲线所需的所有信息。

这五个方法中的每一个都与由紧接其前的方法调用建立的当前点一起工作。例如，LineTo 方法基于当前点向轮廓添加一条直线，因此 LineTo 的参数仅是一个点。

SKPath 类还定义了与这六个方法同名的方法，但开头是 R：

*   RMoveTo
*   RLineTo
*   RArcTo
*   RCubicTo
*   RQuadTo
*   RConicTo

R 代表相对。这些方法与不带 R 的相应方法具有相同的语法，但相对于当前点，这些对于在您多次调用的方法中绘制路径的相似部分非常方便。

轮廓以对 MoveTo 或 RMoveTo 的另一个调用结束，该调用开始一个新轮廓，或对 Close 的调用将闭合该轮廓。

Close 方法自动从当前点到轮廓的第一个点追加一条直线，并将该路径标记为闭合，这意味着将在不使用任何笔划上限的情况下进行渲染。

打开和闭合轮廓之间的差异在 TwoTriangleContoursPage 中进行了说明，该页面使用具有两个轮廓的 SKPath 对象渲染两个三角形。第一个轮廓打开，第二个轮廓关闭。

如您所见，第一个轮廓显然是由三条相连的线组成的序列，但是末端与起点之间没有连接，两条线在顶部重叠。

第二个轮廓显然是闭合的，并且通过减少 LineTo 调用来完成，因为 Close 方法自动添加了最后一条线来闭合轮廓。

SKCanvas 仅定义一个 DrawPath 方法，在本示例中，该方法被调用两次以填充和描边路径。

填充了所有轮廓，即使没有闭合的轮廓也是如此，为了填充未封闭的路径，假定在轮廓的起点和终点之间存在一条直线。

如果从第一个轮廓删除最后一个 LineTo，或从第二个轮廓删除 Close 调用，则每个轮廓将只有两个侧面，但将被填充，就好像它是一个三角形一样。

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
public class TwoTriangleContoursPage : ContentPage
    {
        public TwoTriangleContoursPage()
        {
            Title = "Two Triangle Contours";

            SKCanvasView canvasView = new SKCanvasView();
            canvasView.PaintSurface += OnCanvasViewPaintSurface;
            Content = canvasView;
        }

        void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
        {
            SKImageInfo info = args.Info;
            SKSurface surface = args.Surface;
            SKCanvas canvas = surface.Canvas;

            canvas.Clear();

            // Create the path
            SKPath path = new SKPath();

            // Define the first contour
            path.MoveTo(0.5f * info.Width, 0.1f * info.Height);
            path.LineTo(0.2f * info.Width, 0.4f * info.Height);
            path.LineTo(0.8f * info.Width, 0.4f * info.Height);
            path.LineTo(0.5f * info.Width, 0.1f * info.Height);

            // Define the second contour
            path.MoveTo(0.5f * info.Width, 0.6f * info.Height);
            path.LineTo(0.2f * info.Width, 0.9f * info.Height);
            path.LineTo(0.8f * info.Width, 0.9f * info.Height);
            path.Close();

            // Create two SKPaint objects
            SKPaint strokePaint = new SKPaint
            {
                Style = SKPaintStyle.Stroke, //轮廓
                Color = SKColors.Magenta,
                StrokeWidth = 50  //设置为小点 顶部就看似重合了
            };

            SKPaint fillPaint = new SKPaint
            {
                Style = SKPaintStyle.Fill, //填充
                Color = SKColors.Cyan
            };

            // Fill and stroke the path。。填充并描边
            //canvas.DrawPath(path, fillPaint);
            canvas.DrawPath(path, strokePaint);
        }
    }
```

View Code

请记住，SKPath 对象仅定义一个几何图形：一系列点和连接。 仅当 SKPath 与 SKPaint 对象组合时，路径才会以特定的颜色，笔触宽度等进行渲染。

另外，请记住，传递给 DrawPath 方法的 SKPaint 对象定义了整个路径的特征。 如果要绘制需要几种颜色的东西，则必须为每种颜色使用单独的路径。

正如线条的开始和结尾的外观是由笔划帽定义的一样，两条线条之间的连接的外观是由笔触联接（拐角处）定义的。 您可以通过将 SKPaint 的 StrokeJoin 属性设置为 SKStrokeJoin 枚举的成员来指定它：

*   `Miter` for a pointy join
*   `Round` for a rounded join，圆角连接
*   `Bevel` for a chopped-off join

StrokeJoinsPage 显示了这三个笔触连接，其代码类似于 StrokeCapspage。

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427114937077-66158943.png)

###  3、The Path Fill Types

SkiaSharp 路径填充类型可能带来的不同效果

路径中的两个轮廓可以重叠，组成一个轮廓的线可以重叠。 任何封闭区域都可以填充，但是您可能不想填充所有封闭区域。 

填充算法由 SKPath 的 SKFillType 属性控制，您可以将其设置为 SKPathFillType 枚举的成员：

*   `Winding`, the default
*   `EvenOdd`
*   `InverseWinding`
*   `InverseEvenOdd`

winding and even-odd 算法都基于从该区域绘制到无限远的假设线来确定是否填充了任何封闭区域。该线与构成路径的一条或多条边界线交叉。

在 Winding 模式下，如果在一个方向上绘制的边界线的数量与在另一方向上绘制的边界线的数量平衡，则不会填充该区域。否则，该区域将被填充。如果边界线的数量为 odd，则奇偶算法将填充一个区域。

对于许多常规路径，Winding 算法通常会填充路径的所有封闭区域。EvenOdd 算法通常会产生更有趣的结果。

经典示例是五角星，如 FivePointedStarPage 实例化两个 Picker 视图，以选择 路径填充类型以及是描边路径还是填充路径，或者两者都是，以及选择顺序：

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427153101582-1864819516.png)

### 4、折线和参数方程式

使用 SkiaSharp 渲染可以用参数方程式定义的任何行

在本指南的 “ [SkiaSharp 曲线和路径”](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/user-interface/graphics/skiasharp/curves/text-paths) 部分中，您将看到 SKPath 定义的用于渲染某些类型曲线的各种方法。 但是，有时有必要绘制 SKPath 不直接支持的曲线。

在这种情况下，可以使用折线（连接的线的集合）来绘制可以数学定义的曲线。 如果使线足够小且足够多，结果将看起来像曲线，例如，下面这个螺旋实际上是 3600 条小线：

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200427153322119-706730128.png)

有点类似极坐标方程

通常，最好根据一对参数方程式定义曲线。这些是 X 和 Y 坐标的等式，它们取决于第三个变量，有时在时间上称为 t。例如，以下参数方程式定义了一个半径为 1 的圆，该圆的中心为 0 到 1 的 t 的点（0，0）。

x = cos（2πt）

y = sin（2πt）

### 5、点和短划线

### 6、手指画图

用手指在画布上绘画。

SKPath 对象可以不断更新和显示。 此功能允许将路径用于交互式绘图，例如在手指画程序中。

Xamarin.Forms 中的触摸支持不允许跟踪屏幕上的各个手指，因此开发了 Xamarin.Forms 触摸跟踪效果以提供其他触摸支持。 从[效果中调用事件](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/effects/touch-tracking)一文中介绍了此效果。

示例程序 “Touch-Tracking Effect Demos” 包括两个使用 SkiaSharp 的页面，其中包括一个手指绘画程序。

 .NET Standard 库项目包括 TouchEffect 类，TouchActionType 枚举，TouchActionEventHandler 委托和 TouchActionEventArgs 类。 每个平台项目都包括该平台的 TouchEffect 类。 iOS 项目还包含一个 TouchRecognizer 类。

FingerPaintPag 是手指画的简化实现。 它不允许选择颜色或笔触宽度，它无法清除画布，当然也不能保存您的图稿。

[回到顶部](#_labelTop)

四、SkiaSharp Transforms
----------------------

SkiaSharp 支持作为 SKCanvas 对象的方法实现的传统图形转换。 在数学上，变换会更改您在绘制图形对象时在 SKCanvas 绘图函数中指定的坐标和尺寸。 变换通常便于绘制重复的图形或动画。 如果不使用转换，则无法使用某些技术（例如旋转位图或文本）。

SkiaSharp 转换支持以下操作：

*   转换 以将坐标从一个位置移动到另一位置
*   缩放 以增加或减少坐标和大小
*   旋转 以围绕点旋转坐标
*   倾斜 以水平或垂直移动坐标，以使矩形成为平行四边形

这些被称为仿射变换（ _affine_ transforms）。 仿射变换始终保留平行线，绝不会导致坐标或大小变为无限大。 正方形永远不会变换为平行四边形，圆形永远不会变换为椭圆形。

SkiaSharp 还支持基于标准 3×3 变换矩阵的非仿射变换（也称为投影变换或透视变换）。 非仿射变换允许将正方形变换为任何凸四边形，这是一个四边形，所有内角均小于 180 度。 非仿射变换可以使坐标或大小变为无限，但是它们对于 3D 效果至关重要。

**SkiaSharp 和 Xamarin.Forms 转换之间的区别**  
Xamarin.Forms 还支持类似于 SkiaSharp 中的转换。 Xamarin.Forms VisualElement 类定义以下转换属性：

*   TranslationX 和 TranslationY
*   Scale
*   `Rotation`, `RotationX`, and `RotationY`

RotationX 和 RotationY 属性是透视转换，可创建准 3D 效果。

SkiaSharp 转换和 Xamarin.Forms 转换之间存在几个关键区别：

1、第一个区别是 SkiaSharp 转换应用于整个 SKCanvas 对象，而 Xamarin.Forms 转换应用于单个 VisualElement 派生对象。

（您可以将 Xamarin.Forms 转换应用于 SKCanvasView 对象本身，因为 SKCanvasView 是从 VisualElement 派生的，但是在该 SKCanvasView 中，SkiaSkarp 转换也适用。）

SkiaSharp 变换相对于 SKCanvas 的左上角，而 Xamarin.Forms 变换相对于应用它们的 VisualElement 的左上角。在应用缩放和旋转变换时，此差异非常重要，因为这些变换始终相对于特定点。

2、真正的最大区别是，SKiaSharp 转换是方法，而 Xamarin.Forms 转换是属性。

这是语义上的区别，而不仅仅是语法上的区别：

SkiaSharp 转换执行操作，而 Xamarin.Forms 转换设置状态。

SkiaSharp 变换适用于随后绘制的图形对象，但不适用于应用变换之前绘制的图形对象。相反，设置属性后，Xamarin.Forms 转换将应用于先前渲染的元素。

SkiaSharp 转换在调用方法时是累积（多次设置平移，坐标会累积计算）的；当属性设置为另一个值时，将替换 Xamarin.Forms 转换。

### 1、The Translate Transform

了解如何使用平移变换来移动 SkiaSharp 图形

SkiaSharp 中最简单的转换类型是 translate。 此变换可在水平和垂直方向上移动图形对象。 从某种意义上说，平移是最不必要的变换，因为通常可以通过简单地更改绘图功能中使用的坐标来达到相同的效果。

但是，在渲染路径时，所有坐标都封装在路径中，因此应用平移变换来移动整个路径要容易得多。

translate 对于动画和简单的文字效果也很有用。

SKCanvas 中的 Translate 方法，这些参数导致随后绘制的图形对象在水平和垂直方向上移动：

```
public void Translate (Single dx, Single dy)
public void Translate (SKPoint point)
```

示例：AccumulatedTranslatePage，演示了 Translate 方法的多次调用是累积的，它显示同一矩形的 20 个版本，每个版本与上一个矩形的偏移量刚好足以使它们沿对角线延伸。

平移对 之后的图像有影响。即画完一个 然后在移动坐标，画下一个。

![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

```
public class AccumulatedTranslatePage : ContentPage
    {
        public AccumulatedTranslatePage()
        {
            Title = "Accumulated Translate";

            SKCanvasView canvasView = new SKCanvasView();
            canvasView.PaintSurface += OnCanvasViewPaintSurface;
            Content = canvasView;
        }

        void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
        {
            SKImageInfo info = args.Info;
            SKSurface surface = args.Surface;
            SKCanvas canvas = surface.Canvas;

            canvas.Clear();

            using (SKPaint strokePaint = new SKPaint())
            {
                strokePaint.Color = SKColors.Black;
                strokePaint.Style = SKPaintStyle.Stroke;
                strokePaint.StrokeWidth = 3;

                int rectangleCount = 20;
                SKRect rect = new SKRect(0, 0, 250, 250);
                float xTranslate = (info.Width - rect.Width) / (rectangleCount - 1);  //可移动的距离 除以 想移动的次数
                float yTranslate = (info.Height - rect.Height) / (rectangleCount - 1);

                for (int i = 0; i < rectangleCount; i++)
                {
                    canvas.DrawRect(rect, strokePaint);  
                    canvas.Translate(xTranslate, yTranslate);//平移对 之后的图像有影响。即画完一个 然后在移动坐标，画下一个。
                }
            }
        }
    }
```

View Code

Translate 变换的另一个常见用途是渲染视觉对象，该对象最初是使用方便绘制的坐标创建的。 例如，您可能想指定一个以（0，0）为中心的模拟时钟的坐标。 然后，您可以使用 转换在所需位置显示时钟。 HendecagramArrayPage 中演示了此技术。 

动画通常涉及变换。 Hendecagram 动画页面将 11 个点的星星绕一圈移动。 HendecagramAnimationPage 类从一些字段开始，并覆盖 OnAppearing 和 OnDisappearing 方法以启动和停止 Xamarin.Forms 计时器。

可以将星星 替换为文本。

### 2、The Scale Transform

translate 转换可以将图形对象从一个位置移动到另一位置。 相反，比例转换会更改图形对象的大小。

### 3、The Rotate Transform

通过旋转变换，SkiaSharp 图形对象摆脱了与水平轴和垂直轴对齐的限制

为了绕点（0，0）旋转图形对象，SkiaSharp 支持 RotateDegrees 方法（旋转度数）和 RotateRadians（旋转弧度）方法：

```
public void RotateDegrees (Single degrees)
public Void RotateRadians (Single radians)
```

360 度的圆与两个π弧度相同，因此很容易在两个单位之间进行转换。  .NET Math 类中的所有三角函数均使用弧度单位。

顺时针旋转可增加角度。 （尽管按惯例，笛卡尔坐标系上的旋转是逆时针方向，但顺时针旋转与 Y 坐标的增加一致，如 SkiaSharp 中所述。）允许使用负角和大于 360 度的角度。

旋转的变换公式比平移和缩放的公式复杂。 对于α角，转换公式为：

x'= x•cos（α）– y•sin（α）

y` = x•sin（α）+ y•cos（α）

BasicRotatePage 演示了 RotateDegrees 方法。

BasicRotate.xaml.cs 文件显示一些文本，其基线在页面上居中，并基于 Slider（范围介于–360 到 360 之间）对其进行旋转。这是 PaintSurface 处理程序的相关部分：

因为旋转以画布的左上角为中心，所以对于该程序中设置的大多数角度，文本在屏幕外旋转：

通常，您会希望使用以下版本的 RotateDegrees 和 RotateRadians 方法来旋转以指定的枢轴点为中心的内容：

```
public void RotateDegrees (Single degrees, Single px, Single py)
public void RotateRadians (Single radians, Single px, Single py)
```

 示例 CenteredRotatePage：将旋转中心设置为与放置文本相同的点。

```
canvas.RotateDegrees((float)rotateSlider.Value, info.Width / 2, info.Height / 2); //以中心点来旋转
canvas.DrawText(Title, info.Width / 2, info.Height / 2, textPaint);
```

其实 RotateDegrees 调用等效于 两个 Translate 调用和一个非居中的 RotateDegrees：

```
canvas.Translate(info.Width / 2, info.Height / 2);
canvas.RotateDegrees((float)rotateSlider.Value);
canvas.Translate(-info.Width / 2, -info.Height / 2);
canvas.DrawText(Title, info.Width / 2, info.Height / 2, textPaint);
```

在特定位置显示文本的 DrawText 调用 等效于该位置的 Translate 调用，后跟（0，0）点的 DrawText：

```
canvas.Translate(info.Width / 2, info.Height / 2);
canvas.RotateDegrees((float)rotateSlider.Value);
canvas.Translate(-info.Width / 2, -info.Height / 2);
canvas.Translate(info.Width / 2, info.Height / 2);
canvas.DrawText(Title, 0, 0, textPaint);
```

其中两个 Translate 抵消，所以可以等效为：

```
canvas.Translate(info.Width / 2, info.Height / 2);
canvas.RotateDegrees((float)rotateSlider.Value);
canvas.DrawText(Title, 0, 0, textPaint);
```

从概念上讲，这两种转换的应用顺序与它们在代码中的显示方式相反。 DrawText 调用在画布的左上角显示文本。 RotateDegrees 调用相对于左上角旋转该文本。 然后，Translate 调用将文本移动到画布的中心。

通常有几种 组合旋转和平移的方法。 RotatedTextPage 创建以下显示：

![](https://img2020.cnblogs.com/blog/727485/202004/727485-20200428102118140-2060298401.png)

通常可以从更多全局转换开始（循环外边），然后是更多本地转换（循环里面）。这通常是组合旋转和平移的最简单方法。

例如，假设您要绘制一个图形对象，该对象围绕其中心旋转，就像一个在其轴上旋转的行星一样。但是，您还希望该对象围绕屏幕中心旋转，就像行星围绕太阳旋转一样。

您可以通过将对象放置在画布的左上角，然后使用动画将其围绕该角（左上角）旋转来实现。接下来，像轨道半径一样水平平移对象。现在，围绕原点应用第二个动画旋转，这使对象绕转角旋转，现在平移到画布的中心。

示例：RotateAndRevolvePage

示例 UglyAnalogClock 程序 使用旋转来绘制时钟的分钟和小时标记并旋转指针。 该程序使用基于以点（0，0）为中心，半径为 100 的圆的任意坐标系绘制时钟。它使用平移和缩放在页面上扩展和居中该圆。

Translate 和 Scale 调用全局应用于时钟，因此这些是在初始化 SKPaint 对象之后首先调用的：

必须全天围成一圈绘制 60 个具有两种不同大小的标记。 DrawCircle 调用在相对于时钟中心的点（0，–90）处绘制该圆，对应于 12:00。 在每个刻度线之后，RotateDegrees 调用将旋转角度增加 6 度。 angle 变量仅用于确定是绘制大圆还是小圆：

（-90 这个数 相当于确定 时钟的半径）

[回到顶部](#_labelTop)

更多参考
----

[Mono/SkiaSharp](https://hub.fastgit.org//mono/SkiaSharp)

[.Net Core 使用 SkiaSharp 绘制小程序分享图](https://www.cnblogs.com/Intouchables/p/10090555.html)

[](https://www.cnblogs.com/Intouchables/p/10090555.html)[在. Net Core 2.1 下使用 SkiaSharp 进行图片处理](https://cloud.tencent.com/developer/article/1404320)

[ASP.NET Core 使用 SkiaSharp 实现验证码](https://www.cnblogs.com/maxzhang1985/p/8137199.html)

[](https://www.cnblogs.com/maxzhang1985/p/8137199.html)[SkiaSharp drawText 中文乱码问题](https://www.cnblogs.com/IWings/p/9461845.html)

[android 使用 canvas 画线，位移，旋转，绘制五角星](https://blog.csdn.net/weixin_36888674/article/details/82893001)

分类: [【移动开发】](https://www.cnblogs.com/peterYong/category/1548216.html) 标签: [SkiaSharp](https://www.cnblogs.com/peterYong/tag/SkiaSharp/), [Xamarin.Forms](https://www.cnblogs.com/peterYong/tag/Xamarin.Forms/) [好文要顶](javascript:void(0);) [关注我](javascript:void(0);) [收藏该文](javascript:void(0);) [![](https://common.cnblogs.com/images/icon_weibo_24.png)](javascript:void(0); "分享至新浪微博") [![](https://common.cnblogs.com/images/wechat.png)](javascript:void(0); "分享至微信") [![](https://pic.cnblogs.com/face/727485/20190531113306.png)](https://home.cnblogs.com/u/peterYong/) [peterYong](https://home.cnblogs.com/u/peterYong/)  
[粉丝 - 90](https://home.cnblogs.com/u/peterYong/followers/) [关注 - 86](https://home.cnblogs.com/u/peterYong/followees/)  
[+ 加关注](javascript:void(0);) 1 0 [«](https://www.cnblogs.com/peterYong/p/12024394.html) 上一篇： [使用 MailKit 发送邮件](https://www.cnblogs.com/peterYong/p/12024394.html "发布于 2020-04-10 19:11")  
[»](https://www.cnblogs.com/peterYong/p/12987095.html) 下一篇： [PKI/CA 与数字证书](https://www.cnblogs.com/peterYong/p/12987095.html "发布于 2020-05-10 13:23") posted @ 2020-04-24 18:57  [peterYong](https://www.cnblogs.com/peterYong/)  阅读 (2446)  评论 (0)  [编辑](https://i.cnblogs.com/EditPosts.aspx?postid=12767465)  [收藏](javascript:void(0))  [举报](javascript:void(0))