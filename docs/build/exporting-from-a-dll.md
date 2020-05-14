---
title: Exportieren aus einer DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196741"
---
# <a name="exporting-from-a-dll"></a>Exportieren aus einer DLL

Das Layout einer DLL-Datei ähnelt dem einer EXE-Datei. Ein wichtiger Unterschied besteht jedoch darin, dass eine DLL-Datei über eine Exporttabelle verfügt. Die Exporttabelle umfasst die Namen aller Funktionen, die von der DLL in andere ausführbare Dateien exportiert werden. Die Funktionen sind Einstiegspunkte in die DLL. Andere ausführbare Dateien können nur auf die in der Exporttabelle genannten Funktionen zugreifen. Alle weiteren Funktionen in der DLL sind privat, d. h. ausschließlich auf die DLL bezogen. Die Exporttabelle einer DLL kann angezeigt werden, indem das [DUMPBIN](reference/dumpbin-reference.md)-Tool mit der /EXPORTS-Option verwendet wird.

Es gibt zwei Methoden zum Exportieren von Funktionen aus einer DLL:

- Erzeugen Sie eine Moduldefinitionsdatei (.def), und verwenden Sie beim Erstellen der DLL diese DEF-Datei. Verwenden Sie diese Methode, wenn Sie [Funktionen aus einer DLL über die Ordnungszahl statt über den Namen exportieren](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) möchten.

- Verwendung des **__declspec(dllexport)** -Schlüsselwortes in der Funktionsdefinition.

Wenn Sie Funktionen mit einer dieser beiden Methoden exportieren, sollten Sie darauf achten, die [__stdcall](../cpp/stdcall.md)-Aufrufkonvention zu verwenden.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von „AFX_EXT_CLASS“](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Ermitteln der zu verwendenden Exportmethode](determining-which-exporting-method-to-use.md)

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Importieren in eine Anwendung](importing-into-an-application.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Importieren und Exportieren](importing-and-exporting.md)
