# IMEI Label Tool

一个基于 Flask + SQLite 的 IMEI/MAC 标签管理与打印工具。

## 当前结构

- `app.py`: Flask 入口，提供页面和 API
- `index.html`: 项目列表与项目创建
- `project.html`: 批次生成与管理
- `print.html`: 打印页面
- `printed.html`: 已打印记录
- `iot.db`: SQLite 数据库

## 本地开发

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

默认地址：`http://127.0.0.1:5001`

兼容旧路径：

- `/`
- `/project`
- `/print`
- `/printed`
- `/imei/...`

## 已处理的恢复项

- 启动时自动初始化数据库
- 自动补齐 `label_projects` 缺失字段
- 兼容旧版 `/imei/*` 前缀访问
- 修复 `printed_labels` 接口的 JSON 序列化
- 增加健康检查：`/api/health`

## 下一步建议

1. 把前端页面内硬编码的 `/imei/...` 统一抽成一个 `baseUrl`
2. 增加 `requirements-dev.txt`、格式化和测试脚本
3. 补接口测试，覆盖项目、批次、导出和打印记录流程
4. 把单文件 `app.py` 拆成 `routes/`, `services/`, `db/`
