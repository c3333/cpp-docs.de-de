---
title: Rohzeiger (C++)
description: Verwenden von unformatierten Zeigern inC++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 2dbb4f11fc0c08578e82371e8df77e9643313879
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077149"
---
# <a name="raw-pointers-c"></a>Rohzeiger (C++)

Ein Zeiger ist ein Typ von Variable, der die Adresse eines Objekts im Arbeitsspeicher speichert und für den Zugriff auf das Objekt verwendet wird. Ein unformatierter *Zeiger* ist ein Zeiger, dessen Lebensdauer nicht durch ein kapselnde Objekt wie einen [intelligenten Zeiger](smart-pointers-modern-cpp.md)gesteuert wird. Einem unformatierten Zeiger kann die Adresse einer anderen nicht-Zeiger Variablen zugewiesen werden, oder ihm kann der Wert [nullptr](nullptr.md)zugewiesen werden. Ein Zeiger, dem kein Wert zugewiesen wurde, enthält zufällige Daten.

Ein Zeiger kann auch *dereferenziert* werden, um den Wert des Objekts abzurufen, auf das er verweist. Der *Member Access-Operator* ermöglicht den Zugriff auf die Member eines Objekts.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Ein Zeiger kann auf ein typisiertes Objekt oder auf das **void**-Objekt zeigen. Wenn ein Programm ein neues Objekt auf dem [Heap](https://wikipedia.org/wiki/Heap) im Arbeitsspeicher belegt, empfängt es die Adresse des Objekts in Form eines Zeigers. Solche Zeiger werden als *besitzende Zeiger*bezeichnet. ein Besitz ender Zeiger (oder eine Kopie davon) muss verwendet werden, um das vom Heap zugeordnete Objekt explizit zu löschen, wenn es nicht mehr benötigt wird. Wenn der Arbeitsspeicher nicht gelöscht wird, führt dies zu einem *Speicher* Verluste und rendert diesen Speicher Speicherort für ein anderes Programm auf dem Computer nicht. Weitere Informationen finden Sie unter [New-und DELETE-Operatoren](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Ein Zeiger (wenn er nicht als " **konstant**" deklariert ist) kann inkrementiert oder dekrementiert werden, sodass er auf einen neuen Speicherort im Arbeitsspeicher verweist. Dies wird als *Zeigerarithmetik* bezeichnet und wird bei der Programmierung im C-Stil verwendet, um Elemente in Arrays oder anderen Datenstrukturen zu durchlaufen. Ein **konstanter Zeiger kann** nicht erstellt werden, um auf einen anderen Speicherort zu verweisen, und in diesem Sinne ähnelt dies einem [Verweis](references-cpp.md). Weitere Informationen finden Sie unter Konstante [und volatile-Zeiger](const-and-volatile-pointers.md).

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

Bei 64-Bit-Betriebssystemen hat ein Zeiger eine Größe von 64 Bits. die Zeiger Größe eines Systems bestimmt, wie viel Adressier barer Arbeitsspeicher aufweisen kann. Alle Kopien eines Zeigers zeigen auf denselben Speicherort. Zeiger (zusammen mit verweisen) werden häufig in C++ verwendet, um größere Objekte an und von Funktionen zu übergeben, weil es in der Regel weitaus effizienter ist, die 64-Bit-Adresse eines Objekts zu kopieren, als ein gesamtes Objekt zu kopieren. Geben Sie beim Definieren einer Funktion Zeiger Parameter als **konstant** an, es sei denn, Sie beabsichtigen, dass die Funktion das Objekt ändert. Im Allgemeinen sind die **Konstanten** Verweise die bevorzugte Methode, um Objekte an Funktionen zu übergeben, es sei denn, der Wert des Objekts kann **nullptr**sein.

[Zeiger auf Funktionen](#pointers_to_functions) ermöglichen das Übertragen von Funktionen an andere Funktionen und werden für "Rückrufe" bei der Programmierung im C-Format verwendet. Modern C++ verwendet für diesen Zweck [Lambda-Ausdrücke](lambda-expressions-in-cpp.md) .

## <a name="initialization-and-member-access"></a>Initialisierung und Element Zugriff

Im folgenden Beispiel wird gezeigt, wie ein unformatierter Zeiger deklariert und mit einem Objekt initialisiert wird, das auf dem Heap zugeordnet ist, und wie es verwendet wird. Außerdem werden einige der Gefahren im Zusammenhang mit unformatierten Zeigern angezeigt. (Denken Sie daran, dass es sich hierbei um Programmier Programmierung C++im C-Stil und nicht um moderne

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

Zeiger und Arrays sind eng miteinander verknüpft. Wenn ein Array als Wert an eine Funktion übermittelt wird, wird es als Zeiger an das erste Element übermittelt. Im folgenden Beispiel werden die folgenden wichtigen Eigenschaften von Zeigern und Arrays veranschaulicht:

- der `sizeof`-Operator gibt die Gesamtgröße eines Arrays in Bytes zurück.
- um die Anzahl der Elemente zu ermitteln, teilen Sie die Gesamtanzahl der Bytes durch die Größe eines Elements.
- Wenn ein Array an eine Funktion übermittelt wird, *wird es zu* einem Zeigertyp.
- der `sizeof`-Operator gibt bei Anwendung auf einen Zeiger die Zeiger Größe, 4 Bytes auf x86 oder 8 Bytes auf x64 zurück.

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

Bestimmte Arithmetische Operationen können für nicht konstante Zeiger ausgeführt werden, damit Sie auf einen neuen Speicherort zeigen. Ein Zeiger kann mit den Operatoren **++** , **+=** , **-=** und **--** erhöht und dekrementiert werden. Dieses Verfahren kann in Arrays verwendet werden und ist besonders nützlich für Puffer von nicht typisierten Daten. Ein **void-\*** Inkremente um die Größe eines **char** (1 Byte). Ein typisierter Zeiger erhöht die Größe des Typs, auf den er verweist.

Im folgenden Beispiel wird veranschaulicht, wie Zeigerarithmetik für den Zugriff auf einzelne Pixel in einer Bitmap unter Windows verwendet werden kann. Beachten Sie die Verwendung von " **New** " und " **Delete**" sowie den Dereferenzierungsoperator.

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

## <a name="void-pointers"></a>void *-Zeiger

Ein Zeiger auf " **void** " zeigt einfach auf einen rohspeicher Speicherort. Manchmal ist es erforderlich, **void\*** Zeiger zu verwenden, z. b. C++ bei der Übergabe zwischen Code und C-Funktionen.

Wenn ein typisierter Zeiger in einen void-Zeiger umgewandelt wird, wird der Inhalt des Speicher Orts nicht geändert, aber die Typinformationen gehen verloren, sodass Sie keine Inkrement-oder Dekrement-Vorgänge ausführen können. Eine Speicheradresse kann z. b. von MyClass * in void * und wieder zurück in MyClass * umgewandelt werden. Solche Vorgänge sind grundsätzlich fehleranfällig und erfordern große Sorgfalt, um Fehler zu vermeiden. Modern C++ schreckt die Verwendung von void-Zeigern ab, sofern dies nicht unbedingt erforderlich ist.

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
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
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

Bei der Programmierung im C-Stil werden Funktionszeiger hauptsächlich verwendet, um Funktionen an andere Funktionen zu übergeben. In diesem Szenario kann der Aufrufer das Verhalten einer Funktion anpassen, ohne Sie zu ändern. In modernen C++sind [Lambda-Ausdrücke](lambda-expressions-in-cpp.md) mit größerer Typsicherheit und anderen Vorteilen identisch.

Eine Funktionszeiger Deklaration gibt die Signatur an, über die die pointierenfunktion verfügen muss:

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

Das folgende Beispiel zeigt eine Funktions `combine`, die eine Funktion als Parameter annimmt, die eine `std::string` akzeptiert und eine `std::string`zurückgibt. Abhängig von der Funktion, die an `combine` weitergeleitet wird, wird eine Zeichenfolge vorangestellt oder angefügt.

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

## <a name="see-also"></a>Weitere Informationen

[Intelligenter Zeiger](smart-pointers-modern-cpp.md)
[Dereferenzierungsoperator: *](indirection-operator-star.md)<br/>
[address-of-Operator](address-of-operator-amp.md)</br>
[Willkommen zurück beiC++](welcome-back-to-cpp-modern-cpp.md)
