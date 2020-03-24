---
title: Compilerwarnung (Stufe 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: 04252f6100f0cabcd6bca0ff4145b55cfcadd234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200121"
---
# <a name="compiler-warning-level-1-c4109"></a>Compilerwarnung (Stufe 1) C4109

Unerwarteter Bezeichner "identifier"

Das Pragma mit dem unerwarteten Bezeichner wird ignoriert.

## <a name="example"></a>Beispiel

```cpp
// C4109.cpp
// compile with: /W1 /LD
#pragma init_seg( abc ) // C4109
```
