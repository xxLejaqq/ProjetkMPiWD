# Projekt zaliczeniowy z Metod Pozyskiwania i Wizualizacji Danych

**Autor:** Maja Darczuk

## Temat analizy

Jakie zależności występują między danymi technicznymi w analizowanych markach samochodów w Polsce w latach 2021-2023. Jakie cechy charakterystyczne posiadają dane marki. Jaką markę warto wybrać pod względem własnych preferencji.

## Wybór marek aut

Wybrane zostało 10 najpopularniejszych marek aut w Polsce w latach 2021-2023 według danych z Serwisu Rzeczpospolitej Polskiej.

Można zaobserwować znaczną przewagę ilości pojazdów marki Volkswagena i Toyoty. Nieco mniejsze wyniki odnotowały marki Ford, Audi i Opel. Na potrzeby dalszej analizy wybrano 5 najpopularniejszych marek samochodów w Polsce.

## Zescrapowany zbiór danych

Zbiór danych zawiera informacje techniczne 5 najpopularniejszych marek samochodów w Polsce w latach 2021-2023 zescrapowanych ze strony Auto Centrum. Zbiór zawiera **7064 obserwacji** i **13 zmiennych**.

### Opis zmiennych

| Zmienna | Typ | Opis |
|---------|-----|------|
| Marka | chr | Marki samochodu: Volkswagen, Toyota, Ford, Audi, Opel |
| Model | chr | Modele samochodów danych marek |
| Generacja | chr | Generacje samochodów (puste jeśli brak informacji) |
| Wersja | chr | Wersje samochodów (puste jeśli brak informacji) |
| PojemnoscSilnika | num | Pojemność silnika w litrach (0.8 - 7.5) |
| MocSilnika | int | Moc silnika w KM (25 - 925) |
| TypSilnika | chr | Typ silnika: benzynowy, diesel, hybrydowy, hybrydowy plug-in, elektryczny, benzynowy z LPG |
| SrednieSpalanieZuzycie | num | Średnie spalanie w L/100km lub kWh/100km (0.4 - 28.4) |
| Silnik | chr | Szczegółowe nazwy silnika |
| RodzajSkrzyni | chr | Rodzaj skrzyni biegów: manualna, automatyczna, bezstopniowa, zautomatyzowana |
| RodzajNapedu | chr | Rodzaj napędu: na przednią oś, na tylną oś, 4x4 |
| RokRozpoczeciaProdukcji | int | Rok rozpoczęcia produkcji (1938 - 2024) |
| RokZakonczeniaProdukcji | int | Rok zakończenia produkcji (1940 - 2025) |

## Historia marek

### Volkswagen

Ferdinand Porsche zaprojektował w 1934 roku Volkswagena Garbusa – tani, rodzinny samochód mający odciążyć kolej. Nazwa „Volkswagen" oznacza „samochód ludowy". Produkcja ruszyła w 1938 roku. Po II wojnie światowej Garbus stał się symbolem sukcesu marki.

### Toyota

W 1929 roku Kiichirō Toyoda odwiedził USA i Europę. W 1931 roku opracował prototyp silnika spalinowego. W 1937 roku powstała Toyota Motor Company. Obecnie Toyota jest największym producentem samochodów na świecie, sprzedając ponad 10 mln pojazdów rocznie. Toyota jako pierwsza wprowadziła hybrydy spalinowo-elektryczne do masowej sprzedaży.

### Ford

Henry Ford założył Ford Motor Company 16 czerwca 1903 roku w Detroit. Firma stała się jednym z największych producentów samochodów, zajmując drugie miejsce w USA i piąte na świecie. Ford opowiadał się za masową produkcją tanich aut.

### Audi

