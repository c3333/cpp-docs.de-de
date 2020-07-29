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
ms.openlocfilehash: d4511ed7d09ff280d01214a2a177148956580ee5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221613"
---
# <a name="enumerations-c"></a>Enumerationen (C++)

Eine Enumeration ist ein benutzerdefinierter Typ, der aus einem Satz von benannten ganzzahligen Konstanten besteht, die als Enumeratoren bezeichnet werden.

> [!NOTE]
> Dieser Artikel behandelt den ISO **`enum`** -Standard-C++-Sprachtyp und den in C++ 11 eingeführten Enumerationstypen (oder stark typisierten) der **Enumeration-Klasse** . Weitere Informationen über die **öffentliche Enumerationsklasse** oder **private** Enumerationstypen in C++/CLI und C++/CX finden Sie unter Enumerationsklasse. [enum class](../extensions/enum-class-cpp-component-extensions.md)

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

*identifier*<br/>
Der Typname, der für die Enumeration angegeben wurde.

*type*<br/>
Der zugrunde liegende Typ der Enumeratoren. Alle Enumeratoren weisen den gleichen zugrunde liegenden Typ auf. Kann ein beliebiger ganzzahliger Typ sein.

*Enum-Liste*<br/>
Eine durch Trennzeichen getrennte Liste mit Enumeratoren in der Enumeration. Jeder Enumerator oder Variablenname im Bereich muss eindeutig sein. Allerdings können die Werte doppelt vorkommen. In einer Aufzählung ohne Bereichs Einschränkung ist der Gültigkeitsbereich der umgebende Bereich. in einer Bereichs bezogenen Aufzählung ist der Gültigkeitsbereich die *enum-List* .  In einer Bereichs bezogenen Aufzählung kann die Liste leer sein, was in der Tat einen neuen ganzzahligen Typ definiert.

*class*<br/>
Wenn Sie dieses Schlüsselwort in der-Deklaration verwenden, geben Sie an, dass die Enumeration den Bereich hat, und es muss ein *Bezeichner* angegeben werden. Sie können auch das- **`struct`** Schlüsselwort anstelle von verwenden **`class`** , da Sie in diesem Kontext semantisch äquivalent sind.

## <a name="enumerator-scope"></a>Enumeratorbereich

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

Jeder Enumerator wird als Konstante behandelt und muss innerhalb des Bereichs, in dem der definiert ist (für Enumerationswerte ohne Bereichs Einschränkung **`enum`** ), oder innerhalb des **`enum`** selbst (für Bereichs bezogene Enumerationswerte) einen eindeutigen Namen aufweisen. Die Werte, die für die Namen angegeben werden, müssen nicht eindeutig sein. Wenn z. B. die Deklaration einer Enumeration ohne Bereichseinschränkung `Suit` folgendermaßen ist:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Dann betragen die Werte von `Diamonds`, `Hearts`, `Clubs` und `Spades` 5, 6, 4 bzw. 5. Beachten Sie, dass 5 mehrmals verwendet wird; dies ist zulässig, auch wenn möglicherweise nicht beabsichtigt. Diese Regeln sind für bereichsbezogene Enumerationen identisch.

## <a name="casting-rules"></a>Umwandlungsregeln

Enumerationskonstanten ohne Bereichs Einschränkung können implizit in konvertiert werden **`int`** , aber eine kann **`int`** nie implizit in einen Enumerationswert konvertiert werden. Das folgende Beispiel veranschaulicht, was geschieht, wenn Sie versuchen, `hand` einen Wert zuzuweisen, der nicht `Suit` ist:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Eine Umwandlung ist erforderlich, um eine **`int`** in einen Bereichs bezogenen oder einen Enumerator ohne Bereichs Einschränkung zu konvertieren. Sie können jedoch einen Enumerator ohne Bereichseinschränkung auch ohne Umwandlung auf einen Ganzzahlwert heraufstufen.

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

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>Enumerationen ohne Enumeratoren

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): indem Sie eine Enumeration (regulär oder Bereichs bezogen) mit einem expliziten zugrunde liegenden Typ und keinen Enumeratoren definieren, können Sie einen neuen integralen Typ mit einer impliziten Konvertierung in einen anderen Typ einführen. Wenn Sie diesen Typ anstelle des integrierten zugrunde liegenden Typs verwenden, können Sie das Potenzial für feine Fehler vermeiden, die durch unbeabsichtigte implizite Konvertierungen verursacht werden.

```cpp
enum class byte : unsigned char { };
```

Der neue-Typ ist eine exakte Kopie des zugrunde liegenden Typs und hat daher die gleiche Aufruf Konvention, d. h., er kann ohne Leistungseinbußen in ABIS verwendet werden. Wenn Variablen des Typs mithilfe der direkt Listen Initialisierung initialisiert werden, ist keine Umwandlung erforderlich. Im folgenden Beispiel wird gezeigt, wie Enumerationen ohne Enumeratoren in verschiedenen Kontexten initialisiert werden:

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

## <a name="see-also"></a>Weitere Informationen

[C-Enumerationsdeklarationen](../c-language/c-enumeration-declarations.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
