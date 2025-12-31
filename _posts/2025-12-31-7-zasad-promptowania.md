---
title: 7 Złotych Zasad Promptowania Claude'a - oficjalny przewodnik od Anthropic
date: 2025-12-31 10:00
categories: "[Tutorial]"
tags: "[Prompting, Claude, AI, Anthropic]"
---

## 🚀 Intro

### Po co mi te zasady?

Pracując z Claude'em na co dzień, szybko zauważyłem jedną rzecz: jakość moich promptów bezpośrednio przekłada się na jakość odpowiedzi. Brzmi banalnie? Może. Ale większość ludzi uczy się promptowania z przypadkowych porad w internecie, a potem dziwi się, że AI generuje im "AI slop" - generyczne, bezpłciowe treści.

Tymczasem Anthropic - firma, która stworzyła Claude'a - opublikowała oficjalny przewodnik. Nie są to przypadkowe tipy z Twittera, tylko **wytyczne prosto od twórców modelu**. I uwierz mi, robią różnicę.

Wyobraź sobie, że prosisz AI o stworzenie dashboardu. Bez konkretnych wytycznych dostaniesz:
- Fioletowe gradienty
- Zaokrąglone rogi
- Standardowy, "bezpieczny" design

Dlaczego? Bo model ma naturalną "grawitację" ciągnącą go w stronę najczęstszych wzorców z danych treningowych. Te siedem zasad pomoże ci wyrwać się z tej grawitacji.

### 🎬 Materiał źródłowy

