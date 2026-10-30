# 2026 Q3–Q4 具身智能头部技术战略：Google DeepMind × 阿里 Rynn × Figure AI

> 更新时间：2026-10-30 · 证据口径：以企业官方技术博客、论文/项目主页和开源仓库为主。指标仅比较各自实验，**不跨不同 benchmark 排行**。本报告不包括已独立成篇的 NVIDIA GTC 和智元 AI WAVE 专题。

## 执行摘要

| 企业 | 当前主线 | 代表性发布 | 主要突破 | 更适合关注的研发对象 |
|---|---|---|---|---|
| Google DeepMind | Physical Reasoning + Coding Agent + Robotics ER | Gemini 4 Argon（10/13）、Gemini Robotics ER 2 企业预览（10/27） | 图像/视频 → 自动重建物理仿真 → 生成课程/数据 → VLA 微调；高层多机器人/技能编排 | Agentic Robot Learning、可复现 Agent 自动研发、Active Perception |
| 阿里巴巴达摩院 Rynn | 统一具身大脑 + 无原生动作标签预训练 + 可控世界模型 | RynnUnify（10/26）、RynnVLA-Latent（10/27）、RynnWorld-Latent（10/28） | 3D-grounded latent action 贯通人类/机器人/仿真视频，分两阶段适配机器人本体 | VLA 数据拓展、世界模型生成、RoboTwin 2.0 泛化 |
| Figure AI | 人类行为数据飞轮 + 神经策略泛化 + 规模化训练与部署 | Index（8/25）、Nscale 算力合作（9/3）、Helix 2.5（9/17） | 相同任务微调数据下 Index 预训练将 30 个陌生家庭完整任务成功率从 9% 提升至 56% | 数据多样性、端到端完成判定、真实长程泛化 |

**核心判断**：Google 让 Agent 成为机器人研发工程师；阿里让不同本体的动作学习共享潜在表征；Figure 用海量人类行为数据和真实陌生环境验证模型泛化。三者不是同一条模型竞赛路线。

## 一、Google DeepMind：从 Coding Agent 到物理世界学习与部署

### 1.1 2026 年时间线和模块分工

- 2026-07-30：Gemini Robotics ER 2 正式介绍，高层具身推理模块；自然语言/视频感知、任务分解，调用低层 VLA、导航等工具。
- 2026-10-13：Gemini 4 Argon for Robotics。通用物理推理/代码智能体应用于 MuJoCo 任务重建、机器人控制、数据合成与硬件自我改进。
- 2026-10-27：ER 2 在 Google Cloud 进入公共预览。可通过 API 工具编排、多机器人调度、视频理解与生命周期管理接入企业系统。
- **注意区别**：Argon ≠ ER 2 ≠ 底层 VLA；Argon 是能力广泛的通用推理/编码模型，ER 2 是高层机器人具身推理 VLM，低层运动由独立动作策略或 API 执行。

### 1.2 关键可复现实验：Argon 让物理仿真自动产生训练数据

**输入**：一张双 Franka FR3 机械臂桌面工作空间 RGB 图像；实验涉及九个道具、四路 RGB 相机。

**Agent 目标**：建立准确的 MuJoCo 模型（几何、碰撞、物性与复位）、定义 77 个单/双臂任务（抓取、翻正、定向推动、空中交换、扫拢、并行清台等）、合成闭环 IK 轨迹、进行随机初始姿态扰动（公开 prompt 为 ±10cm）、用 MuJoCo reward 验证，导出 4,500+ 条 Episode 微调通用 VLA。

**结果**（厂商在特定实验中的对照）：真机成功率 56% → 75%（+19 个百分点）；完成时间 35s → 24s（约降低 31.4%）。

~~~mermaid
flowchart TD
  A[真实 RGB 图/多视角执行日志] --> B[Gemini 4 Argon / Research + Coding Agent]
  B --> C[自动生成 MuJoCo 数字孪生/资产物性/相机]
  C --> D[77 任务课程/随机化/IK 轨迹]
  D --> E[物理验证/4,500+ 合成 Episodes]
  E --> F[VLA 微调]
  F --> G[独立真实机器人评测]
  G -->|失败日志与新观测| B
~~~

**与其他演示的区别**：

1. **Real2Sim**：Argon 从真实操作录像建立仿真，优化视觉一致性与触觉力方向/大小的一致性；官网 prompt 明确不能作弊修改实时物体 qpos 或关闭碰撞。
2. **Sim2Real**：不是只生成视频，而是产生具有物理验证的机器人训练轨迹。
3. **在线代码自修复**：SO-101 视觉抓取实验展示多轮自我诊断，时间从 58.9s → 22.9s → 17.4s；这是单案例视频，不是成功率统计。
4. **论文复现**：通过阅读机器人论文构建 MuJoCo WASM 浏览器实验，验证论文控制参数和任务进展；证明部分研发流程自动化，不等于复现实验的每项结果与原论文完全等价。

