# OpenVPN Server Auto Setup Script

## Features

- Full otomatik openvpn kurulumu 
- ovpn dosyası kurulum bittiğinde otomatik olarak oluşturulur.
- Optimizes `sysctl` settings for improved VPN performance

## Installation - Kurulum

Script'i indirin.

```bash
wget -O openvpn.sh https://get.vpnsetup.net/ovpn
```

Script'i başlatın.

```bash
sudo bash openvpn.sh --auto
```
NOT:
Sunucular için 1194 numaralı portu açamayı unutmayın.Aksi takdirde çalışmaycaktır.

<details>
<summary>
Terminal çıktısı şu şekilde olmalı
</summary>

**Note:** DEMO.

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>


**Option 2:** Interactive install using custom options.

```bash
sudo bash openvpn.sh
```

You can customize the following options: VPN server's DNS name, protocol (TCP/UDP) and port, DNS server for VPN clients and name of the first client.

For servers with an external firewall, open your selected TCP or UDP port for the VPN.

<details>
<summary>
Click here if you are unable to download.
</summary>

You may also use `curl` to download:

```bash
curl -fL -o openvpn.sh https://get.vpnsetup.net/ovpn
```

Then follow the instructions above to install.

Alternative setup URLs:

```bash
https://github.com/hwdsl2/openvpn-install/raw/master/openvpn-install.sh
https://gitlab.com/hwdsl2/openvpn-install/-/raw/master/openvpn-install.sh
```

If you are unable to download, open [openvpn-install.sh](openvpn-install.sh), then click the `Raw` button on the right. Press `Ctrl/Cmd+A` to select all, `Ctrl/Cmd+C` to copy, then paste into your favorite editor.
</details>
<details>
<summary>
Advanced: Auto install using custom options.
</summary>

Advanced users can auto install OpenVPN using custom options, by specifying command-line options when running the script. For more details, see the next section "view usage information for the OpenVPN script".

Alternatively, you may provide a Bash "here document" as input to the setup script. This method can also be used to provide input to manage users after install.

First, install OpenVPN interactively using custom options, and write down all your inputs to the script.

```bash
sudo bash openvpn.sh
```

If you need to remove OpenVPN, run the script again and select the appropriate option.

Next, create the custom install command using your inputs. Example:

```bash
sudo bash openvpn.sh <<ANSWERS
n
1
1194
2
client
y
ANSWERS
```

**Note:** The install options may change in future versions of the script.
</details>
<details>
<summary>
View usage information for the OpenVPN script.
</summary>

```
Usage: bash openvpn.sh [options]

Options:

  --addclient [client name]      add a new client
  --exportclient [client name]   export configuration for an existing client
  --listclients                  list the names of existing clients
  --revokeclient [client name]   revoke an existing client
  --uninstall                    remove OpenVPN and delete all configuration
  -y, --yes                      assume "yes" as answer to prompts when revoking a client or removing OpenVPN
  -h, --help                     show this help message and exit

Install options (optional):

  --auto                         auto install OpenVPN using default or custom options
  --listenaddr [IPv4 address]    IPv4 address that OpenVPN should listen on for requests
  --serveraddr [DNS name or IP]  server address, must be a fully qualified domain name (FQDN) or an IPv4 address
  --proto [TCP or UDP]           protocol for OpenVPN (TCP or UDP, default: UDP)
  --port [number]                port for OpenVPN (1-65535, default: 1194)
  --clientname [client name]     name for the first OpenVPN client (default: client)
  --dns1 [DNS server IP]         primary DNS server for clients (default: Google Public DNS)
  --dns2 [DNS server IP]         secondary DNS server for clients

To customize options, you may also run this script without arguments.
```
</details>

## Next steps

After setup, you can run the script again to manage users or uninstall OpenVPN.

Get your computer or device to use the VPN. Please refer to:

**[Configure OpenVPN Clients](docs/clients.md)**

**Read [:book: VPN book](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J) to access [extra content](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J).**

Enjoy your very own VPN! :sparkles::tada::rocket::sparkles:

## Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/openvpn-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

<details>
<summary>
List of enhancements over Nyr/openvpn-install.
</summary>

- Improved compatibility with Setup IPsec VPN
- Improved script reliability, user input and output
- Supports auto install using default or custom options
- Supports using a DNS name as server address
- Added support for openSUSE Linux
- Added support for Amazon Linux 2
- Supports exporting configuration for an existing VPN client
- Supports listing existing VPN clients
- Supports custom DNS server(s) for VPN clients
- Supports command-line options for managing VPN clients
- Optimizes `sysctl` settings for improved VPN performance
- Improved creation of client config files when using `sudo`

...and more!
</details>

## License

MIT
