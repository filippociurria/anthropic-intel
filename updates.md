# Anthropic Intel — Updates

Newest entries first. Managed by the intel scraper. Do not edit manually.

---

## Memory for Claude Managed Agents (Public Beta) — 2026-04-23
- **What**: Persistent memory layer for Managed Agents now in public beta; agents learn from every session with an intelligence-optimized memory store that developers can inspect, manage, and export via the API
- **Situations**: building agents that remember user preferences across sessions, enterprise agents that accumulate domain knowledge over time, production agents that improve through repeated use
- **Tags**: [dev, automation]
- **Source**: https://claude.com/blog/claude-managed-agents-memory

## Claude Code MCP Tool Hooks (`type: "mcp_tool"`) — 2026-04-23
- **What**: Hooks can now directly invoke MCP tools by setting `type: "mcp_tool"` instead of a shell command, eliminating shell-glue wrappers for MCP-backed automation
- **Situations**: sending Slack notifications via an MCP server on PostToolUse events, chaining MCP actions into Claude Code hook pipelines without shell wrappers, triggering multi-tool workflows from Claude Code events
- **Tags**: [dev, automation]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Code Vim Visual Mode & Custom Themes — 2026-04-23
- **What**: Vim visual mode (`v`) and visual-line mode (`V`) added to the editor; new `/theme` command for creating and managing custom color themes in Claude Code (v2.1.118)
- **Situations**: Vim-workflow developers needing character/line selection in Claude Code's editor, customizing Claude Code's appearance for personal or team preferences, creating branded terminal environments for demos
- **Tags**: [dev]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Code `--from-pr` Multi-Platform Support — 2026-04-23
- **What**: `--from-pr` flag now accepts GitLab merge-request, Bitbucket pull-request, and GitHub Enterprise PR URLs in addition to GitHub.com (v2.1.119)
- **Situations**: GitLab teams reviewing MRs directly in Claude Code, Bitbucket-based projects using Claude Code's PR analysis workflow, enterprises on GitHub Enterprise Server accessing `--from-pr` for the first time
- **Tags**: [dev]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Design — 2026-04-17
- **What**: Research preview powered by Opus 4.7 that reads your codebase and design files to generate a reusable design system (colors, typography, components) applied consistently across future projects
- **Situations**: maintaining visual brand consistency across a growing product, auto-generating UI components from existing design tokens, bootstrapping a design system from a legacy codebase
- **Tags**: [product, dev]
- **Source**: https://9to5mac.com/2026/04/17/anthropic-launches-claude-design-for-mac-following-opus-4-7-model-upgrade/

