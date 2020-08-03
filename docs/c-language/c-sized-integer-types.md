---
title: C-Ganzzahltypen (angepasst)
ms.date: 07/22/2020
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 7f785efb2fc93d2ec57783dd20a43642c87e4a4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226502"
---
# <a name="c-sized-integer-types"></a>C-Ganzzahltypen (angepasst)

**Microsoft-spezifisch**

Microsoft C bietet Unterstützung für ganzzahlige Typen mit angegebener Größe. Sie können 8, 16, 32 oder 64 Bit große ganzzahlige Variablen deklarieren, indem Sie den Typspezifizierer `__intN` verwenden, wobei *`N`* die Größe der ganzzahligen Variable (in Bit) ist. Der Wert von *n* kann 8, 16, 32 oder 64 sein. Im folgenden Beispiel wird eine Variable für jeden der vier Typen der nach Größe angepassten Ganzzahlen deklariert:

```C
__int8  nSmall;     // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Die ersten drei Typen von Ganzzahlen mit festgelegter Größe sind Synonyme für die ANSI-Typen der entsprechenden Größe. Sie sind nützlich beim Erstellen von portierbarem Code, der sich auf verschiedenen Plattformen gleich verhält. Der Datentyp **`__int8`** entspricht dem Typ **`char`** , **`__int16`** dem Typ **`short`** , **`__int32`** dem Typ **`int`** und **`__int64`** dem Typ **`long long`** .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Speicherung von einfachen Typen](../c-language/storage-of-basic-types.md)
