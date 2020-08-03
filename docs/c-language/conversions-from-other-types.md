---
title: Konvertierungen von anderen Typen
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: bd00bbb8944a0273163fa0c5952be510c9dd697c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200334"
---
# <a name="conversions-from-other-types"></a>Konvertierungen von anderen Typen

Da ein **`enum`** -Wert definitionsgemäß ein **`int`** -Wert ist, sind Konvertierungen aus einem und in einen **`enum`** -Wert identisch mit denen für den Typ **`int`** . Für den Microsoft C-Compiler entspricht eine ganze Zahl einem Wert vom Typ **`long`** .

**Microsoft-spezifisch**

Es sind keine Konvertierungen zwischen Struktur- oder Union-Typen zulässig.

Jeder Wert kann in den Typ **`void`** konvertiert werden, aber das Ergebnis einer solchen Konvertierung kann nur in einem Kontext verwendet werden, in dem ein Ausdruckswert verworfen wird, z. B. in einer Ausdrucksanweisung.

Der Typ **`void`** verfügt definitionsgemäß über keinen Wert. Daher kann er nicht in einen anderen Typ konvertiert werden, und andere Typen können nicht durch Zuweisung in **`void`** konvertiert werden. Sie können jedoch explizit einen Wert in den Typ **`void`** umwandeln, wie in [Typumwandlungskonvertierungen](../c-language/type-cast-conversions.md) erläutert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
