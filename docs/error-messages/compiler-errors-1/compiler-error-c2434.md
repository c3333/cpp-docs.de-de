---
title: Compilerfehler C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205463"
---
# <a name="compiler-error-c2434"></a>Compilerfehler C2434

> '*Symbol*': ein Symbol, das mit __declspec (Process) deklariert wurde, kann im/CLR: pure-Modus nicht dynamisch initialisiert werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Es ist nicht möglich, eine prozessspezifische Variable unter **/clr: pure**dynamisch zu initialisieren. Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) und [verarbeiten](../../cpp/process.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2434 generiert. Um dieses Problem zu beheben, verwenden Sie Konstanten, um `process` Variablen zu initialisieren.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
