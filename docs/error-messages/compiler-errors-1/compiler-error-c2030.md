---
title: Compilerfehler C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208031"
---
# <a name="compiler-error-c2030"></a>Compilerfehler C2030

ein Destruktor mit "protected private"-Zugriffsmöglichkeiten kann kein Member einer Klasse sein, die als "sealed" deklariert wurde

Eine Windows-Runtime-Klasse, die als `sealed` deklariert wird, kann nicht über einen geschützten privaten Destruktor verfügen. Nur öffentliche virtuelle und private nicht virtuelle Destruktoren sind für versiegelte Typen zulässig. Weitere Informationen finden Sie unter [Referenzklassen und -strukturen](../../cppcx/ref-classes-and-structs-c-cx.md).

Um diesen Fehler zu beheben, ändern Sie den Zugriff auf den Destruktor.
