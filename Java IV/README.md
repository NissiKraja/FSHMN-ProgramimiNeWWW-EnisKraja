# Java IV — Festivali që përshtatet në çdo ekran

## Çfarë mëson

Flexbox, Grid, media queries dhe pamje responsive.

Referencë tematike: kap. 6–7 të librit.

## Skenari

Programi i një festivali shkencor duhet të lexohet si në telefon ashtu edhe në ekran të gjerë.

## Çfarë realizova

- Faqja kryesore `index.html` me menu fleksibile (Flexbox), gjashtë karta aktivitetesh (Grid) dhe seksionet Rreth festivalit, Vizita dhe Kontakti.
- Faqja `detaje.html` me përshkrimin e secilit aktivitet; lidhja "Shih detajet" e çdo karte çon te seksioni përkatës.
- Grid me `repeat(2, 1fr)` nga 600 px dhe `repeat(3, 1fr)` nga 900 px; nën 600 px ka një kolonë.
- Çdo kartë ka titull, kategori, orar, imazh dhe lidhje detajesh. Titujt përdorin `overflow-wrap: anywhere`, kartat kanë `min-width: 0` dhe asnjë tekst nuk ka lartësi fikse.
- Imazhet janë SVG lokale në `assets/` me `max-width: 100%` dhe `height: auto`.
- Menuja përdor lidhje të vërteta, ka stil `:focus-visible` dhe lidhjen "Kalo te përmbajtja" që shfaqet me tastierë.

## Struktura

```
JavaIV/
├── index.html
├── detaje.html
├── style.css
├── README.md
└── assets/
    └── aktiviteti-1.svg … aktiviteti-6.svg
```

## Hapat e hapjes

1. Klono repository-n dhe hyr në dosjen `JavaIV/`.
2. Hap `index.html` në shfletues (klik i dyfishtë ose `File → Open`). Nuk nevojitet server ose instalim.
3. Për testim, hap DevTools dhe përdor Responsive Design Mode me gjerësi 360, 768 dhe 1280 px.

## Testimi

Testet u kryen në Chromium (Playwright) me lartësi 740, 1024 dhe 800 px përkatësisht.

| Hyrje | Rezultat i pritur | Rezultat i marrë |
|---|---|---|
| Gjerësia 360 px | 1 kolonë | 1 kolonë |
| Gjerësia 768 px | 2 kolona | 2 kolona |
| Gjerësia 1280 px | 3 kolona | 3 kolona |
| `scrollWidth` kundrejt `clientWidth` në 360 px | Të barabarta (pa scroll horizontal) | 360 = 360 |
| `scrollWidth` kundrejt `clientWidth` në 768 px | Të barabarta | 768 = 768 |
| `scrollWidth` kundrejt `clientWidth` në 1280 px | Të barabarta | 1280 = 1280 |
| Karta me titull 100 karakteresh në 360 px | Titulli mbetet brenda kartës | Titulli brenda kartës, pa tejkalim |
| Tab nga fillimi i faqes | Fokusi kalon në "Kalo te përmbajtja", pastaj në çdo lidhje të menusë | Radha: Kalo te përmbajtja, Programi, Rreth festivalit, Vizita, Kontakti, lidhjet e kartave |
| Enter mbi "Kalo te përmbajtja" | Adresa merr `#main` | `#main` |

## Rastet e pranimit

- [x] Në 360/768/1280 px shfaqen përkatësisht 1/2/3 kolona.
- [x] Nuk ka scroll horizontal në faqen e plotë.
- [x] Menuja mbetet e përdorshme me tastierë.

## Sfida e transferimit

Karta e pestë ka titull me saktësisht 100 karaktere. Në 360 px, 768 px dhe 1280 px ai thyhet në disa rreshta brenda kartës, falë `overflow-wrap: anywhere` dhe `min-width: 0` te elementi i Grid-it, dhe nuk krijon scroll horizontal. Karta zgjatet në lartësi sepse asnjë tekst nuk ka lartësi fikse, kurse lidhja e detajeve mbetet në fund të kartës.

## Reflektim individual

Kur do të zgjidhje Flexbox dhe kur Grid?

Flexbox e përdor kur përmbajtja renditet në një drejtim të vetëm, me rresht ose me kolonë, dhe elementët duhet të ndajnë hapësirën sipas madhësisë së tyre. Në këtë ushtrim e përdora për menunë, ku lidhjet kalojnë në rresht të ri kur nuk ka vend, dhe brenda kartës për ta shtyrë lidhjen e detajeve në fund. Grid e përdor kur kam nevojë për rreshta dhe kolona njëkohësisht dhe kur struktura e faqes vendoset nga rrjeta, jo nga përmbajtja. Për kartat e programit e zgjodha Grid sepse numri i kolonave ndryshon me gjerësinë e ekranit (1, 2, 3) dhe të gjitha kartat duhet të kenë gjerësi të njëjtë.

## Deklarimi i AI dhe burimeve

- Struktura fillestare e ushtrimit (`index.html`, `style.css`, `README.md`) vjen nga fleta e dhënë nga lënda.
- Kodi HTML dhe CSS, imazhet SVG dhe teksti i këtij README u gjeneruan me ndihmën e Claude (Anthropic). Rezultatet e testeve u maten me një skript Playwright në Chromium të pa-ekranit.
- Burime teknike: dokumentacioni MDN për CSS Grid, Flexbox, `overflow-wrap` dhe `:focus-visible`, si dhe kapitujt 6–7 të librit të lëndës.
- Të dhënat e festivalit (aktivitetet, orari) janë të sajuara.
