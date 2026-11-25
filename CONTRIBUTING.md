# Contributing to NeoDesk

Changes come in as pull requests against `main`. This page applies to every
neodeskapp repository that has no contributing guide of its own. The full
guide is on the website:

- [Contributing](https://docs.neode.sk/development/contributing/): how to
  propose a change, what a pull request needs, commit messages and
  contributor licensing.
- [Building from source](https://docs.neode.sk/development/building/) and
  [Tests and checks](https://docs.neode.sk/development/tests-and-checks/):
  how to build the server and which checks to run before you open the pull
  request.

Questions go to the [NeoDesk Discord](https://discord.gg/nwERSawufr) or to
[GitHub Discussions](https://github.com/neodeskapp/neodesk/discussions).
Report security problems privately, as [SECURITY.md](SECURITY.md) describes,
not on Discord or in Discussions.

## Propose a change

1. For a larger change, start a discussion first and describe what you want
   to change, so we can agree on the approach before you write the code.
2. Fork the repository and create a branch from the current `main`.
3. Make the smallest change that solves the problem. Keep one concern per
   pull request.
4. Build what you changed and run its tests. Write tests that fail when the
   behaviour they cover is broken.
5. Open the pull request against `main` and fill in the template.

## Pull request rules

- **No private data:** no credentials, keys, hostnames, IP addresses or
  configuration of a real deployment. Use example addresses such as
  `203.0.113.10`.
- **No secrets for fork code:** don't add a workflow that runs code from a
  fork with the repository's secrets.
- **Provenance:** say where external code, generated files and anything taken
  from upstream come from, and keep the author and license of reused code.
- **Security changes:** a change to sign-in, permissions or a network path
  says who may do what, where the limits are and how it fails.
- **Tests:** list the commands you ran and their results.

## Commit messages

Use a Conventional Commits subject without a scope:

```text
fix: keep the device list sorted after a device comes online
feat: move a database between SQLite and PostgreSQL with neodesk-server migrate
```

- The type is one of `feat`, `fix`, `refactor`, `chore`, `docs`, `test` and `ci`.
- After the colon: lower case, imperative, no full stop at the end. Say what
  changes for the user, not which file you touched.
- Put the discussion or pull request number at the end of the subject when
  there is one: `... #42`.
- Most commits need a subject only. A large change gets a body in plain prose
  that explains why.

## License

Everything here is under the AGPL-3.0. Who keeps the copyright in a
contribution, and how outside work is credited, is in
[Contributor licensing](https://docs.neode.sk/development/contributing/#contributor-licensing).

Everyone who takes part follows the [code of conduct](CODE_OF_CONDUCT.md).
