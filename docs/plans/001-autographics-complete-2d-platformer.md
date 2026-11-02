---
plan_id: PLAN-001
status: drafting
feature_name: AutoGraphics完整2D平台游戏
author: [Codex]
created_at: 2026-11-02
updated_at: 2026-11-02
plan_revision: 1
current_step: 0
total_steps: 10
depends_on: [auto-ui/PLAN-032]
supersedes_spec_components: []
new_spec_components: [docs/specs/game2d.md]
touched_goals: [GOAL-008]
affects: [game2d, public-launch, resources, offline-package]
---

# PLAN-001：独立完整2D平台游戏（G2-001）

## 0. 变更摘要

在独立ag-platformer-2d交付同一个真实Auto程序，完成原G2-01..09、玩法/精灵/声音/HUD、编辑保存及离线搬迁；引擎由auto-ui/032供应，Demo在ag-examples独立推进。drafting r1、0/10，暂不实施。本轮仅本地管理仓/设计/合同，无远端、游戏源码/素材、构建、实施树或agent。

[本仓设计](../design/g2-game-contract.md)与[三线路线](../../../auto-ui/docs/design/autographics/m2-game-first-three-lane-roadmap.md)。frontmatter依赖032是T-05完整接线硬门；T-01..04可以独立准备，不要求引擎先交付。准备不等于游戏已可运行，不能追032开发tip或复用其引擎夹具当正式游戏。

## 1. 目标

1. 独立公共项目入口，普通use/node/model/view-2d/msg/on/Life.Start/Tick表达局部组件和具名资源；真实Auto决定运动、巡逻、收集、胜败/重开及表现，不写专用Rust业务。
2. 完整保原G2-01..09固定关卡/输入/参数、三币/敌人/目标、idle/run/jump/fall与朝向、jump/coin一次声音、n/3和胜败HUD，在同一程序/实际引擎版本成立。
3. 可读源码/可编辑保存关开/改Auto规则真实变化、资源许可与验证、完整离线ZIP及A→B/坏件恢复，不靠生产者源码/target/网络回退。
4. 每个真实分支在原服务/资源/VM包络内，内容独立oracle证明正式关卡与完整流程；引擎绿不代内容完成，游戏交付不代整个M2。

非目标：修改引擎/SDK/auto-ui、Gallery/3D游戏、全编辑器/反向重写Auto/双向同步、额外物理/网络/多个可控角色、Life.Frame/多呈现、ACE/AOT/ECS/CPC/跨端、改预算或删验收。暂不制作发布远端或创建实施树。

## 2. 架构方案

本仓Auto局部组件/关卡/资源/许可→固定实际032公开Node生成工具→受检生成Auto/scene/identity/closure→固定公开driver/SDK681→Host/GPU/mixer/HUD。永久工具只做启动/来源校验/打包/外部观察，不能计算替代游戏分数/运动或注入测试私有玩法。

拟唯一实施与顺序独立review树D:/autostack/.wt/g2-001/ag-platformer-2d，codex/plan-001-dev；本轮不创建。引擎/语言/SDK只读、target/报告/安装/包独占；不建链接。游戏消费实际交付后冻结source、Spec、toolchain/锁、生成器/runner哈希；文档接口草稿不是可执行依赖锁。

## 3. 技术栈

当前本仓仅README/AGENTS/docs/design/docs/plans/.next-id与本合同，无既有游戏实现。拟新增src/main.at、player/enemy/coin/goal/boundary及纯helper模块、资源manifest/许可/配方、generated/、project元数据、公开启动/打包工具、tools/verify_game2d.py与永久独立oracle/负控（均提案路径，T-02冻结实际布局/CLI）。不新造内容侧编译器/VM/decoder/物理控制器。

复用UI020/022/025现有局部组件/精灵/音画合同；完整组合必须消费032最终交付。无需030三维能力或AG013内容先完成。永久回归夹具可入仓；临时探针/日志/截图/包/外部消费者均只入本Plan自有材料scope。

## 4. 需求分析与背景调查

用户2026-11-02明确路线为2D引擎＋完整2D游戏＋Demo三线并行，同时规划3D表现音画，2D稳定闭环后再交付完整3D。原M2不是更多隔离演示；全程真实Auto、公有接口、独立工程及原验收分母保持。

