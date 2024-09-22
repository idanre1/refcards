# Downscale
Choose portrait/landscape
```sh
filename=<infile>
ffmpeg -i $filename -vf scale=720:-1 -c:v libx264 -crf 18 -preset veryslow -c:a copy downscaled_${filename}
ffmpeg -i $filename -vf scale=-1:720 -c:v libx264 -crf 18 -preset veryslow -c:a copy downscaled_${filename}
```
