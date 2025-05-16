# Project Onboarding: Excalidraw

## Welcome

Welcome to the Excalidraw project! Excalidraw is an open source virtual hand-drawn style whiteboard. Collaborative and end-to-end encrypted.

## Project Overview & Structure

The core functionality revolves around providing a virtual whiteboard for creating hand-drawn like diagrams and wireframes. The project is organized as a monorepo, with the following key components/modules:

## Core Modules

### `packages/excalidraw/components`

- **Role:** Zawiera kluczowe komponenty interfejsu użytkownika (UI) edytora Excalidraw, z `App.tsx` jako centralnym punktem. Odpowiada za renderowanie UI, obsługę zdarzeń użytkownika i ogólną koordynację interfejsu.
- **Key Files/Areas:**
  - UI Elements: `packages/excalidraw/components/App.tsx` (główny komponent aplikacji, zarządzający stanem i interakcjami)
  - Statistics: `packages/excalidraw/components/Stats` (komponent do wyświetlania statystyk)
- **Top Contributed Files:** `packages/excalidraw/components/App.tsx`
- **Recent Focus:** Ciągłe doskonalenie UI/UX, w tym poprawki błędów (np. związane z narzędziem lasso), refaktoryzacje (np. logika przycisków radiowych) i dodawanie nowych funkcji (np. wyszukiwanie z uwzględnieniem nazw ramek, API `onIncrement`). Wysoka częstotliwość zmian w `App.tsx` potwierdza jego centralną rolę.
- **Relationships:** Ściśle współpracuje z `packages/excalidraw/actions` (obsługa akcji), `packages/excalidraw/element` (manipulacja elementami) i `packages/excalidraw/types` (definicje stanu i właściwości).

### `packages/excalidraw/element` (Legacy/Refactored)

- **Role:** Tradycyjnie zarządzał elementami (kształtami, tekstem, liniami itp.) na płótnie, ich właściwościami i interakcjami. Analiza historii Git i struktury plików wskazuje, że ten moduł przeszedł znaczącą refaktoryzację, a jego podstawowa logika mogła zostać przeniesiona do `packages/element/src`.
- **Key Files/Areas (Historyczne):**
  - Element Logic: `packages/excalidraw/element/binding.ts`, `packages/excalidraw/element/linearElementEditor.ts` (te pliki mogą już nie istnieć w tej lokalizacji lub ich rola jest ograniczona).
- **Top Contributed Files (Historyczne):** `packages/excalidraw/element/binding.ts`, `packages/excalidraw/element/linearElementEditor.ts`
- **Recent Focus:** Historia commitów wskazuje na intensywne prace nad refaktoryzacją (wydzielenie logiki do osobnego pakietu), poprawkami błędów w bindowaniu, konwersji strzałek i edycji elementów liniowych.
- **Relationships:** Współpracował z `packages/excalidraw/components` (renderowanie elementów) i `packages/excalidraw/actions` (tworzenie/modyfikacja elementów). Jego obecna relacja z `packages/element/src` wymaga wyjaśnienia.

### `packages/excalidraw/actions`

- **Role:** Obsługuje akcje i polecenia użytkownika w edytorze (np. tworzenie kształtów, cofanie/ponawianie, eksportowanie, zmiana właściwości narzędzi).
- **Key Files/Areas:**
  - Action Definitions: `packages/excalidraw/actions/actionProperties.tsx` (definiuje UI i logikę dla właściwości akcji/narzędzi).
- **Top Contributed Files:** `packages/excalidraw/actions/actionProperties.tsx`
- **Recent Focus:** Ciągłe udoskonalanie i dodawanie nowych akcji oraz właściwości narzędzi. Commity wskazują na refaktoryzacje (np. konwersja typów elementów, oddzielenie logiki przycisków radiowych), nowe funkcje (np. pokazywanie pustego aktywnego koloru) i poprawki.
- **Relationships:** Ściśle powiązany z `packages/excalidraw/components/App.tsx` (wywoływanie akcji i aktualizacja UI) oraz `packages/excalidraw/element` (modyfikacja elementów).

### `packages/excalidraw`

