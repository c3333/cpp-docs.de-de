---
title: Compilerwarnung (Stufe 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 20d6010cb83107946c00f2f7b00cda771b2e70b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199016"
---
# <a name="compiler-warning-level-3-c4159"></a>Compilerwarnung (Stufe 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma-Pragma (Pop-,...): hat den zuvor per pushid-Bezeichner "*Bezeichner*" entfernt

## <a name="remarks"></a>Bemerkungen

Der Quellcode enthält eine **Push** -Anweisung mit einem Bezeichner für ein Pragma, gefolgt von einer **Pop** -Anweisung ohne einen Bezeichner. Daher wird der *Bezeichner* per Pop ausgeblendet, und nachfolgende Verwendungszwecke des *Bezeichners* können zu unerwartetem Verhalten führen.

## <a name="example"></a>Beispiel

Um diese Warnung zu vermeiden, müssen Sie einen Bezeichner in der **Pop** -Anweisung erteilen. Beispiel:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
