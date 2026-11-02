# John to LFS SSH launcher

This uses the separate [`ssh-setup`](https://github.com/yellowfinch05/sshscript)
program to set up SSH keys, so you do not have to create or copy keys by hand.

These instructions work on macOS and Linux. On Windows, use Windows
Subsystem for Linux (WSL) or Git Bash, then run the same commands there.

### 1. Download both programs

Run these commands on your own computer:

```sh
mkdir -p ~/bin
curl -L https://raw.githubusercontent.com/yellowfinch05/sshscript/main/ssh-setup \
  -o ~/bin/ssh-setup
curl -L https://raw.githubusercontent.com/yellowfinch05/johntolfsscript/main/ssh-john-lfs \
  -o ~/bin/ssh-john-lfs
chmod +x ~/bin/ssh-setup ~/bin/ssh-john-lfs
```

### 2. Set up SSH to John

Run this on your own computer:

```sh
~/bin/ssh-setup YOUR_USERNAME@john.cedarville.edu
```

Follow the prompts. This installs your SSH key on John.

### 3. Copy `ssh-setup` to John

Still on your own computer, run:

```sh
scp ~/bin/ssh-setup YOUR_USERNAME@john.cedarville.edu:~/
```

### 4. Set up SSH to LFS

Log in to John:

```sh
ssh YOUR_USERNAME@john.cedarville.edu
```

On John, make `ssh-setup` executable:

```sh
chmod +x ~/ssh-setup
```

Find your LFS machine's address:

```sh
LFS-Machine-IP MACHINE_NUMBER
```

Use the address shown by that command with `ssh-setup`:

```sh
~/ssh-setup lfs@LFS_ADDRESS
```

Follow the prompts. This installs John's SSH key on LFS.

### 5. Connect all the way through

Leave John and return to your own computer:

```sh
exit
```

Run the local copy of the launcher:

```sh
~/bin/ssh-john-lfs
```

Enter your John username and machine number when asked. The launcher then
connects to John and from John to LFS.

The launcher remembers those answers. To enter them again, use:

```sh
~/bin/ssh-john-lfs --redo
```

now you can simply run ssh-john-lfs and get all the way to the lfs machine with no passwords and no remembering commands!
