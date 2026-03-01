# grok

一个 [OpenClaw](https://openclaw.ai) skill，让 AI 助手能够通过浏览器自动化访问 [Grok AI](https://grok.com) 获取实时信息。

## 功能

- 打开 grok.com 或复用已有标签页
- 自动输入问题并点击发送
- 轮询检测回答完成（覆盖思考阶段 + 输出阶段）
- 支持多轮对话
- 自动处理弹窗/横幅（SuperGrok 升级提示、登录弹窗等）

## 前置要求

- OpenClaw 已启用浏览器功能
- 用户已在 OpenClaw 浏览器中登录 grok.com
- 拥有 Grok 账号（免费版即可，无需 SuperGrok）

## 安装

将 `SKILL.md` 复制到 OpenClaw skills 目录：

```bash
mkdir -p ~/.openclaw/workspace/skills/grok
cp SKILL.md ~/.openclaw/workspace/skills/grok/SKILL.md
```

## 工作原理

该 skill 引导 AI 助手通过浏览器自动化完成以下流程：

1. 打开或复用 grok.com 标签页
2. Snapshot 获取页面元素 ref
3. 处理弹窗/横幅
4. 在 ProseMirror 输入框中输入问题
5. 点击"提交"按钮（Enter 键是换行，不是发送）
6. 短等待 + snapshot 轮询，直到出现"Regenerate"按钮
7. 获取回答内容

## 许可

MIT
