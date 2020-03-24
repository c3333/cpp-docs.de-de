---
title: Compilerwarnung (Stufe 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161385"
---
# <a name="compiler-warning-level-4-c4207"></a>Compilerwarnung (Stufe 4) C4207

nicht dem Standard entsprechende Erweiterung: Formular für erweiterte Initialisierung

Mit Microsoft Extensions (/Ze) können Sie ein Array von `char` ohne Größenanpassung mithilfe einer Zeichenfolge in geschweiften Klammern initialisieren.

## <a name="example"></a>Beispiel

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Diese Initialisierungen sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
