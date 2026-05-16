# Situation Map

Maps practical situations → relevant Anthropic features. Updated by the intel scraper.

---

## Automation & Scheduling

| Situation | Feature | Date |
|-----------|---------|------|
| Schedule recurring tasks (tests, audits, syncs) without keeping a laptop on | Claude Code Routines | 2026-04-14 |
| Trigger repo-wide automations on a cron or event | Claude Code Routines | 2026-04-14 |
| Prevent context compaction from dropping critical tool results mid-task | PreCompact Hook | 2026-04-13 |
| Keep prompts cached for an hour across a long agent session | `ENABLE_PROMPT_CACHING_1H` | 2026-04-14 |
| Blocking specific domains while keeping broad network access in sandbox | `sandbox.network.deniedDomains` | 2026-04-17 |
| Preventing exec-wrapper tricks from bypassing Claude Code deny rules | Claude Code Permission Security Hardening | 2026-04-17 |
| Securing find-based allowlists to block destructive `-exec` commands | Claude Code Permission Security Hardening | 2026-04-17 |
| Directing Bedrock production workloads to reserved capacity vs. flex tier | `ANTHROPIC_BEDROCK_SERVICE_TIER` | 2026-04-28 |
| Setting up Claude Code auth inside CI/CD, devcontainers, or SSH sessions | Claude Code Terminal OAuth | 2026-05-01 |
| Getting a desktop notification when a long Claude Code task finishes | Hook Desktop Notifications (`terminalSequence`) | 2026-05-13 |
| Updating the terminal window title to reflect Claude's current task | Hook Desktop Notifications (`terminalSequence`) | 2026-05-13 |
| Launching a background agent with a different model or effort level | `claude agents` Dispatched Session Flags | 2026-05-14 |
| Pointing a dispatched background agent at a custom MCP config or plugin directory | `claude agents` Dispatched Session Flags | 2026-05-14 |
| Preserving auto-approved permissions when spawning background agents | Background Agent Permission Mode Preservation | 2026-05-13 |
| Scoping a workload-identity-federation token to a specific workspace | `ANTHROPIC_WORKSPACE_ID` | 2026-05-13 |
| AWS-native full Managed Agents deployment with IAM auth and AWS billing | Claude Platform on AWS | 2026-05-11 |
| Retiring AWS commitments against Claude usage | Claude Platform on AWS | 2026-05-11 |
| Getting up-to-2.5× faster Opus 4.7 output for real-time agentic workflows | Fast Mode for Opus 4.7 | 2026-05-12 |
| Running background agents in repos where git worktrees are impractical | `worktree.bgIsolation: "none"` | 2026-05-15 |
| Safely disabling a Claude Code plugin that other plugins depend on | Plugin Dependency Enforcement | 2026-05-15 |
| Checking per-plugin token cost before enabling it in Claude Code | Plugin Cost Estimates in Marketplace | 2026-05-15 |

## Development & API

