# FFmpeg

First of all, you need to type `cmd` on `C:\ffmpeg\bin` to launch.

Converting files:
```cs
ffmpeg -i "C:\FFM1\OGG\track.ogg" -q:a 0 "C:\FFM1\MP3\track.mp3"
```

Mass converting an entire folder:
```cs
for %f in ("C:\FFM1\OGG\*.ogg") do ffmpeg -i "%f" -c:a libmp3lame -b:a 192k "C:\FFM1\MP3\%~nf.mp3"
```


