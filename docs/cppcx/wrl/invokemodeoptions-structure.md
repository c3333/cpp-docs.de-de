---
title: Invokemodeoptions-Struktur
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 9bca49479d97ee371f6728f90a9aa96da0387f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213836"
---
# <a name="invokemodeoptions-structure"></a>Invokemodeoptions-Struktur

Gibt an, ob alle Ereignisse in der delegatwarteschlange ausgelöst oder nach dem Auslösen eines Fehlers nicht mehr ausgelöst werden soll. Die zulässigen Werte werden in der `InvokeMode` Enumeration angegeben.

## <a name="syntax"></a>Syntax

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Event. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)<br/>
[Microsoft:: WRL:: agileeventsource-Klasse](agileeventsource-class.md)
