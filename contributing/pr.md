# Pull Request 规范

## Title

Title 的要求和 [Commit 信息规范](https://pdfe.github.io/GUIDELINE/#/contributing/commit) 中规定的 Commit 的 Title 的要求相同。

## Content

Pull Request 的内容应该包含以下内容：

- Pull Request 的目的和内容
- Pull Request 的测试方式
- 以及以下的检查;
  - Pull Request 涉及的类型
  - 是否符合 GUIDELINE
  - 相关测试是否添加
  - 文档部分是否需要改动；如果需要，是否也被更新

下面是一个 Pull Request 的模板：

```markdown
## Please check if your PR fulfills the following requirements:

- [ ] The commit message follows our guidelines.
- [ ] Tests for the changes have been added (for bug fixes / new features).
- [ ] Docs have been added / updated (for bug fixes / new features).

## What kind of change does this PR introduce? (check with "x")

- [ ] Bug fix
- [ ] Feature
- [ ] Code style update (formatting, local variables)
- [ ] Refactoring (no functional changes, no api changes)
- [ ] Build related changes
- [ ] CI related changes
- [ ] Other... Please describe:

## Does this PR introduce a breaking change? (check one with "x")

- [ ] Yes
- [ ] No

If this PR introduce a breaking change, add description about how to mirage it:

____

## Description


____

## How to Verification and Review

```
