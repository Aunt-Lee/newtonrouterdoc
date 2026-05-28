# API 中转站安装部署

这份文档用于记录 API 中转站从本地搭建、文档编写到 Vercel 部署的完整流程。

## 安装

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 配置

=== "macOS"

    创建文档项目目录：

    ```bash
    mkdir api-relay-docs
    cd api-relay-docs
    ```

    启动本地预览：

    ```bash
    mkdocs serve -a 127.0.0.1:8001
    ```

=== "Vercel"

    Vercel 构建配置：

    ```text
    Install Command: pip install -r requirements.txt
    Build Command: mkdocs build
    Output Directory: site
    ```

<div class="steps" markdown>

### 创建项目

先完成 Python 虚拟环境和 MkDocs 依赖安装，确保本地可以运行 `mkdocs` 命令。

```bash
mkdocs --version
```

### 编辑文档

所有页面都放在 `docs/` 目录中，左侧导航由 `mkdocs.yml` 的 `nav` 字段控制。

```text
docs/
├─ index.md
├─ setup/
├─ deploy/
└─ api/
```

### 部署上线

把项目推送到 GitHub 后，在 Vercel 导入仓库。Vercel 会读取 `vercel.json` 并自动构建 `site/` 静态目录。

</div>
