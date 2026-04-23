# Data Contract

本文件定义 Demo Page 的字段规则，目标是让前端实现能直接依赖配置，不靠硬编码补语义。

## 1. 页面数据来源

支持两种来源：

- 静态配置文件
- 接口返回的结构化数据

两种来源必须对齐同一份字段语义，不允许“mock 一套、真实接口一套”。

## 2. 字段分级

### 必填字段

缺任一字段时，页面不能进入 success，只能进入 error 或 fallback：

- `page_id`
- `page_name`
- `task_id`
- `title`
- `goal_summary`
- `primary_cta`

### 常用可选字段

- `subtitle`
- `scene_summary`
- `question_text`
- `video_url`
- `poster_url`
- `auto_advance_to`
- `supporting_tags`
- `tracking_meta`

## 3. CTA 结构

主 CTA 建议统一为对象：

```json
{
  "label": "开始观看",
  "action": "navigate",
  "target": "task-02-choice-gate",
  "disabled": false
}
```

要求：

- `label` 必填
- `action` 必填，可选值必须受控，如 `navigate`、`play`、`retry`
- `target` 在 `navigate` 场景下必填
- `disabled` 默认为 `false`

## 4. Mock 规则

- 允许前端在 Demo 阶段使用 mock。
- mock 数据必须放在明确目录，不内联在组件文件里。
- mock 字段名必须与未来正式数据一致。
- 使用 mock 时，页面文档必须明确写 `允许前端 mock：是`。

## 5. 版本规则

推荐在配置中保留版本字段：

```json
{
  "schema_version": "1.0",
  "page_id": "story-entry"
}
```

规则：

- 字段新增时优先向后兼容。
- 字段重命名时必须同步更新页面文档。
- 删除字段前先确认没有页面仍在消费。

## 6. 前端消费边界

- 前端负责渲染，不负责脑补剧情逻辑。
- 如果文案缺失，只展示 fallback，不自己生成文案替代。
- 跳转目标必须来自配置或受控路由映射，不允许组件内部写死。
