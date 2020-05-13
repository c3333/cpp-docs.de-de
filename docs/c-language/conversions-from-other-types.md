---
title: Konvertierungen von anderen Typen
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312465"
---
# <a name="conversions-from-other-types"></a>Konvertierungen von anderen Typen

Da ein **enum**-Wert definitionsgemäß ein **int**-Wert ist, sind Konvertierungen aus und in einen **enum**-Wert identisch mit denen für den Typ **int**. Für den Microsoft C-Compiler entspricht eine Ganzzahl **long**.

**Microsoft-spezifisch**

Es sind keine Konvertierungen zwischen Struktur- oder Union-Typen zulässig.

Jeder Wert kann in den Typ **void** konvertiert werden, aber das Ergebnis einer solchen Konvertierung kann nur in einem Kontext verwendet werden, in dem ein Ausdruckswert verworfen wird, z.B. in einer Ausdrucksanweisung.

Der **void**-Typ hat definitionsgemäß keinen Wert. Daher kann er nicht in einen anderen Typ konvertiert werden, und andere Typen können nicht durch Zuweisung in **void** konvertiert werden. Sie können jedoch explizit einen Wert in den Typ **void** umwandeln, wie in [Typumwandlungskonvertierungen](../c-language/type-cast-conversions.md) erläutert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
