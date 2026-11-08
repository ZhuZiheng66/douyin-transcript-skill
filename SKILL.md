---
name: douyin-transcript-extraction
description: Use when a user provides a Douyin link and asks for the full spoken transcript, metadata, or a reusable transcript note.
version: 1.0.0
author: Community Skill
license: MIT
metadata:
  compatibility: cross-agent
  platforms: [doubao, workbuddy, deepseek-harness, claude, chatgpt, gemini, openclaw, cursor, opencode, codex]
---

# Douyin Transcript Extraction

Use `AGENTS.md` as the source of truth for this task. It defines a browser-first, cross-agent workflow for extracting a complete spoken transcript and metadata from Douyin videos.

## Trigger

Activate when the user provides a `v.douyin.com` share link or a `douyin.com/video` link and asks to extract copy, transcribe speech, get a verbatim transcript,整理口播, or save the result as a material note.

## Non-goals

Do not download or deliver the full video, analyze frames, or collect comment text. Do not use yt-dlp, curl, or bare HTTP scraping against Douyin.

## Required method

Use an authenticated browser session, capture the page's own `media-audio` request, convert the audio to 16kHz mono MP3, verify duration against the video, upload the MP3 to a reachable location, and submit it to an available speech-to-text capability. Preserve any returned transcript document or smart-minutes link.

## Output

Return the metadata, duration check, correction notes, and a semantically segmented Markdown transcript. If a term is uncertain, preserve the raw transcription and mark it for human review instead of guessing.

Read `AGENTS.md` for the complete procedure, failure handling, batch rules, and verification checklist.
