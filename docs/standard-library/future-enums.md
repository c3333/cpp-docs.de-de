---
title: '&lt;future&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 45dc3277b3f14b7f9dbb043cf9db1f1865d4e4c9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838021"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt;-Enumerationen

[future_errc](#future_errc)\
[future_status](#future_status)\
[Starten](#launch)

## <a name="future_errc-enumeration"></a><a name="future_errc"></a> future_errc-Enumeration

Liefert symbolische Namen für alle Fehler, die von der [future_error](../standard-library/future-error-class.md)-Klasse gemeldet werden.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a> future_status-Enumeration

Liefert symbolische Namen für die Gründe, aus denen eine zeitgesteuerte Wartefunktion eine Rückgabe ausführen kann.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a> Launch-Enumeration

Stellt einen Bitmaskentyp dar, mit dem die möglichen Modi für die Vorlagenfunktion [async](../standard-library/future-functions.md#async) beschrieben werden.

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Weitere Informationen

[\<future>](../standard-library/future.md)
