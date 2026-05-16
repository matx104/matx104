# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

> **Operating contract**: This file follows the sovereign template at
> `~/PROJECTS/CLAUDE_SOVEREIGN_TEMPLATE.md`. The sovereign rules apply
> (additive enhancement, invent nothing, evidence before conclusion).

> **Classification**: GitHub profile README repo
> (`matx104/matx104`) — the special-named repo whose README.md
> renders on the user's GitHub profile page. **High-visibility
> public surface.** Content is the user's professional bio,
> credentials, and project highlights. All factual claims
> (certifications, employment, dates) require user verification.

## Project Overview

This is the **GitHub profile README** repo for [matx104](https://github.com/matx104). The `README.md` at the root of this repo renders directly on the user's GitHub profile page. Content advertises the user as a DevSecOps Engineer / Cloud Security Architect / CISSP-certified, currently featured with an animated header banner.

## Repository Truths

- **Stack**: markdown only — no static-site stack at the repo level
- **Render target**: GitHub profile page (auto-rendered by GitHub)
- **No deploy step** — committing to `main` updates the profile immediately

## Existing Project Conventions

- Animated header banner via capsule-render.vercel.app
- Profile-style markdown with badges, stats widgets, etc.
- Crown / matrix-green visual identity consistent with the matx104 ecosystem

## Claude Operating Doctrine

- **Factual claims need user verification.** Cert numbers, employment dates, certification expirations.
- **Don't break the existing visual flow.** Animated banner + badges + stats widgets — preserve these unless replacing intentionally.
- **No engagement-bait language.** Keep the tone honest and technical.
- **External image services**: many profile READMEs use external services (shields.io, capsule-render, github-readme-stats). These are public CDN-style services — fine, but be aware they could break. Don't add new external services without user approval.

## Session Discipline

One scope per session.

## Task Execution Rules

Markdown changes — preview by viewing the rendered README on a forked test repo or using a markdown renderer locally before pushing.

## Testing & Stability Gates

None automated. Visual review on GitHub itself after push.

## Deployment & Verification

Push to `main` — GitHub renders the README on the profile page within seconds. Verify at [github.com/matx104](https://github.com/matx104).

## Epistemology & Evidence Rules

Profile content is public bio. Every claim is verifiable; don't include claims that can't be verified by a third party (e.g. linked certs, linked employers, linked projects).

## UI / System Design Rules

- Preserve animated banner (capsule-render.vercel.app) unless replacing intentionally
- Preserve matrix-green / crown identity
- Don't add tracking pixels or analytics (profile READMEs don't need them and the user has expressed privacy preferences in adjacent repos)
- Accessibility on alt text for all images / banners

## Completion Standard

- Factual claims user-verified
- Rendered profile page checked on GitHub after push
- Visual identity preserved
- Repo memory preserved

---

## Agent skills

### Issue tracker

GitHub Issues at `matx104/matx104`, accessed via the `gh` CLI. See `docs/agents/issue-tracker.md`.

### Triage labels

Canonical five-role vocabulary plus profile-flavour labels (`bio-update`, `banner`, `stats-widget`, `cert-update`, `social-link`). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context layout — `CONTEXT.md` + `docs/adr/` at the repo root (create lazily). See `docs/agents/domain.md`.
