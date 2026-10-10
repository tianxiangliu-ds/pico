# 开发与维护

唯一维护仓库是 `tianxiangliu-ds/pico`，Python 包名与 CLI 命令均为 `pico`。`examples/mini-pico/` 是同仓维护的教学示例。

需要 Python 3.10+。在虚拟环境中安装项目、教学版和测试依赖：

```bash
python -m pip install -e . -e ./examples/mini-pico pytest
python -m compileall -q pico examples/mini-pico/mini_pico
python -m pytest tests -q
python -m pytest examples/mini-pico/tests -q
git diff --check
```

测试使用假模型和隔离工作区，不需要 API key。完整测试以 Linux CI 为准；部分 verifier 使用 POSIX shell 引号，Windows 本地结果可能不同，符号链接测试也需要对应系统权限。Windows 的命名时区数据由 `tzdata` 依赖提供。

配置变更时同步更新 README 和 `.env.example`。提交前检查 `git status --short` 和 `git diff --cached`，不要提交真实 `.env`、运行日志、会话或未经脱敏的评测产物。截图应注明版本，不得展示凭据。

提交说明应描述具体变化和验证结果。新增代码使用当前包路径：`pico/evaluation/`、`pico/providers/` 和 `pico/features/`；不要恢复已移除的旧 import 入口。

仓库尚未指定开源许可证；请先与维护者确认贡献及再分发权限。
