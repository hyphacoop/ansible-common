# setup

Generic setup tasks to prep server for use.

- `setup_upgrade`: (true) upgrade the system packages
- `setup_basic`: (true) Install additional useful debugging tools like `curl` and `htop` and `mtr`
- `setup_build`: (false) Install build essentials and git
- `setup_disable_predictable_network`: (false) Disable predictive network interface naming
- `setup_tcp_timestamps`: (true) Disable TCP timestamps, see [here](https://raxis.com/blog/2018/06/04/goodies-for-hoodies-tcp-timestamps/)
- `setup_timezone`: (undefined) sets time zone, for example: `America/Toronto`
