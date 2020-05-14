---
title: 'Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs'
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220745"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs

MFC bietet ab Version 7.0 erweiterte Unterstützung für Satelliten-DLLs – eine Funktion, die den Entwickler bei der Erstellung von Anwendungen unterstützt, die für mehrere Sprachen lokalisiert sind. Eine Satelliten-DLL ist eine [reine Ressourcen-DLL](creating-a-resource-only-dll.md), die die für eine bestimmte Sprache lokalisierten Ressourcen einer Anwendung enthält. Wenn die Anwendung mit der Ausführung beginnt, lädt MFC automatisch die lokalisierte Ressource, die für die Umgebung am besten geeignet ist. Sie können beispielsweise über eine Anwendung mit englischen Sprachressourcen mit zwei Satelliten-DLLs verfügen, von denen eine die französische Übersetzung Ihrer Ressourcen und die andere die deutsche Übersetzung enthält. Wenn die Anwendung auf einem englischsprachigen System ausgeführt wird, verwendet sie die englischen Ressourcen. Wenn sie auf einem französischen System ausgeführt wird, werden die französischen Ressourcen verwendet. Wird sie hingegen auf einem deutschen System ausgeführt, werden die deutschen Ressourcen verwendet.

Zur Unterstützung lokalisierter Ressourcen in einer MFC-Anwendung versucht MFC, eine Satelliten-DLL zu laden, die in einer bestimmten Sprache lokalisierte Ressourcen enthält. Satelliten-DLLs tragen den Namen *AnwendungsnameXXX*.dll, wobei *Anwendungsname* für den Namen der ausführbaren Datei bzw. DLL-Datei steht, die MFC verwendet. *XXX* ist der aus drei Buchstaben bestehende Code für die Sprache der Ressourcen (z. B. „ENU“ oder „DEU“).

MFC versucht, die Ressourcen-DLL für jede der folgenden Sprachen in der unten angegebenen Reihenfolge zu laden, und stoppt, wenn eine dieser DLL gefunden wird:

1. Die Standardbenutzeroberflächensprache des aktuellen Benutzers, wie von der GetUserDefaultUILanguage() Win32-API zurückgegeben.

1. Die Standardbenutzeroberflächensprache des aktuellen Benutzers ohne bestimmte Teilsprache (d. h. ENC [kanadisches Englisch] wird zu ENU [Englisch (USA)]).

1. Die Standardbenutzeroberflächensprache des Systems, wie von der GetSystemDefaultUILanguage()-API zurückgegeben. Auf anderen Plattformen ist dies die Sprache des Betriebssystems.

1. Die Standardbenutzeroberflächensprache des Systems, ohne dass eine bestimmte Teilsprache vorhanden ist.

1. Eine Pseudosprache mit dem Dreibuchstabencode LOC.

Wenn MFC keine Satelliten-DLLs findet, werden jedwede Ressourcen verwendet, die in der Anwendung selbst enthalten sind.

Nehmen wir beispielsweise an, dass die Anwendung LangExample.exe MFC verwendet und auf einem System mit mehreren Benutzeroberflächen ausgeführt wird. Die Benutzeroberflächensprache des Systems ist ENU [Englisch (USA)], und die Benutzeroberflächensprache des aktuellen Benutzers ist auf FRC [Französisch (Kanada)] festgelegt. MFC sucht in dieser Reihenfolge nach den folgenden DLLs:

1. LangExampleFRC.dll (Benutzeroberflächensprache des Benutzers).

1. LangExampleFRA.dll (Benutzeroberflächensprache des Benutzers ohne die Teilsprache, in diesem Beispiel Französisch (Frankreich).

1. LangExampleENU.dll (Benutzeroberflächensprache des Systems).

1. LangExampleLOC.dll.

Wenn keine dieser DLLs gefunden wird, verwendet MFC die Ressourcen in LangExample.exe.

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)<br/>
[TN057: Lokalisierung von MFC-Komponenten](../mfc/tn057-localization-of-mfc-components.md)
