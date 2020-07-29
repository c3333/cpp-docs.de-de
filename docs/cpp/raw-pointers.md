---
title: Rohzeiger (C++)
description: Verwenden von unformatierten Zeigern in C++
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- ':::no-loc(void):::'
- ':::no-loc(nullptr):::'
- ':::no-loc(const):::'
- ':::no-loc(char):::'
- ':::no-loc(new):::'
- ':::no-loc(delete):::'
ms.openlocfilehash: 53679559888191fe7f2aad7cb5a70d607974ae96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233651"
---
# <a name="raw-pointers-c"></a>Rohzeiger (C++)

Ein *Zeiger* ist ein Variablentyp. Er speichert die Adresse eines Objekts im Arbeitsspeicher und wird für den Zugriff auf das Objekt verwendet. Ein unformatierter *Zeiger* ist ein Zeiger, dessen Lebensdauer nicht durch ein kapselnde Objekt, z. b. einen [intelligenten Zeiger](smart-pointers-modern-cpp.md), gesteuert wird. Einem unformatierten Zeiger kann die Adresse einer anderen nicht-Zeiger Variablen zugewiesen werden, oder ihm kann der Wert zugewiesen werden [:::no-loc(nullptr):::](:::no-loc(nullptr):::.md) . Ein Zeiger, dem kein Wert zugewiesen wurde, enthält zufällige Daten.

Ein Zeiger kann auch *dereferenziert* werden, um den Wert des Objekts abzurufen, auf das er verweist. Der *Member Access-Operator* ermöglicht den Zugriff auf die Member eines Objekts.

```cpp
    int* p = :::no-loc(nullptr):::; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

Ein Zeiger kann auf ein typisiertes Objekt oder auf verweisen **`:::no-loc(void):::`** . Wenn ein Programm im Arbeitsspeicher ein Objekt auf dem [Heap](https://wikipedia.org/wiki/Heap) belegt, empfängt es die Adresse des Objekts in Form eines Zeigers. Solche Zeiger werden als *besitzende Zeiger*bezeichnet. Ein Besitz ender Zeiger (oder eine Kopie davon) muss verwendet werden, um das vom Heap zugeordnete Objekt explizit freizugeben, wenn es nicht mehr benötigt wird. Wenn Sie den Arbeitsspeicher nicht freigeben, führt dies zu einem Arbeits *Speicherverluste*, und rendert diesen Speicher Speicherort für ein anderes Programm auf dem Computer nicht verfügbar. Der mit zugeordnete Arbeitsspeicher **`:::no-loc(new):::`** muss mithilfe von **`:::no-loc(delete):::`** (oder ** :::no-loc(delete)::: \[ ]**) freigegeben werden. Weitere Informationen finden Sie unter [ :::no-loc(new)::: und- :::no-loc(delete)::: Operatoren](:::no-loc(new):::-and-:::no-loc(delete):::-operators.md).

```cpp
    MyClass* mc = :::no-loc(new)::: MyClass(); // allocate object on the heap
    mc->print(); // access class member
    :::no-loc(delete)::: mc; // :::no-loc(delete)::: object (please don't forget!)
```

Ein Zeiger (wenn er nicht als deklariert ist **`:::no-loc(const):::`** ) kann erhöht oder dekrementiert werden, um auf einen anderen Speicherort im Arbeitsspeicher zu verweisen. Dieser Vorgang wird als *Zeigerarithmetik*bezeichnet. Sie wird bei der Programmierung im C-Stil verwendet, um Elemente in Arrays oder anderen Datenstrukturen zu durchlaufen. Ein **`:::no-loc(const):::`** Zeiger kann nicht erstellt werden, um auf einen anderen Speicherort zu verweisen, und ist in diesem Sinn vergleichbar mit einem [Verweis](references-cpp.md). Weitere Informationen finden Sie unter [ :::no-loc(const)::: und volatile-Zeiger](:::no-loc(const):::-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    :::no-loc(const)::: :::no-loc(char):::* str = "Hello world";

    :::no-loc(const)::: int c = 1;
    :::no-loc(const)::: int* p:::no-loc(const)::: = &c; // declare a non-:::no-loc(const)::: pointer to :::no-loc(const)::: int
    :::no-loc(const)::: int c2 = 2;
    p:::no-loc(const)::: = &c2;  // OK p:::no-loc(const)::: itself isn't :::no-loc(const):::
    :::no-loc(const)::: int* :::no-loc(const)::: p:::no-loc(const):::2 = &c;
    // p:::no-loc(const):::2 = &c2; // Error! p:::no-loc(const):::2 is :::no-loc(const):::.
```

