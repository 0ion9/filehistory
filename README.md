# filehistory
Basic automated file-history-tracker for *nix

Single shell script, invoked as 'filehistory [filenames]'. Designed for use making WIP animations of artwork.

When you want to stop tracking the files for the moment, simply terminate it by pressing `Ctrl+C`.


*Requires*:

* inotifywait ('inotify-tools' package)
* find
* zenity

*Optional*:

* notify-send (`libnotify` package)

### In detail:

Watches files using `inotifywait`.

* When a new version is saved, it is assigned a revision number
  and stored in `FILENAME.hist/REVISION-MD5HASH.EXT` (example: revision 1 of foo.png might be stored as
  `000001-d6c3121c4c62524a23c66649be247df3.png`)
* The user is prompted using `zenity` to describe
  their changes, and this is logged to `FILENAME.hist/log.txt`.
* If the user enters an empty message or cancels, the revision is not stored in history.

In the case of images, this system means it is easy to browse through your history visually with an
ordinary image viewer.

You can also edit history via normal filesystem operations.
