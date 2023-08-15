VIM guide
 
=================================================================================================================================================================
*W trybie nie interaktywnym:
x - usuwa litery
dd - usuwa linię
dw - usuwa słowo
o - przechodzi linijke niżej i włącza tryb interaktywny
a - przechodzi litere/znak dalej i włacza tryb interaktywny
w - przechodzi do poczatku nastepnego wyrazu
e - przechodzi do końca następnego wyrazu
shift + 6 - przechodzi na początek linii
shift + 4 - przechodzi na koniec linii
b - przechodzi do poczatku obecnego wyrazu i kazedgo poprzedniego
0 - przenosi do poczatku linijki, ale tylko tej, na której obecnie się znajduję
gg - przenosi na początek tekstu
shift + gg - przenosi na koniec tekstu
r - gdy jestesmy na danej literze klikamy "r" i litere/znak jaka chcemy ją zastąpić
u - (undo) usuwa wprowadzone przez nas zmiany
. - gdy wprowadzilismy jakies zmiany np. wpisalismy "test test" klikniecie "." skopiuje i wklei to
shift + zz - zapisuje i wychodzi z pliku (alternatywa dla wq!)
: + f - wyświetla nazwe pliku, w którym jesteśmy
 
=================================================================================================================================================================
*Jeśli mamy np { tekst }, to kombinacja "shift + %" przeniesie nas do łączącej się w pary klamry (będzie przeskakiwać pomiędzy nimi)
 
*Jeśli chcę przeskoczyć o np 9 wyrazów klikam (w trybie nie interaktywnym) "9w", Jeśli chcę się cofnąć o np 9 wyrazów klikam (w trybie nie interaktywnym) "9b"
 
*Jeśli chcę zastąpić np 4 litery jakims znakiem to klikam "4r" i znak jakim chce zastąpic
*Jeśli chcę usunac np 10 liter to klikam "10x"
 
*Żeby skopiowac cala linie klikam "yy" i "p" zeby wkleic w dowolnym miejscu
*Żeby skopiowac dowolny tekst klikam "v" i zaznaczam co chce skopiowac, nastepnie "y" i wklejam w dane miejsce "p"
 
*Aby sprawdzić coś w pliku tekstowym, bez wychodzenia z niego - ":" a następnie  " ! ls -al ~"
*Aby wkleić coś w obecnym pliku tekstowym z innego, bez wychodzenia z niego - ":" a następnie  "r ! cat <ścieżka_do_pliku>"
*Aby przenieść output z komendy do obecnego pliku tekstowego, bez wychodzenia z niego - ":" a następnie np.  "r !  ls -al /etc/ | wc -l"
*Aby przesortowac dane linie w tekscie - ":" a następnie np.  "<nr_linii>,<nr_linii> ! sort -r"
 
*W przypadku gdy wprowadziliśmy jakąś zmiane w tekscie ale nie cchemy zapisac jej w obecnym pliku tylko w innym - ":" a następnie "saveas <nazwapliku.txt>"
 
=================================================================================================================================================================
*W trybie interaktywnym:
ctr + u - usuwa całą linię od momemntu (<), w którym sie znajdujesz
 
=================================================================================================================================================================
*W CLI:
ctr + a - przechodzimy na początek linii
ctr + e - przechodzimy na koniec linii
 
=================================================================================================================================================================
*Inny sposob na poruszanie sie po ekranie zamiast strzałek
h - lewo
l - prawo
k - góra
j - dół
 
