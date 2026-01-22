# 行业速成大师 (chuinb-skill)

<p align="center">
  <img src="assets/icon.png" alt="Industry Mastery Icon" width="128" height="128">
</p>

<p align="center">
  <strong>让你在几小时内从行业小白变成内行人</strong>
</p>

<p align="center">
  <img src="assets/landing-banner.png" alt="Industry Mastery Banner" width="100%">
</p>

---

这是一个 Claude Code 技能（skill），帮助你快速掌握任何陌生的行业、领域或技能。它会自动搜索最新信息、下载相关图片和视频、生成 AI 概念图，最终输出一份精美的学习笔记。

---

## 这个技能能帮你做什么？

想象一下这些场景：

- 下周要和投资人聊区块链，但你完全不懂？
- 想转行到新能源行业，需要快速了解行业全貌？
- 朋友约你聊咖啡文化，你想显得很懂行？

**行业速成大师**会帮你：

1. 用最简单的语言解释行业本质（连12岁小孩都能听懂）
2. 教你行业黑话，让你说话像个内行人
3. 介绍必知的关键人物和经典案例
4. 生成精美的图片和视频，让学习更生动
5. 提供闪卡和测验，帮你巩固记忆
6. 最后保存成一份可以随时翻阅的笔记

---

## 安装指南（小白友好版）

### 第一步：确认你已经安装了 Claude Code

如果你能在终端里运行 `claude` 命令并看到 Claude 的界面，说明你已经安装好了。

如果还没安装，请先访问 [Claude Code 官网](https://claude.ai/code) 按照指引安装。

### 第二步：安装这个技能

在终端里运行以下命令：

```bash
# 进入 Claude Code 的技能目录
cd ~/.claude/skills

# 如果目录不存在，先创建它
mkdir -p ~/.claude/skills

# 下载这个技能（如果你是从 GitHub 获取的）
# git clone https://github.com/your-repo/chuinb-skill.git

# 或者直接复制整个 chuinb-skill 文件夹到这里
```

### 第三步：安装依赖工具

这个技能需要一些辅助工具才能正常工作：

#### 1. 安装 Python 依赖

```bash
pip install requests yt-dlp Pillow
```

#### 2. 安装视频处理工具

**Mac 用户**：
```bash
brew install ffmpeg
```

**Windows 用户**：
从 [ffmpeg 官网](https://ffmpeg.org/download.html) 下载并安装。

**Linux 用户**：
```bash
sudo apt install ffmpeg
```

### 第四步：配置 API 密钥

这个技能需要一些免费的 API 密钥来生成图片和下载素材。

#### 获取 ModelScope API Key（用于 AI 生成图片）

1. 打开 https://modelscope.cn
2. 注册一个账号（可以用手机号）
3. 登录后，点击右上角头像 → "我的访问令牌"
4. 创建一个新的访问令牌，复制它

#### 配置环境变量

**Mac/Linux 用户**，编辑你的 `~/.zshrc` 或 `~/.bashrc` 文件：

```bash
# 用你喜欢的编辑器打开，比如：
nano ~/.zshrc

# 在文件末尾添加这一行：
export MODELSCOPE_API_KEY="你复制的密钥"

# 保存后，运行这个命令让配置生效：
source ~/.zshrc
```

**Windows 用户**：
1. 搜索"环境变量"
2. 点击"编辑系统环境变量"
3. 点击"环境变量"按钮
4. 在"用户变量"中点击"新建"
5. 变量名填 `MODELSCOPE_API_KEY`，变量值填你的密钥

#### （可选）配置图片下载 API

如果你想下载网络图片（而不只是 AI 生成），还需要配置图库 API：

1. 访问 https://www.pexels.com/api/ 注册获取免费 API Key
2. 添加到环境变量：`export PEXELS_API_KEY="你的密钥"`

### 第五步：验证安装

在终端运行：

```bash
# 检查 media-downloader 状态
python ~/.claude/skills/media-downloader/media_cli.py status
```

如果看到 yt-dlp 和 ffmpeg 显示 ✅，说明安装成功了！

---

## 使用方法

### 方法一：直接对话

打开 Claude Code，直接用自然语言说：

```
帮我快速了解私募股权行业
```

```
我想成为咖啡行业的内行人
```

```
下周要和区块链的人聊天，帮我速成
```

### 方法二：使用命令

```
/chuinb 半导体行业
```

```
/master venture capital
```

### 使用流程

1. **回答几个问题**：Claude 会先问你学习目标、背景和时间预算
2. **等待研究**：Claude 会自动搜索最新信息、下载图片视频
3. **选择保存位置**：Claude 会问你想把笔记保存到哪里
4. **获得学习笔记**：一份精美的 Markdown 文件，包含图片和视频

---

## 输出示例

运行后，你会得到这样的文件结构：

```
你指定的目录/
├── 私募股权行业速成指南.md    # 主文档（可以用 Obsidian 打开）
└── media/                      # 媒体文件夹
    ├── diagram-value-chain.jpg # AI 生成的价值链图
    ├── diagram-process.jpg     # AI 生成的流程图
    └── video-explained.mp4     # 下载的教学视频
```

笔记内容包括：
- 一句话看懂行业
- 行业本质分析
- 专业术语表
- 必知人物介绍
- 经典案例分析
- 视频片段
- 闪卡和测验
- 行动清单

---

## 常见问题

### Q: 生成图片时报错 "API Key required"

**解决方法**：确保你已经配置了 `MODELSCOPE_API_KEY` 环境变量，并且重启了终端。

### Q: 视频下载失败

**解决方法**：
1. 确保安装了 yt-dlp：`pip install yt-dlp`
2. 确保安装了 ffmpeg：`brew install ffmpeg`（Mac）

### Q: 图片下载失败

**解决方法**：这个技能会优先使用 AI 生成图片，所以即使图片下载失败也没关系。如果你想下载网络图片，需要配置 Pexels 或 Pixabay 的 API Key。

### Q: 笔记里的图片/视频显示不出来

**解决方法**：这个技能生成的笔记使用 Obsidian 的语法（`![[文件名]]`）。推荐使用 [Obsidian](https://obsidian.md) 打开笔记，图片和视频就能正常显示了。

### Q: 可以用中文还是英文？

**回答**：都可以！这个技能支持中英文双语，你可以用中文或英文提问，它会根据你的语言生成对应的内容。

---

## 技术支持

如果遇到问题，可以：

1. 在 Claude Code 中输入 `/help` 查看帮助
2. 检查环境变量是否配置正确
3. 确保所有依赖工具都已安装

---

## 更新日志

### v1.1.0 (2026-01-22)
- 新增：强制媒体获取流程，确保每次都生成图片和下载视频
- 新增：保存前询问用户路径
- 新增：中英文 README 文档
- 优化：更清晰的执行流程

### v1.0.0
- 初始版本发布
