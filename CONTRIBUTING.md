# Contributing to NeoDesk

Changes come in as pull requests against `main`. This page applies to every
neodeskapp repository. The full guide is on the website:

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

## AI-assisted contributions

AI tools are part of how NeoDesk is developed, and you're welcome to use
them for code, tests, translations and documentation. You don't need to say
that you did. You are responsible for what you submit, the same as for
anything you wrote by hand: understand it, run it, and be ready to explain
it in review.

### Use a capable model

Use a current, capable model, the strongest one your tool offers. Don't use
small, heavily quantized or older-generation models. NeoDesk is a large
codebase built on the RustDesk protocol, which most models know little
about, and weaker models fill the gaps with guesses that look right:

- protocol messages, fields and ports that RustDesk clients don't send or
  expect
- settings, environment variables and API routes that don't exist in
  NeoDesk
- database changes that work on SQLite and break on PostgreSQL, or the
  other way round
- console strings added in one language instead of in every locale file
- tests that pass no matter what the code does

Read the whole diff before you open the pull request, and run the checks
from [Tests and checks](https://docs.neode.sk/development/tests-and-checks/)
on it.

## Desktop client

[docs/BUILD_DESKTOP.md](https://github.com/neodeskapp/neodesk-client/blob/main/docs/BUILD_DESKTOP.md)
in neodesk-client has the full build steps for Windows x64 and Linux x64,
with the tool versions CI uses. In short:

```sh
git submodule update --init --recursive
python build.py --flutter --hwcodec --vram --skip-portable-pack   # Windows
python3 ./build.py --flutter --hwcodec                            # Linux
python3 flutter/tool/check_colours.py   # the colour check CI runs on flutter/lib
cd flutter && flutter test && flutter analyze
```

- On Windows, `scripts/check_desktop_env_windows.ps1` checks the toolchain
  first.
- Colours come from the tokens in `flutter/lib/common/theme/nd_theme.dart`.
- The Flutter tests and the analyzer need `flutter/lib/generated_bridge.dart`,
  which is not in the repository. Generate it with
  `flutter_rust_bridge_codegen` 1.80.1 as `.github/workflows/bridge.yml`
  does, or take it from the bridge artifact of a CI run.
- Icons come from Material Symbols through `NdIcons`. To add one, add its
  line to `flutter/tool/nd_symbols.txt` and run
  `python3 tool/build_symbols.py` in `flutter/`.
- The client is built on RustDesk: keep its copyright and license notices
  in the files you change.

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
