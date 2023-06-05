# Egzamin zawodowy inf.04
---
## cpp - oznacza C++
## cs - oznaczna C#
---

## Rozdziały:
1. Konsolowe:
   1. Algorytmy
   2. Klasy 
2. Mobilne
3. Webowe
4. Desktopowe

# 1.

#### W tej części opisane będą algorytmy które wystąpiły juz w poprzednich egzaminach oraz te które mogą wystąpic

## Generowanie liczb losowych
##### Kod w C++
```cpp
  #include <stdlib.h> // niezbędne dla funkcji srand i rand
  #include <time.h> // niezbędne dla funkcji time
  srand(time(NULL));
  (rand() % 200) - 100 // w ten sposób uzyskuje się pseudolosowe liczby o zakresie od - 100 do 100
```
##### Kod C#
```cs
  Random rnd = new Random();
  rnd.Next(10, 20) // zwraca losową liczbę w zakresie <10,20)
```
---
## Inf.04 2021 Czerwiec Sortowanie przez wybieranie

Jak działa ten algorytm opisane jest na egzaminie, mieliśmy go juz wiele razy więc nie będę streszczał jego działania

##### Kod w C++
```cpp
  void selection_sort(int tab[],int n) { //n - ilość elementów do posortowania
  int mn_index; //zmienna pomocnicza przechowująca indeks komórki 
          //z minimalną wartością
    for(int i=0;i<n-1;i++) {
      mn_index = i;

      //pętla wyszukuje najmniejszy element w podzbiorze nieposortowanym
      for(int j=i+1;j<n;j++) 
      if(tab[j]<tab[mn_index]) mn_index = j;
  
      //zamiana elementu najmniejszego w podzbiorze z pierwszą pozycją nieposortowaną
      swap(tab[i], tab[mn_index]);
    }
  } 
```
*kod jest z komentarzami, więc nie powinno byc problemu w razie co aby go przerobic pod egzamin*
##### Kod C#
```cs
  static int[] InsertionSort(int[] inputArray) {
    for (int i = 0; i < inputArray.Length - 1; i++) {
        for (int j = i + 1; j > 0; j--) {
          if (inputArray[j - 1] > inputArray[j]) {
            int temp = inputArray[j - 1];
            inputArray[j - 1] = inputArray[j];
            inputArray[j] = temp;
          }
        }
    }
    return inputArray;         
  }
```
---
## Inf 04 rok 2022 Czerwiec Przeszukiwanie z wartownikiem

Opis tego algorytmu równiez jest na egzaminie, jest on tam dobrze wytłumaczony

#### Kod w C++
```cpp
  //przeszukanie tablicy
  while(tab[i] != szukana && tab[i] != -1) ++i; 
  //koniec wyszukiwania    
  //jeśli zatrzymaliśmy się na wartowniku, to oznacza, 
  //że szukana liczba nie występuje w zbiorze    
  if(tab[i] == -1) {
    cout << "Szukany element nie występuje w tablicy" << endl;
  }
  else {
    cout << "Liczba " << szukana << " znajduje się na pozycji " << i+1 << endl;
  }
    
```
#### Kod w C#
```cs
//szukaj elementu x
  a[n] = x;
  i = 0;
  while (a[i] != x) i++;
  //podaj wynik
  if (i == n) {
    Console.WriteLine("Nie znaleziono w tablicy elementu " + x);
  }
  else {
    Console.WriteLine("Odnaleziono element " + x + " pod indeksem " + i);
  }
```
---
## Inf 04 2023 Styczen NWD
No tutaj jest nwd nic skomplikowanego

#### Kod C++
```cpp
  int NWD(int a, int b) {
      while(a != b)
        if(a > b)
            a-=b; //lub a = a - b;
        else
            b-=a; //lub b = b - a
      return a; // lub b - obie zmienne przechowują wynik NWD(a,b)
  }
```
*Kodu w C# nie zamieszczam bo to jest to samo co c++*

# Następne algorytmy nie pojawiły się jeszcze na egzaminie ale mogą się pojawic lub są po prostu przydatne

---
## Wyszukiwanie binarne
Raczej jest mała szansa na to ze się trafi jednak jest to popularny algorytm więc go zamieszczę

