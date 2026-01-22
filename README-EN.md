# Industry Mastery (chuinb-skill)

<p align="center">
  <img src="assets/icon.png" alt="Industry Mastery Icon" width="128" height="128">
</p>

<p align="center">
  <strong>Transform from outsider to insider in hours, not months</strong>
</p>

<p align="center">
  <img src="assets/landing-banner.png" alt="Industry Mastery Banner" width="100%">
</p>

---

This is a Claude Code skill that helps you quickly master any unfamiliar industry, field, or domain. It automatically searches for the latest information, downloads relevant images and videos, generates AI concept diagrams, and outputs a beautifully formatted learning note.

---

## What Can This Skill Do For You?

Imagine these scenarios:

- Meeting with investors about blockchain next week, but you know nothing about it?
- Want to transition to the renewable energy industry and need a quick overview?
- Friends invited you to discuss coffee culture, and you want to sound knowledgeable?

**Industry Mastery** will help you:

1. Explain the industry essence in simple terms (even a 12-year-old can understand)
2. Teach you industry jargon so you can talk like an insider
3. Introduce key figures and classic cases you must know
4. Generate beautiful images and videos to make learning more engaging
5. Provide flashcards and quizzes to help you retain knowledge
6. Save everything as a note you can review anytime

---

## Installation Guide (Beginner Friendly)

### Step 1: Make Sure You Have Claude Code Installed

If you can run the `claude` command in your terminal and see Claude's interface, you're all set.

If not, please visit [Claude Code official website](https://claude.ai/code) and follow the installation guide.

### Step 2: Install This Skill

Run the following commands in your terminal:

```bash
# Navigate to Claude Code's skills directory
cd ~/.claude/skills

# Create the directory if it doesn't exist
mkdir -p ~/.claude/skills

# Download this skill (if you got it from GitHub)
# git clone https://github.com/your-repo/chuinb-skill.git

# Or simply copy the entire chuinb-skill folder here
```

### Step 3: Install Dependencies

This skill requires some helper tools to work properly:

#### 1. Install Python Dependencies

```bash
pip install requests yt-dlp Pillow
```

#### 2. Install Video Processing Tool

**Mac users**:
```bash
brew install ffmpeg
```

**Windows users**:
Download and install from [ffmpeg official website](https://ffmpeg.org/download.html).

**Linux users**:
```bash
sudo apt install ffmpeg
```

### Step 4: Configure API Keys

This skill needs some free API keys to generate images and download media.

#### Get ModelScope API Key (for AI image generation)

1. Go to https://modelscope.cn
2. Register an account
3. After logging in, click your avatar → "My Access Tokens"
4. Create a new access token and copy it

#### Configure Environment Variables

**Mac/Linux users**, edit your `~/.zshrc` or `~/.bashrc` file:

```bash
# Open with your favorite editor, e.g.:
nano ~/.zshrc

# Add this line at the end:
export MODELSCOPE_API_KEY="your-copied-key"

# Save and run this command to apply:
source ~/.zshrc
```

**Windows users**:
1. Search for "Environment Variables"
2. Click "Edit the system environment variables"
3. Click "Environment Variables" button
4. Under "User variables", click "New"
5. Variable name: `MODELSCOPE_API_KEY`, Variable value: your key

#### (Optional) Configure Image Download API

If you want to download web images (not just AI-generated ones), you'll also need to configure image library APIs:

1. Visit https://www.pexels.com/api/ to register and get a free API Key
2. Add to environment variables: `export PEXELS_API_KEY="your-key"`

### Step 5: Verify Installation

Run in terminal:

```bash
# Check media-downloader status
python ~/.claude/skills/media-downloader/media_cli.py status
```

If you see yt-dlp and ffmpeg showing ✅, the installation is successful!

---

## How to Use

### Method 1: Natural Conversation

Open Claude Code and simply say:

```
Help me quickly understand the private equity industry
```

```
I want to become an insider in the coffee industry
```

```
I have a meeting about blockchain next week, help me get up to speed
```

### Method 2: Use Commands

```
/chuinb semiconductor industry
```

```
/master venture capital
```

### Usage Flow

1. **Answer a few questions**: Claude will first ask about your learning goals, background, and time budget
2. **Wait for research**: Claude will automatically search for latest info, download images and videos
3. **Choose save location**: Claude will ask where you want to save the notes
4. **Get your learning notes**: A beautifully formatted Markdown file with images and videos

---

## Output Example

After running, you'll get a file structure like this:

```
your-specified-directory/
├── Private-Equity-Quick-Guide.md    # Main document (can be opened with Obsidian)
└── media/                            # Media folder
    ├── diagram-value-chain.jpg       # AI-generated value chain diagram
    ├── diagram-process.jpg           # AI-generated process diagram
    └── video-explained.mp4           # Downloaded tutorial video
```

The notes include:
- One-sentence industry summary
- Industry essence analysis
- Professional terminology table
- Key figures introduction
- Classic case studies
- Video clips
- Flashcards and quizzes
- Action checklist

---

## FAQ

### Q: Getting "API Key required" error when generating images

**Solution**: Make sure you've configured the `MODELSCOPE_API_KEY` environment variable and restarted your terminal.

### Q: Video download fails

**Solution**:
1. Make sure yt-dlp is installed: `pip install yt-dlp`
2. Make sure ffmpeg is installed: `brew install ffmpeg` (Mac)

### Q: Image download fails

**Solution**: This skill prioritizes AI-generated images, so it's okay if image downloads fail. If you want to download web images, you need to configure Pexels or Pixabay API Keys.

### Q: Images/videos in notes don't display

**Solution**: This skill generates notes using Obsidian syntax (`![[filename]]`). We recommend using [Obsidian](https://obsidian.md) to open the notes, and images/videos will display properly.

### Q: Can I use Chinese or English?

**Answer**: Both! This skill supports bilingual Chinese and English. You can ask questions in either language, and it will generate content accordingly.

---

## Technical Support

If you encounter issues:

1. Type `/help` in Claude Code to see help
2. Check if environment variables are configured correctly
3. Make sure all dependency tools are installed

---

## Changelog

### v1.1.0 (2026-01-22)
- New: Mandatory media acquisition flow, ensuring images and videos are generated/downloaded every time
- New: Ask user for save path before saving
- New: Chinese and English README documentation
- Improved: Clearer execution flow

### v1.0.0
- Initial release
