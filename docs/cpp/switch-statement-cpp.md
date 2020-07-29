---
title: :::no-loc(switch):::Anweisung (C++)
description: 'Verweis auf die C++-Standard :::no-loc(switch)::: Anweisung in Microsoft Visual Studio C++.'
ms.date: 04/25/2020
f1_keywords:
- :::no-loc(default):::_cpp
- :::no-loc(switch):::_cpp
- :::no-loc(case):::_cpp
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C++]'
- ':::no-loc(case)::: keyword [C++], in :::no-loc(switch)::: statements'
- ':::no-loc(default)::: keyword [C++]'
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
- ':::no-loc(while):::'
- ':::no-loc(opt):::'
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d71989b6d8af0213c4cd6d4fbd8d5a84b318701a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223589"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`Anweisung (C++)

Ermöglicht die Auswahl von mehreren Codeabschnitten, abhängig vom Wert eines ganzzahligen Ausdrucks.

## <a name="syntax"></a>Syntax

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;**`:::no-loc(switch):::`**&nbsp;**`(`**&nbsp;*`init-statement`*<sub>:::no-loc(opt):::</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;**`)`**&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>:::no-loc(opt):::</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Hinweise

Eine **`:::no-loc(switch):::`** -Anweisung bewirkt, dass die Steuerung abhängig vom Wert *`condition`* auf eine *`labeled-statement`* im Anweisungstext übertragen wird.

Muss einen ganzzahligen *`condition`* Typ aufweisen oder ein Klassentyp sein, der eine eindeutige Konvertierung in einen ganzzahligen Typ aufweist. Ganzzahlige herauf Stufung findet statt, wie in [Standard Konvertierungen](standard-conversions.md)beschrieben.

Der **`:::no-loc(switch):::`** Anweisungs Text besteht aus einer Reihe von **`:::no-loc(case):::`** Bezeichnungen und einer :::no-loc(opt)::: ional- **`:::no-loc(default):::`** Bezeichnung. Eine *`labeled-statement`* ist eine dieser Bezeichnungen und die folgenden Anweisungen. Die Anweisungen mit der Bezeichnung sind nicht syntaktische Anforderungen, aber die **`:::no-loc(switch):::`** Anweisung ist ohne sie bedeutungslos. Es können nicht zwei *`constant-expression`* Werte in- **`:::no-loc(case):::`** Anweisungen zu demselben Wert ausgewertet werden. Die **`:::no-loc(default):::`** Bezeichnung wird möglicherweise nur einmal angezeigt. Die- **`:::no-loc(default):::`** Anweisung wird häufig am Ende platziert, aber Sie kann an beliebiger **`:::no-loc(switch):::`** Stelle im Anweisungs Text angezeigt werden. Eine **`:::no-loc(case):::`** - oder **`:::no-loc(default):::`** -Bezeichnung kann nur innerhalb einer **`:::no-loc(switch):::`** -Anweisung erscheinen.

Die *`constant-expression`* in jeder **`:::no-loc(case):::`** Bezeichnung wird in einen konstanten Wert konvertiert, der dem gleichen Typ wie entspricht *`condition`* . Anschließend wird es mit *`condition`* auf Gleichheit verglichen. Das Steuerelement wird an die erste Anweisung nach dem Wert weitergeleitet, der mit **`:::no-loc(case):::`** *`constant-expression`* dem Wert von übereinstimmt *`condition`* . Der resultierende Verhalten wird in der folgenden Tabelle gezeigt.

### <a name="no-locswitch-statement-behavior"></a>`:::no-loc(switch):::`Anweisungs Verhalten

| Bedingung | Aktion |
|--|--|
| Der konvertierte Wert stimmt mit dem des hochgestuften steuernden Ausdrucks überein. | Die Steuerung wird an die Anweisung übertragen, die auf die Bezeichnug folgt. |
| Keine der Konstanten entspricht den Konstanten in den **`:::no-loc(case):::`** Bezeichnungen **`:::no-loc(default):::`** . eine Bezeichnung ist vorhanden. | Das Steuerelement wird an die Bezeichnung übertragen **`:::no-loc(default):::`** . |
| Keine der Konstanten entspricht den Konstanten in den **`:::no-loc(case):::`** Bezeichnungen **`:::no-loc(default):::`** . es ist keine Bezeichnung vorhanden. | Das Steuerelement wird an die Anweisung nach der-Anweisung übertragen **`:::no-loc(switch):::`** . |

Wenn ein übereinstimmender Ausdruck gefunden wird, kann die Ausführung bis zu einem späteren Zeitpunkt fortgesetzt werden **`:::no-loc(case):::`** **`:::no-loc(default):::`** . Die [`:::no-loc(break):::`](../cpp/:::no-loc(break):::-statement-cpp.md) -Anweisung wird verwendet, um die Ausführung anzuhalten und die Steuerung an die Anweisung nach der-Anweisung zu übertragen **`:::no-loc(switch):::`** . Ohne eine- **`:::no-loc(break):::`** Anweisung wird jede Anweisung der übereinstimmenden **`:::no-loc(case):::`** Bezeichnung bis zum Ende der **`:::no-loc(switch):::`** ausgeführt, einschließlich der-Anweisung **`:::no-loc(default):::`** . Beispiel:

