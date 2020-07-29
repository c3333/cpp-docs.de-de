---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 2ab94a44d08165ca6e8f394278e24d7c8d201398
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223498"
---
# <a name="__unaligned"></a>__unaligned

**Microsoft-spezifisch**. Wenn Sie einen Zeiger mit dem- **`__unaligned`** Modifizierer deklarieren, geht der Compiler davon aus, dass der Zeiger nicht ausgerichtete Daten adressiert. Folglich wird Platt Form geeigneter Code generiert, um nicht ausgerichtete Lese-und Schreibvorgänge über den Zeiger zu verarbeiten.

## <a name="remarks"></a>Bemerkungen

Dieser Modifizierer beschreibt die Ausrichtung der Daten, die vom Zeiger adressiert werden. Es wird davon ausgegangen, dass der Zeiger selbst ausgerichtet wird.

Die Notwendigkeit des **`__unaligned`** Schlüssel Worts variiert je nach Plattform und Umgebung. Wenn Daten nicht ordnungsgemäß gekennzeichnet werden, kann dies zu Problemen mit Leistungseinbußen und Hardwarefehlern führen. Der- **`__unaligned`** Modifizierer ist für die x86-Plattform ungültig.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_unaligned`** ein Synonym für, **`__unaligned`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Weitere Informationen zur Ausrichtung finden Sie unter:

- [`align`](../cpp/align-cpp.md)

- [`alignof`KOM](../cpp/alignof-operator.md)

- [`pack`](../preprocessor/pack.md)

- [`/Zp`(Ausrichtung des Strukturmembers)](../build/reference/zp-struct-member-alignment.md)

- [Beispiele für die Strukturausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
