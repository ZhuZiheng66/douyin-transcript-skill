请打开并读取这个 GitHub 仓库：
https://github.com/ZhuZiheng66/douyin-transcript-skill

优先读取仓库根目录的 `AGENTS.md`，并按其中的“抖音口播逐字稿提取规范”执行。如果无法读取仓库页面，请读取：
https://raw.githubusercontent.com/ZhuZiheng66/douyin-transcript-skill/main/AGENTS.md

不要下载视频文件，不要分析画面，不要采集评论正文。请提取以下抖音视频的完整口播逐字稿和元数据：

- 标题
- 作者
- 粉丝数
- 发布时间
- 点赞
- 评论
- 收藏

请用已登录浏览器抓取页面自己的 `media-audio`，转成 16kHz 单声道 MP3，并核对音频时长和视频时长。转写后按语义分段、补标点、修正有充分依据的听写错误；不确定的专名保留原文并标注。最后按 `references/output-template.md` 输出 Markdown，并附上转写纪要文档链接或 token（如果有）。

视频链接：
1. https://v.douyin.com/替换为真实短链/
