# Introduction

Simple shell script to read screens off Rigol DS1xx4Z and similar scopes.
Originally Al Williams al.williams@awce.com Forked By Mark Finn to fix a trailing trim issue.

This uses the network connection (but could probably use /dev/usbtmc) and
you can change the scope name/port # at the top of the script

Just provide one or more file names to capture. You can use jpg, png, pdf
or many other extensions to get the file type you want. Note: You do need
netcat (nc) and ImageMagick installed, but most Linux boxes will have these
anyway.

# Usage

  scopesnap [-B] [-d delay][-a template] [-i address] [-p port] [-r count] [-R] file [file ...]
  Where file is a file name ending with the format you want
  (e.g., jpg or png or pdf)
  Options:
  -b or -B - The image will not be opened after capture
  -d - Delay (in seconds) after each capture
  -a - Auto generate file names from template
  -r - Repeat for count captures (assumes one file name or -a)
  -R - Repeat forever (assumes one file name or -a)
  -i - Name or IP address of scope (default: rigollan.local)
  -p - Port number (default: 5555) 

# Examples:
Save one screen shot:
     scopesnap pulse.png


Save four shots 30 seconds apart:
     scopesnap -d 30 start.png second.png third.png last.png


Save four shots 10 seconds apart to pulse1.png, pulse2.png, pulse3.png, etc.
     scopesnap -d 30 -a pulse1.png -r 4


NOTE: pulse1.png is a template. The program will find the highest numbered
file (e.g., pulse99.png) that already exists and add one to that.

Save a PDF file every 10 minutes overwriting the old one
     scopesnap -d 600 -R capture.pdf





