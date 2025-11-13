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
