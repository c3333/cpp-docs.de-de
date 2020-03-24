---
title: Compilerwarnung (Stufe 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175115"
---
# <a name="compiler-warning-level-1-c4794"></a>Compilerwarnung (Stufe 1) C4794

Segment der Variable 'Variable' im lokalen Thread-Speicher von 'Abschnittsname' nach '.tls$' verschoben

Sie haben [#pragma data_seg](../../preprocessor/data-seg.md) verwendet, um eine tls-Variable in einem Abschnitt zu positionieren, der nicht mit „.tls$“ beginnt.

Der Abschnitt „.tls$*x* “ befindet sich in der Objektdatei, wo die [__declspec(thread)](../../cpp/thread.md) -Variablen definiert werden. Durch diese Abschnitte ergibt sich ein „.tls“-Abschnitt in der EXE- oder DLL-Datei.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4794 generiert.

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```
