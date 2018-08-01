# PDFE Workflow

!> 以下是 PDFE 的工作流规范

- 当创建一个项目的时候，生成 LICENSE、README、`.gitignore` 等文件；在 `master` 分支之下，完成对基本框架和原型的搭建
- 在 `master` 分支的基础上 fork 出 `develop` 分支，之后的开发都围绕 `develop` 分支展开，`master` 分支仅存放稳定的代码，生产环境实时同步 `master` 分支
- 比较小的改动、细节的优化、`hotfix` 等，可以直接推送进 `develop` 分支
- 比较大的新特性、新的模块、代码重构、涉及范围较大的修复时，需要从 `develop` 分支上再 fork 出一个新的分支，在该分支的单元测试通过后通过 Pull Request 的方式 Merge 回 `develop` 分支
- 对 `master` 分支进行的紧急修复可以直接推送进 `master` 中，但是事后需要通过 Pull Request 的方式 merge 回 `develop` 分支
- 当一个阶段的开发结束以后，进行一次完整测试，测试通过后把 `develop` 分支通过 Pull Request 的方式 merge 进 `master` 分支、推送到生产环境
- 涉及 `develop` 分支的 Pull Request 需要两名及以上成员 review 后通过才能 merge
- 设计 `master` 分支的 Pull Request 需要五名及以上成员 review 后才能 merge

?> Review 包括目视检查各项 changes，并审核 CI 进行的测试的日志

!> **绝对不要 Force Push**  
如果 local 和 remote 出现冲突，**先 rebase**

?> 对于没有 repo 推送权限的开发者，需要 fork repo 以后，checkout 到 `develop` 分支上，并根据需要自行决定是否从 `develop` 分支上新建分支进行开发，测试通过后用 Pull Request 的方式申请 merge 进 repo 的 `develop` 分支
