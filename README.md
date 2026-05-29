
![](https://files.mdnice.com/user/166515/9dfaae3f-61bb-478f-8f5b-682e3d18f3a4.png)

# 告别 Gemini CLI！Google 新神器 Antigravity CLI 上手指南（Windows 新手版）

核心命令只有一个：`agy`。

跟着这篇走，10 分钟搞定安装、登录、第一个 Prompt。


# 写在前面

Google 已于 **2026 年 5 月 19 日**正式宣布 Antigravity CLI 向所有人开放。

![](https://files.mdnice.com/user/166515/6b090747-793e-4dc1-9675-76b35a3f28e8.png)

同时，Gemini CLI 将在 **2026 年 6 月 18 日**之后停止为免费用户、Google AI Pro 及 Ultra 用户提供服务。

也就是说——**现在该换了**。

本文面向 Windows 新手，手把手带你完成安装、登录和第一次使用。

# 一、你需要准备什么

开始之前，确认你手边有这几样东西：

- 一台 Windows / macOS / Linux 电脑
- 一个 Google 账号（不知道怎么注册谷歌邮箱可以点击查看文章：[2026 年国内最新注册 Gmail 谷歌邮箱教程 | 一部手机五分钟，注册成功率90%以上](https://clawdo.com/2026/04/Google-Email-Registration/)）
- 能正常访问 Google 服务的网络
- 一个用于测试的项目文件夹，比如 `D:\agy-demo`

Antigravity CLI 原生支持 Windows、macOS 和 Linux，安装后统一通过 `agy` 命令启动，简洁干净。


# 二、安装 Antigravity CLI

### Windows 推荐：用 PowerShell

打开 **PowerShell**，粘贴以下命令并回车：

```powershell
irm https://antigravity.google/cli/install.ps1 | iex
```

### 备选：用 CMD

打开**命令提示符（CMD）**，执行：

```cmd
curl -fsSL https://antigravity.google/cli/install.cmd -o install.cmd && install.cmd && del install.cmd
```

### macOS / Linux

```bash
curl -fsSL https://antigravity.google/cli/install.sh | bash
```

安装完成后，`agy` 会自动加入系统路径，无需手动配置。



# 三、验证是否安装成功

安装完成后，**关闭终端，重新打开 PowerShell**，输入：

```powershell
agy --version
```

看到版本号，说明一切正常。

![](https://files.mdnice.com/user/166515/92b02228-f399-457a-b564-9cbfbe98cb1f.png)

# 四、第一次登录

直接运行：`agy`

第一次启动会进入登录引导，你会看到：


![](https://files.mdnice.com/user/166515/5c064f5e-eb27-441f-889d-a9d997f29f9f.png)


**普通个人用户选第 1 项：Google OAuth。**

![](https://files.mdnice.com/user/166515/113da634-eac0-4d04-8ca6-5f56070cbb4e.png)

它会自动打开浏览器（未自动打开你可以复制链接到浏览器，自行打开授权），用你的 Google 账号完成授权。

![](https://files.mdnice.com/user/166515/8dc233f4-a0d1-476a-9c1c-1c84bc292308.png)


授权成功后，按提示把授权码粘贴回终端。

![复制授权码](https://files.mdnice.com/user/166515/3c3cb623-d17e-444d-bef3-117c3433ea46.png)

![填写授权码，等待登录](https://files.mdnice.com/user/166515/4d3c80f8-f1b9-402f-b79c-86b656a0c6d8.png)

再接受一下条款，就完成了。


> **什么时候选第 2 项？** 如果你是企业用户、有 GCP 项目或团队协作场景，才需要选 `Use a Google Cloud project`。个人用户无需考虑。



# 五、创建并进入测试项目

强烈建议新手先建一个空文件夹来练手，避免误改真实项目：

```powershell
mkdir C:\Users\屎努比\Desktop\grokdemo1
cd C:\Users\屎努比\Desktop\grokdemo1
agy
```

第一次进入新文件夹，它会问你是否信任该目录：


![](https://files.mdnice.com/user/166515/5431fa06-b037-4364-bcc2-9956e083ddf8.png)


选 **Yes**——Antigravity CLI 需要读取和操作当前目录里的文件，这是正常权限请求。


![](https://files.mdnice.com/user/166515/d1f31b9c-15b5-45ea-bbb3-63e09216e68d.png)
`


# 六、第一个 Prompt，现在就试

进入 `agy` 交互界面后，可以直接输入中文。

**分析项目结构（推荐第一步）：**
`
你现在是我的编程助手。请先阅读当前项目结构，不要修改任何文件。然后用中文告诉我：这个项目是什么、主要文件有哪些、下一步适合做什么。
`

**让它创建一个小页面：**
`
请帮我创建一个最简单的 HTML + CSS + JS 页面，主题是待办事项列表，
要求页面简洁、可运行，并解释每个文件的作用。
`

> **新手提示**：先不要开"完全自动执行"模式。让它给出修改计划，你确认后再执行，这样最安全。



# 七、常用内置命令速查

进入 `agy` 后，这几个命令最常用：

| 命令 | 作用 |
|------|------|
| `/settings` | 打开设置面板 |
| `/config` | 修改配置（主题、模型、工具权限等） |
| `/permissions` | 查看或修改工具权限 |
| `?` | 查看快捷键和帮助 |

配置文件默认保存在：
`
~/.gemini/antigravity-cli/settings.json
`


# 八、如何更新

`
agy update
`
更新后重新打开终端，运行 `agy --version` 确认版本已更新。


# 九、常见问题解答

###  `agy` 提示"不是内部或外部命令"

环境变量未生效。解决方法：**关闭 PowerShell，重新打开**，再试一次。如果还不行，重新执行安装命令即可。



###  登录后反复要求重新登录

先执行更新：`agy update`

这个问题在 1.0.1 版本已修复，更新后重启 `agy` 即可恢复正常。WSL 环境下此问题偶发，同样建议更新解决。



# 十、新手练习路线图

刚开始别急着让它改大项目，按这个顺序循序渐进，最稳：

```
第一步：让它读取并分析项目结构
第二步：让它解释某段代码
第三步：让它新增一个小功能
第四步：让它修复一个明确的 bug
第五步：让它生成 README 文档
第六步：熟练后，再考虑让它重构项目
```

功能越来越强大，但每一步你都清楚发生了什么——这才是用好 AI 编程工具的正确姿势。



# 小结

Antigravity CLI 的使用门槛其实很低，核心就一个命令：`agy`。安装、登录、信任项目、开始对话，全程不超过 10 分钟。


