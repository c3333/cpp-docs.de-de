---
title: Signalkonstanten
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: d26671b8c3d983e7f1c3fd559d8aa2029e3162fe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841141"
---
# <a name="signal-constants"></a>Signalkonstanten

## <a name="syntax"></a>Syntax

```
#include <signal.h>
```

## <a name="remarks"></a>Bemerkungen

Das `sig`-Argument muss eine der unten aufgelisteten (und in SIGNAL.H definierten) Manifestkonstanten sein.

|Konstante|Beschreibung|
|-|-|
|SIGABRT|Nicht ordnungsgemäße Beendigung. Die Standardaktion beendet das aufrufende Programm mit Exitcode 3.  |
|SIGABRT_COMPAT|Identisch mit SIGABRT. Zur Kompatibilität mit anderen Plattformen.  |
|SIGFPE|Gleitkommafehler, z.B. Überlauf, Division durch 0 (null) oder eine ungültige Operation. Die Standardaktion beendet das aufrufende Programm.  |
|SIGILL|Ungültige Anweisung. Die Standardaktion beendet das aufrufende Programm.  |
|SIGINT|STRG+C-Unterbrechung. Die Standardaktion beendet das aufrufende Programm mit Exitcode 3.  |
|SIGSEGV|Ungültiger Speicherzugriff. Die Standardaktion beendet das aufrufende Programm.  |
|SIGTERM|An das Programm gesendete Beendigungsanforderung. Die Standardaktion beendet das aufrufende Programm mit Exitcode 3.  |
|SIG_ERR|Ein Rückgabetyp aus einem Signal, der angibt, das ein Fehler aufgetreten ist.  |

## <a name="see-also"></a>Weitere Informationen

[signal](../c-runtime-library/reference/signal.md)<br/>
[züchten](../c-runtime-library/reference/raise.md)<br/>
[Globale Konstanten](../c-runtime-library/global-constants.md)