## Claude Code Permission Security Hardening — 2026-04-17
- **What**: Bash deny rules now match commands wrapped in `env`/`sudo`/`watch`/`ionice`/`setsid`; `Bash(find:*)` allowlists no longer auto-approve `find -exec`/`-delete`; macOS `/private/{etc,var,tmp,home}` paths flagged as dangerous removal targets
- **Situations**: preventing exec-wrapper tricks from bypassing Claude Code deny rules, securing find-based allowlists that previously allowed destructive `-exec` flags, hardening shared or automated Claude Code deployments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `sandbox.network.deniedDomains` — 2026-04-17
- **What**: New Claude Code setting to explicitly block specific domains even when a broader `allowedDomains` wildcard would otherwise permit them
- **Situations**: blocking high-risk endpoints while keeping broad internet access in sandboxed sessions, enterprise deployments with outbound domain restrictions, fine-grained per-project network control
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `/ultrareview` Command — 2026-04-16
- **What**: Cloud-based parallel multi-agent code review; run `/ultrareview` on the current branch or `/ultrareview <PR#>` to fetch and review any GitHub PR
- **Situations**: getting comprehensive pre-merge review without switching to an external tool, reviewing a GitHub PR from directly inside Claude Code, surfacing security or logic issues across large changesets
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `xhigh` Effort Level & Interactive `/effort` Slider — 2026-04-16
- **What**: New `xhigh` effort tier for Opus 4.7 sitting between `high` and `max`; `/effort` with no arguments now opens an interactive arrow-key slider to set the level
- **Situations**: dialing Opus 4.7 intelligence vs. speed without paying full `max` compute, quickly adjusting effort mid-session via keyboard, performance-tuning long agentic runs
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code PowerShell Tool — 2026-04-16
- **What**: Native PowerShell tool now rolling out on Windows (opt in/out via `CLAUDE_CODE_USE_POWERSHELL_TOOL`); also available on Linux/macOS with `pwsh` on PATH
- **Situations**: running PowerShell scripts natively in Claude Code on Windows, Windows-native shell automation without WSL, cross-platform PowerShell workflows
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude in Amazon Bedrock — Generally Available — 2026-04-16
- **What**: Claude via the Messages API (`/anthropic/v1/messages`) is now open to all Amazon Bedrock customers; Opus 4.7 and Haiku 4.5 available self-serve via the Bedrock console across 27 AWS regions
- **Situations**: AWS teams adopting Claude without special account approval, deploying Opus 4.7 or Haiku 4.5 directly from the Bedrock console, enterprise workloads requiring regional AWS endpoints
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Opus 4.7 — 2026-04-16
- **What**: Most capable generally available Claude model for complex reasoning and agentic coding at the same $5/$25 per MTok pricing as Opus 4.6; includes updated tokenizer and API breaking changes vs 4.6
- **Situations**: long-horizon agentic coding requiring the highest available intelligence, production workloads needing frontier reasoning at Opus 4.6 price, migrating from Opus 4.6 (review breaking changes before upgrading)
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Code Routines — 2026-04-14
- **What**: Cloud-based scheduled automations (cron or event-triggered) that run on Claude Code's web infrastructure even when your local machine is offline
- **Situations**: scheduling nightly dependency audits or test runs, triggering repo-wide tasks on a schedule without a laptop staying awake, packaging and reusing automations across repos via connectors
- **Tags**: [automation, dev]
- **Source**: https://code.claude.com/docs/en/routines

## Claude Code Parallel Sessions & Desktop Redesign — 2026-04-14
- **What**: Run multiple Claude Code sessions side-by-side from one window with a new sidebar manager, plus an integrated terminal, file editor, HTML/PDF preview, and drag-and-drop layout
- **Situations**: managing separate agent tasks on parallel feature branches simultaneously, monitoring a deploy in one pane while editing code in another, comparing two Claude conversations side by side
- **Tags**: [dev, automation]
- **Source**: https://siliconangle.com/2026/04/14/anthropics-claude-code-gets-automated-routines-desktop-makeover/

