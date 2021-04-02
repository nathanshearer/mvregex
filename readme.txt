Description:
  Move or rename files that match the given regular expression.

Usage:
  mvregex [options] SOURCE_REGEX DESTINATION_REGEX FILE...
  mvregex [options] --transliterate windows FILE...

Options:
  -f, --force
    Do not prompt before overwriting files. Disabled by default, but writable
    files are still overwritten by default.
    Without this option, overwrite files that are writable, and only prompt for
    files that are not writable.
    With this option, overwrite all files without prompting.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
    See -i or -n to disable overwriting existing files.
  -h, --help
    Display this help message and exit.
  -i, --interactive
    Prompt before overwriting files. Disabled by default.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
  --merge
    Merge files into existing destination folders. Disabled by default.
  -n, --no-clobber
    Do not overwrite files. Disabled by default.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
  --no-merge
    Disable --merge.
  --no-recursive
    Disable --recursive.
  -p, --pretend
    Perform a simulation only. No files are actually moved ore renamed.
    This option will increase the verbosity level to 2.
  -r, --recursive
    Process files in directories recursively. Disabled by default.
  --transliterate windows
    Convert strings into a format supported by windows:
      double quote '"' -> two single quotes "''"
      colon ':' -> ratio '∶' U+2236 (UTF-8 0xE288B6)
      asterisk '*' -> heavy asterisk '✱' U+2731 (UTF-8 0xE29CB1)
      backslash '\' -> underscore '_'
      question mark '?' -> underscore '_'
      pipe '|' -> underscore '_'
      less than '<' -> underscore '_'
      greater than '>' -> underscore '_'
      remove trailing spaces (ASCII 0x20)
      remove trailing spaces (cygwin UTF-8 0xEF80A8)
      remove trailing period (ASCII 0x2E)
      remove trailing period (cygwin UTF-8 0xEF80A9)
  -v
    Increase the verbosity level by 1.
  --verbose #
    Use more or less verbose output. Valid values are:
      0  Default. No output.
      1  Show only renamed files.
      2  Show subfiles that are moved during a folder merge.
      3  Show all files.

Examples:
  Convert "JPG" extension to "jpg"
    mvregex -p -v '[jJ][pP][eE]?[gG]$' 'jpg' *
  Convert "###" to "S#E##"
    mvregex -p -v '^([0-9])([0-9][0-9])' 'S\1E\2' *.mkv
  Convert upper case to lower case
    mvregex -p -v '(.*)' '\L\1' *
  Convert lower case to upper case
    mvregex -p -v '(.*)' '\U\1' *
  Remove trailing spaces on all files recursively
    mvregex -p -r '^(.*) +$' '\1' *
  Remove trailing spaces (cygwin encoded byte sequence EF80A8) on all files recursively
    mvregex -p -r '^(.*)\xEF\x80\xA8$' '\1' *
  Remove trailing . on all files recursively
    mvregex -p -r '^(.*)\.+$' '\1' *
  Remove trailing . (cygwin encoded byte sequence EF80A9) on all files recursively
    mvregex -p -r '^(.*)\xEF\x80\xA9$' '\1' *

Version:
  mvregex 2.4.0.0
  Copyright (C) 2007 Nathan Shearer
  Licensed under GNU General Public License 2.0
