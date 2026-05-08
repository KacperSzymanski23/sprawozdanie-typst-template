# Szablon sprawozdań – Politechnika Krakowska `[W.I.P.]`

Szablon do tworzenia sprawozdań laboratoryjnych na **Politechnice Krakowskiej** za pomocą [Typst](https://github.com/typst/typst). Automatycznie generuje stronę tytułową z danymi uczelni, prowadzącego i zespołu itd. w skrócie ułatwia robotę.

---

## Pliki szablonu

| Plik                             | Opis                                                 |
| -------------------------------- | ---------------------------------------------------- |
| `template.typ`                   | Główny plik szablonu, **nie edytuj**                 |
| `main.typ`                       | Plik roboczy, w tym pliku piszesz sprawozdanie       |
| `pk_logo.svg`                    | Logo Politechniki Krakowskiej                        |
| `weik_logo.svg`                  | Logo Wydziału Inżynierii Elektrycznej i Komputerowej |
| `Agila Monokai Extended.tmtheme` | Motyw kolorystyczny podświetlania składni kodu       |

---

## Wymagania

- [Typst](https://github.com/typst/typst) `>= 0.11`
- [GhostScript](https://www.ghostscript.com/) - do zmniejszenia rozmiaru pliku PDF (opcjonalny ale rekomendowany)
- Czcionki zainstalowane w systemie (możesz je zastąpić swoimi):
  - [Noto Sans](https://fonts.google.com/noto/specimen/Noto+Sans) — domyślna czcionka tekstu
  - [Fira Code](https://github.com/tonsky/FiraCode) — domyślna czcionka bloków kodu
  - [Nerd Fonts](https://www.nerdfonts.com) — ikony w ramkach (opcjonalnie)
- Edytor Typst, możesz korzystać z VS Code z zainstalowanym rozszerzeniem [Tinymist](https://github.com/Myriad-Dreamin/tinymist) lub z domyślnego edytora [Typst](https://typst.app/)

---

## Jak użyć szablonu

1. Sklonuj repozytorium:

   ```sh
   git clone <adres-repozytorium>
   cd <katalog>
   ```

   Albo po prostu pobierz plik .zip z repozytorium.

2. Uzupełnij metadane sprawozdania w `main.typ`:

   ```typst
   #show: report.with(
     title: "Temat ćwiczenia",
     author: "Jan Kowalski, Anna Nowak",
     many-authors: true,
     course: "Nazwa przedmiotu",
     group: "L4",
     lecturer-name: "Mariusz Garota",
     academic-title: "dr inż.",
     date-format: "[day].[month].[year]",
   )
   ```

3. Skompiluj do PDF:

   ```sh
   typst compile main.typ
   ```

4. (Opcjonalnie) Aby zmniejszyć rozmiar pliku wygenerowanego PDFa za pomocą GhostScript:

   ```sh
   gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook \
      -dNOPAUSE -dQUIET -dBATCH -sOutputFile="OUTPUT.pdf" main.pdf
   ```

   Naprawdę bez tego pliki PDF wygenerowane przez Typst potrafią mieć 30MiB i więcej, więc będzie ciężko go załączyć w mailu. [GhostScript](https://www.ghostscript.com/) to najlepszy sposób na zmniejszenie rozmiaru pliku.

---

## Dostępne elementy szablonu

### Równania

```typst
#eq($T(n) = O(n log n)$)
```

Zawiera dodatkowy styl dla równań (na razie jest trochę biedny).

### Blok kodu z podświetlaniem składni

````typst
#code-block(lang: "Python", syntax-theme: "Agila Monokai Extended.tmtheme")[
  ```python
  def hello():
      print("Hello, World!")
  ```
]

````

### Ramki informacyjne

| Funkcja          | Zastosowanie              |
| ---------------- | ------------------------- |
| `#warn-box[...]` | Ostrzeżenia i ważne uwagi |
| `#info-box[...]` | Informacje i założenia    |
| `#tip-box[...]`  | Wskazówki i podpowiedzi   |
| `#note-box[...]` | Dodatkowe notatki         |

### Grafiki

```typst
#figure(
  image("wykres.svg", width: 80%),
  caption: [Podpis rysunku],
)
```

> Jeśli umieszczasz jakieś grafiki w sprawozdaniu np. wykresy, diagram itp. to preferuj format `.svg`, aby uniknąć problemów z rozmiarem PDF. W przypadku innych formatów skorzystaj z GhostScript do zmniejszenia rozmiaru pliku.

---

## W szablonie wykorzystano

- [**Agila Monokai Theme** by arvi](https://github.com/arvi/Agila-Theme) — motyw kolorystyczny dla bloków kodu
- [**Typst**](https://github.com/typst/typst) — nowy system do generowania dokumentów à la LaTeX
- [**Fira Code** by Nikita Prokopov](https://github.com/tonsky/FiraCode) — czcionka dla kodu źródłowego
- [**Nerd Fonts**](https://www.nerdfonts.com) — ikony
- [**GhostScript**](https://www.ghostscript.com/) — do zmniejszenia rozmiaru PDFów
- [**Logo Wydziału i Uczelni**](https://wieik.pk.edu.pl/)
