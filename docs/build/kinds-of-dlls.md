---
title: Arten von DLLs
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328501"
---
# <a name="kinds-of-dlls"></a>Arten von DLLs

Anhand der Informationen unter diesem Thema können Sie feststellen, welche Art von DLL erstellt werden sollte.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Verschiedene Arten von DLLs verfügbar

Mit Visual Studio können Sie Win32-DLLs in C oder C++ erstellen, die nicht die MFC-Bibliothek (Microsoft Foundation Class) verwenden. Um ein MFC-fremdes DLL-Projekt zu erstellen, verwenden Sie den Win32-Anwendungs-Assistenten.

Die MFC-Bibliothek selbst ist über den MFC-DLL-Assistenten entweder in Static Link Libraries oder in einer Reihe von DLLs verfügbar. Wenn Ihre DLL MFC verwendet, unterstützt Visual Studio drei verschiedene DLL-Entwicklungsszenarien:

- Erstellen einer regulären MFC-DLL, die MFC statisch verknüpft

- Erstellen einer regulären MFC-DLL, die MFC dynamisch verknüpft

- Erstellen einer MFC-Erweiterungs-DLL, die immer dynamisch mit MFC verknüpft wird

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [MFC-fremde DLLs: Übersicht](non-mfc-dlls-overview.md)

- [Reguläre, statisch mit MFC verknüpfte MFC-DLLs](regular-dlls-statically-linked-to-mfc.md)

- [Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC extension DLLs: Overview (MFC-Erweiterungs-DLLs: Übersicht)](extension-dlls-overview.md)

- [Zu verwendender DLL-Typ](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Entscheiden, welche Art von DLL verwendet werden soll

Wenn Ihre DLL MFC nicht verwendet, verwenden Sie Visual Studio, um eine Nicht-MFC Win32-DLL zu erstellen. Das (statische oder dynamische) Verknüpfen einer DLL mit MFC beansprucht erhebliche Festplattenspeicher- und Arbeitsspeicherkapazitäten. Sie sollten eine Verknüpfung mit MFC nur dann vorsehen, wenn MFC von der DLL auch tatsächlich verwendet wird.

Wenn Ihre DLL MFC verwendet und entweder von MFC- oder Nicht-MFC-Anwendungen verwendet wird, müssen Sie entweder eine reguläre MFC-DLL erstellen, die dynamisch mit MFC verknüpft ist, oder eine reguläre MFC-DLL, die statisch mit MFC verknüpft ist. In den meisten Fällen möchten Sie wahrscheinlich eine normale MFC-DLL verwenden, die dynamisch mit MFC verknüpft ist, da die Dateigröße der DLL viel kleiner ist und die Speichereinsparungen durch die Verwendung der freigegebenen Version von MFC erheblich sein können. Bei einer statischen Verknüpfung mit MFC wird die DLL größer, und es wird möglicherweise mehr Arbeitsspeicher benötigt, da eine eigene Kopie des MFC-Bibliothekscodes geladen wird.

Das Erstellen einer DLL, die dynamisch mit MFC verknüpft wird, verläuft schneller als das Erstellen einer DLL, die statisch mit MFC verknüpft wird, da MFC selbst in diesem Fall nicht verknüpft werden muss. Dies trifft insbesondere auf Debugbuilds zu, bei denen der Linker die Debuginformationen komprimieren muss. Durch das Verknüpfen mit einer DLL, die bereits Debuginformationen enthält, bleiben innerhalb der DLL weniger Debuginformationen zu komprimieren.

Ein Nachteil der dynamischen Verknüpfung mit MFC besteht darin, dass Sie die gemeinsam genutzten DLLs, nämlich Mfcx0.dll und Msvcrxx.dll (oder ähnliche Dateien), zusammen mit der DLL verteilen müssen. Die MFC-DLLs können frei verteilt werden, sie müssen jedoch noch im Setupprogramm installiert werden. Darüber hinaus müssen Sie Msvcrxx.dll mitliefern. Diese Datei enthält die C-Laufzeitbibliothek, die sowohl vom Programm als auch von den MFC-DLLs selbst verwendet wird.

Wenn Ihre DLL nur von ausführbaren MFC-Dateien verwendet wird, haben Sie die Wahl zwischen dem Erstellen einer regulären MFC-DLL oder einer MFC-Erweiterungs-DLL. Wenn Ihre DLL wiederverwendbare Klassen implementiert, die von den vorhandenen MFC-Klassen abgeleitet sind, oder Sie MFC-abgeleitete Objekte zwischen der Anwendung und der DLL übergeben müssen, müssen Sie eine MFC-Erweiterungs-DLL erstellen.

Wenn die DLL dynamisch mit MFC verknüpft wird, können die MFC-DLLs zusammen mit der DLL verteilt werden. Diese Architektur ist besonders geeignet, wenn die Klassenbibliothek von mehreren ausführbaren Dateien gemeinsam genutzt wird, um Festplattenspeicher zu sparen und die Arbeitsspeicherauslastung zu minimieren.

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [MFC-fremde DLLs: Übersicht](non-mfc-dlls-overview.md)

- [Reguläre, statisch mit MFC verknüpfte MFC-DLLs](regular-dlls-statically-linked-to-mfc.md)

- [Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC extension DLLs: Overview (MFC-Erweiterungs-DLLs: Übersicht)](extension-dlls-overview.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
