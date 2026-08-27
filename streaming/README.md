# Video Streaming

This guide explains how to access the Bosch Eyes Camera live stream.

## Overview

The camera provides local live streaming using RTSP over HTTPS/TLS.

- `RTSP+HTPS` on port `443`
- `RTSPS` on port `9554`

Both flows are TLS-protected and require authentication with a local camera user.

## Prerequisites

Before connecting to the stream, make sure you have:

- Camera IP address or local hostname (`<camera_host>`)
- Local camera user name (`<username>`)
- Local camera password (`<password>`)


## Stream URL Format

Use this format for the stream URL:

```text
rtsps://<username>:<password>@<camera_host>:9554/rtsp_tunnel?line=1&inst=1&enableaudio=1
```

Parameter notes:

- `inst=1`: High-resolution stream
- `inst=2`: Low-resolution stream
- `inst=3`: Preview stream with a 1 Hz refresh rate
- `enableaudio=1`: Audio enabled
- `enableaudio=0`: Audio disabled

## ffplay Examples

Example with explicit HTTPS transport:

```bash
SSL_CERT_FILE="./root_cert.pem" ffplay -rtsp_transport https "rtsp://<username>:<password>@<camera_host>:443/rtsp_tunnel?line=1&inst=1&enableaudio=1"
```

Example without explicitly setting transport:

```bash
SSL_CERT_FILE="./root_cert.pem" ffplay "rtsps://<username>:<password>@<camera_host>:9554/rtsp_tunnel?line=1&inst=1&enableaudio=1"
```

## Security Notes

- Keep credentials secret and never commit them to source control.
- Verify the camera identity and certificate chain in production environments.
- Root certificate: [Root Certificate](../best_practice/README.md#root-certificate).
- Only expose port `9554` to trusted networks and clients that need stream access.
- Prefer least-privilege firewall rules and avoid broad internet exposure.
