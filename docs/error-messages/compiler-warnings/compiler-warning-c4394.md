---
title: Compilerwarnung C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: ad6b9624a1bf510465843167d104d1bec189bc70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197357"
---
# <a name="compiler-warning-c4394"></a>Compilerwarnung C4394

'Funktion': Ein anwendungsdomänenspezifisches Symbol sollte nicht mit __declspec(dllexport) markiert werden

Eine Funktion, die mit dem [AppDomain](../../cpp/appdomain.md) - **`__declspec`** Modifizierer gekennzeichnet ist, wird in MSIL (nicht in System eigen) kompiliert, und Export Tabellen ([exportmodifizierer](../../windows/export.md) **`__declspec`** ) werden für verwaltete Funktionen nicht unterstützt.

Sie können eine verwaltete Funktion mit öffentlicher Zugriffsmöglichkeit deklarieren. Weitere Informationen finden Sie unter [Typsichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) und Element [Sichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 wird immer als Fehler ausgegeben.  Sie können diese Warnung mit `#pragma warning` oder **/WD**deaktivieren. Weitere Informationen hierzu finden Sie unter [Warning](../../preprocessor/warning.md) or/w,/W0,/W1,/W2,/w3,/W4,/W1,/W2,/w3 [,/W4,/Wall,/WD,/We](../../build/reference/compiler-option-warning-level.md) ,/wo,/WV,/WX,,,,, (Warnstufe).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4394 generiert.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
