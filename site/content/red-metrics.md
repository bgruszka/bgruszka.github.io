---
date: 2025-09-19
tags: metrics,devops,observability
---
# Metryki RED – prosty sposób na zrozumienie zdrowia systemu

Monitorowanie systemów rozproszonych, mikroserwisów czy aplikacji webowych może wydawać się trudne. W praktyce jednak nie zawsze potrzebujemy zaawansowanych, skomplikowanych narzędzi – czasami wystarczy prosty model, który pomoże nam ocenić, czy wszystko działa jak należy.

Jednym z takich modeli są metryki RED:
* Rate – liczba żądań na sekundę
* Errors – liczba błędów na sekundę
* Duration – czas trwania żądań

Brzmi prosto? Bo takie właśnie ma być 🙂

## Rate – ile żądań przetwarza twój system

Pierwsza metryka mówi nam, jak bardzo "obciążony" jest system. To po prostu tempo obsługi żądań.

Możesz na przykład sprawdzić:

```bash
requests_per_second = total_requests / observation_time
```

Dlaczego to ważne?
* pozwala zauważyć skoki ruchu,
* ułatwia planowanie pojemności systemu,
* pokazuje, czy system w ogóle przyjmuje żądania (bo jeśli tempo nagle spada do zera, to mamy problem 😉).

## Errors – jakie błędy pojawiają się w systemie

Nie wystarczy wiedzieć, ile żądań trafia do aplikacji – trzeba też wiedzieć, ile z nich kończy się niepowodzeniem.

```bash
error_rate = failed_requests / total_requests
```

Monitorując błędy, zwróć uwagę na:
* nagłe skoki błędów 5xx (problem po stronie serwera),
* błędy 4xx (np. niepoprawne dane wejściowe),
* nietypowe kody statusu, które mogą oznaczać problemy w logice aplikacji.

Dzięki tej metryce bardzo szybko dowiesz się, czy system działa poprawnie – nawet jeśli nadal odpowiada na żądania.

## Duration – ile trwa obsługa żądania

Trzecia metryka dotyczy czasu reakcji. Użytkownik może nie zauważyć, że serwer obsłużył milion żądań – ale na pewno zauważy, jeśli każda strona ładuje się 5 sekund.

Dlatego mierzymy:

```bash
avg_duration = total_time / total_requests
```

Możesz też śledzić percentyle (np. P95, P99), żeby zobaczyć, jak wygląda doświadczenie większości użytkowników, a nie tylko średnia.

## Dlaczego RED działa tak dobrze?

Bo te trzy proste metryki wystarczą, żeby odpowiedzieć na kluczowe pytania:
* czy mój system działa? (Rate)
* czy działa poprawnie? (Errors)
* czy działa wystarczająco szybko? (Duration)

Nie potrzebujesz od razu setek wskaźników ani skomplikowanych dashboardów – wystarczy RED jako podstawa monitoringu.

Jak widzisz, metryki RED są proste i jednocześnie skuteczne 🙂
Jeśli wprowadzisz je do swojego systemu, będziesz miał zawsze jasny obraz tego, co się dzieje – niezależnie od tego, jak skomplikowana jest twoja architektura.