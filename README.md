<p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p>

# 写给真正工程师的 Skills

[![skills.sh](https://skills.sh/b/mattpocock/skills)](https://skills.sh/mattpocock/skills)

这是我每天用来做真正工程开发的智能体技能（skill）——而不是凭感觉编程（vibe coding）。

开发真正的应用很难。GSD、BMAD 和 Spec-Kit 之类的方法试图通过接管整个流程来提供帮助。但这样做的同时，它们剥夺了你的控制权，也让流程中出现的问题难以解决。

这些技能的设计原则是：小巧、易于改造、可自由组合。它们适用于任何模型，基于数十年的工程经验。尽管拿去折腾，改造成你自己的。祝你用得开心。

如果你想及时了解这些技能的更新以及我创建的新技能，可以和约 60,000 名开发者一起订阅我的通讯：

[订阅通讯](https://www.aihero.dev/s/skills-newsletter)

## 快速开始（30 秒完成配置）

1. 运行 skills.sh 安装程序：

```bash
npx skills@latest add mattpocock/skills
```

2. 选择你想要的技能，以及要安装到哪些编程智能体上。**务必选中 `/setup-matt-pocock-skills`**。

3. 在你的智能体中运行 `/setup-matt-pocock-skills`。它会：
   - 询问你想使用哪种 issue 跟踪器（GitHub、Linear 或本地文件）
   - 询问你在分诊工单时会打哪些标签（`/triage` 会用到标签）
   - 询问你想把我们创建的文档保存在哪里

4. 搞定——可以开始了。

## 为什么会有这些技能

我开发这些技能，是为了解决我在 Claude Code、Codex 和其他编程智能体身上常见的失败模式。

### #1：智能体没有按我的意思做

> “No-one knows exactly what they want”（没有人确切地知道自己想要什么）
>
> David Thomas & Andrew Hunt，[The Pragmatic Programmer（程序员修炼之道）](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题所在**：软件开发中最常见的失败模式是理解不一致。你以为开发者知道你想要什么，结果看到他们做出来的东西，才发现对方完全没理解你。

在 AI 时代也是一样。你和智能体之间存在沟通鸿沟。解决办法是进行一次**拷问式问答（grilling session）**——让智能体就你要构建的东西向你提出详细的问题。

**解决方法**是使用：

- [`/grill-me`](./skills/productivity/grill-me/SKILL.md) —— 用于非代码场景
- [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) —— 与 [`/grill-me`](./skills/productivity/grill-me/SKILL.md) 相同，但增加了更多好东西（见下文）

这是我最受欢迎的技能。它们能帮你在开工前与智能体达成一致，并深入思考你要做的改动。_每次_想做改动时都用一下。

### #2：智能体太啰嗦了

> 有了通用语言，开发者之间的交流和代码的表达都源自同一个领域模型。
>
> Eric Evans，[Domain-Driven-Design（领域驱动设计）](https://www.amazon.co.uk/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

**问题所在**：在项目开始时，开发者和他们为之构建软件的人（领域专家）通常说着不同的语言。

我和我的智能体之间也有同样的隔阂。智能体通常被直接丢进一个项目，被要求边做边弄懂各种术语。于是本来一个词就能说清的事，它们要用 20 个词。

**解决方法**是建立一套共享语言。它是一份帮助智能体解读项目中所用术语的文档。

<details>
<summary>
示例
</summary>

这里有一个来自我的 `course-video-manager` 仓库的 [`CONTEXT.md`](https://github.com/mattpocock/course-video-manager/blob/076a5a7a182db0fe1e62971dd7a68bcadf010f1c/CONTEXT.md) 示例。哪一个更容易读？

- **之前**：“当课程某个章节里的一节课被变成‘真实的’（即在文件系统中分配了一个位置）时，会出现问题”
- **之后**：“物化级联（materialization cascade）有问题”

这种简洁会在一次又一次的会话中带来回报。

</details>

这已内置在 [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) 中。它也是一次拷问式问答，但会帮助你与 AI 建立共享语言，并把难以解释的决策记录到 ADR 中。

很难形容这有多强大。它可能是这个仓库里最酷的技巧。试试就知道了。

> [!TIP]
> 共享语言除了减少啰嗦之外，还有很多其他好处：
>
> - **变量、函数和文件的命名保持一致**，都使用共享语言
> - 因此，智能体**更容易在代码库中导航**
> - 智能体也**在思考上花费更少的 token**，因为它可以使用更简洁的语言

### #3：代码跑不起来

> “Always take small, deliberate steps. The rate of feedback is your speed limit. Never take on a task that’s too big.”（始终迈出小而审慎的步子。反馈的速度就是你的速度上限。永远不要承接过大的任务。）
>
> David Thomas & Andrew Hunt，[The Pragmatic Programmer（程序员修炼之道）](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题所在**：假设你和智能体已经就要构建什么达成一致。如果智能体_仍然_写出一堆垃圾，该怎么办？

这时就该审视你的反馈回路了。如果得不到关于其代码实际运行情况的反馈，智能体就是在盲飞。

**解决方法**：你需要常规的一整套反馈回路：静态类型、浏览器访问和自动化测试。

对于自动化测试，“红-绿-重构”循环至关重要。也就是让智能体先写一个失败的测试，再修复它。这能为智能体提供稳定的反馈，从而产出好得多的代码。

我做了一个 **[`/tdd`](./skills/engineering/tdd/SKILL.md) 技能**，可以放进任何项目。它鼓励“红-绿-重构”，并为智能体提供大量关于好测试和坏测试的指导。

在调试方面，我还做了一个 **[`/diagnosing-bugs`](./skills/engineering/diagnosing-bugs/SKILL.md)** 技能，把最佳调试实践封装成一个简单的循环。

### #4：我们造出了一团泥球

> “_每天_都要在系统设计上投入。”
>
> Kent Beck，[Extreme Programming Explained（解析极限编程）](https://www.amazon.co.uk/Extreme-Programming-Explained-Embrace-Change/dp/0321278658)

> “最好的模块是深模块。它们让你通过简单的接口访问大量功能。”
>
> John Ousterhout，[A Philosophy Of Software Design（软件设计哲学）](https://www.amazon.co.uk/Philosophy-Software-Design-2nd/dp/173210221X)

**问题所在**：大多数借助智能体构建的应用都复杂且难以修改。由于智能体能极大地加快编码速度，它们也加速了软件熵增。代码库正以前所未有的速度变得越来越复杂。

**解决方法**是一种全新的 AI 驱动开发方式：关心代码的设计。

这一点贯穿了这些技能的每一层：

- [`/to-prd`](./skills/engineering/to-prd/SKILL.md) 会在创建 PRD 之前询问你要改动哪些模块

更关键的是，[`/improve-codebase-architecture`](./skills/engineering/improve-codebase-architecture/SKILL.md) 能帮你拯救已经变成一团泥球的代码库。我建议每隔几天就在你的代码库上运行一次。

### 总结

软件工程的基本功比以往任何时候都重要。这些技能是我尽最大努力把这些基本功提炼成可重复的实践，帮助你交付职业生涯中最好的应用。祝你用得开心。

## 参考

这些技能按一个维度划分——由谁来调用。**用户调用**的技能只有在你输入时才会触发（例如 `/grill-me`）；它们的职责是编排。**模型调用**的技能既可以由你调用，_也_可以在任务合适时由智能体自动调用；它们承载可复用的方法论。用户调用的技能可以调用模型调用的技能，但绝不会调用另一个用户调用的技能。

### 工程

我每天写代码时使用的技能。

**用户调用**

- **[ask-matt](./skills/engineering/ask-matt/SKILL.md)** —— 询问哪个技能或流程适合你的情况。是本仓库中用户调用类技能的路由器。
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)** —— 拷问式问答，同时构建项目的领域模型，打磨术语，并随时更新 `CONTEXT.md` 和 ADR。
- **[triage](./skills/engineering/triage/SKILL.md)** —— 让 issue 在由各分诊角色组成的状态机中流转。
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)** —— 扫描代码库，找出可以加深模块的机会，以可视化 HTML 报告呈现，然后针对你选中的那一项进行拷问式问答。
- **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)** —— 为工程类技能配置当前仓库（issue 跟踪器、分诊标签、领域文档布局）。在使用其他工程类技能前，每个仓库运行一次。
- **[to-issues](./skills/engineering/to-issues/SKILL.md)** —— 用垂直切片的方式，把任何计划、规格说明或 PRD 拆分成可独立领取的 issue。
- **[to-prd](./skills/engineering/to-prd/SKILL.md)** —— 把当前对话整理成 PRD 并发布到 issue 跟踪器。不做访谈——只综合你已经讨论过的内容。

**模型调用**

- **[prototype](./skills/engineering/prototype/SKILL.md)** —— 构建一个用完即弃的原型来回答设计问题——针对状态/逻辑问题做一个可运行的终端应用，或者在一个路由下做出几个可切换的、截然不同的 UI 变体。
- **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)** —— 针对棘手 bug 和性能回退的严谨诊断循环：复现 → 最小化 → 提出假设 → 埋点观测 → 修复 → 回归测试。
- **[tdd](./skills/engineering/tdd/SKILL.md)** —— 采用“红-绿-重构”循环的测试驱动开发。每次一个垂直切片地构建功能或修复 bug。
- **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)** —— 主动构建和打磨项目的领域模型——对照术语表质疑用词，用边界场景进行压力测试，并随时更新 `CONTEXT.md` 和 ADR。
- **[codebase-design](./skills/engineering/codebase-design/SKILL.md)** —— 设计深模块的共享方法论和词汇：在小接口背后封装大量行为，放在清晰的接缝处，并能通过该接口进行测试。
- **[code-review](./skills/engineering/code-review/SKILL.md)** —— 对自某个固定点以来的 diff 进行双维度评审：**规范**（是否遵循仓库的编码规范，以及 Fowler 代码坏味道基线？）和**需求**（是否忠实实现了来源 issue/PRD？），以并行子智能体运行，互不干扰。

### 效率

通用的工作流工具，不限于代码。

**用户调用**

- **[grill-me](./skills/productivity/grill-me/SKILL.md)** —— 就某个计划或设计接受刨根问底的访谈，直到决策树的每个分支都被解决。
- **[handoff](./skills/productivity/handoff/SKILL.md)** —— 把当前对话压缩成一份交接文档，让另一个智能体可以继续工作。
- **[teach](./skills/productivity/teach/SKILL.md)** —— 在多次会话中教用户一项新技能或新概念，将当前目录用作有状态的教学工作区。
- **[writing-great-skills](./skills/productivity/writing-great-skills/SKILL.md)** —— 编写和修改技能的参考：让技能行为可预测的词汇和原则。

**模型调用**

- **[grilling](./skills/productivity/grilling/SKILL.md)** —— 就某个计划或设计对用户进行刨根问底的访谈，直到决策树的每个分支都被解决。是 `grill-me` 和 `grill-with-docs` 背后的可复用循环。
