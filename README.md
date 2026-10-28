# 翁彥斌 · Tearimi

> 产品设计（2026 届）→ **AI 产品经理** 方向。
> 我只做两件事：**把复杂系统讲清楚**，**把设计判断落到真正能交付的东西上**。

**Product Design (Class of 2026) → AI Product Manager.**
Two things I do: make complex systems legible, and turn design judgment into something shippable.

---

## 🧭 我是谁 / About Me

| | |
|---|---|
| 学校 | 厦门工学院 · 产品设计（本科，2026 届） |
| 城市 | 福建 · 厦门 |
| 校招方向 | AI 产品经理（消费者型 / +AI 软件型）· 工业设计 · UI / 交互 |
| 到岗状态 | 可立即到岗 |
| 关注领域 | LLM / Agent / RAG · AI 交互体验 · 智能硬件与消费电子 |

**为什么是我**：设计出身给我的不是"画图"，而是**在约束下做取舍**的习惯——
人机工程、CMF、量产可行性这些硬约束，让我做 AI 产品时会本能地问三件事：
**这个 Agent 在真实场景里会不会说错话？错了有没有兜底？用户能不能一眼看懂它做到了哪一步？**

---

## 🛠 能力结构 / What I Can Do

| 维度 | 具体内容 |
|---|---|
| **AI 产品设计** | 多轮对话流程设计、风险分级与分流、RAG 证据链、Prompt / Agent 编排、失败兜底与人工介入点 |
| **产品与系统** | 需求拆解、信息架构、状态机设计、边界条件与异常路径、可验收的产物定义 |
| **工程实现** | Python · JavaScript / HTML / CSS · Node.js CLI · Git / Shell · 单文件零依赖交付 |
| **设计与工程化** | Rhino / KeyShot · CMF · 人机工程 · 结构可行性 · 3D 白模 Web 交互（three.js） |
| **协作与表达** | 开源 PR 规范与证据留痕、技术文档工程、CI 结果判读、中英双语交付 |

---

## 📦 代表作品 / Selected Work

### 1️⃣ archify — 开源协作（PR #178）

> **给一个零依赖 Node CLI 补上"跨 Agent 工具手动安装"文档，并守住它的 README 词数预算与 Windows 路径契约。**

