DEALSBOT — GROK BUILD EXECUTION PACK
======================================

PURPOSE

This pack is optimized specifically for xAI Grok Build, not generic LLM prompting.

Use it to build the Linux Deals Bot phase-by-phase with Grok Build while exploiting the parts of Grok Build that matter most:

- AGENTS.md repository instructions
- Plan mode before major edits
- /goal for bounded long-running implementation
- grok inspect before execution
- parallel subagents for exploration / testing / adversarial review
- git worktrees only for genuinely independent workstreams
- hooks for deterministic verification
- project-scoped .grok/config.toml
- MCP servers only when needed and narrowly permissioned
- headless mode for repeatable verification/CI
- sandbox + permission rules rather than always-approve/yolo

CURRENT GROK BUILD WORKFLOW

At the start of the repo:

1. Install Grok Build.
2. cd into the repository.
3. Run:
   grok inspect
4. Confirm it discovered:
   - AGENTS.md
   - .grok/config.toml
   - skills/plugins/hooks/MCP only if intentionally configured
5. Start Grok Build.
6. For a new phase:
   - open the matching phase .txt
   - enter Plan mode
   - ask Grok to inspect the repo and produce a concrete phase plan
   - approve/rewrite the plan
   - run the approved implementation as a bounded /goal
7. While /goal runs:
   - steer only when needed
   - do not broaden scope
8. When the goal claims completion:
   - run the required verification commands
   - inspect diffs
   - run an independent review/audit subagent for high-risk phases
   - commit only after green verification
   - STOP before the next phase

DO NOT USE ALWAYS-APPROVE/Y0LO FOR THESE PHASES.

Use narrow permissions and a workspace/strict sandbox. The build pack intentionally requires review gates before code changes and before commits.

SUBAGENT RULE

Use parallel subagents for:
- repository exploration
- source-of-truth research
- independent test design
- independent arithmetic/oracle derivation
- adversarial review
- documentation verification

Do NOT let multiple subagents edit the same shared files in parallel.

If worktrees are used:
- each worktree must own disjoint files/workstreams;
- final integration happens in one parent session;
- run the full gate after integration.

PHASE DISCIPLINE

IMPLEMENT -> TEST -> VERIFY -> DOCUMENT -> COMMIT -> STOP

Every phase is bounded.
Never start the next phase automatically.
Never pull later-phase work forward because it looks convenient.

PRIMARY PRODUCT TARGETS

- Apple Mac Studio
- exactly 128GB MacBook Pro
- laptops with NVIDIA GeForce RTX 5090 Laptop GPU
- desktop/workstation/prebuilt/custom PCs with desktop NVIDIA GeForce RTX 5090

Identity rule:
DESKTOP RTX 5090 != RTX 5090 LAPTOP GPU.

DEAL DEFAULTS

- New: usually >=10–15% below best current reputable price
- Open-box/refurb: usually >=15–25% below comparable new
- Used/private: usually >=20–30% below recent sold comps after risk/condition/friction
- Normal Deal Score alert floor >=80
- DND: stay silent on weak/no/stale/duplicate/blocked opportunities

SOURCE REALITY

Before the live-source phase:
- fixture/manual evidence only;
- no fake “monitoring Amazon/eBay/etc.” claims.

After live sources:
- each source must be individually capability-certified;
- no capability inference;
- no CAPTCHA/WAF/auth/paywall/rate-limit bypass.

HIGH-RISK AUDIT RULE

For financial, optimization, compatibility, arbitrage and alert-safety phases:
do not trust green tests alone.

Require an independent semantic oracle or independently derived expected result wherever practical.

The dangerous historical bug class is:
correct arithmetic attached to the wrong classification.

Examples:
- asking vs sold
- gross vs net
- estimated vs known
- reusable vs unknown-price
- actionability vs safety
- compatible vs merely present
- landed cost vs cash capital committed
