# User Setup

## SSH Keys

On your local machine (the one you'll use to remotely connect to the RPi), check if you already have an SSH key at `~/.ssh/id_ed25519`. You can use this existing key or generate a new one. It's recommended to generate a new key for each device.

To generate a new key, use the following command:

```bash
ssh-keygen-ted25519-f~/.ssh/id_ed25519_<SSH_KEY_ID>
```

Replace `<SSH_KEY_ID>` with a descriptive name to identify what the key will be used for. For example, use `~/.ssh/id_ed25519_<NAME_OF_MACHINE>` or `~/.ssh/id_ed25519_rpi`.

To view the contents of your public key in the terminal:

```bash
cat~/.ssh/id_ed25519_<SSH_KEY_ID>.pub
```

> [!NOTE]
> Notice the `.pub` extension, which indicates the public key file. If you accidentally run `cat ~/.ssh/id_ed25519_<SSH_KEY_ID>` without `.pub`, you'll expose your private key. Always keep your private key secure and never share it.

Copy the contents of `cat ~/.ssh/id_ed25519_<SSH_KEY_ID>.pub` to the RPi at the following path: `/root/.ssh/authorized_keys`.

## SSH Config

To easily connect to the Raspberry Pi you should edit your ssh config file.
You can do this through `nvim`, `vim`, `nano`, or if you prefer VS Code `code ~/.ssh/config`

Append the following to `~/.ssh/config`:

```bash
Host <NAME_OF_MACHINE>
  HostName <RPI_ADDR>
  User root
  Port <RPI_SSH_PORT> # default port is 22 (if not configured in /etc/ssh/sshd_config)
  IdentityFile ~/.ssh/id_ed25519_<SSH_KEY_ID>
  AddKeysToAgent yes # This will add `~/.ssh/id_ed25519_<SSH_KEY_ID>` to your ssh-agent
  ForwardX11 yes   # This allows for X11 to be forwarded to your machine for VNC connections.
  ForwardAgent yes # This gives the remote machine access to your ssh-agent (So your private keys aren't leaked.)
```

Be sure to replace all `<ENV_VAR>` with their correct values, and all comments (columns after #) can be omitted.
