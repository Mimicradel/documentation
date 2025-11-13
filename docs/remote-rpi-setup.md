# How to Setup a Raspberry Pi for Remote Access

## Prerequisites

1. A raspberry pi (rpi)
2. Network admin or authorization to assign static ip addresses

## Network Setup

1. Assign any ip address to the rpi but be sure to keep a record of it. As an example in this doc we will use `<RPI_ADDR>`.
2. Ensure that this network is public facing so that `<RPI_ADDR>` can be pinged from the internet.
3. Send an email or write to IT services. Here is an example:

```txt
Hello ITS Team,

We require a static IPv4 address for a new machine located at <MACHINE_LOCATION>.

Here are the details:

Machine Name: <NAME_OF_MACHINE>
Location: <MACHINE_LOCATION>
MAC Address: <RPI_MAC_ADDR>
Please let us know if you need any additional information from our side.

Thank you,

<YOUR_NAME>
```

> [!NOTE]
> You will need to know the rpi's MAC Address in order to assign it a static ip.
> If using `wifi` you can do this with
>
> ```bash
> ip addr show dev wlan0 | grep -i ether
> ```
>
> or if using `ethernet`
>
> ```bash
> ip addr show dev eth0 | grep -i ether
> ```
>
> Ethernet is preferred.
>
> The MAC Address should look something like `01:23:45:67:89:ab:cd`.

> [!NOTE]
> If you would like to use a home modem you will need to utilize `Port Forwarding`
> as you will not be able to assign static ips outside of your modem.

## SSH Keys

On your local machine. (The one you will be using to remotely connect to the pi) check
if you already have an ssh key at `~/.ssh/id_ed25519` you can either use this one or generate a new key.
I always recommend generating a new key per each new device.

To generate a new key use the following command:

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_<SSH_KEY_ID>
```

Where `<SSH_KEY_ID>` is a name you get to specify to identify what the key will be used for.
Since we have the name of the RPi I would call it `~/.ssh/id_ed25519_<NAME_OF_MACHINE>` or `~/.ssh/id_ed25519_rpi`

Then you will need to copy the contents of the public key. To view the contents of the file in the terminal use:

```bash
cat ~/.ssh/id_ed25519_<SSH_KEY_ID>.pub
```

> [!NOTE]
> Notice the `.pub` at the end of the key. This is important as if you `cat` the `~/.ssh/id_ed25519_<NAME_OF_MACHINE>` you will be showing others your private key. Always keep this safe and do not let it be leaked from your personal machine.

##
