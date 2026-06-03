# lark-cs-training-doc

> 客户支持组新品培训文档 skill —— 给 AI agent 用的能力包。
> 基于飞书 wiki《客户支持组新品培训模板》固化,支持「生成」和「审查」两个动作。

## 这是什么

一个 [lark-cli](https://github.com/) 系列 skill。装进支持 skill 的 AI agent(Claude Code / Openclaw 等)后,agent 就能:

- **生成** —— 你喂产品资料(定位 / 功能 / 配件 / FAQ…),agent 按 11 章模板生成一份飞书云文档培训文档草稿,工作原理章节用画板梳理,资料缺的章节自动留 `⚠️ 待补充` 提示。
- **审查** —— 给一份已写好的培训文档 URL,agent 对照 11 章模板逐项体检(章节是否齐全、是否踩反例、权限是否已开),输出修改报告。

判断标准始终是:**一线客服专员遇到客户提问时,能不能照着文档直接答**。

## 安装

clone 到 agent 的 skills 目录即可(以 Claude Code / Openclaw 为例):

```bash
git clone git@github.com:Soky96/lark-cs-training-doc.git ~/.claude/skills/lark-cs-training-doc
# Openclaw 用户路径替换为 ~/.openclaw/skills/lark-cs-training-doc
```

装好后重启 agent 加载 skill。

## 依赖

- **lark-cli** 已安装并完成飞书授权(`lark-cli auth login`)。
- 同环境的 lark 系列基础 skill(随 `lark-cli update` 一起安装):
  - `lark-shared`(认证 / 权限)
  - `lark-doc`(文档读写)
  - `lark-whiteboard`(画板)
  - `lark-drive`(开权限)
- 飞书 scope:`docx:document:create`、`docx:document:write_only`、`docx:document:readonly`、`board:whiteboard:node:create`、`docs:permission.member:create`、`wiki:node:read`。

## 用法

直接对 agent 说话即可,例如:

- 生成:`给【XX 新品】写一份客服培训文档,资料我贴在下面…`
- 审查:`帮我检查这份培训文档合不合规:https://…feishu.cn/docx/xxxx`

## 来源

内部飞书《客户支持组新品培训模板》(SwitchBot 客户支持组维护)。
本仓库只是其**抽象框架**;完整的好例 / 反例与本公司具体案例在内部飞书文档中,请向客户支持组索取访问权限。
