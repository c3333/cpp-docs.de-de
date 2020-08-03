---
title: Inlinefunktionen
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: 5ee07dbb6cd6ea26991da588747ccbe720358326
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211813"
---
# <a name="inline-functions"></a>Inlinefunktionen

**Microsoft-spezifisch**

Das **`__inline`** -Schlüsselwort weist den Compiler an, den Code in der Funktionsdefinition für jede Instanz eines Funktionsaufrufs zu ersetzen. Die Ersetzung wird allerdings nur nach Ermessen des Compilers ausgeführt. Zum Beispiel führt der Compiler eine Funktion nicht inline aus, wenn ihre Adresse akzeptiert wird oder wenn sie für den Inlinevorgang zu groß ist.

Damit eine Funktion als Kandidat für das Inlining in Betracht gezogen werden kann, muss sie die neue Funktionsdefinition verwenden.

Verwenden Sie dieses Format, um eine Inlinefunktion anzugeben:

> **`__inline`** *Typ*<sub>opt</sub> *Funktionsdefinition*

Die Verwendung von Inlinefunktionen generiert einen schnelleren Code und kann manchmal auch kleineren Code generierten als der entsprechende Funktionsaufruf. Das hat folgende Gründe:

- Die Zeit, die erforderlich ist, um Funktionsaufrufe ausführen, wird gespart.

- Kleine Inlinefunktionen, etwa drei Zeilen oder weniger, erstellen weniger Code als der entsprechende Funktionsaufruf, da der Compiler keinen Code generiert, um Argumente und einen Rückgabewert zu behandeln.

- Inline generierte Funktionen werden Codeoptimierungen unterzogen, die für normale Funktionen nicht verfügbar sind, da der Compiler keine interprozeduralen Optimierungen durchführt.

Funktionen, die **`__inline`** verwenden, sollten nicht mit Inlineassemblercode verwechselt werden. Weitere Informationen finden Sie unter [Inlineassembler](../c-language/inline-assembler-c.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)
