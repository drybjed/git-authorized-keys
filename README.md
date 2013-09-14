# git-authorized-keys

This script reads a formatted list of git repositories from
`~/.ssh/git_authorized_keys`, clones them to a temporary directory and copies
contents of specified file into `~/.ssh/authorized_keys` (with backup copy of
previous version).

## Options

    -c, --checksum          check file checksums, return the result, exit
    -e, --edit              open text editor with list of repositories
    -f, --force             force regeneration of ~/.ssh/authorized_keys
    -g, --list-git          print list of git clone commands and exit
    -h, --help, --usage     display this help message and exit
    -l, --list              print list of git repositories and exit
    -q, --quiet             be quiet, ignore errors
    -t, --test              check if list of repositories exists, if not then
                            exit without raising error
    --version               display version and exit

When run without options, update-authorized-keys looks for changes in
`~/.ssh/authorized_keys` or `~/.ssh/git_authorized_keys` and recreates the former
if necessary.

## Key list format:

    <git repository> <dir/filename> [branch]

  - git repository: any URI accepted by `git clone`
  - dir/filename: path to file with ssh public keys relative to repository
  - branch: optional branch/tag to checkout, default: master

Empty lines and lines beginning with '#' are ignored.

To use as different user: `sudo -H -u <username> update-authorized-keys`

## Author, copyright

Copyright (C) 2013 Maciej Delmanowski <drybjed@gmail.com>

License GPLv2+: GNU GPL version 2 or later (http://gnu.org/licenses/gpl.html).
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

