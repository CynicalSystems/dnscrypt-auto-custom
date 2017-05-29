dnscrypt-auto-custom
====================

A customized script for installing and automatically configuring DNSCrypt on Debian Linux-based systems.

## This is a customized script specific for our deployments. Free software, no warranties, etc, etc.
## If you don't know exactly what you are doing please use the original repo located at: https://github.com/simonclausen/dnscrypt-autoinstall

# Description

This script will automatically and securely set up DNSCrypt as a background service that runs at system startup using [DNSCrypt-proxy](https://github.com/jedisct1/dnscrypt-proxy/), the [libsodium](https://github.com/jedisct1/libsodium) cryptography library, and the DNSCrypt service provider of your choice. The script also will set up dnsmasq as a cache for dnscrypt, and all outgoing port 53 traffic will be force-redirected to it with iptables DNAT.

The script supports Debian-based (Debian, Ubuntu, Linux Mint) distributions. The configuration file is pre-configured with resolvers and keys that we most commonly use. Fork this repo and make changes approrpiate for your environment before deploying. A list of resolvers can be found here: https://github.com/jedisct1/dnscrypt-proxy/blob/master/dnscrypt-resolvers.csv

| Note | Scripts with sysvinit support were moved to the "legacy" branch (CentOS 6, Debian 7, Ubuntu < 16.04) |
| --- | --- |

wget https://raw.githubusercontent.com/CynicalSystems/dnscrypt-auto-custom/master/dnscrypt-auto-custom.sha1

wget https://raw.githubusercontent.com/CynicalSystems/dnscrypt-auto-custom/master/dnscrypt-auto-custom

sha1sum -c dnscrypt-auto-custom.sha1; if [[ $? -eq 1 ]]; then echo "Doanload is corrupt!"; else

chmod +x dnscrypt-auto-custom

su -c ./dnscrypt-auto-custom

fi

## Troubleshooting

If the install fails at a particular stage and the script mentions DNSCrypt is already configured, use the `forcedel` argument to force an uninstallation:

./dnscrypt-auto-custom forcedel
