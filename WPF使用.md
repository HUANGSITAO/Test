# WPF使用 #
## 目录 ##
1. WPF使用PictureBox
2. WPF窗体关闭按钮事件(关闭程序时需要做的一些处理)
3. 点击关闭按钮或ESC按钮程序退出
4. C++中使用WPF图片资源不能显示
5. 命名空间“Microsoft”中不存在类型或命名空间名称“Windows”(是否缺少程序集引用?)
6. 添加图片代码后程序一直中断，提示“System.Windows.Markup.XamlParseException”类型的未经处理的异常在 PresentationFramework.dll 中发生错误 
7. 文本框透明
8. 窗体移动
## 1.WPF使用PictureBox ##
添加引用WindowsFormsIntegration，否则不能使用WindowsFormsHost.</br>
添加引用System.Windows.Forms, 否则不能使用PictureBox控件</br>
<pre><code>xmlns:wfi ="clr-namespace:System.Windows.Forms.Integration;assembly=WindowsFormsIntegration"
xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"</code></pre>
使用
<pre><code>< WindowsFormsHost Name="WinFormsHost" Height="440" Width="690" HorizontalAlignment="Left">
	< wf:PictureBox x:Name="picture" SizeMode="Normal"></wf:PictureBox>
< /WindowsFormsHost>
</code></pre>
完整代码
<pre><code>&lt Window x:Class="WpfApplication1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:wfi ="clr-namespace:System.Windows.Forms.Integration;assembly=WindowsFormsIntegration"
        Title="MainWindow" Height="583" Width="1132"
        xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms">
    &lt StackPanel Background="LightBlue" Height="513" Width="1077">
        &lt StackPanel Orientation="Horizontal">
            &lt WindowsFormsHost Name="WinFormsHost" Height="440" Width="690" HorizontalAlignment="Left">
                &lt wf:PictureBox x:Name="picture" SizeMode="Normal"></wf:PictureBox>
            &lt /WindowsFormsHost>
            &lt ListBox Name="ListBoxLog" />
        &lt /StackPanel>
    &lt /StackPanel>
&lt /Window>
</code></pre>
## 2. WPF窗体关闭按钮事件(关闭程序时需要做的一些处理) ##
在.xaml中添加以下代码或者也可以在窗体的属性窗口中实现。
<pre><code>Closing="MainWindow_Closing"</code></pre>
在.cs文件中，界面上有一个文本框，如果点击关闭按钮文本框数据不为0，弹出提示对话框**第二个参数的含义位置，可能是e.Cancel为true窗体关闭，为true则不关闭**
<pre><code>private void MainWindow_Closing(object sender, System.ComponentModel.CancelEventArgs e)
        {
            if (!this.TextBox_ExpData.Text.Equals("0"))
            {
                MessageBoxResult result = MessageBox.Show("数据有变更，?是否保存数据变更？", "WPF实害例", MessageBoxButton.YesNoCancel, MessageBoxImage.Question);
                if (result == MessageBoxResult.Yes)
                {
                    MessageBox.Show("数据被保存。");
                    e.Cancel = false;
                }
                else if (result == MessageBoxResult.No)
                {
                    e.Cancel = false;
                }
                else
                {
                    e.Cancel = true;
                }
            }
            else
            {
                e.Cancel = false;
            }
        } 
</code></pre>
## 3. 点击关闭按钮或ESC按钮程序退出 ##
关闭当前窗体
<pre><code>this.close()；</code></pre>
关闭全部窗体并退出程序**但是有时候程序并没有退出，原因不明**
<pre><code>Application.Current.Shutdown();  </code></pre>
## 4. C++中使用WPF图片资源不能显示 ##
1. 把图片资源转为矢量图路径；
2. 图片资源引用的肯定是本地的， 你需要在工程或者程序目录下添加图片资源。
## 5. 命名空间“Microsoft”中不存在类型或命名空间名称“Windows”(是否缺少程序集引用?) ##
添加引用PresentationFramework.Aero
## 6. 添加图片代码后程序一直中断 ##
[https://social.msdn.microsoft.com/Forums/onedrive/zh-CN/8b80b1ae-93f5-4b8e-a253-60658df38e6a/wpf?forum=wpfzhchs](https://social.msdn.microsoft.com/Forums/onedrive/zh-CN/8b80b1ae-93f5-4b8e-a253-60658df38e6a/wpf?forum=wpfzhchs)
### 错误信息 ###
“System.Windows.Markup.XamlParseException”类型的未经处理的异常在 PresentationFramework.dll 中发生 

其他信息: “在“System.Windows.Baml2006.TypeConverterMarkupExtension”上提供值时引发了异常。”，行号为“6”，行位置为“10”。

如有适用于此异常的处理程序，该程序便可安全地继续运行。</br>
1. xaml中如果添加图片，图片资源应该放在程序中，在WPF项目中右键->添加文件夹->改名Images->添加现有项,把需要的图片都放进去。</br>
2. 使用时代码路径一定要对，之前错误的时候路径写的是"/Images/1.png"改为"Images/1.png就对了。
## 7. 文本框透明 ##
1. BorderThickness="0"
2. BorderBrush="Transparent"
## 8. 窗体移动 ##
xaml中
<pre><code>
</code></pre>