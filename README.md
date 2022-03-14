# trial-run

Executes a specified command in its dry-run mode, interactively prompts for
confirmation, and re-executes it for real.

I got tired of manually executing commands with `--dry-run` options and then
manipulating my shell's command history in potentially error-prone ways to
re-execute the command, so I wasted more time writing a script to do it for
me.  (Yes, I am aware that most POSIX shells would allow me to enter
`^--dry-run ^` to perform command substitution, but that's awkward to type
and wouldn't work well for interactive scripts.)


## Installation

`trial-run` depends on submodules, so `--recurse-submodules` is necessary when
using `git clone`:

```shell
git clone --recurse-submodules https://github.com/jamesderlin/trial-run.git
```

Setting `git config submodule.recurse true` is also recommended so that
submodules are automatically and appropriately updated when the parent
repository is updated.


## Examples

* Invoking `trial-run rsync -aC --delete SOURCE DESTINATION` will execute:
    ```shell
    rsync --dry-run -aC --delete SOURCE DESTINATION
    rsync -aC --delete SOURCE DESTINATION
    ```

* Invoking `trial-run --command="MAIN_COMMAND --OPTION SUBCOMMAND" -- --SUBOPTION`
  will execute:

    ```shell
    MAIN_COMMAND --OPTION SUBCOMMAND --dry-run --SUBOPTION
    MAIN_COMMAND --OPTION SUBCOMMAND --SUBOPTION
    ```

* Invoking `trial-run --command="p4 revert" --option=-n` will execute:

    ```shell
    p4 revert -n
    p4 revert
    ```

---

Copyright © 2022 James D. Lin.
