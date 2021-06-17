<h1 align="center">cz-ghostwriter</h1>

<div align="center">

[![CI Status](https://github.com/JSanchezIO/cz-ghostwriter/workflows/CI/badge.svg)](https://github.com/JSanchezIO/cz-ghostwriter/actions/workflows/ci.yml)
[![Code Style: Prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://prettier.io/)
[![Commitizen Friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![NPM Package Version](https://img.shields.io/npm/v/cz-ghostwriter)](https://www.npmjs.com/package/cz-ghostwriter)
[![Semantic Release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://semantic-release.gitbook.io/semantic-release/)

</div>

<br />

You want to leverage commitizen to enforce a consistent commit messages that can be parsed to
generate a `CHANGELOG.md` but none of the available presets support your commit types or tools,
e.g., Bitbucket, JIRA, Trello. This preset supports configuration via a `.changelogrc.js` file.

<br />

## Installation

```sh
npm i cz-ghostwriter
```

<br />

## Usage

1. Create and configure a `.changelogrc.js` file in the root of your repository
2. Update commitizen to leverage `cz-ghostwriter`

   ```json
   {
    ...

    "path": "./node_modules/cz-ghostwriter"

    ...
   }
   ```

3. Run commitizen

<br />

## Configuration

<br />

### `issuePrefixes` : _string[]_

---

The array of prefixes used to detect references to issues.

<br >

### `issueReferencesPrefix` : _string = "for"_

---

The prefix to use before listing issues that a commit refers to. Defaults to `"for"`.

<br >

### `preset` : _"github" | undefined_

---

The configuration preset to use which will set other configuration properties. If this property is
set the following configuration properties are overwritten, i.e., nullable:

- `issuePrefixes`

<br >

### `scopes` : _Scope[] | undefined_

---

The array of scopes that are available for selection when commiting. If left `undefined`, then any
scope may be entered when committing.

```ts
type Scope = { description: string; type: string };
```

<br >

### `types` : _Array<HiddenType | VisibleType>_

---

The array of type objects representing the explicitly supported commit message types, and whether
they should show up in generated CHANGELOGs.

```ts
type CommitType = { description: string; type: string };

type HiddenType = CommitType & { hidden: true; section: undefined };

type VisibleType = CommitType & { hidden: undefined; section: string };
```
