---
title: Eigenschaftenseiten für das Tool XML-Dokument-Generator
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: 9f10ddf98c238120750e72644779a6ad74af2d1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171631"
---
# <a name="xml-document-generator-tool-property-pages"></a>Eigenschaftenseiten für das Tool XML-Dokument-Generator

Die Eigenschaftenseite des XML-Dokument-Generators stellt die Funktionen der „xdcmake.exe“ zur Verfügung. Die „xdcmake.exe“ führt XDC-Dateien in eine XML-Datei zusammen, wenn Ihr Quellcode Dokumentationskommentare enthält und [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](doc-process-documentation-comments-c-cpp.md) angegeben ist. Informationen zum Hinzufügen von Dokumentationskommentaren in Quellcode finden Sie unter [Recommended Tags for Documentation Comments (Empfohlene Tags für Dokumentationskommentare)](recommended-tags-for-documentation-comments-visual-cpp.md).

> [!NOTE]
>  Die Optionen von „xdcmake.exe“ in der Entwicklungsumgebung (Eigenschaftenseiten) unterscheiden sich von den Optionen, wenn „xdcmake.exe“ in der Befehlszeile verwendet wird. Informationen zur Verwendung von „xdcmake.exe“ in der Befehlszeile finden Sie unter [XDCMake Reference (XDCMake-Verweis)](xdcmake-reference.md).

## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente

- **Startbanner unterdrücken**

   Copyrightmeldung unterdrücken

- **Zusätzliche Dokumentdateien**

   Zusätzliche Verzeichnisse, in denen das Projektsystem nach XDC-Dateien suchen soll. XDCMake sucht immer nach XDC-Dateien, die vom Projekt generiert wurden. Mehrere Verzeichnisse können angegeben werden.

- **Ausgabedokumentdatei**

   Der Name und der Speicherort des Verzeichnisses der XML-Ausgabedatei. Weitere Informationen zum Verwenden von Makros zum Angeben von Verzeichnis Speicherorten finden Sie unter [Allgemeine Makros für Buildbefehle und-Eigenschaften](common-macros-for-build-commands-and-properties.md) .

- **Dokumentbibliothekabhängigkeiten**

   Wenn Ihr Projekt von einem LIB-Projekt in der Projektmappe abhängig ist, können Sie XDC-Dateien des LIB-Projekts in die XML-Dateien für das aktuelle Projekt verarbeiten.

## <a name="see-also"></a>Weitere Informationen

[C++Referenz zur Projekteigenschaften Seite](property-pages-visual-cpp.md)
