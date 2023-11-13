# VIM Guide

---

## W trybie nieinteraktywnym:

- `x` - usuwa litery
- `dd` - usuwa linię
- `dw` - usuwa słowo
- `o` - przechodzi linijkę niżej i włącza tryb interaktywny
- `a` - przechodzi literę/znak dalej i włącza tryb interaktywny
- `w` - przechodzi do początku następnego wyrazu
- `e` - przechodzi do końca następnego wyrazu
- `Shift + 6` - przechodzi na początek linii
- `Shift + 4` - przechodzi na koniec linii
- `b` - przechodzi do początku obecnego wyrazu i każdego poprzedniego
- `0` - przenosi do początku linijki, ale tylko tej, na której obecnie się znajdujesz
- `gg` - przenosi na początek tekstu
- `Shift + gg` - przenosi na koniec tekstu
- `r` - gdy jesteśmy na danej literze, klikamy "r" i literę/znak, którą chcemy ją zastąpić
- `u` - (undo) usuwa wprowadzone przez nas zmiany
- `.` - gdy wprowadziliśmy jakieś zmiany, np. wpisaliśmy "test test", kliknięcie "." skopiuje i wklei to
- `Shift + zz` - zapisuje i wychodzi z pliku (alternatywa dla `wq!`)
- `:` + `f` - wyświetla nazwę pliku, w którym jesteśmy

---

## Jeśli mamy np { tekst }, to kombinacja "Shift + %" przeniesie nas do łączącej się w pary klamry (będzie przeskakiwać pomiędzy nimi)

---

## Jeśli chcę przeskoczyć o np 9 wyrazów, klikam (w trybie nieinteraktywnym) "9w". Jeśli chcę się cofnąć o np 9 wyrazów, klikam (w trybie nieinteraktywnym) "9b"

---

## Jeśli chcę zastąpić np 4 litery jakimś znakiem, to klikam "4r" i znak, którym chcę zastąpić
## Jeśli chcę usunąć np 10 liter, to klikam "10x"

---

## Żeby skopiować całą linię, klikam "yy", a następnie "p", żeby wkleić w dowolnym miejscu
## Żeby skopiować dowolny tekst, klikam "v", zaznaczam to, co chcę skopiować, następnie "y", a potem wklejam w dane miejsce "p"

---

## Aby sprawdzić coś w pliku tekstowym, bez wychodzenia z niego - ":" a następnie "! ls -al ~"
## Aby wkleić coś w obecnym pliku tekstowym z innego, bez wychodzenia z niego - ":" a następnie "! cat <ścieżka_do_pliku>"
## Aby przenieść output z komendy do obecnego pliku tekstowego, bez wychodzenia z niego - ":" a następnie np. "! ls -al /etc/ | wc -l"
## Aby posortować dane linie w tekście - ":" a następnie np. "<nr_linii>,<nr_linii> ! sort -r"

---

## W przypadku gdy wprowadziliśmy jakąś zmianę w tekście, ale nie chcemy zapisać jej w obecnym pliku, tylko w innym - ":" a następnie "saveas <nazwapliku.txt>"

---

## W trybie interaktywnym:

- `Ctrl + u` - usuwa całą linię od momentu (<), w którym się znajdujesz

---

## W CLI:

- `Ctrl + a` - przechodzimy na początek linii
- `Ctrl + e` - przechodzimy na koniec linii

---

## Inny sposób na poruszanie się po ekranie zamiast strzałek:

- `h` - lewo
- `l` - prawo
- `k` - góra
- `j` - dół