- **Role:** Główny pakiet biblioteki Excalidraw, pełniący rolę centrum logiki aplikacji i punktu agregacji dla innych modułów. Odpowiada za koordynację różnych części systemu oraz definiuje kluczowe typy.
- **Key Files/Areas:**
  - Core Types: `packages/excalidraw/types.ts` (centralne definicje typów TypeScript dla całej aplikacji).
- **Top Contributed Files:** `packages/excalidraw/types.ts`, `packages/excalidraw/components/App.tsx` (plik `App.tsx` jest częścią `components`, ale jego znaczenie dla całego pakietu `excalidraw` jest ogromne).
- **Recent Focus:** Szeroko zakrojone zmiany wpływające na wiele części aplikacji. `types.ts` jest często modyfikowany w odpowiedzi na nowe funkcje i refaktoryzacje w innych modułach, co wskazuje na ewolucję struktur danych. Ogólna aktywność w pakiecie obejmuje refaktoryzacje, poprawki błędów i nowe funkcje.
- **Relationships:** Integruje i jest wykorzystywany przez większość pozostałych modułów. `types.ts` jest fundamentalny dla całego ekosystemu Excalidraw.

### `packages/excalidraw/tests`

- **Role:** Zawiera zautomatyzowane testy (jednostkowe, integracyjne, migawkowe) dla aplikacji i biblioteki Excalidraw.
- **Key Files/Areas:**
  - Snapshots: `packages/excalidraw/tests/__snapshots__/history.test.tsx.snap`, `packages/excalidraw/tests/__snapshots__/regressionTests.test.tsx.snap`, `packages/excalidraw/tests/__snapshots__/contextmenu.test.tsx.snap`. Te pliki przechowują oczekiwane stany UI lub danych dla różnych scenariuszy testowych.
- **Top Contributed Files:** Pliki snapshot są bardzo często aktualizowane, co odzwierciedla ciągły rozwój i zmiany w UI/funkcjonalności.
- **Recent Focus:** Wysoka częstotliwość zmian w plikach snapshot wskazuje na aktywne prace rozwojowe i dbałość o pokrycie testami nowych funkcji oraz regresji. Testy są dostosowywane do refaktoryzacji i zmian w logice aplikacji.
- **Relationships:** Testuje funkcjonalność zaimplementowaną w innych modułach, głównie `packages/excalidraw/components`, `packages/excalidraw/actions` i `packages/excalidraw/element` (oraz jego nowszym odpowiedniku).

### `packages/excalidraw/fonts`

- **Role:** Zarządza zasobami czcionek używanymi w Excalidraw, szczególnie dla elementów tekstowych. Odpowiada za dostarczanie i konfigurację czcionek.
- **Key Files/Areas:**
  - Specific Fonts: `packages/excalidraw/fonts/Xiaolai`, `packages/excalidraw/fonts/woff2/Xiaolai`.
- **Top Contributed Files:** Pliki w katalogach czcionek.
- **Recent Focus:** Zmiany są mniej częste, ale dotyczą kluczowych aspektów, takich jak dodawanie nowych czcionek, aktualizacje istniejących oraz poprawki związane z ładowaniem czcionek i ich metrykami, zwłaszcza w kontekście eksportu i renderowania tekstu. Wiele zmian w tym module jest również powiązanych z szerszymi refaktoryzacjami w projekcie.
- **Relationships:** Wykorzystywany przez logikę renderowania tekstu, prawdopodobnie w `packages/excalidraw/element` i `packages/excalidraw/components`.

### `packages/element/src` (Potencjalnie Nowy Główny Moduł Elementów)

- **Role:** Wydaje się być nowszym, bardziej modularnym podejściem do zarządzania logiką elementów, potencjalnie jako biblioteka niższego poziomu lub refaktoryzowany komponent zastępujący lub uzupełniający `packages/excalidraw/element`.
- **Key Files/Areas:** Zawiera kod źródłowy do manipulacji elementami, z naciskiem na czystszą separację odpowiedzialności.
- **Top Contributed Files:** (Wymagałoby to bardziej szczegółowej analizy commitów specyficznie dla tego katalogu, ale zmiany w nim są częste i znaczące).
- **Recent Focus:** Intensywny rozwój fundamentalnej logiki elementów. Commity (obserwowane ogólnie dla ścieżek zawierających `element/src`) wskazują na refaktoryzacje, nowe funkcje (np. obsługa nowych typów osadzonych treści, punkty przyciągania) i poprawki błędów.
- **Relationships:** Ściśle współpracuje z `@excalidraw/common` (typy, narzędzia) i jest intensywnie wykorzystywany przez `packages/excalidraw/components/App.tsx` do operacji na elementach. Jego dokładna relacja z `packages/excalidraw/element` powinna zostać wyjaśniona przez zespół.

