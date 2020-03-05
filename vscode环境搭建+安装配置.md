# vscode vue环境搭建+配置eslint和prettier  

## 一、安装Node.js、cnpm、webpack、vue-cli
**1. 安装Node.js**  

官网 https://nodejs.org/en/download/ 选择.msi进行安装。安装成功后打开cmd，输入node -v和npm –v查看版本号。

**2. 安装cnpm（比npm快，因为使用淘宝的服务器做为的包源 ）**  

在cmd中，输入命令：`npm install –g cnpm --registry=https://registry.npm.taobao.org` 。安装成功输入cnpm –v查看相关信息。

**3. 安装webpack（js应用程序的静态模块打包器module bundler）**  

在cmd中，输入命令：`cnpm install webpack –g` 进行安装。

**4. 安装vue-cli（用来生成vue模版的工具）**  

在cmd中，输入命令：`cnpm install vue-cli –g` 进行安装。安装成功后，输入命令：`cnpm install -g @vue/cli-init`。

 

## 二、在cmd新建vue项目进行测试
**1. 在cmd，cd进入你想保存项目的文件目录。输入命令：`cnpm install -g @vue/cli-init`。**  

**2. 输入命令：`vue init webpack testDemo`**，新建项目。（最好不要有大写，不然接下来第一个会提示你Project name不能有大写，需要一个小写的名字）。

前面的回车即可，后面两个填no（因为之后要使用cnpm来下载依赖，npm太慢了）。最后一个本来选中的是“Yes, use NPM"（蓝色为选中），使用向下键选中第三个（如图）后回车。

![安装-1](/pictures/notes/安装-1.png)

**3. 之后会显示建议如下图**（把里面的npm全部换成cnpm后再一条条执行，不然npm太慢了）

![安装-2](/pictures/notes/安装-2.png)

即逐条运行如下命令，第一条：`cd testDemo`，第二条：`cnpm install`，第三条：`cnpm run lint -- --fix`，第四条：`cnpm run dev`

**4. 根据给出的提示，在浏览器通过http://localhost:8080地址访问。** 访问成功即测试成功。

 

## 三、安装vscode、插件vetur、插件eslint、插件prettier
**1. 插件通过左侧extensions安装**（可通过Crtl+Shift+X快捷键打开左侧extensions）。三个插件安装完成后重启vscode。

**2. 更改配置文件setting.json**（打开方式：界面左下角设置图标->Settings->搜索框中搜索eslint->点击edit in setting.json）

![安装-3](/pictures/notes/安装-3.png)

更改setting.json文件如下：
 ```json
{
    "editor.fontFamily": "Fira Code, Consolas", //调整字体，Fira Code
    "editor.detectIndentation": false,// vscode默认启用了根据文件类型自动设置tabsize的选项
    "editor.tabSize": 4,            // 重新设定tabsize
    "editor.formatOnSave": true,        // #每次保存的时候自动格式化 
    "editor.formatOnPaste": true,
    "editor.formatOnType": false,
    "editor.suggestSelection": "first",
    "editor.autoIndent": false,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
 
    "eslint.enable": true,
    "eslint.run": "onType",
    // 添加 vue 支持
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "vue-html",
        "html",
        "vue"
    ],
    "eslint.options": {
        "extensions": [
            ".js",
            ".vue"
        ]
    },
    "files.associations": {
        "*.vue": "vue",
        "*.js": "javascript",
        "*.cjson": "jsonc",
        "*.wxss": "css",
        "*.wxs": "javascript",
        // "*.wpy": "vue"
    },
 
    //  #去掉代码结尾的分号 
    "prettier.semi": false,
    //  #使用带引号替代双引号 
    "prettier.singleQuote": true,
    //  #让函数(名)和后面的括号之间加个空格
    "javascript.format.insertSpaceBeforeFunctionParenthesis": true,
    // #这个按用户自身习惯选择 
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    // #让vue中的js按编辑器自带的ts格式进行格式化 
    "vetur.format.defaultFormatter.js": "vscode-typescript",
 
    "git.ignoreMissingGitWarning": true,
    "git.confirmSync": false,
    "git.autofetch": true,
    "git.enableSmartCommit": true,
    "files.autoSave": "onWindowChange",
    "explorer.confirmDelete": false,
    "terminal.integrated.rendererType": "dom",
    "vetur.format.defaultFormatterOptions": {
        "js-beautify-html": {
            "wrap_attributes": "force-aligned"
            // #vue组件中html代码格式化样式
        }
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "extensions.autoUpdate": true,
}
```
**3. 想要每次保存时自动将双引号变为单引号，则在项目根目录下新建“.prettierrc"，文件内容如下：**   
```json
{
    "semi":false,
    "singleQuote":true
}
```
重启（可能需要）vscode后生效。（其实vscode右键就有'格式化文档'。）  



# 四、在vscode中运行vue项目  

**1. File -> Open Folder，打开刚才使用cmd创建的项目testDemo。**  

**2. 打开Terminal**（可以顶部工具栏Terminal-> New Terminal打开）  

**3. 输入命令： `cnpm install`**，用于检查和下载依赖。（这一步我碰到了很多问题，会在文末说明我遇到过的问题以及解决方法）  

**4. 输入命令： `cnpm run dev`**，运行项目。  

**5. 根据给出的提示，在浏览器通过http://localhost:8080地址访问。**  

![安装-4](/pictures/notes/安装-4.png)

 

# 五、使用cnpm时遇到的坑
**问题：使用cnpm install时报错'cnpm : 无法加载文件 ... ，因为在此系统上禁止运行脚本。...'**
报错如下：
![安装-5](/pictures/notes/安装-5.png)


**解决方案**
1. 在win10搜索框中搜索Windows PowerShell，以管理员身份运行。  

2. 输入命令：set-executjionpolicy remotesigned。（很遗憾在这一步又出现问题了，具体报错忘记截图了，大概就是说这个命令不能运行啥的。解决方案见下一步。）（如果这一步你能成功，请直接跳到第4步）  

3. 解决第2步出现的问题（第2步没问题的直接看第4步）：在cmd中输入命令：get-help set-executionpolicy。运行完这个命令后，再在PowerShell中尝试运行2中的命令，如果成功，则执行第4步。  

4. 更改权限为A。输入命令：Ge-ExecutionPolicy。  

![安装-6](/pictures/notes/安装-6.png)

5. 再回到vscode，在Terminal中输入命令：cnpm -v。如果能成功，说明问题解决了，cnpm install也能正常运行了。  