### Opis:
Algorytm szuka danego elementu w tablicy uporządkowanej (posortowanej). Algorytm jest realizowany metodą "dziel i zwyciężaj". Dzieli on tablicę na mniejsze podtablice do momentu wyszukania pozycji (lub nie w przypadku gdy taki element nie istnieje) elementu szukanego. Wykorzystuje on 3 zmienne pomocnicze:
1. l - lewa
2. p - prawa
3. sr - srodek
#### Kod w C++
```cpp
  long long tab[1000000]; //tablica z posortowanymi elementami

  //l - lewy index tablicy, p - prawy index tablicy
  int szukaj(int l, int p, long szukana) {
    int sr;
    while(l<=p) {
      sr = (l + p)/2;
      
      if (tab[sr] == szukana) return sr;
      if (tab[sr] > szukana) p = sr - 1;
      else l = sr + 1;
    }
    return -1; //zwracamy -1, gdy nie znajdziemy elementu
  }
```

#### Kod C#
```cs
  public static object BinarySearchIterative(int[] inputArray, int key) { 
    int min = 0;
    int max = inputArray.Length - 1; 
      while (min <=max) {  
        int mid = (min + max) / 2;  
        if (key == inputArray[mid]) return ++mid;  
        else if (key < inputArray[mid]) max = mid - 1;  
        else min = mid + 1;
    }  
    return "Nil";  
  }  
```
---
## Sortowanie bąbelkowe
Chyba wszystkim znany algorytm sortowania więc opis jest zbędny.
#### Kod C++
```cpp
void sortowanie_babelkowe(int tab[],int n)
{
	for(int i = 0; i < n; i++) {
    //pętla wewnętrzna
    for(int j = 1; j < n-i; j++) {
      //zamiana miejscami
      if(tab[j-1] > tab[j]) swap(tab[j-1], tab[j]);
    }
  }
		
}
```
#### Kod C#
```cs
   static void BubbleSort(int[] arr) {
      int n = arr.Length;
      for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
          if (arr[j] > arr[j + 1]) {
            int temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
          }
        }
      }
        
   }
```
---
## Sortowanie szybkie
Szczerze mówiąc, opis jest spory, więc nie zamieszczę go teraz, jezeli trafi się na egzaminie to pewnie tam się on znajdzie. Algorytm jest szybki i to tyle wystarczy.
#### Kod w c++
```cpp
void quick_sort(int *tab, int lewy, int prawy) {
	if(prawy <= lewy) return;

	int i = lewy - 1, j = prawy + 1, 
	pivot = tab[(lewy+prawy) / 2]; //wybieramy punkt odniesienia
	
	while(1) {
		//szukam elementu wiekszego lub rownego piwot stojacego
		//po prawej stronie wartosci pivot
		while(pivot > tab[++i]);
		
		//szukam elementu mniejszego lub rownego pivot stojacego
		//po lewej stronie wartosci pivot
		while(pivot < tab[--j]);
		
		//jesli liczniki sie nie minely to zamień elementy ze soba
		//stojace po niewlasciwej stronie elementu pivot
		if( i <= j)
			//funkcja swap zamienia wartosciami tab[i] z tab[j]
			swap(tab[i], tab[j]);
		
    else break;
	}

	if(j > lewy) quick_sort(tab, lewy, j);
	if(i < prawy) quick_sort(tab, i, prawy);
}
```
#### Kod w C#
```cs
  public int[] SortArray(int[] array, int leftIndex, int rightIndex) {
      var i = leftIndex;
      var j = rightIndex;
      var pivot = array[leftIndex];

      while (i <= j) {
          while (array[i] < pivot) {
              i++;
          }
          
          while (array[j] > pivot) {
              j--;
          }
          if (i <= j) {
              int temp = array[i];
              array[i] = array[j];
              array[j] = temp;
              i++;
              j--;
          }
      }
      
      if (leftIndex < j) SortArray(array, leftIndex, j);
      if (i < rightIndex) SortArray(array, i, rightIndex);

      return array;
  }
```
# TODO: jakieś inne algorytmy
---
## Klasy
  Przypomnienie jak działają klasy, na czym polega hermetyzacja, dzedziczenie, instancje itp.

