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
| Enterprise Windows teams on Bedrock/Vertex/Foundry needing PowerShell without manual opt-in | PowerShell Tool Default-On for Bedrock/Vertex/Foundry | 2026-05-15 |
| Scripts failing due to execution policy restrictions on enterprise Claude Code Windows deployments | PowerShell Tool Default-On for Bedrock/Vertex/Foundry | 2026-05-15 |
| Detaching a session started with a custom MCP config and keeping that config in the background | Background Session `/bg` Config Flag Persistence | 2026-05-15 |
| Resuming a backgrounded session after sleep without losing the selected model or effort level | Background Session `/bg` Config Flag Persistence | 2026-05-15 |
| Connecting Claude to private-network MCP servers without a VPN client | MCP Tunnels Research Preview | 2026-05-19 |
| Using internal company tools as MCP servers from Claude | MCP Tunnels Research Preview | 2026-05-19 |
| Running Managed Agent tool execution on your own infrastructure | Self-hosted Sandboxes for Managed Agents | 2026-05-19 |
| Enterprise data-residency or compliance requirements for Managed Agent code execution | Self-hosted Sandboxes for Managed Agents | 2026-05-19 |
| Adding or rotating MCP tools in a running Managed Agent session without restart | Live MCP Config Updates for Managed Agents | 2026-05-19 |
| Agents receiving large tool responses without hitting context-window limits | Managed Agent Large Output Auto-Spill | 2026-05-19 |
| Building a tmux status bar or dashboard showing active Claude Code sessions | `claude agents --json` | 2026-05-19 |
| Scripting Claude Code session management workflows with `jq` or shell tools | `claude agents --json` | 2026-05-19 |
| Combining cloud and local MCP connectors in a managed enterprise Claude Code deployment | `allowAllClaudeAiMcps` Enterprise MCP Setting | 2026-05-22 |
| Enabling claude.ai cloud MCPs for users under managed IT policies | `allowAllClaudeAiMcps` Enterprise MCP Setting | 2026-05-22 |
| Creating a skill that prevents Claude from using write or execute tools | `disallowed-tools` Frontmatter for Skills | 2026-05-27 |
| Building least-privilege slash commands that restrict available tools | `disallowed-tools` Frontmatter for Skills | 2026-05-27 |
| Auto-labeling Claude Code session windows by branch or project in a terminal multiplexer | `SessionStart` Session Title & Skills Reload | 2026-05-27 |
| Installing skills via a SessionStart hook and using them immediately without restarting | `SessionStart` Session Title & Skills Reload | 2026-05-27 |
| Filtering sensitive patterns from Claude's terminal output for compliance | `MessageDisplay` Hook Event | 2026-05-27 |
| Post-processing Claude's response text through a custom renderer or redaction wrapper | `MessageDisplay` Hook Event | 2026-05-27 |
| Restricting context-aware plugin suggestions to vetted internal org marketplaces | `pluginSuggestionMarketplaces` Managed Setting | 2026-05-27 |
| Preventing Claude Code from surfacing third-party plugins in enterprise deployments | `pluginSuggestionMarketplaces` Managed Setting | 2026-05-27 |
| Onboarding new users to auto mode without a consent prompt friction gate | Auto Mode No Longer Requires Opt-In | 2026-05-27 |
| Deploying auto mode in headless or automated environments | Auto Mode No Longer Requires Opt-In | 2026-05-27 |
| CI/CD pipelines needing resilience when the primary model endpoint is unavailable | Fallback Model Automatic Session Switch | 2026-05-27 |
| Preventing long Claude Code sessions from breaking entirely during a model outage | Fallback Model Automatic Session Switch | 2026-05-27 |
| Building a status line script that adapts its output to terminal width | Status Line `COLUMNS`/`LINES` Env Vars | 2026-05-28 |
| Writing terminal-width-aware Claude Code status plugins | Status Line `COLUMNS`/`LINES` Env Vars | 2026-05-28 |
| Installing plugins from repos with heavy LFS assets on slow or metered networks | `skipLfs` Option for Plugin Marketplace Sources | 2026-05-28 |
| Speeding up plugin installs in CI/CD environments where LFS content isn't needed | `skipLfs` Option for Plugin Marketplace Sources | 2026-05-28 |
| Avoiding repeated macOS permission prompts after each Claude Code upgrade | macOS Background Agent Permission Persistence | 2026-05-28 |
| Granting Claude Code background agents macOS Privacy permissions that survive upgrades | macOS Background Agent Permission Persistence | 2026-05-28 |
| Deploying full Managed Agents (webhooks, multiagent orchestration, self-hosted sandboxes) under AWS billing and IAM | Managed Agents Full Stack on Claude Platform on AWS | 2026-05-29 |
| Enterprises running Managed Agent sandboxes on AWS for data-residency compliance | Managed Agents Full Stack on Claude Platform on AWS | 2026-05-29 |
| Creating and testing a custom team plugin locally without publishing to a marketplace | Auto-loading Local Plugins + `claude plugin init` | 2026-05-29 |
| Scaffolding a new Claude Code plugin in a project's `.claude/skills` folder | Auto-loading Local Plugins + `claude plugin init` | 2026-05-29 |
| Switching between git feature branches inside a single Claude Code session without restarting | `EnterWorktree` Mid-Session Switch | 2026-05-29 |
| Cleaning up Claude-managed git worktrees after session completion without worrying about locks | `EnterWorktree` Mid-Session Switch | 2026-05-29 |
| Building session-aware MCP tools that identify the calling Claude Code session | Stdio MCP Session Env Vars | 2026-05-28 |
| Correlating MCP server logs with specific Claude Code session IDs for debugging | Stdio MCP Session Env Vars | 2026-05-28 |
| Enterprise Bedrock/Vertex/Foundry teams enabling Claude Code auto mode without a separate API account | Auto Mode on Bedrock/Vertex/Foundry | 2026-05-30 |
| Deploying auto mode in cloud-provider Claude Code environments for unattended agentic workflows | Auto Mode on Bedrock/Vertex/Foundry | 2026-05-30 |
| Preventing Claude Code from silently modifying shell startup files that affect command execution | Security Prompts for Shell Startup & Build-Config Writes | 2026-06-02 |
| Auditing which build-tool config files Claude writes in auto-approved (`acceptEdits`) sessions | Security Prompts for Shell Startup & Build-Config Writes | 2026-06-02 |
| Triggering Claude Code's dynamic multi-agent workflow mode using the new `ultracode` keyword | `ultracode` Dynamic Workflow Trigger | 2026-06-02 |
| Diagnosing why "workflow" prompts no longer spawn sub-agents after upgrading Claude Code | `ultracode` Dynamic Workflow Trigger | 2026-06-02 |
| Editing a file immediately after grepping for a symbol without a separate Read round-trip | Edit after Grep (No Pre-Read Required) | 2026-06-02 |
| Reducing unnecessary read operations in agentic grep-then-patch workflows | Edit after Grep (No Pre-Read Required) | 2026-06-02 |
| Enforcing a named agent persona per project so every background session uses the right config | `--agent` Flag + `agent` in settings.json | 2026-05-29 |
| Overriding the default agent for a one-off dispatched task without editing config files | `--agent` Flag + `agent` in settings.json | 2026-05-29 |
| Tracing exact shell commands and MCP calls Claude Code executes for enterprise audit logging | `OTEL_LOG_TOOL_DETAILS` Tool Decision Telemetry | 2026-05-29 |
| Building per-tool usage dashboards for Claude Code in an OpenTelemetry observability stack | `OTEL_LOG_TOOL_DETAILS` Tool Decision Telemetry | 2026-05-29 |
| Segmenting Claude Code usage metrics by team or repository in a shared OTEL backend | `OTEL_RESOURCE_ATTRIBUTES` as Metric Labels | 2026-06-02 |
| Building per-team cost dashboards by attaching custom resource attribute labels to metrics | `OTEL_RESOURCE_ATTRIBUTES` as Metric Labels | 2026-06-02 |
| Agentic workflows fanning out parallel Bash calls that should continue even if one fails | Parallel Tool Call Independence | 2026-06-02 |
| Preventing a single failed tool call from masking results from other parallel batch tools | Parallel Tool Call Independence | 2026-06-02 |
| Keeping long-running background Claude Code agents on the latest version without manual restarts | Background Agent Sessions Auto-Update | 2026-06-04 |
| Ensuring background agents pick up security or bug-fix releases automatically | Background Agent Sessions Auto-Update | 2026-06-04 |
| Injecting post-run diagnostics back into Claude's context from a Stop hook without a hook error | `Stop`/`SubagentStop` Hook `additionalContext` | 2026-06-04 |
| Building stop-event pipelines that pass structured feedback into Claude's next run | `Stop`/`SubagentStop` Hook `additionalContext` | 2026-06-04 |
| Auditing which Claude Code plugins are active vs. disabled across a team setup | `/plugin list` Command | 2026-06-04 |
| Scripting plugin inventory checks or enabling/disabling via filter flags | `/plugin list` Command | 2026-06-04 |
| Enterprises enforcing a minimum Claude Code version org-wide after a security patch | `requiredMinimumVersion`/`requiredMaximumVersion` Managed Settings | 2026-06-04 |
| Blocking overly new Claude Code versions from being used pending IT vetting | `requiredMinimumVersion`/`requiredMaximumVersion` Managed Settings | 2026-06-04 |
| Detecting when a background Claude Code agent is stuck waiting on a permission prompt | `waitingFor` Field in `claude agents --json` | 2026-06-03 |
| Building dashboards that distinguish active from blocked/waiting Claude Code sessions | `waitingFor` Field in `claude agents --json` | 2026-06-03 |
| Monitoring real-time fanout progress across parallel Claude Code sub-agents at a glance | `claude agents` Fanout Progress Display | 2026-06-02 |
| Identifying the bottleneck sub-task during a large parallel agentic run | `claude agents` Fanout Progress Display | 2026-06-02 |
| API/SDK integrations that need native Grep/Glob search in restricted tool sets | Grep/Glob via `--tools` Dedicated Search | 2026-06-03 |
| Previewing and editing a slash command before running it (adding arguments first) | Slash Command Autocomplete Fill | 2026-06-03 |
| Avoiding accidental immediate slash command execution when browsing the autocomplete menu | Slash Command Autocomplete Fill | 2026-06-03 |

