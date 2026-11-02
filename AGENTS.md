# AG Platformer 2D工作约定

本仓只持独立完整2D游戏、资源与自身合同；引擎在auto-ui、Gallery在ag-examples，不复制或修改其实现。当前授权仅规划，任何实施、构建、素材制作及工作树创建须等用户启动对应Plan。

- 本仓从001独立编号，跨仓写ag-platformer-2d/PLAN-NNN；本地显示可简称G2-NNN。取号独占锁docs/plans/.next-id并复扫活动与archived/archive最大号，禁止覆盖；不取外仓高水位。
- auto-plan:new → work →独立上下文review → merge。主检出仅管理文档；实现、构建在合同指定每Plan每仓唯一权威树。归档使用docs/plans/archived/，历史归档不重开；checked/status不是完成证据。
- 普通Auto决定玩法，不写专用Rust业务/私有Host命令。实际引擎、SDK681、工具链、锁、工具及资源身份固定；接口草稿可准备，正式集成硬等上游实际交付，不追开发tip。
- 独立final必须不同实现上下文且绑定revision/输入，同会话自检不代final。冻结定向门、实际合入、canonical Spec核来源后才归档；新Plan只提规范增量，不提前写交付Spec/派生JSON。
- 临时材料唯一D:/autostack/plan-artifacts/plan-NNN/ag-platformer-2d/，开工登记owner/用途/路径/在途。禁止attachments/散落探针或第二暂存区；merge摘要折Plan并逐项对账所有实际输出，删除自有scope及构建物；同号其他仓scope不能删除，仅具名未解决问题记录owner/理由/关闭条件持有。
- worktree内禁止junction/symlink；移除前必须fresh运行bash D:/autostack/wt-guard.sh <实际树>并为clean。未知材料、其他owner WIP不覆盖、不批量提交或清理。
- 按真实受影响用例验证，不为日常合入跑全AG；GPU/窗口/音频重型门同机单实例。OS键鼠/焦点自动化暂停；人工走查或具名缺证如实登记，不以脚本状态/截图替代必需真实运行。
- 小资源随Git；单文件>5MB先说明/获明确例外，不入大日志/构建物。资源清单包含固定来源、许可、派生配方、路径、长度、SHA256与预算；不下载当前上游替换固定源。
