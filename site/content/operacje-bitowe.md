---
date: 2020-06-19
tags: code
---
# Operacje bitowe

Operacje bitowe są wygodną formą manipulowania danymi. 

Wyobraź sobie, że jesteś programistą i masz za zadanie napisac ważny element systemu operacyjnego. Powiedziano Ci, że możesz używać zmiennej przypisanej w następujący sposób:

```python
flagRegister = 0x1234
```

Zmienna przechowuje informacje o różnych aspektach działania systemu. Każdy bit zmiennej przechowuje jedną wartość 0 / 1. Powiedziano Ci również, że tylko jeden z tych bitów należy do Ciebie - trzeci (bity są ponumerowane od zera; bit numer zero jest najniższy, a najwyższy to 31). Pozostałe bity nie mogą się zmieniać, ponieważ są przeznaczone do przechowywania innych danych. Oto twój bit oznaczony literą x →

`flagRegister: 0000000000000000000000000000x000`

Oto co możesz zrobic wykorzystując operacje bitowe:
* sprawdź stan swojego bitu - chcesz poznać wartość swojego bitu; możesz użyć następującej właściwości koniunkcji:
  
  `x & 1 = x`

  `x & 0 = 0`

  Jeśli zastosujesz operację & do zmiennej `flagRegister` wraz z następującym obrazem bitowym:
  `0000000000000000000000000000001000`
  (zwróć uwagę na 1 na pozycji bitu, który Cię interesuje), w wyniku czego otrzymujesz jeden z następujących ciągów bitów:

  `0000000000000000000000000000001000`, jeśli twój bit został ustawiony na 1

  `0000000000000000000000000000000000`, jeśli twój bit został ustawiony na 0

  Taka sekwencja zer i jedynek, których zadaniem jest przechwycenie wartości lub zmiana wybranych bitów, nazywa się maską bitową. Zbudujmy maskę bitową, aby wykryć stan twojego bitu. Dla przypomnienia - jest to trzeci bit licząc od prawej (1000), czyli w tym przypadku 8. Odpowiednią maskę można utworzyć na podstawie następującej deklaracji:

  ```python
  mask = 8
  ```

  Możesz wykonać sekwencję instrukcji w zależności od stanu twojego bitu:

  ```python
  if flagRegister & mask:
      # my bit is set
  else:
      # my bit is reset
  ```

* zresetuj swój bit - przypisujesz zero do swojego bitu, podczas gdy wszystkie inne bity pozostają niezmienione; użyjmy tej samej właściwości koniunkcji, co poprzednio, ale użyjmy nieco innej maski - dokładnie tak jak poniżej:
  111111111111111111111111111111**0**111

  Zauważ, że maska została utworzona w wyniku zanegowania wszystkich bitów zmiennej `mask`. Resetowanie bitu jest proste i wygląda tak:

  ```python
  flagRegister = flagRegister & ~mask
  ```

  ```python
  flagRegister &= ~mask
  ```

* ustaw swój bit - przypisujesz 1 do swojego bitu, podczas gdy wszystkie pozostałe bity muszą pozostać niezmienione; użyj następującej właściwości rozłączenia:
  
  `x | 1 = 1`

  `x | 0 = x`

  Teraz możesz ustawić swój bit, wykonując jedną z poniższych instrukcji:

  ```python
  flagRegister = flagRegister | mask
  ```

  ```python
  flagRegister |= mask
  ```

* Zaneguj swój bit - zamieniasz 1 na 0, a 0 na 1. Możesz użyć interesującej właściwości operatora xor:
  
  `x ^ 1 = ~ x`
  
  `x ^ 0 = x`
  
  Zaneguj swój bit, wykonując poniższe instrukcje:
  
  ```python
  flagRegister = flagRegister ^ mask
  ```

  ```python
  flagRegister ^= mask
  ```

Jak widzisz operacje bitowe są proste i jednocześnie efektywne :)