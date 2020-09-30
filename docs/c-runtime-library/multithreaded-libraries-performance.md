---
title: Leistung von Multithreadbibliotheken
description: Hier finden Sie eine Übersicht über die optimale Leistung der Multithreadbibliotheken der Microsoft C-Laufzeit.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
ms.openlocfilehash: edfbbf3055e9023c74cf0e154577d4b1853f557b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590198"
---
# <a name="multithreaded-libraries-performance"></a>Leistung von Multithreadbibliotheken

Singlethread-CRT ist nicht mehr verfügbar. In diesem Thema wird erläutert, wie Sie maximale Leistung mit Multithreadbibliotheken erzielen.

## <a name="maximizing-performance"></a>Maximieren der Leistung

Die Leistung von Multithreadbibliotheken wurde verbessert und erreicht fast die Leistung der jetzt beseitigten Singlethread-Bibliotheken. Für Situationen, in denen sogar eine noch höhere Leistung erforderlich ist, gibt es mehrere neue Features.

- Mit unabhängiger Datenstromsperrung können Sie einen Datenstrom sperren und anschließend [_nolock-Funktionen](../c-runtime-library/nolock-functions.md) verwenden, die direkt auf den Datenstrom zugreifen. So kann die Sperrverwendung außerhalb kritischer Schleifen gehostet werden.

- Threadspezifisches Gebietsschema reduziert die Kosten des Gebietsschemazugriffs für Multithread-Szenarien (siehe [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Vom Gebietsschema abhängige Funktionen (mit Namen, die mit „_l“ enden) nehmen das Gebietsschema als Parameter, was erhebliche Kosten spart (z.B. [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Optimierungen für allgemeine Codepages verringern die Kosten für viele kurze Vorgänge.

- Definieren von [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) erzwingt, dass alle E/A-Vorgänge ein Singlethread-E/A-Modell voraussetzen und die _nolock-Formen der Funktionen verwenden. So können in hohem Maße E/A-basierte Singlethread-Anwendungen eine bessere Leistung erzielen.

- Das Verfügbarmachen des CRT-Heap-Handles ermöglicht Ihnen das Aktivieren des Windows Low Fragmentation Heap (LFH) für den CRT-Heap, wodurch die Leistung in Szenarien mit hoher Skalierung wesentlich verbessert werden kann.

## <a name="see-also"></a>Weitere Informationen

[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)
