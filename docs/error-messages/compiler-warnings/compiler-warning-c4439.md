---
title: Compilerwarnung C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: baf74733c94fdb03f130d2300d0918845cc4de4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223329"
---
# <a name="compiler-warning-c4439"></a>Compilerwarnung C4439

"Function": die Funktionsdefinition mit einem verwalteten Typ in der Signatur muss eine __clrcall Aufruf Konvention aufweisen.

Der Compiler hat implizit eine Aufruf Konvention durch ersetzt [`__clrcall`](../../cpp/clrcall.md) . Um diese Warnung zu beheben, entfernen Sie die- **`__cdecl`** oder- **`__stdcall`** Aufruf Konvention.

C4439 wird immer als Fehler ausgegeben. Sie können diese Warnung mit `#pragma warning` oder deaktivieren **`/wd`** . Weitere Informationen hierzu finden Sie unter [Warning](../../preprocessor/warning.md) or [/w,/W0,/W1,/W2,/w3,/W4,/W1,/W2,/w3,/W4,/Wall,/WD](../../build/reference/compiler-option-warning-level.md) ,/We,/wo,/WV,/WX (Warnstufe).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4439 generiert.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
