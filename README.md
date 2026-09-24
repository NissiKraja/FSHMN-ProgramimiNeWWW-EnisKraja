# JavaI — Pasaporta digjitale dhe GitHub

## Çfarë realizova

- `index.html` — pasaporta digjitale e personazhit të sajuar **Zana**, me `lang="sq"`, `charset`, `viewport`, titull, `h1`, prezantim, listë me 3 aftësi dhe lidhje relative te `rreth.html`.
- `rreth.html` — histori e shkurtër e personazhit dhe lidhje kthimi te `index.html`.
- `kontakt.html` — sfida e transferimit: një faqe e tretë e lidhur nga të dyja faqet ekzistuese.
- `style.css` — stil i thjeshtë (ngjyra, header me vijë ndarëse, fokus i dukshëm për tastierë).

## Hapat e hapjes

1. Hap folderin `JavaI/` me një server lokal (p.sh. ekstensioni "Live Server" në VS Code, ose `npx serve`).
2. Hap `index.html` në shfletues përmes URL-së që jep serveri (jo me `file://`).
3. Nga `index.html` kliko te `Rreth Zanës` ose `Kontakt` për të lëvizur mes faqeve.

## Hyrje → rezultat i pritur → rezultat i marrë

| Rasti | Hyrja (veprimi) | Rezultati i pritur | Rezultati i marrë |
|---|---|---|---|
| Normal | Hapja e `index.html` përmes serverit lokal | Faqja shfaq h1, prezantimin dhe 3 aftësitë; lidhja te "Rreth Zanës" funksionon | ✅ Përputhet |
| Kufitar 1 | Klikimi i lidhjes "Kthehu te pasaporta" nga `rreth.html` | Kthim te `index.html` pa gabim 404 | ✅ Përputhet |
| Kufitar 2 | Hapja e `index.html` direkt me `file://` (pa server) | Faqja shfaqet, por DevTools → Network nuk regjistron kërkesë HTTP (skema `file:` nuk kalon nëpër server) | ✅ Vërehet mungesa e kërkesës HTTP, siç pritej |

## DevTools → Network

Kur `index.html` hapet përmes serverit lokal, kërkesa kryesore e dokumentit shfaqet me metodë `GET`, URL-në lokale të serverit (p.sh. `http://127.0.0.1:5500/JavaI/index.html`) dhe status `200`.

## Reflektim individual

Ndryshimi që ruhet lokalisht (në disk, si edhe pas `git add`/`git commit`) por nuk shihet ende në GitHub është ai që nuk është "push"-uar — commit-i ekziston vetëm në repository-n lokal derisa `git push` ta dërgojë te remote.

## Deklarimi i AI/burimeve

Struktura dhe përmbajtja e faqeve u përgatitën me ndihmën e një asistenti AI (Claude), bazuar në kërkesat e skedarit `README - kerkesat e detyres 1.md` dhe në stilin e zgjidhjes reference të dhënë. Të dhënat e personazhit janë krejtësisht të sajuara.
