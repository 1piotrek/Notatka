# Egzamin zawodowy inf.04
---
## Rozdziały:
1. Konsolowe
   * Algorytmy
   * Klasy 
2. Mobilne
3. Webowe
4. Desktopowe
___
# 1.
#### a) W tej części opisane będą algorytmy które wystąpiły juz w poprzednich egzaminach oraz te które mogą wystąpic
---
##Generowanie liczb losowych
##### Kod w C++
```c++
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
```c++
void selection_sort(int tab[],int n) //n - ilość elementów do posortowania
{
int mn_index; //zmienna pomocnicza przechowująca indeks komórki 
        //z minimalną wartością
  for(int i=0;i<n-1;i++)
  {
  	mn_index = i;
    for(int j=i+1;j<n;j++) //pętla wyszukuje najmniejszy element w podzbiorze nieposortowanym
    if(tab[j]<tab[mn_index])
      mn_index = j;
 
    //zamiana elementu najmniejszego w podzbiorze z pierwszą pozycją nieposortowaną
	swap(tab[i], tab[mn_index]);
  }
} 
```
* kod jest z komentarzami, więc nie powinno byc problemu w razie co aby go przerobic pod egzamin
##### Kod C#
```cs
        static int[] InsertionSort(int[] inputArray)
        {
            for (int i = 0; i < inputArray.Length - 1; i++)
            {
                for (int j = i + 1; j > 0; j--)
                {
                    if (inputArray[j - 1] > inputArray[j])
                    {
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
## Inf 04 2022 Czerwiec Przeszukiwanie z wartownikiem

Opis tego algorytmu równiez jest na egzaminie, jest on tam dobrze wytłumaczony

#### Kod w C++
```c++
//przeszukanie tablicy
    while(tab[i]!=szukana && tab[i]!=-1) ++i;
    //koniec wyszukiwania
    
    //jeśli zatrzymaliśmy się na wartowniku, to oznacza, 
   //że szukana liczba nie występuje w zbiorze    
    if(tab[i] == -1) 
       cout<<"Szukany element nie występuje w tablicy"<<endl;
    else
       cout<<"Liczba "<<szukana<<" znajduje się na pozycji "<<i+1<<endl;
    
```
#### Kod w C#
```cs
//szukaj elementu x
a[n] = x;
i = 0;
while (a[i] != x)
{
   i++;
}
//podaj wynik
if (i == n)
Console.WriteLine("Nie znaleziono w tablicy elementu " + x);
else
Console.WriteLine("Odnaleziono element " + x + " pod indeksem " + i);
```
---
## Inf 04 2023 Styczen NWD
No tutaj jest nwd nic skomplikowanego

#### Kod C++
```c++
int NWD(int a, int b)
{
    while(a!=b)
       if(a>b)
           a-=b; //lub a = a - b;
       else
           b-=a; //lub b = b-a
    return a; // lub b - obie zmienne przechowują wynik NWD(a,b)
}
```
* Kodu w C# nie zamieszczam bo to jest to samo co c++

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
```c++
long long tab[1000000]; //tablica z posortowanymi elementami

//l - lewy index tablicy, p - prawy index tablicy
int szukaj(int l, int p, long szukana) 
{
	int sr;
	while(l<=p)
	{
		sr = (l + p)/2;
		
		if(tab[sr] == szukana)
			return sr;
			
		if(tab[sr] > szukana)
			p = sr - 1;
		else
			l = sr + 1;
}

	return -1; //zwracamy -1, gdy nie znajdziemy elementu
}
```

#### Kod C#
```cs
public static object BinarySearchIterative(int[] inputArray, int key)  
{ 
  int min = 0;
  int max = inputArray.Length - 1; 
    while (min <=max)  
    {  
       int mid = (min + max) / 2;  
       if (key == inputArray[mid])  
       {  
            return ++mid;  
       }  
       else if (key < inputArray[mid])  
       {  
           max = mid - 1;  
       }  
       else  
       {  
            min = mid + 1;  
       }  
   }  
   return "Nil";  
}  
```
---
## Sortowanie bąbelkowe
Chyba wszystkim znany algorytm sortowania więc opis jest zbędny.
#### Kod C++
```c++
void sortowanie_babelkowe(int tab[],int n)
{
	for(int i=0;i<n;i++)
		for(int j=1;j<n-i;j++) //pętla wewnętrzna
		if(tab[j-1]>tab[j])
			//zamiana miejscami
			swap(tab[j-1], tab[j]);
}
```
#### Kod C#
```cs
   static void BubbleSort(int[] arr)
   {
      int n = arr.Length;

      for (int i = 0; i < n - 1; i++)
         for (int j = 0; j < n - i - 1; j++)
	    if (arr[j] > arr[j + 1])
	    {
	        int temp = arr[j];
		arr[j] = arr[j + 1];
		arr[j + 1] = temp;
	    }
   }
```
---
## Sortowanie szybkie
Szczerze mówiąc, opis jest spory, więc nie zamieszczę go teraz, jezeli trafi się na egzaminie to pewnie tam się on znajdzie. Algorytm jest szybki i to tyle wystarczy.
#### Kod w c++
```c++
void quick_sort(int *tab, int lewy, int prawy)
{
	if(prawy <= lewy) return;
	
	int i = lewy - 1, j = prawy + 1, 
	pivot = tab[(lewy+prawy)/2]; //wybieramy punkt odniesienia
	
	while(1)
	{
		//szukam elementu wiekszego lub rownego piwot stojacego
		//po prawej stronie wartosci pivot
		while(pivot>tab[++i]);
		
		//szukam elementu mniejszego lub rownego pivot stojacego
		//po lewej stronie wartosci pivot
		while(pivot<tab[--j]);
		
		//jesli liczniki sie nie minely to zamień elementy ze soba
		//stojace po niewlasciwej stronie elementu pivot
		if( i <= j)
			//funkcja swap zamienia wartosciami tab[i] z tab[j]
			swap(tab[i],tab[j]);
		else
			break;
	}

	if(j > lewy)
	quick_sort(tab, lewy, j);
	if(i < prawy)
	quick_sort(tab, i, prawy);
}
```
#### Kod w C#
```cs
public int[] SortArray(int[] array, int leftIndex, int rightIndex)
{
    var i = leftIndex;
    var j = rightIndex;
    var pivot = array[leftIndex];

    while (i <= j)
    {
        while (array[i] < pivot)
        {
            i++;
        }
        
        while (array[j] > pivot)
        {
            j--;
        }

        if (i <= j)
        {
            int temp = array[i];
            array[i] = array[j];
            array[j] = temp;
            i++;
            j--;
        }
    }
    
    if (leftIndex < j)
        SortArray(array, leftIndex, j);

    if (i < rightIndex)
        SortArray(array, i, rightIndex);

    return array;
}
```
# TODO: jakieś inne algorytmy
---
## Klasy
Przypomnienie jak działają klasy, na czym polega hermetyzacja, dzedziczenie, instancje itp.

---
## Tworzenie klas, instancji, konstruktory, metody

```c++
//c++
class Osoba
{
public:
    int wiek;
    int wzrost;
private: 
    int nrKartyKredytowej;
    
public: 
    Osoba()
    {
        ...
        //Konstruktor bezparametrowy
    }
    Osoba(int wiekK, int wzrostK, int kartaK)
    {
        this.wiek = wiekK;
        this.wzrost = wzrostK;
        this.nrKartyKredytowej = kartaK;
        //Konstruktor z parametrami
    }
};

//Utworzenie instacji
Osoba nazwainstancji;
```
* TODO: dodaj ktoś konstruktor kopiujący/wirtualny w c++ bo mi się nie chce i nie wiem jak to działa w tym języku
```cs
//C#
public class Osoba
{
    static public int wiek;
    static public int wzrost;
    static private int nrKartyKredytowej;
    //W c# zamiast konstruktorów mozna uzyc setterów
    //public int wiek {get; set;}
    //Jest to ekwiwalent
    //Osoba(int wiekK) {this.wiek = wiekK}
    Osoba()
    {
        ...
        //Konstruktor bezparametrowy
    }

    Osoba(int wiekK, int wzrostK, int kartaK)
    {
        this.wiek = wiekK;
        this.wzrost = wzrostK;
        this.nrKartyKredytowej = kartaK;
        //Konstruktor z parametrami
    }

    Osoba(Osoba poprzedniaOsoba)
    {
        this.wiek = poprzedniaOsoba.wiek;
        this.wzrost = poprzedniaOsoba.wzrost;
        this.nrKartyKredytowej = poprzedniaOsoba.nrKartyKredytowej
        //Konstruktor kopiujący
    }

    public void Metoda()
    {
        //tutaj kod metody
    }
    public void MetodaZWielomaParametrami(params int[] values)
    {
    int sum = 0;
    foreach (int value in values)
    {
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
operator_widoczności może przyjmować jedną z trzech wartości: public, protected, private. Operator widoczności przy klasie, z której dziedziczymy pozwala ograniczyć widoczność elementów publicznych z klasy bazowej.
1. public - oznacza, że dziedziczone elementy (np. zmienne lub funkcje) mają taką widoczność jak w klasie bazowej.
2. protected - oznacza, że elementy publiczne zmieniają się w chronione.
3. private - oznacza, że wszystkie elementy klasy bazowej zmieniają się w prywatne.
4. brak operatora - oznacza, że niejawnie (domyślnie) zostanie wybrany operator private.

W c++ schemat wygląda następująco:
```c++
   class nazwa_klasy :[operator_widocznosci] nazwa_klasy_bazowej, [operator_widocznosci] nazwa_klasy_bazowej ...
   {
        definicja_klasy
   };

   //przykład

   class Nastolatek : private Osoba
   {
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
```cs
using System;

namespace Notatka // Note: actual namespace depends on the project name.
{
    internal class Notatka
    {
        private static int liczbaNotatek = 0;
        private int id = 0;
        protected string tytul;
        protected string tresc;

        Notatka(string tytulK, string trescK)
        {
            liczbaNotatek++;
            this.id = liczbaNotatek;
            tytul = tytulK;
            tresc = trescK;
        }

        public void wyswietl()
        {
            Console.WriteLine("Tytuł: " + tytul + "\nTreść: " + tresc);
        }
        public void diagnostyka()
        {
            Console.WriteLine(liczbaNotatek + ";" + id + ";" + tytul + ";" + ";" + tresc);  
        }

        static void Main(string[] args)
        {
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
## TODO: Dokończ kod z zadaniem 3
### TODO: Zrób ktoś kod z c++
---
# 2. Aplikacje Mobilne
W tej części będzie opis środowiska xamarin oraz parę przykładów kodu z egzaminów zawodowych, nie będę sam dodawał javy/kotlina/flutter, jezeli ktoś chce dodac musi zrobic to na własną rękę

---
#### Krótki opis
Xamarin wygląda prawie tak samo jak WPF jednak rózni się pod paroma względami. Hierachia plików taka sam.
plik.xaml - wygląd aplikacji
plik.cs - kod aplikacji

---
#### Rzeczy które na pewno będą
1. W prawie kazdym egzaminie wymagane jest aby uzywac StackLayout, jego działanie jest bardzo proste. Kazdy element zabiera tyle przestrzeni wertykalnej ile potrzebuje, elementy układane są jeden pod drugim.
2. Entry - w Xamarinie zamiast TextBlock mamy znacznik Entry. Działanie jest to samo
3. Label - Jezeli chcemy dodac zwykły napis w xamarinie uzywamy znacznika Label, jest to ekwiwalent TextBox w WPF
4. Zdjęcie - będziemy musieli dodac zdjęcie, jest to bardzo proste wystarczy je dodac do folderu. Szczególny opis dodawania zdjęcia znajdziemy w dalszej części.
5. Operowanie na danych. Ono jest dosłownie takie same jak w WPF, nizej będzie przedstawiony przykład

---


## W tej części będą przydatne snippety

1. Lista
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
    oraz jej aktualizowanie w cs wraz z domyślnymi elementami
    ```cs
        List<string> listaZm = new List<string>
        {
                "weekend: kino, spacer z psem",
                "Do zrobienia: obiad, umyć podłogi",
                "Zakupy: chleb, masło, ser",
        };
        public MainPage()
        {
            InitializeComponent();

            dupa.ItemsSource = listaZm;
            
        }

        void btnDodaj_Clicked(System.Object sender, System.EventArgs e)
        {
            string nowyElement = entryDodaj.Text;
            listaZm.Add(nowyElement); //dodajemy element do listy
            dupa.ItemsSource = null; //refreshujemy liste w xaml (bez tego nie zobaczymy zmian w aplikacji)
            dupa.ItemsSource = listaZm; //ustalamy kontent naszej listy w xaml aby odpiwiadał liscie w c#
            entryDodaj.Text = ""; // resetujemy kontrolke do dodawania tekstu
        }
    ```
2. Linia horyzontalna 
    ```xml
      <BoxView HorizontalOptions="FillAndExpand" WidthRequest="1" Color="#1690F4"/>
    ```
3. Dodawanie zdjęcia
   Dodawanie zdjęcia w xamarinie jest bardzo proste, wystarczy ze zdjecie które chcemy dodac wstawimy do folderu:
   Android/Resources/drawable
     a następnie w miejscu w którym zdjęcie ma się pokazac dodamy tag:
    ```xml
    <Image Source="nazwaZdjecia.jpg">
    ```
    Dodatkowo jeżeli chcemy zmenić zdjęcie gdy klikniemy w przycisk kod będzie wyglądał następująco
    ```xml
    <Image x:Name="myImage" Source="nazwa_poczatkowego_obrazka.png" />
    <Button Text="Zmień obrazek" Clicked="Button_Clicked" />
    ```

    ```cs
    private void Button_Clicked(object sender, EventArgs e)
    {
        // Zmiana źródła obrazka
        myImage.Source = "nowa_nazwa_obrazka.png";
    }
    ```
    A aby zrobić galerię z paroma zdjęciami możemy zrobić tablicę stringów oraz zmienną która określa którą scieżkę z tablicy wybieramy
    ```cs
    string[] sciezki = {"nowa_nazwa_obrazka1.png," "nowa_nazwa_obrazka2.png3", "nowa_nazwa_obrazka.png"}
    int zdjecieNr = 0;
    private void Button_Clicked(object sender, EventArgs e)
    {
        if(zdjecieNr < 2)
        {
            zdjecieNr++;
            myImage.Source = sciezki[zdjecieNr];
        }
        else
        {
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
   void btnClick_Clicked(System.Object sender, System.EventArgs e)
   {
        iloscKlikniec++;
        kontrolka.Text = iloscKlikniec.ToString();
   }
   ```
   I to tyle, w taki sposób operujemy na danych, analogicznie do potrzebnej sytuacji
