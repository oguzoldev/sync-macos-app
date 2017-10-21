# Sync macOS Applications Script

You can use it to backup applications on your computer except for Mac applications.

```bash
#!/bin/bash
SOURCE=/Applications/
DESTINATION=/Volumes/ExternalHDD/Applications/
EXCLUDE='/tmp/exclude-list.txt'

cat > $EXCLUDE <<_EOF_
.DS_STORE
App Store.app
Automator.app
Calculator.app
Calendar.app
Chess.app
Contacts.app
Dashboard.app
Dictionary.app
DVD Player.app
FaceTime.app
Font Book.app
iBooks.app
Image Capture.app
iTunes.app
Launchpad.app
Mail.app
Maps.app
Messages.app
Mission Control.app
Notes.app
Photo Booth.app
Photos.app
Preview.app
QuickTime Player.app
Reminders.app
Safari.app
Siri.app
Stickies.app
System Preferences.app
TextEdit.app
Time Machine.app
Utilities
_EOF_

rsync --archive --extended-attributes --delete --progress --human-readable --exclude-from $EXCLUDE $SOURCE $DESTINATION

rm $EXCLUDE
```

# Basic Usage

Open your terminal and run file,

```bash
$ sync-macos-app.sh
```

# Note

Please don't forget to change the "DESTINATION" field according to your own computer.