权威输入：[原G2-01..09/几何/来源](../../../auto-lang/docs/design/autographics/m2-game-sample-matrix.md)、[M2-01..09](../../../auto-lang/docs/design/autographics/m2-editor-and-public-game-prototypes.md)、[旧完整预算研究](../../../auto-lang/docs/specs/auto-graphics/g2-full-loop-budget-feasibility.md)、[032合同](../../../auto-ui/docs/plans/032-autographics-node2d-full-game-composition.md)、[022 Spec](../../../auto-ui/docs/specs/auto-graphics/node2d-sprites-and-frame-animation.md)、[025 Spec](../../../auto-ui/docs/specs/auto-graphics/node-presentation-services.md)。旧UI011固定0261ae9两候选no_go是历史证据；当前022与025作者档独立，底层组合存在不证明新作者完整G2已成立。

已核UI020交付16ddfa0；022交付2f45baa+c6aa63a、Spec SHA256 f997bae66305eef07d5eb902dcc5ba195350c2ffff38360fcd456dda9877f1b2；025交付e9cc929/收口54899e9、Spec SHA256 62090294bcbdb83affc2194a0e93e0d284290578e28d162f1ce6f7748528d610。032当前仅drafting/r1，没有实际交付SHA，不能预填。SDK固定7b987ca8b12f2eec3c076a1bfbf3ff4663aa8467及681内容锁；历史对象不可达按原保留副本核内容，不换当前SDK。

原固定素材候选Kenney来源3fa8a04b1c01ab23db43123d4ce814a34c3fc7f0；已有[许可定位](../../../ag-examples/examples/g10-textured-models/sources/kenney/README.md)、[声音派生许可](../../../ag-examples/examples/g12-services/hud/assets/bank-license.txt)仅作输入。声音bank SHA256 b0b740dc49e51abefff9bb1af830080fe00f817b468614992040d438d6171c3d，90060B/44100Hz/2ch/22504frames，jump[0,7403)/coin[7403,20046)/land[20046,22504)。字体LilitaOne SHA4444c23631884f411aa7f2fee35061b1756a9927940c62d2a5572acf470b3ffa/26828B；OFL/RFN SHA31d45880a38de46bc81835329c0c7d964609751e65add92769ea0095ad92c05b/4391B。复用前核实际文件/许可及配方；正式2D帧/敌人素材尚未制作，原GLB不是可直接运行的2D图集。

## 5. 详细设计

### 5.1 并行与实际交付门

T-01..04：独立核原合同/owner、建立唯一树/scope、素材与关卡/纯Auto函数/状态机及Node作者草稿。已交付组件可作隔离实验；对未交付组合只写文档化接口和明确假设，不报完整生成/游戏运行通过。UI032 T-02接口文档冻结后可按其revision对齐草稿，禁止读取实现tip/共享未交付SDK或target。

T-05硬门：核032实际落主commit、独立不同上下文final及冻结门/Spec来源、生成器和driver两图依赖/SDK681/toolchain/锁/工具、owner与清理记录，再固定正式source-build消费锁。缺任一必需证据停完整接线，T-01..04完成不抵扣门。遇公开端口缺口带最小反例回引擎规划，不在游戏改Rust或用私有导出绕过。

### 5.2 原关卡与每项要求

冻结dt=1/60、x右/y上、bounds x[0,30]/y[-4,12]；spawn(2,1)、half(.4,.5)，ground x[0,8]/[10,18]/[20,30]×y[-1,0]，platform x[12,15]/y[1,1.25]，墙x0/30、顶y10、坑fail y=-3。enemy x11..17/y.5/速度1，coin(4,1)/(13,2.25)/(24,1)，goal(28,1)/半径.5；speed4、gravity20、jump8、clearance.002；camera12×8跟随夹界。触发尺寸/地墙顶厚度、原路线/数值容差从原样本和UI011逐值登记，不由素材外观猜测。

| 原ID | 必需正常行为 | 区分反例/证据 |
|---|---|---|
| G2-01 | 左右运动、释放停止，失焦无遗留移动 | 反向/释放/blur的真实输入→Auto位移，非日志自报 |
| G2-02 | 接地一次跳、空中再按无二跳、重力落地 | held/再次pressed/平台边沿、独立f32轨迹 |
| G2-03 | 地墙顶阻挡、最终支撑、掉坑失败 | 顶撞/角/边缘/坑阈值，几何与实际像素 |
| G2-04 | 三个不同币各首次+1并真销毁 | 同Tick三件/重复触碰/旧代/重生，不能只hide |
| G2-05 | 敌人连续在原端点巡逻、接触失败 | 双方同时运动/端点折返，收集时不得停敌人 |
| G2-06 | 集齐到目标胜、未齐不胜、失败/获胜后fresh Enter新Run | 早目标/held/20轮复位、旧局状态句柄隔离 |
| G2-07 | 相机跟随并夹界，角色相机同Tick | 两端/宽高比letterbox/实际内容区像素 |
| G2-08 | idle/run/jump/fall与最后非零facing，敌人可辨 | 错状态/错帧/反朝向/透明空图负控，运动不只方块 |
| G2-09 | jump/coin每事件一次声音、HUD n/3与终局 | ordinal/PCM/字形ROI/实际native流，漏声重声错误计数真失败 |

