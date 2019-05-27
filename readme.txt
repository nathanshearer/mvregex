Description:
  Move files that match the given regular expression.

Usage:
  mvregex [options] SOURCE_REGEX DESTINATION_REGEX FILE...

Options:
  -f, --force
    Do not prompt before overwriting files. Disabled by default, but writable
    files are still overwritten by default.
    Without this option, mv will overwrite files that are writable, and only
    prompt for files that are not writable.
    With this option, mv will overwrite all files without prompting.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
    See -i or -n to disable overwriting existing files.
  -h, --help
    Display this help message and exit.
  -i, --interactive
    Prompt before overwriting files. Disabled by default.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
  -n, --no-clobber
    Do not overwrite files. Disabled by default.
    If you specify more than one of -f, -i, -n, only the final one takes effect.
  -p, --pretend
    Performs a dry run and prints out what files would be moved. No files are
    actually moved. This option will set the verbosity level to 1.
  -v
    Show only the files that are moved. The same as --verbose 1.
  --verbose #
    Use more or less verbose output. Valid values are from 0 to 2 inclusive:
      0  Default. No output
      1  Show only the files that are moved
      2  Show all files that are processed

Examples:
  mvregex -p '[jJ][pP][eE]?[gG]$' 'jpg' *
  mvregex -p '^([0-9])([0-9][0-9])' 'S\1E\2' *.mkv

Version:
  mvregex 1.0.0.0
  Copyright (C) 2007 Nathan Shearer
  Licensed under GNU General Public License 2.0