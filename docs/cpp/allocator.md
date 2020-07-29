---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: a26cf4d2b79d64ddc9f0b60982d778e33d0f200a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216647"
---
# `allocator`

**Microsoft-spezifisch**

Der **`allocator`** deklarationsspezifizierer kann auf benutzerdefinierte Speicher Belegungs Funktionen angewendet werden, um die Zuordnungen über die Ereignis Ablauf Verfolgung für Windows (ETW) sichtbar zu machen.

## <a name="syntax"></a>Syntax

> **`__declspec(allocator)`**

## <a name="remarks"></a>Bemerkungen

Der Native Memory-Profiler in Visual Studio funktioniert, indem die von zur Laufzeit ausgegebenen Zuordnungs-etw-Ereignisdaten gesammelt werden. Zuweisungen im CRT und Windows SDK wurden auf Quellebene kommentiert, sodass ihre Speicherbelegungsdaten erfasst werden können. Wenn Sie Ihre eigenen Zuweisungen schreiben, kann jede Funktion, die einen Zeiger auf neu zugewiesenen Heap Speicher zurückgibt, mit ergänzt werden `__declspec(allocator)` , wie in diesem Beispiel für mymalloc zu sehen ist:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Weitere Informationen finden Sie unter [Messen der Speicherauslastung in Visual Studio](/visualstudio/profiling/memory-usage) und [benutzerdefinierte Native etw-Heap Ereignisse](/visualstudio/profiling/custom-native-etw-heap-events).

**Ende Microsoft-spezifisch**