```cpp
// :::no-loc(switch):::_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, other;
   char c;
   upper:::no-loc(case):::_A = lower:::no-loc(case):::_a = other = 0;

   :::no-loc(while)::: ( c = *buffer++ )   // Walks buffer until NULL
   {
      :::no-loc(switch)::: ( c )
      {
         :::no-loc(case)::: 'A':
            upper:::no-loc(case):::_A++;
            :::no-loc(break):::;
         :::no-loc(case)::: 'a':
            lower:::no-loc(case):::_a++;
            :::no-loc(break):::;
         :::no-loc(default)::::
            other++;
      }
   }
   printf_s( "\nUpper:::no-loc(case)::: A: %d\nLower:::no-loc(case)::: a: %d\nTotal: %d\n",
      upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, (upper:::no-loc(case):::_A + lower:::no-loc(case):::_a + other) );
}
```

Im obigen Beispiel `upper:::no-loc(case):::_A` wird inkrementiert, wenn `c` ein oberer Wert ist :::no-loc(case)::: `'A'` . Die **`:::no-loc(break):::`** -Anweisung nach `upper:::no-loc(case):::_A++` beendet die Ausführung des **`:::no-loc(switch):::`** Anweisungs Texts, und die Steuerung wird an die-Schleife weitergeleitet **`:::no-loc(while):::`** . Ohne die **`:::no-loc(break):::`** -Anweisung würde die Ausführung auf die nächste bezeichnete Anweisung zurückgreifen, sodass `lower:::no-loc(case):::_a` und `other` ebenfalls inkrementiert werden. Ein ähnlicher Zweck wird von der- **`:::no-loc(break):::`** Anweisung für bereitgestellt `:::no-loc(case)::: 'a'` . Wenn `c` ein niedrigerer Wert ist :::no-loc(case)::: `'a'` , `lower:::no-loc(case):::_a` wird inkrementiert, und die- **`:::no-loc(break):::`** Anweisung beendet den **`:::no-loc(switch):::`** Anweisungs Text. Wenn kein `c` `'a'` oder ist `'A'` , wird die- **`:::no-loc(default):::`** Anweisung ausgeführt.

**Visual Studio 2017 und höher:** (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)) das- `[[fallthrough]]` Attribut wird im c++ 17-Standard angegeben. Sie können Sie in einer- **`:::no-loc(switch):::`** Anweisung verwenden. Es ist ein Hinweis für den Compiler, oder jeder, der den Code liest, ist beabsichtigt. Der Microsoft C++-Compiler warnt zurzeit nicht bei einem FallThrough-Verhalten, sodass dieses Attribut keine Auswirkung auf das Compilerverhalten hat. Im Beispiel wird das-Attribut auf eine leere-Anweisung innerhalb der nicht abgeschlossenen Anweisung mit der Bezeichnung angewendet. Das heißt, dass das Semikolon erforderlich ist.

```cpp
int main()
{
    int n = 5;
    :::no-loc(switch)::: (n)
    {

    :::no-loc(case)::: 1:
        a();
        :::no-loc(break):::;
    :::no-loc(case)::: 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    :::no-loc(case)::: 3:
        c();
        :::no-loc(break):::;
    :::no-loc(default)::::
        d();
        :::no-loc(break):::;
    }

    return 0;
}
```

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)). Eine- **`:::no-loc(switch):::`** Anweisung kann eine- *`init-statement`* Klausel enthalten, die mit einem Semikolon endet. Es wird eine Variable eingeführt und initialisiert, deren Bereich auf den Block der Anweisung beschränkt ist **`:::no-loc(switch):::`** :

```cpp
    :::no-loc(switch)::: (Gadget gadget(args); auto s = gadget.get_status())
    {
    :::no-loc(case)::: status::good:
        gadget.zip();
        :::no-loc(break):::;
    :::no-loc(case)::: status::bad:
        throw BadGadget();
    };
```

Ein innerer Block einer- **`:::no-loc(switch):::`** Anweisung kann Definitionen mit Initialisierern enthalten, solange Sie *erreichbar*sind, d. h. nicht durch alle möglichen Ausführungs Pfade umgangen werden. Namen, die mit diesen Deklarationen eingeführt werden, weisen einen lokalen Gültigkeitsbereich auf. Beispiel:

```cpp
// :::no-loc(switch):::_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    :::no-loc(switch):::( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    :::no-loc(case)::: 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        :::no-loc(break):::;

    :::no-loc(case)::: 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        :::no-loc(break):::;

    :::no-loc(default)::::
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        :::no-loc(break):::;
    }
}
```

Eine- **`:::no-loc(switch):::`** Anweisung kann eingefügt werden. Beim Einfügen werden die- **`:::no-loc(case):::`** oder- **`:::no-loc(default):::`** Bezeichnungen mit der nächstgelegenen Anweisung verknüpft, **`:::no-loc(switch):::`** die Sie einschließt.

### <a name="microsoft-specific-behavior"></a>Microsoft-spezifisches Verhalten

Microsoft C++ beschränkt die Anzahl der **`:::no-loc(case):::`** Werte in einer- **`:::no-loc(switch):::`** Anweisung nicht. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt.

## <a name="see-also"></a>Siehe auch

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
