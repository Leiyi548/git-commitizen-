# git-commitizen-学习

这个仓库是我用来学习 git-commitizen，我在这个仓库进行操作和提交，并在这个 README 里面记录

## 1. Commit message 规范

每次提交，Commit message 都包括三个部分：Header，Body 和 Footer。

```text
<type>(<scope>): <subject>
// 空一行
<body>
// 空一行
<footer>
```

其中，Header 是必需的，Body 和 Footer 可以省略。

不管是哪一个部分，任何一行都不得超过 72 个字符（或 100 个字符）。这是为了避免自动换行影响美观。

## 2. Header

Header 部分只有一行，包括三个字段：type（必需）、scope（可选）和 subject（必需）。

### 2.1. type

type 用于说明 commit 的类别，允许使用下面 8 个标识。

- feat：新功能（feature）
- fix：修补 bug
- docs：文档（documentation）
- style： 格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改 bug 的代码变动）
- test：增加测试
- chore：构建过程或辅助工具的变动
- perf: 提升性能
- release:发布一个新的版本或者 tag

如果 type 为 feat 和 fix，则该 commit 将肯定出现在 Change log 之中。其他情况（docs、chore、style、refactor、test）由你决定，要不要放入 Change log，建议是不要。

### 2.2. scope

scope 用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

### 2.3. subject

- subject 是 commit 目的的简短描述，不超过 50 个字符。
- 以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes
- 第一个字母小写
- 结尾不加句号（.）

```text
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─⫸ Commit Scope: The scope should be the name of the component affected
  │                           (as perceived by the person reading the
  │                          changelog generated from commit messages).
  │
  └─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

## 3. Body

Body 部分是对本次 commit 的详细描述，可以分成多行。下面是一个范例。

More detailed explanatory text, if necessary. Wrap it to about 72 characters or so. Further paragraphs come after blank lines. - Bullet points are okay, too - Use a hanging indent

有两个注意点。

（1）使用第一人称现在时，比如使用 change 而不是 changed 或 changes。

（2）应该说明代码变动的动机，以及与以前行为的对比。

## 4. Footer

### 4.1. 不兼容变动

如果当前代码与上一个版本不兼容，则 Footer 部分以 BREAKING CHANGE 开头，后面是对变动的描述、以及变动理由和迁移方法。

```text
BREAKING CHANGE: isolate scope bindings definition has changed.
To migrate the code follow the example below:
Before:
scope: {
myAttr: ‘attribute’,
}
After:
scope: {
myAttr: ‘@’,
}
```

The removed inject wasn’t generaly useful for directives so there should be no code using it.

### 4.2. 关闭 issue

如果当前 commit 针对某个 issue，那么可以在 Footer 部分关闭这个 issue 。

Closes `#234`

也可以一次关闭多个 issue 。

Closes `#123`, `#245`, `#992`

## 5. 生成 Change log

如果你的所有 Commit 都符合 Angular 格式，那么发布新版本时， Change log 就可以用脚本自动生成

生成的文档包括以下三个部分。

- New feature
- Bug fixes
- Breaking changes

每个部分都会罗列相关的 commit ，并且有指向这些 commit 的链接。当然，生成的文档允许手动修改，所以发布前，你还可以添加其他内容。

现在不需要我没有大项目，学习这个不值得。

## 6. 参考文章

[git commit 规范 、CHANGELOG 生成 和版本发布的标准自动化(https://blog.csdn.net/wyhbest/article/details/122789174)
