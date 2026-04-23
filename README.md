# Easy Dev Spec

`easy-dev-spec` 用于把“已经相对明确的需求”细化成实施级开发文档。它适合这样的场景：你已经有提示词、技术文档、语雀资料，或一组需要联动修改的代码仓库，希望 AI 先读资料、看代码、把关键问题问干净，再产出可直接指导开发的 dev spec。

它更关注已有代码分析、接口协议、字段定义、类职责、开发顺序和联调顺序，尤其适合多项目协同需求。

## 输入

支持以下输入源：

- 用户提示词
- Markdown 技术文档
- 本地文本资料
- 可访问的语雀技术文档
- 一个或多个代码仓库路径

## 输出

默认输出到 `.easy-coding/spec/dev/`：

- 单项目：`<项目名>-<需求主题>-dev-spec.md`
- 多项目：每个项目各 1 份项目级 spec
- 多项目额外生成：`<需求主题>-cross-project-dev-spec.md`

所有文档默认统一写到当前工作区，不会自动落到各个目标项目目录。

## 工作方式

1. 先静默分析资料和代码
2. 先给一份阅读/分析/追问计划
3. 每轮固定只问 3 个问题
4. 关键疑问收敛后再生成正式文档
5. 若涉及多项目，再补跨项目总控文档

分析和文档撰写期间，不能修改业务项目代码。

## 文档使用提醒

生成完成后，应主动提醒用户把需要使用的文档拷贝到对应项目工作区，再在目标项目里引用。

## 消费方式

这些 dev spec 不会被自动扫描。正确使用方式是由用户显式引用目标 spec 文件，再交给后续开发流程按这份文档执行。

## 仓库内容

- [SKILL.md](./SKILL.md)：技能主流程与硬规则
- [agents/openai.yaml](./agents/openai.yaml)：Codex 展示名和默认提示
- [references/dev-spec-template.md](./references/dev-spec-template.md)：项目级 dev spec 模板
- [references/cross-project-dev-spec-template.md](./references/cross-project-dev-spec-template.md)：跨项目总控模板
- [references/question-plan-template.md](./references/question-plan-template.md)：计划与追问模板
