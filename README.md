# 具身智能论文技术演进趋势与算法核心原理分析报告

> **2026-10-27 最新研究专题：** [GTC Berlin 2026 具身智能技术洞察与后续研发路线](研究洞察/GTC_2026_Berlin_具身智能与后续研发路线.md) — Isaac Lab 3.0、Isaac OS、Microduck Agent、Embodied Autoresearch、VLA 纠偏与 8 周路线图。

> 分析范围：625篇论文（2025-2026年arXiv具身智能方向）
> 生成时间：2026年6月

## 一、论文主题分布

| 类别 | 论文数 | 2025 | 2026 |
|------|--------|------|------|
| VLA基础模型 | 254 | 212 | 42 |
| 灵巧操作与抓取 | 180 | 166 | 14 |
| 强化与模仿学习 | 122 | 115 | 7 |
| 数据集与基准 | 105 | 99 | 6 |
| 导航与运动 | 94 | 90 | 4 |
| 3D与空间推理 | 75 | 71 | 4 |
| 其他 | 68 | 65 | 3 |
| 世界模型 | 58 | 42 | 16 |
| 安全与对齐 | 57 | 53 | 4 |
| 扩散策略与流匹配 | 40 | 38 | 2 |
| 表示学习与技能 | 36 | 32 | 4 |
| 综述 | 29 | 27 | 2 |
| 人机交互 | 20 | 20 | 0 |

---

## 二、VLA基础模型 (254篇)

### 2.1 代表性VLA模型（按年份排列）

| 模型名 | 年份 | 标题 |
|--------|------|------|
| World-VLA-Loop | 2026 | World-VLA-Loop: Closed-Loop Learning of Video World Model and VLA |
| VLM4VLA | 2026 | VLM4VLA: Revisiting Vision-Language Models in Vision-Language-Act |
| VLAW | 2026 | VLAW: Iterative Co-Improvement of Vision-Language-Action Policy a |
| VLANeXt | 2026 | VLANeXt: Recipes for Building Strong VLA Models |
| VLA-JEPA | 2026 | VLA-JEPA: Enhancing Vision-Language-Action Model with Latent Worl |
| StarVLA | 2026 | StarVLA: Reducing Complexity in Vision-Language-Action Systems |
| StarVLA | 2026 | StarVLA: A Lego-like Codebase for Vision-Language-Action Model De |
| SimVLA | 2026 | SimVLA: A Simple VLA Baseline for Robotic Manipulation |
| ROSClaw projecthttps | 2026 | ROSClaw projecthttps://www.rosclaw.io/ codehttps://github.com/ros |
| RDT2 | 2026 | RDT2: Exploring the Scaling Limit of UMI Data Towards Zero-Shot C |
| Qwen-VLA | 2026 | Qwen-VLA: Unifying Vision-Language-Action Modeling across Tasks,  |
| PokeVLA | 2026 | PokeVLA: Empowering Pocket-Sized Vision-Language-Action Model wit |
| MemER | 2026 | MemER: Scaling Up Memory for Robot Control via Experience Retriev |
| LangForce | 2026 | LangForce: Bayesian Decomposition of Vision Language Action Model |
| LDA-1B | 2026 | LDA-1B: Scaling Latent Dynamics Action Model via Universal Embodi |
| LAP | 2026 | LAP: Language-Action Pre-Training Enables Zero-shot Cross-Embodim |
| HBVLA | 2026 | HBVLA: Pushing 1-Bit Post-Training Quantization for Vision-Langua |
| GigaWorld-Policy | 2026 | GigaWorld-Policy: An Efficient Action-Centered World--Action Mode |
| From Pixels to Tokens | 2026 | From Pixels to Tokens: A Systematic Study of Latent Action Superv |
| Fast-WAM | 2026 | Fast-WAM: Do World Action Models Need Test-time Future Imaginatio |
| EgoScale | 2026 | EgoScale: Scaling Dexterous Manipulation with Diverse Egocentric  |
| DynamicVLA | 2026 | DynamicVLA: A Vision-Language-Action Model for Dynamic Object Man |
| DreamDojo | 2026 | DreamDojo: A Generalist Robot World Model from Large-Scale Human  |
| DiT4DiT | 2026 | DiT4DiT: Jointly Modeling Video Dynamics and Actions for Generali |
| DM0 | 2026 | DM0: An Embodied-Native Vision-Language-Action Model towards Phys |
| Cosmos Policy | 2026 | Cosmos Policy: Fine-Tuning Video Models for Visuomotor Control an |
| CaP-X | 2026 | CaP-X: A Framework for Benchmarking and Improving Coding Agents f |
| ACoT-VLA | 2026 | ACoT-VLA: Action Chain-of-Thought for Vision-Language-Action Mode |
| ABot-M0 | 2026 | ABot-M0: VLA Foundation Model for Robotic Manipulation with Actio |
| villa-X | 2025 | villa-X: Enhancing Latent Action Modeling in Vision-Language-Acti |
| mimic-video | 2025 | mimic-video: Video-Action Models for Generalizable Robot Control  |
| cVLA | 2025 | cVLA: Towards Efficient Camera-Space VLAs |
| X-VLA | 2025 | X-VLA: Soft-Prompted Transformer as Scalable Cross-Embodiment Vis |
| WorldVLA | 2025 | WorldVLA: Towards Autoregressive Action World Model |
| World4Omni | 2025 | World4Omni: A Zero-Shot Framework from Image Generation World Mod |
| World-Env | 2025 | World-Env: Leveraging World Model as a Virtual Environment for VL |
| WMPO | 2025 | WMPO: World Model-based Policy Optimization for Vision-Language-A |
| VideoVLA | 2025 | VideoVLA: Video Generators Can Be Generalizable Robot Manipulator |
| VTLA | 2025 | VTLA: Vision-Tactile-Language-Action Model with Preference Learni |
| VQ-VLA | 2025 | VQ-VLA: Improving Vision-Language-Action Models via Scaling Vecto |
| VLA-Touch | 2025 | VLA-Touch: Enhancing Vision-Language-Action Models with Dual-Leve |
| VLA-Reasoner | 2025 | VLA-Reasoner: Empowering Vision-Language-Action Models with Reaso |
| VLA-RL | 2025 | VLA-RL: Towards Masterful and General Robotic Manipulation with S |
| VLA-RFT | 2025 | VLA-RFT: Vision-Language-Action Reinforcement Fine-tuning with Ve |
| VLA-Cache | 2025 | VLA-Cache: Towards Efficient Vision-Language-Action Model via Ada |
| VLA-Adapter | 2025 | VLA-Adapter: An Effective Paradigm for Tiny-Scale Vision-Language |
| VLA-0 | 2025 | VLA-0: Building State-of-the-Art VLAs with Zero Modification |
| UniVLA | 2025 | UniVLA: Learning to Act Anywhere with Task-centric Latent Actions |
| UP-VLA | 2025 | UP-VLA: A Unified Understanding and Prediction Model for Embodied |
| TwinVLA | 2025 | TwinVLA: Data-Efficient Bimanual Manipulation with Twin Single-Ar |

