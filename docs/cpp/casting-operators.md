---
title: Umwandlungsoperatoren
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 606e8b159bb7bdb7527d33a5211cb33a26913754
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221821"
---
# <a name="casting-operators"></a>Umwandlungsoperatoren

Es gibt mehrere Umwandlungsoperatoren, die spezifisch für die Programmiersprache C++ sind. Diese Operatoren sind vorgesehen, um einen Teil der Mehrdeutigkeiten und Gefahren zu beseitigen, die Umwandlungen in der C-Programmiersprache im altem Stil mit sich brachten. Diese Operatoren sind:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Wird für die Konvertierung von polymorphen Typen verwendet.

- [static_cast](../cpp/static-cast-operator.md) Wird für die Konvertierung von nicht polymorphen Typen verwendet.

- [const_cast](../cpp/const-cast-operator.md) Wird verwendet, um **`const`** die **`volatile`** Attribute, und zu entfernen **`__unaligned`** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Wird für die einfache Neuinterpretation von Bits verwendet.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Wird in C++/CLI verwendet, um überprüfbare MSIL zu liefern.

Verwenden Sie **`const_cast`** und **`reinterpret_cast`** als letztes Mittel, da diese Operatoren dieselben Gefahren wie alte Typumwandlungen darstellen. Allerdings sind sie weiterhin erforderlich, um alte Umwandlungen vollständig zu ersetzen.

## <a name="see-also"></a>Weitere Informationen

[Umwandlung](../cpp/casting.md)
