
# Arshan's SSH Cheat Sheet

## Debugging
Run `ssh` with -v.

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
