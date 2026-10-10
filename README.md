# ReviewAgent — CANN AscendC 算子检查智能体

把 [cann-ascendc-op-dev](.cursor/skills/cann-ascendc-op-dev/) Skill 封装为 Cursor **Subagent**，用于社区任务算子 / Basic API 的分级 Code Review 与验收检查。

仓库别名：`enternalna-Koh/Agent` → `enternalna-Koh/ReviewAgent`。

## 里面有什么

| 路径 | 作用 |
|------|------|
| [`.cursor/agents/cann-op-checker.md`](.cursor/agents/cann-op-checker.md) | 检查智能体：分型、按 mode 裁剪清单、红线、分级报告 |
| [`.cursor/skills/cann-ascendc-op-dev/`](.cursor/skills/cann-ascendc-op-dev/) | Skill 知识包（流程、官方摘录、踩坑、IT 五件套、实例） |

## 怎么用

1. 用 Cursor 打开本仓，或把 `.cursor/agents` + `.cursor/skills` 拷进算子工程。
2. 对话委托，例如：
   - `用 cann-op-checker 检查当前 git diff`
   - `只看 design.md 是否过设计 checklist`
   - `验收前总检 / 能不能交 IT`
   - `按五件套审查 deliverables`
3. 输出 Verdict：`BLOCKER` / `NEEDS_FIX` / `PASS_WITH_NOTES` / `PASS`。

### 检查 mode

| 说法 | mode | 侧重 |
|------|------|------|
| 检查一下 / 看 diff | `diff` | 当前改动（默认） |
| 只看设计 | `design` | design.md / 设计 PR |
| CI / compile / cla | `ci` | 合入门禁 |
| ZIP / 五件套 | `it` | IT 交付 |
| 验收前总检 | `full` | 端到端 |

默认 **只报告不改代码**；需要代改时明确说「顺手修」。

## 相对初版的优化点

- **按 mode 裁剪清单**，避免每次跑全量验收项  
- **内置红线**：skill 路径缺失时仍可做核心拦截  
- **按需读 skill**，不再要求一次读完全部附录  
- **分级 + 任务卡**：BLOCKER/WARN/NOTE，合入仓/门禁不明则先问  
- **触发词加强**：便于主 Agent 自动委派  

## 检查覆盖

任务分型、设计 PR、Host/Kernel 与 SIMT、Device-only 指针重载、codecheck/format、精度与性能（或「无门禁」）、hidevlab / `$ASC` 选择性 sync、SKIP 台账、IT 五件套、Ascend-CANN 邀请。

## 原则

- **任务书 > 官方讨论/模板 > 本仓文档**  
- 禁止跨任务抄门禁数字或合入路径  
- 禁止把未跑通结果写成已通过；SKIP ≠ PASS  

## License

见 [LICENSE](LICENSE)。请同时遵守 CANN 开源仓与社区任务许可。
