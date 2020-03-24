---
title: Übersicht über C++-Anweisungen
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9aba5deddca6fbf480cd9d573606b16b7ab047db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188427"
---
# <a name="overview-of-c-statements"></a>Übersicht über C++-Anweisungen

C++-Anweisungen werden nacheinander ausgeführt, außer wenn diese Sequenz von einer Ausdrucksanweisung, einer Selektionsanweisung, einer Iterationsanweisung oder einer Sprunganweisung speziell geändert wird.

Anweisungen können folgende Typen aufweisen:

```
labeled-statement
expression-statement
compound-statement
selection-statement
iteration-statement
jump-statement
declaration-statement
try-throw-catch
```

In den meisten Fällen ist C++ die-Anweisungs Syntax mit der von ANSI C identisch. Der Hauptunterschied zwischen den beiden besteht darin, dass Deklarationen in C nur am Anfang eines-Blocks zulässig sind. C++ fügt die *Deklaration-Anweisung*hinzu, wodurch diese Einschränkung effektiv entfernt wird. Dadurch können Sie Variablen an einem Punkt im Programm einführen, an dem ein vorausberechneter Initialisierungswert berechnet werden kann.

Das Deklarieren von Variablen innerhalb von Blöcken ermöglicht Ihnen auch die genaue Steuerung des Gültigkeitsbereichs und der Lebensdauer dieser Variablen.

Die Anweisungsthemen beschreiben die folgenden C++-Schlüsselwörter:

|||||
|-|-|-|-|
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[Standardwert](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>Weitere Informationen

[Anweisungen](../cpp/statements-cpp.md)
