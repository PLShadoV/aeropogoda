# AeroPogoda 9.1 — GitHub + Cloudflare Workers

Repozytorium jest gotowe do podłączenia **do istniejącego Workera** `aeropogoda` w Cloudflare.
Nie twórz nowego Workera ani nowego projektu Pages, jeśli chcesz zachować adres `*.workers.dev` obecnej aplikacji.

## Pliki

- `public/index.html` — kompletna aplikacja AeroPogoda 9.1
- `wrangler.jsonc` — konfiguracja statycznych plików w **istniejącym** Workerze `aeropogoda`
- `package.json` — narzędzie do wdrożeń Wrangler

## Pierwsze podłączenie

1. Rozpakuj ZIP i utwórz prywatne repozytorium `aeropogoda` na GitHubie. Wyślij **zawartość folderu**, aby `wrangler.jsonc` był w katalogu głównym, a strona pod `public/index.html`.
2. W Cloudflare wejdź w **Workers & Pages → aeropogoda → Settings → Builds → Connect**.
3. Autoryzuj GitHub, wskaż to repozytorium i gałąź `main`.
4. Ustaw katalog główny projektu `/` (repo root), **Build command** zostaw puste, **Deploy command**: `npx wrangler deploy`.
5. Zatwierdź połączenie. Jeśli nic się nie wdroży, wykonaj kolejny commit w GitHubie (np. drobną zmianę w README) — nowy commit wyzwoli automatyczny deploy.
6. Sprawdź status wdrożenia i ten sam adres Workera.

**Uwaga:** wartość `name` w pliku `wrangler.jsonc` musi być identyczna z nazwą Workera w Cloudflare. W paczce jest `aeropogoda`, zgodnie z widokiem panelu użytkownika. Nie zmieniaj jej bez potrzeby.

## Aktualizacje

Zmieniasz wyłącznie `public/index.html`, commitujesz do `main` i Cloudflare automatycznie publikuje aktualizację **tego samego** Workera. Nie ma potrzeby wgrywania nowego ZIP do Cloudflare.

## Test lokalny

Na komputerze z Node.js: `npm install`, następnie `npx wrangler dev`. Do ręcznego wdrożenia: `npm run deploy` (po zalogowaniu do Cloudflare).

## Dane

Aplikacja korzysta z Open-Meteo. Sekcja alergii 9.1 pokazuje orientacyjny kalendarz sezonowości, **nie** realne stężenia pyłków. Przed wykorzystaniem komercyjnym zweryfikuj licencję API.
