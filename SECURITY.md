# Security Policy

## Supported versions

This project is a browser-based tool with a static frontend and PWA support. Security fixes are expected to land in the latest version on the default branch and in the latest published release.

| Version | Supported |
| --- | --- |
| Latest release | Yes |
| Current `main` branch | Yes |
| Older releases | No |

## Reporting a vulnerability

Please do **not** open a public issue for suspected security problems.

Instead:

1. Use GitHub private vulnerability reporting for this repository, if it is enabled.
2. If private reporting is not available, contact the maintainer through a private channel you already have.
3. Include clear reproduction steps, affected files or pages, browser and OS details, and impact.
4. If possible, include a minimal proof of concept.

Please allow reasonable time for investigation and a fix before disclosing details publicly.

## What is in scope

This repository is a client-side refresh rate and FPS testing tool with a static site and service worker / PWA behavior. Relevant reports may include:

- Cross-site scripting (XSS) or unsafe DOM injection
- Service worker or cache behavior that can create unexpected trust, persistence, or update issues
- Security problems caused by unsafe handling of URL parameters or other user-controlled input
- Supply chain issues caused by introduced third-party scripts, packages, or remote assets
- Clickjacking or embedding behavior that meaningfully changes security expectations
- Any issue that could let an attacker run script in the site origin, alter trusted app behavior, or mislead users about what code is running offline

## Out of scope

The following are usually **not** considered security vulnerabilities for this project:

- Incorrect refresh-rate measurements, FPS calculations, ghost counts, or visual estimates
- Browser, GPU driver, monitor, operating system, or hardware limitations
- General performance problems that do not create a security impact
- Feature requests, UX complaints, or compatibility bugs without a security consequence
- Missing hardening headers on platforms where this repository does not control deployment headers directly
- Problems caused only by running modified local copies of the code

## Security expectations

This project is intended to work without a backend account system or server-side processing. Reports are most useful when they focus on risks that affect visitors of the deployed site or users of the offline PWA experience.

If you are unsure whether something qualifies, report it privately anyway with a concise impact explanation.
