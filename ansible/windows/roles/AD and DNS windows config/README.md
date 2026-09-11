# Windows Server AD/DNS Playbook

These Ansible playbooks configure a Windows Server as an Active Directory domain
controller with DNS, then create domain users, a security group, group
memberships, and a text file for Charlie Brown.

## What It Does

The first play:

- Installs the AD DS and DNS Windows features.
- Creates the `peanuts.local` AD forest with the `PEANUTS` NetBIOS name.
- Reboots the server when domain setup requires it.
- Configures the primary DNS client server.
- Ensures the AD-integrated forward zone exists.
- Creates the `1.168.192.in-addr.arpa` reverse lookup zone.

The second play:

- Creates users Charlie Brown, Snoopy Brown, and Lucy Van Pelt.
- Creates the `Peanuts` global group.
- Adds Snoopy to `Domain Admins`.
- Adds all three users to the `Peanuts` group.
- Creates `C:\Users\charlie.brown\charlie-brown.txt`.

## Before Running

Update these values in `bennett-win-ad-dns.yml` for the target environment:

- `primary_dns_server`: replace `127.0.0.1` with the server's intended static DNS address.
- `reverse_zone_netblock`: change `1.168.192.in-addr.arpa` to match the server's network.
- `safe_mode_password`: for actual competition, change to a challenging password. The same can be said for the user passwords as well. 
- `hosts: windows`: confirm that the inventory group contains the intended Windows Server.

The server should have a static IP address before it is promoted to a domain
controller. The DNS zone is normally created automatically by
`ansible.windows.win_domain`; the explicit zone task is retained to demonstrate
 DNS configuration.

