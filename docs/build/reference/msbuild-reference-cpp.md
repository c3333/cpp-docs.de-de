---
title: MSBuild-Referenz C++ für Projekte in Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: ec1285a760d438a94863181a1b099e6db153c268
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168901"
---
# <a name="msbuild-reference-for-c-projects"></a>MSBuild-Referenz für C++-Projekte

MSBuild ist das systemeigene Buildsystem für alle Projekte in Visual Studio C++ , einschließlich Projekten. Wenn Sie ein Projekt in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen, wird das Tool "MSBuild. exe" aufgerufen, das wiederum die vcxproj-Projektdatei und verschiedene. targets-und. Constants-Dateien verwendet. Im Allgemeinen wird dringend empfohlen, die Visual Studio-IDE zum Festlegen von Projekteigenschaften und zum Aufrufen von MSBuild zu verwenden. Das manuelle Bearbeiten von Projektdateien kann zu schwerwiegenden Problemen führen, wenn dies nicht ordnungsgemäß erfolgt.

Wenn Sie MSBuild aus irgendeinem Grund direkt über die Befehlszeile verwenden möchten, finden Sie weitere [Informationen unter Verwenden von MSBuild über die Befehlszeile](../msbuild-visual-cpp.md). Weitere Informationen zu MSBuild im Allgemeinen finden Sie unter [MSBuild](/visualstudio/msbuild/msbuild) in der Visual Studio-Dokumentation.

## <a name="in-this-section"></a>In diesem Abschnitt

[MSBuild-Interna für C++-Projekte](msbuild-visual-cpp-overview.md)<br/>
Informationen zum Speichern und verbrauchen von Eigenschaften und Zielen.

[Gängige Makros für Buildbefehle und -eigenschaften](common-macros-for-build-commands-and-properties.md)<br/>
Beschreibt Makros (Kompilierzeit Konstanten), die zum Definieren von Eigenschaften verwendet werden können, z. b. Pfade und Produktversionen.

[Für C++ Projekte erstellte Dateitypen](file-types-created-for-visual-cpp-projects.md)<br/>
Beschreibt die verschiedenen Arten von Dateien, die von Visual Studio für verschiedene Projekttypen erstellt werden.

[Visual Studio C++ -Projektvorlagen](visual-cpp-project-types.md)<br>
Beschreibt die auf MSBuild basierenden Projekttypen, die für C++verfügbar sind.

[Neue C++-Elementvorlagen](using-visual-cpp-add-new-item-templates.md)<br>
Beschreibt Quelldateien und andere Elemente, die Sie einem Visual Studio-Projekt hinzufügen können.

[Vorkompilierte Header Dateien](../creating-precompiled-header-files.md) Verwenden vorkompilierter Header Dateien und Erstellen eines eigenen benutzerdefinierten vorkompilierten Codes, um Buildzeiten zu beschleunigen.

[Referenz zu Visual Studio-Projekteigenschaften](property-pages-visual-cpp.md)<br/>
Referenz Dokumentation für Projekteigenschaften, die in der Visual Studio-IDE festgelegt sind.

## <a name="see-also"></a>Weitere Informationen

[Referenz zur C/C++-Erstellung](c-cpp-building-reference.md)
