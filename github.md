# 使用Trae通过github管理个人代码

## 前期准备

1. **安装必要软件**
   - 安装[Trae](https://www.trae.ai/download)
   - 安装[Git](https://git-scm.com/download/mac)
   - 创建[GitHub](https://github.com/)账号

3. **在GitHub上创建新仓库**
   - 访问GitHub网站并登录
   - 头像-->Your Repositories-->New创建新仓库
   - 添加README, .gitignore (选择Python模板), 和开源许可证
   - 
4. **Trae扩展安装**
   - 打开Trae，选择左侧的'Extension Store'
   - 搜索并安装以下扩展:
     - Python (Microsoft)
     - GitGraph

5. **创建SSH密钥**
  打开macOS的终端，输入以下命令创建密钥：
```bash
ssh-keygen -t rsa
```
后面提示可以不看，一路回车，最后生成的密钥会放在~/.ssh/目录下

6. **配置SSH连接**
   打开macOS的终端，输入以下命令：
   ```bash
cat << EOF > ~/.ssh/config
Host github.com
  HostName github.com
  Port 22
  User git
  identityFile ~/.ssh/id_rsa
EOF
   ```
  修改~/.ssh/目录下所有文件的权限：

```bash
chmod 600 ~/.ssh/*
ll ~/.ssh/* #查看文件列表，文件至少要有三个：id_rsa id_rsa_pub config，权限均为-rw-------
```

7. **测试github连接**
   ```bash
   ssh -T git@github.com
   ```
   出现以下内容说明连接成功：You've successfully authenticated, but GitHub does not provide shell access.

## 配置Git和GitHub

1. **配置Git个人信息**
  打开macOS的终端，在任意路径下输入：
   ```bash
   git config --global user.name "你的GitHub用户名"
   git config --global user.email "你的GitHub邮箱"
   ```

2. **在Trae中登录GitHub**
   - 打开github你的个人仓库（头像-->Your Repositories-->选择已经有的项目）
   - 找到绿色按键Code，点击下拉选项卡Local，选择SSH，并copy地址备用（例如：git@github.com:zeeler/pytest1.git）
   - 在Trae的File菜单中选择New Window，会打开新窗口，在窗口中选择`Clone Git Repository`
   - 粘贴在github中复制的项目SSH地址（例如：git@github.com:zeeler/pytest1.git）并回车
   - 第一次连接github时，可能会要求访问验证，要输入8位验证码，在Trae中就有，仔细看下窗口边角小字，类似“AB23-D243”字样
   - 弹窗窗口中，手工选择你想把项目目录放在什么地方（比如桌面），然后点击`Select as Repository Destination`
   - 在弹窗（Would you like to open the repository）选择Open或者在新window open都可
   - 在当前窗口Explorer下就可以看到代码文件

## 项目管理工作流

## 日常开发流程

1. **创建分支**
   - 点击Trae左下角的分支名称
   - 选择"Create new branch"输入新分支名称

2. **编写代码**
   - 创建/编辑Python文件
   - 使用Trae的Python支持功能(智能提示、调试等)

3. **提交更改**
   - 在Source Control面板(Ctrl+Shift+G)查看更改
   - 在更改文件上方点"+"暂存更改
   - 输入commit信息
   - 点击"✓" commit

4. **推送到GitHub**
   - 点击Source Control面板中的"..."
   - 选择"Push"或"Push to..."

5. **创建Pull Request**
   - 完成功能开发后，在GitHub扩展中创建Pull Request
   - 或直接在GitHub网站上创建

## 高级技巧

1. **使用.gitignore**
   - 确保`.gitignore`文件包含Python相关忽略项
   ```
   __pycache__/
   *.py[cod]
   *$py.class
   .venv/
   .vscode/
   ```

2. **利用Trae集成终端**
   - 使用`Ctrl+``打开终端
   - 运行git命令或Python脚本

3. **设置虚拟环境**
   - 创建虚拟环境: `virtualenv -p /usr/bin/python3.12 .venv`
   - 在Trae中选择Python解释器(右下角或命令面板)

4. **使用GitGraph查看历史**
   - 在Trae左侧主菜单列表中选择Source Control，左下部分Graph小窗口会显示版本信息
   - 查看行级别的修改记录和作者信息

## 最佳实践

- 经常提交小的变更而不是一次大提交
- 写清晰的提交信息
- 在功能分支上开发，完成后合并到主分支
- 使用Pull Requests进行代码审查
- 在合并前处理合并冲突

这样设置后，你就可以在Trae中高效地管理你的Python项目并与GitHub无缝协作了。
