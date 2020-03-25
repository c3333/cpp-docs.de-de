---
title: Compilerwarnung (Stufe 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: dfc3a91b2dcb3ed1e8f4f4993edd67219a6bf1d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163844"
---
# <a name="compiler-warning-level-1-c4103"></a>Compilerwarnung (Stufe 1) C4103

' Dateiname ': die Ausrichtung wurde nach dem einschließen des Headers geändert, möglicherweise fehlt #Pragma Pack (Pop).

Das Verpacken wirkt sich auf das Layout von Klassen aus, und wenn Änderungen über Header Dateien hinweg verpackt werden, können Probleme auftreten.

Verwenden Sie #Pragma [Pack](../../preprocessor/pack.md)(Pop), bevor Sie die Header Datei beenden, um diese Warnung zu beheben.

Im folgenden Beispiel wird C4103 generiert:

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

und anschließend

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
