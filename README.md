# Security Audits

Independent security reviews of open-source projects, produced with a
deterministic-scanner + manual-triage methodology:

1. **Secret sweep** - gitleaks over working tree AND full git history
   (a secret removed from HEAD still lives in every clone).
2. **Static analysis** - semgrep (`--config auto` or the repo's own rules),
   every finding triaged by reading the flagged code - reachability,
   attacker-controlled input, blast radius. Noise is dismissed with a stated
   reason, never silently.
3. **Dependency audit** - pip-audit / equivalent against pinned requirements.
4. **Manual review** - auth/session flow, injection paths, SSRF candidates,
   XSS rendering, file handling, approval/governance gates.
5. **Deliverable** - findings table (severity / location / verdict / action)
   plus a self-contained HTML report and a Coverage note listing exactly what
   ran and what was skipped.

Methodology adapted from the OpenWorker `security` coworker
(github.com/andrewyng/openworker) - drive proven scanners, don't replace
them; the reviewer's value is context the scanner can't see.

## Reports

| Date | Target | Findings | Report |
|---|---|---|---|
| 2026-11-01 | [jalemieux/bot_board](https://github.com/jalemieux/bot_board) | 1 high (Pillow 12.3.0, 39 CVEs on image decode), 1 medium (Starlette host-header), 2 low, 1 info - 44 findings triaged as noise | [HTML](bot-board/bot-board-2026-11-01.html) |

bot_board was also reported upstream: jalemieux/bot_board#338.