| Situation | Feature | Date |
|-----------|---------|------|
| Manage multiple agent tasks on parallel branches simultaneously | Claude Code Parallel Sessions | 2026-04-14 |
| Monitor a deploy in one pane while coding in another | Claude Code Parallel Sessions | 2026-04-14 |
| Resume a complex session the next day without losing context | Session Recap (`/recap`) | 2026-04-14 |
| Hand off a session's context to a teammate | Session Recap (`/recap`) | 2026-04-14 |
| Audit codebase for deprecated model strings before a deadline | Sonnet 4 / Opus 4 Deprecation | 2026-04-14 |
| Plan migration from Claude Sonnet 4 or Opus 4 before June 15, 2026 | Sonnet 4 / Opus 4 Deprecation | 2026-04-14 |
| Scripting Claude API calls from the terminal | ant CLI | 2026-04-08 |
| Versioning prompts and API configs in YAML | ant CLI | 2026-04-08 |
| Integrating Claude into CI/CD pipelines | ant CLI | 2026-04-08 |
| Running complex agents without burning full Opus tokens | Advisor Tool | 2026-04-09 |
| Long-horizon agentic pipelines needing occasional deep reasoning | Advisor Tool | 2026-04-09 |
| Deploying autonomous agents without building own infrastructure | Claude Managed Agents | 2026-04-08 |
| Running agents with secure sandboxing and scoped permissions | Claude Managed Agents | 2026-04-08 |
| Building agents that remember user preferences across sessions | Memory for Claude Managed Agents | 2026-04-23 |
| Enterprise agents that accumulate domain knowledge over time | Memory for Claude Managed Agents | 2026-04-23 |
| Production agents that improve through repeated use | Memory for Claude Managed Agents | 2026-04-23 |
| Triggering MCP tool calls directly from Claude Code hooks (no shell glue) | Claude Code MCP Tool Hooks | 2026-04-23 |
| Sending Slack/MCP notifications on PostToolUse events from hooks | Claude Code MCP Tool Hooks | 2026-04-23 |
| Vim-style character/line selection in Claude Code's editor | Claude Code Vim Visual Mode | 2026-04-23 |
| Customizing Claude Code's appearance with custom color themes | Claude Code `/theme` Command | 2026-04-23 |
| Reviewing GitLab MRs or Bitbucket PRs directly from Claude Code | Claude Code `--from-pr` Multi-Platform | 2026-04-23 |
| GitHub Enterprise Server teams using `--from-pr` in Claude Code | Claude Code `--from-pr` Multi-Platform | 2026-04-23 |
| AWS-native Claude deployments matching first-party API shape | Messages API on Amazon Bedrock | 2026-04-07 |
| Migrating from Claude API to Bedrock without changing SDK code | Messages API on Amazon Bedrock | 2026-04-07 |
| Regulated industries requiring AWS data residency | Messages API on Amazon Bedrock | 2026-04-07 |
| Reducing terminal noise during long Claude Code agentic runs | Claude Code Focus View | 2026-04-08 |
| Monitoring a background build or deploy without blocking Claude | Claude Code Monitor Tool | 2026-04-09 |
| Streaming real-time events from long-running background scripts | Claude Code Monitor Tool | 2026-04-09 |
| Getting more thorough Claude Code responses by default | Claude Code Default Effort → High | 2026-04-07 |
| Long-horizon agentic coding requiring the highest available intelligence | Claude Opus 4.7 | 2026-04-16 |
| Migrating from Opus 4.6 (review API breaking changes before upgrading) | Claude Opus 4.7 | 2026-04-16 |
| AWS teams adopting Claude without special Bedrock account approval | Claude in Amazon Bedrock GA | 2026-04-16 |
| Deploying Opus 4.7 or Haiku 4.5 self-serve from the Bedrock console | Claude in Amazon Bedrock GA | 2026-04-16 |
| Enterprise workloads requiring regional AWS endpoints for Claude | Claude in Amazon Bedrock GA | 2026-04-16 |
| Running comprehensive pre-merge code review from inside Claude Code | Claude Code `/ultrareview` | 2026-04-16 |
| Reviewing a specific GitHub PR without leaving Claude Code | Claude Code `/ultrareview` | 2026-04-16 |
| Dialing Opus 4.7 intelligence vs. speed without full `max` compute | `xhigh` Effort Level | 2026-04-16 |
| Quickly adjusting effort level mid-session via keyboard | Interactive `/effort` Slider | 2026-04-16 |
| Running PowerShell scripts natively in Claude Code on Windows | Claude Code PowerShell Tool | 2026-04-16 |
| Windows-native shell automation without WSL | Claude Code PowerShell Tool | 2026-04-16 |
| Auditing integrations using `context-1m-2025-08-07` on Sonnet 4 / 4.5 before errors start | 1M Context Window Beta Retired | 2026-04-30 |
| Migrating large-document pipelines from Sonnet 4/4.5 to Sonnet 4.6 or Opus 4.6 | 1M Context Window Beta Retired | 2026-04-30 |
| Resuming a coding session by pasting a PR URL instead of searching history | PR URL in `/resume` | 2026-04-28 |
| Querying workspace rate limits programmatically before dispatching batch jobs | Rate Limits API | 2026-04-24 |
| Building dashboards to monitor API capacity headroom | Rate Limits API | 2026-04-24 |
| Auditing rate limit configurations across multiple workspaces | Rate Limits API | 2026-04-24 |
| Cleaning up stale Claude Code state after archiving or migrating a repo | `claude project purge` | 2026-05-01 |
| Bulk-removing old projects from Claude Code's registry | `claude project purge` | 2026-05-01 |
| Browsing available models on a self-hosted or enterprise API gateway | `/model` Picker Gateway Support | 2026-05-01 |
| Switching Claude Code models on a LiteLLM or internal proxy gateway | `/model` Picker Gateway Support | 2026-05-01 |
| Freeing context window space mid-session without losing recent tool results | "Summarize up to here" in Rewind | 2026-05-13 |
| Archiving the early exploratory phase of a long Claude Code session | "Summarize up to here" in Rewind | 2026-05-13 |

## Research & Security

| Situation | Feature | Date |
|-----------|---------|------|
| Defensive cybersecurity analysis | Claude Mythos Preview | 2026-04-07 |
| Identifying vulnerabilities in critical software | Claude Mythos Preview | 2026-04-07 |
| Security research requiring advanced reasoning | Claude Mythos Preview | 2026-04-07 |
| Global health research (disease, diagnostics) needing Claude access | Anthropic–Gates Foundation Partnership | 2026-05-14 |
| Education-equity programs building AI tooling for underserved communities | Anthropic–Gates Foundation Partnership | 2026-05-14 |
| Life sciences and agriculture AI initiatives aligned with Gates Foundation | Anthropic–Gates Foundation Partnership | 2026-05-14 |

## Small Business & Workflows

| Situation | Feature | Date |
|-----------|---------|------|
| Automating invoicing or payroll against QuickBooks without custom integrations | Claude for Small Business | 2026-05-13 |
| Running month-end close workflows directly from Claude | Claude for Small Business | 2026-05-13 |
| Launching HubSpot or Canva marketing automations out of the box | Claude for Small Business | 2026-05-13 |

## Product & Collaboration

| Situation | Feature | Date |
|-----------|---------|------|
| Reviewing legal contracts in Microsoft Word | Claude for Word Beta | 2026-04-10 |
| Drafting financial memos with AI-assisted editing | Claude for Word Beta | 2026-04-10 |
| Accepting/rejecting AI edits one-by-one via Track Changes | Claude for Word Beta | 2026-04-10 |
| Onboarding new engineers to a codebase | Claude Code /team-onboarding | 2026-04-10 |
| Documenting team Claude Code conventions for new hires | Claude Code /team-onboarding | 2026-04-10 |
| Maintaining visual brand consistency across a growing product | Claude Design | 2026-04-17 |
| Auto-generating UI components from existing codebase and design files | Claude Design | 2026-04-17 |
| Bootstrapping a design system from a legacy codebase | Claude Design | 2026-04-17 |
