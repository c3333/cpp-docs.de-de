---
title: Compilerfehler C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: f9090e098d7f523bf7bc12b7fa4d9312f6ca5466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212903"
---
# <a name="compiler-error-c2030"></a>Compilerfehler C2030

ein Destruktor mit "protected private"-Zugriffsmöglichkeiten kann kein Member einer Klasse sein, die als "sealed" deklariert wurde

Eine Windows-Runtime Klasse, die als deklariert ist, **`sealed`** darf keinen geschützten privaten Dekonstruktor aufweisen. Nur öffentliche virtuelle und private nicht virtuelle Destruktoren sind für versiegelte Typen zulässig. Weitere Informationen finden Sie unter Verweis [Klassen und Strukturen](../../cppcx/ref-classes-and-structs-c-cx.md).

Um diesen Fehler zu beheben, ändern Sie den Zugriff auf den Destruktor.
