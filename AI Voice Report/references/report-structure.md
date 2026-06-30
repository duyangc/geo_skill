# AI 声量报告结构规范

## 报告整体结构（基础5章 + 可选增强章节）

**基础版**：前5章为必选内容，适用于品牌类诊断报告。章节顺序如下：
1. 核心声量指标概览
2. AI大模型认知现状
3. 分类测试问题与AI回复分析
   - §3.5 品牌被动提及矩阵（非品牌类必选，品牌类可选）
4. 主要竞品AI声量横向对比 ← 先看竞争差距
5. 声量问题诊断与GEO优化建议 ← 再看问题和对策
> 重要：第4章和第5章的顺序不可颠倒。先展示竞争格局让客户看清差距，再针对差距给出诊断和建议，逻辑更顺。

**完整版**：在基础5章之上，可选增加以下增强章节，适用于非品牌类或需要完整GEO行动方案的报告：
- **§3.5 品牌被动提及矩阵**（位于第3章末尾、第4章之前）
- **§6 发现的问题与 GEO 优化行动路径**（含三阶段行动路径 + 行动总纲，位于第5章之后）

---

## Header 区域

| 占位符 | 说明 |
|--------|------|
| `{{BRAND_NAME}}` | 品牌名称，如"高源性格心理学" |
| `{{BRAND_TAGLINE}}` | 副标题/业务描述，如"九型人格心理学 · 个人成长培训" |
| `{{REPORT_DATE}}` | 报告期，如"2026年3月" |
| `{{PLATFORMS}}` | 监测平台列表，如"DeepSeek · 豆包 · 文心一言 · 腾讯元宝 · 千问 · KIMI" |

---

## 第1章：核心声量指标概览

**重要约束：** 本章 **不包含** AI综合声量得分、AI正向提及率、品牌空白提及率三个KPI汇总卡片。仅展示有实测数据的AI平台评分卡片，严禁添加未测试平台的估算卡片或评分。平台网格列数根据实测平台数量确定（如仅测2个平台则用2列布局）。

### 平台评分卡片规范

每个平台卡片包含：
- `platform-name`：平台名称
- SVG 环形得分图（`stroke-dashoffset` 计算公式：`213.63 × (1 - score/100)`）
- `platform-detail`：3行简短描述（平台特点 + 品牌提及率）
- `platform-tag`：标签样式按分数段选择

颜色/标签对照：

| 分数范围 | stroke 颜色 | tag class | 文字 |
|----------|-------------|-----------|------|
| ≥ 60 | `#10B981` | `tag-ok` | 高潜力 |
| 40–59 | `#F59E0B` | `tag-mid` | 中等机会 |
| < 40 | `#D92B2B` | `tag-weak` | 空白市场 |

章节末尾放 `insight-box` 核心结论。

---

## 第2章：AI大模型认知现状

包含两张卡片：
1. **认知定位卡**：左栏"AI已形成的认知"（绿色✓），右栏"AI认知的空白"（红色✗）
2. **关键词AI提及率分析卡**：mini-bar-chart 横条图

bar 颜色规范：
- 目标品牌相关词：`bar-target`（红色渐变）
- 行业通用词/竞品：`bar-comp2`（蓝色渐变）

---

## 第3章：分类测试问题与AI回复分析

共5类，每类一张卡片，固定结构：
- 彩色标签（类别一蓝、类别二橙、类别三绿、类别四紫、类别五橙红）
- `two-col` 分栏：左侧测试问题列表，右侧测试目的 + 数据图表
- `alert-box`：AI回复特征描述
- `warn-box`：分析结论 + 优先级标签

优先级标签颜色：
- 极高机会 / 高机会：`ct-critical`（红色）
- 核心机会：`ct-high`（橙黄色）
- 机会窗口：`ct-medium`（蓝色）

---

## 第4章：主要竞品AI声量横向对比

**位于第3章/§3.5之后、第5章(问题诊断)之前。先展示竞争格局，再给出问题诊断，逻辑更顺畅。**

包含3张卡片：
1. **竞品横向对比表**（comp-table）：目标品牌所在行加 `class="target-row"`（红色高亮）。对比维度可覆盖：通用推荐提及率、品牌核心标签、智能驾驶场景提及、纯电品类推荐力度、AI回复深度等。
2. **竞品GEO能力优势与差距分析**（two-col + info-box + warn-box）：左栏讲竞品优势，右栏讲目标品牌差距与提升空间。

> 注意：建议只保留结构和策略层面的对比维度（如提及率、推荐力度、AI认知标签等），避免使用"正面/负面比"等过于主观或难以量化的指标。

bar 颜色规范：
- 竞品1（排名第一）：`bar-comp1`（绿色）
- 竞品2（排名第二）：`bar-comp2`（蓝色）
- 目标品牌：`bar-target`（红色）

---

## 第5章：声量问题诊断与GEO优化建议