---
## Tworzenie klas, instancji, konstruktory, metody

```cpp
  class Osoba {
  public:
      int wiek;
      int wzrost;
  private: 
      int nrKartyKredytowej;
      
  public: 
      Osoba() {
          ...
          //Konstruktor bezparametrowy
      }
      Osoba(int wiekK, int wzrostK, int kartaK) {
          this.wiek = wiekK;
          this.wzrost = wzrostK;
          this.nrKartyKredytowej = kartaK;
          //Konstruktor z parametrami
      }
  };

//Utworzenie instacji
Osoba nazwainstancji;
```
*TODO: dodaj ktoś konstruktor kopiujący/wirtualny w c++ bo mi się nie chce i nie wiem jak to działa w tym języku*
```cs
  public class Osoba {
    static public int wiek;
    static public int wzrost;
    static private int nrKartyKredytowej;
    //W c# zamiast konstruktorów mozna uzyc setterów
    // public int wiek {get; set;}
    //Jest to ekwiwalent
    //Osoba(int wiekK) {this.wiek = wiekK}
    
    //Konstruktor bezparametrowy
    Osoba() {
      ...
    }

    Osoba(int wiekK, int wzrostK, int kartaK) {
      this.wiek = wiekK;
      this.wzrost = wzrostK;
      this.nrKartyKredytowej = kartaK;
      //Konstruktor z parametrami
    }

    Osoba(Osoba poprzedniaOsoba) {
      this.wiek = poprzedniaOsoba.wiek;
      this.wzrost = poprzedniaOsoba.wzrost;
      this.nrKartyKredytowej = poprzedniaOsoba.nrKartyKredytowej
      //Konstruktor kopiujący
    }

    public void Metoda() {
        //tutaj kod metody
    }

    public void MetodaZWielomaParametrami(params int[] values) {
      int sum = 0;
      foreach (int value in values) {
          sum += value;
      }
      return sum;
      //Przykladowy kod
    }
  }
  //Utworzenie instacji
  Osoba nazwaInstancji = new Osoba();
```
---
## Dziedziczenie
operator_widoczności może przyjmować jedną z trzech wartości: `public, protected, private`. Operator widoczności przy klasie, z której dziedziczymy pozwala ograniczyć widoczność elementów publicznych z klasy bazowej.

1. `public` - oznacza, że dziedziczone elementy `(np. zmienne lub funkcje)` mają taką widoczność jak w klasie bazowej.
2. `protected` - oznacza, że elementy publiczne zmieniają się w chronione.
3. `private` - oznacza, że wszystkie elementy klasy bazowej zmieniają się w prywatne.
4. `brak operatora` - oznacza, że niejawnie `(domyślnie)` zostanie wybrany operator private.

W c++ schemat wygląda następująco:
```cpp
   class nazwa_klasy :[operator_widocznosci] nazwa_klasy_bazowej, [operator_widocznosci] nazwa_klasy_bazowej ... {
        definicja_klasy
   };

   //przykład
   class Nastolatek : private Osoba {
    public:
        string Imie;
        ...
    //w tym przypadku pola dziedziczące np. wiek zamienia się w pole prywatne
   }
```

Dziedziczenie w c# wygląda tak samo, jednak tutaj dodaje przedrostki i ich wytłumaczenie:

##### Przedrostek "static":
Przedrostek "static" oznacza, że dana metoda lub pole należy do klasy, a nie do instancji tej klasy. Oznacza to, że możesz odwoływać się do metody lub pola bez konieczności tworzenia obiektu klasy. Metody statyczne są wywoływane za pomocą składnika klasy, a nie instancji.

##### Przedrostek "override":

Przedrostek "override" jest używany w celu nadpisania metody zdefiniowanej w klasie bazowej. Oznacza to, że klasa pochodna dostarcza własną implementację dla metody, która jest już zdefiniowana w klasie bazowej. Metoda w klasie pochodnej musi mieć ten sam nagłówek (tzn. typ zwracany, nazwa i parametry) co metoda w klasie bazowej.

##### Przedrostek "virtual":

