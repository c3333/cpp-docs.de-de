---
title: Compilerwarnung (Stufe 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: d960e5a5e2d7ad2d2b650095c42e9afea7bfe7fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219871"
---
# <a name="compiler-warning-level-4-c4295"></a>Compilerwarnung (Stufe 4) C4295

> "*Array*": das Array ist zu klein, um ein abschließendes NULL Zeichen einzuschließen.

Ein Array wurde initialisiert, aber das letzte Zeichen im Array ist kein NULL-Wert. der Zugriff auf das Array als Zeichenfolge kann zu unerwarteten Ergebnissen führen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4295 generiert. Um dieses Problem zu beheben, können Sie die Array Größe vergrößern, um eine abschließende NULL aus der initialisiererzeichenfolge zu speichern, oder Sie können eine arrayinitialisiererliste verwenden, um die Absicht klar zu machen, dass es sich um ein Array von handelt **`char`** , nicht um eine auf NULL endende Zeichenfolge.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
