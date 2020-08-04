---
title: static-Speicherklassenspezifizierer
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: e84e2745c6077f038f47295119936a1ad6431bdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229492"
---
# <a name="static-storage-class-specifier"></a>static-Speicherklassenspezifizierer

Eine Variable, die auf interner Ebene mit dem **`static`** -Speicherklassenspezifizierer deklariert wurde, hat eine globale Lebensdauer, ist jedoch nur innerhalb des Blocks sichtbar, in dem sie deklariert ist. Bei konstanten Zeichenfolgen ist die Verwendung von **`static`** nützlich, weil sich damit der Mehraufwand einer häufigen Initialisierung in häufig aufgerufenen Funktionen verringern lässt.

## <a name="remarks"></a>Hinweise

Wenn Sie eine Variable nicht explizit als **`static`** initialisieren, wird sie standardmäßig mit 0 initialisiert. Innerhalb einer Funktion sorgt **`static`** für die Zuordnung von Speicher und dient als Definition. Interne statische Variablen stellen privaten Festspeicher bereit, der nur für eine einzelne Funktion sichtbar ist.

## <a name="see-also"></a>Siehe auch

[C-Speicherklassen](c-storage-classes.md)<br/>
[Speicherklassen (C++)](../cpp/storage-classes-cpp.md)
