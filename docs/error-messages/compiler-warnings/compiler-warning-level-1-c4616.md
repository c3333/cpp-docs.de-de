---
title: Compilerwarnung (Stufe 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: fd36d0cdbcaaeca4f84ce85aa80f3bb1fba616a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185905"
---
# <a name="compiler-warning-level-1-c4616"></a>Compilerwarnung (Stufe 1) C4616

\#pragma-Warnung: die Warnungs Nummer ' Number ' ist keine gültige Compilerwarnung.

Die im [Warnungs](../../preprocessor/warning.md) -Pragma angegebene Warnungs Nummer kann nicht erneut zugewiesen werden. Das Pragma wurde ignoriert.

Im folgenden Beispiel wird C4616 generiert:

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```
