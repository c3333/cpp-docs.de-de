---
title: Typ "int"
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 2bfd9e108b36f073635c6d9e55e2299764dcb309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198865"
---
# <a name="type-int"></a>Typ "int"

Die Größe eines **`signed int`** - oder **`unsigned int`** -Elements entspricht der Standardgröße eines Integers auf einem bestimmten Computer. Bei 16-Bit-Betriebssystemen entspricht der Typ **`int`** beispielsweise in der Regel 16 Bits oder 2 Bytes. Bei 32-Bit-Betriebssystemen entspricht der Typ **`int`** in der Regel 32 Bits oder 4 Bytes. Daher entspricht der Typ **`int`** entweder dem Typ **`short int`** oder **`long int`** , und der Typ **`unsigned int`** ist mit dem Typ **`unsigned short`** oder **`unsigned long`** identisch, abhängig von der Zielumgebung. Alle **`int`** -Typen stellen signierte Werte dar, es sei denn, eine andere Bezeichnung liegt vor.

Die Typspezifizierer **`int`** und **`unsigned int`** (oder einfach **`unsigned`** ) definieren bestimmte Features der C-Sprache (z. B. den Typ **`enum`** ). In diesen Fällen bestimmen die Definitionen von **`int`** und **`unsigned int`** den tatsächlichen Speicher für eine bestimmte Implementierung.

**Microsoft-spezifisch**

Ganzzahlen mit Vorzeichen werden in der Zweierkomplementdarstellung ausgedrückt. Das wichtigste Bit enthält das Vorzeichen: 1 für negative Werte, 0 für positive Werte und 0. Der Wertebereich ist unter [Integer-Grenzwerte in C und C++](../c-language/cpp-integer-limits.md) angegeben und stammt aus der LIMITS.H-Headerdatei.

**Ende Microsoft-spezifisch**

> [!NOTE]
> Die Typspezifizierer **`int`** und **`unsigned int`** werden häufig in C-Programmen verwendet, weil sie einem bestimmten Computer das Verarbeiten von Integerwerten auf die für den jeweiligen Computer effizienteste Weise ermöglichen. Da die Größen der **`int`** - und **`unsigned int`** -Typen jedoch variieren, sind Programme, die von einer spezifischen **`int`** -Größe abhängig sind, möglicherweise nicht auf andere Computer übertragbar. Sie können Ausdrücke mit dem Operator **`sizeof`** verwenden (wie im Artikel zum [`sizeof`-Operator](../c-language/sizeof-operator-c.md) beschrieben), anstatt hartcodierte Datengrößen zu verwenden, um Programme portierbarer zu gestalten.

## <a name="see-also"></a>Siehe auch

[Speicherung von einfachen Typen](../c-language/storage-of-basic-types.md)
