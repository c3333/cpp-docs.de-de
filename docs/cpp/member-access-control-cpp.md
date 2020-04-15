---
title: Memberzugriffssteuerung (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: e8f62e82ebb7fcc18be5ac7d203df0fb46c9b635
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369858"
---
# <a name="member-access-control-c"></a>Memberzugriffssteuerung (C++)

Mit Zugriffssteuerungen können Sie die [öffentliche](../cpp/public-cpp.md) Schnittstelle einer Klasse von den [Details der privaten](../cpp/private-cpp.md) Implementierung und den [geschützten](../cpp/protected-cpp.md) Membern trennen, die nur für die Verwendung durch abgeleitete Klassen verwendet werden können. Der Zugriffsspezifizierer gilt für alle Member, die danach deklariert werden, bis der nächste Zugriffsspezifizierer ermittelt wird.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

Der Standardzugriff ist in einer Klasse **privat** und in einer Struktur oder Union **öffentlich.** Zugriffsspezifizierer in einer Klasse können beliebig oft in jeder Reihenfolge verwendet werden. Die Speicherbelegung für Objekte von Klassentypen ist implementierungsabhängig, aber Member werden garantiert immer höheren Speicheradressen zwischen Zugriffsspezifizierern zugewiesen.

## <a name="member-access-control"></a>Memberzugriffssteuerung

|Zugriffstyp|Bedeutung|
|--------------------|-------------|
|[privat](../cpp/private-cpp.md)|Als **privat** deklarierte Klassenmember können nur von Memberfunktionen und Freunden (Klassen oder Funktionen) der Klasse verwendet werden.|
|[protected](../cpp/protected-cpp.md)|Als **geschützt** deklarierte Klassenmember können von Memberfunktionen und Freunden (Klassen oder Funktionen) der Klasse verwendet werden. Darüber hinaus können sie von Klassen verwendet werden, die aus der Klasse abgeleitet sind.|
|[public](../cpp/public-cpp.md)|Klassenmember, die als **öffentlich** deklariert sind, können von jeder Funktion verwendet werden.|

Mit der Zugriffssteuerung können Sie verhindern, dass Objekte auf andere, nicht zweckgemäße Art und Weise verwendet werden. Dieser Schutz geht verloren, wenn explizite Typkonvertierungen (Umwandlungen) ausgeführt werden.

> [!NOTE]
> Die Zugriffssteuerung ist auf alle Namen gleich anwendbar: Memberfunktionen, Memberdaten, geschachtelte Klassen und Enumeratoren.

## <a name="access-control-in-derived-classes"></a>Zugriffssteuerung in abgeleiteten Klassen

Zwei Faktoren steuern, auf welche Member einer Basisklasse in einer abgeleiteten Klasse zugegriffen werden kann. Dieselben Faktoren steuern den Zugriff auf geerbte Member in der abgeleiteten Klasse:

- Gibt an, ob die abgeleitete Klasse die Basisklasse mithilfe des **Public** Access-Bezeichners deklariert.

- Entspricht dem Zugriff auf den Member in der Basisklasse.

Die folgende Tabelle zeigt die Interaktion zwischen diesen Faktoren und wie der Zugriff auf Basisklassenmember bestimmt wird.

### <a name="member-access-in-base-class"></a>Memberzugriff in Basisklasse

|private|protected|Öffentlich|
|-------------|---------------|------------|
|Unabhängig vom Ableitungszugriff kann nicht zugegriffen werden|Privat in abgeleitete Klasse, wenn Sie private Ableitung verwenden|Privat in abgeleitete Klasse, wenn Sie private Ableitung verwenden|
||Geschützt in abgeleiteter Klasse, wenn Sie geschützte Ableitung verwenden|Geschützt in abgeleiteter Klasse, wenn Sie geschützte Ableitung verwenden|
||Geschützt in abgeleiteter Klasse, wenn Sie öffentliche Ableitung verwenden|Öffentlich in abgeleiteter Klasse, wenn Sie öffentliche Ableitung verwenden|

Das folgende Beispiel veranschaulicht dies:

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

In `DerivedClass1` ist die Memberfunktion `PublicFunc` ein öffentlicher Member und `ProtectedFunc` ist ein geschützter Member, da `BaseClass` eine öffentliche Basisklasse ist. `PrivateFunc` ist für `BaseClass` privat und für keine abgeleiteten Klassen zugänglich.

In `DerivedClass2` werden die Funktionen `PublicFunc` und `ProtectedFunc` als private Member betrachtet, da `BaseClass` eine private Basisklasse ist. Auch hier ist `PrivateFunc` für `BaseClass` privat und für keine abgeleiteten Klassen zugänglich.

Sie können eine abgeleitete Klasse ohne einen Basisklassen-Zugriffsspezifizierer deklarieren. In einem solchen Fall wird die Ableitung als privat betrachtet, wenn die abgeleitete Klassendeklaration das **Klassenschlüsselwort** verwendet. Die Ableitung gilt als öffentlich, wenn die abgeleitete Klassendeklaration das **Schlüsselwort struct** verwendet. Beispielsweise folgender Code:

```cpp
class Derived : Base
...
```

entspricht:

```cpp
class Derived : private Base
...
```

Ebenso folgender Code:

```cpp
struct Derived : Base
...
```

entspricht:

```cpp
struct Derived : public Base
...
```

Beachten Sie, dass Member, die als mit privatem Zugriff deklariert wurden, **friend** für Funktionen oder abgeleitete Klassen nicht zugänglich sind, es sei denn, diese Funktionen oder Klassen werden mithilfe der Friend-Deklaration in der Basisklasse deklariert.

Ein **Union-Typ** kann keine Basisklasse haben.

> [!NOTE]
> Beim Angeben einer privaten Basisklasse ist es ratsam, explizit das **private** Schlüsselwort zu verwenden, damit Benutzer der abgeleiteten Klasse den Memberzugriff verstehen.

## <a name="access-control-and-static-members"></a>Zugriffssteuerung und statische Member

Wenn Sie eine Basisklasse als **privat**angeben, wirkt sie sich nur auf nicht statische Member aus. Öffentliche statische Member sind in den abgeleiteten Klassen immer noch zugänglich. Zugriff auf Member der Basisklasse mithilfe von Zeigern, Verweisen oder Objekten kann jedoch eine Konvertierung erfordern, woraufhin die Zugriffssteuerung erneut übernommen wird. Betrachten Sie das folgenden Beispiel:

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

Im vorherigen Code verhindert die Zugriffssteuerung die Konvertierung von einem Zeiger auf `Derived2` in einen Zeiger auf `Base`. Der **zeiger** ist implizit vom `Derived2 *`Typ . Um die `CountOf` Funktion auszuwählen, muss `Base *` **diese** in typ konvertiert werden. Eine solche Konvertierung ist nicht zulässig, da `Base` eine private indirekte Basisklasse für `Derived2` ist. Die Konvertierung in einen privaten Typ der Basisklasse ist nur für Zeiger auf direkte abgeleitete Klassen akzeptabel. Daher können Zeiger vom Typ `Derived1 *` in den Typ `Base *` konvertiert werden.

Beachten Sie, dass der explizite Aufruf der `CountOf`-Funktion, ohne Verwenden eines Zeigers, Verweises oder Objekts zum Auswählen keine Konvertierung impliziert. Daher wird der Aufruf zugelassen.

Member und Friends einer abgeleiteten `T`-Klasse können einen Zeiger auf `T` in einen Zeiger auf eine private direkte Basisklasse von `T` konvertieren.

## <a name="access-to-virtual-functions"></a>Zugriff auf virtuelle Funktionen

Die Zugriffssteuerung, die auf [virtuelle](../cpp/virtual-cpp.md) Funktionen angewendet wird, wird durch den Typ bestimmt, der zum Aufruf des Funktions verwendet wird. Überschreiben von Deklarationen der Funktion wirkt sich nicht auf die Zugriffssteuerung für einen angegebenen Typ aus. Beispiel:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

Im vorherigen Beispiel wird das Aufrufen der virtuellen Funktion `GetState` mithilfe eines Zeigers auf Aufrufe des Typs `VFuncBase`, `VFuncDerived::GetState` und `GetState` als öffentlich behandelt. `GetState` jedoch mithilfe eines Zeigers auf den Typ `VFuncDerived` aufzurufen, ist eine Verletzung der Zugriffssteuerung, da `GetState` in der Klasse `VFuncDerived` privat deklariert ist.

> [!CAUTION]
> Die virtuelle Funktion `GetState` kann mithilfe eines Zeigers auf die Basisklasse `VFuncBase` aufgerufen werden. Dies bedeutet nicht, dass die aufgerufene Funktion die Basisklassenversion dieser Funktion ist.

## <a name="access-control-with-multiple-inheritance"></a>Zugriffssteuerung mit mehrfacher Vererbung

In den Mehrfachvererbungsgittern, die virtuelle Basisklassen betreffen, kann ein angegebener Name über mehrere Pfade erreicht werden. Da unterschiedliche Zugriffssteuerungen entlang dieser verschiedenen Pfaden angewendet werden können, wählt der Compiler den Pfad aus, der den umfangreichsten Zugriff gewährt. Dies wird in der folgenden Abbildung veranschaulicht.

![Access-Along-Pfade eines Vererbungsdiagramms](../cpp/media/vc38v91.gif "Access-Along-Pfade eines Vererbungsdiagramms") <br/>
Access-Along-Pfade eines Vererbungsdiagramms

In der Abbildung wird ein Name, der in der Klasse `VBase` deklariert wird, immer durch die Klasse `RightPath` erreicht. Auf den rechten Pfad kann einfacher zugegriffen werden, da `RightPath``VBase` als öffentliche Basisklasse deklariert, während `LeftPath``VBase` als privat deklariert.

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)