### `packages/excalidraw/data`

- **Role:** Odpowiada za trwałość danych, import i eksport scen oraz ich przywracanie. Zarządza serializacją i deserializacją stanu aplikacji.
- **Key Files/Areas:**
  - Data Restoration: `packages/excalidraw/data/restore.ts` (kluczowy plik dla logiki przywracania danych, normalizacji i obsługi kompatybilności wstecznej).
- **Top Contributed Files:** `packages/excalidraw/data/restore.ts`
- **Recent Focus:** Aktywny rozwój w zakresie ładowania, zapisywania i przywracania danych rysunków. Commity wskazują na poprawki związane z eksportem (np. format SVG), przywracaniem starszych wersji danych oraz integracją z nowymi funkcjami i refaktoryzacjami w innych częściach systemu (np. dostosowanie do zmian w `packages/element/src`).
- **Relationships:** Współpracuje z `packages/excalidraw/types` (definicje struktur danych) i `packages/excalidraw/components/App.tsx` (inicjalizacja sceny na podstawie przywróconych danych).

### `packages/excalidraw/locales` (Nowo dodany na podstawie analizy)
- **Role:** Zarządza plikami lokalizacyjnymi dla internacjonalizacji (i18n) aplikacji Excalidraw.
- **Key Files/Areas:** `packages/excalidraw/locales/en.json` (plik z angielskimi tłumaczeniami, często modyfikowany).
- **Top Contributed Files:** `en.json` i prawdopodobnie inne pliki językowe.
- **Recent Focus:** Regularne dodawanie nowych kluczy tłumaczeń i modyfikacja istniejących w miarę rozwoju interfejsu użytkownika i dodawania nowych funkcji.
- **Relationships:** Wykorzystywany przez system i18n (prawdopodobnie w `packages/excalidraw/i18n`) do dynamicznego ładowania tekstów w `App.tsx` i innych komponentach UI.

## Key Contributors

*(Ta sekcja została zaktualizowana na podstawie analizy commitów w kluczowych plikach i modułach. Oryginalne informacje zostały zachowane jako punkt wyjścia).*

- **David Luzar (dwelle):** Pozostaje kluczowym i bardzo aktywnym kontrybutorem. Jego commity pojawiają się w wielu obszarach, w tym w `App.tsx`, `actionProperties.tsx`, `restore.ts` oraz w logice elementów. Wydaje się być zaangażowany zarówno w rozwój nowych funkcji, refaktoryzacje, jak i poprawki błędów w całym systemie. Szczególnie widoczny w pracach nad UI, zarządzaniem stanem i logiką narzędzi.
- **Márk Tolmács:** Aktywny kontrybutor, często pojawiający się w commitach dotyczących logiki elementów (`binding.ts`, `linearElementEditor.ts` - historycznie, oraz prawdopodobnie w nowym `packages/element/src`), refaktoryzacji i poprawek błędów, zwłaszcza tych bardziej złożonych (np. bindowanie, konwersje, obsługa dużych scen).
- **Marcel Mraz:** Bardzo aktywny deweloper, którego commity są widoczne w `App.tsx`, `actionProperties.tsx`, `types.ts`, a także w logice elementów i danych. Często zajmuje się refaktoryzacjami, nowymi API (np. `onIncrement`) oraz ogólną architekturą i spójnością kodu.
- **Ryan Di:** Regularny i znaczący kontrybutor. Jego commity często dotyczą implementacji nowych funkcji (np. wyszukiwanie z uwzględnieniem ramek, przełączanie kształtów, zaznaczanie lasso) oraz poprawek błędów w `App.tsx` i powiązanych plikach (np. `locales/en.json` w związku z nowymi tekstami UI).
- **zsviczian:** Kontrybutor, którego commity pojawiają się w kontekście specyficznych funkcji (np. przezroczyste tło linków, obsługa domen dla osadzonych treści). Może koncentrować się na konkretnych ulepszeniach lub integracjach.
- **Inni aktywni kontrybutorzy (na podstawie najnowszej analizy):** Warto zauważyć także wkład innych deweloperów, takich jak **Narek Malkhasyan**, **Rubén Norte**, **Gowtham Selvaraj**, **KODIFY**, **Mursaleen Nisar**, **Ritobroto Kalita**, którzy również wnoszą zmiany w różnych częściach projektu.

