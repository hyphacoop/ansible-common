# blackbox_exporter_http_addnode

Adds HTTP/HTTPS probe targets for blackbox_exporter.

The role runs on the monitor server. For every host in the `http` inventory group,
it writes one file_sd target file, `/opt/prometheus/blackbox-http.d/<inventory_hostname>.yml`.
Prometheus picks up new files automatically, so no reload is needed.

## Variables

Set these per host, on hosts in the `http` group:

- `inventory_hostname`: the host name. Used as the target file name and as the `host` label.
- `blackbox_targets` (required): a list of URLs to probe. Each entry has:
  - `url` (required): the full URL, e.g. `https://api.example.com/readyz`
  - `module` (required): the blackbox module to use. Must exist in `blackbox.yml`.
  - `labels` (optional): extra Prometheus labels for this URL only.
- `blackbox_labels` (optional): labels applied to all of the host's URLs.
  If the same label is set on a target, the target's value wins.

Reserved label names (don't set these yourself): `module`, `host`, `instance`, `job`.

## Available modules

| Module                 | Checks                                                  |
|------------------------|---------------------------------------------------------|
| `http_2xx`             | Plain HTTP, any 2xx                                     |
| `https_2xx`            | HTTPS, any 2xx, valid cert                              |
| `https_body_ok`        | HTTPS, body is exactly `ok`                             |
| `https_body_static`    | HTTPS, body is exactly `static-string-from-api`         |
| `https_json_status_ok` | HTTPS, JSON `status` and every `checks.*.status` is `ok` |

The `https_*` modules fail on plain `http://` URLs.

## Example

```yaml
all:
  children:
    monitor:
      hosts:
        monitor.prod.hypha.coop:
    http:
      hosts:
        api.example.com:
          blackbox_labels: { service: api }
          blackbox_targets:
            - url: "https://api.example.com/livez"
              module: https_body_ok
              labels: { check: liveness }
            - url: "https://api.example.com/readyz"
              module: https_json_status_ok
              labels: { check: readiness }
```