只有Playing积分/巡逻/计数；Won/Failed冻结，fresh Enter请求accepted新Run后配置/计数/物品/敌人/相机/局部状态复位，Stop恢复原编辑Document/Undo，不清库冒充owner释放。根+Player+Enemy+三Coin+Goal+Boundary共8状态Node；Coin同定义独立model/handle/collected/receiver，根只协调计数/结果和显式顺序。纯资源/地台不占状态Node，数字slot/pair/scene ID只在生成层。

### 5.3 表现、资源与预算

玩家帧对应真实状态，敌人可辨且位置持续更新；保jump/coin音效，不强加新的胜败音效。资源具名引用，manifest记原始来源/版本/许可/路径/长度/SHA、离线派生配方/输入输出和像素尺寸/decoded内存。可用受检固定原件派生或原创，缺固定源先核历史副本，不替换当前上游；字体OFL/RFN和音效CC0/原配方随包。T-03制作资源是本游戏独立工作，不能宣称现成帧已满足。

保Callback32 credits、32物理lifecycle写、8状态Node/8slot/8pair、120base+8reserved=128、512潜在mesh、8资源身份/32MiBraw/单件8MiB、CPU/GPU各64MiB、4声音请求/8voice、4HUD槽/槽32ASCII。源码原256/96/352KiB、1000steps/2ms slice、100000steps/120resumes/250ms callback、init30s/tick2s和8ms pump目标保持；最终据032实际正式profile逐项核对硬门与性能目标，不把失败前缀时长算完整帧余量。默认游戏运行资源≤1MiB、引擎实测外游戏内容包增量≤2MiB为原规划目标，超出解释并回规划，不能删必要内容。

每Tick真实输入、角色运动/grounded、敌人推进、所有必要事件/销毁、视觉/声音/HUD计入同一个公共池，不能每Node另给32或把一个credits误作一VM指令。若032新增有界操作只用实际交付的新显式API/价目，游戏不自行免费化getter。原最高路线以及三币同Tick、Jump-land、coin+enemy+goal竞争、未齐目标/终局/重开分别实测；不改地图避峰值、不停走/停巡逻/隔帧延事件/漏第三条/静音过门。

### 5.4 编辑、启动、离线和故障

公开启动与源码选择真实使用固定生成器/runner，非test harness私有命令。编辑场景/参数→保存/SaveAs→关开→真实Run保持；改speed等Auto规则→显式再生→对照轨迹真实不同。保存Document与作者源分别管理，关开不能意外再生覆盖用户编辑；不承诺从Document反写Auto/双向同步。

ZIP含全部作者/生成物/锁/工具入口/运行依赖/资源manifest/许可/配方/操作说明；从A复制到无生产者树/target/网络的B，正式完整游戏真Run、仅闭包冷再生、获胜与失败重开、SaveAs。逐一破坏helper/scene/资源/许可/锁/工具/partial收据具名拒绝→精确恢复→同入口再Run。计源码/资源/引擎与压缩前后真实大小，LF/checkout-stable不依赖mtime。

资源缺失/非法API是明确入口故障，不把整帧回滚当语言全局规则。验证原既有profile共同接受/last-good、Pause/中性Step/fresh Enter与旧Run隔离。20轮Stop/newRun/churn后owner/弱引用和warm账平坦，声音不重播；物理扬声器/人工输入缺证具名，不用离屏图/虚拟设备假装真实可玩走查。

### 规范增量

| delta_id | add/modify/retire | docs/specs/... target | before/after rule | rationale | acceptance IDs |
|---|---|---|---|---|---|
| SD-01 | add | docs/specs/game2d.md | 无独立完整G2→普通Auto局部组件、公有固定引擎、原九项同程序及资源/编辑/离线/故障/预算证据 | 正式游戏独立于引擎夹具和Gallery | AC-01..06/08 |

