<div align="center">
  <a href="https://github.com/zgsgs/eslint-config">
    <h1>@zgsgs/eslint-config</h1>
  </a>

  <p>Manage code specification with eslint only</p>

[**English**](./README.md) |
[**中文翻译**](./README_zh.md)
</div>

---

[![npm](https://img.shields.io/npm/v/@zgsgs/eslint-config?color=a1b858&label=)](https://npmjs.com/package/@zgsgs/eslint-config)

## Feature

- Single quotes, no semi
- Auto fix for formatting (aimed to be used standalone without Prettier)
- TypeScript, Vue, React out-of-box
- Lint also for json, yaml, markdown
- Sorted imports, dangling commas for cleaner commit diff
- Reasonable defaults, best practices, only one-line of config

## Usage

### Install

```bash
pnpm add -D eslint @zgsgs/eslint-config
```

### Config `.eslintrc`

```json
{
  "extends": "@zgsgs"
}
```

OR

```json
// package.json
{
  "eslintConfig": {
    "extends": "@zgsgs"
  }
}
```

> You don't need `.eslintignore` normally as it has been provided by the preset.

### Add script for package.json

For example:

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

### Config VS Code auto fix

Create `.vscode/settings.json`

```json
{
  "prettier.enable": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

> It is recommended not to use prettier when using eslint. This configuration has done quite a bit of formatting lint, leaving the rest of the flexibility and style to the developer.

## VS Code Settings

---

Copy the `.vscode` directory go to Your Project Root Directory

### Other Setting

> - [Default setting](https://code.visualstudio.com/docs/getstarted/settings#_default-settings)
> - [File Nesting Config for VS Code](https://github.com/antfu/vscode-file-nesting-config)

## Github Setting

Copy the `.github` directory go to Your Project Root Directory

## Complete the commit message specification restriction and repair using Husky & lint-staged & COMMITLINT

- Copy the `.husky` directory and `commitlint.config.js` go to Your Project Root Directory
- Edit your `.package.json`

```json
{
  "scripts": {
    "lint": "lint-staged",
    "prepare": "husky install"
  },
  "lint-staged": {
    "*.{vue,js,jsx,ts,tsx,json}": [
      "eslint --fix",
      "git add ." // Note that all files are automatically saved here, please use with `.gitignore`
    ]
  }
}
```

## Other configuration files

- `.editorconfig` - Edit config
- `.gitignore` Git ignore special files
- `LICENSE` Open Source LICENSE
- `netlify.toml` Netlify platform configuration
- `pnpm-workspace.yaml` defines the root of the and enables you to include / exclude directories from the workspace.
- `renovate.json` Use renovate to monitor third-party dependent updates

## Check Also

- [zgsgs/vscode-settings](https://github.com/zgsgs/vscode-settings) - My VS Code settings
- [zgsgs/eslint-config](https://github.com/zgsgs/eslint-config) - My ESLint config
- [zgsgs/ts-starter](https://github.com/zgsgs/ts-starter) - My starter template for TypeScript library
- [zgsgs/vitesse](https://github.com/zgsgs/vitesse) - My starter template for Vue & Vite app

## License

[MIT](./LICENSE)
