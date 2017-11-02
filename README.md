# UsefulCommands

## FIND

find ./ -exec touch -t 201711020000 {} \;

### tar.xz

- Remove spaces in filenames:

- C:
__$ tar cf - dir | xz -e > dir.tar.xz

- X:
__$ tar xf  dir.tar.xz

- T:
__$ xz -t backup.xz

### About file/dir names

- Remove spaces in filenames:

- Directories:
__$ find -name "* *" -type d | rename 's/ /_/g'__

- Files
__$ find -name "* *" -type f | rename 's/ /_/g'__

- Or
__$ for f in *\ *; do mv "$f" "${f// /_}"; done__

## FFMPEG

### About H265

- Convert video (mp4||*) to video (H265/AAC/MP4)

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4__

- Convert video (mp4||*) to video (H265/AAC/MKV)

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mkv__

- Convert video (mp4||*) to video (H265/AAC/MP4) // A little more than the previous one

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4__

- Convert video (mp4||*) to video (H265/AAC/MP4||MKV/FILM) 

__ffmpeg -i org.mp4 -c:v libx265 -tune filme -c:a aac -threads 8 modified.H265.AAC.mp4__


## Debian / Ubuntu

### Create a packet (Ex: squid)

apt-get source squid
apt-get build-dep squid
apt-get install devscripts build-essential fakeroot
cd squid-(TAB)
vim debian/rules
Add --with-openssl \
    --enable-ssl-crtd \ 
In
./configure
debuild -us -uc -b
cd ..
dpkg -i squid*
