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
```C#
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
```C#
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
```C#
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
```c#
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
```c#
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
#### b) W tej części opisane będzie działanie klas, jak je napisac, czym są instancje, hermetyzacja itp.
---