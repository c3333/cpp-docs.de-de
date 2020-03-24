---
title: Compilerwarnung (Stufe 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 76a33b24446debffb2c00bf1b0497cfc86022ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175138"
---
# <a name="compiler-warning-level-1-c4788"></a>Compilerwarnung (Stufe 1) C4788

'Bezeichner': Der Bezeichner wurde auf 'Anzahl' Zeichen gekürzt.

Durch den Compiler wird die für einen Funktionsnamen zugelassene maximale Länge eingeschränkt. Wenn der Compiler funclets für EH/SEH-Code generiert, bildet er den funclet-Namen, indem er den Funktionsnamen mit einem Text vorangestellt, z. b. "__catch", "\__unwind" oder einer anderen Zeichenfolge.

Wenn der erstellte funclet-Name zu lang ist, wird dieser vom Compiler gekürzt, und es wird C4788 ausgegeben.

Um diese Warnung zu vermeiden, kürzen Sie den ursprünglichen Funktionsnamen. Wenn es sich bei der Funktion um eine C++-Vorlagenfunktion oder -Methode handelt, verwenden Sie für einen Teil des Namens eine Typdefinition. Beispiel:

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

Dies kann durch Folgendes ersetzt werden:

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Diese Warnung tritt nur im x64-Compiler auf.
