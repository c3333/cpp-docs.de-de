---
title: reinterpret_cast-Operator
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 34c2fcb0e1f7f4df4e207d1737afc9c42e011feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188284"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast-Operator

Ermöglicht, dass ein beliebiger Zeiger in einen anderen Zeigertyp konvertiert wird. Ermöglicht es außerdem, einen beliebigen ganzzahligen Typ in einen beliebigen Zeigertyp und umgekehrt zu konvertieren.

## <a name="syntax"></a>Syntax

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Bemerkungen

Der Missbrauch des **reinterpret_cast** Operators kann problemlos unsicher sein. Sofern nicht die gewünschte Konvertierung grundsätzlich auf niedriger Ebene stattfindet, sollten Sie einen der anderen Umwandlungsoperatoren verwenden.

Der **reinterpret_cast** -Operator kann für Konvertierungen verwendet werden, z. b. `char*` zu `int*`oder `Unrelated_class*``One_class*`, die grundsätzlich unsicher sind.

Das Ergebnis einer **reinterpret_cast** kann nicht sicher für andere Elemente verwendet werden, als Sie zurück in den ursprünglichen Typ umgewandelt werden. Andere Verwendungsmöglichkeiten sind bestenfalls nicht portierbar.

Der **reinterpret_cast** -Operator kann die Attribute " **Konstanten**", " **volatile**" oder " **__unaligned** " nicht umwandeln. Weitere Informationen zum Entfernen dieser Attribute finden Sie unter [const_cast-Operator](../cpp/const-cast-operator.md) .

Der **reinterpret_cast** -Operator konvertiert einen NULL-Zeiger Wert in den NULL-Zeiger Wert des Zieltyps.

Eine praktische Verwendung von **reinterpret_cast** ist eine Hash Funktion, die einen Wert einem Index so zuordnet, dass zwei unterschiedliche Werte selten denselben Index haben.

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

Der **reinterpret_cast** ermöglicht, dass der Zeiger als ganzzahliger Typ behandelt wird. Das Ergebnis ist dann eine Bitverschiebung oder ein XOR-Vorgang, um einen eindeutigen Index zu erstellen (eindeutig mit hoher Wahrscheinlichkeit). Der Index wird dann von einer standardmäßigen Umwandlung im C-Format in den Rückgabetyp der Funktion abgeschnitten.

## <a name="see-also"></a>Weitere Informationen

[Umwandlungsoperatoren](../cpp/casting-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
