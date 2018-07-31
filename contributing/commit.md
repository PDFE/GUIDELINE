# Commit Message 规范

!> 所有成员必须遵守该规范。否则 PR 将会被以 `Squash` 的形式合并，推送到主分支的代码将会被 Force 回退。

## Title

(1) type

`type` 用于说明 commit 的类别，只允许使用次啊面的标识；如果本条 commit 包括两个以上的 `type`，使用 `/` 分开。

- revert: Revert 代码回退，用于撤回某个改动
- feat: New feature 新功能
- fix: Fix bug 修补 bug
- docs: Documentation 文档（包括 README 的更新）
- style: Format 格式（不影响代码运行的变动）
- refactor: Refactor 重构（即不是新增功能，也不是修改 bug 的代码变动）
- test: Test 测试相关
- workflow: WorkFlow 工作流相关
- chore: 构建过程或辅助工具的变动
- merge: 合并 Pull Request

(2) scope

`scope` 用于说明 commit 影响的范围，紧接 `type` 置于 `()` 之内。

> scope 非必须，当改动代码范围较大或者范围不明确时可忽略

!> 当使用 Merge Pull Request 合并不同分支时，scope 为 PR 在 GitHub 上的编号。
!> 当使用 revert 回退代码时，scope 为对应 commit 的 Title，也可以是简短的介绍。

(3) subject

`subject` 是 commit 目的的简短描述，不超过 50 个字符。

> 1. 以动词开头
> 2. 使用第一人称现在时比如 change，尽可能避免使用 changed 或 changes
> 3. 首字母小写，并且 **尽可能** `subject` 全部小写
> 4. 结尾不加句号 `.`
> 5. 当 `type` 是 `merge` 时，`subject` 应为 `from {base branch name} to {target branch name}`

以下是几个复合规范的 title 的样例：

https://github.com/SukkaW/hexo-theme-suka/commit/5b799d925e5d618c628524d9ffc222185d20fcd7
```
feat(custom_code): muilt line custom code support
```

https://github.com/SukkaW/hexo-theme-suka/commit/75dc6e367ff51f78cbbe556dadf6fbcf423e5e05
```
chore/ci: bring ci to the theme development (#2)
```

https://github.com/SukkaW/hexo-theme-suka/commit/e894ada457826ef53248bef5cd90ddd0f010de2f
```
merge(#5): from master to canary
```

## Body

Body 部分是对本次 commit 的详细描述，可以分成多行。下面是一个范例。

```
docs(commit): add about body of commit message
More detailed explanatory text, if necessary. Wrap it to about 72 characters or so.

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Use a hanging indent
```

和 `title.subject` 不同，Body 只要求以下两点：

> 1. 使用第一人称现在时比如 change，尽可能避免使用 changed 或 changes
> 2. 应该说明代码变动的动机，以及与以前行为的对比。

!> 如果使用 Squash 合并分支时，Body 为以无序列表排列的对应多条 commit 记录。

## Footer

Footer 只有两种使用方式：`BREAKING CHANGES` `issue` 和 `revert`

### BREAKING CHANGES

如果当前代码与上一个版本不兼容、对应构建和部署需要跟着做出较大改动时，此时 Footer 以 BREAKING CHANGE 开头，后面是对变动的描述、变动理由和迁移方法。

```
BREAKING CHANGE: isolate scope bindings definition has changed

To migrate the code follow the example below:

Before:

scope: {
  myAttr: 'attribute',
}

After:

scope: {
  myAttr: '@',
}

The removed `inject` wasn't generaly useful for directives so there should be no code using it.
```

### issue

如果当前 commit 针对某个 issue，那么可以在 Footer 部分关闭这个 issue。

```
Closes #124
```

GitHub 也支持一次 commit 关闭多个 issue。

```
Closes #123, #124, #126
```

### revert

必须写成以下形式，，其中的 hash 是一个或多个被撤销 commit 的 SHA 标识符。

```
This reverts commit <hash>.
```

```
This reverts:
- commit <hash1>
- commit <hash2>
- commit <hash3>
```

如果当前 commit 与被撤销的 commit，在同一个发布（release）里面，那么它们都不会出现在 Change log 里面。如果两者在不同的发布，那么当前 commit，会出现在 Change log 的 Changes 小标题下面。
