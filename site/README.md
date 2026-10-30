# Embodied Lab 网页源码（统一仓库）

本目录是 Embodied Lab · 具身智能实验室的可独立运行网页展示版，与项目的论文知识库、研究笔记**共同维护于 `zmf2022/embodied-aI-wiki`**。

## 结构

- `site/index.html`：单文件 HTML/CSS/JavaScript，包含总览、项目展示、GTC 2026 专题、智元创新日 / Agentic Robot Learning 专题、Embodied Autoresearch 和八周研发工作台模板。
- `site/frontier-2026.html`：Google DeepMind、阿里 Rynn、Figure AI 2026 Q3–Q4 技术战略可视化专题（同一 Pages 网站下的独立深度页面）。
- `研究洞察/头部具身智能技术战略_2026Q3Q4_Google_阿里_Figure.md`：三家公司技术架构、实验对照与研发现状的长文版。
- `研究洞察/GTC_2026_Berlin_具身智能与后续研发路线.md`：GTC 长文版本。
- `研究洞察/智元创新日2026_全栈技术演示与自进化洞察.md`：智元技术与 Agentic Robot Learning 长文版本。
- `README.md`：现有知识库主页，保留原有论文技术分析。

## 本地预览

```bash
cd site
python3 -m http.server 8000
```

打开 http://localhost:8000 。也可以直接使用浏览器打开 `index.html`。无需 Node.js 或构建步骤。

## 和原 ChatGPT Sites 的关系

原始站点：`https://embodied-lab-zmf.spryraven4.chatgpt.site`

这个目录是根据原网站栏目与风格重新整理的**源码展示版**，不是从 Sites 导出的原始源码。GitHub 提交不会自动部署到现有 ChatGPT Sites 原项目；沿用原网址仍需在对应 Sites 项目中关联并发布。

八周任务模板仅保存当前网页浏览器的 `localStorage`，与原 Sites 站点工作台数据不互通；切勿以源码替换覆盖原站点工作台数据。

## 维护原则

1. 不再新建同用途独立仓库；网页、研究内容与技术路线统一归档在此仓库。
2. 研究内容区分官方发布、推断与待验证实验目标。
3. 展示数据不等于已验证性能；所有算法对比应附相同任务、随机种子与独立测试。
4. 当前 GitHub 仓库已公开；发布研究内容和场景图片前应核查保密、授权、数据合规与引用来源。
