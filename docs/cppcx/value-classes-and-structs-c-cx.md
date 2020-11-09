---
title: Wertklassen und Strukturen (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 15d54d139f086ce5bb025aaeab145c71d33903c0
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381596"
---
# <a name="value-classes-and-structs-ccx"></a>Wertklassen und Strukturen (C++/CX)

Eine *Wert Struktur* oder *Wert Klasse* ist ein Windows-Runtime kompatibler Pod ("Plain Old Data Structure"). Sie verfügt über eine feste Größe und besteht nur aus Feldern. Anders als eine Verweisklasse hat sie keine Eigenschaften.

Die folgenden Beispiele zeigen, wie Wertstrukturen deklariert und initialisiert werden.

```

// in mainpage.xaml.h:
    value struct TestStruct
    {
        Platform::String^ str;
        int i;
    };

    value struct TestStruct2
    {
        TestStruct ts;
        Platform::String^ str;
        int i;
    };

// in mainpage.cpp:
    // Initialize a value struct with an int and String
    TestStruct ts = {"I am a TestStruct", 1};

    // Initialize a value struct that contains
    // another value struct, an int and a String
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};

    // Initialize value struct members individually.
    TestStruct ts3;
    ts3.i = 108;
    ts3.str = "Another way to init a value struct.";
```

Wenn eine Variable eines Werttyps einer anderen Variablen zugewiesen wird, wird der Wert kopiert, damit jede der beiden Variablen eine eigene Kopie der Daten besitzt. Eine *Wert* Struktur ist eine Struktur fester Größe, die nur öffentliche Datenfelder enthält und mit dem- **`value struct`** Schlüsselwort deklariert wird.

Eine *Wert Klasse* ist wie eine **`value struct`** , außer dass ihren Feldern explizit öffentliche Barrierefreiheit zugewiesen werden muss. Sie wird mit dem- **`value class`** Schlüsselwort deklariert.

Eine Wert Struktur oder Wert Klasse kann als Felder nur grundlegende numerische Typen, `Platform::String^` Enumerationsklassen, oder [Platform:: iBox \<T> ^ ](../cppcx/platform-ibox-interface.md) enthalten, wobei T ein numerischer Typ oder eine Enumerationsklasse oder eine Wert Klasse oder eine Struktur ist. Ein `IBox<T>^` Feld kann den Wert – haben **`nullptr`** . auf diese Weise implementiert C++ das Konzept von auf NULL festleg *baren Werttypen*.

Eine Wertklasse oder Wertstruktur, die einen `Platform::String^` - oder `IBox<T>^` -Typ als Member enthält, das nicht `memcpy`-fähig ist.

Da alle Member einer **`value class`** oder **`value struct`** öffentlich sind und in Metadaten ausgegeben werden, sind Standard-C++-Typen als Member nicht zulässig. Dies unterscheidet sich von Verweis Klassen, die **`private`** oder **`internal`** C++-Standardtypen enthalten können.

Im folgenden Codefragment werden die `Coordinates` - und `City` -Typen als Wertstrukturen deklariert. Beachten Sie, dass einer der `City` -Datenmember ein `GeoCoordinates` -Typ ist. Eine **`value struct`** kann andere Wert Strukturen als Member enthalten.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Parameterübergabe für Werttypen

Wenn Sie über einen Werttyp als Funktions- oder Methodenparameter verfügen, wird er normalerweise als Wert übergeben. Bei größeren Objekten kann dies zu Leistungsproblemen führen. In Visual Studio 2013 und früheren Versionen wurden Werttypen in C++/CX immer als Wert weitergegeben. In Visual Studio 2015 und höher können Werttypen als Verweis oder als Wert übergeben werden.

Verwenden Sie zum Deklarieren eines Parameters, der einen Werttyp als Wert übergibt, Code wie den folgenden:

```cpp
void Method1(MyValueType obj);
```

Um einen Parameter zu deklarieren, der einen Werttyp als Verweis übergibt, verwenden Sie das Verweissymbol (&), wie im Folgenden dargestellt:

```cpp
void Method2(MyValueType& obj);
```

Der Typ in „Method2“ ist ein Verweis auf „MyValueType“ und funktioniert in der gleichen Weise wie ein Verweistyp in standardmäßigem C++.

Wenn Sie „Method1“ von einer anderen Sprache, wie etwa C#, aus aufrufen, brauchen Sie das Schlüsselwort `ref` oder `out` nicht zu verwenden. Wenn Sie „Method2“ aufrufen, verwenden Sie das `ref` -Schlüsselwort.

```
Method2(ref obj);
```

Sie können auch ein Zeigersymbol (*) verwenden, um einen Werttyp als Verweis zu übergeben. Das Verhalten in Bezug auf Aufrufer in anderen Sprachen ist identisch (Aufrufer in C# verwenden das `ref` -Schlüsselwort ), aber in der Methode ist der Typ ein Zeiger auf den Werttyp.

## <a name="nullable-value-types"></a>Auf NULL festlegbare Werttypen

Wie bereits erwähnt, kann eine Wert Klasse oder eine Wert Struktur ein Feld vom Typ [Platform:: iBox \<T> ^ ](../cppcx/platform-ibox-interface.md)aufweisen, z `IBox<int>^` . –.. Ein solches Feld kann einen beliebigen numerischen Wert haben, der für den **`int`** Typ gültig ist, oder er kann den Wert haben **`nullptr`** . Sie können ein auf NULL festlegbares Feld als Argument an eine Methode, deren Parameter als optional deklariert ist, oder an eine beliebige andere Stelle übergeben, für die ein Werttyp keinen Wert haben muss.

Im folgenden Beispiel wird veranschaulicht, wie eine Struktur mit einem auf NULL festlegbaren Feld initialisiert wird.

```
public value struct Student
{
    Platform::String^ Name;
    int EnrollmentYear;
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.
};
//To create a Student struct, one must populate the nullable type.
MainPage::MainPage()
{
    InitializeComponent();

    Student A;
    A.Name = "Alice";
    A.EnrollmentYear = 2008;
    A.GraduationYear = ref new Platform::Box<int>(2012);

    Student B;
    B.Name = "Bob";
    B.EnrollmentYear = 2011;
    B.GraduationYear = nullptr;

    IsCurrentlyEnrolled(A);
    IsCurrentlyEnrolled(B);
}
bool MainPage::IsCurrentlyEnrolled(Student s)
{
    if (s.GraduationYear == nullptr)
    {
        return true;
    }
    return false;
}
```

Eine Wertstruktur selbst kann genauso auf NULL festgelegt werden, wie hier dargestellt:

```

public value struct MyStruct
{
public:
    int i;
    Platform::String^ s;
};

public ref class MyClass sealed
{
public:
    property Platform::IBox<MyStruct>^ myNullableStruct;
};
```

## <a name="see-also"></a>Siehe auch

[Typsystem (C++-CX)](../cppcx/type-system-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)<br/>
[Verweisklassen und Strukturen (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
