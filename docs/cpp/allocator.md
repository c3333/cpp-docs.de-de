---
title: Zuweisung
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 39708e8cfff7f61c3a3f763f87e1a3da36f0d4b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077253"
---
# <a name="allocator"></a>Zuweisung

**Microsoft-spezifisch**

Der **Allocator** -deklarationsspezifizierer kann auf benutzerdefinierte Speicher Belegungs Funktionen angewendet werden, um die Zuordnungen über die Ereignis Ablauf Verfolgung für Windows (ETW) sichtbar zu machen.

## <a name="syntax"></a>Syntax

```
   __declspec(allocator)
```

## <a name="remarks"></a>Bemerkungen

Der Native Memory-Profiler in Visual Studio funktioniert, indem die von zur Laufzeit ausgegebenen Zuordnungs-etw-Ereignisdaten gesammelt werden. Zuweisungen im CRT und Windows SDK wurden auf Quellebene kommentiert, sodass ihre Speicherbelegungsdaten erfasst werden können. Wenn Sie Ihre eigenen Zuweisungen schreiben, kann jede Funktion, die einen Zeiger auf neu zugewiesenen Heap Speicher zurückgibt, mit `__declspec(allocator)`versehen werden, wie in diesem Beispiel für mymalloc zu sehen ist:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Weitere Informationen finden Sie unter [Messen der Speicherauslastung in Visual Studio](/visualstudio/profiling/memory-usage) und [benutzerdefinierte Native etw-Heap Ereignisse](/visualstudio/profiling/custom-native-etw-heap-events).

**Ende Microsoft-spezifisch**
