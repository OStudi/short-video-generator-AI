# AI shorts generator

![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![Stars](https://img.shields.io/github/stars/OStudi/short-video-generator-AI?style=social) ![Forks](https://img.shields.io/github/forks/OStudi/short-video-generator-AI?style=social)

A free open-source project designed to turn youtube-videos into viral short videos. Highlight detection, subtitles, translation, voiceover, all in one for your content: no pre-clip credits or any watermarks. Designed for creators who want an alternative to short-video SaaS tools like OpusClip or Vidyo.ai for free. 

## Examples of a  processed video
<table>
  <tr>
    <td align="center">
      <img width="360" height="670" alt="image" src="assets/ex1.png" ><br>
      <sub><i>"The Speech that Made Obama President"</i></sub>
    </td>
    <td align="center">
      <img width="298" height="533" alt="image" src="assets/ex2.png" ><br>
      <sub><i>"How Tom Overcame Social Anxiety - The Mindset That Changed Everything"</i></sub>
    </td>
    <td align="center">
      <img width="298" height="533" alt="image" src="assets/ex3.png" ><br>
      <sub><i>"How to stay calm when you know you'll be stressed | Daniel Levitin | TED"</i></sub>
    </td>
  </tr>
</table>

# Features 🪁
- **API**: Freely use this generator in your own projects via our API.
- **Convenient**: Paste a YouTube link (any length!) and get a ready-to-post 9:16 short.
- **Hooks option**: When enabled, adds a context-aware AI-generated hook at the start of the clip
- **Web version**: Besides the CLI, you can also generate videos on a local website
- **Smart Highlight Selection**: Finds the most viral, hot moments from your video automatically based on algorithm

# Requirements
- Python 3.10+
- Any LLM API key(OpenAI/Gemini/MuAPI)
- `requirements.txt` file dependencies

# Quick start
1. **Clone the repo:**

```bash
git clone https://github.com/OStudi/short-video-generator-AI.git
cd short-video-generator-AI
```

2. **Create and activate a virtual environment:**

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```
**Linux/MacOS:**
```bash
python -m venv venv
venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Set up `.env`**
```env
# Used LLM provider(openai/gemini/MuAPI)
LLM_PROVIDER=openai

# Enter the API key for the chosen provider
OPENAI_API_KEY=your_openai_key_here
OPENAI_MODEL=gpt-4o-mini          # optional
GEMINI_API_KEY=your_gemini_key_here
GEMINI_MODEL=gemini-2.5-flash      # optional
MUAPI_API_KEY=your_muapi_key_here

# Whisper settings
LOCAL_WHISPER_MODEL=base # tiny / base / small / medium / large-v3
LOCAL_WHISPER_DEVICE=auto    # auto / cpu / cuda
```
If you uncertain about the provider:
| Provider | Free tier? | Get key |
|---|---|---|
| **Gemini** | ✅ Yes, but daily limit | https://aistudio.google.com |
| **OpenAI** | ❌ Paid | https://platform.openai.com |
| **MuAPI** | ❌ Paid, but pay-per-use, no subscription  | https://muapi.ai |

# Usage
Basic usage:

```bash
python main.py "https://www.youtube.com/watch?v=video_id" 
```


Renderred clips are saved to `output` folder

With flags:

```bash
python main.py "https://www.youtube.com/watch?v=video_id" \
      --n 3 \
      --ratio 9:16 \
      --resolution 1080 \
 ```
      
You can also provide a local video file instead of a YouTube link, for example:

```bash
python main.py "/Users/Admin/Folder/video.mp4" \
      --n 4 \
      --ratio 9:16 \
      --resolution 720 \
      --language zh \
```

## CLI Flags

| Flag | Default | Notes |
|------|---------|-------|
| --n | 3 | How many clips to render |
| --ratio | 9:16 | Any ratio / 9:16 for short videos / 1:1 for square |
| --resolution | 720 | Source video download resolution: `360` / `480` / `720` / `1080` |
| --language | auto | Force Whisper language code (e.g. `en`) |

## Web version set-up
You can also generate videos in your browser