## Claude Code Session Recap (`/recap`) — 2026-04-14
- **What**: Automatically generates an AI context summary when returning to a session after being away; manually invocable with `/recap`, configurable in `/config`
- **Situations**: resuming a complex debugging session the next morning, handing off context to a colleague, re-orienting after a long interruption mid-task
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `ENABLE_PROMPT_CACHING_1H` Env Var — 2026-04-14
- **What**: New Claude Code env var to opt into the 1-hour prompt cache TTL (replacing the 5-minute default) across API key, Bedrock, Vertex, and Foundry; `FORCE_PROMPT_CACHING_5M` forces 5-minute TTL
- **Situations**: long agent sessions where re-reads of the same large system prompt should hit cache for an hour, Bedrock/Vertex setups that previously required separate config for extended TTL, cutting costs on repeated calls within a work session
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Sonnet 4 & Opus 4 Deprecation — 2026-04-14
- **What**: `claude-sonnet-4-20250514` and `claude-opus-4-20250514` are deprecated with retirement on the Claude API scheduled for June 15, 2026; recommended migration targets are Sonnet 4.6 and Opus 4.6
- **Situations**: auditing codebases for hardcoded deprecated model IDs before the June deadline, planning staged rollouts to 4.6 models, updating CI/CD pipelines that pin model strings
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## PreCompact Hook — 2026-04-13
- **What**: New Claude Code hook that fires before context compaction; hooks can block compaction by exiting with code 2 or returning `{"decision":"block"}`
- **Situations**: preserving full conversation context during critical long-running agent tasks, implementing custom compaction logic instead of the default, preventing mid-task summarisation that could drop important tool results
- **Tags**: [automation, dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude for Word Beta — 2026-04-10
- **What**: Native sidebar add-in for Microsoft Word with AI-assisted editing, clickable citations, and Track Changes integration
- **Situations**: reviewing legal contracts in-document, drafting financial memos with inline AI edits, accepting/rejecting AI revisions one-by-one
- **Tags**: [product, automation]
- **Source**: https://www.thurrott.com/a-i/334834/anthropic-launches-claude-for-word-in-beta

## Claude Code /team-onboarding Command — 2026-04-10
- **What**: New `/team-onboarding` slash command that auto-generates a teammate ramp-up guide from your local Claude Code usage patterns
- **Situations**: onboarding new engineers to an unfamiliar codebase, capturing team conventions for new hires, documenting Claude Code workflows
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog

## Advisor Tool (API public beta) — 2026-04-09
- **What**: Pairs a fast executor model (Sonnet 4.6 / Haiku 4.5) with Opus 4.6 as a high-intelligence mid-generation advisor for strategic guidance
- **Situations**: running complex long-horizon agents at executor cost, getting near-Opus quality without full Opus token spend, agentic pipelines where most steps are routine but some require deep reasoning
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/agents-and-tools/tool-use/advisor-tool

## Claude Code Monitor Tool — 2026-04-09
- **What**: New Monitor tool in Claude Code for streaming real-time events from background scripts
- **Situations**: watching a background build or test run, monitoring deploys without blocking Claude's session, streaming events from long-running scripts
- **Tags**: [dev, analytics, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Managed Agents (API public beta) — 2026-04-08
- **What**: Fully managed agent harness: runs Claude autonomously with secure sandboxing, built-in tools, checkpointing, credential management, and SSE streaming
- **Situations**: deploying autonomous agents without building infrastructure, running long-horizon agentic workflows with scoped permissions and tracing, production agents with secure code execution
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/managed-agents/overview

## ant CLI — 2026-04-08
- **What**: Official command-line client for the Claude API with native Claude Code integration and YAML-based API resource versioning
- **Situations**: scripting Claude API calls from the terminal, versioning prompts and API configs in YAML, integrating Claude into CI/CD pipelines
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/api/sdks/cli

## Claude Code Focus View — 2026-04-08
- **What**: Focus view toggle (`Ctrl+O`) in NO_FLICKER mode that shows only prompt, one-line tool summary with diffstats, and Claude's final response
- **Situations**: reducing terminal noise during long agentic runs, presenting Claude's work without raw tool output, working in narrow or shared terminals
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Mythos Preview — 2026-04-07
- **What**: Specialized Claude model with strong general capabilities and particular depth in computer security tasks, available as invitation-only gated research preview via Project Glasswing
- **Situations**: defensive cybersecurity analysis, identifying vulnerabilities in critical software, security research requiring advanced reasoning
- **Tags**: [research, dev]
- **Source**: https://anthropic.com/glasswing

## Messages API on Amazon Bedrock (research preview) — 2026-04-07
- **What**: First-party Claude API endpoint (`/anthropic/v1/messages`) on AWS-managed infrastructure in us-east-1, same request shape as the direct Claude API with zero operator access
- **Situations**: AWS-native Claude deployments with the same SDK/API shape, regulated industries requiring data residency on AWS, migrating from first-party API to Bedrock without code changes
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock-research-preview

## Claude Code Default Effort Changed to High — 2026-04-07
- **What**: Default effort level raised from medium to high for API-key, Bedrock/Vertex/Foundry, Team, and Enterprise Claude Code users (adjustable with `/effort`)
- **Situations**: getting more thorough responses by default, agentic tasks requiring deeper reasoning without manually setting effort, users who previously relied on the medium default
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog
