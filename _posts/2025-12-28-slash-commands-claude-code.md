---
title: Komendy slash w Claude Code - kompletny przewodnik po skrótach i nowościach
date: 2025-12-28 14:30
categories: "[Tutorial]"
tags: "[Claude Code, AI, CLI, productivity]"
---

## 🚀 Intro

### Po co mi te komendy?

Pracując z Claude Code na co dzień, szybko zauważyłem, że wpisywanie pełnych poleceń za każdym razem jest po prostu męczące. Na szczęście twórcy Claude Code pomyśleli o nas, nerdach, i wprowadzili system komend slash - czyli skrótów zaczynających się od `/`, które znacząco przyspieszają pracę.

Wyobraź sobie, że zamiast pisać "sprawdź mój kod pod kątem bezpieczeństwa i jakości", wpisujesz po prostu `/review`. Albo zamiast ręcznie przeszukiwać dokumentację, używasz `/help`. Proste, prawda?

Co więcej, w ostatnich wersjach Claude Code pojawiły się naprawdę ciekawe nowości - **Skills** (umiejętności), **Sub-agents** (podagenci) oraz możliwość **delegowania zadań do chmury**. Te funkcje przenoszą interakcję z AI na zupełnie nowy poziom, ale o tym za chwilę.

## 📋 Wszystkie wbudowane komendy slash

Oto pełna lista komend, które masz dostępne od razu po uruchomieniu Claude Code:

### Zarządzanie sesją i kontekstem

| Komenda | Co robi |
|---------|---------|
| `/clear` | Czyści historię rozmowy - przydatne gdy chcesz zacząć od nowa |
| `/compact [instrukcje]` | Kompresuje rozmowę, opcjonalnie z instrukcjami na czym się skupić |
| `/context` | Pokazuje kolorową siatkę z aktualnym wykorzystaniem kontekstu |
| `/cost` | Wyświetla statystyki użycia tokenów |
| `/exit` | Wychodzi z REPL |
| `/resume [sesja]` | Wznawia rozmowę po ID lub nazwie sesji |
| `/rename <nazwa>` | Zmienia nazwę bieżącej sesji dla łatwiejszej identyfikacji |
| `/rewind` | Cofa rozmowę i/lub zmiany w kodzie |
| `/export [nazwa_pliku]` | Eksportuje rozmowę do pliku lub schowka |

### Konfiguracja i ustawienia

| Komenda | Co robi |
|---------|---------|
| `/config` | Otwiera interfejs ustawień |
| `/model` | Pozwala wybrać lub zmienić model AI |
| `/permissions` | Wyświetla lub aktualizuje uprawnienia |
| `/privacy-settings` | Ustawienia prywatności |
| `/output-style [styl]` | Ustawia styl wyjścia |
| `/statusline` | Konfiguruje linię statusu |
| `/vim` | Włącza tryb vim |

### Praca z kodem i repozytorium

| Komenda | Co robi |
|---------|---------|
| `/add-dir` | Dodaje dodatkowe katalogi robocze |
| `/init` | Inicjalizuje projekt z przewodnikiem `CLAUDE.md` |
| `/review` | Prosi o recenzję kodu |
| `/security-review` | Przeprowadza przegląd bezpieczeństwa zmian na bieżącej gałęzi |
| `/pr-comments` | Wyświetla komentarze z pull requestów |
| `/install-github-app` | Konfiguruje Claude GitHub Actions |

### Diagnostyka i pomoc

| Komenda | Co robi |
|---------|---------|
| `/help` | Wyświetla pomoc |
| `/doctor` | Sprawdza "zdrowie" instalacji Claude Code |
| `/bug` | Zgłasza błędy (wysyła rozmowę do Anthropic) |
| `/release-notes` | Pokazuje notki wydania |
| `/stats` | Wizualizuje dzienne użytkowanie, historię sesji i preferencje |
| `/usage` | Pokazuje limity planu i status rate limit |
| `/status` | Wyświetla wersję, model, konto i status połączenia |

### Zaawansowane funkcje

