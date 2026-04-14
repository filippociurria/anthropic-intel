# Anthropic Intel — Updates

Newest entries first. Managed by the intel scraper. Do not edit manually.

---

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