## Overall Takeaways & Recent Focus

*(Ta sekcja syntetyzuje nowe wnioski z poprzednimi).*

1.  **UI and Core Component Evolution (Nadal aktualne, rozszerzone):** `packages/excalidraw/components/App.tsx` pozostaje epicentrum rozwoju UI, z ciągłymi pracami nad narzędziem lasso, obsługą ramek, nowymi API i ogólnymi usprawnieniami interakcji. `packages/excalidraw/actions/actionProperties.tsx` również dynamicznie się rozwija, odzwierciedlając zmiany w dostępnych narzędziach i ich właściwościach.
2.  **Major Refactoring of Element Logic (Nowy wniosek/Modyfikacja):** Obserwujemy znaczącą refaktoryzację logiki obsługi elementów. Historyczne pliki `packages/excalidraw/element/binding.ts` i `packages/excalidraw/element/linearElementEditor.ts` były intensywnie modyfikowane, a commity wskazują na wydzielenie tej logiki do osobnego pakietu, którym prawdopodobnie jest `packages/element/src`. Ten nowy moduł wykazuje dużą aktywność i wydaje się przejmować odpowiedzialność za fundamentalną logikę elementów.
3.  **Data Handling and State Management (Nadal aktualne):** Zmiany w `packages/excalidraw/data/restore.ts` (obsługa przywracania danych, kompatybilność) i `packages/excalidraw/types.ts` (ewolucja struktur danych) są nadal częste i wskazują na ciągłe prace nad zarządzaniem danymi i stanem aplikacji.
4.  **Testing and Stability (Nadal aktualne):** Wysoka częstotliwość zmian w plikach snapshot (`packages/excalidraw/tests/__snapshots__`) potwierdza zaangażowanie w testowanie. Testy są regularnie aktualizowane, aby odzwierciedlać nowe funkcje, refaktoryzacje i poprawki, co jest kluczowe dla utrzymania stabilności tak dynamicznie rozwijanego projektu.
5.  **Localization and Assets (Nadal aktualne):** Aktywność w `packages/excalidraw/locales/en.json` (dodawanie nowych tekstów UI) i `packages/excalidraw/fonts` (choć rzadsza, to istotna) wskazuje na ciągłe prace nad wsparciem dla wielu języków i zarządzaniem zasobami.
6.  **Current Development Priorities (Nowy wniosek):** Na podstawie ostatnich commitów, priorytety zdają się obejmować:
    *   Usprawnienia narzędzia lasso i ogólnych interakcji zaznaczania.
    *   Rozwój funkcjonalności związanych z ramkami (frames).
    *   Rozszerzanie API aplikacji (np. `onIncrement`).
    *   Kontynuacja refaktoryzacji logiki elementów.
    *   Poprawki błędów i ogólne doskonalenie stabilności.

## Potential Complexity/Areas to Note

*(Ta sekcja została zaktualizowana o konkretne obserwacje z analizy plików).*

