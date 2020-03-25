---
title: Iterationsanweisungen (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: e8f064fd19e69de2819673f48a7f14e26d60b87e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178254"
---
# <a name="iteration-statements-c"></a>Iterationsanweisungen (C++)

Iterationsanweisungen bewirken, dass Anweisungen (oder Verbundanweisungen) NULL mal oder mehrmals ausgeführt werden, je nach LOOP-Beendigungskriterien. Wenn diese Anweisungen Verbund Anweisungen sind, werden Sie in der angegebenen Reihenfolge ausgeführt, es sei denn, die [break](../cpp/break-statement-cpp.md) -Anweisung oder die [Continue](../cpp/continue-statement-cpp.md) -Anweisung ist aufgetreten.

C++bietet vier Iterations Anweisungen – [while](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)und [Range-based for](../cpp/range-based-for-statement-cpp.md). Jede dieser Iteration durchläuft, bis der Beendigungs Ausdruck NULL (false) ergibt, oder bis die Beendigung der Schleife mit einer **break** -Anweisung erzwungen wird. In der folgenden Tabelle werden diese Anweisungen und ihre Aktionen zusammengefasst. Jede von ihnen wird in den folgenden Abschnitten im Detail behandelt.

### <a name="iteration-statements"></a>Iterationsanweisungen

|-Anweisung.|Ausgewertet an|Initialisierung|Increment|
|---------------|------------------|--------------------|---------------|
|**while**|Anfang der Schleife|Nein|Nein|
|**do**|Ende der Schleife|Nein|Nein|
|**for**|Anfang der Schleife|Ja|Ja|
|**Bereichs basiert für**|Anfang der Schleife|Ja|Ja|

Der Anweisungsteil einer Iterationsanweisung kann keine Deklaration sein. Es kann jedoch eine Verbundanweisung sein, die eine Deklaration enthält.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über C++-Anweisungen](../cpp/overview-of-cpp-statements.md)
