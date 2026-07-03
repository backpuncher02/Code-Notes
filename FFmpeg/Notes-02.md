Absolutely. These are the two FFmpeg spells I'd keep in a notes file for future Raine. 🧙‍♀️🎬

# 1. Video + Sound

Use when you have:

* One video file
* One audio file
* Want the audio to replace the video's original audio

```bash
ffmpeg -i "video.ogg" -i "audio.ogg" -map 0:v:0 -map 1:a:0 -c:v libx264 -c:a aac -shortest "output.mp4"
```

### Example

```bash
ffmpeg -i "final_cutsceneV.ogg" -i "final_cutsceneS.ogg" -map 0:v:0 -map 1:a:0 -c:v libx264 -c:a aac -shortest "final_cutscene.mp4"
```

---

# 2. Video + Voice + Music

Use when you have:

* One video file
* One voice file
* One music file
* Want voice and music mixed together

```bash
ffmpeg -i "video.ogg" -i "voice.ogg" -i "music.ogg" -filter_complex "[1:a][2:a]amix=inputs=2:duration=shortest[a]" -map 0:v:0 -map "[a]" -c:v libx264 -c:a aac -shortest "output.mp4"
```

### Example

```bash
ffmpeg -i "cutscene.ogg" -i "voice.ogg" -i "music.ogg" -filter_complex "[1:a][2:a]amix=inputs=2:duration=shortest[a]" -map 0:v:0 -map "[a]" -c:v libx264 -c:a aac -shortest "cutscene_final.mp4"
```

---

# Bonus: Video + Voice + Quieter Music

If the music keeps body-slamming the dialogue:

```bash
ffmpeg -i "video.ogg" -i "voice.ogg" -i "music.ogg" -filter_complex "[2:a]volume=0.3[music];[1:a][music]amix=inputs=2:duration=shortest[a]" -map 0:v:0 -map "[a]" -c:v libx264 -c:a aac -shortest "output.mp4"
```

Here:

```text
0.3 = 30% volume
0.5 = 50% volume
1.0 = 100% volume
```

---

## The Cheat Sheet

```text
2 files:
Video + Audio
↓
-map 0:v:0 -map 1:a:0

3 files:
Video + Voice + Music
↓
-filter_complex "[1:a][2:a]amix=inputs=2[a]"
```

That's honestly enough FFmpeg knowledge to handle about 90% of the media wizardry you'll likely need for PuppetShow, Joyville cutscenes, voiceovers, and lore videos. 🎬✨
