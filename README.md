# vscode-prolin-sdk
# prolin-project 使用背景

- 本扩展提供给ProlinSDK开发者使用。请先安装ProlinSDK，扩展依赖于prolinSDK开发工具。扩展同时支持windows和linux用户使用vscode开发prolin应用，详细细节请参考下方文档。

## 扩展特色

1. 本扩展能完成prlin应用和库项的生成和编译，支持windows和linux系统，用户不用手动编写makefile。
2. 扩展支持多项目管理模式，同vscode本身的workspace模式一致(vscode可以直接打开后缀为.code-workspace的工作空间文档)。扩展将自动识别目录中的工程，并将项目添加到工作空间文档中。
3. 扩展依赖Prolin SDK，用户需要安装Prolin SDK. 请将Prolin SDK安装路径(填写到sdk目录为止，例如C:\ProlinSDK\prolin_sdk_win-2.9.3\sdk)添加到系统环境变量中。 对于linux用户，同样需要将安装路径(同样填写到sdk目录，例如/home/developer/prolin_sdk_linux-2.9.3/sdk)添加到系统环境变量中. 强烈建议在/etc/profile中配置环境变量(**PATH=$PATH:your_path/prolin_sdk_linux-your_ver/sdk**)。 
![add env path(etc/profile)](https://github.com/PAXSwTool/vscode-prolin-sdk/raw/main/linux.etc.profile.png)

## 项目模板文件和文档架构
	
1. 每个模板工程包含default、Inc、Lib、Pkg、Src等目录，同prolinSDK创建的工程模板一致。另外，工程中还引入了vscode配置目录.pax、.vscode，这两个目录存放一些配置信息，可以自行打开目录查看文档内容，不建议改动这两个文件。需要注意的是linux编译脚本build.sh存放在.pax目录，支持一键完成编译操作。  
2. 建议将头文件存放在Inc目录，源文件存放在Src目录，库文件存放在Lib目录。这3个目录已经自动添加引用。  
![Prolin project template](https://github.com/PAXSwTool/vscode-prolin-sdk/raw/main/prolin-project-template.png)


## 如何启动编译？

本扩展安装完成后，会在左侧视图栏添加ProlinSDK图标。点击此图标就能展开应用和库项目创建页面。工程创建完成后，点击工程根目录，右键打开弹出菜单，对工程的编译、清除等操作都包含在此菜单。
The generated intermediate files and target files are saved in the default directory. For Linux projects, you can run build.sh in the. Pax directory to complete project compilation。  ![build Prolin project](https://github.com/PAXSwTool/vscode-prolin-sdk/raw/main/build-prolin-project.gif)


## 如何编译Prolin SDK创建的工程？

本扩展能兼容Prolin SDK创建的项目。 用vscode打开prolinSDK工程目录后，在项目目录根节点右键打开弹出菜单选择初始化项目。“ProlinSDK Initialize”完成项目初始化动作，此功能会重新构造makefile。需要注意的是，在prolinsdk中配置的参数，如预定义、包含目录、引用库目录、引用库等需要重新在vscode中填写（prolinSDK--->Settings菜单项是配置的入口）。

## 如何编译仅有头文件和源文件的工程？

同Prolin SDK创建的项目，仅有头文件和源文件的工程同样只需要初始化项目即可。菜单项“ProlinSDK Initialize”完成项目初始化动作后，就可以重新构建项目配套文件，完成项目编译。