**位于第4章(竞品对比)之后。在客户已经了解竞争差距的基础上，针对性地给出问题诊断和优化建议。**

每个问题卡片结构：
```html
<div class="card" style="border-left:4px solid {{COLOR}};">
  <span class="priority-p0/p1/p2">P0/P1/P2</span> + 问题标题
  <div class="two-col">
    左：问题描述（红/橙色文字）
    右：GEO优化建议（opp-card）
  </div>
</div>
```

优先级颜色：
- P0：`#EF4444`（深红）
- P1：`#F59E0B`（橙黄）
- P2：`#EAB308`（黄色）

章节末尾放 `insight-box` 诊断总结。

---

## 配色规范（CSS 变量）

```css
--brand-red: #D92B2B;    /* 主品牌色，用于边框、按钮、高亮 */
--brand-dark: #1A1A2E;   /* 深色背景、标题 */
--brand-gray: #6B7280;   /* 辅助文字 */
--accent-blue: #2563EB;
--accent-orange: #EA580C;
--accent-green: #16A34A;
--accent-yellow: #CA8A04;
```

Header 渐变：`linear-gradient(135deg, #1A1A2E 0%, #D92B2B 100%)`  
Insight box 渐变：`linear-gradient(135deg, #1E3A5F, #D92B2B)`

---

## 文件命名规范

输出文件名：`诊断报告_{品牌简称}_.html`，例如 `诊断报告_高源性格心理学.html`

---

## 常见注意事项

1. **不要**在第1章添加总结性 KPI 数字卡片（已确认移除）
2. 所有图表使用 HTML+CSS 实现，不依赖 Canvas/外部图表库
3. 报告基础版无需第6章（执行路线图）和第7章（附录）；完整版可选包含第6章
4. 竞品对比中目标品牌行必须使用 `target-row` 而不是 `gaoyuan-row`

---

## 品牌被动提及矩阵（非品牌类增强组件）

> **适用场景**：非品牌类诊断报告必选。位于第3章末尾、第4章之前。
> **核心目的**：量化展示"当用户不主动提及品牌名时，AI是否会在通用推荐/对比问题中被动提到该品牌"。

### 组件结构：X道测试问题被动提及矩阵表

```html
<div class="card">
  <div class="card-title">N道测试问题品牌被动提及矩阵</div>
  <table class="query-table">
    <thead>
      <tr>
        <th style="width:36%;">测试问题</th>
        <th style="width:12%;">问题类别</th>
        <th style="width:16%;">DeepSeek</th>
        <th style="width:16%;">千问</th>
        <th style="width:16%;">豆包</th>
      </tr>
    </thead>
    <tbody>
      <!-- 每行一道测试问题 -->
      <tr>
        <td>Q1: 测试问题描述</td>
        <td>类别标签</td>
        <td class="mention-yes">提及详情</td>   <!-- 或 mention-no / mention-partial -->
        <td class="mention-yes">提及详情</td>
        <td class="mention-yes">提及详情</td>
      </tr>
    </tbody>
  </table>
  <div class="source-note">
    <strong>数据说明：</strong>{{DATA_NOTE}}<br>
    <strong>计算口径：</strong>{{CALC_METHOD}}<br>
    <strong>扫描节点与终端：</strong>{{SCAN_INFO}}
  </div>
</div>
```

### 提及状态样式

| 状态 | class | 颜色含义 |
|------|-------|---------|
| 正面提及 | `mention-yes` | 绿色 #16A34A |
| 未提及 | `mention-no` | 红色 #EF4444 |
| 部分提及/负面为主 | `mention-partial` | 橙色 #EA580C |

### 问题类别分类建议

非品牌类测试通常覆盖以下维度：
1. **泛市场选购** — "20万级新能源车推荐"等通用购车问题（核心诊断区）
2. **价格带锚定** — 特定价位段配置/对比问题
3. **生态关联** — 品牌所属生态圈内的推荐问题（如鸿蒙智行）
4. **品控口碑** — 质量可靠性相关问题
5. **跨界场景** — 家庭/科技/商务等生活化场景

### 数据分析要点

生成此表格时，应同步产出以下洞察并写入报告正文：
- **泛市场0提及率**：目标品牌在通用选购类问题中的被动提及率
- **生态依赖度**：仅在生态关联问题时才被提及 → 标识"路径依赖型声量"
- **平台差异**：不同AI平台对同一问题的回复差异（如品控话题的正面/负面分化）

---

## §6 发现的问题与 GEO 优化行动路径（完整版增强章节）

> **适用场景**：需要输出具体GEO执行方案的报告。位于第5章之后、Footer之前。
> **核心目的**：基于前5章的诊断结论，给出分阶段、有优先级的可执行GEO行动方案。

### 本章结构（3个子组件）

#### 子组件 A：发现的问题总结（info-box / warn-box）

先用 2-3 个 `warn-box` 或 `info-box` 卡片提炼核心诊断发现：

