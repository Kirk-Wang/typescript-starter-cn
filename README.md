<img height="0" width="0" alt="Typescript Starter Dark" src="https://cloud.githubusercontent.com/assets/904007/23006840/4e2b0c6c-f3d2-11e6-8f32-11384ee0cc4b.png"><img alt="typescript-starter" src="https://cloud.githubusercontent.com/assets/904007/23006836/4c67a3b8-f3d2-11e6-8784-12f0a34284d1.png">


一个用于构建javascript库和项目的[typescript](https://www.typescriptlang.org/)启动器：{#typescript-starter}

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

## 开始吧{#Get-started}

在开始之前，请考虑使用一个[具有良好typescript支持](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Editor-Support)的编辑器。

[VS Code](https://code.visualstudio.com/)（以下）是一个受欢迎的选择。具有typscript支持的编辑器可以提供有用的自动完成、内嵌文档和代码重构功能。

<p align="center">
  <img alt="Typescript Editor Support – vscode" width="600" src="https://cloud.githubusercontent.com/assets/904007/23042221/ccebd534-f465-11e6-838d-e2449899282c.png">
</p>

要了解这个启动器如何用作其他项目的依赖关系，请查看示例文件夹。上面的例子来自[`examples/node-typescript`](https://github.com/bitjson/typescript-starter/tree/master/examples/node-typescript)。

## 开发禅宗{#Development-zen}

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

## 启用强类型检查（推荐）{#Enable-stronger-type-checking}

为了让开始更容易，默认的`tsconfig.json`正在使用`config/tsconfig.flexible`配置。这将允许您开始，而没有来自Typescript的任何警告。

要启用附加的Typescript类型检查功能（对关键任务或大型项目来说是个好主意），请将`tsconfig.json`中的`extend`值更改为`./config/tsconfig.strict`。

## 查看测试覆盖率{#View-test-coverage}

要生成和查看测试覆盖率，请运行：

```bash
yarn cov
```

这将创建一个测试覆盖率的HTML报告 - 源映射回Typescript，并在默认浏览器中打开它。

<p align="center">
  <img height="600" alt="source-mapped typescript test coverage example" src="https://cloud.githubusercontent.com/assets/904007/22909301/5164c83a-f221-11e6-9d7c-72c924fde450.png">
</p>

## 生成您的API文档{#Generate-your-API-docs}

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

## 生成/更新[更改日志] & [标签发布]{#Generate-update-changelog-and-tag-release}

该项目用[常规变更日志](https://github.com/conventional-changelog/conventional-changelog)工具来使项目管理发布更容易。 有关工作流的更多信息请参阅[标准版本](https://github.com/conventional-changelog/standard-version)文档，或一个相关例子的[`CHANGELOG.md`](https://github.com/bitjson/typescript-starter/blob/master/CHANGELOG.md)。

```bash
# bump package.json version, update CHANGELOG.md, git tag the release
yarn changelog
```

## 一键发布脚本{#One-step-publish-preparation-script}

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

## 所有包脚本{#All-package-scripts}

您可以运行`info`脚本，以获取有关想要单独运行的每个脚本的信息。

```
yarn run info

  info:
    显示所有有关脚本的信息
  build:
    （垃圾回收）构建库
  lint:
    验证所有的typescript源文件的代码规范
  unit:
    构建库并运行单元测试
  test:
    代码规范验证，构建和测试库
  watch:
    监视源文件，重新构建库上的更改，重新运行相关测试
  cov:
    运行测试，生成HTML覆盖率报告，并在浏览器中打开它
  docs:
    生成HTML API文档并在浏览器中打开它
  docs:publish:
    生成HTML API文档并将其推送到GitHub Pages
  docs:json:
    以typedoc JSON格式生成API文档
  release:
    Bump package.json版本，更新CHANGELOG.md，标记一个版本
  reset:
    删除所有未跟踪的文件，并将仓库重置为最后一次提交
  publish:
    Reset, build, test, publish docs, and prepare release (一键发布过程)
```

## 说明{#Notes}

### 多种构建 (`main`，`module`和`browser`){#Multiple-builds}

`typescript-starter`的`src`被编译成三个单独的构建：`main`，`module`和`browser`。`main`构建是[配置为使用CommonJS模块系统](https://github.com/bitjson/typescript-starter/blob/master/tsconfig.json#L8)，而`module`构建[使用新的ES6模块系统](https://github.com/bitjson/typescript-starter/blob/master/config/tsconfig.module.json)。浏览器版本包含两个软件包，一个ES6模块（优先导出）和一个CommonJS软件包（主要用于测试）。

因为Node.js还不支持ES6模块系统，所以依赖于typescript-starter的Node.js项目将跟随package.json中的`main`字段。支持新系统的工具（如[Rollup](https://github.com/rollup/rollup)）将跟随`module`字段，使他们能够静态分析typescript-starter。当浏览器构建时，较新的工具将遵循`browser`字段，这将解析为浏览器版本的ES6模块。

### 测试{#Testing}

按照惯例，在typcript-starter中的测试与他们测试的文件是共存的。 该项目被配置为允许以Typescript编写测试，并且您的库被导入，就像被另一个项目一样使用。 （例如`import { double, power } from 'typescript-starter'`）。这使得测试既直观又易于阅读，作为另一种形式的文档。

注意，测试是在标准的Node.js运行时（而不是像[ts-node](https://github.com/TypeStrong/ts-node)这样的替代方案）的最终版本中编译和执行的，以确保在该环境中通过测试。 如果在[生产中使用ts-node](https://github.com/TypeStrong/ts-node/issues/104)，则可以修改此项目以跳过测试编译。

### 浏览器库{#Browser-libraries}

虽然浏览器和Node.js版本的库都已经过测试，但是这个启动程序当前**没有**在真正的浏览器中运行浏览器测试（[AVA](https://github.com/avajs/ava)当前是仅用于Node）。虽然目前的测试系统对大多数用例都是足够的，但一些项目（也）需要实施基于浏览器的测试系统，如[karma-ava](https://github.com/avajs/karma-ava)。 （欢迎PR！）

注意：仅针对Node.js实现检查测试覆盖。这更简单，并且适用于node和浏览器实现具有不同依赖性的库，仅需较少的适配代码。只有几行差异（例如`src/adapters/crypto.browser.ts`），包括测试覆盖率分析中的几行通常不是必需的。

### 构建浏览器依赖关系{#Building-browser-dependencies}

此启动程序演示了当浏览器构建时导入和使用CommonJS模块（[`hash.js`](https://github.com/indutny/hash.js)），它的`hash256`方法。 有关更多详细信息，请参阅`build:browser-deps` [package script](https://github.com/bitjson/typescript-starter/blob/master/package.json)和[rollup.config.js](./config/exports/rollup.config.js)。 当然，您的项目可能不需要此依赖关系，因此可以将其删除。如果您的库不需要为浏览器捆绑外部依赖项，还可以删除其他几个devDependencies（`browserify`，`rollup-plugin-alias`，`rollup-plugin-commonjs`，`rollup-plugin-node-resolve`等）。

### 依赖于`tslib`{#Dependency-on-tslib}

默认情况下，此项目需要[tslib](https://github.com/Microsoft/tslib)作为依赖关系。这是为大型项目使用Typescript的es6和es7透明度的推荐方法，但您可以通过删除`tsconfig.json`中的`importHelpers`编译器选项来删除此依赖关系。 根据您的使用情况，这可能会显着增加您的库的大小，因为Typescript编译器将其辅助函数直接注入到使用它们的每个文件中。（另见：[`noEmitHelpers` &rarr;](https://www.typescriptlang.org/docs/handbook/compiler-options.html)）

### 针对较旧的环境{#Targeting-older-environments}

默认情况下，此库针对具有原生（或already-polyfilled）es6功能支持的环境。如果您的库目标是在Internet Explorer，过时的Android浏览器或V4以上版本的Node，则可能需要将tsconfig.json中的目标更改为es5（而不是es6），并导入Promise polyfill（如 [es6-promise](https://github.com/stefanpenner/es6-promise)）。

保持100％的单元测试覆盖率是一个好主意，并且始终在您目标环境中进行测试。

## 其它typescript-starter{#typescript-starter-in-the-wild}

您可以从使用`typescript-starter`的项目中找到更多高级配置，使用示例并获取灵感。

- [BitAuth](https://github.com/bitauth/) – A universal identity and authentication protocol, based on bitcoin
- [s6: Super Simple Secrets * Simple Secure Storage](https://gitlab.com/td7x/s6/) – An NPM library and tool to sprawl secrets with S3, ease, and encryption

使用`typescript-starter`作为你的项目？ 请PR将其添加到列表中！

