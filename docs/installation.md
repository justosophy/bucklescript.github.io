---
title: Installation
---

**Prerequisite**: either NPM (comes with [node](https://nodejs.org/en/)) or [Yarn](https://yarnpkg.com/en/).

If you'd like to install BuckleScript globally, do:

```sh
yarn global add bs-platform
```

or

```sh
npm install -g bs-platform
```

This gives you a few globally exposed commands you can run, described later. But usually, you'd install the project locally:

```sh
yarn add --dev bs-platform
```

```sh
npm install --save-dev bs-platform
```

The commands that are exposed are:

- `bsb`, the build system.
- `bsc`, the raw compiler. Usually not used directly.
- `bsrefmt`, the included [Reason](https://reasonml.github.io) parser & printer.

## Alternatives (Power Users)

### Install From Source, Through NPM/Yarn

**Prerequisite**: either npm or yarn, plus the standard C toolchain.

```sh
git clone https://github.com/bucklescript/bucklescript
cd bucklescript
npm install
```

### Install From Source, Without NPM/Yarn

See this for details https://github.com/BuckleScript/bucklescript/blob/master/CONTRIBUTING.md#setup

## Troubleshooting

### spawnSync ENOENT error

If you get an error that looks like `Error: spawnSync /node_modules/bs-platform/lib/bsb.exe ENOENT` it might be caused if 
you have npm postinstall scripts disabled. In that case, re-enable scripts with `npm config set ignore-scripts false` and re-install `bs-platform`


### Permission denied errors

Under some conditions, the global installation of `bs-platform` will result in npm errors, typically indicating `Error: EACCES: permission denied`. Here are some methods for resolving this problem.

#### Manually change npm’s default directory

Changing where NPM stores the package files may help, see the [second solution](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) on the [docs.npmjs.com](https://docs.npmjs.com/) site.

#### Enable the `unsafe-perm` npm option

While using `unsafe-perm` does have some drawbacks, it easily resolves the permissions issue. When the changing the default directory does not work, then this may be the next best option.

```sh
npm install -g bs-platform --unsafe-perm
```
