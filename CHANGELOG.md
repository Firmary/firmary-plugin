# Changelog

## 1.4.2

- MIT license (copyright 2026 Firmary) replaces the proprietary distribution terms. Claude, Cursor, and Grok manifests declare `MIT`.
- Adds `assets/logo-cursor.png` (512×512, the existing logo on a solid `#171715` plate) and points the Cursor manifest logo at it.
- All manifests (Claude, Cursor, Grok) are at 1.4.2.

## 1.4.1

- `firmary-billing-follow-up`: asking to prepare or draft a reminder stops at the draft; nothing is sent until you ask to send it.
- `firmary-daily-oversight`: before copying a client's details into a shared draft, the assistant confirms in Firmary that everyone the draft is shared with can open that client; otherwise it keeps the draft private to you or leaves that client out.
- All manifests (Claude, Cursor, Grok) are at 1.4.1.

## 1.4.0

- Adds the seven Firmary workflow skills: onboarding, collection review, work management, engagement signatures, billing follow-up, daily oversight and firm setup. They are the same skills as the Claude plugin firms download from Firmary, generated from one source, with tool guidance kept as metadata and no pre-approved tools.
- README lists every skill and points a firm's clients to PocketFirm's own plugin (`app.pocketfirm.app`).
- All manifests (Claude, Cursor, Grok) are at 1.4.0.

## 1.3.3

- Brand icons are PNG instead of SVG so the package contains only file types the Claude plugin directory accepts from every publisher.

## 1.3.2

- Proprietary distribution terms replace MIT for this release.
- Package contains integration metadata, connection settings, skills and branding; the hosted application implementation remains private.

## 1.3.1

- Staff plugin only. Adds the `get-started` skill (what you can ask for, household setup, how approvals work).
- Brand icons (light and dark) and the support, privacy and terms links in the Claude manifest.
- Keywords updated.
- Delegated work is not described here: it isn't qualified on a real host yet.
- All manifests (Claude, Cursor, Grok) are at 1.3.1.

## 1.0.0

- Initial release: Firmary remote MCP connector and the Firmary skill.
