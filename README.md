# Worm Audiobook Binder

## Files

**original_audios/** - Not included. Chapter audio files downloaded from http://audioworm.rein-online.org/.

**processed_mp3s/** - Not included. Chapter audio trimmed of intros and outtros with some minor speech edits.

**abb-input-book-1.txt, etc** - These files provide the order and breakdown of the audios for the audiobook.  Change which arcs go in which book by editing these

**abb-input.txt** - Full list of all arcs in order, this can theoretically be used to bind the full audiobook but I had technical issues when generating a full book with the chapters.

**add_tags.sh** - This script sets tags (Song and Artist) on the files in processed_mp3s/ for use when generating chapter names

**abbinder** - This cli was scavenged from a 2014 version of AudioBookBinder.app that (as a package) no longer works.  This probably shouldn't be included here but it was such a pain to find.

**AudioBookBinder.app** - not included in this repo. Please install latest version from the MacOS App Store

**cover.jpg** - Cover art, not included. I used https://www.deviantart.com/sgcassidy/art/Skitter-Worm-A-Web-Serial-Wallpaper-490974462

**abb.sh** - Script to generate/build/bind the audiobooks.

## Build Process

After updating abb.sh, add_tags.sh, the abb-input-book files, or any of the processed_mp3s/ audios, regenerate the books

```bash
# First time only, make the scripts executable
chmod +x add_tags.sh
chmod +x abb.sh
```

```bash
# Set tags and build audiobooks
./add_tags.sh
./abb.sh
```

## Breakdown of commands in abb.sh

```
./abbinder -v -E "%t %a" -a "J.C. McCrae (Wildbow)" -C ./cover.jpg -b 128 \
-i abb-input-book-5.txt \
-t "Worm - Book 5" \
-o "Worm - Book 5.m4b"
```

**-E "%t %a"** - Sets chapter titles to "Title Artist" as set by add_tags.sh

**-a "J.C. McCrae (Wildbow)"** - Author text for final audiobook files

**-C ./cover.jpg** - File paths can be different for each call so feel free to customize covers

**-b 128** - Bit rate of the source audios, if you have higher quality ones, change this

**-t "Worm - Book 5"** - Display title of the final audiobook

**-o "Worm - Book 5.m4b"** - Output File name