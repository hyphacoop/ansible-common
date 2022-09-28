# firewall

Install and configure iptables firewall.

- Allow ICMPs
- Default ACCEPT with Last Entry DROP (to prevent lockouts)

## System Firewall

`firewall_ipv6`: (true) Open ports on IPv6, not just IPv4

`firewall_ports`:
General IPv4 and IPv6 rules for system:

Default:
```yaml
  - "ssh":
    port: 22
```

Example:
```yaml
firewall_ports:
  - "Cosmetic Name":
    port: "123"
    protocol: "tcp"
    source: "192.168.0.0/24"
```
- `port`: Any valid destination port number
- `protocol`: indicate protocol: tcp or udp, tcp by default
- `source`: valid source IP
  - Can be any value of an IP or IP with CIDR
  - Omitting this means all IPs are allowed

## Docker Firewall

`firewall_docker_interface`: 

Define firewalled docker interface (ex: eth0, ens3). Value must be set to process `firewall_docker_ports`.

`firewall_docker_ports`:

Rules for port forwarded by docker, managing DOCKER-USER chain.

Default: `none set`

Example:
```yaml
firewall_docker_interface: eth0
firewall_docker_ports:
  - "Cosmetic Name":
    port: "123"
    protocol: "tcp"
    source: "192.168.0.0/24"
```
- `port`: Any valid destination port number
- `protocol`: indicate protocol: tcp or udp, tcp by default
- `source`: valid source IP
  - Can be any value of an IP or IP with CIDR
  - Omitting this means all IPs are allowed