## Development & API

| Situation | Feature | Date |
|-----------|---------|------|
| Reducing cost and latency in agentic pipelines by capping the advisor model's output length | Advisor Tool `max_tokens` Parameter | 2026-06-02 |
| Controlling advisor response length to get only a brief strategic hint at lower token cost | Advisor Tool `max_tokens` Parameter | 2026-06-02 |
| Avoiding charges for API requests that are refused before Claude generates any output | No Billing for Zero-Output Refusals | 2026-06-02 |
| High-volume moderation pipelines that need to track refusal rates without incurring extra cost | No Billing for Zero-Output Refusals | 2026-06-02 |
| Discovering project-relevant plugins automatically when entering a new codebase | `/plugin` Discover Tab Context Pinning | 2026-05-28 |
| Surfacing context-appropriate plugins without browsing the full marketplace | `/plugin` Discover Tab Context Pinning | 2026-05-28 |
| Reducing per-turn token overhead for Opus 4.8 sessions in Claude Code | Lean System Prompt as Default | 2026-05-28 |
| Diagnosing unexpected Claude Code behavior changes after upgrading to Opus 4.8 | Lean System Prompt as Default | 2026-05-28 |
| Long-horizon agentic coding tasks requiring the most capable Claude | Claude Opus 4.8 | 2026-05-28 |
| Large-document analysis pipelines needing 1M context by default | Claude Opus 4.8 | 2026-05-28 |
| Migrating from Opus 4.7 at the same pricing | Claude Opus 4.8 | 2026-05-28 |
| Injecting updated instructions into a long Claude session without invalidating the cache prefix | Mid-Conversation System Messages | 2026-05-28 |
| Multi-turn agents that need to dynamically adjust Claude's behavior mid-session | Mid-Conversation System Messages | 2026-05-28 |
| Routing different types of declined requests to the right fallback or human review | Refusal Categories in `stop_details` | 2026-05-28 |
| Showing users context-specific messaging when Claude declines a request | Refusal Categories in `stop_details` | 2026-05-28 |
| Getting Opus 4.8 speed at 2.5× with a 2× price premium | Fast Mode for Opus 4.8 | 2026-05-28 |
| Auditing integrations using Opus 4.6 fast mode before the ~June 28 removal deadline | Fast Mode for Opus 4.6 Deprecated | 2026-05-28 |
| Automating complex multi-phase tasks with up to 1,000 parallel background sub-agents | Claude Code Workflows | 2026-05-28 |
| Monitoring and managing long-running agentic pipelines from `/workflows` | Claude Code Workflows | 2026-05-28 |
| Caching shorter Opus 4.8 prompts (1k–5k tokens) that fell below the Opus 4.7 minimum | Prompt Cache 1,024 Token Minimum on Opus 4.8 | 2026-05-28 |
| Running a build or test in the background without blocking the current Claude Code session | Background Shell Commands `! <command>` | 2026-05-28 |
| Launching fire-and-forget shell jobs from within a Claude Code conversation | Background Shell Commands `! <command>` | 2026-05-28 |
| Distributing a plugin that should stay inactive until users explicitly opt in | Plugin `defaultEnabled: false` | 2026-05-28 |
| Reducing default context overhead in shared Claude Code team environments | Plugin `defaultEnabled: false` | 2026-05-28 |

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
| Budgeting programmatic Claude usage (`claude -p`, GitHub Actions) separately from chat | Claude Agent SDK Credits | 2026-05-14 |
| Teams using OpenClaw or third-party Claude agents resuming subscription-backed use | Claude Agent SDK Credits | 2026-05-14 |
| Planning for the June 15, 2026 billing changeover for programmatic Claude usage | Claude Agent SDK Credits | 2026-05-14 |
| Freeing context window space mid-session without losing recent tool results | "Summarize up to here" in Rewind | 2026-05-13 |
| Archiving the early exploratory phase of a long Claude Code session | "Summarize up to here" in Rewind | 2026-05-13 |
| Resuming a background agent session without hunting through session history | `/resume` Background Session Support | 2026-05-19 |
| Seeing how long a background task ran before completing | `/resume` Background Session Support | 2026-05-19 |
| Temporarily switching models mid-session without affecting other sessions | Per-Session `/model` with `d` Default | 2026-05-19 |
| Setting a preferred default Claude Code model once from the picker | Per-Session `/model` with `d` Default | 2026-05-19 |
| Checking if a Claude Code plugin is actively maintained before installing | Plugin Last-Updated Date in Marketplace | 2026-05-19 |
| Auditing for stale plugins across a team Claude Code setup | Plugin Last-Updated Date in Marketplace | 2026-05-19 |
| Evaluating what a plugin adds before committing to installation | `/plugin` Pre-Installation Details | 2026-05-19 |
| Comparing two similar plugins on feature breadth before installing | `/plugin` Pre-Installation Details | 2026-05-19 |
| Checking whether a plugin exposes MCP servers before adding it to a team setup | `/plugin` Pre-Installation Details | 2026-05-19 |
| Running a quick vs. deep code review in the same session without changing global effort | `/code-review` Command with Effort Level | 2026-05-21 |
| Automatically applying code quality improvements from a review to the working tree | `/code-review --fix` Apply Mode | 2026-05-27 |
| Using `/simplify` to find and apply reuse/simplification improvements in one shot | `/code-review --fix` Apply Mode | 2026-05-27 |
| Reloading custom skills mid-session after editing a skill file | `/reload-skills` Command | 2026-05-27 |
| Picking up a newly added skill from a shared directory without restarting Claude Code | `/reload-skills` Command | 2026-05-27 |
| Keyboard-navigating large diffs in Claude Code without switching to the mouse | `/diff` Detail View Keyboard Navigation | 2026-05-22 |
| Reading AI-generated task lists or action plans as visual checkboxes in Claude Code output | GFM Task List Rendering in Claude Code | 2026-05-22 |
| Identifying which plugins or subagents are consuming the most Claude Code quota | `/usage` Per-Category Breakdown | 2026-05-22 |
| Auditing per-MCP-server token cost in complex Claude Code tool stacks | `/usage` Per-Category Breakdown | 2026-05-22 |
| Debugging unexpected cache misses in multi-turn production API pipelines | Cache Diagnostics (Public Beta) | 2026-05-13 |
| Identifying why prompt cache isn't hitting between conversation turns | Cache Diagnostics (Public Beta) | 2026-05-13 |
| Teams relying on Stainless-hosted SDK generation planning migration before shutdown | Anthropic Acquires Stainless | 2026-05-18 |
| Tracking Anthropic's SDK toolchain ownership and developer ecosystem investment | Anthropic Acquires Stainless | 2026-05-18 |

