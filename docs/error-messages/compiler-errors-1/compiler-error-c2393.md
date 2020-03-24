---
title: Compilerfehler C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: cc3c124f1a4daea0f2517a93c6b354b8233aa5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205984"
---
# <a name="compiler-error-c2393"></a>Compilerfehler C2393

> '*Symbol*': pro-AppDomain-Symbol kann im Segment '*Segment*' nicht zugeordnet werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Die Verwendung von [AppDomain](../../cpp/appdomain.md) -Variablen impliziert, dass Sie mit **/clr: pure** oder **/clr: Safe**kompilieren und ein sicheres oder reines Image keine Daten Segmente enthalten kann.

Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2393 generiert. Um dieses Problem zu beheben, erstellen Sie kein Daten Segment.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
