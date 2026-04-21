# Director A Tasks

本目录用于承接 `demo_flow.md` 拆出来的可执行任务。

任务顺序：

1. `task_01_story_entry.md`：进入恋综主剧情
2. `task_02_choice_gate.md`：礼物选择互动节点
3. `task_03_perfume_branch.md`：香水分支剧情落地
4. `task_04_ai_generation.md`：AI 分支生成展示
5. `task_05_lipstick_branch.md`：口红分支对比落地
6. `task_06_behavior_panel.md`：行为数据与路径可视化
7. `task_07_demo_wrapup.md`：Demo 收束页与讲解链路

依赖关系：

- `Task 01` 是入口任务。
- `Task 02` 依赖 `Task 01`。
- `Task 03` 和 `Task 05` 依赖 `Task 02`。
- `Task 04` 依赖 `Task 03`。
- `Task 06` 依赖 `Task 02`、`Task 03`、`Task 05`。
- `Task 07` 依赖前面所有任务完成。
