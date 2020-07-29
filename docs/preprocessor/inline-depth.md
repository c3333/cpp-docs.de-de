---
title: inline_depth-Pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 73540ec19c4ecc18a740dace0d23a37ad43182c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219416"
---
# <a name="inline_depth-pragma"></a>inline_depth-Pragma

Gibt die inlineheuristische Suchtiefe an. Funktionen mit einer Tiefe im Aufruf Diagramm, die größer als der angegebene Wert sind, sind nicht Inline.

## <a name="syntax"></a>Syntax

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>Bemerkungen

Dieses Pragma steuert das Inlining von Funktionen, die als [Inline](../cpp/inline-functions-cpp.md) -und [__inline](../cpp/inline-functions-cpp.md)gekennzeichnet sind, oder wird automatisch unter der Option Inline geschaltet `/Ob` .

*n* kann ein Wert zwischen 0 und 255 sein, wobei 255 eine unbegrenzte Tiefe im Aufruf Diagramm bedeutet. Der Wert 0 hemmt die Inline Erweiterung. Wenn *n* nicht angegeben wird, wird der Standardwert 254 verwendet.

Das **inline_depth** -Pragma steuert, wie oft eine Reihe von Funktionsaufrufen erweitert werden kann. Nehmen Sie beispielsweise an, die Inline Tiefe ist 4. Wenn ein-Aufruf b aufruft und b dann C aufruft, werden alle drei Aufrufe Inline erweitert. Wenn jedoch die nächstgelegene Inline-tiefen Erweiterung 2 ist, werden nur A und B erweitert, und C bleibt als Funktions aufzurufen.

Um dieses Pragma zu verwenden, müssen Sie die- `/Ob` Compileroption auf 1 oder höher festlegen. Die bei der Verwendung dieses Pragma festgelegte Tiefe ist beim ersten Funktionsaufruf nach dem Pragma wirksam.

Die Inline Tiefe kann während der Erweiterung verringert, aber nicht gesteigert werden. Wenn die Inline Tiefe 6 ist und der Präprozessor während der Erweiterung auf ein **inline_depth** Pragma mit dem Wert 8 stößt, bleibt die Tiefe 6.

Das **inline_depth** -Pragma hat keine Auswirkungen auf Funktionen, die mit markiert sind **`__forceinline`** .

> [!NOTE]
> Rekursive Funktionen können inline in einer maximalen Tiefe von 16 Aufrufen ersetzt werden.

## <a name="see-also"></a>Weitere Informationen

[Pragma-Direktiven und das __Pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