Przedrostek "virtual" jest używany w klasie bazowej do oznaczenia metody, która może być nadpisana w klasach pochodnych. Metoda w klasie bazowej, oznaczona jako "virtual", dostarcza podstawową implementację, ale klasy pochodne mogą ją nadpisać, jeśli jest to wymagane.

##### Przedrostek "abstract":

Przedrostek "abstract" jest używany do oznaczenia klasy lub metody abstrakcyjnej. Klasa abstrakcyjna służy jako szablon dla klas pochodnych, ale nie może być bezpośrednio instancjonowana. Metoda abstrakcyjna nie dostarcza implementacji w klasie bazowej i musi zostać zaimplementowana w klasie pochodnej.

---
## ARKUSZ INF.04 : 2022 - CZERWIEC - ZAD. 02 Zadanie Notatka
Kod w c#
**ważne: namespace zależy od nazwy projektu!!!!**
```cs
  using System;
  namespace Notatka {
      internal class Notatka {
          private static int liczbaNotatek = 0;
          private int id = 0;
          protected string tytul;
          protected string tresc;

          Notatka(string tytulK, string trescK) {
              liczbaNotatek++;
              this.id = liczbaNotatek;
              tytul = tytulK;
              tresc = trescK;
          }

          public void wyswietl() {
              Console.WriteLine("Tytuł: " + tytul + "\nTreść: " + tresc);
          }
          public void diagnostyka() {
              Console.WriteLine(liczbaNotatek + ";" + id + ";" + tytul + ";" + ";" + tresc);  
          }

          static void Main(string[] args) {
              Notatka notatka1 = new Notatka("test1","tresc1");
              Notatka notatka2 = new Notatka("test2", "tresc2");
              notatka1.wyswietl();
              notatka1.diagnostyka();
              notatka2.wyswietl();
              notatka2.diagnostyka();
              Console.ReadKey();

          }
      }
  }
```
* Tutaj przykładowe zadanie skoncentrowane głównie na klasie, bez części z 3 zadania na egzaminie
**TODO: Dokończ kod z zadaniem 3**
kod C++
```
#include <iostream>

using namespace std;

class Notatka{
    private:
        static int licznik;
        int indentyfikator;
    public:
        string tytul;
        string tresc;

        Notatka(string tytulK, string trescK){
            indentyfikator = ++licznik;
            tytul = tytulK;
            tresc = trescK;
        };
        void Wyswietl(){
            cout<<"Tytul: "<<tytul<<"  Tresc: " << tresc<<endl;
        };
        void Wypisz(){

            cout<<"Licznik: "<<licznik<<"; Identyfikator:"<<indentyfikator<<"; Tytul: "<<tytul<<"; Tresc: "<<tresc<<"; "<<endl;
        };
};
int Notatka::licznik=0;
int main()
{
    cout << "Obsluga Notatek" << endl;
    Notatka notatka1("kutas","dupadupa");
    notatka1.Wyswietl();
    notatka1.Wypisz();
    cout<<endl;
    Notatka notatka2("maciek","tochuj");
    notatka2.Wyswietl();
    notatka2.Wypisz();
    return 0;
}
```
---
# 2. Aplikacje Mobilne
W tej części będzie opis środowiska xamarin oraz parę przykładów kodu z egzaminów zawodowych, nie będę sam dodawał javy/kotlina/flutter, jezeli ktoś chce dodac musi zrobic to na własną rękę

---
#### Krótki opis
Xamarin wygląda prawie tak samo jak WPF jednak rózni się pod paroma względami. Hierachia plików taka sam.
`plik.xaml` - *wygląd aplikacji*
`plik.cs` - *kod aplikacji*

---
#### Rzeczy które na pewno będą
1. W prawie kazdym egzaminie wymagane jest aby uzywac StackLayout, jego działanie jest bardzo proste. Kazdy element zabiera tyle przestrzeni wertykalnej ile potrzebuje, elementy układane są jeden pod drugim.
2. `Entry` - w Xamarinie zamiast TextBlock mamy znacznik Entry. Działanie jest to samo
3. `Label` - Jezeli chcemy dodac zwykły napis w xamarinie uzywamy znacznika Label, jest to ekwiwalent TextBox w WPF
4. `Zdjęcie` - będziemy musieli dodac zdjęcie, jest to bardzo proste wystarczy je dodac do folderu. Szczególny opis dodawania zdjęcia znajdziemy w dalszej części.
5. Operowanie na danych. Ono jest dosłownie takie same jak w WPF, nizej będzie przedstawiony przykład

