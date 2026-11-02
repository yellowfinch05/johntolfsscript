# John to LFS SSH launcher

`ssh-john-lfs` opens an SSH session to John and then automatically connects
from John to the configured LFS machine using
`ssh lfs@`LFS-Machine-IP <machine-number>``.

## Usage

Make the script executable and run it:

```sh
chmod +x ssh-john-lfs
./ssh-john-lfs
```

The first run asks for the John username and LFS machine number. The number
is used in the command substitution `` `LFS-Machine-IP <number>` `` and the
values are saved locally for subsequent runs. Use `--redo` to replace them,
or `-h` to display all commands and options.

SSH keys must already be configured for both connections.
