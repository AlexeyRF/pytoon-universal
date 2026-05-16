# PyToon
[![Downloads](https://static.pepy.tech/badge/pytoon)](https://pepy.tech/project/pytoon)

[English](#english) | [Р СѓСЃСЃРєРёР№](#СЂСѓСЃСЃРєРёР№)

---

<a name="english"></a>
## English

### Overview 
PyToon is a Python-based animation library for automatically animating characters and their mouth movements from just an audio file (.mp3 or .wav) of a person speaking English. This tool uses machine learning-based audio analysis techniques to automatically lip-sync animated character mouth movements to a given audio recording of someone talking. 

**Note on Current Version:** To keep the package lightweight and flexible, animation assets (character poses and mouth shapes) are no longer bundled with the library. You must provide a path to an assets folder when initializing the `animate` class. This allows you to easily swap characters and styles.

[Example Output Video](https://www.youtube.com/watch?v=Sg2OBBNwF-k&ab_channel=LKerbs)

**Installation:** `pip install pytoon`

### Features
- Automatically create cartoon animated lip-sync videos from just an audio file.
- Use a provided transcript or let PyToon automatically generate the transcript from the audio with built-in text-to-speech.
- Programmatically generate animated videos.
- Overlay animations over custom background videos or images.
- OS Independent! PyToon works on Mac, Windows, and Linux.
- Optimized for both CPU and GPU.
- Fast Processing! A 60-second lip-sync animation clip takes ~39 seconds to generate.

### Getting Started 
1. Install pytoon: `pip3 install pytoon`
2. Install ffmpeg:
    - Mac: `brew install ffmpeg`
    - Linux: `sudo apt install ffmpeg`
    - Windows: Install from [ffmpeg.org](https://ffmpeg.org/download.html)
3. **Download Assets**: Ensure you have a directory containing the required character poses and visemes.

### Basic Usage

#### Example 1: Generating Animation from an MP3 File (with transcript)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# Read audio transcript to a string.
transcript_path = "./.temp/speech.txt"
with open(transcript_path, "r") as file:
    transcript = file.read()

# Create a PyToon animation 
animation = animate(
    audio_file="speech.mp3",  # Input audio
    transcript=transcript,   # Audio transcript
    assets_path="./assets"   # Path to your character assets directory
)

# Overlay the animation on top of another video and save as an .mp4 file.
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_with_transcript.mp4', background=background_video, scale=0.7)
```

#### Example 2: Generating Animation from an MP3 File (without transcript)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# Create a PyToon animation without providing a transcript
animation = animate(
    audio_file="speech.mp3",  # Input audio (transcript will be auto-generated)
    assets_path="./assets"    # Path to your character assets directory
)

# Overlay the animation on top of another video and save as an .mp4 file.
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_auto_transcript.mp4', background=background_video, scale=0.7)
```

---

<a name="СЂСѓСЃСЃРєРёР№"></a>
## Р СѓСЃСЃРєРёР№

### РћР±Р·РѕСЂ
PyToon вЂ” СЌС‚Рѕ Р±РёР±Р»РёРѕС‚РµРєР° РґР»СЏ Р°РЅРёРјР°С†РёРё РЅР° СЏР·С‹РєРµ Python, РїСЂРµРґРЅР°Р·РЅР°С‡РµРЅРЅР°СЏ РґР»СЏ Р°РІС‚РѕРјР°С‚РёС‡РµСЃРєРѕРіРѕ СЃРѕР·РґР°РЅРёСЏ Р°РЅРёРјР°С†РёРё РїРµСЂСЃРѕРЅР°Р¶РµР№ Рё РґРІРёР¶РµРЅРёР№ РёС… СЂС‚Р° РЅР° РѕСЃРЅРѕРІРµ Р°СѓРґРёРѕС„Р°Р№Р»Р° (.mp3 РёР»Рё .wav). РРЅСЃС‚СЂСѓРјРµРЅС‚ РёСЃРїРѕР»СЊР·СѓРµС‚ РјРµС‚РѕРґС‹ Р°РЅР°Р»РёР·Р° Р·РІСѓРєР° РЅР° Р±Р°Р·Рµ РјР°С€РёРЅРЅРѕРіРѕ РѕР±СѓС‡РµРЅРёСЏ РґР»СЏ Р°РІС‚РѕРјР°С‚РёС‡РµСЃРєРѕР№ СЃРёРЅС…СЂРѕРЅРёР·Р°С†РёРё РіСѓР± (lip-sync) Р°РЅРёРјРёСЂРѕРІР°РЅРЅРѕРіРѕ РїРµСЂСЃРѕРЅР°Р¶Р° СЃ Р·Р°РїРёСЃСЊСЋ СЂРµС‡Рё.

**РћСЃРѕР±РµРЅРЅРѕСЃС‚Рё С‚РµРєСѓС‰РµР№ РІРµСЂСЃРёРё:** Р”Р»СЏ РјРёРЅРёРјРёР·Р°С†РёРё СЂР°Р·РјРµСЂР° РїР°РєРµС‚Р° Рё РїРѕРІС‹С€РµРЅРёСЏ РіРёР±РєРѕСЃС‚Рё, Р°СЃСЃРµС‚С‹ Р°РЅРёРјР°С†РёРё (РїРѕР·С‹ РїРµСЂСЃРѕРЅР°Р¶РµР№ Рё С„РѕСЂРјС‹ СЂС‚Р°) Р±РѕР»СЊС€Рµ РЅРµ РїРѕСЃС‚Р°РІР»СЏСЋС‚СЃСЏ РІРјРµСЃС‚Рµ СЃ Р±РёР±Р»РёРѕС‚РµРєРѕР№. РџСЂРё РёРЅРёС†РёР°Р»РёР·Р°С†РёРё РєР»Р°СЃСЃР° `animate` РЅРµРѕР±С…РѕРґРёРјРѕ СѓРєР°Р·Р°С‚СЊ РїСѓС‚СЊ Рє РїР°РїРєРµ СЃ Р°СЃСЃРµС‚Р°РјРё (`assets_path`). Р­С‚Рѕ РїРѕР·РІРѕР»СЏРµС‚ Р»РµРіРєРѕ РјРµРЅСЏС‚СЊ РїРµСЂСЃРѕРЅР°Р¶РµР№ Рё СЃС‚РёР»Рё Р°РЅРёРјР°С†РёРё.

[РџСЂРёРјРµСЂ РІРёРґРµРѕ](https://www.youtube.com/watch?v=Sg2OBBNwF-k&ab_channel=LKerbs)

**РЈСЃС‚Р°РЅРѕРІРєР°:** `pip install pytoon`

### Р’РѕР·РјРѕР¶РЅРѕСЃС‚Рё
- РђРІС‚РѕРјР°С‚РёС‡РµСЃРєРѕРµ СЃРѕР·РґР°РЅРёРµ Р°РЅРёРјР°С†РёРё СЃРёРЅС…СЂРѕРЅРёР·Р°С†РёРё РіСѓР± РЅР° РѕСЃРЅРѕРІРµ Р°СѓРґРёРѕС„Р°Р№Р»Р°.
- РСЃРїРѕР»СЊР·РѕРІР°РЅРёРµ РіРѕС‚РѕРІРѕРіРѕ С‚РµРєСЃС‚Р° РёР»Рё РµРіРѕ Р°РІС‚РѕРјР°С‚РёС‡РµСЃРєР°СЏ РіРµРЅРµСЂР°С†РёСЏ РёР· Р°СѓРґРёРѕ СЃ РїРѕРјРѕС‰СЊСЋ РІСЃС‚СЂРѕРµРЅРЅРѕР№ СЃРёСЃС‚РµРјС‹ СЂР°СЃРїРѕР·РЅР°РІР°РЅРёСЏ СЂРµС‡Рё.
- РџСЂРѕРіСЂР°РјРјРЅРѕРµ СЃРѕР·РґР°РЅРёРµ РІРёРґРµРѕСЂРѕР»РёРєРѕРІ.
- РќР°Р»РѕР¶РµРЅРёРµ Р°РЅРёРјР°С†РёРё РЅР° С„РѕРЅРѕРІРѕРµ РІРёРґРµРѕ РёР»Рё РёР·РѕР±СЂР°Р¶РµРЅРёСЏ.
- РљСЂРѕСЃСЃРїР»Р°С‚С„РѕСЂРјРµРЅРЅРѕСЃС‚СЊ: СЂР°Р±РѕС‚Р°РµС‚ РЅР° Mac, Windows Рё Linux.
- РћРїС‚РёРјРёР·Р°С†РёСЏ РґР»СЏ CPU Рё GPU.
- Р’С‹СЃРѕРєР°СЏ СЃРєРѕСЂРѕСЃС‚СЊ СЂР°Р±РѕС‚С‹: 60-СЃРµРєСѓРЅРґРЅС‹Р№ СЂРѕР»РёРє СЃРѕР·РґР°РµС‚СЃСЏ РїСЂРёРјРµСЂРЅРѕ Р·Р° 39 СЃРµРєСѓРЅРґ.

### РќР°С‡Р°Р»Рѕ СЂР°Р±РѕС‚С‹
1. РЈСЃС‚Р°РЅРѕРІРёС‚Рµ pytoon: `pip3 install pytoon`
2. РЈСЃС‚Р°РЅРѕРІРёС‚Рµ ffmpeg:
    - Mac: `brew install ffmpeg`
    - Linux: `sudo apt install ffmpeg`
    - Windows: РЎРєР°С‡Р°Р№С‚Рµ СЃ [ffmpeg.org](https://ffmpeg.org/download.html)
3. **РџРѕРґРіРѕС‚РѕРІСЊС‚Рµ Р°СЃСЃРµС‚С‹**: РЈР±РµРґРёС‚РµСЃСЊ, С‡С‚Рѕ Сѓ РІР°СЃ РµСЃС‚СЊ РїР°РїРєР° СЃ РЅРµРѕР±С…РѕРґРёРјС‹РјРё РїРѕР·Р°РјРё РїРµСЂСЃРѕРЅР°Р¶Р° Рё РёР·РѕР±СЂР°Р¶РµРЅРёСЏРјРё РіСѓР± (visemes).

### Р‘Р°Р·РѕРІРѕРµ РёСЃРїРѕР»СЊР·РѕРІР°РЅРёРµ

#### РџСЂРёРјРµСЂ 1: Р“РµРЅРµСЂР°С†РёСЏ Р°РЅРёРјР°С†РёРё РёР· MP3 (СЃ С‚РµРєСЃС‚РѕРј)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# Р§С‚РµРЅРёРµ С‚РµРєСЃС‚Р° СЂРµС‡Рё РёР· С„Р°Р№Р»Р°
transcript_path = "./.temp/speech.txt"
with open(transcript_path, "r", encoding="utf-8") as file:
    transcript = file.read()

# РЎРѕР·РґР°РЅРёРµ Р°РЅРёРјР°С†РёРё PyToon
animation = animate(
    audio_file="speech.mp3",  # Р’С…РѕРґРЅРѕРµ Р°СѓРґРёРѕ
    transcript=transcript,   # РўРµРєСЃС‚ СЂРµС‡Рё
    assets_path="./assets"   # РџСѓС‚СЊ Рє РїР°РїРєРµ СЃ Р°СЃСЃРµС‚Р°РјРё РїРµСЂСЃРѕРЅР°Р¶Р°
)

# РќР°Р»РѕР¶РµРЅРёРµ Р°РЅРёРјР°С†РёРё РЅР° С„РѕРЅРѕРІРѕРµ РІРёРґРµРѕ Рё СЃРѕС…СЂР°РЅРµРЅРёРµ РІ .mp4
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_with_transcript.mp4', background=background_video, scale=0.7)
```

#### РџСЂРёРјРµСЂ 2: Р“РµРЅРµСЂР°С†РёСЏ Р°РЅРёРјР°С†РёРё РёР· MP3 (Р±РµР· С‚РµРєСЃС‚Р°)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# РЎРѕР·РґР°РЅРёРµ Р°РЅРёРјР°С†РёРё Р±РµР· РїСЂРµРґРІР°СЂРёС‚РµР»СЊРЅРѕРіРѕ С‚РµРєСЃС‚Р° (Р±СѓРґРµС‚ СЃРіРµРЅРµСЂРёСЂРѕРІР°РЅ Р°РІС‚РѕРјР°С‚РёС‡РµСЃРєРё)
animation = animate(
    audio_file="speech.mp3",  # Р’С…РѕРґРЅРѕРµ Р°СѓРґРёРѕ
    assets_path="./assets"    # РџСѓС‚СЊ Рє РїР°РїРєРµ СЃ Р°СЃСЃРµС‚Р°РјРё РїРµСЂСЃРѕРЅР°Р¶Р°
)

# РќР°Р»РѕР¶РµРЅРёРµ Р°РЅРёРјР°С†РёРё РЅР° С„РѕРЅРѕРІРѕРµ РІРёРґРµРѕ
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_auto_transcript.mp4', background=background_video, scale=0.7)
```

---

## Contributing / РЈС‡Р°СЃС‚РёРµ РІ СЂР°Р·СЂР°Р±РѕС‚РєРµ
(See English version for detailed steps)

## Acknowledgements / Р‘Р»Р°РіРѕРґР°СЂРЅРѕСЃС‚Рё
This project uses character images open sourced by: [GitHub: lazykh](https://github.com/carykh/lazykh)
You can check out his YouTube channel here: [YouTube: carykh](https://youtube.com/@carykh)