---


## W tej części będą przydatne snippety

1. `Lista`
```xml
  <ListView x:Name="dupa" SeparatorColor="Crimson" SeparatorVisibility="Default">
      <ListView.Header>
        <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand">
          <Entry Placeholder="Nowy element" HorizontalOptions="FillAndExpand" x:Name="entryDodaj"/>
            <Button Text="DODAJ" x:Name="btnDodaj" BackgroundColor="Crimson" TextColor="White" Clicked="btnDodaj_Clicked"/>
        </StackLayout>
      </ListView.Header>
    <ListView.ItemTemplate>
      <DataTemplate>
        <TextCell TextColor="Black" Text="{Binding}"/>
      </DataTemplate>
    </ListView.ItemTemplate>
  </ListView>
```
#### oraz jej aktualizowanie w cs wraz z domyślnymi elementami
```cs
  List<string> listaZm = new List<string> {
          "weekend: kino, spacer z psem",
          "Do zrobienia: obiad, umyć podłogi",
          "Zakupy: chleb, masło, ser",
  };
  public MainPage() {
      InitializeComponent();
      dupa.ItemsSource = listaZm;
  }

  void btnDodaj_Clicked(System.Object sender, System.EventArgs e) {
      string nowyElement = entryDodaj.Text;
      listaZm.Add(nowyElement); //dodajemy element do listy
      dupa.ItemsSource = null; //refreshujemy liste w xaml (bez tego nie zobaczymy zmian w aplikacji)
      dupa.ItemsSource = listaZm; //ustalamy kontent naszej listy w xaml aby odpiwiadał liscie w c#
      entryDodaj.Text = ""; // resetujemy kontrolke do dodawania tekstu
  }
```
2. `Linia horyzontalna` 
```xml
  <BoxView HorizontalOptions="FillAndExpand" WidthRequest="1" Color="#1690F4"/>
```
3. `Dodawanie zdjęcia`
   Dodawanie zdjęcia w xamarinie jest bardzo proste, wystarczy ze zdjecie które chcemy dodac wstawimy do folderu:
   `Android/Resources/drawable` a następnie w miejscu w którym zdjęcie ma się pokazac dodamy tag:
```xml
  <Image Source="nazwaZdjecia.jpg">
```
Dodatkowo jeżeli chcemy zmenić zdjęcie gdy klikniemy w przycisk kod będzie wyglądał następująco
```xml
  <Image x:Name="myImage" Source="nazwa_poczatkowego_obrazka.png" />
  <Button Text="Zmień obrazek" Clicked="Button_Clicked" />
```

```cs
  private void Button_Clicked(object sender, EventArgs e) {
    // Zmiana źródła obrazka
    myImage.Source = "nowa_nazwa_obrazka.png";
  }
```
A aby zrobić galerię z paroma zdjęciami możemy zrobić tablicę stringów oraz zmienną która określa którą scieżkę z tablicy wybieramy
```cs
  string[] sciezki = {"nowa_nazwa_obrazka1.png," "nowa_nazwa_obrazka2.png3", "nowa_nazwa_obrazka.png"}
  int zdjecieNr = 0;
  private void Button_Clicked(object sender, EventArgs e) {
      if(zdjecieNr < 2) {
          zdjecieNr++;
          myImage.Source = sciezki[zdjecieNr];
      }
      else {
          zdjecieNr = 0;
          myImage.Source = sciezki[zdjecieNr];
      }
  }
```
4. Operowanie na zmiennych
   Załózmy ze mamy w aplikacji kontrolkę label która zlicza ilośc kliknięc w przycisk aby to zrobic nasz kod będzie wyglądał w następujący sposób:
```xml
 <Label x:Name="kontrolka"></Label>
 <Button Text="Kliknij mnie!" x:Name="btnClick" Click="btnClick_Clicked"/>
```
   Następnie w kodzie c#:
