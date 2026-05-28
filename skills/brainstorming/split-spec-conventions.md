# Parent/Child Spec 共享约定

当需求被拆成 parent/child spec 时，`SKILL.md`、模板文件和 reviewer prompt 都应遵循这份共享约定。

## 拆分追踪

- 拆分后必须保留父 spec。
- 每轮只允许编写或修订一个当前 child spec。
- 父 spec 的 `Split Specs` 章节只列已经写出的 child spec。
- 每个已写出的 child spec 都必须带实现进度 checkbox，例如 `- [ ] Implementation status: Not done`。
- 父 spec 的 `Candidate Future Split Specs` 章节只列未来候选 child spec，且**不加 checkbox**。
- 交接文档不替代父 spec 的 `Split Specs` 和 `Candidate Future Split Specs`；候选 child spec 信息仍以父 spec 为准。

## 术语规则

- parent/child spec 拆分出的子文档统一称为 `child spec`；不要把 child spec 叫做 slice。
- `feature slice` 只指 spec 文档内部的功能切片，例如 `## Feature Slice 1: ...`。
- 一个 child spec 内可以包含多个 feature slice，因此父 spec、交接文档和 reviewer prompt 都必须用 child spec 来指代子文档。

## 命名规则

- child spec 文件名必须继承父 spec 前缀。
- 父 spec 使用 `YYYY-MM-DD-<topic>-spec.md`。
- child spec 使用 `YYYY-MM-DD-<topic>-child-x-<child spec name>-spec.md`。
- 不要为 child spec 换日期、换 topic 前缀或使用无关联命名。

## 链接规则

- parent/child spec 之间的引用必须写成 markdown 链接。
- 链接目标必须使用**相对当前文档位置**可解析的相对路径。
- 父 spec 的 `Spec:` 条目必须链接到对应 child spec，例如 `[YYYY-MM-DD-<topic>-child-x-<child spec name>-spec.md](./YYYY-MM-DD-<topic>-child-x-<child spec name>-spec.md)`。
- child spec 应包含对父 spec 的反向引用，例如 `[YYYY-MM-DD-<topic>-spec.md](./YYYY-MM-DD-<topic>-spec.md)`。
- 不要只写反引号包裹的纯文本路径。

## Global Constraints 继承规则

- 父 spec 的 `Global Constraints` 负责承载所有 child spec 共用的仓库/产品约束、兼容性、依赖限制和通用 mock 逃逸边界。
- child spec 应保留 `Global Constraints` 章节，但它的职责是：
  - 用相对路径 markdown 链接引用父 spec 的共享约束；
  - 只补充本 child spec 独有的额外约束；
  - 不重复整段拷贝父 spec 已经声明的共享约束。
- 如果 child spec 大段重复父 spec 的共享 `Global Constraints`，或 child spec 缺少对父 spec 共享约束的明确引用，应视为问题。
