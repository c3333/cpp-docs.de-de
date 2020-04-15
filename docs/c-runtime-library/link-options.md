---
title: Linkoptionen
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: ea71faab639a8c0a09d6e332618dd7e09159a4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351102"
---
# <a name="link-options"></a>Linkoptionen

Das Verzeichnis „CRT lib“ umfasst eine Anzahl von kleinen Dateien, die bestimmte CRT-Funktionen ohne Codeänderung ermöglichen. Diese werden als "Linkoptionen" bezeichnet, da Sie sie nur der Linkerbefehlszeile hinzufügen müssen, um sie zu verwenden.

Die reinen CLR-Versionen dieser Objekte sind in Visual Studio 2015 als veraltet markiert und werden in Visual Studio 2017 nicht unterstützt. Verwenden Sie die Standardversionen für nativen Code und /CLR-Code.

|Native und /CLR|Reiner Modus|BESCHREIBUNG|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Legt den Standard-Dateiübersetzungsmodus auf „binär“ fest. Siehe [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|–|Bietet Stapelüberprüfung und alloca-Unterstützung, wenn CRT nicht verwendet wird.|
|commode.obj|pcommode.obj|Legt das globale Commit-Flag auf „commit“ fest. Siehe [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) und [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|–|Initialisiert das MTA (Multithread-Apartment) während des Starts der EXE-Datei, wodurch die Verwendung von COM-Objekten in globalen intelligenten Zeigern ermöglicht wird. Verwenden Sie diese Option nicht für DLLs, da sie während des Beendens einen MTA-Verweis offenlegt. Eine Verknüpfung hiermit entspricht dem Einfügen von „combase.h“ und Definieren von _EXE_INITIALIZE_MTA. |
|fp10.obj|–|Ändert das Standard-Präzisionssteuerelement in 64 Bit. Siehe [Gleitkommaunterstützung](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Legt einen standardmäßigen Handler für ungültige Parameter fest, der nichts bewirkt; d.h., dass ungültige Parameter, die an CRT-Funktionen übergeben werden, nur errno festlegen und ein Fehlerergebnis zurückgeben.|
|legacy_stdio_float_rounding.obj|–|Das Drucken von Gleitkommawerten (z. B. bei Verwendung von [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)) mit der universellen C-Laufzeit von Windows 10 19041 wurde behoben. Es rundet nun genau darstellbare Gleitkommazahlen richtig ab und respektiert die von [fesetenv](../c-runtime-library/reference/fesetenv1.md)angeforderte Gleitkommarundung . Dieses Verhaltensupdate ist in Visual Studio 2019 Version 16.2 und höher verfügbar. Das Legacyverhalten wird in früheren Versionen von Visual Studio oder durch Bereitstellen dieser Linkoption verwendet.|
|loosefpmath.obj|–|Stellt sicher, dass der Gleitkommacode nicht normale Werte toleriert.|
|newmode.obj|pnewmode.obj|Veranlasst [malloc](../c-runtime-library/reference/malloc.md), die neuen Handler als Fehler aufzurufen. Siehe [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md), und [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Deaktiviert alle Verarbeitungsvorgänge von argc und argv.|
|nochkclr.obj|–|Führt keine Aktion aus. Aus Ihrem Projekt entfernen.|
|noenv.obj|pnoenv.obj|Deaktiviert die Erstellung einer zwischengespeicherten Umgebung für CRT.|
|nothrownew.obj|pnothrownew.obj|Ermöglicht die nicht auslösende Version von „neu“ in CRT. Siehe [Operatoren „new“ und „delete“](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Ermöglicht die Platzhaltererweiterung eines Befehlszeilenarguments. Siehe [Erweitern von Platzhalterargumenten](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Ermöglicht das threadspezifische Gebietsschema standardmäßig für alle neuen Threads.|
|wsetargv.obj|pwsetargv.obj|Ermöglicht die Platzhaltererweiterung eines Befehlszeilenarguments. Siehe [Erweitern von Platzhalterargumenten](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Siehe auch

- [CRT-Bibliotheksfunktionen](../c-runtime-library/crt-library-features.md)
