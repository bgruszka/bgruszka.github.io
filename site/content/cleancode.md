---
date: 2020-05-10
tags: cleancode
---
# Clean Code

Pisanie czystego kodu nie jest łatwe i każdy, kto napisał trochę kodu w swoim życiu wie co mam na myśli. 

Jestem obecnie na etapie lektury (a właściwie powrotu do) "Clean Code" Uncle Boba. Chciałbym wypunktować parę rzeczy, które znalazły się w książce i warto o nich pamiętać. Krótko i zwięźle:

* niech nazwy przedstawiają intencje i komunikują do czego są przeznaczone
* unikanie dezinformacji (np. unikanie skrótów)
  ```php
  $criteria zamiast $c
  ```
* nie używamy magicznych liczb
  ```php
  if($counter === 12)
  ```
  lepiej
  ```php
  if($counter === ALLOWED_ENTRIES)
  ```
* nie stosujemy notacji węgierskiej
  ```php
  $strFirstName
  ```
  lepiej:
  ```php
  $firstName
  ```
* nie stosujemy prefiksu lub postfiksu `Interface`. Interfejs jest tylko abstrakcją
  ```php
  interface CsvWriterInterface
  ```
  lepiej:
  ```php
  interface CsvWriter
  ```
* to że Ty wiesz, że zmienna **`r`** znaczy coś, nie znaczy, że ktoś inny jak będzie to czytał, to będzie też to wiedział
* nazwy klas powinny być rzeczownikami lub wyrażeniami rzeczownikowymi
  ```php
  class User {}
  ```
* nazwy metod powinny być czasownikami lub wyrażeniami czasownikowymi
  ```php
  function login() {}
  ```
* akcesory, mutatory i predykaty powinny być poprzedzone przedrostkiem get, set, is
* będź spójny w ramach bazy kodu - np. fetch, retrieve, get do analogicznych metod w róznych klasach
* dodaj znaczący kontekst - wiele nazw nie niesie za sobą wystarczająco treści - konieczne jest umieszczenie nazw we właściwym kontekście przez wstawienie ich w odpowiednio nazwane klasy, funkcje i przestrzenie nazw
* nie prefiksujemy nazw ogólnoznanym terminem np. "Luksusowa Stacja Benzynowa" używamy w nazwach jako LSBCustomer
* twórz małe funkcje max. 20-30 wierszy
* bloki w instrukcjach if, else, while i podobnych powinny mieć po jednym wierszu i prawdopodobnie wiersze te powinny być wywołaniem funkcji; oznacza to że funkcja nie może być na tyle duża, aby zawierała zagnieżdzone struktury, dlatego poziom wcięć w funkcji nie powinien przekraczać dwóch.
* funkcje powinny wykonywać tylko jedną operację, powinny robić to dobrze. powinny robić tylko to.
* długa opisowa nazwa jest lepsza niż krótka enigmatyczna
* im mniej parametrów przekazywanych do funkcji tym lepiej (najlepiej zero), może trzeba je wydzielić jako parametry klasy
* gdy funkcja wymaga więcej niż dwóch lub trzech argumentów, najprawdopodobniej niektóre z nich powinny być umieszczone w osobnej klasie.
* jeśli funkcja musi zmieniać stan czegokolwiek, powinna zmieniać stan własnego obiektu
* rozdzielanie poleceń i zapytań (funkcje powinny coś wykonywać lub odpowiadać na jakieś pytanie, ale nie powinny robić tych dwóch operacji jednocześnie)
* powinniśmy stosować wyjątki zamiast obsługi błędów