- **项目**：[tt-a1i/archify](https://github.com/tt-a1i/archify) — 零依赖 Node.js CLI，把 typed JSON IR 编译成独立 HTML / SVG 架构图，并以 Agent Skill 形式分发。
- **我的 PR**：[#178 `docs(workbuddy): document WorkBuddy manual install without a switcher tab`](https://github.com/tt-a1i/archify/pull/178)
- **我做了什么**：
  1. 定位真实痛点——没有安装器切换页的用户拿不到 WorkBuddy 安装路径，补一份手动安装文档；
  2. 改动后做 **README 2125 词硬预算校验**，在预算刚好卡满处压缩冗余表述，而不是直接超支；
  3. 补 **Windows 路径契约验证**，并把 50 条本地 `fs.symlinkSync` 静默失败判定为环境性问题（后由维护者 Windows CI 全绿反证）；
  4. 用 PAT 调 GitHub Actions API 判读 CI，**推翻自己"合并后 CI 失败导致 revert"的错误假设**，改以证据下结论。
- **状态**：已合入 `dev`；维护者随后因发布流程原因（未获项目所有者确认）自行 revert，并明确说明 **"not a finding against your contribution"**。4 个 commit 在上游可追溯。
- **这段经历真正教会我的**：fork 提交不计入贡献图；`dev` 不是 `main` 的祖先、不会合流默认分支；**只有 Rebase-and-merge 能保留署名**。这直接改变了我之后每一次开源提交的操作方式。

### 2️⃣ 猫咪健康对话 Agent — `cat-care-conversational-agent`

> **一个"先安全、后解释"的多轮健康对话 Agent：不猜病，先分流。**

- **它解决什么**：主人用口语描述症状（"今天突然掉毛很多"），Agent 要理解语境、补齐关键事实、判断风险等级，再给出可执行的下一步——**而不是把一句话改写成疾病诊断**。
- **关键设计**：
  - **E0 红旗预筛查优先**：呼吸困难、无尿、持续抽搐、误食百合等 → 立即升级急诊，不等待继续问答；
  - **四级分流**（E0 急诊 / E1 尽快就医 / E2 观察 + 升级条件 / E3 追问最少事实）；
  - **口语的情景化解析**："掉毛很多" 与 "**突然**掉毛很多" 不是同一风险；短句 "突然的 / 现在呢" 绑定上轮主题而非开启新问题；
  - **权威 RAG 证据链**：结果必须带 `source_id`、机构、原始 URL、核验日期、事实摘录与诊断边界（ Cornell Feline Health Center / VCA / Merck Veterinary Manual）；**没有证据就降低断言强度并追问，不许凭常识补写来源**；
  - **写入门禁**：昵称 / 年龄 / 病史等只进候选层，用户明确确认后才写入档案；提醒必须结构化确认（内容 + 时间 + 时区），缺任一字段继续追问。
- **工程形态**：可直接复用的 Agent Skill（`SKILL.md` + `references/` 知识库与来源登记 + `templates/api-contract.md`）。

### 3️⃣ 工业设计作品集站 — `industrial-design-portfolio`

> **4 个完整项目 + 可旋转的 3D 白模，用网页把"设计过程"而不是"效果图"讲出来。**

- **在线地址**：<https://wengyanbin-portfolio.app.workbuddy.host/>
- **4 个项目**：单反相机（DSLR）· 头戴式耳机 · 智能猫窝 · 越野玩具车
- **统一叙事结构**：问题定义 → 调研 → 概念 → 迭代 → 最终方案
- **硬规则**：主图必须是 **Rhino / KeyShot 真实渲染**，AI 只做场景氛围；图片严格保持原始长宽比，禁止拉伸变形
- **技术点**：three.js + OBJLoader 的 **3D 白模交互模块**（对应 JD 里"用 3D 辅助展示提升产品维度与写实感"）；Playwright + Python 的 **PDF 导出管线**，保证网页版与投递版同源

### 4️⃣ 恐龙考古大冒险 — `dino-typing-adventure`

> **给小学三年级做的打字闯关游戏：单文件 HTML，双击即玩，离线可用。**

- **玩法**：小考古学家偷走恐龙蛋开车逃跑、肉食恐龙在后追。打对加速、连击攒氮气、打错减速抖车、发呆恐龙也会逼近——**恐龙追上即失败**，按正确率 + 用时评 1~3 星。
- **双课程树**：英文（字母认读 → 教材主题单词 → 课本句型）+ 拼音（声母 / 韵母 / 整体认读 → 生字 → 必背古诗），配套考古金币、8 种恐龙图鉴卡、车库换色、无限模式本地高分。
- **两个真实的技术坑，我怎么处理**：
  - **中文输入法下按键失灵**：`keydown` 走 `event.code`（物理键位）+ `event.key`（字符）**双通道判定**，并对输入法 `Process` 事件做兜底映射——**孩子不用切输入法**；
  - **拼音输入规则**：声调不用敲、词语连写自动忽略空格、`ü` 可用 `v` 或 `u`。
- **交付**：全部内容内嵌单文件（约 130 KB），无网络 / 无依赖 / 无插件，localStorage 存档；内容对齐闽教版小学英语三年级（2024 新版）。

---

## 🌱 正在做 / Now

- 备考校招综合素质测评，持续对齐腾讯 AI 产品经理（2027 秋招）JD
- 把一次性验证过的工具沉淀成**可复用 Agent Skill**，跨项目、跨设备复用
- 参与 `archify` 开源：零依赖 MCP server + WorkBuddy Skill 支持

---

## 📫 联系 / Contact

- GitHub：<https://github.com/Teamirni>
- 邮箱：1136468839@qq.com

---

<sub>本页所有作品均为本人实际完成，链接与状态如实标注。开源贡献部分以 PR 页面与 commit 记录为准。</sub>
