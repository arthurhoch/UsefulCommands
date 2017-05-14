# UsefulCommands

## FIND

### About file/dir names

- Remove directory namespaces:

**$ find -name "* *" -type d | rename 's/ /_/g'**

-  Remove files namespaces:

  **$ find -name "* *" -type f | rename 's/ /_/g'**

## FFMPEG

### About H265

- Convert video (mp4||*) to video (H265/AAC/MP4)

ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4

- Convert video (mp4||*) to video (H265/AAC/MKV)

ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mkv

- Convert video (mp4||*) to video (H265/AAC/mp4) // A little more than the previous one

ffmpeg -i org.mp4 -c:v libx265 -c:a aac -threads 8 modified.H265.AAC.mp4

- Convert video (mp4||*) to video (H265/AAC/MP4||MKV/FILM) 

ffmpeg -i org.mp4 -c:v libx265 -tune filme -c:a aac -threads 8 modified.H265.AAC.mp4
