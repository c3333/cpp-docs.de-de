---
title: return-Anweisung (C)
description: Die return-Anweisung der C-Programmiersprache beendet die Funktionsausführung und gibt optional einen Wert an den Aufrufer zurück.
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716293"
---
# <a name="return-statement-c"></a>return-Anweisung (C)

Eine **`return`** -Anweisung beendet die Ausführung einer Funktion und gibt die Steuerung an die aufrufende Funktion zurück. Die Ausführung wird in der aufrufenden Funktion an dem Punkt fortgesetzt, der dem Aufruf unmittelbar folgt. Eine **`return`** -Anweisung kann einen Wert an die aufrufende Funktion zurückgeben. Weitere Informationen finden Sie unter [Rückgabetyp](../c-language/return-type.md).

## <a name="syntax"></a>Syntax

> *jump-statement*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`return`** *expression*&#8203;<sub>opt</sub> **`;`**

Der *expression*-Wert wird, sofern er vorhanden ist, an die aufrufende Funktion zurückgegeben. Wenn *expression* ausgelassen wird, wird der Rückgabewert der Funktion nicht definiert. Der Ausdruck wird, sofern er vorhanden ist, ausgewertet und dann in den von der Funktion zurückgegebenen Typ konvertiert. Wenn eine **`return`** -Anweisung einen Ausdruck in Funktionen mit dem Rückgabetyp **`void`** enthält, generiert der Compiler eine Warnung, und der Ausdruck wird nicht ausgewertet.

Wenn in einer Funktionsdefinition keine **`return`** -Anweisung vorliegt, kehrt die Steuerung nach Ausführung der letzten Anweisung der aufgerufenen Funktion automatisch zur aufrufenden Funktion zurück. In diesem Fall ist der Rückgabewert der aufgerufenen Funktion nicht definiert. Wenn die Funktion einen anderen Rückgabetyp als **`void`** aufweist, handelt es sich um einen schwerwiegenden Fehler, und der Compiler gibt eine Diagnosemeldung zur Warnung aus. Wenn die Funktion den Rückgabetyp **`void`** aufweist, ist dieses Verhalten in Ordnung, kann jedoch als schlechter Stil betrachtet werden. Verwenden Sie eine einfache **`return`** -Anweisung, um Ihre Absichten deutlich zu machen.

Eine bewährte Entwicklungsmethode besteht darin, immer einen Rückgabetyp für Funktionen anzugeben. Wenn kein Rückgabewert erforderlich ist, deklarieren Sie den Rückgabetyp **`void`** für die Funktion. Wenn kein Rückgabetyp angegeben wird, geht der C-Compiler vom Standardrückgabetyp **`int`** aus.

Viele Programmierer schließen das *expression*-Argument der **`return`** -Anweisung in Klammern ein. In C sind die Klammern jedoch nicht erforderlich.

Der Compiler gibt möglicherweise eine Warnung zu nicht erreichbarem Code aus, wenn Anweisungen nach der **`return`** -Anweisung ermittelt werden.

In einer **`main`** -Funktion sind die **`return`** -Anweisung und der Ausdruck optional. Was mit dem Rückgabewert geschieht, sofern einer angegeben wurde, hängt von der Implementierung ab. **Microsoft-spezifisch:** Die C-Implementierung von Microsoft gibt den Ausdruckswert an den Prozess zurück, der das Programm aufgerufen hat, z. B. *`cmd.exe`* . Wenn kein **`return`** -Ausdruck angegeben wird, gibt die C-Runtime von Microsoft einen Wert zurück, der einen Erfolg (0 (Null)) oder einen Fehler (ein Wert ungleich Null) angibt.

## <a name="example"></a>Beispiel

Bei diesem Beispiel handelt es sich um mehrere Abschnitte innerhalb eines Programms. Darin wird die **`return`** -Anweisung und ihre Verwendung zum Beenden einer Funktionsausführung und optional zum Zurückgeben eines Werts veranschaulicht.

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

Die `square`-Funktion gibt das Quadrat des Arguments in einem breiteren Typ zurück, um einen arithmetischen Fehler zu verhindern. **Microsoft-spezifisch:** In der C-Implementierung von Microsoft ist der **`long long`** -Typ groß genug, um das Produkt von zwei **`int`** -Werten ohne Überlauf zu enthalten.

Die Klammern um den **`return`** -Ausdruck in `square` werden als Teil des Ausdrucks ausgewertet und sind für die **`return`** -Anweisung nicht erforderlich.

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

Die `ratio`-Funktion gibt das Verhältnis zwischen den zwei **`int`** -Argumenten als **`double`** -Gleitkommawert zurück. Der **`return`** -Ausdruck wird erzwungen, um eine Gleitkommaoperation zu verwenden, indem einer der Operanden in **`double`** umgewandelt wird. Andernfalls würde der Ganzzahl-Divisionsoperator verwendet werden, und die Nachkommastellen würden verloren gehen.

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

Die `report_square`-Funktion ruft `square` mit dem Parameterwert `INT_MAX` auf. Dabei handelt es sich um den größten signierten Ganzzahlwert, der in einen **`int`** -Wert passt. Das **`long long`** -Ergebnis wird in `squared` gespeichert und dann ausgegeben. Die Funktion `report_square` verfügt über den Rückgabetyp **`void`** , d. h., sie enthält keinen Ausdruck in ihrer **`return`** -Anweisung.

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

Die `report_ratio`-Funktion ruft `ratio` mit den Parameterwerten `1` und `INT_MAX` auf. Das **`double`** -Ergebnis wird in `fraction` gespeichert und dann ausgegeben. Die `report_ratio`-Funktion verfügt über den Rückgabetyp **`void`** , daher muss sie keinen Wert explizit zurückgeben. Die Ausführung von `report_ratio` „fällt weg“, und es wird kein Wert an den Aufrufer zurückgegeben.

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

Die **`main`** -Funktion ruft zwei Werte auf: `report_square` und `report_ratio`. Da `report_square` keine Parameter annimmt und **`void`** zurückgibt, wird das Ergebnis keiner Variable zugewiesen. Dementsprechend wird **`void`** von `report_ratio` zurückgegeben, damit der Rückgabewert auch nicht gespeichert wird. Nach all dieses Funktionsaufrufen wird die Ausführung bei der nächsten Anweisung fortgesetzt. Dann gibt die **`main`** -Methode einen Wert von `0` zurück (um in der Regel einen Erfolg zu melden). Daraufhin wird das Programm beendet.

Erstellen Sie zum Kompilieren des Beispiels eine Quellcodedatei namens *`C_return_statement.c`* . Kopieren Sie dann den gesamten Beispielcode in der gezeigten Reihenfolge. Speichern Sie die Datei, und kompilieren Sie sie in einer Developer-Eingabeaufforderung, indem Sie den folgenden Befehl verwenden:

**`cl /W4 C_return_statement.c`**

Geben Sie dann **`C_return_statement.exe`** in die Eingabeaufforderung ein, um den Beispielcode auszuführen. Die Ausgabe der Beispiele sieht wie folgt aus:

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)
