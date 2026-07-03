# FFmpeg

First of all, you need to type `cmd` on `C:\ffmpeg\bin` to launch.

Converting files:
```cs
ffmpeg -i "C:\FFM1\OGG\track.ogg" -q:a 0 "C:\FFM1\MP3\track.mp3"
```

```cs
ffmpeg -i "C:\FFM1\OGG\joyville.ogg" -vf scale=1024:192 "C:\FFM1\MP3\joyville.mp4"
```

Mass converting an entire folder:
```cs
for %f in ("C:\FFM1\OGG\*.ogg") do ffmpeg -i "%f" -c:a libmp3lame -b:a 192k "C:\FFM1\MP3\%~nf.mp3"
```
```cs
for %f in ("C:\FFM1\OGG\*.ogg") do ffmpeg -i "%f" -c:v libx264 -pix_fmt yuv420p "C:\FFM1\MP4\%~nf.mp4"
```

