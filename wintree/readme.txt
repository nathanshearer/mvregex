Description:
  Recursively copies a directory into windows friendly filenames.

Usage:
  wintree [options] <linux_dir> <windows_dir>

Options:
  -h, --help
    Display this help message and exit.
  -l, --link
    Hard link files instead of creating symbolic links.
  -p, --pretend
    Do not make any changes. Output files that are renamed in the destination.
  -s, --symbolic-link
    Make symbolic links instead of hard links. Enabled by default.

Examples:
  wintree -p /mnt/storage /mnt/storage.wintree
  wintree -p -l /mnt/storage /mnt/storage.wintree

Version:
  wintree 1.1.0.0
  Copyright (C) 2007 Nathan Shearer
  Licensed under GNU General Public License 2.0