Ten wpis powstał na podstawie [tego wideo na YouTube](https://www.youtube.com/watch?v=GKTkPnqhnf0), które z kolei bazuje na [oficjalnym przewodniku Anthropic po promptowaniu Claude'a](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices).

---

## ✨ Zasada 1: Bądź jasny i konkretny

### O co chodzi?

Współczesne modele AI są **świetne w wykonywaniu instrukcji**. Problem w tym, że gdy nie dajesz konkretnych wytycznych, model domyślnie wybiera "najbezpieczniejszą" opcję - czyli to, co najczęściej spotykał w danych treningowych. To właśnie ta "grawitacja" - ciągnie cię w stronę przeciętności.

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Stwórz dashboard analityczny. | Stwórz dashboard analityczny. Uwzględnij jak najwięcej istotnych funkcji i interakcji. Wyjdź poza podstawy i stwórz w pełni funkcjonalną implementację. |
| Stwórz prezentację. | Stwórz profesjonalną prezentację dotyczącą naszych wyników kwartalnych. Uwzględnij przemyślane elementy designu, hierarchię wizualną i angażujące animacje. |

**Kluczowa lekcja:** Specyficzność to twoja broń przeciwko przeciętności. Im dokładniej opiszesz, czego oczekujesz, tym lepsze wyniki.

---

## 🧠 Zasada 2: Wyjaśnij swoje "dlaczego"

### O co chodzi?

Claude potrafi **wnioskować na podstawie kontekstu**. Gdy wyjaśnisz intencję stojącą za prośbą, model może samodzielnie domyślić się wielu rzeczy, których explicite nie powiedziałeś.

To jak delegowanie zadań doświadczonemu pracownikowi - jeśli rozumie cel, może podejmować lepsze decyzje bez pytania o każdy szczegół.

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Napisz to w formalnym tonie. | Napisz to w formalnym tonie, ponieważ trafia do naszej rady dyrektorów i musimy wyglądać wiarygodnie i profesjonalnie. |
| Napisz krótko. | Napisz krótko, ponieważ wysyłam to przez SMS, a dłuższe wiadomości nie są czytane. |

**Kluczowa lekcja:** Jedno zdanie wyjaśniające "dlaczego" może diametralnie zmienić jakość odpowiedzi.

---

## 📝 Zasada 3: Dawaj dobre przykłady

### O co chodzi?

Współczesne modele **naśladują przykłady niemal dosłownie**. To potężne narzędzie, ale też pułapka. Jeśli twój przykład zawiera elementy, których nie chcesz - model je odtworzy.

### Meta-lekcja

Nie tylko jawne przykłady wpływają na odpowiedź - **sam styl twojego promptu** też jest wzorem. Jeśli piszesz:
- Swobodnie i zabawnie → odpowiedź będzie podobna
- Formalnie i ustrukturyzowanie → odpowiedź będzie podobna

**Kluczowa lekcja:** Traktuj swój prompt jak wzór do naśladowania. Pisz go w stylu, jakiego oczekujesz od odpowiedzi.

---

## ✅ Zasada 4: Mów co ma robić, nie czego unikać

### O co chodzi?

Wiele system promptów jest pełnych negacji: "nie rób tego", "unikaj tamtego", "nigdy nie używaj...". Problem w tym, że **pozytywne instrukcje są skuteczniejsze niż negatywne**.

Skoro modele świetnie wykonują polecenia, wystarczy powiedzieć im co mają robić - nie musisz wymieniać wszystkiego, czego robić nie powinny.

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Nie używaj markdown w odpowiedzi. | Twoja odpowiedź powinna składać się z płynnie napisanej prozy i akapitów. |
| Niech dobrze wygląda. | Użyj wyraźnych nagłówków. Pogrub kluczowe wnioski. Dodaj podsumowanie na górze. |

**Kluczowa lekcja:** Zamień "nie rób X" na "zrób Y". Proste.

---

## 🎬 Zasada 5: Bądź bezpośredni w działaniach

### O co chodzi?

Modele AI często domyślnie wybierają "bezpieczną" opcję - sugerowanie zamiast działania. Jeśli używasz ostrożnego języka ("może warto rozważyć...", "co myślisz o..."), model też będzie ostrożny i niczego nie zmieni.

Chcesz, żeby AI **wykonało akcję**? Powiedz to jasno.

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Możesz zasugerować zmiany? | Zmień tę funkcję, żeby poprawić jej wydajność. |
| Co sądzisz o tej propozycji? | Zedytuj tę propozycję - korzyści mają być jaśniejsze, dodaj wezwanie do działania na końcu. |

**Kluczowa lekcja:** Używaj czasowników akcji: "zmień", "napisz", "edytuj", "stwórz". Unikaj: "rozważ", "zasugeruj", "przemyśl".

---

## 🔍 Zasada 6: Wykorzystaj potencjał badawczy

### O co chodzi?

Claude jest **świetny w prowadzeniu researchu**. Ale żeby w pełni wykorzystać ten potencjał, musisz dać mu strukturę.

### Meta-prompt do badań

Anthropic udostępnił uniwersalny prompt do zadań badawczych:

> "Przeprowadź badanie w ustrukturyzowany sposób. W miarę zbierania danych, rozwijaj konkurujące hipotezy. Śledź swoje poziomy pewności i koryguj je w miarę poznawania nowych informacji. Regularnie poddawaj samokrytyce zarówno swoje poziomy pewności, jak i hipotezy. Rozbijaj złożone pytania na mniejsze, łatwiejsze do zarządzania pytania."

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Zbadaj moich konkurentów. | Zbadaj moich trzech głównych konkurentów w branży usług domowych. Dla każdego znajdź ich ceny, główne usługi i opinie klientów. Porównaj je z moją firmą i powiedz mi, gdzie mam przewagę. |

**Kluczowa lekcja:** Daj badaniu strukturę. Określ co, jak i po co.

---

## 📄 Zasada 7: Twórz profesjonalne dokumenty

### O co chodzi?

Claude wykorzystuje specjalne "umiejętności" (skills) do tworzenia dokumentów:
- Prezentacje z animacjami
- Landing pages
- Raporty w PDF
- Arkusze Excel

Wyniki są znacznie lepsze niż kiedyś - pod warunkiem, że dasz odpowiednie wytyczne.

### Jak to wygląda w praktyce?

| Słaby prompt | Mocny prompt |
|--------------|--------------|
| Zrób mi prezentację. | Stwórz profesjonalną prezentację na temat [TEMAT]. Uwzględnij przemyślane elementy designu, hierarchię wizualną i angażujące animacje. |
| Napisz mi raport. | Stwórz miesięczny raport dla zespołu. Podsumowanie na górze, sekcje dla każdego działu, wykresy postępów, zadania na przyszły miesiąc. Czyste formatowanie, łatwe do skanowania. |

**Kluczowa lekcja:** Określ konkretnie: strukturę, formatowanie, elementy wizualne.

---

## 🏁 Podsumowanie

Siedem zasad w pigułce:

| # | Zasada | Kluczowa myśl |
|---|--------|---------------|
| 1 | **Bądź jasny** | Specyficzność pozwala uciec od generycznych odpowiedzi |
| 2 | **Wyjaśnij dlaczego** | Kontekst pozwala modelowi wnioskować więcej |
| 3 | **Dawaj przykłady** | Model naśladuje przykłady niemal dosłownie |
| 4 | **Mów co robić** | Pozytywne instrukcje > negacje |
| 5 | **Bądź bezpośredni** | Czasowniki akcji, nie sugestie |
| 6 | **Strukturyzuj badania** | Daj researchowi ramy i cele |
| 7 | **Opisuj dokumenty** | Struktura, formatowanie, elementy wizualne |

---

## 📌 Na zakończenie

Te zasady pochodzą bezpośrednio od Anthropic - firmy, która stworzyła Claude'a. To nie są przypadkowe tipy z internetu, tylko **oficjalne wytyczne od twórców modelu**.

Pamiętaj: im lepszy twój prompt, tym lepsza odpowiedź. Warto poświęcić chwilę na przemyślenie prośby, zanim ją wyślesz.

To wszystko!
Enjoy it. 🚀

---

*Źródła: [Wideo na YouTube](https://www.youtube.com/watch?v=GKTkPnqhnf0) | [Oficjalny przewodnik Anthropic](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices)*
