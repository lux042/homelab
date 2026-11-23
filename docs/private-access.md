# Case study: Private HTTPS access

## Problem

I wanted to reach a self-hosted digital library from trusted devices without exposing the service directly to the public internet.

## Approach

I installed Tailscale on my NAS and client devices, verified the NAS's Tailscale container was using host networking, and used the Tailscale command-line interface to configure **Tailscale Serve** as an HTTPS reverse proxy for the local Calibre-Web service.

## Engineering lessons

- Private network connectivity and application-level service availability are separate concerns.
- Container network mode affects which local addresses and ports can be reached.
- HTTPS termination and proxy routing should be understood as distinct parts of the access path.
- CLI diagnostics, permission checks, and service verification are essential to troubleshooting.

## Outcome

Calibre-Web became available at a tailnet-only HTTPS endpoint to authorized devices. No private hostname or IP address is published here.

## Next steps

Document repeatable access tests, review authentication and access controls, and record a tested recovery procedure.