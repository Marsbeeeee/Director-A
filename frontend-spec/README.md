# Frontend Spec System

`frontend-spec/` 用于管理多个 Demo Page 的前端开发规范。它和 `tasks/` 的关系如下：

- `tasks/` 负责说明任务范围、依赖和验收。
- `frontend-spec/` 负责说明页面怎么实现、怎么交互、怎么处理状态、怎么消费数据。
- 一个 Task 可以对应一个或多个 Page Spec。

## 目录结构

```text
frontend-spec/
  README.md                        # 规范体系说明与命名规则
  common/
    design-system.md              # 视觉 token、布局和响应式约束
    component-guidelines.md       # 页面级组件拆分与复用规则
    state-handling.md             # loading / fallback / error / success 统一规则
    data-contract.md              # 页面数据字段、mock、配置版本规则
  templates/
    demo-page.template.md         # 单个 Demo Page 标准模板
  pages/
    README.md                     # Demo Page 索引与登记表
    task-01-story-entry.page.md   # 恋综主剧情入口页示例
```

## 页面文档命名规范

### 单页面任务

文件名格式：

`task-<两位任务编号>-<page-slug>.page.md`

示例：

- `task-01-story-entry.page.md`
- `task-02-choice-gate.page.md`

### 一个任务含多个页面

如果同一个 Task 下有多个页面，继续在 slug 中区分页面职责：

- `task-04-ai-generation-panel.page.md`
- `task-04-ai-generation-result.page.md`

## 文档编写规则

1. 每个 Demo Page 必须单独一份文档，不允许把多个页面混写在一个文件里。
2. 页面文档必须直接绑定 Task ID，避免出现“页面已改但任务文档没跟上”的情况。
3. 页面文档必须写清楚状态、数据字段、异常态和跳转去向，不能只写视觉描述。
4. 页面文档里的文案、字段名、按钮行为，默认视为开发输入，不写模糊语句。
5. 页面开发前先补 Page Spec；页面改版时先改 Spec，再改实现。

## 公共规范范围

公共规范不写具体页面内容，只定义所有 Demo Page 都要遵守的规则：

- `design-system.md`：颜色、字体、层级、间距、容器、响应式基线
- `component-guidelines.md`：页面拆块方式、可复用组件边界、命名规则
- `state-handling.md`：页面四态的展示方式和交互要求
- `data-contract.md`：字段必填/可选、mock 规则、配置来源和版本控制

## 页面落地流程

1. 先在 `tasks/` 确认任务目标和依赖。
2. 从 `templates/demo-page.template.md` 复制一份新页面文档到 `pages/`。
3. 按页面真实行为填完 9 个章节，不保留占位语。
4. 在 `pages/README.md` 登记该页面的 Task、状态和负责人。
5. 回写对应 `tasks/task_xx_*.md` 的 `Related Docs`。

## 维护要求

- 页面进入开发后，状态改为 `In Progress`。
- 页面联调通过后，状态改为 `Done`。
- 如果页面结构、字段或交互发生变化，必须同步更新对应 Page Spec。
- 新增公共组件前，先判断是否应补充到 `common/component-guidelines.md`。
