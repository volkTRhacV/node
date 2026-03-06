# Node.js

Node.js is an open-source, cross-platform JavaScript runtime environment.

For information on using Node.js, see the [Node.js website][].

The Node.js project uses an [open governance model](./GOVERNANCE.md). The
[OpenJS Foundation][] provides support for the project.

Contributors are expected to act in a collaborative manner to move
the project forward. We encourage the constructive exchange of contrary
opinions and compromise. The [TSC](./GOVERNANCE.md#technical-steering-committee)
reserves the right to limit or block contributors who repeatedly act in ways
that discourage, exhaust, or otherwise negatively affect other participants.

**This project has a [Code of Conduct][].**

## Table of contents

* [Support](#support)
* [Release types](#release-types)
  * [Download](#download)
    * [Current and LTS releases](#current-and-lts-releases)
    * [Nightly releases](#nightly-releases)
    * [API documentation](#api-documentation)
  * [Verifying binaries](#verifying-binaries)
* [Building Node.js](#building-nodejs)
* [Security](#security)
* [Contributing to Node.js](#contributing-to-nodejs)
* [Current project team members](#current-project-team-members)
  * [TSC (Technical Steering Committee)](#tsc-technical-steering-committee)
  * [Collaborators](#collaborators)
  * [Triagers](#triagers)
  * [Release keys](#release-keys)
* [License](#license)

## Support

Looking for help? Check out the
[instructions for getting support](.github/SUPPORT.md).

## Release types

* **Current**: Under active development. Code for the Current release is in the
  branch for its major version number (for example,
  [v22.x](https://github.com/nodejs/node/tree/v22.x)). Node.js releases a new
  major version every 6 months, allowing for breaking changes. This happens in
  April and October every year. Releases appearing each October have a support
  life of 8 months. Releases appearing each April convert to LTS (see below)
  each October.
* **LTS**: Releases that receive Long Term Support, with a focus on stability
  and security. Every even-numbered major version will become an LTS release.
  LTS releases receive 12 months of _Active LTS_ support and a further 18 months
  of _Maintenance_. LTS release lines have alphabetically-ordered code names,
  beginning with v4 Argon. There are no breaking changes or feature additions,
  except in some special circumstances.
* **Nightly**: Code from the Current branch built every 24-hours when there are
  changes. Use with caution.

Current and LTS releases follow [semantic versioning](https://semver.org). A
member of the Release Team [signs](#release-keys) each Current and LTS release.
For more information, see the
[Release README](https://github.com/nodejs/Release#readme).

### Download

Binaries, installers, and source tarballs are available at
<https://nodejs.org/en/download/>.

#### Current and LTS releases

<https://nodejs.org/download/release/>

The [latest](https://nodejs.org/download/release/latest/) directory is an
alias for the latest Current release. The latest-_codename_ directory is an
alias for the latest release from an LTS line. For example, the
[latest-hydrogen](https://nodejs.org/download/release/latest-hydrogen/)
directory contains the latest Hydrogen (Node.js 18) release.

#### Nightly releases

<https://nodejs.org/download/nightly/>

Each directory and filename includes the version (e.g., `v22.0.0`),
followed by the UTC date (e.g., `20240424` for April 24, 2024),
and the short commit SHA of the HEAD of the release (e.g., `ddd0a9e494`).
For instance, a full directory name might look like `v22.0.0-nightly20240424ddd0a9e494`.

#### API documentation

Documentation for the latest Current release is at <https://nodejs.org/api/>.
Version-specific documentation is available in each release directory in the
_docs_ subdirectory. Version-specific documentation is also at
<https://nodejs.org/download/docs/>.

### Verifying binaries

Download directories contain a `SHASUMS256.txt.asc` file with SHA checksums for the
files and the releaser PGP signature.

You can get a trusted keyring from nodejs/release-keys, e.g. using `curl`:

```bash
curl -fsLo "/path/to/nodejs-keyring.kbx" "https://github.com/nodejs/release-keys/raw/HEAD/gpg/pubring.kbx"
```

Alternatively, you can import the releaser keys in your default keyring, see
[Release keys](#release-keys) for commands on how to do that.

Then, you can verify the files you've downloaded locally
(if you're using your default keyring, pass `--keyring="${GNUPGHOME:-~/.gnupg}/pubring.kbx"`):

```bash
curl -fsO "https://nodejs.org/dist/${VERSION}/SHASUMS256.txt.asc" \
&& gpgv --keyring="/path/to/nodejs-keyring.kbx" --output SHASUMS256.txt < SHASUMS256.txt.asc \
&& shasum --check SHASUMS256.txt --ignore-missing
```

## Building Node.js

See [BUILDING.md](BUILDING.md) for instructions on how to build Node.js from
source and a list of supported platforms.

## Security

For information on reporting security vulnerabilities in Node.js, see
[SECURITY.md](./SECURITY.md).

## Contributing to Node.js

* [Contributing to the project][]
* [Working Groups][]
* [Strategic initiatives][]
* [Technical values and prioritization][]

## Current project team members

For information about the governance of the Node.js project, see
[GOVERNANCE.md](./GOVERNANCE.md).

<!-- node-core-utils and find-inactive-tsc.mjs depend on the format of the TSC
     list. If the format changes, those utilities need to be tested and
     updated. -->

### TSC (Technical Steering Committee)

#### TSC voting members

<!--lint disable prohibited-strings-->



 

<summary>TSC emeriti members</summary>

#### TSC emeriti members

* [addaleax](https://github.com/addaleax) -
  **Anna Henningsen** <<anna@addaleax.net>> (she/her)
-


</details>

<!-- node-core-utils and find-inactive-collaborators.mjs depend on the format
     of the collaborator list. If the format changes, those utilities need to be
     tested and updated. -->

### Collaborators


 
<summary>Emeriti</summary>

<!-- find-inactive-collaborators.mjs depends on the format of the emeriti list.
     If the format changes, those utilities need to be tested and updated. -->

### Collaborator emeriti




You can use the keyring the project maintains at
<https://github.com/nodejs/release-keys/raw/refs/heads/main/gpg-only-active-keys/pubring.kbx>.
Alternatively, you can import them from a public key server. Have in mind that
the project cannot guarantee the availability of the server nor the keys on
that server.

```bash
gpg --keyserver hkps://keys.openpgp.org --recv-keys 5BE8A3F6C8A5C01D106C0AD820B1A390B168D356 # Antoine du Hamel
gpg --keyserver hkps://keys.openpgp.org --recv-keys DD792F5973C6DE52C432CBDAC77ABFA00DDBF2B7 # Juan José Arboleda
gpg --keyserver hkps://keys.openpgp.org --recv-keys CC68F5A3106FF448322E48ED27F5E38D5B0A215F # Marco Ippolito
gpg --keyserver hkps://keys.openpgp.org --recv-keys 8FCCA13FEF1D0C2E91008E09770F7A9A5AE15600 # Michaël Zasso
gpg --keyserver hkps://keys.openpgp.org --recv-keys 890C08DB8579162FEE0DF9DB8BEAB4DFCF555EF4 # Rafael Gonzaga
gpg --keyserver hkps://keys.openpgp.org --recv-keys C82FA3AE1CBEDC6BE46B9360C43CEC45C17AB93C # Richard Lau
gpg --keyserver hkps://keys.openpgp.org --recv-keys 108F52B48DB57BB0CC439B2997B01419BD92F80A # Ruy Adorno
gpg --keyserver hkps://keys.openpgp.org --recv-keys A363A499291CBBC940DD62E41F10027AF002F8B0 # Ulises Gascón
```

See [Verifying binaries](#verifying-binaries) for how to use these keys to
verify a downloaded file.

<details>

<summary>Other keys used to sign some previous releases</summary>

* **Antoine du Hamel** <<duhamelantoine1995@gmail.com>>
  `C0D6248439F1D5604AAFFB4021D900FFDB233756`
* **Beth Griggs** <<bethanyngriggs@gmail.com>>
  `4ED778F539E3634C779C87C6D7062848A1AB005C`
* **Bryan English** <<bryan@bryanenglish.com>>
  `141F07595B7B3FFE74309A937405533BE57C7D57`
>
  `9554F04D7259F04124DE6B476D5A82AC7E37093B`
>
  `94AE36675C464D64BAFA68DD7434390BDBE9B9C5`

  `1C050899334244A8AF75E53792EF661D867B9DFA`
  `74F12602B6F1C4E913FAA37AD3A89613643B6201`

  `B9AE9905FFD7803F25714661B63B535A4C206CA9`


  `93C7E9E91B49E432C2F75674B0A78B0A6C481CF6`

  `56730D5401028683275BD23C23EFEFE93C4CFFFE`

  `71DCFD284A79C3B38668286BC97EC7A07EDE3FC1`

  `FD3A5288F042B6850C66B31F09FE44734EB7990E`

  `61FC681DFB92A079F1685E77973F295594EC4689`

  `114F43EE0176B71C7BC219DD50A3051F888C628D`

  `C4F0DFFF4E8C1A8236409D08E73BC641CC11F4C8`

  `DD8F2338BAE7501E3DD5AC78C273792F7D83545D`

  `A48C2BEE680E841632CD4E44F07496B3EB3C1762`

  `B9E2F5981AA6E0CD28160D9FF13993A75599653C`

  `7937DFD2AB06298B2293C3187D33FF9D0246406D`

The project maintains a keyring able to verify all past releases of Node.js at
<https://github.com/nodejs/release-keys/raw/refs/heads/main/gpg/pubring.kbx>.

</details>

### Security release stewards

When possible, the commitment to take slots in the
security release steward rotation is made by companies in order
to ensure individuals who act as security stewards have the
support and recognition from their employer to be able to
prioritize security releases. Security release stewards manage security
releases on a rotation basis as outlined in the
[security release process](./doc/contributing/security-release-process.md).


## License

Node.js is licensed under the [MIT License](https://opensource.org/licenses/MIT).

This project also depends on external libraries that may use different open-source
licenses. For a complete list of included licenses, please see the
[LICENSE](https://github.com/nodejs/node/blob/main/LICENSE) file.

If you are contributing documentation or source changes, please ensure your
additions comply with the project’s license guidelines.

[Code of Conduct]: https://github.com/nodejs/admin/blob/HEAD/CODE_OF_CONDUCT.md
[Contributing to the project]: CONTRIBUTING.md
[Node.js website]: https://nodejs.org/
[OpenJS Foundation]: https://openjsf.org/
[Strategic initiatives]: doc/contributing/strategic-initiatives.md
[Technical values and prioritization]: doc/contributing/technical-values.md

