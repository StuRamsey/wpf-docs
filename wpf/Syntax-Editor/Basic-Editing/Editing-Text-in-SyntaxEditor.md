---
layout: post
title: Editing Text of the Edit Control | Syncfusion
description: This section gives detailed description on Editing Text and Indentation feature in the EditControl WPF.
platform: wpf
control: Syntax Editor
documentation: ug
---

## Editing Text in EditControl WPF

[EditControl](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl_members.html) supports displaying or editing string values with any number of lines. It also supports all basic editing operations such as typing, cut, copy, paste, delete, backspace, undo and redo operations.

[EditControl](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl_members.html) supports performing edit operations through keyboard and mouse. It supports shortcut keys for basic editing operations such as cut, copy, paste, undo and redo operations. EditControl also has a built-in context menu to perform common editing operations such undo, redo, cut, copy, paste, select all operations using mouse. User can enable/ disable the built- in context menu.  For more information refer to [Default Context Menu](https://help.syncfusion.com/wpf/syntax-editor/basic-editing/default-context-menu).

[Text](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl~Text.html) property of the EditControl contains the text available in the EditControl at any point of time. The [Text](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl~Text.html) property of EditControl gets updated when you edit the text in the control by typing, editing the text by cut, paste, delete, undo or redo operations or by setting the Text property exclusively at runtime. The TextChanged event of EditControl gets raised when the Text property gets changed. Refer to [EditControl Events](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl_members.html ) section to know more about TextChanged and other events available in EditControl.

Set a simple string as EditControl’s Text by using the following line of code.

{% tabs %}

{% highlight XAML %}

<syncfusion:EditControl x:Name="editControl" Text="This is Syncfusion's EditControl"/>

{% endhighlight %}

{% highlight C# %}

editControl.Text = "Setting Text property from code behind (C#)";

{% endhighlight %}

{% endtabs %}

To set a multi-line string as Text property through **XAML**, String class in **mscorlib**.**dll** can be used with **xml**:**space**=”**preserve**”. The following lines of code can be used to set a multiline text from **XAML**.

{% tabs %}

{% highlight XAML %}

<syncfusion:EditControl x:Name="editControl">

<library:String xml:space="preserve" xmlns:library="clr-namespace:System;assembly=mscorlib">Setting multiline

Text using String class in mscorlib.dll.

When preserve is used, XAML considers the indentation spaces as empty spaces.

</library:String>

</syncfusion:EditControl>



{% endhighlight %}

{% endtabs %}


![MultiLine in EditContro in XAML](Editing-Text-in-EditControl_images/Editing-Text-in-EditControl_img1.jpeg)

{% tabs %}

{% highlight C# %}

editControl.Text = @"Setting multi-line text" + Environment.NewLine + "from C# using" + Environment.NewLine + "Environment.NewLine.";


{% endhighlight %}

{% endtabs %}


![MultiLine in EditControl in CodeBehind](Editing-Text-in-EditControl_images/Editing-Text-in-EditControl_img2.jpeg)

## Indentation in EditControl
[EditControl](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl_members.html) allows to auto indent the text when enter key pressed to add new lines. Auto indentation can be enabled by setting [IsAutoIndentationEnabled](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl~IsAutoIndentationEnabled.html) to 'true'. Auto indentation works based on [IndentingOptions](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl~IndentingOptions.html) property which has following options,

* None
* Smart
* Block

#### IndentationOptions (None)
When <kbd>ENTER</kbd>  key is pressed, edit cursor will move to beginning of the next line.

{% tabs %}

{% highlight XAML %}

<syncfusion:EditControl Name="Edit1" Background="White" Margin="0" IsAutoIndentationEnabled="True" IndentingOptions="None" Foreground="Black" ShowLineNumber="True" EnableIntellisense="False">
</syncfusion:EditControl>

{% endhighlight %}

{% highlight C# %}

    EditControl editControl = new EditControl() {Height = 200, Width = 200, Background = Brushes.White, Foreground = Brushes.Black };

    editControl.IndentingOptions = IndentingOptions.None;
    this.Content = editControl;

{% endhighlight %}    
{% endtabs %}     

![IndentingOption as None](Editing-Text-in-EditControl_images/EditControl_IndentingOption_None.gif)

#### IndentationOptions (Smart)
When <kbd>ENTER</kbd> key is pressed, edit cursor will move to next line with one tab space.

![IndentingOption as Smart](Editing-Text-in-EditControl_images/EditControl_IndentingOption_Smart.gif)

#### IndentationOptions (Block)
When <kbd>ENTER</kbd> key is pressed, edit cursor will move to next line with same indentation of current line.

![IndentingOption as Block](Editing-Text-in-EditControl_images/EditControl_IndentingOption_Block.gif)

### TabSpaces in EditControl

[EditControl](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl_members.html) supports changing the number of spaces to be added in editor when <kbd>TAB</kbd> key is pressed. The required number of tabs or spaces can be added to the beginning of each line in the selected block by using the [TabSpaces](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.Edit.Wpf~Syncfusion.Windows.Edit.EditControl~TabSpaces.html) property in the EditControl. By default, the TabSpace property value is set to 4.

{% tabs %}

{% highlight XAML %}

<syncfusion:EditControl Name="Edit1" Background="White" Margin="0" IsAutoIndentationEnabled="True" TabSpaces="10" IndentingOptions="Smart" Foreground="Black" ShowLineNumber="True" />

{% endhighlight %}

{% highlight C# %}

    EditControl editControl = new EditControl() {Height = 200, Width = 200, Background = Brushes.White, Foreground = Brushes.Black };

    editControl.TabSpaces = 10;
    this.Content = editControl;

{% endhighlight %}    
{% endtabs %}        

