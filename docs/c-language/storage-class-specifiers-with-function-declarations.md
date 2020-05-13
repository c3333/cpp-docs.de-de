---
title: Speicherklassenspezifizierer mit Funktionsdeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157878"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Speicherklassenspezifizierer mit Funktionsdeklarationen

Sie können in Funktionsdeklarationen entweder den **static**-Speicherklassenspezifizierer oder den `extern`-Speicherklassenspezifizierer verwenden. Funktionen besitzen immer eine globale Lebensdauer.

**Microsoft-spezifisch**

Funktionsdeklarationen auf der internen Ebene haben dieselbe Bedeutung wie Funktionsdeklarationen auf externer Ebene. Dies bedeutet, dass eine Funktion nach der Deklaration in der gesamten Übersetzungseinheit sichtbar ist, selbst wenn sie im lokalen Gültigkeitsbereich deklariert wurde.

**Ende Microsoft-spezifisch**

Die Sichtbarkeitsregeln für Funktionen weichen geringfügig von den Regeln für Variablen ab:

- Eine Funktion, die als **static** deklariert wird, ist nur innerhalb der Quelldatei sichtbar, in der sie definiert ist. Funktionen in der gleichen Quelldatei können die **static**-Funktion aufrufen, aber Funktionen in anderen Quelldateien können auf sie nicht direkt anhand ihres Namens zugreifen. Sie können eine weitere **static**-Funktion gleichen Namens in einer anderen Quelldatei deklarieren, ohne dass ein Konflikt auftritt.

- Die Funktionen, die als `extern` deklariert werden, sind in allen Quelldateien im Programm sichtbar (es sei denn, dass Sie später eine solche Funktion erneut als **static** deklarieren). Jede Funktion kann eine `extern`-Funktion aufrufen.

- Funktionsdeklarationen, die die Speicherklassenspezifizierer auslassen, sind standardmäßig `extern`.

**Microsoft-spezifisch**

Microsoft lässt eine Neudefinition eines `extern`-Bezeichners als **static** zu.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Speicherklassen](../c-language/c-storage-classes.md)