Bei 64-Bit-Betriebssystemen hat ein Zeiger eine Größe von 64 Bits. Die Zeiger Größe eines Systems bestimmt, wie viel Adressier barer Arbeitsspeicher aufweisen kann. Alle Kopien eines Zeigers zeigen auf denselben Speicherort. Zeiger (zusammen mit verweisen) werden in C++ ausgiebig verwendet, um größere Objekte an und von Funktionen zu übergeben. Das liegt daran, dass es oft effizienter ist, die Adresse eines Objekts zu kopieren, als das gesamte Objekt zu kopieren. Legen Sie beim Definieren einer Funktion Zeiger Parameter als fest, **`:::no-loc(const):::`** Wenn Sie nicht beabsichtigen, das Objekt zu ändern. Im allgemeinen **`:::no-loc(const):::`** sind Verweise die bevorzugte Methode, um Objekte an Funktionen zu übergeben, es sei denn, der Wert des Objekts kann sein **`:::no-loc(nullptr):::`** .

[Zeiger auf Funktionen](#pointers_to_functions) ermöglichen das Übertragen von Funktionen an andere Funktionen und werden für "Rückrufe" bei der Programmierung im C-Format verwendet. Modern C++ verwendet für diesen Zweck [Lambda-Ausdrücke](lambda-expressions-in-cpp.md) .

## <a name="initialization-and-member-access"></a>Initialisierung und Element Zugriff

Im folgenden Beispiel wird gezeigt, wie ein rohzeiger deklariert, initialisiert und verwendet wird. Sie wird mithilfe von initialisiert **`:::no-loc(new):::`** , um auf ein Objekt zu verweisen, das auf dem Heap zugeordnet ist, was Sie explizit benötigen **`:::no-loc(delete):::`** . Das Beispiel zeigt auch einige der Gefahren im Zusammenhang mit unformatierten Zeigern. (Beachten Sie, dass es sich bei diesem Beispiel um C-Programmierung und nicht um modern C++ handelt.)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
:::no-loc(void)::: func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
:::no-loc(void)::: func_B(MyClass mc)
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
    // Use :::no-loc(new)::: to allocate and initialize memory
    MyClass* pmc = :::no-loc(new)::: MyClass{ 108, "Nick" };

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
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    :::no-loc(delete):::(pmc); // don't forget to give memory back to operating system!
   // :::no-loc(delete):::(pmc2); //crash! memory location was already :::no-loc(delete):::d
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Zeigerarithmetik und Arrays

Zeiger und Arrays sind eng miteinander verknüpft. Wenn ein Array als Wert an eine Funktion übermittelt wird, wird es als Zeiger an das erste Element übermittelt. Im folgenden Beispiel werden die folgenden wichtigen Eigenschaften von Zeigern und Arrays veranschaulicht:

- der **`sizeof`** Operator gibt die Gesamtgröße eines Arrays in Bytes zurück.
- um die Anzahl der Elemente zu ermitteln, teilen Sie die Gesamtanzahl der Bytes durch die Größe eines Elements.
- Wenn ein Array an eine Funktion übermittelt wird, *wird es zu* einem Zeigertyp.
- der **`sizeof`** Operator gibt bei Anwendung auf einen Zeiger die Zeiger Größe, 4 Bytes auf x86 oder 8 Bytes auf x64 zurück.

```cpp
#include <iostream>

:::no-loc(void)::: func(int arr[], int length)
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

Bestimmte Arithmetische Operationen können für nicht-- :::no-loc(const)::: Zeiger verwendet werden, um Sie auf einen anderen Speicherort zu verweisen. Zeiger werden mithilfe der **++** **+=** **-=** Operatoren, und inkrementiert und dekrementiert **--** . Dieses Verfahren kann in Arrays verwendet werden und ist besonders nützlich für Puffer von nicht typisierten Daten. Eine **:::no-loc(void):::\*** wird um die Größe eines **`:::no-loc(char):::`** (1 Byte) inkrementiert. Ein typisierter Zeiger wird um die Größe des Typs, auf den er verweist, inkrementiert.

Im folgenden Beispiel wird veranschaulicht, wie Zeigerarithmetik für den Zugriff auf einzelne Pixel in einer Bitmap unter Windows verwendet werden kann. Beachten Sie die Verwendung von **`:::no-loc(new):::`** und **`:::no-loc(delete):::`** und des Dereferenzierungsoperators.

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

    :::no-loc(const):::expr int bufferSize = 30000;
    unsigned :::no-loc(char):::* buffer = :::no-loc(new)::: unsigned :::no-loc(char):::[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned :::no-loc(char):::* begin = &buffer[0];
    unsigned :::no-loc(char):::* end = &buffer[0] + bufferSize;
    unsigned :::no-loc(char):::* p = begin;
    :::no-loc(const):::expr int pixelWidth = 3;
    :::no-loc(const):::expr int borderWidth = 2;

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
        p++; // Increment one byte sizeof(unsigned :::no-loc(char):::).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<:::no-loc(char):::*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(&header), sizeof(header));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(begin), bufferSize);

    :::no-loc(delete):::[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="no-locvoid-pointers"></a>:::no-loc(void):::* Zeiger

Ein Zeiger auf **`:::no-loc(void):::`** zeigt einfach auf einen rohspeicher Speicherort. Manchmal ist es erforderlich **:::no-loc(void):::\*** , Zeiger zu verwenden, z. b. bei der Übergabe zwischen C++-Code und C-Funktionen.

Wenn ein typisierter Zeiger in einen- :::no-loc(void)::: Zeiger umgewandelt wird, bleibt der Inhalt des Speicher Orts unverändert. Die Typinformationen gehen jedoch verloren, sodass Sie keine Inkrement-oder Dekrement-Vorgänge ausführen können. Eine Speicheradresse kann z `MyClass*` . b. von in **`:::no-loc(void):::*`** und zurück in umgewandelt werden `MyClass*` . Solche Vorgänge sind grundsätzlich fehleranfällig und erfordern sehr viel Aufmerksamkeit für :::no-loc(void)::: Fehler. Modern C++ lehnt die Verwendung von :::no-loc(void)::: Zeigern in nahezu allen Fällen ab.

```cpp

//func.c
:::no-loc(void)::: func(:::no-loc(void):::* data, int length)
{
    :::no-loc(char):::* c = (:::no-loc(char):::*)(data);

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
    :::no-loc(void)::: func(:::no-loc(void):::* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = :::no-loc(new)::: MyClass{10, "Marian"};
    :::no-loc(void):::* p = static_cast<:::no-loc(void):::*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator :::no-loc(new)::: to allocate untyped memory block
    :::no-loc(void):::* p:::no-loc(void)::: = operator :::no-loc(new):::(1000);
    :::no-loc(char):::* p:::no-loc(char)::: = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::);
    for(:::no-loc(char):::* c = p:::no-loc(char):::; c < p:::no-loc(char)::: + 1000; ++c)
    {
        *c = 0x00;
    }
    func(p:::no-loc(void):::, 1000);
    :::no-loc(char)::: ch = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::)[0];
    std::cout << ch << std::endl; // 'A'
    operator :::no-loc(delete):::(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Zeiger auf Funktionen

Bei der Programmierung im C-Stil werden Funktionszeiger hauptsächlich verwendet, um Funktionen an andere Funktionen zu übergeben. Diese Technik ermöglicht es dem Aufrufer, das Verhalten einer Funktion anzupassen, ohne Sie zu ändern. In modernen C++ bieten [Lambda-Ausdrücke](lambda-expressions-in-cpp.md) dieselbe Funktion mit größerer Typsicherheit und anderen Vorteilen.

Eine Funktionszeiger Deklaration gibt die Signatur an, über die die pointierenfunktion verfügen muss:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
:::no-loc(void)::: (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

Das folgende Beispiel zeigt eine Funktion `combine` , die eine Funktion als Parameter akzeptiert, die eine akzeptiert `std::string` und einen zurückgibt `std::string` . Abhängig von der Funktion, die an weitergegeben `combine` wird, wird eine Zeichenfolge entweder vorangestellt oder angefügt.

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
 [Dereferenzierungsoperator: *](indirection-operator-star.md)<br/>
[address-of-Operator](address-of-operator-amp.md)</br>
[Willkommen zurück bei C++](welcome-back-to-cpp-modern-cpp.md)
