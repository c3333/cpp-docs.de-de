---
title: switchAnweisung (C++)
description: Verweis auf die Standard-C++-Anweisung switch in Microsoft Visual Studio C++.
ms.date: 04/15/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480824"
---
# <a name="opno-locswitch-statement-c"></a>switchAnweisung (C++)

Ermöglicht die Auswahl von mehreren Codeabschnitten, abhängig vom Wert eines ganzzahligen Ausdrucks.

## <a name="syntax"></a>Syntax

> **`switch (`**\[ *Initialisierung* **`;`**] *Ausdruck***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***Constant-Expression-Anweisung* **`:`** *statement*\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***Anweisung*] \
> **`}`**

## <a name="remarks"></a>Bemerkungen

Der *Ausdruck* muss einen integralen Typ haben oder ein Klassentyp sein, der eine eindeutige Konvertierung in integralen Typ hat. Die integrale Förderung findet wie in [Standardkonvertierungen](standard-conversions.md)beschrieben statt.

Der **switch** Anweisungstext besteht **case** aus einer **default** Reihe von Etiketten und einem optionalen Etikett. Zusammen genommen werden die Anweisungen, die den Bezeichnungen folgen, *als beschriftete* Anweisungen bezeichnet. Die beschrifteten Anweisungen sind keine syntaktischen Anforderungen, aber die **switch** Anweisung ist ohne sie bedeutungslos. Es dürfen keine **case** zwei konstanten Ausdrücke in Anweisungen auf denselben Wert ausgewertet werden. Die **default** Bezeichnung darf nur einmal angezeigt werden. Die **default** Anweisung wird oft am Ende platziert, kann aber **switch** an einer beliebigen Stelle im Textkörper der Anweisung angezeigt werden. Eine **case** **default** oder Bezeichnung kann **switch** nur in einer Anweisung angezeigt werden.

Der *Konstantenausdruck* **case** in jeder Beschriftung wird in den *Ausdruckstyp*konvertiert. Dann wird es mit *dem Ausdruck* für Gleichheit verglichen. Die Steuerung wird **case** an die Anweisung übergibt, deren *Konstantenausdruck* mit dem Wert des *Ausdrucks*übereinstimmt. Der resultierende Verhalten wird in der folgenden Tabelle gezeigt.

### <a name="switch-statement-behavior"></a>Switch-Anweisungsverhalten

| Bedingung | Aktion |
|--|--|
| Der konvertierte Wert stimmt mit dem des hochgestuften steuernden Ausdrucks überein. | Die Steuerung wird an die Anweisung übertragen, die auf die Bezeichnug folgt. |
| Keine der Konstanten stimmt mit **case** den Konstanten in den Beschriftungen überein. ein **default** Etikett vorhanden ist. | Die Steuerung wird **default** auf das Etikett übertragen. |
| Keine der Konstanten stimmt mit **case** den Konstanten in den Beschriftungen überein. es **default** ist kein Etikett vorhanden. | Die Steuerung wird nach **switch** der Anweisung in die Anweisung übertragen. |

Wenn ein übereinstimmender Ausdruck gefunden wird, kann die Ausführung später **case** oder **default** durch Beschriftungen fortgesetzt werden. Die [`break`](../cpp/break-statement-cpp.md) Anweisung wird verwendet, um die Ausführung **switch** und Übertragung der Steuerung auf die Anweisung nach der Anweisung zu beenden. Ohne **break** Anweisung wird jede Anweisung **case** von der übereinstimmenden Bezeichnung bis zum Ende des **switch** ausgeführt, einschließlich der **default**. Beispiel:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

Im obigen Beispiel wird `uppercase_A` inkrementiert, wenn `c` ein groß geschriebenes `'A'` ist. Die **break** Anweisung `uppercase_A++` nach beendet **switch** die Ausführung des Anweisungstexts, und die Steuerung wird an die **while** Schleife übergeben. Ohne **break** die Anweisung würde die Ausführung zur nächsten beschrifteten Anweisung "durchfallen", so dass `lowercase_a` und `other` auch erhöht würde. Einem ähnlichen Zweck dient **break** die `case 'a'`Anweisung für . Wenn `c` es sich `'a'` `lowercase_a` um einen Kleinbuchstaben handelt, wird die Anweisung erhöht, und die **break** Anweisung beendet den **switch** Anweisungstext. Wenn `c` es sich `'a'` nicht `'A'`um **default** ein oder handelt, wird die Anweisung ausgeführt.

**Visual Studio 2017 und höher:** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)) Das `[[fallthrough]]` Attribut wird im C++17-Standard angegeben. Sie können es **switch** in einer Anweisung verwenden. Es ist ein Hinweis an den Compiler oder jeden, der den Code liest, dass Fall-Through-Verhalten absichtlich ist. Der Microsoft C++-Compiler warnt derzeit nicht vor Fallthrough-Verhalten, sodass dieses Attribut keine Auswirkungen auf das Compilerverhalten hat. Im Beispiel wird das Attribut auf eine leere Anweisung innerhalb der nicht beendeten beschrifteten Anweisung angewendet. Mit anderen Worten, das Semikolon ist notwendig.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 Version 15.3 und höher** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)). Eine switch Anweisung kann über eine *Initialisierungsklausel* verfügen. Es wird eine Variable eingeführt und initialisiert, deren Bereich auf den Block der switch Anweisung beschränkt ist:

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

Ein innerer **switch** Block einer Anweisung kann Definitionen mit Initialisierungen enthalten, solange sie *erreichbar*sind, d. h. nicht von allen möglichen Ausführungspfaden umgangen werden. Namen, die mit diesen Deklarationen eingeführt werden, weisen einen lokalen Gültigkeitsbereich auf. Beispiel:

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

Eine **switch** Anweisung kann geschachtelt werden. Wenn sie geschachtelt sind, wird die **case** oder **default** Beschriftungen mit der nächstgelegenen **switch** Anweisung, die sie einschließt, in Verbindung gebracht.

### <a name="microsoft-specific-behavior"></a>Microsoft-spezifisches Verhalten

Microsoft C beschränkt die Anzahl **case** der **switch** Werte in einer Anweisung nicht. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass **case** mindestens 257 Beschriftungen in einer **switch** Anweisung zulässig sind.

Für default Microsoft C sind die Microsoft-Erweiterungen aktiviert. Verwenden Sie die Compileroption [/Za,](../build/reference/za-ze-disable-language-extensions.md) um diese Erweiterungen zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
