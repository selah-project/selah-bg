# bg — Български · NOTES

The Hebrew Bible rendered into Bulgarian from the Hebrew, token by token, under
the rails at `docs/methodology/translation-discipline/bg.md` (selah repo).
Version 1. **Not seated.** Every pass below is its own commit in this repo.

The Name's rail is **Яхве**. Bulgarian is Cyrillic, which moves one whole class
of fault to the opposite side of the mirror — see *the two alphabets* below.

## Burn signature

- **Lit 2026-09-22 10:53 UTC** on the serving lane, engine-side relay
  (`relay-move-on!`), batch 4 → batch 2 → move on.
- First pass reached 18,267 of 23,213 by 11:32; **`:done` 16:35 with residue 66**.
- **Relit 16:41** after a count-mismatch prune of 112 files → `:status :complete,
  :residue 0` at **16:45**, 23,213 files. Committed as this repo's first commit.
- **Relit 16:56** after the census convicted 1,072 → landed **17:18** with
  residue 4.
- **Relit 17:23** after the close-out convicted 174.

**The present-but-wrong class.** The relay fills only what is *missing*. A verse
file that is present but holds an empty token array, or a row more or fewer than
the floor, is never retried — `dev/scripts/count_mismatch_prune.py bg --apply`
hands those back. It found 112 at first landing and **8 more after the refill,
four of them with ZERO rows against a floor of 14–21.**

## The two alphabets

**Every Latin-script chair's homoglyph probe hunts Cyrillic or Greek hiding
inside Latin words. bg is Cyrillic, so the risk runs the other way**, and it runs
in *both* directions at once:

| fault | direction | found |
|---|---|---|
| **homoglyph** | **Latin letters inside Cyrillic words** | 292 |
| **corrupted surface** | **Cyrillic letters inside the HEBREW surface** | 718 |

The homoglyphs are invisible to the eye — `Узa` · `страхa от него` · `народa ми` ·
`синoвете` · `за Авиja` · **`Шувael`**. The first-hour gate caught `заченa` at
Gen 4:17 with a Latin `a`, and the shovel then typed a Latin `e` inside `свe` in
the very file written to hunt the fault. That is why the probe exists.

The corrupted surfaces are the documented fleet-wide mechanism — *each chair
spends its own alphabet into the Hebrew* — and bg spends Cyrillic:

```
мלך  → מלך      [Cyrillic ем]        лבקש → לבקש   [Cyrillic эл]
кי   → כי       [Cyrillic ка]        вדרך → בדרך   [Cyrillic ве]
האופנim → האופנים  [Cyrillic и + ем]  лбайт → לבית  [four Cyrillic letters]
```

`dev/scripts/surface_restore.py bg --apply` restored all **718 → 0** against the
floor. Nothing was laundered; the floor holds the true surface.

## What the press got wrong, and what was done

1. **A wrong number.** Num 26:22 glossed *seventy* as **и шейсет** — sixty.
   Convicted and refilled.
2. **Placeholders reached production, in two shapes.** 1 Kgs 18:19 carried
   **`<празен>`** — the Bulgarian word for *empty* — twice in one verse, where a
   number belongs. Exod 24:4 carried **`⟨какво?⟩`**, the Bulgarian for ***what?***,
   written into a gloss slot inside marker brackets; Ezra 8:31 carried **`⟨⟩`**,
   empty brackets. **A word-shaped or question-shaped placeholder passes every
   marker and parity check there is.** Filed fleet-wide as suspect 48.
3. **Number tokens received the NEXT word's gloss** — `twelve → камъка` (stones),
   `hundred → таланта` (talent), `fifty → годишни` (years-old), `seven → овни`
   (rams), `ten → завеси` (curtains). An off-by-one in alignment, invisible to the
   marker and parity auditors. Filed fleet-wide as suspect 49.
4. **Broken and colloquial numerals** — `шесет`, `найсет`, `стиотин`, `сти`.
   (Note `шейсет` and `четиресет` are *correct* colloquial Bulgarian and were the
   probe's gap, not the chair's fault; both are now in the numeral list.)
5. **Russian and Serbian bleed, 393 verses.** `И било` for `וַיְהִי` where
   Bulgarian says *И беше* / *И стана*; **`сыновете`**, a hybrid of Russian
   *сыновья* with the Bulgarian article (Bulgarian is *синовете*); `который`,
   `этози`; Russian-only `ы э ё` and the Serbian set. Convicted and refilled.
6. **The rails spoke once, and the gate's own word was wrong twice.** The convict
   list fires on the rails' technical vocabulary. **Two entries had to be removed
   because they are also Bible words in correct Bulgarian:**
   - **знак** — `אוֹת` is the bow in the cloud and the mark on Cain, and *знак* is
     its right rendering (Gen 9:13, Gen 4:15). It convicted three clean verses.
   - **седалка** — SoS 3:10 is Solomon's palanquin and `מֶרְכָּבוֹ` is legitimately
     *its seat*. It convicted one clean verse.

   **A rails-word that is also a Bible word is not a rails-word.** Twice on this
   chair.

## The rule that governed the whole close-out

**Read the class back before deleting anything.** It was not a precaution here;
it was the difference between a clean chair and a butchered one:

| probe | first fired | after the read-back | what it was |
|---|---|---|---|
| a Bulgarian rails-word scan | **307 files** | **0** | `начал` substring-matched `начало` and `началник`; **not one whole-word hit** |
| number | **1,355** | **31** | English *one* is an indefinite pronoun; *first* renders пръв; and **the Hebrew DUAL** — the floor glosses `הַקְּרָנַיִם` *the two horns* and Bulgarian, which has no dual, correctly says `роговете` |
| convict | 1 | 0 | `седалка` at SoS 3:10 |

**Over 1,500 clean Bulgarian verses were one unread list away from deletion.**

## The gates

| gate | at | the Name | erasure words | notes |
|---|---|---|---|---|
| 1 | first hour | 44 of 44 **Яхве** | none | caught `заченa`, Gen 4:17, Latin `a` |
| **final** | **23,212 of 23,213 — 2026-09-22 17:31 UTC** | **6,007 of 6,007 Яхве** | **none** | every `יהוה` seat in the Tanakh |

**The Name gate is clean at full count.** `יהוה` stands **6,007** times in the
letter stream, and **all 6,007 carry Яхве** — not one Господ, Бог, Йехова,
Ягве or Адонай on a Name seat.

### What remains, counted and not hidden

| class | files | what it is |
|---|---|---|
| bleed | 49 | Russian/Serbian forms — `И било`, `сыновете` |
| short | 42 | flow carries fewer `⟨את⟩` markers than the rows |
| homoglyph | 13 | Latin letters inside Cyrillic words |
| empty | 13 | a blank gloss where the floor has content |
| number | 2 | a number word with no Bulgarian numeral |
| fabricated · missing · bare · erasure · convict · flownumber | **0** | |

One verse is still unrendered (residue 1 from the 17:23 relay). These are the
**morning gleaning** under the altar-fire charter — the fire outranks the polish,
and residue is recorded rather than ground serially unattended.

## Still open at the last census

`short` 57 (flow carries fewer markers than the rows — `flow_parity.py` fixed 124
and could not fix these) · `gains` 110 (a marker in the flow that no row carries —
**the chair supplying its own** `⟨את⟩`, the documented row-fabrication fault).
Both were convicted and refilled in the 17:23 pass; what survived is in the
residue table above.
