# Python开发环境搭建指南

本指南将帮助你在macOS、Linux和Windows平台上安装Python 3环境，配置virtualenv虚拟环境，并搭建Visual Studio Code (VSCode)作为Python开发IDE。

## 目录

1. [Python 3安装](#1-python-3安装)
2. [Virtualenv虚拟环境配置](#2-virtualenv虚拟环境配置)
3. [VSCode安装与配置](#3-vscode安装与配置)
4. [项目实践](#4-项目实践)
5. [常见问题解决](#5-常见问题解决)

---

## 1. Python 3安装

### macOS

**方法一: 使用Homebrew (推荐)**

```bash
# 安装Homebrew (如果尚未安装)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 安装Python 3
brew install python
```

**方法二: 使用官方安装包**

1. 访问 [Python官方网站](https://www.python.org/downloads/macos/)
2. 下载最新的Python 3安装包
3. 双击下载的.pkg文件并按照向导完成安装

**验证安装**

```bash
python3 --version
```

### Linux

**Ubuntu/Debian**

```bash
# 更新包索引
sudo apt update

# 安装Python 3和pip
sudo apt install python3 python3-pip
```

**CentOS/RHEL**

```bash
# 更新包索引
sudo yum update

# 安装Python 3和pip
sudo yum install python3 python3-pip
```

**Fedora**

```bash
# 安装Python 3和pip
sudo dnf install python3 python3-pip
```

**验证安装**

```bash
python3 --version
```

### Windows

**方法一: 使用官方安装程序(推荐)**

1. 访问 [Python官方网站](https://www.python.org/downloads/windows/)
2. 下载最新的Python 3安装程序
3. 运行安装程序，勾选"Add Python to PATH"选项
4. 点击"Install Now"进行安装

**方法二: 使用Microsoft Store**

1. 打开Microsoft Store
2. 搜索"Python"
3. 选择最新的Python 3版本并安装

**方法三: 使用Chocolatey**

```powershell
# 以管理员身份运行PowerShell安装Chocolatey (如果尚未安装)
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# 安装Python 3
choco install python
```

**验证安装**

```cmd
python --version
```

---

## 2. Virtualenv虚拟环境配置

Virtualenv让你能够为不同项目创建隔离的Python环境，避免依赖冲突。

### 安装virtualenv

**macOS/Linux**

```bash
pip3 install virtualenv
```

**Windows**

```cmd
pip install virtualenv
```

### 使用virtualenv

**创建虚拟环境**

```bash
# macOS/Linux
virtualenv venv  # 创建名为"venv"的虚拟环境
# 查看系统安装的Python的路径
which python3.12
which python3.13
# 或者指定Python版本
virtualenv -p [你的python路径] venv

# Windows
virtualenv venv
# 查看系统安装的Python
where python
# 或者指定Python版本
virtualenv -p [你的python路径] venv
```

**激活虚拟环境**

```bash
# macOS/Linux
source venv/bin/activate

# Windows (cmd)
venv\Scripts\activate.bat

# Windows (PowerShell)
venv\Scripts\Activate.ps1
```

激活后，命令行前会显示虚拟环境的名称，如`(venv)`。

**安装依赖包**

```bash
# 在激活虚拟环境后
pip install package-name
```

**保存依赖列表**

```bash
pip freeze > requirements.txt
```

**从依赖列表安装**

```bash
pip install -r requirements.txt
```

**退出虚拟环境**

```bash
deactivate
```

### 使用venv (Python 3.3+内置模块)

如果你使用Python 3.3或更高版本，可以使用内置的`venv`模块替代virtualenv。

```bash
# 创建虚拟环境
# macOS/Linux
python3 -m venv myenv

# Windows
python -m venv myenv

# 激活与使用方式同virtualenv
```

---

## 3. VSCode安装与配置

### 安装VSCode

**macOS**

1. 访问 [VSCode官网](https://code.visualstudio.com/)
2. 下载macOS版本
3. 将下载的.zip文件解压，将Visual Studio Code应用拖到Applications文件夹中

**Linux**

**使用包管理器**

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install code

# RHEL/Fedora/CentOS
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
sudo yum install code  # CentOS/RHEL
# 或
sudo dnf install code  # Fedora
```

**手动安装**

1. 访问 [VSCode官网](https://code.visualstudio.com/)
2. 下载适合你Linux发行版的安装包(.deb/.rpm)
3. 使用包管理器安装下载的文件

```bash
# Debian/Ubuntu
sudo apt install ./downloaded-vscode-file.deb

# RHEL/Fedora/CentOS
sudo yum install ./downloaded-vscode-file.rpm
# 或
sudo dnf install ./downloaded-vscode-file.rpm
```

**Windows**

1. 访问 [VSCode官网](https://code.visualstudio.com/)
2. 下载Windows版本
3. 运行安装程序并按照向导完成安装

### 配置VSCode for Python

**安装Python扩展**

1. 启动VSCode
2. 打开扩展视图 (`Ctrl+Shift+X` 或 `Cmd+Shift+X` 或点击左侧活动栏的扩展图标)
3. 搜索"Python"
4. 安装Microsoft提供的Python扩展

**安装推荐的其他Python开发扩展**

- **Pylance**: Python语言服务器，提供智能代码补全
- **Python Indent**: 自动缩进
- **autoDocstring**: Python文档字符串生成器
- **Python Test Explorer**: 测试运行器
- **Better Comments**: 增强注释功能
- **Bracket Pair Colorizer**: 括号对着色(VSCode 1.67+内置)

**配置Python解释器**

1. 打开命令面板 (`Ctrl+Shift+P` 或 `Cmd+Shift+P`)
2. 输入并选择 "Python: Select Interpreter"
3. 选择已安装的Python解释器或虚拟环境

**配置自定义设置**

可以在`settings.json`中添加以下配置:

```json
{
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": true,
    "python.formatting.provider": "black",
    "editor.formatOnSave": true,
    "python.linting.flake8Enabled": true,
    "python.linting.mypyEnabled": true,
    "python.testing.pytestEnabled": true,
    "python.terminal.activateEnvironment": true
}
```

**安装常用开发工具**

```bash
# 在虚拟环境中安装开发工具
pip install black flake8 mypy pytest
```

---

## 4. 项目实践

### 创建新项目

```bash
# 创建项目目录
mkdir my_python_project
cd my_python_project

# 创建并激活虚拟环境
virtualenv venv
# macOS/Linux
source venv/bin/activate
# Windows
venv\Scripts\activate

# 创建项目结构
mkdir src tests
touch src/__init__.py tests/__init__.py
touch main.py
touch requirements.txt
```

### 用VSCode打开项目

```bash
code .  # 在当前目录打开VSCode
```

### 配置项目结构

简单项目结构示例:

```
my_python_project/
├── venv/                   # 虚拟环境
├── src/                    # 源代码
│   ├── __init__.py
│   └── module1.py
├── tests/                  # 测试代码
│   ├── __init__.py
│   └── test_module1.py
├── main.py                 # 主程序入口
└── requirements.txt        # 依赖列表
```

### 样例Python代码

**src/module1.py**:
```python
def greet(name):
    """
    Return a greeting message for the given name.
    
    Args:
        name (str): The name to greet
        
    Returns:
        str: The greeting message
    """
    return f"Hello, {name}!"
```

**tests/test_module1.py**:
```python
import unittest
from src.module1 import greet

class TestModule1(unittest.TestCase):
    def test_greet(self):
        self.assertEqual(greet("World"), "Hello, World!")
        
if __name__ == "__main__":
    unittest.main()
```

**main.py**:
```python
from src.module1 import greet

if __name__ == "__main__":
    name = input("Enter your name: ")
    print(greet(name))
```

### 运行程序

**在终端中运行**

```bash
python main.py
```

**在VSCode中运行**

1. 打开`main.py`
2. 点击右上角的运行按钮或按`F5`

### 运行测试

**使用unittest**

```bash
python -m unittest discover
```

**使用pytest (如果已安装)**

```bash
python -m pytest
```

---

## 5. 常见问题解决

### Python路径问题

**问题**: 安装Python后命令`python`或`pip`无法使用

**解决方案**:

- **macOS/Linux**: 确保PATH环境变量中包含Python路径
  ```bash
  echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bash_profile
  source ~/.bash_profile
  ```
  
- **Windows**: 在安装时勾选"Add Python to PATH"或手动添加Python安装目录到系统PATH环境变量

### 虚拟环境问题

**问题**: `virtualenv`命令无法使用

**解决方案**:
```bash
# 使用pip安装或重新安装
pip3 install --upgrade virtualenv

# 或直接使用Python模块运行
python3 -m virtualenv venv
```

**问题**: 无法激活虚拟环境

**解决方案**:
- 确保在正确的目录下执行激活命令
- Windows上，可能需要更改PowerShell执行策略
  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
  ```

### VSCode问题

**问题**: VSCode不识别Python解释器

**解决方案**:
1. 确保已安装Python扩展
2. 使用命令面板手动选择解释器
3. 检查`settings.json`中的配置

**问题**: 虚拟环境在VSCode中不可用

**解决方案**:
1. 确保在VSCode的终端中激活了虚拟环境
2. 确保设置了正确的Python解释器路径

**问题**: 智能提示或自动完成不工作

**解决方案**:
1. 安装Pylance扩展
2. 确保项目结构正确，包含`__init__.py`文件
3. 检查语言服务器是否启用
4. 重新加载VSCode窗口

---

按照本指南的步骤，你应该能够在macOS、Linux或Windows平台上成功搭建一个完整的Python开发环境，包括Python 3安装、虚拟环境配置和VSCode设置。祝你编程愉快！