## 6. 测试设计

新工具/夹具待work建立；下列不是当前通过。实现/内部/final人选未指定，开工核owner；独立final不同上下文，不创建agent。独立几何/状态/PCM/字形/资源oracle不得直接复制游戏公式当唯一期望；精确f32/接触阈值沿原约定。

| ID/AC/owner_stage | 不变量/合法与非法输入 | 入口/oracle/边界 |
|---|---|---|
| V-S01 / AC-01/02 / work | 原关卡/8局部Node/use/同定义三Coin与两个父receiver，数值参数传局部model/helper | 新作者校验/公开generator及真实Auto，改名重排/参数变化到目标；错scope/未解析变量/串状态真失败，无内容编译器 |
| V-S02 / AC-02/03 / work | 全G2-01..09、正常/失败/获胜/重开与原路线 | 新verify_game2d→公开Host/Auto/GPU/PCM+独立状态轨迹/像素/字形；错碰撞/早胜/漏币/错帧/重声变异真失败 |
| V-S03 / AC-03/04 / work | 三同Tick/Jump-land/敌人目标竞争与全部原额，32/33/旧代/第33物理写 | 实际正式profile计量/协议错误与原负控，不能少运动/少事件过门；完整执行量/性能目标分列 |
| V-S04 / AC-03/05 / work | fresh/held/blur/Pause/中性Step/Stop/20轮、坏资源/旧Run/声音释放 | 真实Host事件/Run/owner/弱引用和native音流，原Document/Undo保持；人工窗口走查记录实际输入路径和缺证 |
| V-S05 / AC-04/05 / work | manifest/资源配方/许可/actual source/SDK/工具/锁、改Auto/编辑保存关开 | 真实字节/hash/decoded/资源及源参数对照、SaveAs后内容和行为保持；错误工具/假SHA/篡改许可真拒绝 |
| V-S06 / AC-05/06 / work | ZIP A→B/无生产者无网络/仅闭包冷再生/坏件恢复 | 新package检查与B公开启动/真Run/两条完整流程，冷生成产物一致；不是zip列表或只解析manifest |

拟`python tools/verify_game2d.py --controls`、`python tools/package_game2d.py`和公开启动/冷再生命令均为新路径，T-02冻结准确CLI，T-05/06建立/运行；独占scope显式输出/target。T-01..04隔离检查不记录为V-S02..06完整通过。正式只跑本游戏和共享工具真实受影响case，不跑全AG或根语言测试。

## 7. 验收标准

| AC | owner_stage | 可观察关闭条件 | 验证 |
|---|---|---|---|
| AC-01 | work | 独立仓普通Node/use局部model/msg/on/具名资源，8状态内，无Rust玩法/作者数字绑定/私有运行入口 | V-S01 |
| AC-02 | work | 原G2-01..09固定参数与三币/敌人/完整胜败重开，同一真实程序通过，非演示拼接 | V-S01/02 |
| AC-03 | work | 输入/物理/相机/巡逻/状态帧/一次声音/HUD/新局同步，独立oracle与全部负控、20轮owner/last-good保持 | V-S02..04 |
| AC-04 | work | 实际032交付/独立final/Spec/工具/SDK681固定来源，原服务/物理写/节点/资源/VM包络和完整最高分支实测 | V-S03/05 |
| AC-05 | work | 素材/字体/声音许可/配方/资源验证、公开启动/源码编辑变化/保存关开/SaveAs及缺件拒绝成立 | V-S04..06 |
| AC-06 | work | 完整离线ZIP A→B/冷再生/两条流程与恢复后真Run，SD候选、操作/尺寸/性能/具名缺证摘要移交 | V-S06 |
| AC-07 | review | 同树独立上下文final逐AC/源码diff/SD/遗漏延期workaround/告警审查，finding回work复核pass并绑定revision | T-07 |
| AC-08 | merge | 冻结定向门/来源核后实际合主，canonical SD-01核来源/字节、归档导航，游戏交付不冒称M2全部完成 | T-08/09 |
| AC-09 | merge | fresh guard清自有树/分支/空组、全部输出对账/摘要折Plan/删scope构建物、具名hold与最终收据登记 | T-10 |

## 8. 执行步骤

