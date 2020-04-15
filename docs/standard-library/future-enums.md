---
title: '&lt;future&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0f1064fdf434560c3130d1254512470cc5bc1ee0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370692"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt;-Enumerationen

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Starten](#launch)|

## <a name="future_errc-enumeration"></a><a name="future_errc"></a>future_errc-Enumeration

Liefert symbolische Namen für alle Fehler, die von der [future_error](../standard-library/future-error-class.md)-Klasse gemeldet werden.

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a>future_status-Enumeration

Liefert symbolische Namen für die Gründe, aus denen eine zeitgesteuerte Wartefunktion eine Rückgabe ausführen kann.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a>Enumeration starten

Stellt einen Bitmaskentyp dar, mit dem die möglichen Modi für die Vorlagenfunktion [async](../standard-library/future-functions.md#async) beschrieben werden.

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Siehe auch

[\<zukünftige>](../standard-library/future.md)
