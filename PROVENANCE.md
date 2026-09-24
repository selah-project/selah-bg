# PROVENANCE — how this rendering came to be

*Bulgarian (Български), chair 95. Lit 2026-09-22. Floor 23,213 verses.*

This is the record of how the text in this repository was produced and
what went wrong with it. A machine-assisted rendering has no standing
unless you can see how it was made, so this file says both. The
pass-by-pass working notes, with the residue counted, are in
[NOTES.md](NOTES.md).

---

## The approach

Every verse is rendered from the Hebrew of that verse, under a written
discipline — `docs/methodology/translation-discipline/bg.md` in the
Selah repository, itself written in Bulgarian, because whoever writes
the verses reads Bulgarian and not English. It was built on `sr.md`
(Serbian, Cyrillic), `cs.md` (Czech) and `hil.md`. Seven rules govern
it: the Hebrew word passes word by word; the Names stay Names; both
truths of Deuteronomy 6:4; no foreknowledge (Genesis 22:1 does not know
Genesis 22:13); numbers and letters untouched; no translator's notes;
the heavy verse goes in bare — ketiv is the ground, qere is a lens.

**The `⟨ ⟩` brackets do two different jobs.** `⟨את⟩` is the Hebrew
direct-object marker, which Bulgarian has no word for; it is left
standing so the reader sees it. `⟨дума⟩` is a word the Hebrew did not
write but the Bulgarian sentence requires — visibly marked, so you can
always tell what the Hebrew said from what the grammar needed.

Every verse file names the model that wrote it: **glm-5.3**, on the
**glm-5.2** tier.

## The morphological outpost, decided before the fire

Bulgarian has **lost the nominal cases**, so the ratified case-suffix
ruling — which governs Serbian, Russian and Czech — does not bind this
chair; it is the first where that is true. In its place Bulgarian has
the **postposed definite article** (-ът / -ят / -та / -то / -те), and
the ruling taken before the burn was that **the article does not attach
to a Name**: *Яхве · на Яхве · за Яхве*, never *Яхвето*. The vocative,
alive in Bulgarian (Боже, Господи), was ruled off for Names as well.
On common nouns the article stays lawful — there it is ordinary
grammar, not a broken stem.

## The Name

| Hebrew | here | rejected |
|---|---|---|
| יהוה | **Яхве** | Господ · ГОСПОД · Иеова · Йехова · Бог |
| אלהים | **Елохим** | Бог, when it stands for the One |
| אדני | **Адонай** | Господ |
| אל · אל שדי | **Ел · Ел Шаддай** | Бог · Всемогъщий |
| יה | **Ях** | Господ |
| צבאות | **Цеваот** | "на силите" · "на войнствата" |

**Яхве stands in 6,007 of 6,007 seats** — every bare `יהוה` in the
letter stream — and not one Господ, Бог, Йехова, Ягве or Адонай on a
Name seat. Counting prefixed forms too, 6,825 of the floor's 6,828
tokens still carry the letters יהוה in their surface; the three that do
not are surfaces awaiting restore (Exod 28:29, pointed; 2 Chr 34:26,
`יהווה` twice), and their glosses read Яхве as well.

*богове* over the nations' gods (Exodus 20:3) and *господарю* over a
human lord (Genesis 23:6) remain lawful; that distinction is applied by
the token's Hebrew surface, never by the spelling.

## The burn and the relights

| step | result |
|---|---|
| lit | 10:53 UTC, engine-side relay (`relay-move-on!`), batch 4 → batch 2 → move on |
| first pass | 18,267 of 23,213 by 11:32; `:done` at 16:35 with residue 66 |
| relit 16:41 | after a count-mismatch prune of 112 files → complete, residue 0, at 16:45 |
| relit 16:56 | after the census convicted 1,072 → landed 17:18, residue 4 |
| relit 17:23 | after the close-out convicted 174 |
| final gate | 17:31 UTC — **23,212 of 23,213**, the Name clean at full count |

The corpus was committed to git at its first landing (`6af01ae`), before
the census passes touched it, so every repair is a diff you can read.

**The relay never retries a verse that is present but wrong.** It fills
only what is *missing*, so a file present with an empty token array, or
with a row more or fewer than the floor, is never picked up again.
`count_mismatch_prune.py bg --apply` found 112 such files at the first
landing and 8 more after the refill — **four of them with zero rows
against a floor of 14 to 21.**

## Finding: on a Cyrillic chair the homoglyph risk runs both ways

Every Latin-script chair hunts Cyrillic or Greek hiding inside Latin
words. Bulgarian is Cyrillic, so the risk reverses — and it ran in both
directions at once:

| fault | direction | found |
|---|---|---|
| homoglyph | Latin letters inside Cyrillic words | 292 |
| corrupted surface | Cyrillic letters inside the **Hebrew** surface | 718 |

The homoglyphs are invisible to the eye: `Узa` · `народa ми` ·
`синoвете` · **`Шувael`**. The first-hour gate caught `заченa` at
Genesis 4:17 with a Latin `a` — and then a Latin `e` was typed inside
`свe` in the very script written to hunt the fault. That is why the
probe exists.

