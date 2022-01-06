# Facebook unfollow everything 
## Skrypt do automatycznego odobserwowywania wszystkich użtykowników, stron, itd. Całkowitego czyszczenia wall'a
###### instrukcja:
```
1.Wejdz na swoje konto na FB
2.Kliknij strzałkę menu w prawym górnym rogu 
3.W menu wybierz ustawienia i prywatność
4.Następnie kliknij preferencje aktualnosci
5.Wybierz opcje przestań obserwować
6. scroluj liste ludzi i stron do samego końca aby załadowac wszystko
7. otwórz konsole w przeglądarce f12
8. wklej poniższy skrypt i wcisnij enter
```
###### Facebook nie lubi gdy się odobserwowywuje wszystko więc możliwe, że wyloguje konto kilka razy albo sgłosi błąd. Nie można się zrażać, tylko zacząć raz jeszcze.

```
const follows = document.querySelectorAll('div[aria-label="Przełącz, aby obserwować"]'); // w wersji angielskiej Toggle to follow. Generalnie odnajdowanie przycisku wyłączającego obserwowanie, dlatego nazwa musi się zgadzać.
const delay = 1500 + follows.length; // czas między usunięciami jest różny, aby facebook myslał, że to ręcznie

let i = 0; // licznik usuniętych stron

function unfollow() { // początek funkcji do usuwania
    if (i == follows.length) { // gdy usunie wszystyko to się kończy
        return;
    }

    const remaining = ((follows.length - i) * delay / 1000).toFixed(2); // obliczanie ile jeszcze pozostało

    console.log("Unfollowing", i + 1, "of", follows.length + ",", remaining + "s", "remaining…"); // wypisywanie w konsoli akutalnego stanu 

    follows[i].click(); // wcisnięcie przycisku

    i = i + 1; // iteracja licznika

    setTimeout(unfollow, delay); // odczekiwanie chwili aby zacząć wszystko od początku z kolejną stroną 
}

unfollow(); // start procedury

```
