# Getting Started - Guided tour of the creation of a new OpenSilver application

The development experience with OpenSilver is very similar to that of Silverlight, WPF and Universal Platform.

OpenSilver is distributed as a NuGet package (on [NuGet.org](https://www.nuget.org/packages/OpenSilver)) and as a [VSIX extension](https://www.opensilver.net/download.aspx) for Visual Studio 2019 (or higher) containing the project templates.

To create a new OpenSilver-type project, it is recommended to download the project templates first. To do that, go to https://OpenSilver.NET , click Download, log in with your Microsoft account and download the OpenSilver.VSIX file. This extension for Visual Studio will install project templates and other elements like the XAML editor.

![OpenSilver Website](/images/1.OpenSilverWebsite.png "The OpenSilver.NET site")

Next, open Visual Studio and click on "Create a new project" and choose "OpenSilver Application". Note that there is also a "UWP-Compatible" version of OpenSilver, which uses the XAML dialect of UWP instead of that of Silverlight, allowing increased compatibility with Universal Platform.

![Windows prompt for new project](/images/2.NewDialogProjectWithVB.png "The window for creating a new project")

Once the solution is created, you will see that it has three projects.

![Solution explorer](/images/3.solutionExplorer.png "The Solution Explorer showing newly created projects for C#")
![Solution explorer](/images/3.solutionExplorerWithVB.png "The Solution Explorer showing newly created projects for VB.NET")

The first one is where you will place the files for your application. Its structure is identical to that of a new Silverlight project. It notably contains the files:
			
	* For C# code migration :- App.xaml, App.xaml.cs, MainPage.xaml and MainPage.xaml.cs. 
	* For VB.NET code migration :- App.xaml, App.xaml.vb, MainPage.xaml and MainPage.xaml.vb. 


The second project, named with the suffix ".Browser", is the one you will have to launch to test your application in the browser. It plays a role similar to the ".Web" project that existed for Silverlight applications. This is an ASP.NET Blazor Client-Side project. This project references the first project and serves as an entry point to launch the application in WebAssembly.


Finally the third project, named with the suffix ".Simulator" is the one that you will have to launch to test your application in the Simulator. We will talk more about the Simulator later. Its main interest is to allow debugging with the very powerful tools of the .NET Framework, such as the possibility of moving the execution point or executing C# or VB.NET code at runtime in the "Immediate" window, things that are not possible in the browser.

#### As a test, let's create a Button in out Xaml application:

1. Add the following XAML code inside the MainPage.xaml file, replacing the `<Canvas>` element:

```
<StackPanel HorizontalAlignment="Left">
  <TextBlock Text="Enter some text below:"/>
  <TextBox x:Name="MyTextBox1"/>
  <Button Content="Click me" Click="Button_Click"/>
</StackPanel>
```

![MainPage.xaml](/images/4.MainPage.xaml.png "The modified MainPage.xaml page")  

2. Add the following code:

- In C#

 Inside the MainPage.xaml.cs file:
```
			void Button_Click(object sender, RoutedEventArgs e)
			{
			    MessageBox.Show("You entered the following text: " + MyTextBox1.Text);
			}
```
![MainPage.xaml.cs](/images/5.MainPage.xaml.cs.png "The modified MainPage.xaml.cs page")

- In VB.NET

Inside the MainPage.xaml.vb file:
	
```
			Private Sub Button_Click(sender As Object, e As RoutedEventArgs)
			{
			    MessageBox.Show("You entered the following text: " + MyTextBox1.Text)
			}
```
![MainPage.xaml.vb](/images/5.MainPage.xaml.vb.png "The modified MainPage.xaml.vb page")

#### Now that the modifications are done, we can test our application.

Let's recompile the solution and launch the project with the suffix ".Browser". The default browser opens and the application runs.

![application displaying a message in the browser](/images/6.AppBrowser.png "The application running in the browser")

Now, if we enter some text and press the button. A dialog box will appear with the text entered.

![application displaying a message in the browser](/images/7.DialogBrowser.png "The application displaying a message in the browser")

To see that the application runs in WebAssembly (currently in interpreted mode), we can go to the browser development tools (Chrome in this example) by pressing the F12 key, then go to the "Network" tab and refresh the page by pressing F5. Microsoft .NET assemblies (such as "mscorlib.dll" and "System.dll") are downloaded by the browser instead of JavaScript files.

![Network tab](/images/8.NetworkTab.png "Network tab in Chrome's development tools")

Now let's go back to Visual Studio and launch the project with the suffix ".Simulator"

Note: if a message indicates that the Simulator is not configured, simply open the "Package Manager Console" and wait for the Simulator to be automatically configured, then restart the project.

The simulator appears and shows the application. Like before, we can enter some text and click the button to make a idalog box appear.

![Application in the Simulator](/images/9.AppSimulator.png "The application running in the Simulator")

Let's put a breakpoint inside the Button_Click method, then press the button. It is possible to inspect the variables and to do step-by-step debugging.

![Breakpoint](/images/10.Breakpoint.png "C# code Variables inspection at a Breakpoint")
![Breakpoint](/images/10.Breakpoint.vb.png "VB.NET code Variables inspection at a Breakpoint")


Once done, press the F5 key to continue.

In the Simulator window, there is an "Inspect Visual Tree" button in the top right corner. Pressing it will open a panel letting you explore the visual tree that constitutes the UI of the application.

![Breakpoint](/images/11.VisualTree.png "The Simulator visual tree inspector")
