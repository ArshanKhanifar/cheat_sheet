# Arshan's SSH Cheat Sheet

## Debugging

Run `ssh` with -v.

## Using SSH-Agent

This is for preventing password checking.
From [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent):

1. Add this to the `.arshrc`

```
eval `ssh-agent`
```

2. Add the following to `~/.ssh/config`

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

This will keep stop asking the password.

## Key-based Authentication

On the client machine do:

```
ssh-keygen -t rsa -b 2048
```

On the remote machine copy the contents of id_rsa.pub to
`~/.ssh/authorized_keys`.

```
echo "<contents of your public key>" >> ~/.ssh/authorized_keys
```

To enable key-based authentication run `ssh` with a `-i` option

```
ssh -i ~/.ssh/<your_private_key> <your-remote-machine>
```

### Copying Shortcut

There's this command: `ssh-copy-id` that makes it easier:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote
```

## Fixed Issues

#### Permissions can be too open!

Once I had the permissions on the `authorized_keys` file on the remote machine as:

```
-rw-rw-rw- 1 username users 590 May 22 11:29 authorized_keys
```

Turns out permissions can be too open! So I changed it to be used only by the user:

```
chmod -R 700 .ssh/
```

Now the permissions are as follows

```
-rwx------  1 akhanifa users 594 May 24 08:20 authorized_keys
```

This fixed my issue.
