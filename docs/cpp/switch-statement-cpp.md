---
title: switchAnweisung (C++)
description: Verweis auf die C++-Standard switch Anweisung in Microsoft Visual Studio C++.
ms.date: 04/25/2020
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
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "83389700"
---
# <a name="switch-statement-c"></a>`switch`Anweisung (C++)

Ermöglicht die Auswahl von mehreren Codeabschnitten, abhängig vom Wert eines ganzzahligen Ausdrucks.

## <a name="syntax"></a>Syntax

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Hinweise

Eine __`switch`__ -Anweisung bewirkt, dass die Steuerung abhängig vom Wert *`condition`* auf eine *`labeled-statement`* im Anweisungstext übertragen wird.

Muss einen ganzzahligen *`condition`* Typ aufweisen oder ein Klassentyp sein, der eine eindeutige Konvertierung in einen ganzzahligen Typ aufweist. Ganzzahlige herauf Stufung findet statt, wie in [Standard Konvertierungen](standard-conversions.md)beschrieben.

Der __`switch`__ Anweisungs Text besteht aus einer Reihe von __`case`__ Bezeichnungen und einer optionalen __`default`__ Bezeichnung. Eine *`labeled-statement`* ist eine dieser Bezeichnungen und die folgenden Anweisungen. Die Anweisungen mit der Bezeichnung sind nicht syntaktische Anforderungen, aber die __`switch`__ Anweisung ist ohne sie bedeutungslos. Es können nicht zwei *`constant-expression`* Werte in- __`case`__ Anweisungen zu demselben Wert ausgewertet werden. Die __`default`__ Bezeichnung wird möglicherweise nur einmal angezeigt. Die- __`default`__ Anweisung wird häufig am Ende platziert, aber Sie kann an beliebiger __`switch`__ Stelle im Anweisungs Text angezeigt werden. Eine __`case`__ - oder __`default`__ -Bezeichnung kann nur innerhalb einer __`switch`__ -Anweisung erscheinen.

Die *`constant-expression`* in jeder __`case`__ Bezeichnung wird in einen konstanten Wert konvertiert, der dem gleichen Typ wie entspricht *`condition`* . Anschließend wird es mit *`condition`* auf Gleichheit verglichen. Das Steuerelement wird an die erste Anweisung nach dem Wert weitergeleitet, der mit __`case`__ *`constant-expression`* dem Wert von übereinstimmt *`condition`* . Der resultierende Verhalten wird in der folgenden Tabelle gezeigt.

### <a name="switch-statement-behavior"></a>`switch`Anweisungs Verhalten

| Bedingung | Aktion |
|--|--|
| Der konvertierte Wert stimmt mit dem des hochgestuften steuernden Ausdrucks überein. | Die Steuerung wird an die Anweisung übertragen, die auf die Bezeichnug folgt. |
| Keine der Konstanten entspricht den Konstanten in den __`case`__ Bezeichnungen __`default`__ . eine Bezeichnung ist vorhanden. | Das Steuerelement wird an die Bezeichnung übertragen __`default`__ . |
| Keine der Konstanten entspricht den Konstanten in den __`case`__ Bezeichnungen __`default`__ . es ist keine Bezeichnung vorhanden. | Das Steuerelement wird an die Anweisung nach der-Anweisung übertragen __`switch`__ . |

Wenn ein übereinstimmender Ausdruck gefunden wird, kann die Ausführung bis zu einem späteren Zeitpunkt fortgesetzt werden __`case`__ __`default`__ . Die [`break`](../cpp/break-statement-cpp.md) -Anweisung wird verwendet, um die Ausführung anzuhalten und die Steuerung an die Anweisung nach der-Anweisung zu übertragen __`switch`__ . Ohne eine- __`break`__ Anweisung wird jede Anweisung der übereinstimmenden __`case`__ Bezeichnung bis zum Ende der __`switch`__ ausgeführt, einschließlich der-Anweisung __`default`__ . Beispiel:

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

Im obigen Beispiel wird `uppercase_A` inkrementiert, wenn `c` ein groß geschriebenes `'A'` ist. Die __`break`__ -Anweisung nach `uppercase_A++` beendet die Ausführung des __`switch`__ Anweisungs Texts, und die Steuerung wird an die-Schleife weitergeleitet __`while`__ . Ohne die __`break`__ -Anweisung würde die Ausführung auf die nächste bezeichnete Anweisung zurückgreifen, sodass `lowercase_a` und `other` ebenfalls inkrementiert werden. Ein ähnlicher Zweck wird von der- __`break`__ Anweisung für bereitgestellt `case 'a'` . Wenn `c` ein Kleinbuchstabe ist `'a'` , `lowercase_a` wird inkrementiert, und die- __`break`__ Anweisung beendet den __`switch`__ Anweisungs Text. Wenn kein `c` `'a'` oder ist `'A'` , wird die- __`default`__ Anweisung ausgeführt.

**Visual Studio 2017 und höher:** (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)) das- `[[fallthrough]]` Attribut wird im c++ 17-Standard angegeben. Sie können Sie in einer- __`switch`__ Anweisung verwenden. Es ist ein Hinweis für den Compiler, oder jeder, der den Code liest, ist beabsichtigt. Der Microsoft C++-Compiler warnt zurzeit nicht bei einem FallThrough-Verhalten, sodass dieses Attribut keine Auswirkung auf das Compilerverhalten hat. Im Beispiel wird das-Attribut auf eine leere-Anweisung innerhalb der nicht abgeschlossenen Anweisung mit der Bezeichnung angewendet. Das heißt, dass das Semikolon erforderlich ist.

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

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)). Eine- __`switch`__ Anweisung kann eine- *`init-statement`* Klausel enthalten, die mit einem Semikolon endet. Es wird eine Variable eingeführt und initialisiert, deren Bereich auf den Block der Anweisung beschränkt ist __`switch`__ :

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

Ein innerer Block einer- __`switch`__ Anweisung kann Definitionen mit Initialisierern enthalten, solange Sie *erreichbar*sind, d. h. nicht durch alle möglichen Ausführungs Pfade umgangen werden. Namen, die mit diesen Deklarationen eingeführt werden, weisen einen lokalen Gültigkeitsbereich auf. Beispiel:

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

Eine- __`switch`__ Anweisung kann eingefügt werden. Beim Einfügen werden die- __`case`__ oder- __`default`__ Bezeichnungen mit der nächstgelegenen Anweisung verknüpft, __`switch`__ die Sie einschließt.

### <a name="microsoft-specific-behavior"></a>Microsoft-spezifisches Verhalten

Microsoft C++ beschränkt die Anzahl der __`case`__ Werte in einer- __`switch`__ Anweisung nicht. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt.

## <a name="see-also"></a>Siehe auch

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
