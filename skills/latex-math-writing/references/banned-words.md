# Banned words

These words must not appear in a mathematics research paper. The ban covers
every part of the paper a reader sees: title, abstract, body, theorem
statements, proofs, footnotes, captions, section titles, acknowledgements, and
comments in the TeX source if it is distributed. It also covers inflected
forms (plural, past tense, participle, adverb) unless an entry says otherwise.

Do not swap a banned word for a synonym of the same kind. Say what is meant
mathematically: name the estimate, the quantity, the step, or the comparison.

## Absolute

**ledger** and **certificate** are banned in every context and every form:
ledger(s); certificate(s), certify, certifies, certified, certification.

## List

A qualifier in parentheses limits the ban to that use. An entry without one is
banned in every sense.

- bridge / bridging (figurative)
- budget
- certificate / certifies
- champion (verb)
- clock (figurative)
- collar
- comprehensive (as filler)
- consumer
- crank / crank out
- cutting-edge
- deep dive
- delve
- driver / drivers / driving (figurative)
- extinction
- foster
- game-changer
- gap (any sense; "the spectral gap" only as a fixed technical term of art)
- garner
- gate / gating / gatekeeper
- groundbreaking (as filler)
- harness (verb)
- holistic
- illuminate
- intricate
- landscape (figurative)
- ledger
- lens (figurative)
- leverage (verb or noun)
- marching (figurative)
- multifaceted
- navigate (figurative)
- no go / no-go
- nuanced
- panorama
- paradigm / paradigm shift
- pivotal
- producer
- ridge
- robustly
- schedule
- seamless / seamlessly
- shed light on (as filler)
- showcase
- spearhead
- state-of-the-art
- synergy
- tapestry
- toolkit
- transformative
- under the hood
- underpins
- underscore / underscores
- unlock
- unprecedented
- workhorse

## Check

Run this on the changed TeX files before accepting a draft. Then judge every
hit: absolute and unqualified entries must go, and a qualified entry goes when
it is used in the banned sense.

```bash
grep -n -i -w -E "ledgers?|certif[a-z]*|bridg[a-z]*|budget[a-z]*|champion[a-z]*|clock[a-z]*|collar[a-z]*|comprehensive[a-z]*|consumers?|crank[a-z]*|cutting-edge|deep[ -]dives?|delv[a-z]*|driv(er|ers|ing)|extinction|foster[a-z]*|game-changers?|gaps?|garner[a-z]*|gat(e|es|ed|ing|ekeepers?)|groundbreaking|harness[a-z]*|holistic[a-z]*|illuminat[a-z]*|intricate[a-z]*|landscapes?|lens(es)?|leverag[a-z]*|marching|multifaceted|navigat[a-z]*|no[ -]go|nuanced?|panorama[a-z]*|paradigm[a-z]*|pivotal|producers?|ridges?|robustly|schedul[a-z]*|seamless[a-z]*|shed(s|ding)? light|showcas[a-z]*|spearhead[a-z]*|state-of-the-art|synerg[a-z]*|tapestr[a-z]*|toolkits?|transformative|under the hood|underpin[a-z]*|underscor[a-z]*|unlock[a-z]*|unprecedented|workhorses?" <file>.tex
```

The pattern also matches command names and labels, which the reader never
sees; those hits may stay.

## Changing the list

Add or remove words only on the author's instruction, and keep the list and the
check pattern in sync.
