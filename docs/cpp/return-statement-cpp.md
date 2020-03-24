---
title: return-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: c8ea796ab40a2090ed9853377f7c9415914bc0e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178981"
---
# <a name="return-statement-c"></a>return-Anweisung (C++)

Beendet die Ausführung einer Funktion und gibt die Steuerung an die aufrufende Funktion zurück (oder an das Betriebssystem, wenn Sie die Steuerung von der `main`-Funktion übertragen). Die Ausführung wird in der aufrufenden Funktion an dem Punkt fortgesetzt, der dem Aufruf unmittelbar folgt.

## <a name="syntax"></a>Syntax

```
return [expression];
```

## <a name="remarks"></a>Bemerkungen

Die Klausel `expression` wird, sofern vorhanden, in den Typ konvertiert, der in der Funktionsdeklaration angegeben wird, als ob eine Initialisierung durchgeführt würde. Durch die Konvertierung vom Typ des Ausdrucks in den **Rückgabetyp** der Funktion können temporäre Objekte erstellt werden. Weitere Informationen darüber, wie und wann temporare erstellt werden, finden Sie unter [temporäre Objekte](../cpp/temporary-objects.md).

Der Wert der `expression`-Klausel wird an die aufrufende Funktion zurückgegeben. Wenn der Ausdruck ausgelassen wird, wird der Rückgabewert der Funktion nicht definiert. Konstruktoren und Dekonstruktoren sowie Funktionen vom Typ **void**können keinen Ausdruck in der **Return** -Anweisung angeben. Funktionen aller anderen Typen müssen in der **Return** -Anweisung einen Ausdruck angeben.

Wenn die Ablauf Steuerung den Block beendet, der die Funktionsdefinition einschließt, ist das Ergebnis das gleiche wie beim Ausführen einer **Return** -Anweisung ohne Ausdruck. Dies ist ungültig bei Funktionen, die mit Rückgabewert deklariert werden.

Eine Funktion kann eine beliebige Anzahl von **Return** -Anweisungen aufweisen.

Im folgenden Beispiel wird ein Ausdruck mit einer **Return** -Anweisung verwendet, um die größte von zwei Ganzzahlen abzurufen.

## <a name="example"></a>Beispiel

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Weitere Informationen

[Sprunganweisungen](../cpp/jump-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
