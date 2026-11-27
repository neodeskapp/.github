# Security policy

How to report a vulnerability in a neodeskapp repository and what to expect
after you do. This policy covers every repository of the organization.

## Reporting a vulnerability

Please don't post a security problem in public, on Discord or in GitHub
Discussions. Report it privately:

- Server, web console, installers and Docker images:
  <https://github.com/neodeskapp/neodesk/security/advisories/new>
- Desktop client:
  <https://github.com/neodeskapp/neodesk-client/security/advisories/new>
- Anything else, or if you prefer mail: security@neode.sk

Please include, where you can:

- What the problem is and what an attacker gains.
- How to reproduce it: a proof of concept, a request and its answer, the
  steps in the client, or a test case.
- The affected version or commit, the operating system, and how NeoDesk
  was installed (Docker, the Linux or Windows installer, the client's
  installer or MSI, a package, a build from source).
- Logs, screenshots or traffic captures, with sensitive data removed.
- Whether the problem is also in RustDesk, if you know.

## Response targets

- **Acknowledgement:** within 7 days of the report.
- **Triage decision:** within 14 days (severity, scope, fix plan).
- **Coordinated disclosure:** at most 90 days from the acknowledgement,
  shorter if the issue is being exploited.
- **Credit:** if you want it, in the release notes or the advisory.

If you get no acknowledgement within 7 days, write on the
[NeoDesk Discord](https://discord.gg/nwERSawufr) only that you are waiting
for an answer to a security report, with no details.

## Supported versions

Security fixes go into `main` and the next release. Older releases may get
a backport for a critical issue at the maintainers' discretion.

| Version | Supported |
| ------- | --------- |
| `main` | Yes |
| Newest release | Yes |
| Older releases | Best effort |

## Scope

In scope:

- [neodesk](https://github.com/neodeskapp/neodesk): the Go server in
  `neodesk-server/` (the ID server and the relay, the HTTP and WebSocket
  API, the client API for RustDesk clients, the CDAP gateway, the
  MeshCentral compatibility layer, the database code, the release
  signature checks and the command-line tools), the web console with its
  server code in `neodesk-server/console/` and the web app in `web-ui/`
  including the browser remote desktop viewer, the installers and compose
  files in `install/`, the Docker images in `docker/`, the CDAP SDKs in
  `sdks/`, the reference bridges in `bridges/`, the RDP and VNC gateway
  files in `remote-gateway/`, and the release workflows.
- [neodesk-client](https://github.com/neodeskapp/neodesk-client): the
  desktop client (the Rust code in `src/` and `libs/`, the Flutter app in
  `flutter/`), its installers and packages, and the release workflows.
- [hbb_common](https://github.com/neodeskapp/hbb_common), the client's
  shared Rust library.
- [website](https://github.com/neodeskapp/website): neode.sk and the docs.

Out of scope:

- Issues that need an attacker who already controls the host's operating
  system, the database file, or an administrator's account or browser
  session.
- Denial of service from plain network flooding without an amplification
  vector.
- Self-XSS, missing security headers on the website, or theoretical issues
  without a concrete way to exploit them.
- Reports from automated scanners that nobody checked by hand.
- Problems in the stock RustDesk client or RustDesk's own servers. Report
  those to [RustDesk](https://github.com/rustdesk/rustdesk/security).

## Running a server safely

The settings and steps that make a server harder to attack are on the
website: <https://docs.neode.sk/operations/security/>.
