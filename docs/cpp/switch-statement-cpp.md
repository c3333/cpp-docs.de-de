---
title: switch-Anweisung (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160813"
---
# <a name="switch-statement-c"></a>switch-Anweisung (C++)

Ermöglicht die Auswahl von mehreren Codeabschnitten, abhängig vom Wert eines ganzzahligen Ausdrucks.

## <a name="syntax"></a>Syntax

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Bemerkungen

Der *Ausdruck* muss einen integralen Typ oder einen Klassentyp aufweisen, für den eine eindeutige Konvertierung in einen ganzzahligen Typ vorliegt. Die ganzzahlige herauf Stufung wird wie in [Standard Konvertierungen](standard-conversions.md)beschrieben ausgeführt.

Der **Switch** -Anweisungs Text besteht aus einer Reihe von **Case** -Bezeichnungen und einer optionalen **Standard** Bezeichnung. In **Case** -Anweisungen können keine zwei Konstanten Ausdrücke zum gleichen Wert ausgewertet werden. Die **Standard** Bezeichnung kann nur ein Mal angezeigt werden. Die Anweisungen mit der Bezeichnung sind nicht syntaktische Anforderungen, aber die **Switch** -Anweisung ist ohne sie bedeutungslos.   Die default-Anweisung muss nicht am Ende stehen. Sie kann überall im Text der switch-Anweisung vorkommen. Eine case- oder default-Bezeichnung kann nur innerhalb einer switch-Anweisung angezeigt werden.

Der *constant-expression-Ausdruck* in jeder **Case** -Bezeichnung wird in den Typ des *Ausdrucks* konvertiert und mit *Expression* auf Gleichheit verglichen. Das Steuerelement wird an die Anweisung weitergeleitet, deren **Case** *Constant-Expression* mit dem Wert von *Expression*übereinstimmt. Der resultierende Verhalten wird in der folgenden Tabelle gezeigt.

### <a name="switch-statement-behavior"></a>Verhalten der switch-Anweisung

|Bedingung|Action|
|---------------|------------|
|Der konvertierte Wert stimmt mit dem des hochgestuften steuernden Ausdrucks überein.|Die Steuerung wird an die Anweisung übertragen, die auf die Bezeichnug folgt.|
|Keine der Konstanten entspricht den Konstanten in den **Case** -Bezeichnungen. Es ist eine **Standard** Bezeichnung vorhanden.|Das Steuerelement wird auf die **Standard** Bezeichnung übertragen.|
|Keine der Konstanten entspricht den Konstanten in den **Case** -Bezeichnungen. die **Standard** Bezeichnung ist nicht vorhanden.|Das Steuerelement wird an die Anweisung nach der **Switch** -Anweisung übertragen.|

Wenn ein übereinstimmender Ausdruck gefunden wird, wird das Steuerelement nicht durch nachfolgende **Case** -oder **default** -Bezeichnungen behindert. Die [break](../cpp/break-statement-cpp.md) -Anweisung wird verwendet, um die Ausführung anzuhalten und die Steuerung an die Anweisung nach der **Switch** -Anweisung zu übertragen. Ohne eine **break** -Anweisung wird jede Anweisung von der passenden **Case** -Bezeichnung bis zum Ende des **Schalters**ausgeführt, einschließlich des **Standard**mäßigen. Beispiel:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

Im obigen Beispiel wird `capa` inkrementiert, wenn `c` ein groß geschriebenes `A` ist. Die **break** -Anweisung nach `capa++` beendet die Ausführung des **Switch** -Anweisungs Texts, und das Steuerelement übergibt an die **while** -Schleife. Ohne die **break** -Anweisung würde die Ausführung auf die nächste bezeichnete Anweisung zurückgreifen, sodass `lettera` und `nota` ebenfalls inkrementiert werden. Ein ähnlicher Zweck wird von der **break** -Anweisung für `case 'a'`bereitgestellt. Wenn `c` ein Kleinbuchstabe `a`ist, wird `lettera` inkrementiert, und die **break** -Anweisung beendet den **Switch** -Anweisungs Text. Wenn `c` keine `a` oder `A`ist, wird die **default** -Anweisung ausgeführt.

**Visual Studio 2017 und höher:** (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)) das `[[fallthrough]]`-Attribut wird im c++ 17-Standard angegeben. Sie kann in einer **Switch** -Anweisung als Hinweis für den Compiler (oder für jeden, der den Code liest) verwendet werden, der durch ein durch FallThrough-Verhalten bestimmt wird. Der Microsoft C++ -Compiler warnt derzeit nicht bei einem FallThrough-Verhalten, sodass dieses Attribut keine Auswirkung auf das Compilerverhalten hat. Beachten Sie, dass das-Attribut auf eine leere Anweisung innerhalb der Anweisung mit der Bezeichnung angewendet wird. Anders ausgedrückt, ist das Semikolon erforderlich.

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

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): eine Switch-Anweisung kann eine Variable, deren Bereich auf den Block der Switch-Anweisung beschränkt ist, einführen und initialisieren:

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

Ein innerer Block einer **Switch** -Anweisung kann Definitionen mit Initialisierungen enthalten, solange Sie erreichbar sind – d. h. nicht durch alle möglichen Ausführungs Pfade umgangen werden. Namen, die mit diesen Deklarationen eingeführt werden, weisen einen lokalen Gültigkeitsbereich auf. Beispiel:

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

Eine **Switch** -Anweisung kann scht werden. In solchen Fällen werden **Case** -oder **default** -Bezeichnungen mit der nächstgelegenen **Switch** -Anweisung verknüpft, die Sie einschließt.

**Microsoft-spezifisch**

Microsoft C schränkt die Anzahl von Case-Werten in einer **Switch** -Anweisung nicht ein. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass mindestens 257 Case-Bezeichnungen in einer **Switch** -Anweisung zulässig sind.

Bei Microsoft C sind die Microsoft-Erweiterungen standardmäßig aktiviert. Verwenden Sie die [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption, um diese Erweiterungen zu deaktivieren.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
