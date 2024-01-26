# Getting Started - Guided tour of the creation of a new OpenSilver application via dotnet CLI

The development experience with OpenSilver is very similar to that of Silverlight, WPF and Universal Platform.

OpenSilver is distributed as a NuGet package (on [NuGet.org](https://www.nuget.org/packages/OpenSilver)) for those who prefer to use the dotnet CLI a NuGet package called "Opensilver CLI templates" is availablable.

## OpenSilver cross-platform CLI tools
OpenSilver now offers two methods to initiate a new project from a template. The first is the traditional VSIX, which installs a few pre-configured templates directly into Visual Studio. The second option leverages the cross-platform .NET Core CLI interface.

### What is the .net CLI?
The .NET Command-Line Interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET applications1. The .NET CLI is included with the .NET SDK and now OpenSilver supports also this workflow.

That way you can create new projects on any platform like Linux, MacOS or Widnows and then use your favourite IDE for development, like VSCode.

## Steps 

### 1. The first step is to install the nuget package from nuget.org to do so use this command line:
```
nuget install "Opensilver CLI templates"
```
This will download and install the latest templates (they comes in C#, VB and FX flavors).

### 2. Check if the templates are installed correctly
 To check if the templates are installed correctly on the system you can use the command:
 
 ```
dotnet new list
- OR - 
dotnet new -l 
 ```

This command will display the pre-installed .NET Core project templates. The list includes details such as the name of the templates, the short name of the template, default programming language, and the template tags. That way you should see three new templates under the category OpenSilver.CLI.Tools

The output should be similar to this:

 ```
 These templates matched your input:
 WPF Application     wpf                         [C#],VB     Common/WPF
 Template Name                                  Short Name                  Language    Tags
 ---------------------------------------------  --------------------------  ----------  ------------------------------------------------------------------------------------------
 Opensilver business (OpenRia) web application  opensilverbusinessapp       [C#],VB,F#  common/library/opensilver/xaml
 Opensilver class library                       opensilverlib               [C#],VB,F#  common/opensilver/xaml/VB/C#/Class Library
 Opensilver web application                     opensilverapp               [C#],VB,F#  common/library/opensilver/xaml/VB
 .NET MAUI App                                  maui                        [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/Windows/Tizen
 .NET MAUI Blazor Hybrid App                    maui-blazor                 [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/Windows/Tizen/Blazor/Blazor Hybrid
 .NET MAUI Class Library                        mauilib                     [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/Windows/Tizen
 .NET MAUI ContentPage (C#)                     maui-page-csharp            [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/WinUI/Tizen/Xaml/Code
 .NET MAUI ContentPage (XAML)                   maui-page-xaml              [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/WinUI/Tizen/Xaml/Code
 .NET MAUI ContentView (C#)                     maui-view-csharp            [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/WinUI/Tizen/Xaml/Code
 .NET MAUI ContentView (XAML)                   maui-view-xaml              [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/WinUI/Tizen/Xaml/Code
 .NET MAUI ResourceDictionary (XAML)            maui-dict-xaml              [C#]        MAUI/Android/iOS/macOS/Mac Catalyst/WinUI/Xaml/Code
 ```

### 3. Create your first OpenSilver project via the CLI

In order to create your first OpenSilver app you have to choose the available template you want to use (WebApp, Business app etc). and then issue the command:

 ```
	dotnet new opensilverapp -n MyProject -ta net7.0
 ```

This will create in the current directory an new Opensilver web project called "**MyProject**" targeting .net 7.0 (the default). Remember that you must use the short name of the template not the full template name. That are: **opensilverbusinessapp, opensilverapp, opensilverlib**. 
 
For your convenience our templates will also take care of restoring the necessary nuget packages from the    default repositories.

  For more information about the command line switches you can run this command to get all the information you need for each template.

 ```
	dotnet new opensilverapp -h
 ```

  If you need help for another OpenSilver template, let's say the Class Library template just change the name of the template as follows:

 ```
	dotnet new opensilvercl -h
 ```
### 4. That's it
With those simple steps you will be able to create ready to run applications in OpenSilver on Linux, Mac or windows. Please note that is also possible create new projects via VSCode since our templates are registered globally.

## Use the VS Code CLI templates in Visual Studio 2022 or later 

To use VS Code CLI templates in Visual Studio 2022, you can follow these steps:

### Install Visual Studio Code Integration Extension:
1. Open Visual Studio 2022.
2. Go to Extensions (Ctrl+Shift+X).
3. Search for "Visual Studio Code Integration" extension and install it.
4. Access VS Code CLI Templates.

### Once the extension is installed, navigate to File > New > Project.
In the "Create a new project" dialog, select "OpenSilver" category.
You should see the list of available templates, which are based on the VS Code CLI templates.
Create Project:

Choose the desired template and proceed with creating your project as you normally would in Visual Studio.

### Use CLI Commands (Optional):

If you prefer, you can also utilize CLI commands directly within Visual Studio's integrated terminal to interact with your OpenSilver project.
By following these steps, you can leverage the VS Code CLI templates within Visual Studio 2022 for your OpenSilver projects.

If you still encounter any issues, please contact:
- the OpenSilver team at: https://opensilver.net/contact.aspx