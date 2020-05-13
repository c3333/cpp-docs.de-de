---
title: MSBuild-Referenz für C++-Projekte in Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: 96987a252d12f718025dd55deecad5c6bac26872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336214"
---
# <a name="msbuild-reference-for-c-projects"></a>MSBuild-Referenz für C++-Projekte

MSBuild ist das systemeigene Buildsystem für alle Projekte in Visual Studio, einschließlich C++-Projekten. Wenn Sie ein Projekt in der integrierten Visual Studio-Entwicklungsumgebung (IDE) erstellen, wird das Tool msbuild.exe aufgerufen, das wiederum die .vcxproj-Projektdatei sowie verschiedene .targets- und .props-Dateien verwendet. Im Allgemeinen wird dringend empfohlen, die Visual Studio-IDE zum Festlegen von Projekteigenschaften und aufzurufen von MSBuild zu verwenden. Das manuelle Bearbeiten von Projektdateien kann zu schwerwiegenden Problemen führen, wenn sie nicht ordnungsgemäß ausgeführt werden.

Wenn Sie MSBuild aus irgendeinem Grund direkt über die Befehlszeile verwenden möchten, finden Sie weitere Informationen unter Verwenden von [MSBuild über die Befehlszeile](../msbuild-visual-cpp.md). Weitere Informationen zu MSBuild im Allgemeinen finden Sie unter [MSBuild](/visualstudio/msbuild/msbuild) in der Visual Studio-Dokumentation.

## <a name="in-this-section"></a>In diesem Abschnitt

[MSBuild-Interna für C++-Projekte](msbuild-visual-cpp-overview.md)<br/>
Informationen darüber, wie Eigenschaften und Ziele gespeichert und genutzt werden.

[Allgemeine Makros für Buildbefehle und -eigenschaften](common-macros-for-build-commands-and-properties.md)<br/>
Beschreibt Makros (Kompilierungszeitkonstanten), die zum Definieren von Eigenschaften wie Pfaden und Produktversionen verwendet werden können.

[Für C++-Projekte erstellte Dateitypen](file-types-created-for-visual-cpp-projects.md)<br/>
Beschreibt die verschiedenen Dateitypen, die Visual Studio für verschiedene Projekttypen erstellt.

[Visual Studio C++-Projektvorlagen](visual-cpp-project-types.md)<br>
Beschreibt die MSBuild-basierten Projekttypen, die für C++ verfügbar sind.

[Neue C++-Elementvorlagen](using-visual-cpp-add-new-item-templates.md)<br>
Beschreibt Quelldateien und andere Elemente, die Sie einem Visual Studio-Projekt hinzufügen können.

[Vorkompilierte Headerdateien](../creating-precompiled-header-files.md) Verwenden vorkompilierter Headerdateien und Erstellen eines eigenen benutzerdefinierten vorkompilierten Codes zur Beschleunigung der Buildzeiten.

[Visual Studio-Projekteigenschaftsreferenz](property-pages-visual-cpp.md)<br/>
Referenzdokumentation für Projekteigenschaften, die in der Visual Studio-IDE festgelegt sind.

## <a name="see-also"></a>Siehe auch

[Referenz zur C/C++-Erstellung](c-cpp-building-reference.md)