### 2.2 VLA技术演进趋势

| 技术方向 | 2025 | 2026 | 趋势 |
|----------|------|------|------|
| 规模化扩展 | 52 | 17 | ↑ |
| 推理能力增强 | 49 | 8 | → |
| 后训练/RL微调 | 34 | 7 | → |
| 空间推理增强 | 29 | 5 | → |
| 开放词汇操作 | 23 | 2 | → |
| 3D感知VLA | 19 | 4 | → |
| 实时推理加速 | 19 | 2 | → |
| 层次化策略 | 12 | 2 | → |
| Flow Matching动作生成 | 9 | 3 | ↑ |
| Diffusion Transformer动作头 | 6 | 3 | ↑ |
| 闭环控制 | 6 | 3 | ↑ |
| 潜在动作空间 | 3 | 5 | ↑↑ |
| 记忆机制 | 5 | 3 | ↑↑ |
| 量化部署 | 3 | 2 | ↑↑ |
| MoE混合专家 | 5 | 0 | ↓ |
| 模型蒸馏 | 3 | 1 | ↑ |
| 逆动力学预测头 | 2 | 2 | ↑↑ |

### 2.3 VLA核心算法原理


VLA（Vision-Language-Action）是2025-2026具身智能的**核心架构范式**，统一架构由三大模块组成：

**1. 视觉编码器（Vision Encoder）**
- 主流：SigLIP/CLIP ViT-L（预训练视觉-语言对齐表征）
- 演进：2D图像 → 多帧视频（4D-VLA）→ 3D点云/深度图（PointVLA, 3D-VLA）→ 3D高斯泼溅
- 关键创新：SpatialVLA引入空间感知视觉特征，DexGraspVLA增加深度通道

