---
title: Kompatibilität
description: Beschreibt die Kompatibilität der Microsoft Universal c-Lauf Zeit Bibliothek (ucrt) mit der Standard-c-Bibliothek, POSIX, der sicheren CRT und Store-Apps.
ms.date: 9/11/2020
helpviewer_keywords:
- CRT, compatibility
- compatibility, C runtime libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: d6562be0abde8e9d51260b2d230f225ed159c199
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075749"
---
# <a name="compatibility"></a>Kompatibilität

Die universelle c-Lauf Zeit Bibliothek (ucrt) unterstützt den größten Teil der c-Standardbibliothek, die für C++ Konformität erforderlich ist. Sie implementiert die C99-Bibliothek (ISO/IEC 9899:1999) mit bestimmten Ausnahmen:
- strikte Typkompatibilität in \<complex.h> . 
- `aligned_alloc`, die wahrscheinlich nicht implementiert wird, da das Windows-Betriebssystem keine ausgerichteten Zuordnungen unterstützt. Verwenden Sie stattdessen den nicht standardmäßigen `_aligned_malloc` .
-  `strerrorlen_s`
- atomarische Unterstützung in \<stdatomic.h>
- Threading Unterstützung in \<threads.h>

Die ucrt implementiert auch eine große Teilmenge der POSIX. 1-C-Bibliothek (ISO/IEC 9945-1:1996, POSIX-System Anwendungsprogramm Schnittstelle). Es ist jedoch nicht vollständig mit einem spezifischen POSIX-standardkonform. Die ucrt implementiert auch mehrere Microsoft-spezifische Funktionen und Makros, die nicht Teil eines Standards sind.

Die für die Microsoft-Implementierung von Visual C++ spezifischen Funktionen befinden sich in der vcruntime-Bibliothek.  Viele dieser Funktionen dienen der internen Verwendung und können nicht von Benutzercode aufgerufen werden. Einige sind für den Gebrauch beim Debuggen und aus Gründen der Implementierungskompatibilität dokumentiert.

Im C++-Standard sind Namen, die im globalen Namespace mit einem Unterstrich beginnen, für die Implementierung reserviert. Sowohl die POSIX-Funktionen als auch die Microsoft-spezifischen Funktionen der Lauf Zeit Bibliothek befinden sich im globalen Namespace, sind jedoch nicht Teil der Standard-C-Lauf Zeit Bibliothek. Aus diesem Grund haben die bevorzugten Microsoft-Implementierungen dieser Funktionen einen führenden Unterstrich. Aus Gründen der Portierbarkeit unterstützt die UCRT außerdem die Standardnamen. Der Microsoft Visual C++-Compiler gibt jedoch beim Kompilieren von Code eine Veraltungswarnung aus, wenn dieser Standardnamen verwendet. Nur die Standardnamen sind veraltet, nicht die Funktionen selbst. Um die Warnung zu unterdrücken, definieren Sie `_CRT_NONSTDC_NO_WARNINGS` , bevor Sie Header in den Code einschließen, in denen die ursprünglichen POSIX-Namen verwendet werden.

Bestimmte Funktionen in der Standard-C-Bibliothek wurden in der Vergangenheit aufgrund missbräuchlich verwendeter Parameter und nicht deaktivierter Puffer häufig unsicher verwendet. Diese Funktionen stellen oft die Ursache von Sicherheitsproblemen im Code dar. Microsoft hat einen Satz sicherer Versionen dieser Funktionen erstellt, die die Verwendung von Parametern überprüfen. Sie rufen den Handler für ungültige Parameter auf, wenn zur Laufzeit ein Problem erkannt wird.  Standardmäßig gibt der Microsoft Visual C++-Compiler eine Veraltungswarnung aus, wenn eine Funktion verwendet wird, zu der eine sicherere Variante verfügbar ist. Wenn Sie Ihren Code als C++ kompilieren, können Sie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` als 1 definieren, um die meisten Warnungen auszuschließen. Dieses Makro ermöglicht Vorlagen Überladungen, die sichereren Varianten aufzurufen, während portablen Quellcode beibehalten wird. Um die Warnung zu unterdrücken, definieren Sie `_CRT_SECURE_NO_WARNINGS` , bevor Sie Header in den Code einschließen, die diese Funktionen verwenden. Weitere Informationen finden Sie unter [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

Sofern nicht in der Dokumentation zu bestimmten Funktionen anders vermerkt, ist die UCRT mit der Windows-API kompatibel.  Bestimmte Funktionen werden in Windows Store-oder universelle Windows-Plattform-Apps ([UWP](/uwp)) nicht unterstützt. Diese Funktionen werden in CRT-Funktionen aufgelistet, die [in universelle Windows-Plattform-apps nicht unterstützt](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)werden.

## <a name="related-articles"></a>Verwandte Artikel

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[UWP-apps, die Windows-Runtime und die C-Laufzeit](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Beschreibt, wann ucrt-Routinen nicht mit universellen Windows-Apps oder Microsoft Store-Apps kompatibel sind.|
|[ANSI C-Konformität](../c-runtime-library/ansi-c-compliance.md)|Beschreibt die normgerechte Benennung in der UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Enthält Richtlinien zum Portieren von Programmen zu UNIX.|
|[Windows-Plattformen (CRT)](../c-runtime-library/windows-platforms-crt.md)|Listet die Betriebssysteme auf, die durch CRT unterstützt werden.|
|[Abwärtskompatibilität](../c-runtime-library/backward-compatibility.md)|Beschreibt, wie alte CRT-Namen neuen zugeordnet werden.|
|[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)|Bietet eine Übersicht über die CRT-Bibliotheksdateien (.lib) und über die zugehörigen Compileroptionen.|
