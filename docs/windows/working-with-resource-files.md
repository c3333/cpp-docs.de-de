---
title: Arbeiten mit Ressourcendateien (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 3e387a1cefb6577760a34c7957d4f5019b1d49ef
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502902"
---
# <a name="working-with-resource-files"></a>Arbeiten mit Ressourcendateien

> [!WARNING]
> Dieser Abschnitt gilt für in C++ erstellte Windows-Desktopanwendungen.
>
> Weitere Informationen zu Ressourcen in universelle Windows-Plattform in C++ geschriebenen apps finden Sie unter [Definieren von App-Ressourcen](/windows/uwp/app-resources/)oder Hinzufügen von Ressourcen zu C++/CLI (verwalteten) Projekten. Weitere Informationen finden Sie unter [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index) im Entwicklerhandbuch zu .NET Framework.

Ressourcen können aus einer Vielzahl von Elementen bestehen, wie z. b.:

- Schnittstellen Elemente, die dem Benutzerinformationen bereitstellen, z. b. eine Bitmap, ein Symbol oder einen Cursor.
- Benutzerdefinierte Ressourcen, die Daten-und Anwendungsanforderungen enthalten.
- Versions Ressourcen, die von Setup-APIs verwendet werden.
- Menü-und Dialogfeld Ressourcen.

Sie können Ihrem Projekt neue Ressourcen hinzufügen und diese mit dem entsprechenden Ressourcen-Editor ändern. Die meisten Visual C++-Assistenten generieren automatisch ein RC-Datei für Ihr Projekt.

> [!NOTE]
> Die **Ressourcen-Editoren** und **Ressourcenansicht** sind in Express-Editionen nicht verfügbar.

Informationen zum manuellen Hinzufügen von Ressourcen Dateien zu verwalteten Projekten finden Sie unter [Erstellen von Ressourcen Dateien für Desktop-Apps](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Dieser Artikel enthält Informationen zum Zugreifen auf Ressourcen, zum Anzeigen statischer Ressourcen und zum Zuweisen von Ressourcen Zeichenfolgen zu Eigenschaften.

Informationen zum Globalisieren und Lokalisieren von Ressourcen in verwalteten apps finden Sie unter [Globalisieren und Lokalisieren von .NET Framework Anwendungen](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>In diesem Abschnitt

[Ressourcen Dateien](../windows/resource-files-visual-studio.md)<br/>
Beschreibt Ressourcen Dateien und wie Sie in Windows-Desktop Anwendungen verwendet werden. Enthält auch Links zu Artikeln, in denen die Verwendung von Ressourcen Dateien beschrieben wird.

[Ressourcen Bezeichner (Symbole)](../windows/symbols-resource-identifiers.md)<br/>
Beschreiben Symbole und bieten Informationen zur Verwendung des Dialogfelds **Ressourcensymbole** , um Symbole in Ihren Projekten zu verwalten.

[Ressourcen-Editoren](../windows/resource-editors.md)<br/>
Beschreibt die Ressourcen-Editoren, die in Visual Studio bereitgestellt werden, und die Ressourcentypen, die Sie mit jedem Editor ändern können. Bietet auch Links zu detaillierten Informationen zur Verwendung der einzelnen Editor.

## <a name="related-sections"></a>Verwandte Abschnitte

[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
Enthält Links zur Visual C++-Dokumentation

[Sprechen Sie mit uns](/visualstudio/ide/talk-to-us)<br/>
Bietet Links zu Informationen über die Verwendung des Dokumentationssatzes, Support-Kontaktdaten sowie über die Bereitstellung von Barrierefreiheitsfunktionen.

## <a name="see-also"></a>Weitere Informationen

[Windows-Desktop Anwendungen](./desktop-applications-visual-cpp.md)<br/>
[Menüs und weitere Ressourcen](/windows/win32/menurc/resources)