Niemiecki inżynier August Horch założył Audi 16 lipca 1909 roku w Zwickau. Nazwa przedsiębiorstwa wywodzi się z łacińskiego tłumaczenia nazwiska Horch (oznacza „słuchaj!"). Audi należy do koncernu Volkswagen AG.

### Opel

Adam Opel założył w 1862 roku fabrykę maszyn do szycia, która od 1866 roku produkowała rowery. W 1899 roku rozpoczęto produkcję pierwszego samochodu marki Opel – Opel System Lutzmann.

## Analiza korelacji zmiennych

### Moc silnika
- Silna dodatnia korelacja z PojemnoscSilnika (0.681)
- Umiarkowana dodatnia korelacja z SrednieSpalanieZuzycie (0.435)
- Ujemna korelacja z RodzajNapedu i RodzajSkrzyni

### Rodzaj napędu
- Ujemna korelacja z MocSilnika (-0.348)
- Słabe korelacje z SrednieSpalanieZuzycie i PojemnoscSilnika

### Rodzaj skrzyni
- Najwyższa korelacja z RodzajNapedu (0.440)
- Ujemna korelacja z MocSilnika (-0.502)

### Średnie spalanie
- Umiarkowana dodatnia korelacja z MocSilnika (0.435) i PojemnoscSilnika (0.535)

### Pojemność silnika
- Najsilniejsza korelacja z MocSilnika (0.681)
- Umiarkowana korelacja z SrednieSpalanieZuzycie (0.535)

### Typ silnika
- Brak silnych korelacji z innymi zmiennymi

## Braki danych o średnim spalaniu

| Typ silnika | Odsetek braków |
|-------------|----------------|
| Benzynowy | 23,8% |
| Elektryczny | 11% |
| Hybrydowy | 9,1% |
| Hybrydowy plug-in | 8,9% |
| Diesel | 8,5% |
| Benzynowy z LPG | 0% |

Największy odsetek braków występuje dla silników benzynowych. Najlepiej udokumentowane są silniki benzynowe z LPG.

## Wnioski z analizy

### Spalanie a typ silnika

- **Silnik benzynowy**: Mniejsza efektywność termodynamiczna niż diesel
- **Silnik benzynowy z LPG**: Fabrycznie dostępne w Opel i Volkswagen
- **Silnik diesel**: Bardziej efektywny pod względem spalania paliwa
- **Silnik elektryczny**: Znacznie mniejsze zużycie energii
- **Silnik hybrydowy**: Niższe spalanie dzięki połączeniu dwóch źródeł energii
- **Silnik hybrydowy plug-in**: Możliwość ładowania z zewnętrznego źródła, najniższe spalanie

### Pojemność silnika

- Każda marka oferuje różne podejścia do doboru silników
- Ford i Audi prezentują największą różnorodność pojemności
- Toyota stawia na bardziej zrównoważoną ofertę
- Volkswagen i Opel dominują w segmencie średniej pojemności (1.6L, 2.0L)

### Podział na klastry

Na podstawie średniego spalania i mocy silnika wyodrębniono 8 klastrów:
- Samochody benzynowe i dieslowe charakteryzują się wyższym średnim zużyciem paliwa
- Hybrydy i hybrydy plug-in mają wyraźnie niższe spalanie przy zachowaniu dużej mocy
- Toyota i Volkswagen występują w wielu klastrach, co pokazuje różnorodność oferty

### Rodzaj skrzyni a rodzaj napędu

- Najczęściej spotykana kombinacja: manualna skrzynia biegów + napęd na przednią oś
- Automatyczne skrzynie biegów częściej występują w pojazdach 4x4
- Bezstopniowa (CVT) i zautomatyzowana skrzynia stanowią marginalny procent

## Rekomendacje

### Dla osób szukających ekonomicznych silników
- Toyota i Ford oferują najbardziej ekonomiczne rozwiązania

### Dla osób zainteresowanych hybrydami plug-in
- Audi wyróżnia się w tej kategorii
- Volkswagen i Opel również oferują atrakcyjne opcje

### Dla osób preferujących benzynowe silniki z większą mocą
- Ford i Audi oferują silniki o stabilniejszym spalaniu przy średnich pojemnościach
- Należy liczyć się ze wzrostem spalania przy większych pojemnościach

### Dla osób preferujących niskie spalanie przy dużych pojemnościach
- Toyota oferuje wyjątkową efektywność

### Rekomendacje poszczególnych marek

| Marka | Charakterystyka |
|-------|-----------------|
| Volkswagen | Silnik benzynowy o średniej pojemności, napęd na przednią oś, szeroka oferta diesli |
| Toyota | Pojazdy benzynowe o małej pojemności, napęd na przednią oś, najlepsze hybrydy |
| Ford | Większe silniki, wyższa moc, dobra oferta hybryd |
| Audi | Marka luksusowa, większe silniki, wyższe moce, napęd 4x4, pojazdy elektryczne |
| Opel | Samochody benzynowe z średnimi silnikami, mniejsza moc |

## Technologie użyte w projekcie

- **Język R** - analiza danych i wizualizacja
- **Web Scraping** - pozyskiwanie danych ze strony Auto Centrum
- **ggplot2** - wizualizacja danych

## Źródła danych

- Auto Centrum (https://www.autocentrum.pl/)
- Serwis Rzeczpospolitej Polskiej

## Licencja

Projekt edukacyjny.
