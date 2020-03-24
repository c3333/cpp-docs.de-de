---
title: Umwandlungsoperatoren
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: eac274a0207be675b8d13532c3110c6e71bd55c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190098"
---
# <a name="casting-operators"></a>Umwandlungsoperatoren

Es gibt mehrere Umwandlungsoperatoren, die spezifisch für die Programmiersprache C++ sind. Diese Operatoren sind vorgesehen, um einen Teil der Mehrdeutigkeiten und Gefahren zu beseitigen, die Umwandlungen in der C-Programmiersprache im altem Stil mit sich brachten. Diese Operatoren sind:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Wird für die Konvertierung von polymorphen Typen verwendet.

- [static_cast](../cpp/static-cast-operator.md) Wird für die Konvertierung von nicht polymorphen Typen verwendet.

- [const_cast](../cpp/const-cast-operator.md) Wird **zum Entfernen der Attribute**"Konstante", " **volatile**" und " **__unaligned** " verwendet.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Wird für die einfache Neuinterpretation von Bits verwendet.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Wird in C++/CLI verwendet, um überprüfbare MSIL zu liefern.

Verwenden Sie **const_cast** und **reinterpret_cast** als letztes Mittel, da diese Operatoren dieselben Gefahren wie alte Typumwandlungen darstellen. Allerdings sind sie weiterhin erforderlich, um alte Umwandlungen vollständig zu ersetzen.

## <a name="see-also"></a>Weitere Informationen

[Umwandlung](../cpp/casting.md)