### 1.3 验证问题

- 物理接触真实性是否通过未见资产、摩擦、夹爪尺寸独立测试？
- 数据中合成标签与真实执行的差距是否有量化？
- 优化来自更多数据、更好的课程，还是更大的计算预算？
- 自动生成的代码在隔离容器/仿真中运行，是否由冻结规则/安全门禁约束？
- 从工具生成代码到 VLA 参数微调，哪些步骤人工介入？

**对现有平台适配建议**：采用 Isaac Lab 代替 MuJoCo 也可以验证类似闭环，但需要以标准化物理测试验证生成的场景资产；先在药房抓取/翻转/传送带和样本操作里自动产生课程，优先统计未见初始状态的改善与单位 GPUh 收益。

**来源**：
- [Google Developers — Gemini 4 Argon for Robotics](https://developers.googleblog.com/en/gemini-4-argon-for-robotics/)（2026-10-13，含原始演示视频与实验 prompt）
- [Google DeepMind — Gemini Robotics ER 2](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/gemini-robotics-er-2/)（2026-07-30）
- [Google Cloud — Gemini Robotics ER 2 企业预览](https://cloud.google.com/blog/products/ai-machine-learning/gemini-robotics-embodied-reasoning-2-is-now-available-on-google-cloud)（2026-10-27）
- [Google ER 2 官方模型说明](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/gemini/robotics-er-2)

## 二、阿里 Rynn：统一具身大脑、潜在动作与跨本体世界模型

### 2.1 三项发布不是三个孤立竞争模型

| 发布 | 模型/训练路线 | 解决的核心问题 | 数据与结果口径 |
|---|---|---|---|
| RynnUnify（10/26） | 16B，8B Reasoner + 8B 视频 Generator，联合注意力；Agentic 视频工具选择；world-action 扩展 | 理解、视觉预测和动作决策脱节 | Rynn-VP 比 Cosmos 3 Nano 高 9.75 分；Agentic extension Rynn-GEU 比直接推理高 6.0 分；特定 20 个 RoboCasa365 复合任务成功 51.5%，三类实机任务平均 46.7% |
| RynnVLA-Latent（10/27） | RynnLAM 从视觉转移中自监督获得连续 3D-grounded latent action；flow matching VLA 预训练，Stage 2 本体专用后训练 | 人类视频缺原生机器人动作标签、机器人之间动作空间不兼容 | 30.1k h 混合视频，745.52M latent 描述；4B 报告 LIBERO 98.8%，LIBERO-Plus 84.7%，VLABench 51.9%，RoboTwin2.0 88.6% |
| RynnWorld-Latent（10/28） | 统一潜在动作条件视频世界模型；数字遥操作与视频编辑生成 | 让世界模型从「预测」升级为数据生产 | 23 数据集、约 553.5M 帧；合成数据在其特定实验中改善训练效果 |

### 2.2 统一架构

~~~mermaid
flowchart TD
  A[真实机器人、人类第一视角、仿真视频] --> L[RynnLAM: 3D Grounded Latent Actions]
  L --> V[RynnVLA-Latent: Latent Chunk 预测与动作学习]
  V --> P[Stage 2: 本体专用动作专家/后训练]
  L --> W[RynnWorld-Latent: 跨本体可控未来视频]
  W --> S[合成动作-视频数据/任务覆盖]
  S --> V
  R[RynnUnify: 理解 + 视频推演 + Agentic Reasoning] --> C[高层任务决策]
  C --> P
  P --> E[真实操作/评测]
  E --> A
~~~

**注意**：该图是研究上可组合的参考架构，三项论文并未正式声明已经以这条完整系统调用链统一部署。

### 2.3 关键技术机制

**RynnUnify**：将理解模型与视频生成模型放入共同框架，使用交织式视频—语言推理进行长程规划；Agentic extension 学习何时值得调用视频预测，而不是每一步都支付完整未来生成成本。独立控制扩展体现从「想象」到「动作」的桥接。

**RynnLAM**：不是直接把人类手的像素变化等同于机械臂关节动作，而是从相邻帧学习与控制相关的 3D 潜在变化。用相机运动补偿和残差未来特征监督减轻视角与外观干扰。随后机器人本体的真实动作标注仍需用于 Stage 2 适配。

**RynnWorld-Latent**：以初始图像和潜在动作序列生成未来视频，一条路线输入目标本体机器人动作做数字遥操作，另一条路线以视频起始帧编辑 + 潜在动作重用合成轨迹。物理真实性与稳定碰撞仍需实机/仿真验证。

### 2.4 开源核查与研究提示

- [RynnUnify 项目页](https://alibaba-damo-academy.github.io/RynnUnify.github.io/) · [论文](https://arxiv.org/abs/2610.32965)
- [RynnVLA-Latent 代码](https://github.com/alibaba-damo-academy/RynnVLA-Latent) · [论文](https://arxiv.org/abs/2610.34356)
- [RynnWorld-Latent 代码](https://github.com/alibaba-damo-academy/RynnWorld-Latent) · [论文](https://arxiv.org/abs/2610.36791)
- **重要**：RynnVLA-Latent 仓库的 2B/4B Stage 1 权重仅产生潜在动作，不是闭环实机动作策略；需执行 Stage 2 本体对齐训练，不能把预训练权重直接投入 RoboTwin 测评。
- 数据集、训练预算、仿真协议的差异使其 88.6% 不可直接与其他 RoboTwin2 Clean/Random 结果比较。

**对现有研发建议**：优先尝试在现有 RoboTwin2/机械臂环境运行官方 sample 数据/CPU tests，再小规模验证潜在动作标签是否改善遮挡、物体位置扰动与新对象泛化；世界模型作为后续可选数据生成层，不作为首要重训目标。

## 三、Figure：Index 人类经验数据飞轮与 Helix 2.5 泛化

### 3.1 战略分层

1. **Index（2026-08-25）**：真实世界人类行为视频采集 App → 质量过滤、反欺诈、去重、数据重平衡、层级描述 → 大规模预训练。
2. **Helix 2.5（2026-09-17）**：从 Index 预训练基础模型，使用任务专用数据适配三种行为，再在 30 个陌生家庭、未见物体上做无场景适配评测。
3. **算力扩张（2026-09-03）**：Nscale 合作潜在上限 100,000 个 NVIDIA Vera Rubin GPU，初期部署目标自 2027 下半年开始；最初计算承诺 35 亿美元，拟扩大至 60 亿美元以上。**这些为协议/计划，不是 2026 年已上线的 GPU 数量。**
4. **真实部署**：Figure 03 在 BMW 环境进行新的物流/流程操作演示，属于厂商部署声明，不足以证明家庭场景已商业化。

### 3.2 Index 数据体系

官方 8 月 25 日披露：超过 26.4 万次 App 下载、100+ 国家、约 4.4 万周活跃贡献者、超过 1600 万条上传视频，当时每秒处理约 30 分钟人类视频；9 月的 Nscale 合作稿将采集量更新至 35 分钟/秒。两次口径/时间不同，不应混写。

数据治理五环：过滤 → 反欺诈审查 → 去重 → 按任务/嵌入重平衡 → 分层文本标注。视频规模不是有效数据规模，需关注物理交互和任务多样性覆盖。

### 3.3 Helix 2.5 的真实评测

- 三种行为：客厅收纳、毛巾折叠、铺床；
- 30 个湾区陌生家庭，**没有在这些评测家庭及目标物体上采集、微调或适配**；
- 同一个 Index 预训练基础模型分别适配三种行为，每类行为使用冻结 checkpoint；不是「三项任务绝对无需任务数据」；
- 冻结任务数据、架构、优化和评测，仅比较 Index 预训练：**完整任务成功率 9% → 56%**（厂商盲测报告）。任务成功需全部玩具入篮、全部毛巾折好入篮或床铺符合既定标准，不给部分分；
- 相比代表性 Helix 02 行为，新路线在任务特定训练数据使用量减半时达到同等级性能，但对象是跨 30 个未见家庭；
- 需要进一步查看完整每任务 trial 数、置信区间、失败模式、人工干预与重试条件。

~~~mermaid
flowchart TD
  A[Index: 大规模人类行为视频] --> B[去重/质量/多样性/层级标注]
  B --> C[Helix 2.5 基础模型预训练]
  C --> D[针对收纳/折毛巾/铺床的任务适配]
  D --> E[30 个陌生家庭/冻结 checkpoint]
  E --> F[完整任务成功率/主动感知/错误恢复]
  F --> G[未见环境失败类型 → 下一轮数据与训练]
~~~

### 3.4 与自己的上半身研发有什么关系？

不用复现下半身或全身运动控制，最值得迁移的是 **真实环境泛化实验设计**：

- 从一个药房/样本库固定位置扩展至不同货架、物体分布、遮挡、相机和工具配置；
- 用「从未见过的真实初始状态」而不是常规相同任务复位来检验 VLA；
- 通过人类示范与模拟数据覆盖多样性，而不是无限重采同一种成功动作；
- 把任务成功设为业务终态（药盒方向、目标位置、条码/样本核验等），不能只看单动作成功率。

**来源**：
- [Figure — Introducing Index](https://www.figure.ai/news/introducing-index)（2026-08-25）
- [Figure — Helix 2.5](https://www.figure.ai/news/helix-2-5-zero-shot-30-home-generalization)（2026-09-17，含原始演示视频、统计与消融）
- [Figure — Nscale 算力合作](https://www.figure.ai/news/figure-and-nscale-sign-strategic-partnership)（2026-09-03）
- [Figure 03 at BMW](https://www.figure.ai/news/f-03-at-bmw)（2026-06-30）
- [Figure — Helix 02](https://www.figure.ai/news/helix-02)（2026-01-27）

## 四、跨企业对比：不同公司在解决什么瓶颈？

| 维度 | Google | 阿里 Rynn | Figure |
|---|---|---|---|
| 第一性问题 | 机器人研发和训练流程人工成本高 | 动作标签稀缺、机器人本体动作空间不统一 | 真实世界数据覆盖不足、陌生环境泛化弱 |
| 优先能力 | Coding Agent + Real2Sim + Data Engine + 高层 ER | Latent Action + Unified Brain + 可控视频世界模型 | 人类数据 Index + Helix 全身策略 + 规模部署 |
| 数据依赖 | 少量真实观测 → 仿真合成 | 30.1k h 混合视频 / 23 数据集世界模型 | 大规模人类行为视频 + 任务专用适配数据 |
| 评测证据 | Argon 特定台面 VLA 真机 56→75%；ER 2 是企业 Preview | 4B RoboTwin2.0 88.6%；RynnUnify 指定实机任务 46.7% | 30 陌生家庭任务完整成功 9→56% |
| 开放方式 | 模型/API + 官方视频与 prompt，完整机器人训练管线不是直接一键开源包 | 论文、项目页与部分代码/权重；Stage 2 需要本体适配 | 官方演示/数据战略，Helix/Index 训练资产不等同完整开放 |
| 与上半身项目的适配优先级 | **P0**：Coding Agent 自动生成任务数据与实验 | **P0/P1**：潜在动作与数据增强；先小规模基线 | **P1**：陌生环境评测与多样性数据治理 |

## 五、研发路线（不投入人形下半身）

**0–2 周 / Agentic Simulation Builder**：冻结 Isaac Lab 药房抓取、翻转、传送带和样本技能基线，定义统一 reset/observation/action/reward/verifier；接入 Codex/Claude Code 生成任务分布、仿真资产参数、失败干预与候选策略，记录 Git diff、种子、GPUh、失败日志。

**2–4 周 / 自主实验与技能提升**：Codex/Claude 自动提出抓取/接触失败修复方案；将 Code-as-Policy 与 BC/RL/VLA 微调分别归因，新增技能进入有测试覆盖的 Skill Registry；通过冻结 OOD 测试才晋升版本。

**4–6 周 / 数据表示探索**：在 RoboTwin2 选少量任务复现 RynnLAM latent action 的标注或训练结构，对比单纯数据增强；检查机器人动作映射损失、已知/未知物体和不同视角泛化。

**6–8 周 / 分布外可靠性评价**：借鉴 Helix 2.5，设置独立的陌生场景/任务和业务终态验收，固定重试次数和时间预算；结果同时报成功率、恢复率、人工介入、工作量与单位改进成本。

### 实验公平性与安全

训练 Agent 不得修改冻结测试集、通过标准或真实机器人安全边界。所有候选代码先隔离仿真运行，实机部署必须由人审或明确安全门禁决定；部署后的自学习需要策略版本、日志审计和回滚。不要把多次试错、更长上下文与额外计算简单算作模型泛化能力提升。

## 六、阅读入口与后续跟踪

- [Google Argon 官方视频与实验 Prompt](https://developers.googleblog.com/en/gemini-4-argon-for-robotics/)
- [Google ER 2 Cloud Preview](https://cloud.google.com/blog/products/ai-machine-learning/gemini-robotics-embodied-reasoning-2-is-now-available-on-google-cloud)
- [RynnUnify 项目页](https://alibaba-damo-academy.github.io/RynnUnify.github.io/)
- [RynnVLA-Latent 项目页](https://alibaba-damo-academy.github.io/RynnVLA-Latent.github.io/)
- [RynnWorld-Latent 项目页](https://alibaba-damo-academy.github.io/RynnWorld-Latent.github.io/)
- [Figure Helix 2.5 原始演示](https://www.figure.ai/news/helix-2-5-zero-shot-30-home-generalization)
- [Figure Index 数据战略](https://www.figure.ai/news/introducing-index)

> 研究依据截至 2026-10-30。项目状态、开源范围、模型版本可能变化。公布的单项 benchmark 不能代表完整产业部署效果。