- **State Management in `App.tsx` (Potwierdzone, z dodatkowym kontekstem):** Plik `App.tsx` jest bardzo duży (ponad 11000 linii kodu) i ma najwyższą częstotliwość zmian. Zarządza ogromną ilością stanu i logiki interakcji, co czyni go naturalnie złożonym. Zrozumienie przepływu stanu i zależności w tym pliku jest kluczowe, ale może być wyzwaniem.
- **Refactored Element Logic (Nowy obszar złożoności):** Trwająca lub niedawno zakończona refaktoryzacja logiki elementów (przeniesienie z `packages/excalidraw/element` do `packages/element/src`) może wprowadzać tymczasową złożoność lub wymagać od deweloperów zrozumienia zarówno "starego", jak i "nowego" podejścia, dopóki dokumentacja nie zostanie w pełni zaktualizowana. Pliki `binding.ts` i `linearElementEditor.ts` były historycznie często zmieniane i mogły być źródłem błędów.
- **Canvas Rendering & Interaction (Potwierdzone):** Pozostaje obszarem o wysokiej złożoności, co widać w licznych metodach obsługi zdarzeń i aktualizacji stanu w `App.tsx`.
- **Collaboration and Encryption (Potwierdzone):** Te funkcje z natury wprowadzają znaczną złożoność.
- **Modularity and Packages (Potwierdzone, z uwypukleniem zmian):** Struktura monorepo z wieloma pakietami nadal wymaga zrozumienia interakcji. Szczególną uwagę należy zwrócić na relację i ewentualne pokrywanie się odpowiedzialności między `packages/excalidraw/element` a `packages/element/src`.
- **High Churn Files Requiring Attention (Nowy wniosek):**
    - `App.tsx`: Ze względu na rozmiar, centralną rolę i częstotliwość zmian.
    - `types.ts`: Zmiany tutaj mają szeroki wpływ; zrozumienie aktualnych typów jest kluczowe.
    - `actionProperties.tsx`: Częste zmiany wskazują na dynamiczny rozwój interfejsu właściwości.
    - `restore.ts`: Kluczowy dla obsługi danych, częste zmiany mogą wpływać na import/eksport.
    - Pliki snapshot testów: Wysoka częstotliwość zmian, choć oczekiwana, wymaga uwagi przy aktualizacji i interpretacji błędów testów.
- **Areas of Frequent Multi-Contributor Activity (Nowy wniosek):** `App.tsx`, `types.ts`, `actionProperties.tsx` oraz logika elementów (historycznie i prawdopodobnie w `packages/element/src`) są obszarami, gdzie wielu głównych kontrybutorów aktywnie wprowadza zmiany. Może to wskazywać na potrzebę dobrej koordynacji i dzielenia się wiedzą.
- **Discrepancies (Nowy wniosek):** Największą rozbieżnością między pierwotną dokumentacją a obserwacjami jest stan modułu `packages/excalidraw/element` i jego relacja z nowym, bardziej aktywnym `packages/element/src`.

## Questions for the Team

*(Pytania zostały zaktualizowane i sformułowane na podstawie przeprowadzonej analizy).*

1.  Jaka jest obecna i przyszła rola modułu `packages/excalidraw/element` w kontekście istnienia i aktywnego rozwoju `packages/element/src`? Czy `packages/element/src` całkowicie zastępuje logikę z `packages/excalidraw/element`, a jeśli tak, jakie są plany dotyczące usunięcia lub archiwizacji starszego modułu?
2.  Biorąc pod uwagę rozmiar i złożoność `App.tsx`, jakie są kluczowe strategie lub wzorce stosowane do zarządzania jego stanem (poza ogólnym użyciem React Context)? Czy istnieją plany dalszej modularyzacji tego komponentu?
3.  Jakie są najlepsze praktyki i zalecany przepływ pracy przy aktualizowaniu licznych plików snapshot (`.snap`) po wprowadzeniu zmian, które mają szeroki wpływ na UI lub stan aplikacji? Czy istnieją narzędzia lub skrypty wspomagające ten proces?
4.  W kontekście refaktoryzacji logiki elementów, jakie są główne wyzwania i korzyści płynące z wydzielenia jej do `packages/element/src`? Jakie to ma implikacje dla deweloperów pracujących nad nowymi typami elementów lub modyfikujących istniejące?
5.  Jakie są kluczowe mechanizmy synchronizacji stanu i rozwiązywania konfliktów w trybie współpracy (multiplayer), zwłaszcza w odniesieniu do zmian w `appState` i operacji na elementach?

## Next Steps

*(Rekomendacje zostały zaktualizowane i uszczegółowione).*

1.  **Set up the development environment:** (Zachowane z oryginału) Use the instructions from the `README.md` and `package.json` to install dependencies (`yarn install`) and run the application (`yarn start`).
2.  **Deep Dive into Core UI and State:**
    *   **Explore `packages/excalidraw/components/App.tsx`:** Mimo jego rozmiaru, jest to kluczowy plik do zrozumienia głównego przepływu aplikacji, obsługi zdarzeń i zarządzania stanem. Skup się na metodach cyklu życia, głównych handlerach zdarzeń i sposobie interakcji z innymi serwisami/modułami.
    *   **Review `packages/excalidraw/types.ts`:** Zrozumienie kluczowych struktur danych, zwłaszcza `AppState` i typów elementów, jest fundamentalne.
