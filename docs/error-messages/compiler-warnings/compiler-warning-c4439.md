---
title: Compilerwarnung C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: c125fa84119c62e3090611c9a841f46eee759711
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165209"
---
# <a name="compiler-warning-c4439"></a>Compilerwarnung C4439

"Function": die Funktionsdefinition mit einem verwalteten Typ in der Signatur muss eine __clrcall Aufruf Konvention aufweisen.

Der Compiler ersetzte eine Aufruf Konvention implizit durch [__clrcall](../../cpp/clrcall.md). Entfernen Sie die `__cdecl` oder `__stdcall` Aufruf Konvention, um diese Warnung zu beheben.

C4439 wird immer als Fehler ausgegeben. Sie können diese Warnung mit dem `#pragma warning` oder **/WD**deaktivieren. Weitere Informationen finden Sie unter [Warning](../../preprocessor/warning.md) or [/w,/W0,/W1,/W2,/w3,/W4,/W1,/W2,/w3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (Warnstufe)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4439 generiert.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
