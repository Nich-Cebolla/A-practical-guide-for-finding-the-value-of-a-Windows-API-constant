<!-- reddit post https://www.reddit.com/r/AutoHotkey/comments/1oybr5a/how_to_find_the_value_of_any_windows_api_constant/ -->
# How to find the value of a Windows API constant

When reviewing other users' code and browsing the forums, we often come across something like this:
```ahk
OnMessage(0x0200, Callback, 1) ; WM_MOUSEMOVE
Callback(wParam, lParam, msg, hwnd) {
    if wParam = 0x0001 { ; MK_LBUTTON
        ; code
    }
    return 0
}
```

But rarely do we see an explanation for where the values  `0x0200` and  `0x0001` come from. We learn eventually that we can go to [learn.microsoft.com](https://learn.microsoft.com/) and search for some of these, and we feel a great boost in confidence at our newfound skills and opportunities.

Then, one day we come across something like [https://learn.microsoft.com/en-us/windows/win32/controls/static-control-styles](https://learn.microsoft.com/en-us/windows/win32/controls/static-control-styles) and to our dismay, the values are not listed! Microsoft seems to have forsaken the noob and expects its platform developers to know where to get these values, or, more likely, to know that they can refer to the values by name. However, we are coding in AHK, and so we are not able to refer to the values by name.

This guide is a short, step-by-step guide to help you find any Windows API constant value from the header files on your own machine.

View this guide with images included from the repository: [https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/tree/main](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/tree/main)

View this guide with images included from the AutoHotkey forums: [https://www.autohotkey.com/boards/viewtopic.php?f=96&t=139549](https://www.autohotkey.com/boards/viewtopic.php?f=96&t=139549)

# Steps

1. If you have not already, download and install [Visual Studio](https://learn.microsoft.com/en-us/visualstudio/install/install-visual-studio) (NOT Visual Studio Code). When you get to Step 4 - Choose Workloads - install the Desktop development with C++ workload, among any other workloads you are interested in.
2. After Visual Studio is installed, launch Visual Studio. If you are presented with the Visual Studio Installer, click Launch. If not, continue to the next step. [image - visual studio installer](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/visual-studio-installer.png)
3. You should now be looking at the Get Started interface. Click Create a new project. [image - create a new project](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/create-a-new-project.png)
4. Find the Windows Desktop Application option, then click on it and click Next. [image - windows desktop application](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/windows-desktop-application.png)
5. Change any details or leave them the default, then click Create. [image - create](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/create.png)
6. After the project is created and everything loads, either press the keyboard shortcut Ctrl+Shift+F, or click Edit > Find and Replace > Find in Files. [image - find in files](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/find-in-files.png)
7. Input the search term, i.e. the constant's name, change the Look in dropdown to All Visual C++ Directories, then use one of the Find options at the bottom. [image - find](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/find.png)
8. If you selected Find Previous or Find Next, you will typically see the constant definition in the header file, something like the below image. If the constant's name is found inside the name of something else, you might have to click Find Previous / Find Next a few more times until you find the actual definition. [image - find result](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/find-result.png)
9. If you select Find All, then review the results until you find something like "#define &lt;symbol name> &lt;symbol value>", then click on that. [image - find all result](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/find-all-result.png)

There you have it! Super easy and now you can write AHK code like a pro.

# Bonus guide - finding a specific header file

Sometimes we just want to open a specific header file and review its contents. This is very easy. Start from step 6 above (you should have the project open to an editable file).

1. Type `#include "<name>.h"` anywhere in the file.
   [image - type include](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/type-include.png)
2. Hold down Ctrl and left-click on the text you just typed. The mouse pointer should change form to indicate that it is hovering over interactible content. The header file will open automatically.
   [image - new tab](https://github.com/Nich-Cebolla/A-practical-guide-for-finding-the-value-of-a-Windows-API-constant/raw/main/images/new-tab.png)
