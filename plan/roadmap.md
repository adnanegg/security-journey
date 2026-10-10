# Roadmap: junior-hireable web/AppSec by late 2027

2h/day on weekdays (3rd hour = bonus), weekends off. Free resources only.
Detail for each stage is refined after the previous gate, so stages 1-4 are outlines.

## Gate protocol (every stage)
1. Verifiable proof (platform completion, rooted boxes without walkthroughs, etc.)
2. Fresh timed closed-book exam from Claude
3. Oral defense: explain attacks and fixes out loud
4. Published write-up in `writeups/`
Fail = gap list + targeted practice + retake with a different variant. Results go in `gates/`.

## Stage 0: Foundations (~40h)
Linux, networking, HTTP, Python/bash. See `stage-0.md` for daily missions.
Gate: diagnostic + exam + oral + write-up.

## Stage 1: Web hacking (~130h)
PortSwigger Web Security Academy (free). Core topics: SQL injection, XSS, CSRF, authentication,
access control, SSRF, file upload, path traversal, server-side flaws.
Gate: all labs of the core topics solved with no hints + exam + oral + write-up.
CV project 1: build a Next.js/Supabase app, attack it, patch it, document the fixes
(include an RLS/misconfiguration audit).

## Stage 2: Systems (~110h)
Linux and Windows privilege escalation, network attacks, Active Directory basics.
Free sources: TryHackMe free rooms, HTB free tier, OverTheWire (check what is free when you get here).
Gate: several boxes rooted without walkthroughs + exam + oral + write-up.
Decide your track (offense / blue / cloud / GRC) at the end of this stage.

## Stage 3: Blue side (~60h)
Logs, detection, MITRE ATT&CK, a home SIEM (Wazuh or ELK), Sigma-style rules, free
challenge sites (CyberDefenders, Blue Team Labs free tier).
Gate: build a detection for an attack you ran yourself + exam + oral + write-up.
CV project 2: home SOC lab with custom detection rules.

## Stage 4: Specialization (open-ended)
Bug bounty (read program scopes first, test only what is in scope), CTFs (CTFtime),
CVE hunting, open-source contributions.
CV project 3: open-source security tool (e.g. a Supabase/Next.js misconfiguration scanner).
CV project 4: public results (CTF placements, accepted bug reports).

## Certificates
Not part of the free plan. Decide around month 6 whether one is worth paying for.

## Safety
Only test systems you own or have written permission to test. Never commit secrets,
lab flags/passwords, or write-ups of active HTB machines.