The corrupted surfaces are the documented fleet mechanism — *each chair
spends its own alphabet into the Hebrew* — and this one spends Cyrillic:
`мלך` for מלך, `кי` for כי, `האופנim` for האופנים, `лбайт` for לבית.
`surface_restore.py bg --apply` restored all **718 → 0** against the
floor. Nothing was laundered; the floor holds the true surface.

## Two findings the auditors could not see

- **Placeholders reach production in more than one shape.** 1 Kings
  18:19 carried **`<празен>`** — Bulgarian for *empty* — twice in one
  verse, where a number belongs; Exodus 24:4 carried **`⟨какво?⟩`**,
  Bulgarian for ***what?***, inside marker brackets; Ezra 8:31 carried
  `⟨⟩`. **A word-shaped or question-shaped placeholder passes every
  marker and parity check there is.** Filed fleet-wide as suspect 48.
- **A number token can receive the next word's gloss** — `twelve →
  камъка` (stones) · `hundred → таланта` · `fifty → годишни`
  (years-old) · `seven → овни` (rams). An off-by-one in alignment,
  invisible to the marker and parity auditors; filed as suspect 49.
  Numbers 26:22 also glossed *seventy* as **и шейсет** — sixty.

## Finding: read the class back before deleting anything

This was not a precaution on this chair; it was the difference between
a clean rendering and a butchered one.

| probe | first fired | after the read-back | what it was |
|---|---|---|---|
| a rails-word scan | **307 files** | **0** | `начал` substring-matched `начало` and `началник` — not one whole-word hit |
| number | **1,355** | **31** | English *one* is an indefinite pronoun, *first* renders пръв, and the **Hebrew dual** (*the two horns*) is rightly plural in a language with no dual |
| convict | 1 | 0 | `седалка` at Song 3:10 |

**Over 1,500 clean Bulgarian verses were one unread list away from
deletion.** And twice on this chair a rails-word turned out to be a
Bible word: **знак** is the right rendering of `אוֹת` (the bow in the
cloud, the mark on Cain) and **седалка** of `מֶרְכָּבוֹ` (Solomon's
palanquin). **A rails-word that is also a Bible word is not a
rails-word.**

Russian and Serbian bleed was real, though — 393 verses convicted and
refilled: `И било` for `וַיְהִי` where Bulgarian says *И беше*;
**`сыновете`**, Russian *сыновья* fused with the Bulgarian article;
`который`, `этози`; the Russian-only ы э ё and the Serbian set.

## The cure, in order

| pass | what |
|---|---|
| count-mismatch prune | 112 files, then 8 more |
| census → convict | **1,072 files** refilled |
| surface restore | **718 → 0** corrupted Hebrew surfaces |
| flow parity | 124 marker losses fixed; 57 residue; 110 gains convicted |
| census → convict | 174 files |
| homoglyph probe | 292 Latin letters inside Cyrillic words |

No verse in this repository was written or spliced by hand; no file
carries a `hand` field. Every repair was a prune, a convict-and-refill,
or a restore against the floor.

## Open — declared, not repaired

[NOTES.md](NOTES.md) carries the residue table as the close-out left it
(bleed 49 · short 42 · homoglyph 13 · empty 13 · number 2 · one
unrendered verse; fabricated, missing, bare, erasure, convict and
flownumber all 0). Counted again at writing (2026-09-24):

- **Eleven verses whose Hebrew surface is still off the floor** — seven
  arrived **pointed** (vowels and cantillation instead of bare
  consonants: Exod 28:29 · Num 7:84 · Ezra 8:31 · Ezek 6:5 · Ezek 38:4 ·
  Josh 19:39 · 19:40), and four hold a stray Cyrillic letter or a leaked
  instruction string inside the Hebrew (Gen 48:15 · Jer 44:15 · Josh
  20:4 · Num 10:28, whose surface reads `ולסעו will be replaced: ויסעו`).
  **2 Chronicles 34:26** carries `יהווה` — a doubled vav — twice; those
  two rows still read Яхве, which is why the Name gate does not see
  them.
- **71 flows carry doubled or empty brackets** (`⟨⟨неговата⟩⟩` at
  Genesis 2:2 is the type), and **41** use ASCII `<…>` where the angle
  brackets belong. Both classes pass every marker check.
- **The ⟨את⟩ gap** — 65 flows short of their rows, 127 with a marker no
  row carries.
- **Six words** in the Bulgarian still carry a Latin letter (`Ахиjah`,
  `Анa`, `каатитe`).
- **Judgment calls flagged for Scott** in the rails and not overruled:
  **Мишкан** against the tradition's *скиния*; **Яхве** as the
  transliteration; the vocative ruled off for Names; *рече* against
  *каза* as a register, watched in case it is Church Slavonic bleed; and
  Latinization as a later, parallel layer that never displaces the
  Cyrillic.

## Final

**23,213 files.** The final gate read 23,212 of 23,213 at 17:31 UTC,
with one verse left in the residue; at writing every one of the 23,213
files carries its token rows. Яхве in **6,007 of 6,007** bare Name
seats, with no erasure word on any of them. Every corrupted surface the
close-out found was restored from the floor; the eleven named above
remain. This chair is **version 1, not seated**.
