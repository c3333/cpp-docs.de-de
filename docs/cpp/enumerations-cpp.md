---
title: Enumerationen (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: 2a1b3d33534887568c6a55e320e77e0a018cafff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366323"
---
# <a name="enumerations-c"></a>Enumerationen (C++)

Eine Enumeration ist ein benutzerdefinierter Typ, der aus einem Satz von benannten ganzzahligen Konstanten besteht, die als Enumeratoren bezeichnet werden.

> [!NOTE]
> Dieser Artikel behandelt den **ISO-Standard C++-Sprachenumerumtyp** und den in C++11 eingeführten bereichsgebundenen (oder stark typisierten) **Enumerumklassentyp.** Informationen zur **öffentlichen Enumerumklasse** oder zu **den privaten Enumerumklassentypen** in C++/CLI und C++/CX finden Sie unter [enum class](../extensions/enum-class-cpp-component-extensions.md).

## <a name="syntax"></a>Syntax

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>Parameter

*Bezeichner*<br/>
Der Typname, der für die Enumeration angegeben wurde.

*type*<br/>
Der zugrunde liegende Typ der Enumeratoren. Alle Enumeratoren weisen den gleichen zugrunde liegenden Typ auf. Kann ein beliebiger ganzzahliger Typ sein.

*enum-liste*<br/>
Eine durch Trennzeichen getrennte Liste mit Enumeratoren in der Enumeration. Jeder Enumerator oder Variablenname im Bereich muss eindeutig sein. Allerdings können die Werte doppelt vorkommen. In einer nicht spartierten Enumerat ist der Bereich der umgebende Bereich. in einer Bereichsenumerum ist der Bereich die *Enumeratliste* selbst.  In einer Bereichsenumerauchungen kann die Liste leer sein, was faktisch einen neuen Integraltyp definiert.

*class*<br/>
Wenn Sie dieses Schlüsselwort in der Deklaration verwenden, geben Sie an, dass die Enumeration bereichsgebunden ist, und es muss ein *Bezeichner* angegeben werden. Sie können das **Schlüsselwort struct** auch anstelle der **Klasse**verwenden, da sie in diesem Kontext semantisch äquivalent sind.

## <a name="enumerator-scope"></a>Enumerator-Bereich

Eine Enumeration stellt Kontext zum Beschreiben eines Bereichs von Werten bereit, die als benannte Konstanten dargestellt und auch als Enumeratoren bezeichnet werden. In den ursprünglichen C- und C++-Enumerationstypen sind die nicht qualifizierten Enumeratoren überall in dem Bereich sichtbar, in dem die Enumeration deklariert wird. In bereichsbezogenen Enumerationen muss der Enumeratorname durch den Enumerationstypnamen qualifiziert werden. Das folgende Beispiel veranschaulicht diesen grundlegenden Unterschied zwischen den beiden Arten von Enumerationen:

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

Jedem Namen in einer Enumeration wird ein ganzzahliger Wert zugewiesen, der seiner Stelle in der Reihenfolge der Werte in der Enumeration entspricht. Standardmäßig wird dem ersten Wert 0, dem nächsten Wert 1 usw. zugewiesen. Sie können jedoch den Wert eines Enumerators explizit festlegen, wie im Folgenden dargestellt:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

Dem Enumerator `Diamonds` wird der Wert `1` zugewiesen. Nachfolgende Enumeratoren erhalten den Wert des vorherigen Enumerators plus eins, wenn ihnen kein expliziter Wert zugeordnet wurde. Im vorherigen Beispiel würde `Hearts` den Wert 2, `Clubs` den Wert 3 usw. erhalten.

Jeder Enumerator wird als Konstante behandelt und muss einen eindeutigen Namen innerhalb des Bereichs haben, in dem die **Enumerat** definiert ist (für nicht-scoped-Enumerats) oder innerhalb der **Enumerat** selbst (für bereichsgebundene Enumerungen). Die Werte, die für die Namen angegeben werden, müssen nicht eindeutig sein. Wenn z. B. die Deklaration einer Enumeration ohne Bereichseinschränkung `Suit` folgendermaßen ist:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Dann betragen die Werte von `Diamonds`, `Hearts`, `Clubs` und `Spades` 5, 6, 4 bzw. 5. Beachten Sie, dass 5 mehrmals verwendet wird; dies ist zulässig, auch wenn möglicherweise nicht beabsichtigt. Diese Regeln sind für bereichsbezogene Enumerationen identisch.

## <a name="casting-rules"></a>Umwandlungsregeln

Unscoped Enumkonstanten können implizit in **int**konvertiert werden, aber ein **int** ist nie implizit in einen Enumeratwert konvertiert. Das folgende Beispiel veranschaulicht, was geschieht, wenn Sie versuchen, `hand` einen Wert zuzuweisen, der nicht `Suit` ist:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Eine Umwandlung ist erforderlich, um einen **int in** einen bereichs- oder nicht mit Scoped-Enumerator konvertierten. Sie können jedoch einen Enumerator ohne Bereichseinschränkung auch ohne Umwandlung auf einen Ganzzahlwert heraufstufen.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Eine solche Verwendung der impliziten Konvertierungen kann zu unbeabsichtigten Nebeneffekten führen. Um Programmierfehler im Zusammenhang mit Enumerationen ohne Bereichseinschränkung zu eliminieren, sind bereichsbezogene Enumerationswerte stark typisiert. Bereichsbezogene Enumeratoren müssen durch den Enumerationstypnamen (Bezeichner) qualifiziert werden und können nicht, wie im folgenden Beispiel gezeigt, implizit konvertiert werden:

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

Beachten Sie, dass die Zeile `hand = account_num;` noch den Fehler verursacht, der bei Enumerationen ohne Bereichsbeschränkung auftritt, wie oben beschrieben. Sie ist mit einer expliziten Umwandlung zulässig. Bei bereichsbezogenen Enumerationen ist der Versuch einer Konvertierung in der nächsten Anweisung, `account_num = Suit::Hearts;`, nicht mehr ohne eine explizite Umwandlung zulässig.

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>Enumerate ohne Enumeratoren

**Visual Studio 2017 Version 15.3 und höher** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Durch Definieren einer Enumerat (regelmäßig oder im Rahmen) mit einem expliziten zugrunde liegenden Typ und ohne Enumeratoren können Sie in der Tat einen neuen integralen Typ einführen, der keine implizite Konvertierung in einen anderen Typ hat. Wenn Sie diesen Typ anstelle des integrierten zugrunde liegenden Typs verwenden, können Sie das Potenzial für subtile Fehler beseitigen, die durch unbeabsichtigte implizite Konvertierungen verursacht werden.

```cpp
enum class byte : unsigned char { };
```

Der neue Typ ist eine exakte Kopie des zugrunde liegenden Typs und verfügt daher über dieselbe Aufrufkonvention, was bedeutet, dass er ohne Leistungseinbußen für ABIs verwendet werden kann. Es ist keine Umwandlung erforderlich, wenn Variablen des Typs mithilfe der Initialisierung der Direktliste initialisiert werden. Das folgende Beispiel zeigt, wie Enumeren ohne Enumeratoren in verschiedenen Kontexten initialisiert werden:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>Siehe auch

[C-Enumerationsdeklarationen](../c-language/c-enumeration-declarations.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
