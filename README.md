# bash-trash
bash functions for simple CLI trash on \*NIX systems

## about

`bash-trash` is a script that allows you to manage a trash directory
from the command line. Functions are provided for moving files to the
trash, restoring them from the trash, and emptying the trash. It is 
simple, lightweight, and fairly configurable.

## usage

`bash-trash` is controlled through three functions:

`trash [files]` will move each file specified in the argument list to the
trash directory.

`untrash [files]` will restore each file specified in the argument list
back to it's original location. `untrash` has a completion function that
will complete for all files in the trash. Aside from saving time typing,
if tab is pressed with no text in the current argument, bash will list
all the items in the trash for you.

`empty-trash [force?]` will empty the trash after prompting the user for
confirmation. If `--force` is passed as the first argument, the trash
will be emptied without prompting for confirmation.

## installation

The best way to install `bash-trash` is to source it into your `~/.bashrc`.
Save the file somewhere, and take note of the path. Then either add the
following line to your `~/.bashrc`
```
    source YOUR/PATH/HERE/bash-trash
```
or run the following command to append it to your `~/.bashrc`.
```
    echo "source YOUR/PATH/HERE/bash-trash" >> ~/.bashrc
```
Now you just need to open a new terminal or run
```
    source ~/.bashrc
```
The program should now be installed!

## configuration

The following options are located at the top of the script and
can be used as follows:

`__BT_TRASH_DIR` -- sets the location of the trash directory. This should be
expressed either as an absolute path or one relative to `$HOME`.

`__BT_LOG_LEVEL` -- sets the verbosity of logging. Valid levels are `quiet` 
(only log errors), `normal` (log general information about actions), and 
`verbose` (log detailed information about actions).

`__BT_COLORS` -- sets whether or not colored output will be used. Valid 
settings are `yes` and `no`.

`__BT_RM` -- the command that is used when emptying the trash. Defaults to 
`rm`, but will work just fine with `srm` or similar commands.

`__BT_RM_V` -- sets the argument that will be added to `__BT_RM` when
verbose output is enabled. This will probably be `-v` or `--verbose`, or
empty if your remove command does not support verbose output.

You will either need to `source` the file or open a new terminal for
changes to these values to take effect.

`bash-trash` will try to detect and warn you if a value is configured
incorrectly, as this will probably cause problems!
