## Scalable Project Architecture Template

A template for creating a production-ready fullstack Next.js 13 application using `app/` directory (beta).

## Table of Contents

1. [Install](#install)
2. [Configuration](#config)
3. [Engine Locking](#engine-locking)
4. [ESLint](#eslint)
5. [Git Hooks](#git-hooks)
6. [Creators](#creators)
7. [Thanks](#thanks)

## Install

1.  Run `npm install` to install the Node.js dependencies, including Husky (Git hooks).
2.  Run `npm run dev` to start the development server.
3.  Open `http://localhost:3000/` in your browser, and voilà.

## Configuration

`next.config.js`

```
  experimental: {
    appDir: true,
  },
```

Experimental feature `appDir` in `next.config.js` is enabled. Experimental features are not covered by semver, and may cause unexpected or broken application behavior. Use at your own risk.

## Engine Locking

`.nvmrc`

```
lts/hydrogen
```

Node.js version is set to [Hydrogen](https://nodejs.org/download/release/latest-hydrogen/) (18.x)
<br>

`.npmrc`

```
engine-strict=true
```

If set to true, then npm will stubbornly refuse to install (or even consider installing) any package that claims to not be compatible with the current Node.js version
<br>

`package.json`

```
"engines": {
  "node": ">=18.0.0",
  "yarn": "please-use-npm",
  "npm": ">= 8.0.0"
},
```

The `"engines"` field specifies what versions of Node and npm must be used.

## ESLint

`.eslintrc.json`

```
  "globals": {
    "React": "readonly"
  },
```

`React` is always defined, even if it is not explicitly imported.
<br>

`.eslintrc.json`

```
  "rules": {
    "no-unused-vars": [1, { "args": "after-used", "argsIgnorePattern": "^_" }]
  }
```

Prefix variables with an underscore `_` that have been declared but not used yet.
<br>

## Prettier

[Prettier](https://prettier.io/) plugin for [VS Code](https://code.visualstudio.com/) is required.

`.prettierrc`

```
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```

Prettier configuration.
<br>

`package.json`

```
  ...
  "scripts: {
    ...
    "prettier": "prettier --write ."
  }
```

Run `npm run prettier` to automatically format and save all files, except those mentioned in `.prettierignore`.

## Git Hooks

`package.json`

```
  ...
  "scripts: {
    ...
    "prepare": "husky install"
  }
```

This will ensure Husky gets installed automatically when other developers run the project.
<br>

`commitlint.config.js` Contains the standard defaults for commit messages. [Learn more](https://www.conventionalcommits.org/en/v1.0.0-beta.4/).

## Creators

Cosmin Iancu

- [GitHub](https://github.com/ianstecos)

## Thanks

Thanks [Alex Eagleson](https://github.com/alexeagleson) for inspiration. Your blogs and videos were very informative!
