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
ms.openlocfilehash: 5f93aaa79fd7c3664ecf80d5007d5954002bce4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160644"
---
# <a name="__unaligned"></a>__unaligned

**Microsoft-spezifisch**. Wenn Sie einen Zeiger mit dem **__unaligned** -Modifizierer deklarieren, geht der Compiler davon aus, dass der Zeiger nicht ausgerichtete Daten adressiert. Folglich wird Platt Form geeigneter Code generiert, um nicht ausgerichtete Lese-und Schreibvorgänge über den Zeiger zu verarbeiten.

## <a name="remarks"></a>Bemerkungen

Dieser Modifizierer beschreibt die Ausrichtung der Daten, die vom Zeiger adressiert werden. Es wird davon ausgegangen, dass der Zeiger selbst ausgerichtet wird.

Die Notwendigkeit für das **__unaligned** -Schlüsselwort variiert je nach Plattform und Umgebung. Wenn Daten nicht ordnungsgemäß gekennzeichnet werden, kann dies zu Problemen mit Leistungseinbußen und Hardwarefehlern führen. Der **__unaligned** Modifizierer ist für die x86-Plattform ungültig.

Aus Gründen der Kompatibilität mit früheren Versionen ist **_unaligned** ein Synonym für **__unaligned** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Weitere Informationen zur Ausrichtung finden Sie unter:

- [align](../cpp/align-cpp.md)

- [__alignof-Operator](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Strukturmemberausrichtung)](../build/reference/zp-struct-member-alignment.md)

- [Beispiele für die Strukturausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)
