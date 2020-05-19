---
title: Festlegen der Exportmethode
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273736"
---
# <a name="determine-which-exporting-method-to-use"></a>Festlegen der Exportmethode

Sie können Funktionen auf zwei Weisen exportieren – mit einer DEF-Datei oder mit dem Schlüsselwort `__declspec(dllexport)`. Berücksichtigen Sie bei der Entscheidung, welche Methode für Ihre DLL besser geeignet ist, die folgenden Fragestellungen:

- Planen Sie später weitere Funktionen zu exportieren?

- Wird Ihre DLL nur von Anwendungen verwendet, die Sie neu erstellen können, oder wird sie von Anwendungen verwendet, die Sie nicht neu erstellen können, z. B. Anwendungen, die von Drittanbietern erstellt wurden?

## <a name="pros-and-cons-of-using-def-files"></a>Vor- und Nachteile der Verwendung von DEF-Dateien

Durch das Exportieren von Funktionen in eine DEF-Datei erhalten Sie die Kontrolle über die Exportordnungszahlen. Wenn Sie der DLL eine exportierte Funktion hinzufügen, können Sie ihr einen höheren Ordnungszahlwert als jeder anderen exportierten Funktion zuweisen. Wenn Sie dies tun, müssen Anwendungen, die implizites Verknüpfen verwenden, nicht neu mit der Importbibliothek verknüpft werden, die die neue Funktion enthält. Dies ist sehr praktisch, wenn Sie eine DLL für viele Anwendungen entwerfen, da Sie neue Funktionen hinzufügen und zudem sicherstellen können, dass sie mit den Anwendungen, die sich bereits auf sie verlassen, weiterhin ordnungsgemäß funktioniert. Die MFC-DLLs werden beispielsweise mithilfe von DEF-Dateien erstellt.

Ein weiterer Vorteil bei der Verwendung einer DEF-Datei besteht darin, dass Sie das `NONAME`-Attribut verwenden können, um eine Funktion zu exportieren. Dadurch wird nur die Ordnungszahl in die Exporttabelle in der DLL eingefügt. Bei DLLs, die über eine große Anzahl von exportierten Funktionen verfügen, kann durch die Verwendung des `NONAME`-Attributs die Größe der DLL-Datei reduziert werden. Informationen dazu, wie Sie eine Moduldefinitionsanweisung schreiben, finden Sie unter [Regeln für Moduldefinitionsanweisungen](reference/rules-for-module-definition-statements.md). Informationen zum Exportieren von Ordnungszahlen finden Sie unter [Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Ein Nachteil bei der Verwendung einer DEF-Datei besteht darin, dass Sie beim Exportieren von Funktionen in einer C++-Datei entweder die dekorierten Namen in die DEF-Datei einfügen oder die exportierten Funktionen mithilfe von extern "C" definieren müssen, um die vom MSVC-Compiler durchgeführte Namensergänzung zu vermeiden.

Wenn Sie die dekorierten Namen in die DEF-Datei einfügen müssen, können Sie diese mithilfe des Tools [DUMPBIN](reference/dumpbin-reference.md) oder mit der [/MAP](reference/map-generate-mapfile.md)-Linkeroption abrufen. Die dekorierten Namen, die vom Compiler erzeugt werden, sind compilerspezifisch. Wenn Sie daher die vom Compiler erzeugten dekorierten Namen in eine DEF-Datei einfügen, müssen die Anwendungen, die auf die DLL verweisen, ebenfalls mit der gleichen Version des Compilers erstellt werden, sodass die dekorierten Namen in der aufrufenden Anwendung mit den exportierten Namen in der DEF-Datei der DLL übereinstimmen.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>Vor- und Nachteile der Verwendung von „__declspec(dllexport)“

Die Verwendung von `__declspec(dllexport)` ist praktisch, da Sie sich nicht darum kümmern müssen, eine DEF-Datei zu verwalten und die dekorierten Namen der exportierten Funktionen abzurufen. Die Nützlichkeit dieser Exportmethode wird jedoch durch die Anzahl der verknüpften Anwendungen beschränkt, die Sie neu erstellen möchten. Wenn Sie die DLL mit neuen Exporten neu erstellen, müssen Sie auch die Anwendungen neu erstellen, da sich möglicherweise die dekorierten Namen für exportierte C++-Funktionen ändern, wenn Sie eine andere Version des Compilers für die Neuerstellung verwenden.

### <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

- [Dekorierte Namen](reference/decorated-names.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
