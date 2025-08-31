# single file
```bash
heif-convert 20230225_181051.heic 20230225_181051.jpg
```
# multi files
```bash
mkdir converted; for f in *.heic; do heif-convert "$f" "converted/$f.jpg"; done
```
# install
```bash
sudo apt-get install libheif1
```