| T | owner_stage | 依赖 | 写面/可验证结果 | AC | 进度 |
|---|---|---|---|---|---|
| T-01 | work | 用户启动；无032交付硬门 | 核原合同/owner/公共已交付来源、唯一树和scope登记，冻结准备范围 | AC-01/04 | [ ] |
| T-02 | work | T-01 | 冻结原G2/逐项oracle/资源许可/布局/准确CLI；032接口若未冻结则列有界假设，不写正式消费锁 | AC-01/02/05 | [ ] |
| T-03 | work | T-02；不等032落主 | 制作受检2D玩家/敌人等资源、配方/许可/manifest、关卡数据；独立素材/尺寸检查 | AC-02/05 | [ ] |
| T-04 | work | T-02；可与T-03交错 | 纯Auto运动/巡逻/收集状态机/helper与局部Node作者草稿/反例，固定文档接口revision，非完整运行通过 | AC-01/02 | [ ] |
| T-05 | work | T-03/04；032实际交付/独立final/冻结Spec及工具来源 | 固定正式锁/公开启动与生成，完成真实全链，拒绝读开发tip/内容补引擎 | AC-01..05 | [ ] |
| T-06 | work | T-05 | 全G2/峰值/音画像素/20轮/编辑变化/离线A→B/冷再生/坏件恢复与SD候选 | AC-01..06 | [ ] |
| T-07 | review | T-06 | 同权威树独立final，finding回work同员复核，精确revision/输入绑定 | AC-07 | [ ] |
| T-08 | merge | T-07 pass | 冻结定向并集/来源，实际合master；不擅自发布/打M2标签 | AC-08 | [ ] |
| T-09 | merge | T-08 | canonical SD-01核字节/来源、归档/导航/两游戏索引定位，区分单游戏与M2总状态 | AC-08 | [ ] |
| T-10 | merge | T-09 | fresh guard/全输出对账、清自有树/分支/scope/构建物，具名hold及最终hash登记 | AC-09 | [ ] |

## 9. 复审记录

2026-11-02 / stage: new / plan_id: ag-platformer-2d/PLAN-001 / plan_revision: 1 / outcome: pass（规划可审阅；T-01..04可在用户启动后并行，T-05仍blocked待032实际交付） / next: 用户启动后work T-01/T-02。0/10。仅新建本地管理仓/设计/合同，没有游戏实现、素材制作、探针、构建、远端或实施树；不是可行性go/游戏运行通过/独立final。本地独占核空仓号源，001取号后next002，不借用Gallery编号。

2026-11-02三线规划静态预检：三合同均0..10节、10T/9AC/6V-S/1SD，work6/review1/merge3、drafting0/10与阶段门一致；AG013原25名及顺序逐字保持，G2原九项/原几何与预算不减。241个当前管理文档本地链接经核（含历史归档定位修正）；本轮新增引用无断链。活动/归档编号唯一，UI next033（031为其他owner已保留号）、AG next014、游戏next002。metadata实际生成路径16/22，`python tools/gallery.py validate --all`退出0、12逻辑项/22入口/许可一致；022/025/030 canonical SHA与引用一致。未创建三计划实施树、提案canonical Spec、游戏源/素材/探针/构建/GPU/agent。以上仅规划/目录验证，不是实际新链可行性go、游戏运行验收或独立final。

## 10. 待澄清事项

| ID | 事项 | owner/关闭动作 |
|---|---|---|
| D-01 | 032实际正式接口/来源交付 | work T-02记录文档接口revision，T-05核实际delivery/独立final/Spec/工具/SDK681；缺失停完整接线 |
| D-02 | 固定原件/真正2D帧和全部许可闭包 | work T-03核受检输入/派生/尺寸/来源，缺历史副本不替换当前上游 |
| D-03 | 完整G2/声音峰值原额与数值参数局部传递 | work T-04..06真实全链/负控，不能继承AG012未解析参数变通为永久限制；缺公共能力回引擎规划 |
| D-04 | 人工可玩/物理声学与OS暂停、final上下文 | work/review分别核真实证据，必需项缺失不能计PASS，不创建agent或自动焦点输入 |

材料唯一D:/autostack/plan-artifacts/plan-001/ag-platformer-2d/，开工登记owner/用途/在途；所有临时输出/外部安装/发行包/target显式归scope，禁止attachments/第二暂存区。merge摘要折Plan后逐项对账所有实际输出并删本仓自有scope/构建物；同号他仓scope不动，父目录仅确认空才清，仅具名未解决问题记录owner/理由/关闭条件持有。禁止worktree链接，清理先fresh D:/autostack/wt-guard.sh；旧specs.json只读，canonical仅review/merge后沉淀。