```html
<div class="card">
  <!-- 发现一、二、三... 用 warn-box 或 info-box 分别呈现 -->
  <div class="warn-box">
    <strong>发现一：XXX。</strong>具体问题描述与分析...
  </div>
  <div class="warn-box">
    <strong>发现二：XXX。</strong>具体问题描述与分析...
  </div>
</div>
```

#### 子组件 B：GEO 三阶段行动路径（竖向堆叠）

> **重要排版变化**：roadmap-grid 使用竖向堆叠（`flex-direction: column`）而非横排三列。每条任务内容较长时竖向排列可读性更好，且避免底部空白不齐的问题。

**三阶段框架**（时间线可根据品牌实际情况调整，但逻辑不变）：

```
Phase 01 · 紧急补位期（0-3个月）→ 解决最紧迫的认知空白/负面暴露
Phase 02 · 认知强化/筑底提升期（4-6个月）→ 建立独立产品认知
Phase 03 · 长效运营/升维领跑期（7-12个月）→ 稳定声量形成正向循环
```

每个阶段卡片结构（**纵向堆叠布局**）：

```html
<div class="roadmap-grid">
  <div class="roadmap-phase phase-1">
    <div class="phase-label">Phase 01 · {{PHASE_NAME}}</div>
    <div class="phase-title">{{TIME_RANGE}}：{{PHASE_THEME}}</div>
    <div style="font-size:12px;font-weight:600;color:#991B1B;margin-bottom:8px;">
      核心目标：{{CORE_OBJECTIVE}}
    </div>
    <ul class="phase-tasks">
      <li class="task-item">
        <div class="task-title">{{TASK_TITLE}}</div>
        <div class="task-desc">{{TASK_DESC}}</div>
      </li>
      <!-- 更多任务项... -->
    </ul>
    <div class="phase-kpi">
      <div class="phase-kpi-title">阶段GEO目标指标</div>
      <div class="kpi-item"><span class="kpi-dot"></span><span class="kpi-text">{{KPI_TEXT}}——从而解决{{PROBLEM_TEXT}}</span></div>
      <!-- 更多KPI指标... -->
    </div>
  </div>
  <!-- Phase 02, Phase 03 同结构，换 phase-2 / phase-3 和对应颜色 -->
</div>
```

**阶段配色**：

| 阶段 | class | 渐变背景 | 边框色 | label文字色 | KPI背景 |
|------|-------|---------|--------|-------------|--------|
| Phase 01 | `phase-1` | `#FEF2F2 → #FEE2E2` | `#FECACA` | `#991B1B` (红) | `rgba(254,226,226,0.5)` |
| Phase 02 | `phase-2` | `#FFFBEB → #FEF3C7` | `#FDE68A` | `#92400E` (橙) | `rgba(254,243,199,0.5)` |
| Phase 03 | `phase-3` | `#F0FDF4 → #DCFCE7` | `#86EFAC` | `#166534` (绿) | `rgba(220,252,231,0.5)` |

**任务列表纵向堆叠规范**（重要！不用双栏写法）：

每条任务采用「标题 + 缩进描述」的两层结构，避免使用 `——` 分隔的双栏拥挤排版：

```css
.phase-tasks { list-style: none; }
.phase-tasks .task-item { margin-bottom: 10px; }
.phase-tasks .task-title {
  font-size: 13px; font-weight: 700; color: var(--brand-dark); margin-bottom: 2px;
}
.phase-tasks .task-desc {
  font-size: 12px; color: #6B7280;
  padding-left: 14px; line-height: 1.65;
  border-left: 2px solid #E5E7EB;
}
```

**阶段命名原则**（按品牌类型选择）：
- **品牌类**：止血修复期 → 筑底提升期 → 升维领跑期
- **非品牌类**：紧急补位期 → 认知强化期 → 长效运营期

> **关于子组件C（优先级矩阵）**：优先级矩阵的内容已合并到子组件B的三阶段行动路径中。每个任务在标题中标注P0/P1/P2标签，并写明时间周期和预期效果，不再使用独立的geo-table表格。这样避免信息重复，让行动路径更完整。

#### 子组件 D：行动总纲（insight-box）

本章最后一部分用 `insight-box` 总结整体战略方向：

```html
<div class="insight-box">
  <h3>
    <svg .../>行动总纲
  </h3>
  <p>{{ACTION_SUMMARY}}</p>
</div>
```

总纲要点：
- 用**结构化排版**（分步区块 + 颜色标签 + 缩进）代替一整段文字堆砌，提升可读性
- 用一段话概括三步走战略逻辑（如"先XX、再XX、后XX"）
- 明确关键里程碑指标（用可验证的指标，如"某场景提及率稳定在X%以上""进入推荐前三顺位"）
- 不上"AI综合声量得分""认知覆盖率"等无统一计算标准的指标
- 升华到品牌数字化生存的战略意义
