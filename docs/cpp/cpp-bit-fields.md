---
title: C++-Bitfelder
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 7c2dbb6e2932265984c8cb4e1e34504921e5d666
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221782"
---
# <a name="c-bit-fields"></a>C++-Bitfelder

Klassen und Strukturen können Member enthalten, die weniger Speicher als ein ganzzahliger Typ belegen. Diese Member werden als Bitfelder angegeben. Die Syntax für die Spezifikation der *Bitfeldmember-Deklarator* folgt:

## <a name="syntax"></a>Syntax

*Deklarator* **:** *Constant-Expression*

## <a name="remarks"></a>Bemerkungen

Der *Deklarator* (optional) ist der Name, mit dem im Programm auf den Member zugegriffen wird. Es muss ein ganzzahliger Typ sein (einschließlich Enumerationstypen). *Constant-Expression* gibt die Anzahl der Bits an, die der Member in der Struktur einnimmt. Anonyme Bitfelder, also Bitfeldmember ohne Bezeichner, können zur Auffüllung verwendet werden.

> [!NOTE]
> Ein unbenanntes Bitfeld mit der Breite 0 erzwingt die Ausrichtung des nächsten Bitfelds an der nächsten **Typgrenze** , wobei **Type** der Typ des Members ist.

Das folgende Beispiel deklariert eine Struktur, die zwei Bitfelder enthält:

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

Das konzeptionelle Speicherlayout eines Objekts vom Typ `Date` wird in der folgenden Abbildung dargestellt.

![Speicherlayout eines Datumsobjekts](../cpp/media/vc38uq1.png "Speicherlayout eines Datumsobjekts") <br/>
Speicherlayout von Datumsobjekten

Beachten Sie, dass `nYear` 8 Bits lang ist und die Wort Grenze des deklarierten Typs überlaufen würde **`unsigned short`** . Daher wird er am Anfang eines neuen gestartet **`unsigned short`** . Es ist nicht notwendig, dass alle Bitfelder in ein Objekt des zugrunde liegenden Typs passen. Neue Speichereinheiten werden entsprechend der Anzahl von Bits, die in der Deklaration angefordert werden, zugeordnet.

**Microsoft-spezifisch**

Die Daten, die als Bitfelder deklariert werden, werden beginnend mit dem niedrigsten Bitwert bis hin zum höchsten Bitwert aufgeführt, wie in der Abbildung oben dargestellt.

**Ende Microsoft-spezifisch**

Wenn die Deklaration einer Struktur ein unbenanntes Feld mit der Länge 0 (null) enthält, wie im folgenden Beispiel gezeigt,

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

Anschließend wird das Speicher Layout wie in der folgenden Abbildung gezeigt:

![Layout des Datums Objekts mit 0 (null)&#45;Längen Bitfeld](../cpp/media/vc38uq2.png "Layout des Datums Objekts mit 0 (null)&#45;Längen Bitfeld") <br/>
Layout des Datumsobjekts mit Bitfeld der Länge 0 (null)

Der zugrunde liegende Typ eines Bitfelds muss ein ganzzahliger Typ sein, wie in den [integrierten Typen](../cpp/fundamental-types-cpp.md)beschrieben.

Wenn es sich bei dem Initialisierer für einen Verweis vom Typ um `const T&` einen lvalue handelt, der auf ein Bitfeld vom Typ verweist `T` , wird der Verweis nicht direkt an das Bitfeld gebunden. Stattdessen wird der Verweis an eine temporär initialisierte gebunden, die den Wert des Bitfelds enthalten soll.

## <a name="restrictions-on-bit-fields"></a>Einschränkungen bei Bitfeldern

Die folgende Liste zeigt Einzelheiten zu fehlerhaften Operationen in Bitfeldern:

- Verwenden der Adresse eines Bitfelds.

- Initialisieren eines nicht- **`const`** Verweises mit einem Bitfeld.

## <a name="see-also"></a>Weitere Informationen

[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)
