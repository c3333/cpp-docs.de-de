---
title: sequenced_policy-Klasse
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444915"
---
# <a name="sequenced_policy-class"></a>sequenced_policy-Klasse

Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen zu unterscheiden, und erfordert, dass die Ausführung eines parallelen Algorithmus möglicherweise nicht parallelisiert wird.

## <a name="syntax"></a>Syntax

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Bemerkungen

Wenn während der Ausführung eines parallelen Algorithmus mit der `execution::sequenced_policy`-Richtlinie der Aufruf einer Element Zugriffs Funktion über eine nicht abgefangene Ausnahme beendet wird, müssen `terminate()` aufgerufen werden.
