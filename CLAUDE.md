# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 仓库概览

Hello-Agents — Datawhale 社区开源教程《从零开始构建智能体》，中文 AI Native Agent 系统性学习教程。这是一个纯文档仓库，无构建/测试/CI。教程含中英双语（README.md/README_EN.md，_sidebar.md/_sidebar_en.md）。第七章自研框架独立仓库：https://github.com/jjyaoao/helloagents。

## 目录结构

```
docs/                    ← 教程正文（16章，5部分）
  chapter1~16/           ← 每章独立目录，含 .md 正文和 images/ 配图
  _sidebar.md            ← docsify 侧边栏导航
  index.html             ← docsify 入口
code/                    ← 各章节配套代码（chapter1~16）
Extra-Chapter/           ← 社区投稿（面试题、Skill、Dify教程等）
Additional-Chapter/      ← 安装指南（N8N、NodeJS）
Co-creation-projects/    ← 社区共创毕业设计（30+项目，每项目一目录）
```

## Git 分支策略

```
upstream → datawhalechina/hello-agents  （上游原仓库）
origin   → penpey/hello-agents          （个人 fork）

main  分支：只从 upstream 拉取同步，不直接写代码
learn 分支：学习笔记和实验的工作区
```

同步上游更新（一条龙，不逐步确认）：
```bash
git checkout main && git pull upstream main && git push origin main && git checkout learn && git merge main && git push origin learn
```

## 关键外部链接

- HelloAgents 自研框架（第七章配套）：https://github.com/jjyaoao/helloagents（当前 V1.0.2）
- Agent 学习路线（官方）：https://github.com/datawhalechina/Agent-Learning-Hub
- 教程在线阅读：https://datawhalechina.github.io/hello-agents/ 或国内加速 https://hello-agents.datawhale.cc

## 代理配置

全局 `http.proxy` 设为 `127.0.0.1:7890`（Ficlash），以下国内域名通过空代理直连：
- `git.longhu.net`、`gitee.com` — 直连
- `github.com` 走全局代理，不设空代理（国内直连不通）

```bash
git config --global --get-regexp "http\..*\.proxy"  # 查看当前代理配置
```

## CodeGraph

已初始化并正常运行。查询代码结构时优先使用 codegraph_ 系列工具，而不是 grep/read 遍历：
- `codegraph_search` — 按名称查找符号
- `codegraph_callers` / `codegraph_callees` — 查调用关系
- `codegraph_impact` — 分析修改影响范围
- `codegraph_context` — 获取符号的完整上下文
- `codegraph_explore` — 批量查看多个相关符号源码

## 注意事项

- 所有路径使用正斜杠 `/`（Git Bash 环境，反斜杠被当转义字符）
- docsify 本地预览：`docsify serve docs`
- 仓库中英双语对应：`README.md`/`README_EN.md`、`docs/README.md`/`docs/README_EN.md`、`docs/_sidebar.md`/`docs/_sidebar_en.md`
- `.codegraph/` 是本地索引缓存，已在 `.gitignore` 中忽略，不提交
