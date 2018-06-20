# exif-date-changer
Simple and intuitive bash script that uses exiftool to modify exif dates. You would want to use it typically when you took some pictures and later on you realized that you hadn't configured the clock of your camera properly.

# Usage
```
$ exif-date-change -h

exif-date-change [OPTION]... [IMAGE]...

Shifts the Exif date from a list of images.
Uses the exiftool to achive that.

Options:
  -h, --help             Shows this help message
  -d, --dry-run          Shows the time changes for all provided IMAGES without
                          applying any changes. Use this for testing.

  -r R_EXIF_TIME_TAG, --reference-exif-tag R_EXIF_TIME_TAG
                         The R_EXIF_TIME_TAG is a valid time tag that can be extracted
                          from the photograph with the exiftool. The R_EXIF_TIME_TAG
                          is used as a reference when adding/subtracting the STIME.
                          Tags that will work (unless they have been stripped) are:
                             DateTimeOriginal, CreateDate, ModifyDate,
                             FileAccessDate, FileModifyDate, FileInodeChangeDate

                          Default value: DateTimeOriginal

  -s STIME, --shift-time STIME
                         The STIME defines the time shift that will be applied to the
                          IMAGES. The format is human readable and must be parsable
                          by the date command. Some examples:
                           1. The leading minus (-) in the following example indicates
                              that the time described in the human readable format will
                              be subtracted from the DateTimeOriginal Exif info.
                               "-1 year -2 months -13 days -1 hour +15 minutes +3 seconds"
                           2. The following example will add 383 days and subtract 3846 seconds.
                               "+383 days -3846 seconds"

  -m, --update-system-modify-time
                         If the -m flag is used, the file system modify time will also
                          be updated.
  -f, --force-delete-backups
                         Exiftool takes a backup of an image whenever a modification is
                          happening. At the end of the execution of this script you are
                          asked if you want to keep these backed up images or delete them.
                          When using the -f flag, the script will force delete the backups
                          at the end.
```