3.  **Understand Element Logic:**
    *   **Prioritize `packages/element/src`:** Biorąc pod uwagę aktywność i commity wskazujące na refaktoryzację, ten moduł jest prawdopodobnie obecnym i przyszłym miejscem dla logiki elementów. Zbadaj jego strukturę i sposób, w jaki definiuje i zarządza elementami.
    *   **Review `packages/excalidraw/data/restore.ts`:** Aby zrozumieć, jak dane są ładowane, normalizowane i przywracane, co da wgląd w strukturę i ewolucję elementów.
4.  **Analyze Action Handling:**
    *   **Examine `packages/excalidraw/actions/actionProperties.tsx`:** Aby zobaczyć, jak definiowane są właściwości narzędzi i jak UI panelu właściwości oddziałuje na stan aplikacji i elementy.
5.  **Run the project's test suite:** (Zachowane z oryginału) Execute `yarn test` (or `yarn test:app`) to familiarize yourself with the testing setup and see tests in action. Zwróć uwagę na to, jak zmiany w kodzie wpływają na pliki snapshot.
6.  **Trace a core user action:** (Zachowane z oryginału, z sugestią aktualizacji ścieżek) For example, trace the "create rectangle" action from the UI (`App.tsx`), through `packages/excalidraw/actions`, to its effect on element creation (likely via `packages/element/src`) and canvas rendering.
7.  **Review recent Pull Requests:** (Zachowane z oryginału) Look at merged PRs related to `packages/element/src`, `packages/excalidraw/components/App.tsx` or `packages/excalidraw/actions` on the project's GitHub repository to understand recent changes and coding patterns.
8.  **Documentation Improvement Recommendations:**
    *   **Clarify Element Logic Architecture:** Dokumentacja powinna jasno opisać obecną architekturę obsługi elementów, w tym rolę `packages/element/src` i jego relację do (potencjalnie przestarzałego) `packages/excalidraw/element`.
    *   **High-Level Overview of `App.tsx`:** Stworzenie uproszczonego diagramu przepływu danych lub opisu kluczowych sekcji w `App.tsx` mogłoby znacznie ułatwić nowym deweloperom zrozumienie tego pliku.
    *   **State Management Details:** Rozszerzenie sekcji o zarządzaniu stanem o bardziej szczegółowe informacje dotyczące wzorców używanych w `App.tsx`.
    *   **Snapshot Test Workflow:** Dodanie krótkiego przewodnika lub najlepszych praktyk dotyczących pracy z testami migawkowymi.

## Development Environment Setup

1. **Prerequisites:** Node.js version 18.0.0 - 22.x.x (from `package.json`)
2. **Dependency Installation:** `yarn install` (inferred from `packageManager: yarn` and common practice, though `clean-install` script uses `yarn install` explicitly)
3. **Building the Project (if applicable):** `yarn build` (which runs `yarn --cwd ./excalidraw-app build`)
4. **Running the Application/Service:** `yarn start` (which runs `yarn --cwd ./excalidraw-app start`)
5. **Running Tests:** `yarn test` (which runs `yarn test:app`, an alias for `vitest`)
6. **Common Issues:** Common issues section not found in checked files. Refer to project documentation or community channels if setup problems arise.

## Helpful Resources

- **Documentation:** [https://docs.excalidraw.com](https://docs.excalidraw.com) (from `README.md`)
- **Issue Tracker:** [https://github.com/excalidraw/excalidraw/issues](https://github.com/excalidraw/excalidraw/issues) (from `README.md`)
- **Contribution Guide:** [https://docs.excalidraw.com/docs/introduction/contributing](https://docs.excalidraw.com/docs/introduction/contributing) (from `README.md`)
- **Communication Channels:** Discord: [https://discord.gg/UexuTaE](https://discord.gg/UexuTaE) (from `README.md`)
- **Learning Resources:** Specific learning resources section not found in `README.md`. The main documentation is the best starting point. 