**2. 语言模型主干（LLM Backbone）**
- 主流：LLaMA-2/3 7B, Qwen2 7B（开源VLA）或更大闭源模型（π0, Gemini Robotics）
- 核心范式之争：
  - **离散动作token**（RT-2/OpenVLA）：将动作量化为离散token，用LLM自回归生成。简单但动作精度受限
  - **连续动作流**（π0/FlowPolicy）：用Flow Matching或Diffusion生成连续动作分布。精度高但计算量大
  - **逆动力学预测**（PIDM/CLIP-RT）：给定(s_t, s_{t+1})预测中间动作a_t。训练信号更强，可利用大量无标注视频
  - **潜在动作空间**（LDA-1B/LAP）：将动作编码到潜在空间，跨embodiment泛化

**3. 动作解码头（Action Head）**——2025-2026的核心战场
- **Diffusion Transformer Head**：去噪网络生成动作，适合多模态动作分布（67篇VLA使用）
- **Flow Matching Head**：连续归一化流生成动作，1-4步推理（vs 扩散10-100步）
- **Inverse Dynamics Head**：预测状态转移间的动作，可从视频中学习
- **Latent Action Head**：在压缩潜在空间预测，减少动作维度、跨机器泛化

**2025→2026关键演进**：
- 3D感知从"加分项"→"标配"（2D→3D点云/深度/高斯泼溅）
- 推理能力：Chain-of-Thought + VLA = ThinkAct/ACoT-VLA，先推理再行动
- 闭环控制取代开环：World-VLA-Loop，世界模型预测→VLA执行→验证→修正
- 后训练RL微调（TGRPO/SRPO）：BC预训练→RL微调，类比LLM的SFT→RLHF
- 模型压缩：HBVLA 1-bit量化，VLA-Cache token缓存，PokeVLA端侧部署

## 三、扩散策略与流匹配 (40篇)

### 3.1 代表性工作

