# Security policy

How to report a vulnerability in a neodeskapp repository and what to expect
after you do. The server and the client have their own policies with the
full scope:
[neodesk](https://github.com/neodeskapp/neodesk/blob/main/SECURITY.md) and
[neodesk-client](https://github.com/neodeskapp/neodesk-client/blob/main/SECURITY.md).

## Reporting a vulnerability

Please don't post a security problem in public, on Discord or in GitHub
Discussions. Report it privately:

- Server, web console, installers and Docker images:
  <https://github.com/neodeskapp/neodesk/security/advisories/new>
- Anything else, or if you prefer mail: security@neode.sk

Please include, where you can:

- What the problem is and what an attacker gains.
- How to reproduce it: a proof of concept, a request and its answer, or a
  test case.
- The affected version or commit, and the operating system.
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

## Out of scope

- Issues that need an attacker who already controls the host's operating
  system, the database file, or an administrator's browser session.
- Denial of service from plain network flooding without an amplification
  vector.
- Reports from automated scanners that nobody checked by hand.
- Problems in the stock RustDesk client or RustDesk's own servers. Report
  those to [RustDesk](https://github.com/rustdesk/rustdesk/security).
