<div align="center">
  <a href="https://github.com/zgsgs/eslint-config">
    <h1>@zgsgs/eslint-config</h1>
  </a>

  <p>仅使用 eslint 管理代码规范</p>

[**English**](./README.md) |
[**中文翻译**](./README_zh.md)
</div>

---

[![npm](https://img.shields.io/npm/v/@zgsgs/eslint-config?color=a1b858&label=)](https://npmjs.com/package/@zgsgs/eslint-config)

## 功能

- 单引号，不半引号
- 自动修复格式(旨在独立使用而不使用 Prettier)
- TypeScript, Vue, React 开箱即用的
- 也可以Lint jso、yaml、markdown 类型文件
- 排序导入，悬挂逗号表示，实现更清晰的 commit diff
- 合理的默认值，最佳实践，只有一行配置

## 用法

安装

```bash
pnpm add -D eslint @zgsgs/eslint-config
```

### 配置 `.eslintrc`

```json
{
  "extends": "@zgsgs"
}
```

或者

```json
// package.json
{
  "eslintConfig": {
    "extends": "@zgsgs"
  }
}
```

> 正常情况下，你不需要 `.eslintignore`，因为它已由预设提供。

### 为 package.json 添加脚本

例如:

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

### 配置 VS Code 自动修复

创建 `.vscode/settings.json`

```json
{
  "prettier.enable": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

当使用 eslint 时，建议不要使用 prettier。这个配置已经完成了相当多的格式化工作，剩下的灵活性和样式留给了开发人员。

## VS Code 设置

---

将 `.vscode` 目录复制到您的项目根目录

### 其他设置

> - [Default setting](https://code.visualstudio.com/docs/getstarted/settings#_default-settings)
> - [File Nesting Config for VS Code](https://github.com/antfu/vscode-file-nesting-config)

## Github 设置

将 `.github` 目录复制到您的项目根目录

## 使用 husky & lint-staged & commitlint 完成 commit message 规范限制和修复

- 将 `.husky` 目录和 `commitlint.config.js` 文件复制到您的项目根目录
- 编辑你的 `.package.json` 文件

```json
{
  "scripts": {
    "lint": "lint-staged",
    "prepare": "husky install"
  },
  "lint-staged": {
    "*.{vue,js,jsx,ts,tsx,json}": [
      "eslint --fix",
      "git add ." // 请注意，所有文件都自动保存在这里，请使用 `.gitignore`
    ]
  }
}
```

## 其他配置文件

- `.editorconfig` - 编辑器配置
- `.gitignore` Git忽略特殊文件
- `LICENSE` 开源许可证
- `netlify.toml` Netlify 平台配置
- `pnpm-workspace.yaml` 定义 的根目录并使您能够从工作空间中包含/排除目录。
- `renovate.json` 使用 renovate 监控第三方相关更新

## 也可以查看

- [zgsgs/vscode-settings](https://github.com/zgsgs/vscode-settings) - 我的 VS Code 设置
- [zgsgs/eslint-config](https://github.com/zgsgs/eslint-config) - 我的 ESLint 配置
- [zgsgs/ts-starter](https://github.com/zgsgs/ts-starter) - 我的 TS 库的启动模板
- [zgsgs/vitesse](https://github.com/zgsgs/vitesse) - 我的 Vue & Vite 应用的启动模板

## 许可证

[MIT](./LICENSE)
