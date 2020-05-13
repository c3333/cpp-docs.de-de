---
title: Typ für Zeichenfolgenliterale
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 7e832ac7aa08ad80ab395baa59eabbabb486b46f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344849"
---
# <a name="type-for-string-literals"></a>Typ für Zeichenfolgenliterale

Zeichenfolgenliterale haben ein Typarray von `char` (d.h. **char[ ]** ). (Breitzeichenzeichenfolgen haben ein Typarray von `wchar_t` (d.h. **wchar_t[ ]** ).) Dies bedeutet, dass eine Zeichenfolge ein Array mit Elementen vom Typ `char` ist. Die Anzahl der Elemente im Array entspricht der Anzahl von Zeichen in der Zeichenfolge plus einem beendenden Null-Zeichen.

## <a name="see-also"></a>Siehe auch

[C-Zeichenfolgenliterale](../c-language/c-string-literals.md)
