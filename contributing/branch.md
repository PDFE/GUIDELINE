# Branch 命名规范

```
<type>/<scope>/<subject>
```

## Type

Type 用于标记这个分支的作用。下面是一些例子：

feat: 新的特性、新的功能
fix: 修复 Bugs
docs: 关于文档的更新
style: 代码格式化，代码简化等（不影响代码的运行）
refactor: 重构（没有新特性增加也没有 Bug 被修复）
test: 项目测试
chore: 升级工具（如 gulpfile 的更新）
ci: 修改 CI 的流程
remove: 简单地将部分模块的代码从项目中移除

一个分支可以包含一或两个 Type。

## Scope

用 1 到 2 个单词注明项目中的哪一部分、哪一模块会被影响

## Subject(Not necessary)

用 1 到 2 个单词注明项目中这一部分中的哪些代码会被影响，或简单注明为什么新建了这个分支

---

以下是几个复合规范的 Branch 命名的样例：

```
feat/player
fix/index/navbar
refactor/user/new-design
```
