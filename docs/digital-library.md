# Case study: Operating the Calibre backend for a community digital library

## Context and responsibility

I maintain the **Calibre backend** for a digital library accessed by a small community through **Calibre-Web**. Both applications run in Docker on a UGREEN NAS. Community members interact with the library through the web interface; I take responsibility for the underlying Calibre service and the infrastructure supporting it.

This distinction matters: the frontend makes resources accessible, but reliable access also depends on correctly configured backend services, storage, networking, and ongoing administration.

## Architecture and implementation

- **Calibre:** Backend library-management application and content server.
- **Calibre-Web:** Community-facing browser interface for accessing the collection.
- **Docker:** Containerized deployment and service configuration.
- **UGREEN NAS:** Host and persistent storage for the environment.
- **Linux and SSH:** Administrative access and troubleshooting.
- **Tailscale Serve:** A verified HTTPS access path for Calibre-Web within a private tailnet.

The applications have distinct service roles and port mappings. Getting them connected required diagnosing container-to-host port configuration, service reachability, and how the browser frontend relates to the Calibre backend.

## My operational responsibilities

**Backend administration:** I administer Calibre behind the community-facing Calibre-Web interface, including the service configuration needed for the library to function.

**Infrastructure maintenance:** I manage the Docker-based environment, persistent storage mappings, and supporting NAS services.

**Connectivity and troubleshooting:** I investigate access and connectivity problems across the application, container, host, and private-network layers.

**Resource access:** I maintain the technical foundation that allows authorized community members to use the library without having to administer the backend themselves.

## A concrete troubleshooting example

While configuring the library, I had to distinguish Calibre's content-server endpoint from the Calibre-Web frontend and reconcile their Docker port mappings. I verified connectivity to the Calibre services, then configured Tailscale Serve to provide an HTTPS route to Calibre-Web for authorized devices.

This work demonstrates a practical understanding of the difference between **a running container, a reachable application, and a usable service**.

## Outcome

The library is in use by a small community through Calibre-Web, and I continue to maintain the Calibre backend. The project demonstrates operational ownership of a real service, not just a sample deployment.

## Further documentation and development

- Publish sanitized configuration examples after reviewing them for secrets.
- Document the collection-management and metadata workflow once its specific steps are verified.
- Record and test backup and restoration procedures.
- Evaluate usability and accessibility for community members.
- Explore a physical-media scanning workflow for authorized materials.

The repository intentionally does not publish community membership, private endpoints, or the contents of the collection. It also does not claim that backup automation or formal service-level guarantees are already in place.
