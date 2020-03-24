---
title: Kompatibilität
description: Beschreibt die Kompatibilität der Microsoft Universal c-Lauf Zeit Bibliothek (ucrt) mit der Standard-c-Bibliothek, POSIX, der sicheren CRT und Store-Apps.
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 39b936acc43243973c2f66ef6fc7306026cc3259
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171046"
---
# <a name="compatibility"></a>Kompatibilität

Die universelle C-Laufzeitbibliothek (UCRT, Universal C Run-Time Library) unterstützt den größten Teil der C-Standardbibliothek, der für die C++-Kompatibilität erforderlich ist. Sie implementiert die C99-Bibliothek (ISO/IEC 9899:1999) mit bestimmten Ausnahmen: die typgenerischen Makros, die in \<tgmath. h-> definiert sind, und eine strikte Typkompatibilität in \<Complex. h->. Die ucrt implementiert auch eine große Teilmenge der POSIX. 1-C-Bibliothek (ISO/IEC 9945-1:1996, POSIX-System Anwendungsprogramm Schnittstelle). Es ist jedoch nicht vollständig mit einem spezifischen POSIX-standardkonform. Die ucrt implementiert auch mehrere Microsoft-spezifische Funktionen und Makros, die nicht Teil eines Standards sind.

Die für die Microsoft-Implementierung von Visual C++ spezifischen Funktionen befinden sich in der vcruntime-Bibliothek.  Viele dieser Funktionen dienen der internen Verwendung und können nicht von Benutzercode aufgerufen werden. Einige sind für den Gebrauch beim Debuggen und aus Gründen der Implementierungskompatibilität dokumentiert.

Im C++-Standard sind Namen, die im globalen Namespace mit einem Unterstrich beginnen, für die Implementierung reserviert. Sowohl die POSIX-Funktionen als auch die Microsoft-spezifischen Funktionen der Lauf Zeit Bibliothek befinden sich im globalen Namespace, sind jedoch nicht Teil der Standard-C-Lauf Zeit Bibliothek. Aus diesem Grund haben die bevorzugten Microsoft-Implementierungen dieser Funktionen einen führenden Unterstrich. Aus Gründen der Portierbarkeit unterstützt die UCRT außerdem die Standardnamen. Der Microsoft Visual C++-Compiler gibt jedoch beim Kompilieren von Code eine Veraltungswarnung aus, wenn dieser Standardnamen verwendet. Nur die Standardnamen sind veraltet, nicht die Funktionen selbst. Um die Warnung zu unterdrücken, definieren Sie `_CRT_NONSTDC_NO_WARNINGS` , bevor Sie Header in den Code einschließen, in denen die ursprünglichen POSIX-Namen verwendet werden.

Bestimmte Funktionen in der Standard-C-Bibliothek wurden in der Vergangenheit aufgrund missbräuchlich verwendeter Parameter und nicht deaktivierter Puffer häufig unsicher verwendet. Diese Funktionen stellen oft die Ursache von Sicherheitsproblemen im Code dar. Microsoft hat einen Satz sicherer Versionen dieser Funktionen erstellt, die die Verwendung von Parametern überprüfen. Sie rufen den Handler für ungültige Parameter auf, wenn zur Laufzeit ein Problem erkannt wird.  Standardmäßig gibt der Microsoft Visual C++-Compiler eine Veraltungswarnung aus, wenn eine Funktion verwendet wird, zu der eine sicherere Variante verfügbar ist. Wenn Sie den Code als C++kompilieren, können Sie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` als 1 definieren, um die meisten Warnungen auszuschließen. Dieses Makro ermöglicht Vorlagen Überladungen, die sichereren Varianten aufzurufen, während portablen Quellcode beibehalten wird. Um die Warnung zu unterdrücken, definieren Sie `_CRT_SECURE_NO_WARNINGS` , bevor Sie Header in den Code einschließen, die diese Funktionen verwenden. Weitere Informationen finden Sie unter [Security Features in the CRT (Sicherheitsfunktionen in der CRT)](../c-runtime-library/security-features-in-the-crt.md).

Sofern nicht in der Dokumentation zu bestimmten Funktionen anders vermerkt, ist die UCRT mit der Windows-API kompatibel.  Bestimmte Funktionen werden in Windows Store-oder universelle Windows-Plattform-Apps ([UWP](/uwp)) nicht unterstützt. Diese Funktionen werden in CRT-Funktionen aufgelistet, die [in universelle Windows-Plattform-apps nicht unterstützt](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)werden.

## <a name="related-articles"></a>Verwandte Artikel

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[UWP-Apps, die Windows-Runtime und die C-Runtime](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Beschreibt, wann ucrt-Routinen nicht mit universellen Windows-Apps oder Microsoft Store-Apps kompatibel sind.|
|[ANSI C-Kompatibilität](../c-runtime-library/ansi-c-compliance.md)|Beschreibt die normgerechte Benennung in der UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Enthält Richtlinien zum Portieren von Programmen zu UNIX.|
|[Windows-Plattformen (CRT)](../c-runtime-library/windows-platforms-crt.md)|Listet die Betriebssysteme auf, die durch CRT unterstützt werden.|
|[Abwärtskompatibilität](../c-runtime-library/backward-compatibility.md)|Beschreibt, wie alte CRT-Namen neuen zugeordnet werden.|
|[CRT-Bibliotheksfunktionen](../c-runtime-library/crt-library-features.md)|Bietet eine Übersicht über die CRT-Bibliotheksdateien (.lib) und über die zugehörigen Compileroptionen.|
