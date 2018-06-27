# Relix
A tool help you push release to NPM.

It auto generate version (use [SemVer](https://semver.org/)), push commit and tag, publish to npm.

## What?

When we publish a package to NPM, we need do these works:

* Change version in package.json manually.
* Git add and Commit with a message like `bump version xxx`
* Push commit to github.
* Git tag version.
* Push tag to github.
* Publish to NPM by `npm publish`.

Oops... So annoying! That's why I create **Relix**!

## What can Relix help you?

* Auto change release version according to [SemVer](https://semver.org/).

  You don't have to spend time on changing versions. MAJOR.MINOR.PATCH.BETA, Fully automatic.

* Auto add changed files and generate commit message according to **SemVer version type**.

  For example, you use `relix --patch`, the commit message will be `Bump version x.x.x`.

  If you use `relix --prerelease alpha`, the commit message will be `Prerelease alpha version x.x.x`.

  Sounds great! Right?

* Push commit to github and make a tag according to new version, then push it to github too.

* Publish to NPM!

## Usage

```bash
npm i relix -g
# or
npm i relix -D
```

```bash
relix -h
```

```
  Usage: relix [options]

  Version format: MAJOR.MINOR.PATCH (see: https://semver.org/)

  Options:

    -v, --version              output the version number
    --patch                    version when you make backwards-compatible bug fixes.
    --minor                    version when you add functionality in a backwards-compatible manner
    --major                    version when you make incompatible API changes
    --prepatch [identifier]    increments the patch version, then makes a prerelease (default: beta)
    --preminor [identifier]    increments the minor version, then makes a prerelease (default: beta)
    --premajor [identifier]    increments the major version, then makes a prerelease (default: beta)
    --prerelease [identifier]  increments version, then makes a prerelease (default: beta)
    --accessPublic             npm publish --access=public
    -h, --help                 output usage information
```

## Cli

eg: Current Version: **1.1.1**

cmd: `relix [options]`

| Cmd                      | Version         | commit_msg     | Description |
|--------------------------|-----------------|----------------|-------------|
| `--patch`                | `1.1.2`         | Bump version 1.1.2 | Generate a version when you make backwards-compatible bug fixes. |
| `--minor`                | `1.2.0`         | Release minor version 1.2.0 | Generate a version when you add functionality ina backwards-compatible manner. |
| `--major`                | `2.0.0`         | Release major version 2.0.0 | Generate a version when you make incompatible API changes. | 
| `--prepatch alpha`       | `1.1.2-alpha.0` | Prerelease alpha version 1.1.2-alpha.0 | Increments the patch version, then makes a prerelease. | 
| `--preminor rc`          | `1.2.0-rc.0`    | Prerelease rc version 1.2.0-rc.0 | Increments the patch version, then makes a prerelease. | 
| `--preminor`             | `2.0.0-beta.0`  | Prerelease beta version 2.0.0-beta.0 | Increments the patch version, then makes a prerelease. |
| `--prerelease`           | `1.1.2-beta.0`  | Prerelease beta version 1.1.2-beta.0 | Increments the patch version, then makes a prerelease. |
| `--patch --accessPublic` | `1.1.2`         | Bump version 1.1.2 | `npm publish --access=public`, When your npm package is under scope,use it. eg: `package name: @scope/packageName` |

## LICENSE

[MIT](./LICENSE) © PengJiyuan
