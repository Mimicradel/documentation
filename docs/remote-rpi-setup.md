# How to Set Up a Raspberry Pi for Remote Access

## Prerequisites

1. A Raspberry Pi (RPi)
2. Network administrator access or authorization to assign static IP addresses

## Network Setup

1. Assign an IP address to the RPi and record it for future reference. For this guide, we'll use `<RPI_ADDR>` as a placeholder.
2. Ensure the network is publicly accessible so that `<RPI_ADDR>` can be pinged from the internet.
3. Contact your IT services department to request a static IP address. Here's an example email template:

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
> You will need the RPi's MAC address to assign it a static IP.
>
> For **WiFi**, use:
>
> ```bash
> ip addr show dev wlan0 | grep -i ether
> ```
>
> For **Ethernet** (preferred):
>
> ```bash
> ip addr show dev eth0 | grep -i ether
> ```
>
> The MAC address should look something like `01:23:45:67:89:ab:cd`.

> [!NOTE]
> If you're using a home modem, you'll need to configure **port forwarding** since you won't be able to assign static IP addresses outside of your local network.

Copy the contents of the provided public key to the RPi at the following path: `/root/.ssh/authorized_keys`.