```cs
 int iloscKlikniec = 0;
 void btnClick_Clicked(System.Object sender, System.EventArgs e) {
   iloscKlikniec++;
   kontrolka.Text = iloscKlikniec.ToString();
 }
```
   I to tyle, w taki sposób operujemy na danych, analogicznie do potrzebnej sytuacji
5. Dodawanie zegara oraz daty, szanse są raczej małe że się pojawi ale dodam jakby się okazała taka potrzeba
    W pliku MainPage.xaml dodaj kontrolkę Label, która będzie wyświetlać czas:
```xml
  <Label x:Name="dateTimeLabel" HorizontalOptions="Center" VerticalOptions="Center" FontSize="24"/>
```
W pliku MainPage.xaml.cs dodaj kod do aktualizacji etykiety z bieżącą datą i czasem:
```cs
    public MainPage() {
        InitializeComponent();
        Device.StartTimer(TimeSpan.FromSeconds(1), () => {
            Device.BeginInvokeOnMainThread(() => {
                DateTime currentDateTime = DateTime.Now;
                dateTimeLabel.Text = currentDateTime.ToString("dd.MM.yyyy HH:mm:ss");
            });
            return true;
        });
    }
```
---
# 3. Aplikacje Webowe
W tej częsci będzie opis Reacta, jak tworzyc moduły, podstawowe funkcje takie jak useState/Useeffect/Ref/Map i inne przydatne.

---
## Tworzenie projektu i uruchomienie
W terminalu wpisz poniższą komendę, aby zainicjalizować nowy projekt React z TypeScript: `npx create-react-app nazwa-projektu --template typescript`

Przejdź do nowo utworzonego folderu projektu: `cd nazwa-projektu`

W terminalu wpisz poniższą komendę, aby uruchomić projekt: `npm start`

W przegladarce wejdz na strone `localhost:3000`

## Dodawanie komponentow
1. W folderze *src* utwórz nowy folder o nazwie *modules*.
2. Wewnątrz folderu *modules* możesz utworzyć pliki dla poszczególnych komponentów.
3. Utwórz nowy plik .tsx w folderze *modules* dla swojego komponentu, na przykład `dupa.tsx`.
4. W pliku `dupa.tsx` wpisz RFCE i kliknij enter, jezeli kod się nie wygeneruje dodaj **ten**:
```tsx
  import React from 'react'

  function dupa() {
    return (
      <div>dupa</div>
    )
  }

  export default dupa;
```
5. W tym samym folderze utwórz plik `index.ts` a następnie exportuj swój moduł, na powyzyszym przykladzie będzie to wyglądało w następujący sposób:
```ts
  export { default as dupa } from './dupa'
```
6. Teraz możesz zaimportować komponenty z folderu *modules* w innych plikach. Na przykład, jeśli masz plik `App.tsx` w folderze *src*, możesz zaimplementować importowanie komponentu:  
```tsx
  import dupa from './dupa'
```
Ostatecznie aby komponent wyświetlił się na stronie musisz dodac zwykły *tag* w pkiku `App.tsx`, w tym wypadku będzie to:
```tsx
  <dupa/>
```
---
## Wytłumaczenie podstawowych funkcji
#### useState
`useState` jest funkcją używaną w React z TypeScript (TS) do zarządzania stanem *komponentów funkcyjnych*. Pozwala to na przechowywanie danych wewnątrz komponentu i reagowanie na ich zmiany.<br>
`useState` to **hook**, który pozwala zadeklarować zmienną stanu wewnątrz komponentu. Przyjmuje on początkową wartość stanu i zwraca parę: aktualną wartość stanu oraz funkcję, która pozwala na zmianę wartości stanu.

