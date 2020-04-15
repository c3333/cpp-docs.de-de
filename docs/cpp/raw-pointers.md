---
title: Rohzeiger (C++)
description: Verwenden von Rohzeigern in C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374668"
---
# <a name="raw-pointers-c"></a>Rohzeiger (C++)

Ein Zeiger ist ein Typ von Variablen, der die Adresse eines Objekts im Speicher speichert und für den Zugriff auf dieses Objekt verwendet wird. Ein *unformatierter Zeiger* ist ein Zeiger, dessen Lebensdauer nicht von einem kapselnden Objekt wie einem [intelligenten Zeiger](smart-pointers-modern-cpp.md)gesteuert wird. Einem Unformatzeiger kann die Adresse einer anderen Nichtzeigervariablen zugewiesen werden, oder ihm kann ein Wert von [nullptr](nullptr.md)zugewiesen werden. Ein Zeiger, dem kein Wert zugewiesen wurde, enthält zufällige Daten.

Ein Zeiger kann auch *dereferenziert* werden, um den Wert des Objekts abzurufen, auf das er zeigt. Der *Memberzugriffsoperator* bietet Zugriff auf die Member eines Objekts.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Ein Zeiger kann auf ein typisiertes Objekt oder auf **void**zeigen. Wenn ein Programm ein neues Objekt auf dem [Heap](https://wikipedia.org/wiki/Heap) im Speicher zuweist, empfängt es die Adresse dieses Objekts in Form eines Zeigers. Solche Zeiger werden als *eigene Zeiger*bezeichnet; Ein eigener Zeiger (oder eine Kopie davon) muss verwendet werden, um das heap-zugeordnete Objekt explizit zu löschen, wenn es nicht mehr benötigt wird. Wenn der Speicher nicht gelöscht wird, führt dies zu einem *Speicherverlust* und macht diesen Speicherort für kein anderes Programm auf dem Computer verfügbar. Weitere Informationen finden Sie unter Neue und Löschen von [Operatoren](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Ein Zeiger (wenn er nicht als **const**deklariert ist) kann so inkrementiert oder dekrementiert werden, dass er auf eine neue Position im Speicher verweist. Dies wird *Zeigerarithmetik* genannt und wird in der C-Stil-Programmierung verwendet, um Elemente in Arrays oder anderen Datenstrukturen zu iterieren. Ein **const-Zeiger** kann nicht auf eine andere Speicherposition zeigen und ist in diesem Sinne einem [Verweis](references-cpp.md)sehr ähnlich. Weitere Informationen finden Sie unter [const- und volatile Pointer](const-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c;
    // pconst2 = &c2; // Error! pconst2 is const.
```

Bei 64-Bit-Betriebssystemen hat ein Zeiger eine Größe von 64 Bit; Die Zeigergröße eines Systems bestimmt, wie viel adressierbarer Speicher es haben kann. Alle Kopien eines Zeigers verweisen auf dieselbe Speicherposition. Zeiger (zusammen mit Referenzen) werden in C++ ausgiebig verwendet, um größere Objekte an und von Funktionen zu übergeben, da es in der Regel viel effizienter ist, die 64-Bit-Adresse eines Objekts zu kopieren, als ein gesamtes Objekt zu kopieren. Geben Sie beim Definieren einer Funktion Zeigerparameter als **const** an, es sei denn, Sie beabsichtigen, dass die Funktion das Objekt ändert. Im Allgemeinen sind **const-Referenzen** die bevorzugte Methode, Objekte an Funktionen zu übergeben, es sei denn, der Wert des Objekts kann möglicherweise **nullptr**sein.

[Zeiger auf Funktionen](#pointers_to_functions) ermöglichen die Weitergabe von Funktionen an andere Funktionen und werden für "Rückrufe" in der C-Programmierung verwendet. Moderne S++ verwendet zu diesem Zweck [Lambda-Ausdrücke.](lambda-expressions-in-cpp.md)

## <a name="initialization-and-member-access"></a>Initialisierung und Memberzugriff

Das folgende Beispiel zeigt, wie Sie einen Unformatzeiger deklarieren und mit einem auf dem Heap zugewiesenen Objekt initialisieren und ihn dann verwenden. Es zeigt auch einige der Gefahren, die mit rohen Zeigern verbunden sind. (Denken Sie daran, dies ist C-Stil Programmierung und nicht moderne C++!)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Zeigerarithmetik und Arrays

Zeiger und Arrays sind eng miteinander verknüpft. Wenn ein Array neben Wert an eine Funktion übergeben wird, wird es als Zeiger an das erste Element übergeben. Im folgenden Beispiel werden die folgenden wichtigen Eigenschaften von Zeigern und Arrays veranschaulicht:

- Der `sizeof` Operator gibt die Gesamtgröße in Bytes eines Arrays zurück
- Um die Anzahl der Elemente zu bestimmen, dividieren Sie die Gesamtzahl der Bytes durch die Größe eines Elements
- Wenn ein Array an eine Funktion übergeben wird, *zerfällt* es zu einem Zeigertyp
- Der `sizeof` Operator, wenn er auf einen Zeiger angewendet wird, gibt die Zeigergröße zurück, 4 Bytes auf x86 oder 8 Bytes auf x64

```cpp
#include <iostream>

void func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

Bestimmte arithmetische Operationen können für Nicht-Const-Zeiger ausgeführt werden, damit sie auf eine neue Speicherposition verweisen. Ein Zeiger kann mit **++** den Operatoren , **+=** **-=** und **--** Operatoren erhöht und dekrementiert werden. Diese Technik kann in Arrays verwendet werden und ist besonders nützlich in Puffern von nicht typisierten Daten. Ein **\* Leerzeichen** erhöht sich um die Größe eines **Zeichens** (1 Byte). Ein typisierter Zeiger erhöht sich nach Größe des Typs, auf den er zeigt.

Im folgenden Beispiel wird veranschaulicht, wie Zeigerarithmetik verwendet werden kann, um auf einzelne Pixel in einer Bitmap unter Windows zuzugreifen. Beachten Sie die Verwendung von **new** und **delete**und des Dereferenzierungsoperators.

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>void*-Zeiger

Ein Zeiger auf **void** zeigt einfach auf eine unformatierte Speicherposition. Manchmal ist es notwendig, **leere\* ** Zeiger zu verwenden, z. B. beim Übergeben zwischen C++-Code und C-Funktionen.

Wenn ein typisierter Zeiger in einen Leerenzeiger geworfen wird, wird der Inhalt des Speicherspeicherorts nicht geändert, aber die Typinformationen gehen verloren, sodass Sie keine Inkrementierungs- oder Dekrementvorgänge ausführen können. Ein Speicherspeicherort kann z. B. von MyClass* in void* und wieder zurück zu MyClass* gecastet werden. Solche Operationen sind von Natur aus fehleranfällig und erfordern große Sorgfalt, um Fehler zu vermeiden. Moderne s++ rät von der Verwendung von Leerzeichen ab, es sei denn, dies ist unbedingt erforderlich.

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Zeiger auf Funktionen

In der Programmierung im C-Stil werden Funktionszeiger in erster Linie verwendet, um Funktionen an andere Funktionen zu übergeben. In diesem Szenario kann der Aufrufer das Verhalten einer Funktion anpassen, ohne sie zu ändern. In modernen C++ bieten [Lambda-Ausdrücke](lambda-expressions-in-cpp.md) die gleiche Fähigkeit mit größerer Typsicherheit und anderen Vorteilen.

Eine Funktionszeigerdeklaration gibt die Signatur an, die die point-to-Funktion haben muss:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

Das folgende Beispiel `combine` zeigt eine Funktion, die als `std::string` Parameter `std::string`jede Funktion verwendet, die eine akzeptiert und eine zurückgibt. Abhängig von der Funktion, `combine` die an sie übergeben wird, wird eine Zeichenfolge entweder vorangestellt oder angehängt.

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>Siehe auch

[Intelligente Zeiger](smart-pointers-modern-cpp.md)
[Indirection Operator: *](indirection-operator-star.md)<br/>
[address-of-Operator](address-of-operator-amp.md)</br>
[Willkommen zurück bei C++](welcome-back-to-cpp-modern-cpp.md)