- Learning to Group and Grasp Multiple Objects (2025)
- S2-Diffusion: Generalizing from Instance-level to Category-level Skills in Robot (2025)
- Responsive Noise-Relaying Diffusion Policy: Responsive and Efficient Visuomotor  (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- RA-DP: Rapid Adaptive Diffusion Policy for Training-Free High-frequency Robotics (2025)
- Dita: Scaling Diffusion Transformer for Generalist Vision-Language-Action Policy (2025)
- H3DP: Triply-Hierarchical Diffusion Policy for Visuomotor Learning (2025)
- NavDP: Learning Sim-to-Real Navigation Diffusion Policy with Privileged Informat (2025)
- A Practical Guide for Incorporating Symmetry in Diffusion Policy (2025)
- FLARE: Robot Learning with Implicit World Modeling (2025)
- Learning Generalizable Robot Policy with Human Demonstration Video as a Prompt (2025)

### 3.2 核心原理


**扩散策略（Diffusion Policy）**将动作生成建模为去噪扩散过程：
1. 前向加噪：将专家轨迹逐步加高斯噪声 a_t ~ N(√ᾱ_t·a_0, (1-ᾱ_t)I)
2. 反向去噪：训练网络ε_θ预测噪声，从随机噪声逐步恢复动作
3. 动作分块（Action Chunking）：一次生成未来H步动作，提高时序一致性

**Flow Matching**是扩散的替代范式：
- 用连续归一化流（CNF）建立简单分布→动作分布的ODE映射
- 推理只需1-4步（vs 扩散10-100步），速度大幅提升
- 代表：FlowPolicy（Consistency Flow）、3D Flow Diffusion Policy

**2025→2026演进**：
- 扩散骨干从U-Net→DiT（Diffusion Transformer），scalability更强
- Flow Matching兴起，逐步替代扩散成为更高效的动作生成方案
- 层次化扩散（Hierarchical Diffusion Policy）：高层语义规划+低层扩散执行
- Consistency Model实现单步动作生成，接近实时
- 扩散+流混合：先用流快速粗生成，再用扩散精修

## 四、世界模型 (58篇)

### 4.1 代表性工作

- Cosmos World Foundation Model Platform for Physical AI (2025)
- Robotic World Model: A Neural Network Simulator for Robust Policy Optimization i (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- WMNav: Integrating Vision-Language Models into World Models for Object Goal Navi (2025)
- AdaWorld: Learning Adaptable World Models with Latent Actions (2025)
- EWMBENCH: Evaluating Scene, Motion, and Semantic Quality in Embodied World Model (2025)
- FlowDreamer: A RGB-D World Model with Flow-based Motion Representations for Robo (2025)
- LaDi-WM: A Latent Diffusion-based World Model for Predictive Manipulation (2025)
- DreamGen: Unlocking Generalization in Robot Learning through Video World Models (2025)
- FLARE: Robot Learning with Implicit World Modeling (2025)
- Evaluating Robot Policies in a World Model (2025)
- 3DFlowAction: Learning Cross-Embodiment Manipulation from 3D Flow World Model (2025)

### 4.2 核心原理


**世界模型**学习环境动态转移函数 p(s_{t+1}|s_t, a_t)，三大流派：

**1. 视频世界模型**：将未来预测建模为视频生成
- Cosmos（NVIDIA）：物理AI基础世界模型，预训练+微调范式
- GameFactory：用游戏引擎生成训练数据
- 核心思想：能"想象"未来 = 能"规划"动作

**2. 潜在世界模型**：在潜在空间预测未来状态
- Dreamer系列：潜在空间想象rollout + RL训练
- LDA-1B：潜在动力学动作模型，10亿参数
- 优势：计算高效，可大规模想象训练

**3. 世界模型+VLA闭环**（2026核心趋势）
- World-VLA-Loop：世界模型预测→VLA生成动作→验证→修正
- VLA-JEPA：潜在世界模型增强VLA
- VLAW：世界模型和VLA迭代共同改进

**2025→2026关键变化**：
- 世界模型占比大幅增长（42→16，相对占比从7%→28%↑↑）
- 从"辅助工具"→"核心组件"，与VLA深度融合
- 视频生成模型（Sora/CogVideoX等）直接作为世界模型
- 4D Gaussian Splatting用于可微渲染+世界建模
- Fast-WAM质疑：世界动作模型是否需要推理时想象？

## 五、强化与模仿学习 (122篇)

### 5.1 代表性工作

- VR-Robo: A Real-to-Sim-to-Real Framework for Visual Robot Navigation and Locomot (2025)
- Beyond Behavior Cloning: Robustness through Interactive Imitation and Contrastiv (2025)
- Learning to Group and Grasp Multiple Objects (2025)
- S2-Diffusion: Generalizing from Instance-level to Category-level Skills in Robot (2025)
- Responsive Noise-Relaying Diffusion Policy: Responsive and Efficient Visuomotor  (2025)
- COMPASS: Cross-embOdiment Mobility Policy via ResiduAl RL and Skill Synthesis (2025)
- Hi Robot: Open-Ended Instruction Following with Hierarchical Vision-Language-Act (2025)
- Sim-to-Real Reinforcement Learning for Vision-Based Dexterous Manipulation on Hu (2025)
- Action Tokenizer Matters in In-Context Imitation Learning (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)

### 5.2 核心原理


**模仿学习（IL）范式**：
1. 行为克隆（BC）：直接回归专家动作 π(a|s)，问题：分布漂移
2. 逆强化学习（IRL）：从专家演示推断奖励函数
3. 逆动力学模型（IDM）：给定(s_t, s_{t+1})预测a_t，可从无标注视频学习

**强化学习微调VLA**（2025新范式，类比LLM的RLHF）：
- TGRPO：Group Relative Policy Optimization微调VLA
- SRPO：Self-Referential Policy Optimization
- GRAPE：偏好对齐微调机器人策略
- 核心范式：BC预训练→RL微调→偏好对齐（SFT→RLHF→Constitutional AI）

**2025→2026演进**：
- 纯RL → "IL预训练+RL微调"两阶段范式
- RLHF/偏好对齐从NLP迁移到机器人
- 稀疏奖励 → 稠密奖励 → 学习型奖励（Reward Model）
- Sim2Real+RL：先仿真RL训练→真实世界部署
- Refined Policy Distillation：从VLA通才→RL专家的知识蒸馏

## 六、灵巧操作与抓取 (180篇)

### 6.1 代表性工作

- DexVLA: Vision-Language Model with Plug-In Diffusion Expert for General Robot Co (2025)
- Learning to Group and Grasp Multiple Objects (2025)
- S2-Diffusion: Generalizing from Instance-level to Category-level Skills in Robot (2025)
- Responsive Noise-Relaying Diffusion Policy: Responsive and Efficient Visuomotor  (2025)
- Surface-Based Manipulation (2025)
- Hi Robot: Open-Ended Instruction Following with Hierarchical Vision-Language-Act (2025)
- Sim-to-Real Reinforcement Learning for Vision-Based Dexterous Manipulation on Hu (2025)
- DexGraspVLA: A Vision-Language-Action Framework Towards General Dexterous Graspi (2025)
- AVR: Active Vision-Driven Robotic Precision Manipulation with Viewpoint and Foca (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)

### 6.2 核心原理


**操作问题分类与核心方法**：

**1. 双手操作（Bimanual）**：双臂协调+角色分配
- RoboTwin 2.0：大规模双手基准，鲁棒性评估
- RoboCOIN：开源双手数据采集
- 核心挑战：双臂时序协调、避免自碰撞

**2. 灵巧手操作（Dexterous）**：高维动作空间（>20DoF）
- DexUMI：用人类手作为通用操作界面
- DexGraspVLA：VLA驱动的灵巧抓取
- 方法：潜在动作空间+课程学习+仿真预训练

**3. 抓取（Grasping）**：可供性地图 → 抓取位姿
- GraspCoT：Chain-of-Thought抓取推理
- 趋势：语言条件抓取（"抓住红色杯子"）
- 演进：2D可供性→3D 6DoF抓取位姿

**4. 可变形物体**：布料折叠、流体操作
- 方法：仿真RL+图神经网络

**技术演进**：单物体→多物体交互，刚性→可变形，独立抓取→上下文感知抓取

## 七、导航与运动 (94篇)

### 7.1 代表性工作

-  (2025)
-  (2025)
- DivScene: Benchmarking LVLMs for Object Navigation with Diverse Scenes and Objec (2025)
- Semantic Mapping in Indoor Embodied AI - A Comprehensive Survey and Future Direc (2025)
- VL-Nav: Real-time Vision-Language Navigation with Spatial Reasoning (2025)
- VR-Robo: A Real-to-Sim-to-Real Framework for Visual Robot Navigation and Locomot (2025)
- TRAVEL: Training-Free Retrieval and Alignment for Vision-and-Language Navigation (2025)
- Responsive Noise-Relaying Diffusion Policy: Responsive and Efficient Visuomotor  (2025)
- MapNav: A Novel Memory Representation via Annotated Semantic Maps for VLM-based  (2025)
- OpenFly: A Versatile Toolchain and Large-scale Benchmark for Aerial Vision-Langu (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)

### 7.2 核心原理


**视觉导航**：SLAM建图→路径规划→避障 → 端到端学习→VLN
- NaVILA：足式机器人VLA导航
- TopV-Nav：顶视图空间推理增强
- DivScene：多样化场景导航基准

**足式运动（Locomotion）**：
- 从规则控制器→学习型控制器
- Sim2Real训练范式
- 核心：鲁棒性+地形适应性

**2025→2026演进**：
- 导航从2D→3D（场景图+NeRF/Gaussian Splatting）
- 足式机器人从专用控制器→VLA统一模型
- 语言导航从单轮→多轮对话式
- 无人机VLA导航（UAV-VLA等）

## 八、数据集与基准 (105篇)

### 8.1 代表性工作

-  (2025)
- Cosmos World Foundation Model Platform for Physical AI (2025)
- GameFactory: Creating New Games with Generative Interactive Videos (2025)
- Learning to Group and Grasp Multiple Objects (2025)
- Responsive Noise-Relaying Diffusion Policy: Responsive and Efficient Visuomotor  (2025)
- Human2Robot: Learning Robot Actions from Paired Human-Robot Videos (2025)
- OpenFly: A Versatile Toolchain and Large-scale Benchmark for Aerial Vision-Langu (2025)
- AVR: Active Vision-Driven Robotic Precision Manipulation with Viewpoint and Foca (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)

### 8.2 核心原理


**数据工程**成为最大瓶颈和突破点：

1. 数据规模化：RoboMIND 2.0, Open X-Embodiment跨embodiment统一数据
2. 数据生成：仿真(Isaac Gym) + 视频生成模型 + AIGC辅助
3. 遥操作系统：低成本(ALOHA/Gello) + 全身 + VR远程
4. 跨Embodiment统一：动作token化将不同机器人映射到统一离散空间

**趋势**：数据工程取代算法创新成为最大瓶颈，"数据即模型"时代到来

## 九、3D与空间推理 (75篇)

### 9.1 代表性工作

- VL-Nav: Real-time Vision-Language Navigation with Spatial Reasoning (2025)
- S2-Diffusion: Generalizing from Instance-level to Category-level Skills in Robot (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- Dynamic Path Navigation for Motion Agents with LLM Reasoning (2025)
- AutoSpatial: Visual-Language Reasoning for Social Robot Navigation through Effic (2025)
- SmartWay: Enhanced Waypoint Prediction and Backtracking for Zero-Shot Vision-and (2025)
- VISO-Grasp: Vision-Language Informed Spatial Object-centric 6-DoF Active View Pl (2025)
- Mitigating Cross-Modal Distraction and Ensuring Geometric Feasibility via Afford (2025)
- Free-form language-based robotic reasoning and grasping (2025)
- A0: An Affordance-Aware Hierarchical Model for General Robotic Manipulation (2025)
- DeCo: Task Decomposition and Skill Composition for Zero-Shot Generalization in L (2025)

### 9.2 核心原理


**3D表征演进**：点云(PointNet++)→NeRF→3D Gaussian Splatting
- PointVLA：点云输入VLA
- 3D Flow Action：3D空间流匹配动作生成
- SpatialVLA：空间推理增强
- Spatial Forcing：强制空间对齐训练

**演进**：2D→2.5D深度→3D点云→3D高斯泼溅，表征越来越丰富

## 十、安全与对齐 (57篇)

### 10.1 代表性工作

- Beyond Behavior Cloning: Robustness through Interactive Imitation and Contrastiv (2025)
- Learning to Group and Grasp Multiple Objects (2025)
- COMPASS: Cross-embOdiment Mobility Policy via ResiduAl RL and Skill Synthesis (2025)
- FetchBot: Object Fetching in Cluttered Shelves via Zero-Shot Sim2Real (2025)
- Action Tokenizer Matters in In-Context Imitation Learning (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)

### 10.2 核心原理


1. 安全约束：动作空间安全边界（SafeVLA, SafePlan）
2. 偏好对齐：RLHF for Robots（GRAPE），人类偏好→奖励模型→RL微调
3. 约束满足：CBF+安全过滤层（策略输出后安全约束投影）

**趋势**：安全从"后处理"→"训练时内化"，与LLM安全对齐路径一致

## 十一、人机交互 (20篇)

- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- MindEye-OmniAssist: A Gaze-Driven LLM-Enhanced Assistive Robot System for Implic (2025)
- HACTS: a Human-As-Copilot Teleoperation System for Robot Learning (2025)
- Context-Aware Human Behavior Prediction Using Multimodal Large Language Models:  (2025)
- H-RDT: Human Manipulation Enhanced Bimanual Robotic Manipulation paperhttps://ar (2025)
-  (2025)
- EquAct: An SE3-Equivariant Multi-Task Transformer for Open-Loop Robotic Manipula (2025)
- Knowledge Insulating Vision-Language-Action Models: Train Fast, Run Fast, Genera (2025)
- SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics (2025)
- SwitchVLA: Execution-Aware Task Switching for Vision-Language-Action Models (2025)

## 十二、表示学习与技能 (36篇)

- S2-Diffusion: Generalizing from Instance-level to Category-level Skills in Robot (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- Dita: Scaling Diffusion Transformer for Generalist Vision-Language-Action Policy (2025)
- GROVE: A Generalized Reward for Learning Open-Vocabulary Physical Skill (2025)
- Grasping Deformable Objects via Reinforcement Learning with Cross-Modal Attentio (2025)
- ViSA-Flow: Accelerating Robot Skill Learning via Large-Scale Video Semantic Acti (2025)
- Real-Time Verification of Embodied Reasoning for Generative Skill Acquisition (2025)
- H2R: A Human-to-Robot Data Augmentation for Robot Pre-training from Videos (2025)
- Exploring the Limits of Vision-Language-Action Manipulations in Cross-task Gener (2025)
- V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Plan (2025)

## 十三、综述论文 (29篇)

- Semantic Mapping in Indoor Embodied AI - A Comprehensive Survey and Future Direc (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- OVAMOS: A Framework for Open-Vocabulary Multi-Object Search in Unknown Environme (2025)
- Multimodal Fusion and Vision-Language Models: A Survey for Robot Vision (2025)
- Dexterous Manipulation through Imitation Learning: A Survey (2025)
- Diffusion Models for Robotic Manipulation: A Survey (2025)
- Vision-Language-Action (VLA) Models: Concepts, Progress, Applications and Challe (2025)
- Neural Brain: A Neuroscience-inspired Framework for Embodied Agents (2025)
- Search-TTA: A Multimodal Test-Time Adaptation Framework for Visual Search in the (2025)
- Parallels Between VLA Model Post-Training and Human Motor Learning: Progress, Ch (2025)
- A Survey on Vision-Language-Action Models for Autonomous Driving (2025)
- A Survey on Vision-Language-Action Models: An Action Tokenization Perspective (2025)
- Foundation Model Driven Robotics: A Comprehensive Review (2025)
- Large Model Empowered Embodied AI: A Survey on Decision-Making and Embodied Lear (2025)
- Large VLM-based Vision-Language-Action Models for Robotic Manipulation: A Survey (2025)

---

## 十四、全局技术演进趋势总结


### 14.1 2025→2026五大技术趋势

**趋势一：VLA基础模型——从专用到通才**
- 2024：RT-2/OpenVLA开创VLA范式
- 2025：VLA数量爆发（254篇），3D/推理/记忆等能力叠加
- 2026：VLA成为具身智能标准架构，类似LLM在NLP的地位
- 核心演进：2D→3D感知 | 开环→闭环 | 单任务→通才 | 7B→70B+

**趋势二：动作生成——从离散到连续**
- 自回归离散token(RT-2) → 扩散去噪(Diffusion Policy) → 流匹配(Flow Matching) → 单步一致性
- 动作空间从7DoF单臂 → 双手14DoF → 全身30+DoF → 灵巧手20+DoF
- 生成范式从单步预测 → 动作分块(ACTION CHUNKING) → 长时序轨迹

**趋势三：训练范式——从纯监督到RL微调**
- 行为克隆(BC) → BC+RL微调 → RLHF偏好对齐
- 完美复现NLP路径：预训练→SFT→RLHF→Constitutional AI
- RL微调使VLA从"模仿者"变为"优化者"

**趋势四：世界模型——从辅助到核心**
- 2025：世界模型作为数据增强/仿真工具（辅助角色）
- 2026：世界模型与VLA深度融合，形成感知-预测-行动闭环（核心角色）
- 占比从7%激增至28%，是增长最快的方向

**趋势五：数据工程——从手工到自动化**
- 数据瓶颈取代算法瓶颈成为最大挑战
- 遥操作+数据引擎+仿真生成三管齐下
- 跨embodiment统一数据集推动通才策略

### 14.2 核心算法原理总结表

| 算法类别 | 核心思想 | 代表工作 | 适用场景 |
|----------|----------|----------|----------|
| 自回归VLA | LLM生成离散动作token | RT-2, OpenVLA | 低维动作、单臂 |
| 扩散策略 | 去噪生成连续动作轨迹 | Diffusion Policy, DP3 | 多模态动作分布 |
| 流匹配策略 | ODE流生成动作 | FlowPolicy, π0 | 快速推理 |
| 逆动力学预测 | 预测状态转移间的动作 | PIDM, CLIP-RT | 可扩展预训练 |
| 潜在动作模型 | 压缩空间预测动作 | LDA-1B, LAP | 跨embodiment |
| 层次化策略 | 高层规划+低层执行 | Hi Robot, HDP | 长时序任务 |
| 世界模型+RL | 想象训练+策略优化 | Dreamer, RoboHorizon | 数据稀缺 |
| 视频世界模型 | 视频生成=动作预测 | Cosmos, GameFactory | 物理理解 |

### 14.3 2026年预测方向

1. **统一VLA+世界模型**：感知-预测-行动一体化架构（World-VLA-Loop, VLAW已初现）
2. **GPU-native仿真训练**：Isaac Sim/Gym支撑10亿级交互训练
3. **人形机器人VLA**：全身控制的高维动作生成（2026年人形元年）
4. **语言驱动零样本操作**：无需微调即可执行新任务
5. **安全对齐标准化**：类似LLM的红队测试+安全评估体系
6. **端侧部署VLA**：量化/蒸馏实现手机/嵌入式端实时推理
