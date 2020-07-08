---
title: '##line-Anweisung (C/C++)'
description: 'Beschreibt die #line Direktive, die verwendet wird, um die von Präprozessormakros gemeldete Zeilennummer und den Dateinamen festzulegen.'
ms.date: 07/06/2020
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 7b671cfdf5d5ce43024ac3e038c214396ac8679c
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058619"
---
# <a name="line-directive-cc"></a>#line-Direktive (C/C++)

Die **#Line** -Direktive weist den Präprozessor an, die gemeldeten Werte des Compilers für die Zeilennummer und den Dateinamen auf eine bestimmte Zeilennummer und einen bestimmten Dateinamen festzulegen.

## <a name="syntax"></a>Syntax

> **`#line`***Ziffern Sequenz* ["*Dateiname*"]

## <a name="remarks"></a>Bemerkungen

Der Compiler verwendet die Zeilennummer und den optionalen Dateinamen, um auf Fehler zu verweisen, die während der Kompilierung gefunden werden. Die Zeilennummer verweist normalerweise auf die aktuelle Eingabezeile, und der Dateiname verweist auf die aktuelle Eingabedatei. Nach der Verarbeitung jeder Zeile wird die Zeilennummer erhöht.

Der *Ziffern Sequenz* Wert kann eine beliebige ganzzahlige Konstante sein. Makro Ersetzung kann für die Vorverarbeitungs Token verwendet werden, aber das Ergebnis muss in der richtigen Syntax ausgewertet werden. Der *Dateiname* kann eine beliebige Kombination von Zeichen sein und muss in doppelte Anführungszeichen () eingeschlossen werden `" "` . Wenn *filename* ausgelassen wird, bleibt der vorherige Dateiname unverändert.

Sie können die Quell Zeilennummer und den Dateinamen ändern, indem Sie eine- **`#line`** Anweisung schreiben. Die- **`#line`** Direktive legt den Wert für die Zeile fest, die direkt auf die-Direktive in der Quelldatei folgt. Der Konvertierer verwendet die Zeilennummer und den Dateinamen, um die Werte der vordefinierten Makros und zu bestimmen `__FILE__` `__LINE__` . Sie können diese Makros verwenden, um selbsterklärende Fehlermeldungen in den Programmtext einzufügen. Weitere Informationen zu diesen vordefinierten Makros finden Sie unter [vordefinierte Makros](../preprocessor/predefined-macros.md).

Das- `__FILE__` Makro wird zu einer Zeichenfolge erweitert, deren Inhalt der Dateiname ist, umgeben von doppelten Anführungszeichen ( `" "` ).

Wenn Sie die Zeilennummer und den Dateinamen ändern, ignoriert der Compiler die vorherigen Werte und setzt die Verarbeitung mit den neuen Werten fort. Die **#Line** -Direktive wird in der Regel von Programm-Generatoren verwendet. Sie wird verwendet, um zu bewirken, dass Fehlermeldungen auf die ursprüngliche Quelldatei und nicht auf das generierte Programm verweisen.

## <a name="example"></a>Beispiel

In den folgenden Beispielen werden **`#line`** und die `__LINE__` -und- `__FILE__` Makros veranschaulicht.

Im ersten Beispiel wird die Zeilennummer auf 10 und dann auf 20 festgelegt, und der Dateiname wird in *Hello. cpp*geändert.

```cpp
// line_directive.cpp
// Compile by using: cl /W4 /EHsc line_directive.cpp
#include <stdio.h>

int main()
{
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 10
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 20 "hello.cpp"
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
}
```

```Output
This code is on line 7, in file line_directive.cpp
This code is on line 10, in file line_directive.cpp
This code is on line 20, in file hello.cpp
This code is on line 21, in file hello.cpp
```

In diesem Beispiel `ASSERT` verwendet das-Makro die vordefinierten Makros `__LINE__` und `__FILE__` , um eine Fehlermeldung zur Quelldatei auszugeben, wenn eine gegebene Erklärung nicht wahr ist.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Weitere Informationen

[Präprozessoranweisungen](../preprocessor/preprocessor-directives.md)
