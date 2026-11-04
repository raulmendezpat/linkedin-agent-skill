---
name: li-safe
description: >-
  Check a LinkedIn draft (post, comment, profile section, DM) for content an
  employee of a government agency should not publish: confidential project
  details, security architecture, procurement information, internal names,
  and official comment on policy. Use before anything from this pack is shown
  as copy-ready, or when the user asks "is this safe to post".
---

# li-safe

The user works in the Queensland public sector. Their posts are personal, but
public officers are still bound by the Code of Conduct for the Queensland
Public Service and their agency's social media policy. This skill reads a
draft and returns PASS, REWRITE or BLOCK, with the reason for every flag.

Read `~/.claude/linkedin/voice.md`, section "Off limits", first. Anything
listed there is a BLOCK.

## BLOCK (do not publish, propose a different angle)

- Security architecture: network topology, IAM design, firewall, VPN or
  tunnel details, vendor versions, account or tenant identifiers, anything
  that helps an attacker.
- Active procurement: an EOI, RFQ or tender that is open or under evaluation,
  vendor names in that context, budget figures, evaluation criteria.
- Internal decisions not yet public: board or review group outcomes, business
  cases, funding, restructures.
- Personal information about colleagues, the public or incident data.
- Speaking for the agency, or commenting on government policy in a way that
  could read as the official view.

## REWRITE (fine once generalised)

- A real project described with internal names. Rewrite to the pattern:
  "an emergency services agency integrating rostering with incident
  management", not the system or project name.
- Numbers from internal reports. Keep only figures that are already public,
  or use a range or ratio the user confirms is publishable.
- The employer named alongside an opinion. Keep the opinion, drop the link to
  the employer, or add "views are my own" in the profile, not the post.

## PASS

Lessons, patterns, opinions about the craft, public frameworks (TOGAF, AWS
Well-Architected), certifications, study, conference talks, and anything
already published by the agency itself (link to it rather than restating it).

## Output

```
LI-SAFE  REWRITE
  line 2   names an internal system and project   -> generalise
  line 5   cites an evaluation outcome            -> remove
```

Then the rewritten draft. If the verdict is BLOCK, do not rewrite around it;
say what the post could be about instead. When unsure, flag it and tell the
user to check with their manager or the agency's communications team. This
skill is a checklist, not legal or HR advice.

References:
- Queensland Government, Personal use of social media guideline (QGEA):
  https://www.forgov.qld.gov.au/information-and-communication-technology/qgea-policies-standards-and-guidelines/personal-use-of-social-media-guideline
- Crime and Corruption Commission, Social media and the public officer (2017):
  https://www.ccc.qld.gov.au/sites/default/files/Docs/Publications/CCC/Corruption-Prevention-Advisory-Social-media-and-the-public-officer-2017.pdf
