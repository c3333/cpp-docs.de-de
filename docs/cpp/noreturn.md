---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f0b5b17a6d64375f49a6d55021c72ba7119eb976
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213306"
---
# <a name="noreturn"></a>noreturn

**Microsoft-spezifisch**

Dieses **`__declspec`** Attribut weist den Compiler an, dass eine Funktion nicht zurückgibt. Folglich weiß der Compiler, dass der Code, der einem Rückruf einer Funktion folgt, **`__declspec(noreturn)`** nicht erreichbar ist.

Wenn der Compiler eine Funktion mit einem Kontrollpfad findet, die keinen Wert zurückgibt, wird eine Warnung (C4715) oder Fehlermeldung (C2202) generiert. Wenn der Steuerelement Pfad aufgrund einer Funktion, die nie zurückgibt, nicht erreicht werden kann, können Sie verwenden, **`__declspec(noreturn)`** um diese Warnung oder den Fehler zu verhindern.

> [!NOTE]
> Das Hinzufügen **`__declspec(noreturn)`** zu einer Funktion, die zurückgegeben werden soll, kann zu undefiniertem Verhalten führen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel enthält die- **`else`** Klausel keine Return-Anweisung.  Das Deklarieren von `fatal` als **`__declspec(noreturn)`** vermeidet eine Fehler-oder Warnmeldung.

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

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
