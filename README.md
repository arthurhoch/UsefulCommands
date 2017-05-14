# UsefulCommands

## FIND

### About file/dir names

- Remove directory namespaces:

__$ find -name "* *" -type d | rename 's/ /_/g'__

-  Remove files namespaces:

__$ find -name "* *" -type f | rename 's/ /_/g'__

## FFMPEG

### About H265

- Convert video (mp4||*) to video (H265/AAC/MP4)

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4__

- Convert video (mp4||*) to video (H265/AAC/MKV)

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mkv__

- Convert video (mp4||*) to video (H265/AAC/mp4) // A little more than the previous one

__ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4__

- Convert video (mp4||*) to video (H265/AAC/MP4||MKV/FILM) 

__ffmpeg -i org.mp4 -c:v libx265 -tune filme -c:a aac -threads 8 modified.H265.AAC.mp4__
