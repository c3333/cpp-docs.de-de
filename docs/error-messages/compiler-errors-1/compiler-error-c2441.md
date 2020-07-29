---
title: Compilerfehler C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: aa55392e9f58caa4292cf5f96ef97f65a53bf913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207952"
---
# <a name="compiler-error-c2441"></a>Compilerfehler C2441

> '*Variable*': ein mit __declspec (Process) deklariertes Symbol muss im/CLR: pure-Modus konstant sein.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Standardmäßig liegen Variablen pro Anwendungsdomäne unter **/clr: pure**vor. Eine `__declspec(process)` mit **/clr: pure** markierte Variable ist anfällig für Fehler, wenn Sie in einer Anwendungsdomäne geändert und in einer anderen Anwendung gelesen wird.

Daher erzwingt der Compiler, dass sich pro Prozessvariablen **`const`** unter **/clr: pure**befinden, sodass Sie in allen Anwendungs Domänen schreibgeschützt sind.

Weitere Informationen finden Sie unter [Process](../../cpp/process.md) and [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2441 generiert.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
