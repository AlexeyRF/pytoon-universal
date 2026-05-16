# PyToon

[English](#english) | [Русский](#русский)

---

<a name="english"></a>
## English

### Overview 
PyToon is a Python-based animation library for automatically animating characters and their mouth movements from just an audio file (.mp3 or .wav) of a person speaking English. This tool uses machine learning-based audio analysis techniques to automatically lip-sync animated character mouth movements to a given audio recording of someone talking. 

**Note on Current Version:** To keep the package lightweight and flexible, animation assets (character poses and mouth shapes) are no longer bundled with the library. You must provide a path to an assets folder when initializing the `animate` class. This allows you to easily swap characters and styles.

### Features
- Automatically create cartoon animated lip-sync videos from just an audio file.
- Use a provided transcript or let PyToon automatically generate the transcript from the audio with built-in text-to-speech.
- Programmatically generate animated videos.
- Overlay animations over custom background videos or images.
- OS Independent! PyToon works on Mac, Windows, and Linux.
- Optimized for both CPU and GPU.
- Fast Processing! A 60-second lip-sync animation clip takes ~39 seconds to generate.

### Getting Started 
1. Install pytoon-universal
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

<a name="русский"></a>
## Русский

### Обзор
PyToon - это библиотека для анимации на языке Python, предназначенная для автоматического создания анимации персонажей и движений их рта на основе аудиофайла (.mp3 или .wav). Инструмент использует методы анализа звука на базе машинного обучения для автоматической синхронизации губ (lip-sync) анимированного персонажа с записью речи.

**Особенности текущей версии:** Для минимизации размера пакета и повышения гибкости, ассеты анимации (позы персонажей и формы рта) больше не поставляются вместе с библиотекой. При инициализации класса `animate` необходимо указать путь к папке с ассетами (`assets_path`). Это позволяет легко менять персонажей и стили анимации.

### Возможности
- Автоматическое создание анимации синхронизации губ на основе аудиофайла.
- Использование готового текста или его автоматическая генерация из аудио с помощью встроенной системы распознавания речи.
- Программное создание видеороликов.
- Наложение анимации на фоновое видео или изображения.
- Кроссплатформенность: работает на Mac, Windows и Linux.
- Оптимизация для CPU и GPU.
- Высокая скорость работы: 60-секундный ролик создается примерно за 39 секунд.

### Начало работы
1. Установите pytoon-universal
2. Установите ffmpeg:
    - Mac: `brew install ffmpeg`
    - Linux: `sudo apt install ffmpeg`
    - Windows: Скачайте с [ffmpeg.org](https://ffmpeg.org/download.html)
3. **Подготовьте ассеты**: Убедитесь, что у вас есть папка с необходимыми позами персонажа и изображениями губ (visemes).

### Базовое использование

#### Пример 1: Генерация анимации из MP3 (с текстом)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# Чтение текста речи из файла
transcript_path = "./.temp/speech.txt"
with open(transcript_path, "r", encoding="utf-8") as file:
    transcript = file.read()

# Создание анимации PyToon
animation = animate(
    audio_file="speech.mp3",  # Входное аудио
    transcript=transcript,   # Текст речи
    assets_path="./assets"   # Путь к папке с ассетами персонажа
)

# Наложение анимации на фоновое видео и сохранение в .mp4
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_with_transcript.mp4', background=background_video, scale=0.7)
```

#### Пример 2: Генерация анимации из MP3 (без текста)
```python
from pytoon.animator import animate
from moviepy.editor import VideoFileClip

# Создание анимации без предварительного текста (будет сгенерирован автоматически)
animation = animate(
    audio_file="speech.mp3",  # Входное аудио
    assets_path="./assets"    # Путь к папке с ассетами персонажа
)

# Наложение анимации на фоновое видео
background_video = VideoFileClip("./path/to/background_video.mp4")
animation.export(path='video_auto_transcript.mp4', background=background_video, scale=0.7)
```

---
