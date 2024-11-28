# Extract audio tracks from videos
```sh
ffmpeg -i vid.mp4 -vn -acodec copy vid.aac
```
* `-vn` is no video.
* `-acodec copy` says use the same audio stream that's already in there.
# Downscale
Choose portrait/landscape (select appropriate command acording to video orientation)
```sh
filename=<infile>
ffmpeg -i $filename -vf scale=720:-1 -c:v libx264 -crf 18 -preset veryslow -c:a copy downscaled_${filename}
ffmpeg -i $filename -vf scale=-1:720 -c:v libx264 -crf 18 -preset veryslow -c:a copy downscaled_${filename}
```
# Process directory
https://stackoverflow.com/questions/9913032/how-can-i-extract-audio-from-video-with-ffmpeg
```sh
mkdir converted; for f in *.mp4; do ffmpeg -i "$f" "converted/conv.aac"; done
```
