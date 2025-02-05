# Electron 版本管理

> 详细查看我们的版本控制策略和实现。

在 2.0.0.0版本，Electron 跟随 [semver](#semver)。 以下命令将安装最新稳定的 Electron 版本：

```sh
npm install --save-dev electron
```

现有项目更新到最新的稳定版本:

```sh
npm install --save-dev electron@latest
```

## 版本1.x

Electron versions *< 2.0* did not conform to the [semver](https://semver.org) spec: major versions corresponded to end-user API changes, minor versions corresponded to Chromium major releases, and patch versions corresponded to new features and bug fixes. 虽然方便开发人员合并功能，但却为面向客户端应用程序的开发人员带来了麻烦。 像Slack，Stride，Teams，Skype，VS Code，Atom和Desktop等主要应用程序的QA测试周期可能很长，稳定性是一个非常理想的结果。 尝试吸收错误修复时，采用新功能的风险很高。

以下是 1.x 策略的一个例子：

![](../images/versioning-sketch-0.png)

使用 `1.8.1`开发的应用程序无法吸收 `1.8.2 ` 的功能，或者通过反向移植修复和维护新的发行版，无法采用 `1.8.3`错误修复。

## 版本 2.0 和之后版本

我们的1.x战略有以下几项重大变化。 每次更改都是为了满足开发者/维护者和应用开发者的需要和优先事项。

1. 严格使用 semver
2. 引入符合 semver 的 `-beta` 标签
3. 引入[常规提交消息](https://conventionalcommits.org/)
4. 明确定义的稳定分支
5. `master`分支没有版本信息，只有稳定分支会包含版本信息。

我们将详细介绍 git 分支是如何工作的，npm 标记是如何工作的，开发人员应该看到什么，以及如何能够支持更改。

# semver

从 2.0 开始，Electron 将遵循 semver。

下面是一个表格，明确地将变化的类型映射到它们对应的 semver 类别 (例如Major，Minor，Patch)。

| Major 版本增量          | Minor 版本增量           | Patch 版本增量         |
| ------------------- | -------------------- | ------------------ |
| Electron 突破性 API 变更 | Electron 无突破性 API 变更 | Electron bug 修复    |
| Node.js 重大版本更新      | Node.js 次要版本更新       | Node.js patch 版本更新 |
| Chromium 版本更新       |                      | 修复相关的 chromium 补丁  |

请注意，大多数Chromium更新都将被认为是分解的。 可以返回的修复很可能会被精选为补丁。

# 稳定分支

稳定分支是与主子平行的分支，只是在挑选的与安全或稳定有关的精选承诺中。 这些分支永远不会被合并为主人.

![](../images/versioning-sketch-1.png)

既然Electron 8, 稳定分支总是 **个主要版本行** 并根据以下模板 `$MAJOR-x-y` e命名。 。 `8-x-y`  在此之前，我们使用 **个次要的** 版本行，并将它们命名为 `$MAJOR-$MINOR-x` 例如： `2-0-x`

我们允许同时存在多个稳定分支，并且打算在任何时候至少支持两个并行支持安全修复。 ![](../images/versioning-sketch-2.png)

GitHub不支持旧线路，但是其他分组可以自行获取所有权和返回稳定性和安全修复。 我们不鼓励这样做，但是认识到它使得许多应用程序开发人员的生活更轻松。

# 测试版和 Bug 修复

开发人员想知道哪个版本可以 _安全_ 使用。 即使是简单的功能也会使应用程序变得复杂。 同时，锁定到一个固定的版本是很危险的，因为你忽略了自你的版本以来可能出现的安全补丁和错误修复。 我们的目标是在 `package.json ` 中允许以下标准的 semver 范围:

* 使用 ` ~ 2.0. 0 ` 只接受您的 ` 2.0.0 ` 版本的稳定性或安全性相关的修复程序。
* 使用 ` ^ 2.0. 0 ` 可允许不破坏性的 _ 合理稳定 _ 功能以及安全性和 bug 修复。

第二点重要的是使用 `^` 的应用程序仍然能够期望合理的稳定性水平。 为了达到这个目的，semver允许一个 _pre-release 标识_ 来表示一个特定的版本还不 _安全_ 或 _稳定_.

无论你选择什么，你将定期不得不在 `package.json` 中打破版本，因为突破性变更是 Chromium 的一个常态。

过程如下:

1. 所有新的主要和次要的版本行都以 `beta 的分号预发布标签表示的测试系列开头。`, 例如 `2.0.0-beta.1`。 在第一次测试后，测试版随后的释放必须满足以下所有条件：
    1. 更改是落后的 API 兼容 (允许废弃)
    2. 实现我们稳定的时间表的危险必须是低的。
2. 如果允许更改需要在释放测试版之后进行，则使用并增加预放标签，例如`2.0.0-beta.2`。
3. 如果特定的beta版本_通常被认为_是稳定的，那么它将作为稳定版本被重新发布，只改变版本信息。例如.0。 例如 `2.0.0-beta.1`. 在第一个稳定之后，所有的变化都必须落后兼容的 bug 或安全修复。
4. 如果未来错误修复或安全补丁一旦发布稳定，它们将被应用，并且 _补丁_ 版本被增量 ，例如 `2.0.1`。

特别地，上述步骤意味着：

1. 允许在测试周期第三周之前进行非拆解-API更改，即使这些更改有可能造成适度的副效果
2. 接受特征标记的更改，这些更改不会改变现有的代码路径。在测试周期中的大多数点都是好的。 用户可以在他们的应用中明确启用那些标记。
3. 第三周之后在测试周期内接纳任何类型的功能是 👎 没有很好的理由。

对于每个主要和次要的颠覆，你都应该像以下示例一样进行操作：

```plaintext
2.0.0-beta.1
2.0.0-beta.2
2.0.0-beta.3
2.0.0
2.0.1
2.0.2
```

图片中的生命周期示例:

* 创建了一个新的发行分支，包括最新的功能。 它已发布为 `2.0.0-beta.1`。 ![](../images/versioning-sketch-3.png)
* Bug 修复会被导入主，可以返回发布分支。 补丁已应用，一个新测试版已发布为 `2.0.0-beta.2`。 ![](../images/versioning-sketch-4.png)
* 测试版被认为是 _ 一般稳定 _ 的, 它在 ` 2.0.0 ` 下作为非 beta 版本再次被发布。 ![](../images/versioning-sketch-5.png)
* 后来，揭露了零天的利用情况，并对大师采取了补救措施。 我们支持修复为 `2-0-x` 行，并释放 `2.0.1`。 ![](../images/versioning-sketch-6.png)

几个不同的 semver 范围将如何接收新版本的示例:

![](../images/versioning-sketch-7.png)

# 缺失的特性: alpha版本

我们的战略有几次权衡，我们现在认为这是适当的。 最重要的是, 新的主分支特性可能需要一段时间才能作为稳定版发布。 如果你想立即尝试一个新的特性, 你必须自己编译Electron 。

作为未来的考虑, 我们可以介绍以下一种或两种情况:

* 具有松散稳定性限制的 alpha 释放版; 例如, 当稳定通道在 _ alpha _ 中时, 允许接纳新特性

# 功能标志

功能标志是 Chromium 的一种常见的做法, 在网络开发生态系统中得到了很好的确立。 在 Electron 环境中, 功能标志或 ** 软分支 ** 必须具有以下属性:

* 是在运行时或生成时启用/禁用的。我们不支持请求作用域功能标志的概念
* 它完全细分新的和旧的代码路径; 重构旧代码以允许新功能 _ 违反 _ 功能标志内容
* 在合并功能后, 功能标志最终将被删除

# 提交语义

我们力求在更新和发布过程的各个层面提高清晰度。 从 ` 2.0.0 ` 开始, 我们将要求遵循 [ 常规提交 ](https://conventionalcommits.org/) 规范的拉请求, 可以概括如下:

* 会导致 semver **major** 版本改变的提交必须以`BREAKING CHANGE:`开头。
* 提交会导致 semver **minor** 必须以 `feat:` 开头。
* 提交会导致 semver ** patch ** 必须以 ` fix:` 开头。

* 我们允许丢弃提交，条件是被丢弃的信息符合上述信息格式。
* 只要pull request里包含有意义的总结性的版本语义消息，即使它其中的某些提交消息不包含版本语义前缀也是可以接受的

# 打了版本的 `主分支`

- The `master` 分支将始终在其 `package.json` 中包含 `0.0.0-dev`.
- Release 分支永远不会合并回 master 分支
- 发布分支 _在_ 其`package.json ` 中包含正确的版本
- 一旦一个主要的释放分支被切割，主子就必须被打碎为下一个大师。  I.e. `master` is always versioned as the next theoretical release branch
