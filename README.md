# 抖音视频口播逐字稿提取规范

这是一个**跨 Agent 通用的任务规范与操作引导**，适用于：

- 豆包 / WorkBuddy
- DeepSeek Harness
- Claude / ChatGPT / Gemini
- OpenClaw、Cursor、OpenCode、Codex 等 Agent
- 任何能够操作浏览器、读取网络请求、处理音频并调用语音转写服务的 Agent

它不是某个 Agent 的插件，也不绑定特定 SDK。使用时，把 [`AGENTS.md`](./AGENTS.md) 或 [`SKILL.md`](./SKILL.md) 的内容交给 Agent，或者让 Agent 读取本仓库后再执行。

## 能做什么

给 Agent 一条或多条抖音链接后，提取：

- 完整口播逐字稿
- 标题
- 作者
- 粉丝数
- 发布时间
- 点赞数
- 评论数
- 收藏数
- 可访问的转写纪要文档（如果转写服务返回）

最终输出分段、加标点、校对后的 Markdown 文案，同时保留不确定专名的说明。

## 不做什么

- 不下载或交付完整视频文件
- 不分析画面内容
- 不采集评论正文
- 不抓取推荐流中的无关数据
- 不使用 yt-dlp、裸 HTTP 或 curl 直抓抖音页面

## 快速使用

仓库地址：<https://github.com/ZhuZiheng66/douyin-transcript-skill>

跨 Agent 原始指令文件：<https://raw.githubusercontent.com/ZhuZiheng66/douyin-transcript-skill/main/AGENTS.md>

如果 Agent 能读取 GitHub 文件，让它先读取 `AGENTS.md`；如果不能联网读取，就复制仓库中的 `AGENTS.md` 内容给它。

把下面这段话和抖音链接一起发给任意 Agent：

> 请打开并读取这个 GitHub 仓库：<https://github.com/ZhuZiheng66/douyin-transcript-skill>。优先读取仓库根目录的 `AGENTS.md`，并严格按其中的“抖音口播逐字稿提取规范”执行。若无法读取仓库页面，请读取原始文件：<https://raw.githubusercontent.com/ZhuZiheng66/douyin-transcript-skill/main/AGENTS.md>。
>
> 不要下载视频文件，不要采集评论正文。请提取视频完整口播逐字稿和元数据，按规范校对、分段、加标点，最后输出 Markdown 文案。
>
> 视频链接：`粘贴 v.douyin.com 或 douyin.com/video 链接`

## 关键前置条件

1. Agent 必须能操作一个**已登录抖音的浏览器会话**。
2. 必须能读取浏览器网络请求，筛选独立音频流。
3. 本地需要音频转码能力。推荐 PyAV：`pip install av`；也可以使用系统 ffmpeg。
4. 需要一个可访问的语音转写能力。具体上传和转写接口由 Agent 所在平台决定。
5. 不能把抖音原始 m4a 直接交给转写服务，必须先转成标准 MP3。

## 目录

- `AGENTS.md`：跨 Agent 主指令，优先读取
- `SKILL.md`：同一规范的 Skill 版
- `references/output-template.md`：标准 Markdown 输出模板
- `references/troubleshooting.md`：常见问题与排错
- `examples/request.md`：给 Agent 的示例请求

## 许可证

MIT
