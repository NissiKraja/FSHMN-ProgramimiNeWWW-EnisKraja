# Java III — Klinika e CSS: shpëto afishen

Afishja e klubit të debatit e kthyer në një ftesë të qartë, me CSS të jashtëm.

## Struktura

```
JavaIII/
├── index.html
├── style.css          # variabla, karta, etiketat, butoni, focus
├── Fillimi/
│   └── gabime.css     # rregullat e diagnostikuara dhe të riparuara
├── assets/
│   └── debat.svg      # asete lokale
└── README.md
```

## Si plotësohen kërkesat

1. **Afisha**: titull, datë (`<time>`), vend, përshkrim dhe lidhje (`Kërko informacion`).
2. **CSS i jashtëm**: `style.css` + `Fillimi/gabime.css`; klasa të ripërdorshme (`.card`, `.badge`, `.btn`) dhe variabla `--color-*`, `--space-*` në `:root`.
3. **Tri etiketa**: *Falas*, *Vende të kufizuara: 20*, *Edhe online*. Dallohen me tekst dhe stil kufiri (e dyta ka kufi të ndërprerë), jo vetëm me ngjyrë.
4. **Gabimet**: dy konflikte dhe overflow të diagnostikuara në `Fillimi/gabime.css`, riparuar pa `!important`.
5. **Focus**: `a:focus-visible` ka outline 3px portokalli me offset; `.skip` shfaqet kur merr fokus.

## Diagnoza e gabimeve

| Problemi | Shkaku | Riparimi |
|---|---|---|
| Teksti i bardhë mbi sfond të bardhë | `#poster` (1,0,0) mundi `.poster` (0,1,0) në `color` | U hoq `#poster`, mbeti vetëm `.poster` |
| Paneli del nga ekrani 360 px | `width: 700px` fiks + `padding: 80px` | `width: 100%`, `max-width: 700px`, `padding: clamp(...)` |

## box-sizing: width, padding dhe border

Me `content-box` (parazgjedhja), `width` vlen vetëm për përmbajtjen, ndaj gjerësia e vërtetë është
`width + padding + border`. Një kuti me `width: 100%` dhe `padding: 2rem` do të tejkalonte prindin.
Me `* { box-sizing: border-box; }` `width` përfshin padding dhe border, kështu
`width: 100%` mbetet 100% dhe paneli nuk del jashtë.

## Reflektim individual

**Cili rregull fitoi në kaskadë dhe pse?**
Fitoi `#poster { color: white; }`. Kaskada e zgjidh konfliktin sipas specifikës para renditjes:
selektori me ID (1,0,0) është më specifik se ai me klasë (0,1,0), ndaj ngjyra e bardhë mbivendosi
`#17263c` edhe pse `.poster` shkruhej më poshtë. Rregulli i riparuar nuk përdor `!important`, por
heq burimin e dyfishtë: një selektor i vetëm me specifikë të ulët.
