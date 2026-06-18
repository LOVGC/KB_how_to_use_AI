# raw/ — 原始来源 (immutable)

存放原始来源，每个来源一个 markdown 文件。**只读**：wiki 从这里读取，但永不修改这些文件。
This folder is the source of truth — the LLM reads from it but never edits it.

## 命名 / Naming

`YYYY-MM-DD-slug.md` — 日期为摄入日期，slug 用英文 `kebab-case`（来源是中文也用英文 slug）。
例 / e.g. `2026-06-18-context-engineering.md`

## 状态标记 / Status

摄入完成后，原始文件名会加上 `_ingested` 后缀作为标记：`foo.md` → `foo_ingested.md`。
没有后缀 = 待摄入（queued）；带 `_ingested` = 已摄入（done）。

## 放入方式 / How sources arrive

- 给我一个 **URL** → 我抓取并转成干净的 markdown 存到这里；
- 或你自己把 **.md 文件** 放进来（例如 Obsidian Web Clipper）；
- 或直接 **粘贴文本** → 我来保存。

每次摄入前，我会先读这篇来源、用中文跟你过一遍要点，并问你想强调什么，然后才写进 `wiki/`。