## Funding & Company News

| Situation | Feature | Date |
|-----------|---------|------|
| Enterprises finding pre-vetted Claude consulting/SI partners by tier and region | Claude Partner Network Services Track & Partner Hub | 2026-06-03 |
| Consulting firms tracking certification counts and deployments to qualify for tier promotion | Claude Partner Network Services Track & Partner Hub | 2026-06-03 |
| Channel partners planning their Claude practice around the January/July tier review cycle | Claude Partner Network Services Track & Partner Hub | 2026-06-03 |
| Assessing Anthropic's financial runway before a multi-year platform commitment | Anthropic Series H ($65B / $965B valuation) | 2026-05-29 |
| Tracking the Claude vs. GPT competitive landscape ahead of potential IPOs | Anthropic Series H ($65B / $965B valuation) | 2026-05-29 |

## Research & Security

| Situation | Feature | Date |
|-----------|---------|------|
| Catching injection flaws and insecure patterns in code before they reach a PR | Security Guidance Plugin for Claude Code | 2026-05-27 |
| Automatically reviewing every AI-generated code change for ~25 vulnerability classes | Security Guidance Plugin for Claude Code | 2026-05-27 |
| Running instant, zero-cost vulnerability scanning on every file save in Claude Code | Security Guidance Plugin for Claude Code | 2026-05-27 |
| Grounding a financial research agent in primary SEC filings with citations | Web Search Tool SEC Filing Data | 2026-05-18 |
| Earnings analysis or due-diligence workflows requiring cited primary sources | Web Search Tool SEC Filing Data | 2026-05-18 |
| Evaluating Claude Mythos for large-scale defensive security analysis before requesting access | Project Glasswing: First Quantified Results | 2026-05-22 |
| Benchmarking AI-assisted vulnerability discovery against human researcher baselines | Project Glasswing: First Quantified Results | 2026-05-22 |
| Tracking Anthropic's cybersecurity research progress ahead of a broader Mythos release | Project Glasswing: First Quantified Results | 2026-05-22 |
| Security teams benchmarking AI-assisted threat actor TTPs against the MITRE ATT&CK framework | AI-Enabled Cyber Threats MITRE ATT&CK Analysis | 2026-06-03 |
| Defenders prioritizing post-compromise controls as AI shifts attacker focus from initial access | AI-Enabled Cyber Threats MITRE ATT&CK Analysis | 2026-06-03 |
| Enterprise risk teams tracking the evolving AI threat landscape ahead of ATT&CK framework updates | AI-Enabled Cyber Threats MITRE ATT&CK Analysis | 2026-06-03 |
| Critical infrastructure operators (power, water, healthcare, comms) seeking Glasswing access | Project Glasswing Expansion: 150 New Orgs | 2026-06-02 |
| Tracking Anthropic's scaling of AI vulnerability discovery to ICS/OT and critical infrastructure | Project Glasswing Expansion: 150 New Orgs | 2026-06-02 |
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
| Enterprise consulting teams evaluating Claude for large-scale staff deployment and certification | PwC–Anthropic Expanded Alliance | 2026-05-14 |
| Finance/CFO-office workflows seeking Claude-native tooling via PwC's Office of the CFO group | PwC–Anthropic Expanded Alliance | 2026-05-14 |
| Assessing Anthropic's Big Four presence before an enterprise Claude adoption decision | PwC–Anthropic Expanded Alliance | 2026-05-14 |