| Komenda | Co robi |
|---------|---------|
| `/agents` | Zarządza niestandardowymi podagentami AI |
| `/bashes` | Wyświetla i zarządza zadaniami w tle |
| `/hooks` | Zarządza konfiguracjami hooków dla zdarzeń |
| `/ide` | Zarządza integracjami IDE |
| `/mcp` | Zarządza połączeniami serwerów MCP i OAuth |
| `/memory` | Edytuje pliki pamięci `CLAUDE.md` |
| `/plugin` | Zarządza wtyczkami |
| `/todos` | Wyświetla bieżące elementy TODO |
| `/sandbox` | Włącza izolowane środowisko bash |
| `/terminal-setup` | Instaluje Shift+Enter dla nowych linii (iTerm2/VSCode) |
| `/login` / `/logout` | Logowanie/wylogowanie z konta Anthropic |

## ✨ Tworzenie własnych komend slash

To jest ta część, która naprawdę mnie kręci. Możesz tworzyć własne komendy jako pliki Markdown!

### Gdzie je umieścić?

- **Dla projektu:** `.claude/commands/`
- **Osobiste (wszystkie projekty):** `~/.claude/commands/`

### Przykład prostej komendy

Tworzysz plik `.claude/commands/optimize.md`:

```markdown
Przeanalizuj ten kod pod kątem wydajności i zasugeruj optymalizacje:
```

Teraz wystarczy wpisać `/optimize` i Claude zrobi resztę.

### Komendy z argumentami

Możesz też przekazywać argumenty:

```bash
> /fix-issue 123 high-priority
# $ARGUMENTS zawiera: "123 high-priority"
# $1 = "123", $2 = "high-priority"
```

### Zaawansowana konfiguracja z frontmatter

```markdown
---
allowed-tools: Bash(git add:*), Bash(git status:*)
argument-hint: [message]
description: Create a git commit
model: claude-3-5-haiku-20241022
---

Utwórz commit z wiadomością: $ARGUMENTS
```

## 🎯 Nowości: Skills - umiejętności Claude'a

Tutaj zaczyna się prawdziwa magia. **Skills** to pliki markdown, które uczą Claude'a wykonywać określone zadania. Najfajniejsze jest to, że aktywują się automatycznie, gdy Twoje zapytanie pasuje do ich opisu.

### Jak to działa?

1. **Discovery** - Claude ładuje tylko nazwę i opis Skill'a przy starcie
2. **Activation** - Gdy zapytanie pasuje, Claude prosi o potwierdzenie
3. **Execution** - Claude wykonuje instrukcje z pliku

### Tworzenie pierwszego Skill'a

Utwórz katalog i plik:

```bash
mkdir -p ~/.claude/skills/explaining-code
```

W pliku `~/.claude/skills/explaining-code/SKILL.md`:

```markdown
---
name: explaining-code
description: Wyjaśnia kod za pomocą diagramów i analogii. Użyj gdy pytam "jak to działa?"
---

# Explaining Code

Przy wyjaśnianiu kodu zawsze:

1. **Zacznij od analogii** - Porównaj kod do czegoś z codziennego życia
2. **Narysuj diagram** - Użyj ASCII art do pokazania przepływu
3. **Przejdź przez kod** - Wyjaśnij krok po kroku
4. **Wskaż pułapki** - Typowe błędy i nieporozumienia
```

### Lokalizacje Skills

| Typ | Ścieżka | Zakres |
|-----|---------|--------|
| Osobiste | `~/.claude/skills/` | Wszystkie projekty |
| Projektowe | `.claude/skills/` | Zespół w repo |
| Z pluginu | Wbudowane | Po instalacji |

### Skills vs inne opcje

| Opcja | Kiedy użyć | Aktywacja |
|-------|-----------|-----------|
| **Skills** | Specjalistyczna wiedza | Automatycznie |
| **Slash commands** | Reużywalne prompty | Wpisujesz `/command` |
| **CLAUDE.md** | Instrukcje projektu | Zawsze aktywne |

### 💎 Gotowe Skills do użycia

