---
title: Compilerfehler C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 7ef22711884dabb83efa8c7ebfdb7648316c12ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205412"
---
# <a name="compiler-error-c2435"></a>Compilerfehler C2435

> "*var*": die dynamische Initialisierung erfordert eine verwaltete CRT, kann nicht mit/CLR: safe kompiliert werden.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Für die Initialisierung der globalen anwendungsspezifischen Domänen Variablen muss die CRT mit `/clr:pure`kompiliert werden, die kein überprüfbares Image erzeugt.

Weitere Informationen finden Sie unter [appdomain](../../cpp/appdomain.md) und [process](../../cpp/process.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2435 generiert:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