Oto przykład użycia useState:
```tsx
  import React, { useState } from 'react';

  const MyComponent: React.FC = () => {
    const [count, setCount] = useState(0);

    const incrementCount = () => {
      setCount(count + 1);
    };

    return (
      <div>
        <p>Count: {count}</p>
        <button onClick={incrementCount}>Increment</button>
      </div>
    );
  };

  export default MyComponent;
```
W powyższym przykładzie używamy `useState` do zadeklarowania zmiennej stanu count oraz funkcji `setCount`, która pozwala na zmianę wartości `count`. Początkowo ustawiamy `count` na 0.
Wewnątrz komponentu możemy użyć zmiennej count, aby wyświetlać aktualną wartość stanu. W przypadku przycisku *Increment* wywołujemy funkcję `incrementCount`, która zwiększa wartość `count` o 1, korzystając z `setCount`.

Każde użycie `setCount` powoduje ponowne renderowanie komponentu z nową wartością stanu, co oznacza aktualizację widoku na podstawie nowych danych.

Ważne jest, aby pamiętać, że `useState` może być używane wielokrotnie wewnątrz komponentu, aby zarządzać różnymi zmiennymi stanu.

Podsumowując, `useState` jest *hookiem* w React z TypeScript, który pozwala na deklarację i aktualizację zmiennych stanu wewnątrz komponentu funkcyjnego. Używając `useStat`e, możemy reagować na zmiany stanu i aktualizować widok komponentu.
##### Tak ten jak i następne opisy zostały wygenerowane przez chatGPT, nie chce mi się samemu tego pisac

`useEffect`

##### Notka: Tego na egzaminie raczej nie będzie więc jak ktoś chce to moze pominąc tą częśc

Metoda `useEffect` jest *hookiem* w React z TypeScript (TS), który pozwala na wykonywanie efektów `ubocznych (side effects)` w komponencie funkcyjnym. Efekty uboczne to akcje, które są wykonywane po renderowaniu komponentu, takie jak pobieranie danych z serwera, subskrypcje zdarzeń, manipulacja DOM itp.

Głównym celem `useEffect` jest umożliwienie interakcji z zewnętrznymi zasobami lub zachowań, które nie są bezpośrednio związane z renderowaniem komponentu.

Oto przykład użycia `useEffect`:
```tsx
  import React, { useState, useEffect } from 'react';

  const Timer: React.FC = () => {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
      const interval = setInterval(() => {
        setSeconds(prevSeconds => prevSeconds + 1);
      }, 1000);

      return () => {
        clearInterval(interval);
      };
    }, []);

    return (
      <div>
        <p>Seconds: {seconds}</p>
      </div>
    );
  };

  export default Timer;

```
W tym przykładzie useEffect jest używany do utworzenia prostego licznika sekund. Po pierwszym renderowaniu komponentu, efekt uboczny jest uruchamiany, tworząc interwał, który co sekundę zwiększa wartość zmiennej seconds o 1.

Funkcja przekazana do useEffect jako pierwszy argument jest wywoływana po renderowaniu komponentu. Tworzymy interwał za pomocą setInterval, który zwiększa wartość seconds i wywołuje funkcję setSeconds w każdej sekundzie.

Pusta tablica zależności ([]) przekazana jako drugi argument do useEffect oznacza, że efekt zostanie wykonany tylko raz po pierwszym renderowaniu komponentu. W tym przypadku nie mamy żadnych zależności, które powodowałyby ponowne wykonanie efektu.

Dodatkowo, wewnątrz funkcji przekazanej do useEffect, zwracamy funkcję czyszczącą (clearInterval(interval)), która jest wywoływana przed usunięciem komponentu. Dzięki temu interwał zostanie zatrzymany i nie będzie działał po usunięciu komponentu.

Podsumowując, useEffect pozwala na wykonywanie efektów ubocznych w komponencie funkcyjnym. W tym prostszym przykładzie używamy go do tworzenia prostego licznika sekund, ale może być również używany do innych celów, takich jak pobieranie danych z serwera, subskrypcje zdarzeń, manipulacja DOM itp.

#### useRef
`useRef()` przyjmuje wartość i jest używany do stworzenia *adresu*, do którego możemy przypisać znacznik HTML.

Komponent używający useRef:


```jsx
  // Aby używać hook'ów należy je zaimportować
  import { useRef } from 'react';

  function Licznik() {
      // buttonRef to jakiś pusty adres
      const buttonRef = useRef(0);

      // Po przypisaniu buttonRef to adres danego przycisku
      // Natomiast buttonRef.current to w tym przypadku przycisk
      return (
        <div>
            <button ref={buttonRef}>Kliknij</button>
        </div>
      );
  }
```

