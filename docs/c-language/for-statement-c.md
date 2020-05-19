---
title: for-Anweisung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233643"
---
# <a name="for-statement-c"></a>for-Anweisung (C)

Mit der **for**-Anweisung können Sie eine Anweisung oder eine Verbundanweisung so häufig wie angegeben wiederholen. Der Text einer **for**-Anweisung wird nicht oder mehrmals ausgeführt, bis eine optionale Bedingung falsch ist. Sie können optionale Ausdrücke in der **for**-Anweisung verwenden, um Werte während der Ausführung der **for**-Anweisung zu initialisieren und zu ändern.

## <a name="syntax"></a>Syntax

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *Initialisierungsausdruck*<sub>opt</sub> **;** *Bedingungsausdruck*<sub>opt</sub> **;** *Schleifenausdruck*<sub>opt</sub> **)** *Anweisung*

Eine **for**-Anweisung wird wie folgt ausgeführt:

1. *init-expression* wird ausgewertet, falls vorhanden. Dadurch wird die Initialisierung für die Schleife angegeben. Für den Typ *init-expression* besteht keine Einschränkung.

1. *cond-expression* wird ausgewertet, falls vorhanden. Dieser Ausdruck muss einen arithmetischen Typ oder einen Zeigertyp aufweisen. Er wird vor jeder Iteration ausgewertet. Drei Ergebnisse sind möglich:

   - Wenn *cond-expression***TRUE** ist (ungleich 0), wird *statement* ausgeführt; anschließend wird *loop-expression* ausgeführt, falls vorhanden. *loop-expression* wird nach dem Abschluss jeder Iteration ausgewertet. Für den zugehörigen Typ besteht keine Einschränkung. Nebeneffekte werden in der Reihenfolge ausgeführt. Der Prozess beginnt anschließend erneut mit der Auswertung von *cond-expression*.

   - Wenn *cond-expression* weggelassen wird, gilt *cond-expression* dennoch als „TRUE“, und die Ausführung wird genau wie im vorherigen Absatz beschrieben fortgesetzt. Eine **for**-Anweisung ohne ein *cond-expression*-Argument wird nur beendet, wenn eine **break**- oder **return**-Anweisung innerhalb des Anweisungstexts ausgeführt wird, oder wenn **goto** (eine Anweisung mit Bezeichnung außerhalb des **for**-Anweisungstexts) ausgeführt wird.

   - Wenn *cond-expression***FALSE** ist (0), wird die **for**-Anweisung beendet und das Steuerelement an die nächste Anweisung im Programm weitergegeben.

Die **for**-Anweisung kann auch beendet werden, wenn eine **break**-, eine **goto**- oder eine **return**-Anweisung innerhalb des Anweisungstexts ausgeführt wird. Eine **continue**-Anweisung in einer **for**-Schleife führt zur Auswertung von *loop-expression*. Wenn eine **break**-Anweisung innerhalb einer **for**-Schleife ausgeführt wird, wird *loop-expression* weder ausgewertet noch ausgeführt. Diese Anweisung

```C
for( ; ; )
```

ist die übliche Methode zum Erstellen einer Endlosschleife, die nur mit einer **break**-, **goto**- oder **return**-Anweisung beendet werden kann.

## <a name="example"></a>Beispiel

In diesem Beispiel wird die **for**-Anweisung veranschaulicht:

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Output

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)
