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

__ffmpeg -i input.mp4 -s hd480 -c:v libx264 -crf 23 -c:a aac -strict -2 output.mp4__



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





CREATE OR REPLACE FUNCTION db_to_csv(path TEXT) RETURNS void AS $$
declare
   tables RECORD;
   statement TEXT;
begin
FOR tables IN 
   SELECT (table_name) AS schema_table
   FROM information_schema.tables t INNER JOIN information_schema.schemata s 
   ON s.schema_name = t.table_schema 
   WHERE t.table_schema NOT IN ('pg_catalog', 'information_schema')
   AND t.table_type NOT IN ('VIEW')
   ORDER BY schema_table
LOOP
   statement := 'COPY "' || tables.schema_table || '" TO ''' || path || '\' || tables.schema_table || '.csv' ||''' DELIMITER '';'' CSV HEADER';
   EXECUTE statement;
END LOOP;
return;  
end;
$$ LANGUAGE plpgsql;

SELECT db_to_csv('C:\Program Files\PostgreSQL\9.5\data');


