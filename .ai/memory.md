# memory.md · [AppName]
<!--
  AGENTS.md loads automatically every query — this file does NOT. Attach it
  manually via the Context drawer at the start of a work session (add
  docs/tsa/TSA-X-FULL.md too, only if the task is MODE 3).
  AI maintains this file. Human pastes MEMORY UPDATE blocks here after each
  session. Workflow: copy === MEMORY UPDATE === from the AI's response →
  paste into [LOG] → save.
-->

## [PROJECT]
Name    : [AppName]
Stack   : [stack]
Root    : [path]
Created : [date]

## [ENV & PORTS]
(fill as discovered — ports, DB paths, API key locations, service names)

## [KNOWN LIMITS]
(rate-limit tables per [RATE LIMIT PROTOCOL] in TSA-X-FULL.md, only if the
project calls an external API — model / RPM / TPM / RPD / source)

## [OPEN ISSUES] ← AI reads this before starting any work
STATUS      PRI   DESCRIPTION
─────────────────────────────────────────────────────────
(none)

Add:     UNRESOLVED  HIGH/MED/LOW  [desc] | Suspect:[x] | File:[x] | Next:[x]
Resolve: move to [LOG] with RESOLVED tag

## [LOG] ← paste MEMORY UPDATE blocks here, newest on top
[date]  INIT — Project initialized
        Stack: [stack] | Root: [path]

## [FILE INDEX]
FILE                         LAST TOUCHED
─────────────────────────────────────────
.ai/memory.md                [date]

## [NOTES]
(manual: credential locations, non-standard ports, naming conventions, team decisions)
