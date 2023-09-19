
<hr>

# plugin

```
# GitHub Dark
code --install-extension GitHub.github-vscode-theme;

# vscode-icons
code --install-extension vscode-icons-team.vscode-icons;

# prettier
code --install-extension esbenp.prettier-vscode;

# python
code --install-extension ms-python.python;

# c/c++
code --install-extension ms-vscode.cpptools;

# java
code --install-extension vscjava.vscode-java-pack;
```
	
<hr>

# setting

```

{
  "workbench.startupEditor": "none",
  "workbench.colorTheme": "GitHub Dark",
  "workbench.iconTheme": "vscode-icons",
  "editor.fontLigatures": false,

  "editor.fontSize": 22,
  "editor.fontFamily": "'DejaVu Sans Mono'",
  "editor.fontWeight": "normal",
  "editor.wordWrap": "on",
  "extensions.ignoreRecommendations": true,
  "editor.cursorBlinking": "smooth", //使编辑器光标的闪烁平滑,有呼吸感
  "editor.cursorSmoothCaretAnimation": "on", //让光标移动、插入变得平滑
  "editor.formatOnType": true, //敲完一行代码自动格式化
  "editor.smoothScrolling": true, //使编辑器滚动变平滑
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  /* 文件自动保存
   onFocusChange:当前文件失去焦点后自动保存.
   onWindowChange:需要当前 VScode 窗口失去焦点才会自动保存.
   afterDelay:与 files.autoSaveDelay 配置联动,也就是在间隔多少毫秒自动保存,默认「1000毫秒」,
   有个小细节,如果配置了保存格式化代码,这个配置下自动保存不会格式化代码. */
  "files.autoSave": "onWindowChange",
  "files.autoSaveDelay": 2000,
  // 配置 Tab 空格数
  "editor.tabSize": 2,
  // 保存自动格式化代码
  "editor.formatOnSave": true,
  // 粘贴自动格式化
  "editor.formatOnPaste": true,

  // 可以为不同语言的文件类型单独配置
  "[typescript]": {
    "editor.formatOnSave": false
  },
  "[markdown]": {
    "editor.formatOnSave": true
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[python]": {
    "editor.defaultFormatter": "ms-python.python"
  },
  "[cpp]": {
    "editor.defaultFormatter": "ms-vscode.cpptools"
  },
  "[java]": {
    "editor.defaultFormatter": "redhat.java"
  },
  
  "redhat.telemetry.enabled": true,

  //关闭自动更新
  "update.mode": "none",

  "debug.internalConsoleOptions": "openOnSessionStart", //每次调试都打开调试控制台,方便调试
  "debug.showBreakpointsInOverviewRuler": true, //在滚动条标尺上显示断点的位置,便于查找断点的位置
  "window.dialogStyle": "custom", //使用更具有VSCode的UI风格的弹窗提示(更美观)
  "workbench.editor.wrapTabs": true, //编辑器标签页在空间不足时以多行显示

  "html.format.indentHandlebars": true, //在写包含形如{{xxx}}的标签的html文档时,也对标签进行缩进(更美观)

  "files.autoGuessEncoding": true, //让VScode自动猜测源代码文件的编码格式
  "files.watcherExclude": {
    //不索引一些不必要索引的大额占存文件夹以减少内存和CPU消耗
    "**/.git/objects/**": true,
    "**/.git/subtree-cache/**": true,
    "**/node_modules/**": true,
    "**/tmp/**": true,
    "**/bower_components/**": true,
    "**/dist/**": true
  },

  "terminal.integrated.fontSize": 20,
  "terminal.integrated.fontFamily": "Liberation Mono",
  "terminal.integrated.cursorBlinking": true,
  "explorer.confirmDelete": false, //终端光标闪烁
  "update.showReleaseNotes": false,
  "editor.fontVariations": false
}


```
