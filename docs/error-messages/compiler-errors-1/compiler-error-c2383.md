---
title: Compilerfehler C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206027"
---
# <a name="compiler-error-c2383"></a>Compilerfehler C2383

'*Symbol*': für dieses Symbol sind keine Standardargumente zulässig.

Der C++ Compiler lässt keine Standardargumente für Zeiger auf Funktionen zu.

Dieser Code wurde vom Microsoft C++ -Compiler in Versionen vor Visual Studio 2005 akzeptiert, gibt jetzt jedoch einen Fehler aus. Weisen Sie für Code, der in allen Versionen C++von Visual funktioniert, keinen Standardwert einem Pointer-to-function-Argument zu.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2383 generiert und eine mögliche Lösung angezeigt:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
