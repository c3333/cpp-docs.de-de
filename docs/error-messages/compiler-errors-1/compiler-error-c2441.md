---
title: Compilerfehler C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205308"
---
# <a name="compiler-error-c2441"></a>Compilerfehler C2441

> '*Variable*': ein mit __declspec (Process) deklariertes Symbol muss im/CLR: pure-Modus konstant sein.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Standardmäßig liegen Variablen pro Anwendungsdomäne unter **/clr: pure**vor. Eine Variable, die als `__declspec(process)` unter **/clr: pure** gekennzeichnet ist, ist anfällig für Fehler, wenn Sie in einer Anwendungsdomäne geändert und in einem anderen gelesen wird.

Daher erzwingt der Compiler, dass pro Prozessvariablen unter **/clr: pure**`const` werden, sodass Sie in allen Anwendungs Domänen schreibgeschützt sind.

Weitere Informationen finden Sie unter [Process](../../cpp/process.md) and [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2441 generiert.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
