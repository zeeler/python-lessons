## 环境搭建

### 1. 安装Python3和virtualenv虚拟环境
#### macOS
* 去官网下载安装
[https://www.python.org/downloads/](https://www.python.org/downloads/macos/)
* 通过brew安装
  ```bash
  # 先安装homebrew
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  brew update
  # 在安装python3
  brew install python@3.12
  brew install pip3
  brew install virtualenv
  ```
#### Linux
* 去官网下载源代码编译安装
[https://www.python.org/downloads/linux/](https://www.python.org/downloads/source/)
* 通过apt或yum安装
  ```bash
  # ubuntu
  apt update
  sudo apt install python3
  sudo yum install python3-virtualenv
  # redhat/centos
  yum update
  sudo yum install python3
  sudo yum install python3-virtualenv
  ```

#### Windows
* 访问Python官方网站：https://www.python.org/downloads/windows/
* 下载适合Windows的最新Python 3安装程序（通常是一个.exe文件）。
* 运行下载的安装程序，并确保选中“Add Python to PATH”选项，以便将Python添加到系统的环境变量中，完成安装过程。
* 打开命令提示符（Command Prompt）或PowerShell，输入命令安装virtualenv
  ```bash
  pip3 install virtualenv
  ```

### 2. 创建项目目录和虚拟环境
#### macOS或Linux
* 打开终端，输入
  ```bash
  # 创建目录
  mkdir test1
  # 进入目录
  cd test1
  # 如果装了多个版本python，查看要用的python的bin目录
  which python3.12
  # 创建虚拟环境，使用目录为.env
  virtualenv .env --python=上面查询到的python3.12目录
  # 切换到虚拟环境
  source .env/bin/activate
  # 确认Python版本是预期的
  python -VV
  # 更新pip3
  pip install --upgrade pip
  # 退出虚拟环境
  deactivate
  ```
#### Windows
* 手工创建项目目录（文件夹）
* 打开命令提示符或PowerShell，并导航到希望创建虚拟环境的目录
  ```bash
  # 如果装了多个版本python，查看一下她们的路径
  where python
  # 创建虚拟环境，使用目录为.env
  virtualenv myenv --python=上面查询到的路径
  # 切换到虚拟环境
  myenv\Scripts\activate.bat
  # 确认Python版本是预期的
  python -VV
  # 更新pip3
  pip install --upgrade pip
  # 退出虚拟环境
  deactivate
  ```

### 3.安装和配置VSCode
为什么要选VSCode，其实代码生产效率和能力并不比PyCharm低多少，但更轻量级，占用系统资源少，适合更老的电脑。另外，目前很多AI编程工具都默认支持或绑定VSCode，因为他是开源的IDE（Integrated Development Envirement）。
* 去官网下载并安装
  ```bash
  https://code.visualstudio.com/download
  ```
* 建议安装的插件
1. Microsoft的autopep8, Pylance, Pylint, Python, Python Debugger
2. 三方的Python Environment Manager, python snippets, Git Graph
* 创建项目和Workspace
1. 创建项目目录
2. 在VSCode菜单中File --> Open Folder 打开上面创建的项目目录
3. 在VSCode菜单中File --> Save Workspace As ... 使用默认文件名即可，会创建“项目名.code-workspace”文件
* 配置虚拟环境
1. 点击VSCode左侧图标最下面的Python，在PYTHON:WORKSPACE ENVIRONMENT界面中，点击“+” Create Environment(创建新虚拟环境)
2. 选择类型：Select an environment type，选择Venv，默认在项目目录中创建.venv目录
3. 选择使用的Python：Select a Python installation to create the virtual environment，选择Python 3.13
* 配置Workspace的Interpreter
1. 点击VSCode左侧图标最上面Explorer，按“Command+,”按键，打开Settings设置，
2. 搜索框输入python
3. 点击下面的User旁边的Workspace，设置当前项目的工作环境
4. 点击下面Extensions的Python，在右侧详情页找到Python: Default Interpreter Path，输入“.venv/bin/activate” (回车保存)
5. 在右侧详情页找到Python: Env File，改成“${workspaceFolder}/.venv” (回车保存)
6. 关闭Settings窗口
* 在项目中安装需要的三方库
1. 点击VSCode左侧图标最下面的Python
2. 展开Workspace Envs，点击.venv右侧的“Open in Terminal”图标，会在右下终端窗口自动切换到虚拟环境状态
3. 