##### Obsługa inputów

Wyróżniamy dwa, różne sposoby na obsługiwanie inputów:

1. Używając `useRef()`
2. Używajac `useState()`

Różnią się tym, że używając `useState()` możemy programatycznie zmieniać wartość inputa, a `używając useRef()` możemy tą wartość programatycznie jedynie odczytać

useRef:
```jsx
  import { useRef } from 'react';
  function App() {
    const inputRef = useRef(0);

    // W ten sposób możemy odczytać wartość inputa używając inputRef.current.value
    return <input ref={inputRef}>
  }
  export default App;
```

useState:
```jsx
  import { useState } from 'react';
  function App() {
    const [tekst, setTekst] = useState('');

    /* W ten sposób możemy:
      1. odczytać wartość inputa używając zmiennej tekst
      2. nadpisać wartość inputa używając funkcji setTekst
    */
    return <input value={tekst} onChange={(e) => setTekst(e.target.value)}>
  }
  export default App;
```

##### map

Gdy nasze dane znajdują się w tablicy możemy je wypisać używając metody `.map()`. Daje nam to możliwość generowania znaczników HTML jakbyśmy to robili używając pętli. Jeśli elementy mają być wypisane w liście należy użyć ul, bądź ol zależnie od polecenia

```jsx
  const tablica = ['a', 'b', 'c'];

  // Wypełniamy znacznik <ol> danymi z tablicy
  <ol>
      { tablica.map(element => (<li key={element}>{element}</li>)) }
  </ol>;
```
**W ten sposób w naszym `<ol>` stworzymy 3 znaczniki `<li>`:**
```html
  <li key="a">a</li>
  <li key="b">b</li>
  <li key="c">c</li>
```
---

#### Aplikacja Webowa z egzaminu

App.js
```jsx
  import "./App.css";
  import { useState } from "react"; // Importujemy useState

  function App() {
    const kursy = [
      "Programowanie w C#",
      "Angular dla początkujących",
      "Kurs Django",
    ]; // Tablica zawierająca 3 kursy

    const [imie, setImie] = useState(""); // State do inputu z imieniem
    const [kurs, setKurs] = useState(); // State do inputu z numerem kursu

    function handleSubmit(e) {
      // Funkcja wywołana po wysłaniu formularza
      e.preventDefault(); // Blokujemy odświeżenie strony po przesłaniu formularza

      console.log(imie);
      if (kursy[kurs - 1]) {
        console.log(kursy[kurs - 1]);
      } else {
        console.log("Nieprawidłowy numer kursu");
      }
    }

    return (
      <div className="App">
        <h2>Liczba kursów {kursy.length}</h2> {/* Wypisujemy listę kursów */}
        <ol>
          {kursy.map((kurs) => (
            <li key={kurs}>{kurs}</li> // Wypisanie elementów tablicy "kursy" za pomocą metody .map()
          ))}
        </ol>
        <form onSubmit={handleSubmit}>
          {" "}
          {/* Formularz, który po przesłaniu wywołuje funkcję handleSubmit() */}
          <div className="form-group">
            <label htmlFor="imieInput">Imię i nazwisko:</label>
            <input
              type="text"
              className="form-control"
              id="imieInput"
              value={imie} // Przypisanie state "imie" do wartosci inputu
              onChange={(e) => setImie(e.target.value)} // Zmiana wartości state "imie"
            />
          </div>
          <div className="form-group">
            <label htmlFor="kursInput">Numer kursu:</label>
            <input
              type="text"
              className="form-control"
              id="kursInput"
              value={kurs} // Przypisanie state "kurs" do wartości inputu
              onChange={(e) => setKurs(e.target.value)} // Zmiana wartości state "kurs"
            />
          </div>
          <button className="btn btn-primary">Zapisz do kursu</button>
        </form>
      </div>
    );
  }

  export default App;
```

App.css
```css
  .App {
    width: 60%; /* Ustawienie szerokości aplikacji na 60% body*/
    margin: 0 auto; /* Wyśrodkowanie aplikacji */
  }
```
