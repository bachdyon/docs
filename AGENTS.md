# Documentation project instructions

## About this project

- Mintlify documentation site for **video-automator-skills** ([repo](https://github.com/bachdyon/video-automator-skills), [production](https://vas.bachdyon.com/)).
- Pages are MDX files with YAML frontmatter (`title`, `description`, `icon`).
- Navigation is configured in `docs.json`.
- Local preview: `mint dev` (in `docs/`).
- Broken-link check: `mint broken-links` (must pass before PR).

## Terminology

Project-specific terms — keep usage consistent:

- **video-automator-skills** — repo name (lowercase, hyphenated). Don't write "Video Automator Skills".
- **skill** — a reusable module under `skills/<name>/SKILL.md`. The word "skill" is lowercase unless starting a sentence. The `$skill-name` invocation form (e.g. `$audio-deduplicate`) keeps the dollar prefix.
- **job** — a single pipeline run under `jobs/<job_id>/`. Don't say "task" or "session".
- **asset_index** — module name (snake_case), kept as `asset_index` or `Asset Index` (Title Case for headings) but **never** "asset index" two words mid-sentence in code refs.
- **watcher** — the filesystem watcher process; lowercase.
- **router** — `tools/asset_index/router.py`, dispatches per-media analyzer.
- **analyzer** — `image_gemini`, `video_gemini`, `audio_gemini`. Lowercase.
- **embed model** — `text-embedding-3-small` by default; keep model name verbatim.
- **render plan** — TOML file representing the EDL (edit decision list).
- **raw_assets** — global pool folder; keep underscore form (matches filesystem).

## Language conventions

- **Body text**: write in **Vietnamese** (giải thích, hướng dẫn, mô tả, callout content, frontmatter `title`/`description`). The audience is Vietnamese-speaking creators/devs.
- **Technical terms**: keep in **English** — `watcher`, `debounce`, `embedding`, `vector`, `idempotent`, `launchd`, `Task Scheduler`, `service`, `pipeline`, `fork`, `branch`, `commit`, `PR`, `Issue`, `API key`, `env`, `venv`, `repo`, `OpenAI`, `Gemini`, `OS`, `CLI`, `MDX`, `frontmatter`, `analyzer`, `router`.
- **File / folder / command names**: keep verbatim (`raw_assets/`, `.asset_index/`, `Install.command`, `mint dev`).
- **Code, comments, commit messages**: English (per [CONTRIBUTING.md](https://github.com/bachdyon/video-automator-skills/blob/main/CONTRIBUTING.md)).
- **LICENSE**: kept in English (PolyForm Noncommercial 1.0.0 — preserve legal precision).
- **Mintlify components**: component names stay English (`<Note>`, `<Tip>`, `<Steps>`, `<AccordionGroup>`, `<Card>`, `<Columns>`); content inside writes in Vietnamese.

## Style preferences

- Active voice and second person — "Bạn cần…" / "Mở terminal…".
- Một ý mỗi câu (one idea per sentence).
- Sentence case for headings (`## Bước tiếp theo`, not `## BƯỚC TIẾP THEO`).
- **Bold** for UI elements: Click **Settings**.
- Code formatting (`backticks`) for file names, commands, paths, env vars, code refs.
- Code blocks always have a language tag (` ```bash `, ` ```python `, ` ```toml `, ` ```mdx `).
- Use MDX components when they add value — don't over-use:
  - `<Note>` — neutral background context.
  - `<Tip>` — helpful trick / shortcut.
  - `<Warning>` — destructive or risky action.
  - `<Info>` — TL;DR / metadata callout.
  - `<Steps>` — sequential procedure.
  - `<AccordionGroup>` — collapsible alternatives (per-OS, FAQ).
  - `<Card>` / `<Columns>` — landing-page-style navigation.

## Content boundaries

- **DO** document: skills, asset_index, installation, configuration, usage, troubleshooting, contributing.
- **DON'T** document: API keys actual values, production secrets, internal owner DMs, anything outside the published OSS surface.
- When porting `SKILL.md` → MDX, **preserve technical content verbatim** (only change format to MDX components). Don't paraphrase or "improve" skill rules.

## Reference structure

Active navigation lives in [`docs.json`](docs.json). Current top-level groups:

1. Bắt đầu (Getting started) — `index`, `quickstart`.
2. Cài đặt đầy đủ — `installation/{macos,windows,linux}`.
3. Cấu hình — `configuration/{env,structure}`.
4. Sử dụng — `usage/{index,search,status,verify}`.
5. Skills — port từ `skills/<name>/SKILL.md`.
6. Asset Index nâng cao — `asset-index/{architecture,cli,files,idempotency,cross-platform,extending}`.
7. Vận hành — `troubleshooting`, `maintenance`.
8. Cộng đồng — `contributing`.

When adding a new page, update `docs.json` AND link it from at least one related page (cross-link).
