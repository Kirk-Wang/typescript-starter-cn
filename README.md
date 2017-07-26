<img height="0" width="0" alt="Typescript Starter Dark" src="https://cloud.githubusercontent.com/assets/904007/23006840/4e2b0c6c-f3d2-11e6-8f32-11384ee0cc4b.png"><img alt="typescript-starter" src="https://cloud.githubusercontent.com/assets/904007/23006836/4c67a3b8-f3d2-11e6-8784-12f0a34284d1.png">


一个用于构建javascript库和项目的[typescript](https://www.typescriptlang.org/)启动器：

* 写**标准的，未来的**javascript - 具有稳定的es7功能 - 今天（[stage 3](https://github.com/tc39/proposals)或[finished](https://github.com/tc39/proposals/blob/master/finished-proposals.md)功能）
* [可以选择使用typescript](https://basarat.gitbooks.io/typescript/content/docs/why-typescript.html)来改进tooling，linting和文档生成
* 为消费者使用[es6导入](https://github.com/rollup/rollup/wiki/pkg.module)（如[Rollup](http://rollupjs.org/)或[Webpack 2](https://webpack.js.org/)），导出为一个[JavaScript模块](http://jsmodules.io/)，使您的工作**fully tree-shakable**
* 导出类型声明，以提高您的下游开发经验
* Node.js风格（CommonJS）导入的向后兼容性
* 兼备[严格](https://github.com/bitjson/typescript-starter/blob/master/config/tsconfig.strict.json)和[灵活](https://github.com/bitjson/typescript-starter/blob/master/config/tsconfig.flexible.json)两种可利用的typescript配置

因此我们可以拥有很棒的东西：
* 生成API文档（HTML或JSON），而[没有一团糟的JSDoc标记](https://blog.cloudflare.com/generating-documentation-for-typescript-projects/)来维护
* 用[AVA](https://github.com/avajs/ava)进行并置，原子，并发单元测试
* 用[nyc](https://github.com/istanbuljs/nyc)源代码覆盖率报告
* 可配置的代码覆盖测试（用于持续集成）

## 开始吧

在开始之前，请考虑使用一个[具有良好typescript支持](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Editor-Support)的编辑器。

[VS Code](https://code.visualstudio.com/)（以下）是一个受欢迎的选择。具有typscript支持的编辑器可以提供有用的自动完成、内嵌文档和代码重构功能。

<p align="center">
  <img alt="Typescript Editor Support – vscode" width="600" src="https://cloud.githubusercontent.com/assets/904007/23042221/ccebd534-f465-11e6-838d-e2449899282c.png">
</p>

要了解这个启动器如何用作其他项目的依赖关系，请查看示例文件夹。上面的例子来自[`examples/node-typescript`](https://github.com/bitjson/typescript-starter/tree/master/examples/node-typescript)。

## 开发禅宗

这个启动器包括一个监视任务，使开发更快，更具互动性。对[TDD](https://en.wikipedia.org/wiki/Test-driven_development)/[BDD](https://en.wikipedia.org/wiki/Behavior-driven_development)工作流程尤其有用。

要开始工作，[安装Yarn](https://yarnpkg.com/en/docs/getting-started)并运行：

```
yarn watch
```

这将构建和监视整个项目的更改（对库源文件和测试源文件）。在开发新功能时，您可以为新功能添加测试－最初会失败－在开发新的功能之前。每次保存时，任何更改都将被重新生成并重新测试。

<p align="center">
  <img alt="Typescript and AVA watch task" src="https://cloud.githubusercontent.com/assets/904007/23443884/c625d562-fdff-11e6-8f26-77bf75add240.png">
</p>

由于只有更改的文件被重建和重新测试，即使对于大型项目，此工作流仍然很快。

## 启用强类型检查（推荐）

为了让开始更容易，默认的`tsconfig.json`正在使用`config/tsconfig.flexible`配置。这将允许您开始，而没有来自Typescript的任何警告。

要启用附加的Typescript类型检查功能（对关键任务或大型项目来说是个好主意），请将`tsconfig.json`中的`extend`值更改为`./config/tsconfig.strict`。

## 查看测试覆盖率

要生成和查看测试覆盖率，请运行：

```bash
yarn cov
```

这将创建一个测试覆盖率的HTML报告 - 源映射回Typescript，并在默认浏览器中打开它。

<p align="center">
  <img height="600" alt="source-mapped typescript test coverage example" src="https://cloud.githubusercontent.com/assets/904007/22909301/5164c83a-f221-11e6-9d7c-72c924fde450.png">
</p>

## 生成您的API文档

使用[typedoc](https://github.com/TypeStrong/typedoc)，这个src文件夹被分析并且自动生成文档。

```bash
yarn docs
```

此命令以HTML格式为您的库生成API文档，并在浏览器中打开它。

由于类型由Typescript跟踪，因此不需要指定JSDoc格式的类型。有关更多信息，请参阅[typedoc文档](http://typedoc.org/guides/doccomments/)。

要生成并发布您的文档到[GitHub Pages](https://pages.github.com/)，请使用以下命令：

```bash
yarn docs:publish
```

一旦发布，对于您的仓库，您的文档应该在正确的GitHub页面URL中可用。 以[这个仓库的GitHub页面](https://bitjson.github.io/typescript-starter/)为例。

<p align="center">
  <img height="500" alt="typedoc documentation example" src="https://cloud.githubusercontent.com/assets/904007/22909419/085b9e38-f222-11e6-996e-c7a86390478c.png">
</p>

对于更高级的文档生成，您可以提供自己的[typedoc theme](http://typedoc.org/guides/themes/)或[构建您自己的文档](https://blog.cloudflare.com/generating-documentation-for-typescript-projects/)使用JSON typedoc导出：

```bash
yarn docs:json
```

## 生成/更新[更改日志] & [标签发布]

该项目用[常规变更日志](https://github.com/conventional-changelog/conventional-changelog)工具来使项目管理发布更容易。 有关工作流的更多信息请参阅[标准版本](https://github.com/conventional-changelog/standard-version)文档，或一个相关例子的[`CHANGELOG.md`](https://github.com/bitjson/typescript-starter/blob/master/CHANGELOG.md)。

```bash
# bump package.json version, update CHANGELOG.md, git tag the release
yarn changelog
```

## 一键发布脚本

汇集上面的许多步骤，这个库包含一个一键发布命令。

```bash
# Standard release
yarn release
# Release without bumping package.json version
yarn changelog -- --first-release
# PGP sign the release
yarn changelog -- --sign
```

此命令运行如下命令：
- `yarn reset`: cleans the repo by removing all untracked files and resetting `--hard` to the latest commit. (**Note: this could be destructive.**)
- `yarn test`: build and fully test the project
- `yarn docs:publish`: generate and publish the latest version of the documentation to GitHub Pages
- `yarn changelog`: bump package.json version, update CHANGELOG.md, and git tag the release

当脚本完成后，它将记录推送发布提交到仓库的所需的最终命令，并在`npm`注册处发布包：

```
git push --follow-tags origin master; npm publish
```

如果你想先查看发布，然后执行命令发布所有内容。

## 所有包脚本

您可以运行`info`脚本，以获取有关想要单独运行的每个脚本的信息。

```
yarn run info

  info:
    Display information about the scripts
  build:
    (Trash and re)build the library
  lint:
    Lint all typescript source files
  unit:
    Build the library and run unit tests
  test:
    Lint, build, and test the library
  watch:
    Watch source files, rebuild library on changes, rerun relevant tests
  cov:
    Run tests, generate the HTML coverage report, and open it in a browser
  docs:
    Generate HTML API documentation and open it in a browser
  docs:publish:
    Generate HTML API documentation and push it to GitHub Pages
  docs:json:
    Generate API documentation in typedoc JSON format
  release:
    Bump package.json version, update CHANGELOG.md, tag a release
  reset:
    Delete all untracked files and reset the repo to the last commit
  publish:
    Reset, build, test, publish docs, and prepare release (a one-step publish process)
```



