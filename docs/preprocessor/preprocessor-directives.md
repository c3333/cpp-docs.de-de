---
title: Präprozessordirektiven
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: ac765d33aec4795e94866c097d6c453dbd0e4a08
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845327"
---
# <a name="preprocessor-directives"></a>Präprozessordirektiven

Präprozessordirektiven, wie z. b. `#define` und, `#ifdef` werden in der Regel verwendet, um das ändern und Kompilieren von Quell Programmen in verschiedenen Ausführungs Umgebungen zu vereinfachen. Anweisungen in der Quelldatei weisen den Präprozessor an, bestimmte Aktionen auszuführen. Beispielsweise kann der Präprozessor Token im Text ersetzen, den Inhalt von anderen Dateien in die Quelldatei einfügen oder die Kompilierung eines Teils der Datei unterdrücken, indem er Textabschnitte entfernt. Präprozessorzeilen werden vor der Makroerweiterung erkannt und ausgeführt. Wenn ein Makro in etwas, das wie ein Präprozessorbefehl aussieht, erweitert wird, wird es daher vom Präprozessor nicht erkannt.

Präprozessoranweisungen verwenden den gleichen Zeichensatz wie Quelldatei Anweisungen, mit der Ausnahme, dass Escapesequenzen nicht unterstützt werden. Der Zeichensatz, der in Präprozessoranweisungen verwendet wird, ist mit dem Ausführungszeichensatz identisch. Der Präprozessor erkennt auch negative Zeichenwerte.

Der Präprozessor erkennt die folgenden Direktiven:

:::row:::
   :::column span="":::
      [`#define`](../preprocessor/hash-define-directive-c-cpp.md)\
      [`#elif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#else`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#endif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#error`](../preprocessor/hash-error-directive-c-cpp.md)\
      [`#if`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#ifdef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)\
      [`#ifndef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#import`](../preprocessor/hash-import-directive-cpp.md)\
      [`#include`](../preprocessor/hash-include-directive-c-cpp.md)\
      [`#line`](../preprocessor/hash-line-directive-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#pragma`](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
      [`#undef`](../preprocessor/hash-undef-directive-c-cpp.md)\
      [`#using`](../preprocessor/hash-using-directive-cpp.md)
   :::column-end:::
:::row-end:::

Das Nummern Zeichen ( `#` ) muss das erste nicht-Leerzeichen in der Zeile sein, die die Direktive enthält. Leerzeichen können zwischen dem Nummern Zeichen und dem ersten Buchstaben der Direktive angezeigt werden. Manche Anweisungen enthalten Argumente oder Werte. Jedem Text, der auf eine Direktive folgt (außer einem Argument oder einem Wert, der Teil der Anweisung ist), muss das einzeilige Kommentar Trennzeichen () vorangestellt `//` oder in Kommentar Trennzeichen () eingeschlossen werden `/* */` . Zeilen, die Präprozessordirektiven enthalten, können fortgesetzt werden, indem der zeitzeiendemarker mit einem umgekehrten Schrägstrich () unmittelbar vorangestellt wird `\` .

Präprozessordirektiven können an beliebiger Stelle in einer Quelldatei vorkommen, Sie gelten jedoch nur für den Rest der Quelldatei, nachdem Sie angezeigt wurden.

## <a name="see-also"></a>Weitere Informationen

[Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)\
[Vordefinierte Makros](../preprocessor/predefined-macros.md)\
[c/c++-präprozessorverweis](../preprocessor/c-cpp-preprocessor-reference.md)
