# Firewall

Install and configure iptables firewall

- Allow ICMPs
- Default ACCEPT with Last Entry DROP (to prevent lockouts)

## System Firewall
`firewall_ports`:
General ipv4 and ipv6 rules for system

Default:
```
  - "ssh":
    port: 22
```

Example:
```
firewall_ports:
  - "Cosmetic Name":
    port: "123"
    protocol: "tcp"
    source: "192.168.0.0/24"
```
- `port`: Any valid destination port number)
- `protocol`: (tcp) indicate porotol: tcp or udp
- `source`: (omitted) Any value of an  IP or IP with CIDR

## Docker  Firewall

`firewall_docker_interface`: 

Define firewalled docker interface IE eth0, ens3. Value must be set to process `firewall_docker_ports`

`firewall_docker_ports`:

Rules for port forwarded by docker, manageing DOCKER-USER 

Default: `none set`

Example:
```
firewall_docker_interface: eth0
firewall_docker_ports:
  - "Cosmetic Name":
    port: "123"
    protocol: "tcp"
    source: "192.168.0.0/24"
```
- `port`: Any valid destination port number)
- `protocol`: (tcp) indicate porotol: tcp or udp
- `source`: (omitted) Any value of an  IP or IP with CIDR