# GitHub + Cloudflare — instrukcja dla telefonu

## Krok 1: GitHub

1. Zarejestruj / zaloguj się na https://github.com/ .
2. Wybierz `New repository` → nazwa `aeropogoda` → Private → `Create repository`.
3. Rozpakuj paczkę ZIP w aplikacji `Moje pliki` na Samsungu.
4. Wgraj do repozytorium pliki `wrangler.jsonc`, `package.json`, `.gitignore`, `README.md`, a plik `index.html` umieść **wewnątrz folderu `public`**. Najprościej wykonać pierwsze wysłanie na komputerze, bo przesyłanie folderów z mobilnej przeglądarki GitHub może być niewygodne.
5. Jeśli GitHub poprosi o Commit changes, zatwierdź z gałęzią `main`.

## Krok 2: Cloudflare

1. Otwórz dash.cloudflare.com → Workers & Pages.
2. Kliknij **istniejący** Worker `aeropogoda` (nie Create application).
3. Wybierz `Settings` → `Builds` (czasem `Build`).
4. Kliknij `Connect` przy Git Repository, wybierz GitHub i nadaj uprawnienia do repozytorium `aeropogoda`.
5. Root directory: `/`; Production branch: `main`; Build command: pozostaw puste; Deploy command: `npx wrangler deploy`.
6. Zapisz. Kolejny commit uruchomi nowy build/deploy. Sprawdź status `Success` i swoją istniejącą domenę `workers.dev`.

## Krok 3: następne aktualizacje

Wystarczy podmienić `public/index.html` w GitHubie i wykonać Commit na `main`. Cloudflare automatycznie aktualizuje ten sam Worker i ten sam adres.

## Uwaga

- Nie twórz nowego Cloudflare Pages, jeśli ważny jest identyczny adres `workers.dev`.
- Przed pierwszym deployem zanotuj dotychczasowy URL i identyfikator poprzedniej wersji w Cloudflare. Poprzednią wersję można przywrócić, jeśli wystąpi problem.
- `wrangler.jsonc` musi wskazywać dokładnie nazwę obecnego Workera (`aeropogoda`).
- Dotychczasowe ulubione przechowywane w localStorage pozostaną na tym samym adresie w tej samej przeglądarce. Nie wyczyść danych witryny.
