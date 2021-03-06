# jsdoc-vue-component

> A simple plugin for jsdoc (`pase vue SFC info to description by AST analysis`).

Maybe you will try [jsdoc-vuedoc](https://github.com/ccqgithub/jsdoc-vuedoc), and you have a better experience。

## Installation

```sh
npm i jsdoc-vue-component -D
```

## Related

- [espree](https://github.com/eslint/espree): parse code to ast.
- [escodegen](https://github.com/estools/escodegen): generate code from ast.
- [estraverse](https://github.com/estools/estraverse): traverse the AST tree.
- [JsDoc3](https://github.com/jsdoc3/jsdoc).
- [docstrap](https://github.com/docstrap/docstrap): a theme for jsdoc3.
- [jsdoc-vuedoc](https://github.com/ccqgithub/jsdoc-vuedoc): A jsdoc3 plugin use `@vuedoc/md`.

## Use:

> This plugin just extract the component's info into `markdown` format, and instert it into the `@vuedoc`'s position.

> Not affect other jsdoc features of the code.

1. add `@vuedoc` tag to comment.
2. add `@exports componentName` tag to comment.

just add `@vuedoc` tag, `@exports` tag, to the to document in you vue SFC.

```js
/**
 * sidebar component description
 * @vuedoc
 * @exports component/SideBar
 */
export default {}
```

## 如何使用jsdoc？

- 安装jsdoc: `npm i jsdoc -D`
- 安装模板：`npm i sherry-docstrap -D`, 原来的[docstrap](https://github.com/docstrap/docstrap)有点小bug还未修复，所以自己暂时发布一个。
- 在项目目录下建了配置文件：下面有示例，适当修改。
- 在pacakge.json 里添加一个script: `"jsdoc": "rm -rf public/jsdoc && node_modules/.bin/jsdoc -c jsdoc.json"`, `public/jsdoc`为发布位置，适当修改
- 生成文档: `npm run jsdoc`

## Options

- `log`: true,
- `tag`: 'vuedoc'

## jsdoc.json

```json
{
  "plugins": [
    "node_modules/jsdoc-vue-component",
    "plugins/markdown",
    "plugins/summarize"
  ],
  "jsdoc-vue-component": {
    "log": true
  },
  "markdown": {
    "tags": ["author", "classdesc", "description", "param", "property", "returns", "see", "throws", "vue"]
  },
  "recurseDepth": 10,
  "source": {
    "include": ["fe/src"],
    "includePattern": ".+\\.(js|vue)$",
    "excludePattern": "(^|\\/|\\\\)_"
  },
  "sourceType": "module",
  "tags": {
    "allowUnknownTags": true,
    "dictionaries": ["jsdoc", "closure"]
  },
  "templates": {
    "logoFile": "",
    "cleverLinks": false,
    "monospaceLinks": false,
    "dateFormat": "ddd MMM Do YYYY",
    "outputSourceFiles": true,
    "outputSourcePath": true,
    "systemName": "DocStrap",
    "footer": "",
    "copyright": "DocStrap Copyright © 2012-2015 The contributors to the JSDoc3 and DocStrap projects.",
    "navType": "vertical",
    "theme": "cosmo",
    "linenums": true,
    "collapseSymbols": false,
    "inverseNav": true,
    "protocol": "html://",
    "methodHeadingReturns": false
  },
  "markdown": {
    "parser": "gfm",
    "hardwrap": true
  },
  "opts": {
    "template": "node_modules/sherry-docstrap/template",
    "encoding": "utf8",
    "destination": "./public/jsdoc/",
    "recurse": true,
    "readme": "README.md",
    "tutorials": "./docs/"
  }
}
```

## 效果

![效果](assets/xiaoguo.jpeg).
