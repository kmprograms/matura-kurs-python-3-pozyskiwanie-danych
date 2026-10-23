**Polski** · [English](README.en.md)

---

# Matura z informatyki, poziom rozszerzony - kurs Python, lekcja 3. "Pozyskiwanie danych, losowanie, systemy liczbowe i moduł math"

> ### 🎬 Wideo z omówieniem
> Pełne omówienie tej lekcji krok po kroku znajdziesz na moim kanale YouTube:
> **[Link do filmu na YouTube](https://youtu.be/RoBpYAWXxas)**
>
> Na filmie pokazuję, jak pobierać dane z klawiatury, jak losować liczby za pomocą modułu `random`, jak zamieniać wartości między systemami liczbowymi, jak wykonywać operacje bitowe i jakie funkcje oferuje moduł `math`. Cały kod uruchamiam na bieżąco w Pythonie.

---

## Opis

Kod do trzeciej lekcji kursu języka Python, który przygotowuje do matury z informatyki na poziomie rozszerzonym.

Lekcja zaczyna się od pobierania danych wpisywanych z klawiatury i od losowania liczb. Na maturze dane pochodzą najczęściej z pliku tekstowego albo z przykładowych wartości podanych w treści zadania, dlatego oba tematy są omówione skrótowo. Przydają się jednak, gdy chcesz na szybko coś wpisać, wylosować albo poeksperymentować z językiem.

Druga część lekcji to uzupełnienia przydatne przy zadaniach maturalnych: systemy liczbowe, operacje na bitach oraz moduł `math`. W tej lekcji po raz pierwszy w kursie pojawia się też instrukcja `import`.

Repozytorium zawiera również kod z dwóch wcześniejszych lekcji kursu. Kolejna część kursu dotyczy instrukcji warunkowych i pętli.

## Wymagania

- Python 3.8 lub nowszy, ponieważ od tej wersji dostępne są zapis `f"{x1 = }"` w f-stringach oraz funkcja `math.isqrt`
- Brak zewnętrznych zależności, wykorzystano wyłącznie moduły `random` i `math` z biblioteki standardowej

## Uruchomienie

```bash
git clone https://github.com/kmprograms/matura-kurs-python-3-pozyskiwanie-danych
cd matura-kurs-python-3-pozyskiwanie-danych
```

Program z tej lekcji:

```bash
python app-3-pozyskiwanie-danych-systemy-liczbowe-float.py
```

Programy z wcześniejszych lekcji:

```bash
python app-1-pierwszy-program-zmienne.py
python app-2-liczby-calkowite.py
```

W pliku `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` fragment z instrukcją `input` jest zakomentowany. Dzięki temu nie trzeba wpisywać danych od nowa przy każdym uruchomieniu. Aby go wypróbować, usuń znaki `#` na początku tych wierszy.

## Struktura projektu

| Plik | Opis |
| --- | --- |
| `app-1-pierwszy-program-zmienne.py` | Kod z wcześniejszej lekcji: pierwszy program, zmienne i ich typy, f-stringi z formatowaniem wartości, operatory arytmetyczne, zamiana wartości zmiennych, parametry `end` i `sep` funkcji `print`, konwersja typów oraz operatory `+=`, `-=` i `*=` |
| `app-2-liczby-calkowite.py` | Kod z wcześniejszej lekcji: działania na liczbach całkowitych, w tym `**`, `//` i `%`, parzystość i podzielność, operatory relacji, spójniki `and` i `or`, wyznaczanie cyfr liczby oraz zamiana sekund na godziny, minuty i sekundy |
| `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` | Kod z tego nagrania: pobieranie danych za pomocą `input`, losowanie z modułem `random`, systemy liczbowe, operacje bitowe i moduł `math` |

## Omówione zagadnienia

### Pobieranie danych z klawiatury

Dane od użytkownika pobiera się instrukcją `input`. W nawiasie podajesz podpowiedź, która wyświetli się przed miejscem wpisywania danych.

```python
# imie = input("Podaj imię: ")
# print(imie)
#
# a = int(input("Podaj pierwszą liczbę: "))
# b = int(input("Podaj drugą liczbę: "))
# print(f'a + b = {a + b}')
#
# waga = float(input("Podaj wagę: "))
# print(waga + 10)
```

Wszystko, co pobierzesz za pomocą `input`, jest napisem. Możesz to sprawdzić za pomocą `type`. Gdyby zmienne `a` i `b` pobrać bez konwersji, to po wpisaniu `10` i `20` wynikiem `a + b` nie byłoby 30. Operator `+` wykonany na dwóch napisach realizuje konkatenację, więc zobaczylibyśmy dwa sklejone napisy, czyli `1020`.

Dlatego całe wywołanie `input` umieszczamy w nawiasie `int`. Najpierw `input` zwraca napis, a potem `int` zamienia go na liczbę całkowitą. Teraz dla `10` i `20` program wypisuje `a + b = 30`. W ten sam sposób `float` zamienia napis na liczbę zmiennoprzecinkową. Po wpisaniu wagi `12.3` program wypisuje `22.3`.

Jeżeli do `int` trafi coś, co nie jest liczbą, na przykład imię, program zakończy się błędem. Taki błąd można przechwycić i obsłużyć na kilka sposobów. Na potrzeby przygotowania do matury zakładamy jednak, że zawsze wpisujemy takie dane, jakich program oczekuje.

### Losowanie liczb

Do losowania potrzebny jest moduł `random`, który trzeba zaimportować instrukcją `import random`. W języku Python niektóre moduły importujemy dopiero wtedy, gdy są nam potrzebne.

```python
x1 = random.randint(1, 6)  # Wartość od 1 do 6
print(f"{x1 = }")

x2 = random.uniform(2, 19.3)
print(f"{x2 = } lub {round(x2, 2)}")

x3 = random.randrange(0, 100, 2)  # 0, 2, 4, ..., 98
print(f"{x3 = }")
```

| Funkcja | Działanie |
| --- | --- |
| `random.randint(1, 6)` | Losuje liczbę całkowitą z przedziału od 1 do 6, razem z końcami przedziału |
| `random.uniform(2, 19.3)` | Losuje liczbę zmiennoprzecinkową z przedziału od 2 do 19.3 |
| `random.randrange(0, 100, 2)` | Losuje wartość z ciągu 0, 2, 4, ..., 98 |

Wylosowaną liczbę zmiennoprzecinkową można zaokrąglić funkcją `round`. Wywołanie `round(x2, 2)` zaokrągla wartość do dwóch miejsc po przecinku.

Zapis `f"{x1 = }"` wypisuje nazwę zmiennej razem z jej wartością, na przykład `x1 = 5`. Dzięki temu od razu widać, której zmiennej dotyczy wynik.

Komputer tak naprawdę nie losuje liczb, tylko je wylicza. W uproszczeniu robi to na podstawie pewnego zaszytego ciągu liczbowego. Zmienność otrzymanych wartości jest jednak na tyle duża, że możemy traktować je jak losowe. Precyzyjnie mówi się o wartościach pseudolosowych.

### Systemy liczbowe

```python
n = 2026
print(bin(n))
print(oct(n))
print(hex(n))

s1 = 0b10001011
s2 = 0o17
s3 = 0xff

print(int("1101", 2))
print(int("12", 3))
```

Funkcje `bin`, `oct` i `hex` zwracają zapis liczby w systemie dwójkowym, ósemkowym i szesnastkowym. Otrzymane wyniki są napisami.

Python pozwala też zapisywać liczby bezpośrednio w innych systemach. Prefiks `0b` oznacza system dwójkowy, `0o` ósemkowy, a `0x` szesnastkowy. Zmienne `s1`, `s2` i `s3` przechowują zwykłe liczby całkowite 139, 15 i 255.

Zamianę z dowolnego systemu na dziesiętny wykonuje `int`, któremu oprócz napisu podajesz podstawę systemu. `int("1101", 2)` daje 13, a `int("12", 3)` daje 5. Wynikiem są zwykłe liczby całkowite, na których można wykonywać działania arytmetyczne.

Ręcznego przeliczania wartości między systemami i wykonywania w nich działań uczymy się na innym etapie przygotowania do matury.

### Operacje bitowe

```python
a = 0b1010
b = 0b1100

print(bin(a & b))
print(bin(a | b))
print(bin(a ^ b))
print(bin(12 << 1))
print(bin(12 >> 1))
```

| Operator | Operacja |
| --- | --- |
| `&` | Bitowe i (AND) |
| `\|` | Bitowe lub (OR) |
| `^` | Bitowa alternatywa wykluczająca (XOR) |
| `<<` | Przesunięcie bitów w lewo |
| `>>` | Przesunięcie bitów w prawo |

Liczba po prawej stronie operatora `<<` lub `>>` określa, o ile pozycji przesuwamy bity. Funkcja `bin` pokazuje wynik w postaci binarnej i pomija zera wiodące, dlatego wynik XOR, czyli `0110`, wyświetla się jako `0b110`.

### Moduł math

Moduł `math` również trzeba zaimportować. Zawiera wiele funkcji matematycznych oraz stałych.

```python
print(math.sqrt(19))
print(math.isqrt(19))
print(19 ** 0.5)
print(math.pow(2, 10))
print(math.floor(19 ** 0.5))
print(math.ceil(19 ** 0.5))
```

| Wyrażenie | Działanie |
| --- | --- |
| `math.sqrt(19)` | Pierwiastek kwadratowy |
| `math.isqrt(19)` | Część całkowita pierwiastka kwadratowego |
| `19 ** 0.5` | Potęga o wykładniku jedna druga, czyli również pierwiastek kwadratowy |
| `math.pow(2, 10)` | Potęgowanie, wynik jest liczbą zmiennoprzecinkową |
| `math.floor(19 ** 0.5)` | Zaokrąglenie w dół |
| `math.ceil(19 ** 0.5)` | Zaokrąglenie w górę |

### Dokumentacja

Na końcu pliku znajdują się linki do dokumentacji obu modułów:

- [Moduł `math`](https://docs.python.org/3/library/math.html)
- [Moduł `random`](https://docs.python.org/3/library/random.html)

W dokumentacji znajdziesz przegląd wszystkich funkcji i stałych modułu. Po kliknięciu w funkcję zobaczysz jej opis, a gdy to możliwe, także przykład kodu równoważnego jej działaniu albo pokazującego jej zastosowanie. Dokumentacja modułu `random` kończy się zestawem przykładów. Warto ją przejrzeć, żeby wiedzieć, gdzie szukać kolejnych funkcji i ich opisów.

## Odniesienie do matury

Na maturze z informatyki dane do zadań programistycznych pochodzą najczęściej z pliku tekstowego. Czasem trzeba też sprawdzić działanie zaimplementowanej funkcji dla przykładowych wartości z treści zadania. Pobieranie danych z klawiatury i losowanie przydają się głównie podczas nauki, eksperymentów i rozwiązywania zadań ćwiczeniowych.

Konwersje między systemami liczbowymi na maturze bardzo często trzeba wykonać ręcznie. Funkcje `bin`, `oct`, `hex` oraz `int` z podaną podstawą przydają się wtedy, gdy możesz skorzystać z możliwości języka Python.

Jeżeli na maturze pojawią się operacje bitowe, bardziej prawdopodobne jest, że trzeba będzie napisać własny algorytm, niż że wystarczą gotowe operatory. W zadaniach z programowania na plikach tekstowych, w których nie ma formułki ograniczającej dozwolone elementy języka, znajomość tych operatorów może jednak przyspieszyć rozwiązanie.

## Wyniki

Pierwsze trzy wiersze wypisywane przez `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` zależą od losowania i zmieniają się przy każdym uruchomieniu. Na nagraniu `random.randint(1, 6)` zwróciło 5, a `random.randrange(0, 100, 2)` zwróciło 6. Dla `x2` program wypisuje wylosowaną wartość oraz jej zaokrąglenie do dwóch miejsc po przecinku.

Część dotycząca systemów liczbowych i operacji bitowych zawsze wypisuje to samo:

```
0b11111101010
0o3752
0x7ea
13
5
0b1000
0b1110
0b110
0b11000
0b110
```

Ostatnie sześć wierszy to wyniki funkcji z modułu `math`:

| Wyrażenie | Wynik |
| --- | --- |
| `math.sqrt(19)` | 4.3588... |
| `math.isqrt(19)` | 4 |
| `19 ** 0.5` | 4.3588... |
| `math.pow(2, 10)` | 1024.0 |
| `math.floor(19 ** 0.5)` | 4 |
| `math.ceil(19 ** 0.5)` | 5 |

Przy pierwiastku Python wypisuje pełną wartość zmiennoprzecinkową. W tabeli jest ona skrócona do czterech miejsc po przecinku.

## Uwagi implementacyjne

Instrukcje `import random` i `import math` znajdują się na początku pliku `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py`. To pierwszy plik w kursie, który korzysta z importu modułów.

Fragment z `input` jest zakomentowany, aby program dało się uruchamiać bez wpisywania danych przy każdym starcie.

Wyniki funkcji `bin`, `oct` i `hex` są napisami, a wyniki `int` z podaną podstawą to liczby całkowite. Napisy omawiamy dokładniej w dalszej części kursu.

`math.isqrt` zwraca liczbę całkowitą, natomiast `math.pow` zwraca liczbę zmiennoprzecinkową, stąd wynik `1024.0`.

Zmienne `s1`, `s2` i `s3` nie są wypisywane. Pokazują jedynie, jak zapisywać liczby w systemie dwójkowym, ósemkowym i szesnastkowym bezpośrednio w kodzie.