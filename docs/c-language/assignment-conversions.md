---
title: Zuweisungskonvertierungen
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: cc75bdd8227c09247f6d4270f1fc21235de2eb05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211839"
---
# <a name="assignment-conversions"></a>Zuweisungskonvertierungen

Bei Zuweisungsvorgängen wird der Typ des zugewiesenen Werts in den Typ der Variablen konvertiert, die die Zuweisung empfängt. C lässt Konvertierungen durch Zuweisung zwischen Ganzzahl- und Gleitkommatypen zu, auch wenn Informationen in der Konvertierung verloren gehen. Die verwendete Konvertierungsmethode hängt von den Typen ab, die an der Zuweisung beteiligt sind, wie unter [Übliche arithmetische Konvertierungen](../c-language/usual-arithmetic-conversions.md) und in den folgenden Abschnitten beschrieben:

- [Konvertierungen von integralen Typen mit Vorzeichen](../c-language/conversions-from-signed-integral-types.md)

- [Konvertierungen von integralen Typen ohne Vorzeichen](../c-language/conversions-from-unsigned-integral-types.md)

- [Konvertierungen von Gleitkommatypen](../c-language/conversions-from-floating-point-types.md)

- [Konvertierungen in und von Zeigertypen](../c-language/conversions-to-and-from-pointer-types.md)

- [Konvertierungen von anderen Typen](../c-language/conversions-from-other-types.md)

Typqualifizierer wirken sich nicht auf die Zulässigkeit der Konvertierung aus, obwohl der I-Wert **`const`** nicht auf der linken Seite der Zuweisung verwendet werden kann.

## <a name="see-also"></a>Siehe auch

[Typkonvertierungen](../c-language/type-conversions-c.md)