Nie musisz tworzyć wszystkich Skills od zera. Społeczność już przygotowała wiele gotowych rozwiązań. Polecam zajrzeć do repozytorium [Awesome Claude Skills](https://github.com/ComposioHQ/awesome-claude-skills) - znajdziesz tam kolekcję sprawdzonych Skills, które możesz od razu zainstalować i używać. Od generowania commitów, przez recenzje kodu, po integracje z różnymi serwisami.

A jeśli chcesz tworzyć własne Skills, ale nie masz ochoty ręcznie pisać plików YAML i Markdown? Jest na to rozwiązanie - **Skill Creator**. To skill, który... pomaga tworzyć inne skille. 🔄 Tak, wiem - brzmi jak inception, ale to naprawdę przydatne narzędzie. Zamiast samemu pamiętać o strukturze plików, wymaganych polach i najlepszych praktykach, po prostu opisujesz Claude'owi czego potrzebujesz, a Skill Creator przeprowadzi Cię przez cały proces i wygeneruje gotowy do użycia skill. Meta? Może. Użyteczne? Zdecydowanie.

## 🤖 Nowości: Sub-agents - podagenci

To kolejna funkcja, która zmienia sposób pracy z Claude Code. **Sub-agents** to wyspecjalizowani asystenci AI, którym główny agent może delegować zadania.

### Dlaczego to jest genialne?

- Każdy subagent ma **własny kontekst** - nie zaśmieca głównej rozmowy
- Ma **wyspecjalizowane instrukcje** dla konkretnej domeny
- Można go używać **w różnych projektach**
- Ma **elastyczne uprawnienia** - inny dostęp do narzędzi

### Wbudowani subagenci

Claude Code ma już kilku wbudowanych podagentów:

| Subagent | Model | Zastosowanie |
|----------|-------|--------------|
| **Explore** | Haiku (szybki) | Przeszukiwanie bazy kodu (tylko odczyt) |
| **Plan** | Sonnet | Planowanie przed wykonaniem |
| **General-purpose** | Sonnet | Złożone, wieloetapowe zadania |

### Tworzenie własnego subagenta

Utwórz plik `.claude/agents/code-reviewer.md`:

```markdown
---
name: code-reviewer
description: Ekspert do przeglądu kodu. Użyj proaktywnie po zmianach.
tools: Read, Grep, Glob, Bash
model: inherit
---

Jesteś starszym recenzentem kodu. Przy każdym przeglądzie:

1. Uruchom `git diff` aby zobaczyć zmiany
2. Sprawdź czytelność kodu
3. Szukaj problemów bezpieczeństwa
4. Sprawdź obsługę błędów

Grupuj feedback:
- Krytyczne (trzeba naprawić)
- Ostrzeżenia (powinno się naprawić)
- Sugestie (warto rozważyć)
```

### Zarządzanie subagentami

Najłatwiej przez komendę:

```bash
/agents
```

Otworzy menu do przeglądania, tworzenia i edycji subagentów.

### Używanie subagentów

Claude automatycznie deleguje zadania na podstawie opisu, ale możesz też wywołać jawnie:

```bash
> Użyj subagenta code-reviewer do sprawdzenia moich zmian
> Poproś debugger o zbadanie tego błędu
```

## 🆕 Co nowego w ostatnich wersjach?

Z changelogu Claude Code wybrałem najciekawsze nowości:

### Background Agents (v2.0.60)
Agenci mogą teraz działać **w tle** i wysyłać wiadomości do głównego agenta podczas gdy Ty pracujesz nad czymś innym. To prawdziwy game-changer dla złożonych zadań.

### Named Sessions (v2.0.64)
Możesz teraz nazywać sesje komendą `/rename` i wracać do nich przez `claude --resume <nazwa>`. Koniec z szukaniem sesji po ID.

### Skills Frontmatter (v2.0.43)
Subagenci mogą teraz automatycznie ładować Skills zdefiniowane w ich konfiguracji:

```yaml
---
name: code-reviewer
skills: pr-review, security-check
---
```

### LSP Tool (v2.0.74) 🔍

Nowe narzędzie **Language Server Protocol** to prawdziwy game-changer dla pracy z kodem. LSP to standard, który używają IDE takie jak VS Code do zapewnienia "inteligencji kodu". Teraz Claude Code ma do niego bezpośredni dostęp.

Co to oznacza w praktyce? Claude może teraz:

- **Go-to-definition** - skoczyć do definicji funkcji, klasy czy zmiennej
- **Find references** - znaleźć wszystkie miejsca, gdzie coś jest używane
- **Hover documentation** - wyświetlić dokumentację bez opuszczania terminala

Przykład użycia:
```bash
> Znajdź wszystkie miejsca gdzie używana jest funkcja processPayment
> Pokaż mi definicję klasy UserService
> Jakie metody ma interfejs PaymentGateway?
```

Claude używa LSP w tle, żeby dać Ci precyzyjne odpowiedzi zamiast zgadywać na podstawie tekstu. To jak mieć IDE experience, ale w terminalu.

### MCP Wildcards (v2.0.70) 🔐

**MCP (Model Context Protocol)** to otwarty standard integracji Claude'a z zewnętrznymi narzędziami i źródłami danych - bazami danych, API, serwisami jak GitHub, Sentry, Jira i wieloma innymi.

Nowość z wersji 2.0.70 to **wildcards w uprawnieniach**. Wcześniej trzeba było zatwierdzać każde narzędzie z serwera MCP osobno. Teraz możesz jednym ruchem zezwolić na wszystkie narzędzia z danego serwera:

```bash
# Zezwól na wszystkie narzędzia z serwera github
mcp__github__*

# Zablokuj wszystkie narzędzia z serwera
# (dodaj do deny rules w /permissions)
mcp__dangerous-server__*
```

To szczególnie przydatne, gdy ufasz danemu serwerowi i nie chcesz klikać "Allow" dla każdego narzędzia z osobna. Oszczędza czas i nerwy.

## ☁️ Claude Code on the Web - delegowanie do chmury

To jest funkcja, która naprawdę mnie zafascynowała. **Claude Code on the Web** pozwala uruchamiać zadania asynchronicznie na bezpiecznej infrastrukturze chmurowej Anthropic. Brzmi skomplikowanie? W praktyce jest genialnie proste.

### Jak to działa?

1. Wchodzisz na [claude.ai/code](https://claude.ai/code)
2. Łączysz swoje konto GitHub
3. Wybierasz repozytorium i opisujesz zadanie
4. Claude klonuje repo do bezpiecznej maszyny wirtualnej
5. Pracuje nad zadaniem (nawet gdy zamkniesz przeglądarkę!)
6. Dostajesz powiadomienie gdy skończy
7. Przeglądasz zmiany i tworzysz Pull Request

### Kiedy to jest przydatne?

- **Praca równoległa** - możesz zlecić naprawę kilku bugów jednocześnie
- **Repo nie na Twoim komputerze** - kod, którego nie masz sklonowanego lokalnie
- **Długie zadania** - nie musisz trzymać terminala otwartego
- **Zmiany backendowe** - Claude pisze testy, potem kod je spełniający

### Co jest w środowisku chmurowym?

Domyślny obraz zawiera praktycznie wszystko, czego potrzebujesz:

- **Języki**: Python, Node.js, Ruby, PHP, Java, Go, Rust, C++
- **Bazy danych**: PostgreSQL 16, Redis 7.0
- **Narzędzia**: popularne build tools, package managery, testing frameworks

### Przenoszenie między webem a terminalem

Fajne jest to, że możesz **przenieść sesję z chmury do lokalnego terminala**. Klikasz "Open in CLI", wklejasz komendę w terminalu i kontynuujesz pracę lokalnie z pełnym kontekstem tego, co Claude zrobił w chmurze.

> ⚠️ **Uwaga**: Funkcja jest obecnie w fazie badawczej i dostępna dla użytkowników Pro, Max, Team i Enterprise.

## 🔌 Komendy z pluginów i MCP

Warto też wiedzieć, że komendy mogą pochodzić z:

### Pluginy
```bash
/plugin-name:command-name
```

### Serwery MCP
```bash
/mcp__github__list_prs
/mcp__github__pr_review 456
```

## 🎬 Podsumowanie

Komendy slash w Claude Code to potężne narzędzie, które pozwala:

- ⚡ Przyspieszyć codzienną pracę prostymi skrótami
- 🛠️ Tworzyć własne komendy dopasowane do workflow
- 🎯 Używać Skills do automatycznej aktywacji specjalistycznej wiedzy
- 🤖 Delegować zadania do wyspecjalizowanych Sub-agents
- ☁️ Zlecać zadania do chmury i pracować równolegle

Polecam zacząć od eksploracji wbudowanych komend (`/help`), a potem stopniowo tworzyć własne. Możliwości są naprawdę imponujące - i co ważne, ciągle się rozwijają.

To wszystko!
Jak zawsze - enjoy it. 🚀
