# Architecture and trust boundaries

This is a **conceptual** overview of the current home lab. It does not imply that services are publicly accessible.

```mermaid
flowchart LR
    Clients[Authorized devices] -->|Tailscale private network| Host[UGREEN NAS]
    Host -->|Docker| CW[Calibre-Web]
    Host -->|Docker| C[Calibre]
    Host -->|Docker| J[Jellyfin]
    Host --> Vol[(Persistent storage)]
    CW --> Vol
    C --> Vol
    J --> Vol
    Clients -->|HTTPS via Tailscale Serve| CW
```

## Boundaries

- **Clients:** Only devices authorized to the private tailnet are in scope.
- **Host:** The NAS runs services and stores application data.
- **Containers:** Applications have separate runtime configurations and persistent storage mappings.
- **HTTPS endpoint:** Tailscale Serve proxies Calibre-Web for tailnet access; this is not a public internet endpoint.

## To verify before publishing more detail

Confirm container-to-host port mappings, storage paths, backup strategy, and access-control policies before adding sanitized configurations. Do not publish private addresses, credentials, device identifiers, or personal collection contents.