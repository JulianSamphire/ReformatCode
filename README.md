
# Reformat Code Script

A reformat code script for the [Xojo IDE](https://www.xojo.com/) that has some useful features.

## Features
-   Pad the inside of parentheses with a space. e.g. `a(b,c)` will become `a( b,c )`
-   Pad the outside of parentheses with a space. e.g. `a(b,c)` will become `a (b,c)`
-   Pad empty parentheses with a space. e.g. `a()` will become `a( )`
-   Remove empty parentheses. e.g. `a()` will become `a`
-   Pad commas. e.g. `a(b,c)` will become `a(b, c)`
-   Pad operators. e.g. `a=b+c` will become `a = b + c`
-   Pad inline ifs so `a=if(b=1,0,1)` will become `a=if (b=1,0,1)`
-   Pad before a line continuation mark (underscore)
-   Aid with some common transpositions i.e. `endif` will become `End If`
-   Comment replacement e.g. `'` will become `//` or vice versa
-   Pad comments before and after the comment mark
-   Code replacement, `a++`, `a+=1`, `if a!=1` etc.
-   Macros, quickly insert pre-defined text with autocomplete description
-   Automatic calculation of windows declare types
-   Automatic conversion of hex types
-   Automatic conversion of #Define to Const
-   Automatic conversion of MSDN code blocks to declares
-   An error checking feature that will notify you if the line has:
    -   mismatched parentheses
    -   missing opening parenthesis
    -   missing closing parenthesis
    -   mismatched quotes
    -   any of the above across line continuation when pasting a code chunk
-   Automatic conversion of Dim to Var and Var to Dim as desired
-   Automatic conversion of Var back to Dim if you're using a pre 2019r2 edition of the IDE
-   Force case to UPPERCASE, lowercase or Xojo default on anything except variables

## TL;DR - Where do I go for help?

If you read through the following and need a little help, please:

Watch the video - https://youtu.be/IAVjh-xiO0w

Latest features update video - https://youtu.be/-JPjQ4Gn1bM

Ask questions on the forum - https://forum.xojo.com/47389-xojo-ide-reformat-code-script

**If nothing happenes make sure you have "Apply standardize format after ending line" turned on under:**

**Options->Coding.**

## Getting Started
([Jump to to this point in the video](https://youtu.be/IAVjh-xiO0w?t=9s))

The easiest way to install the script is to directly download it and place it into the Scripts folder of your Xojo installation.

To get started, close down the Xojo IDE as the script is loaded when the IDE is opened.

To download the script, click ReformatCode.xojo_script above then right click (context menu) on the Raw button in the top right corner of the code view and select "Save link as...". You can save it directly into the Xojo Script folder or move it there after downloading.

An alternative method is to clone the repository and either copy of the file out of there or create a link from ReformatCode.xojo_script in the repository to your Xojo's Scripts folder. This will enable you to keep up to date with the latest changes to the Reformat Code Script with minimal effort.

Start the IDE back up and move the cursor around your code!

**If nothing happenes make sure you have "Apply standardize format after ending line" turned on under:**

**Options->Coding.**

## **Settings**
([Jump to to this point in the video](https://youtu.be/IAVjh-xiO0w?t=2m58s))

Defaults are shown in parentheses `( )`  
Booleans can be `true,yes,1` or `false,no,0`

Settings can be altered by placing constants into the project, initially these settings are read in from the `App` object at the top of the project. This can be changed by defining:

    ConstantStorageLocation (App)

Use this setting to change the location where settings are located. You might want to keep your App object clean so you could move your settings into a module named Settings. To do this, set ConstantStorageLocation to Settings

If the prefix is set to Me then settings are read locally so you can change settings if you are in a class or module etc.

*Note: If you set your settings modules “Include In” settings (under advanced settings) to all unchecked then none of the constants you place inside will be included in your built application.*

    Prefix (<empty>)

If the setting is set, the prefix for all future settings will be based on that value, so setting it to `Test_` will change all settings in that project to require a `Test_` prefix. You can use this if you want to avoid naming conflicts in your projects.

    DimVar (<empty>)

If you set this value to `Var` it will automatically change `Dim` to `Var`. If you set this value to `Dim` it will automatically change `Var` to `Dim`. If you leave it blank it will not change Dim or Var. The script will also automatically convert Var to Dim if you’re using an API1 edition of Xojo (pre 2019r2).

    ForceCase (<empty>)

If you set this value to `Uppercase` it will force everything except variables to UPPERCASE so `Dim a As String` will become `DIM a AS STRING`. If you set this value to `Lowercase` it will force everything except variables to lowercase so `Dim a As String` will become `dim a as string`. If you leave this value blank it will use the standard formatting defined in the script e.g. `Dim a As String`.

    PadParInside (false)

Pad the inside of parentheses with a space. e.g. `a(b,c)` will become `a( b,c )`

    PadParOutside (false)
    
Pad the outside of parentheses with a space. e.g. `a(b,c)` will become `a (b,c)`

    PadEmptyParInside (false)

Pad empty parentheses with a space. e.g. `a()` will become `a( )`

    RemoveEmptyPar (false)

Remove empty parentheses. e.g. `a()` will become `a`

    PadComma (true)

Pad commas. e.g. `a(b,c)` will become `a(b, c)`

    PadOperators (true)

Pad operators. e.g. `a=b+c` will become `a = b + c`

    PadIif (false)

Pad inline ifs e.g. `a=if(b=1,0,1)` will become `a=if (b=1,0,1)`

This setting will override PadParOutside and PadOperators because you might like your inline ifs to be connected to your parentheses, or not.

    PadLineContinuation (true)

Pad before a line continuation mark (underscore)

    ReplaceWords (see below)

    "!", "Not", "endif", "End If", "endselect", "End Select",
    "endsub", "End Sub", "endfunction", "End Function", "endtry", "End Try"

A paired comma separated list of strings. The first string in the pair is the original string and the second string of the pair is the replacement string. If an original string is found it is replaced with the second string. This is useful for correcting typos or expanding commonly used words. You can add your own by using the ReplaceWords constant in the format:

    Original1,Replacement1,Original2,Replace2 etc.

If there is an odd number of entries in ReplaceWords the whole setting will be ignored until it is corrected. When you add your own replacement words you don’t need to use quotes. If the word is found as a reserved words first it won’t be replaced.

    Comment (<empty>)

If you want to ensure that all your comments follow the same format then enter your required comment type in here and all comments will be changed to this format: `'`, `//` or `Rem`. If you don’t specify a comment type it will retain the type that is already there.

    PadCommentBefore (<empty>)

If you set this value to true it will try to place a space before the comment token. If you set it to false it will remove the space before the comment token, if you leave it blank it will not add/remove a space and will leave whatever is already there.

    PadCommentAfter (<empty>)

If you set this value to true it will try to place a space after the comment token. If you set it to false it will remove the space after the comment token, if you leave it blank it will not add/remove a space and will leave whatever is already there.

### Error Checking

The error message will automatically be removed when you move off the line if the error is corrected without altering the format or spacing of the error message. Error checking can now take place over lines that are split with continuation marks `_` if the block is pasted in with a spare blank line at the end.

    MessageComment (')

This is the comment type used for error message notifications. This setting can either be `'`, `//` or `Rem`.

    MessageParMismatched (MISMATCHED PARENTHESES)

This is the message that is shown to notify you if there are mismatched parentheses on the line. Setting this to `_` (underscore) will turn off checks for this setting and the error message will not be shown.

    MessageParOpening (MISSING OPENING PARENTHESIS)

This is the message that is shown to notify you if there is a missing opening parenthesis on the line. Setting this to `_` (underscore) will turn off checks for this setting and the error message will not be shown.

    MessageParClosing (MISSING CLOSING PARENTHESIS)

This is the message that is shown to notify you if there is a missing closing parenthesis on the line. Setting this to `_` (underscore) will turn off checks for this setting and the error message will not be shown.

    MessageQuoteMismatched (MISMATCHED QUOTES)

This is the message that is shown to notify you if there are mismatched quotes on the line. Setting this to `_` (underscore) will turn off checks for this setting and the error message will not be shown.

    MessageInCodeBlock ( IN CODE BLOCK)

This message is added to the end of one of the messages shown above when there is an issue inside a recently pasted code block that uses line continuation marks `_`.

### Debugging

    DebugLevel (0)

Reports debug information (see `System.DebugLog` for more information). This setting is off by default, setting to 1 will show some debug information, 2 will show detailed debug information.

## Code Replacements
([Jump to to this point in the video](https://youtu.be/IAVjh-xiO0w?t=13m22s))

There are a set of replacements that happen when moving onto a new line which aid with coding:

    a+=1    a=a+1
    a-=1    a=a-1
    a*=1    a=a*1
    a/=1    a=a/1
    a++     a=a+1
    a--     a=a-1

The above section also works with dot notation e.g.:

    window1.title+="hello"    window1.title=window1.title+"hello"

If you have come from other languages it will also help you with:

    If a not = 1    if a <> 1
    If a != 1       if a <> 1
    
## Macros
([Jump to to this point in the video](https://youtu.be/IAVjh-xiO0w?t=14m44s))

Macros have been implemented by replacing specially formatted strings with other content that is stored in the current project. As you move off the line containing the macro it is converted.

By default, to keep things tidy, macros are looked for inside a module called `Macro`

This can be changed with the following setting:

    MacroStorageLocation (Macro)

Creating a module named Macro and placing a text constant inside allows you to autocomplete that macro while typing. As you move off the line the macro is converted into the text that is listed inside the constant.

If you create a two lined macro with a comment on the first line (using either `'` or `//` at the start) this sentence is placed into the autocomplete list so you can add a description to the macro that you will see during auto-completion. When the macro is converted it will use the content from the second line in the macro.

Macros can be nested inside modules which allows you keep macros organised when you have more of them, so for example, you could create macro.hello.world

Macros was originally designed with automatic insertion of multi line macros, however a bug was discovered that meant that this feature has been placed on hold until a future release of Xojo that corrects the problem. When this happens, you will be able to insert blocks of text with the macro system to quickly insert regularly used code or comment blocks.

*Note: If you set your macro modules “Include In” settings (under advanced settings) to all unchecked then none of the constants you place inside will be included in your built application.*

## Windows Declares
([Jump to to this point in the video](https://youtu.be/IAVjh-xiO0w?t=20m53s))

The ReformatCode script will attempt to resolve windows declares for you so you don’t need to look up the correct Xojo types. Just enter the variable type with a w_ before it and it will be converted to its relevant Xojo type when you move off the line. The list of conversion is taken from my [blog](https://blog.samphire.net/2017/01/22/windows-to-xojo-data-type-conversion/). If you see a * appear, it means that you should visit my blog and read the additional notes associated with that type.

For example, to add SetWindowLong type the following:

    declare function SetWindowLong lib "User32" alias "SetWindowLongW" (hWnd as w_hwnd, nIndex as w_int, dwNewLong as w_long) as w_long

and it will be converted to:

    Declare Function SetWindowLong Lib "User32" Alias "SetWindowLongW" (hWnd As Integer, nIndex As Int32, dwNewLong As Int32) As Int32

### Hex conversion

You can copy hex values from msdn pages, windows header files or any location and paste them directly into Xojo with the reformat script handling the conversion so `0x0001` becomes `&h0001`. As long as the values are in the format 0x0 they will be converted.

### Conversion of #Define's to Const's

The ReformatCode script will convert from #Define's that you find in windows header files or on MSDN into the correct Const syntax in Xojo, for example:

    #define WM_QUIT                         0x0012

will be converted to:

    Const WM_QUIT = &h0012

### Conversion of MSDN code blocks

If you are a regular user of windows declares you'll be familiar with MSDN and the code samples they provide. For example if you visit [SetWindowLongPtrW On MSDN](https://docs.microsoft.com/en-us/windows/desktop/api/winuser/nf-winuser-setwindowlongptrw) and see the section labled Syntax you will see the following piece of code:

    LONG_PTR SetWindowLongPtrW(
      HWND     hWnd,
      int      nIndex,
      LONG_PTR dwNewLong
    );

Because of the way that the IDE has implemented the reformat code scripting system there are two ways to get this into Xojo. The first requires an additional step and the second is quicker but requires a more accurate copy process.

#### Method 1

Click the Copy button in the top right corner of the code block on the MSDN page and paste this directly into Xojo. Unfortunately, the way the reformat code system (not this script) has been implemented by the IDE it will mean that you will end up with something like this, which isn't correct:

    LONG_PTR SetWindowLongPtrW('MISSING CLOSING PARENTHESIS
    HWND hWnd,
    int nIndex,
    LONG_PTR dwNewLong
    );

Pressing enter or moving off the last line will add an additional error comment to the last line. What you'll need to do is press Enter to make a new line, copy that entire block including the new line you just created then cut and paste it again to have this script process the block correctly (don't worry about removing the additional comments, the script will take care of those). When this works, you'll see the following in the IDE:

    Declare Function SetWindowLongPtrW Lib "REPLACE_ME.dll" Alias "SetWindowLongPtrW" ( _
      hWnd As Integer, _
      nIndex As Int32, _
      dwNewLong As Integer _
      ) As Integer

#### Method 2 (my preferred method)

Rather than clicking the Copy button, select from the start of the code snippet (just before LONG_PRT in this case) all the way down to just before the P of parameters. This will include an additional blank line that will mean our paste into the IDE will work first time, so switch to the IDE and paste the code and you will see the following in the IDE:

    Declare Function SetWindowLongPtrW Lib "REPLACE_ME.dll" Alias "SetWindowLongPtrW" ( _
      hWnd As Integer, _
      nIndex As Int32, _
      dwNewLong As Integer _
      ) As Integer

The alias is always added ready so you can change the name of the call before Lib to anything you need ensuring that the correct call is used within the Alias quotes. To complete the process, double click REPLACE_ME and paste in the name of the dll from the bottom of the MSDN page under the section Requirements, DLL.

**If this is all a bit confusing, just watch this [video](https://youtu.be/-JPjQ4Gn1bM) for a quick rundown of how to do it, once you get the hang of it, it makes working with declares a LOT quicker.**

You will still need to make sure that you correctly use ByRef before your parameter names. See the notes at the top of my [blog](https://blog.samphire.net/2017/01/22/windows-to-xojo-data-type-conversion/) about this.

If you have any questions, feature requests or bug reports, please visit to the Xojo forum [thread](https://forum.xojo.com/47389-xojo-ide-reformat-code-script) regarding this script.

More information regarding Custom Code Reformatting in the Xojo IDE can be found [here](https://docs.xojo.com/UserGuide:Custom_Code_Reformatting).
