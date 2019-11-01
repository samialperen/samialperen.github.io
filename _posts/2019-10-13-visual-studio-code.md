---
layout: post
title:  "Visual Studio Code: Free Source-Code Editor for All Languages"
date:   2019-10-13
image: /images/visual-studio-code/1.jpg
---

![Visual Studio Code](/images/visual-studio-code/1.jpg)

In the end, I found a perfect source-code editor for myself thanks to my friend Austin (yeey!). Previously, I was using **PyCharm** for Python and **Qt Creator** for C++. However, switching between them was quite tiring. After lots of different editor trials, **Visual Studio Code** saved me from all the trouble. It is a free source-code editor developed by Microsoft. It can be used in all Linux, macOS or Windows computers. It contains editor, debugging tool,  embedded git control and Github (my favorite property), syntax highlighting, intelligent code completion, snippets and much more than you expect from a code-editor.

You can download it using [this](https://code.visualstudio.com/) link. After installation, I strongly recommend to follow [tips and tricks page](https://code.visualstudio.com/docs/getstarted/tips-and-tricks). This page will give you quick review of editor and introduce all the cool properties. You have to install different **code extensions** to start coding such as Python one. To find out how to do it, see **Extensions** section of tips and tricks page. Except from tips and tricks page, each language extension has its own getting started tutorial like [Getting Started with Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial). Before starting coding in a specific programming language, visit corresponding getting started page. 

Now, thanks to **VS Code** , you can code and test (debug) your project in one window. It also allows you to upload your code to Github in the same window. Lastly, you can google different users' preferences and favorite keyboard shortcuts like [this](https://vslive.com/Blogs/News-and-Tips/2015/04/5-VS-Keyboard-Shortcuts.aspx) to get best experience from the editor. 

**NOTE:** If you have problems with multi-line selection short cut (Alt + Click) , that's normal. This problem occured to me as well for Ubuntu 16.04. To fix this, you need to enable multi-cursor clicking by typing following command into the terminal:
```
gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier "<Super>"   
```

Happy coding!
