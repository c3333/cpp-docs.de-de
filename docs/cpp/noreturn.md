---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367858"
---
# <a name="noreturn"></a>noreturn

**Microsoft Specific**

Dieser **__declspec-Attribut** teilt dem Compiler mit, dass eine Funktion nicht zurückgegeben wird. Infolgedessen weiß der Compiler, dass der Code, der einem Aufruf einer **__declspec(noreturn)-Funktion** folgt, nicht erreichbar ist.

Wenn der Compiler eine Funktion mit einem Kontrollpfad findet, die keinen Wert zurückgibt, wird eine Warnung (C4715) oder Fehlermeldung (C2202) generiert. Wenn der Steuerelementpfad aufgrund einer Funktion, die nie zurückgegeben wird, nicht erreicht werden kann, können Sie **__declspec(noreturn)** verwenden, um diese Warnung oder diesen Fehler zu verhindern.

> [!NOTE]
> Das Hinzufügen **__declspec(noreturn)** zu einer Funktion, die voraussichtlich zurückgegeben wird, kann zu einem undefinierten Verhalten führen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel enthält die **else-Klausel** keine Rückgabeanweisung.  Wenn `fatal` Sie als **__declspec(noreturn)** deklarieren, wird ein Fehler oder eine Warnmeldung vermieden.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
