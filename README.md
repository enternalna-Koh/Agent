# ReviewAgent — CANN AscendC 算子检查智能体

把 [cann-ascendc-op-dev](.cursor/skills/cann-ascendc-op-dev/) Skill 封装为 Cursor **Subagent**，用于 CANN 社区任务算子 / Basic API 的 Code Review 与验收检查。

仓库别名：`enternalna-Koh/Agent` → `enternalna-Koh/ReviewAgent`。

## 里面有什么

| 路径 | 作用 |
|------|------|
| [`.cursor/agents/cann-op-checker.md`](.cursor/agents/cann-op-checker.md) | 算子检查智能体（系统提示 + 检查清单） |
| [`.cursor/skills/cann-ascendc-op-dev/`](.cursor/skills/cann-ascendc-op-dev/) | 完整 Skill 知识包（流程、官方摘录、踩坑、IT 五件套、实例） |

## 在 Cursor 里怎么用

1. Clone 本仓，并用 Cursor 打开该目录（或把 `.cursor/agents` + `.cursor/skills` 拷进你的算子工程）。
2. 在对话里委托检查，例如：
   - `用 cann-op-checker 检查当前 MR / git diff`
   - `检查这份 design.md 是否满足社区任务设计 checklist`
   - `按 acceptance-pack 审查 IT 五件套 ZIP`
3. Agent 会读取 `.cursor/skills/cann-ascendc-op-dev/` 下的规范，输出 **BLOCKER / NEEDS_FIX / PASS_WITH_NOTES** 报告。

也可把 Skill 单独装到个人目录：

```powershell
Copy-Item -Recurse .\.cursor\skills\cann-ascendc-op-dev "$env:USERPROFILE\.cursor\skills\cann-ascendc-op-dev"
```

```bash
cp -a .cursor/skills/cann-ascendc-op-dev ~/.cursor/skills/cann-ascendc-op-dev
```

## 检查覆盖

- 任务分型（算子 / Basic API / 仅设计）与 tasklist 目录核对  
- 设计 PR、CLA、评审流程  
- Host/Kernel、SIMT、codecheck、clang-format、Device-only 指针重载  
- 精度 / 性能门禁（或「无门禁」声明）  
- hidevlab、`$ASC` 选择性 sync、架构 SKIP 台账  
- IT 交付五件套与 Ascend-CANN 邀请  

细则见 Skill 内 `SKILL.md`、`pitfalls.md`、`acceptance-pack.md`。

## 原则

- **任务书 > 官方讨论/模板 > 本仓文档**  
- 禁止把 SpMV / CUBE 的门禁数字或合入路径照搬到其他任务  
- 禁止把未跑通结果写成已通过  

## License

见 [LICENSE](LICENSE)。文档以学习复用为目的；请同时遵守 CANN 开源仓与社区任务许可。
