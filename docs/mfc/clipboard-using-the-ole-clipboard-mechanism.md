---
title: 'Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: da0b99e6c9c803f3c3a4c09d67853649a4bac314
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626054"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus

OLE verwendet Standardformate und einige OLE-spezifische Formate zum Übertragen von Daten über die Zwischenablage.

Wenn Sie Daten aus einer Anwendung Ausschneiden oder kopieren, werden die Daten in der Zwischenablage gespeichert, damit Sie später in Einfügevorgängen verwendet werden. Diese Daten befinden sich in einer Vielzahl von Formaten. Wenn ein Benutzer sich für das Einfügen von Daten aus der Zwischenablage entscheidet, kann die Anwendung auswählen, welche dieser Formate verwendet werden sollen. Die Anwendung sollte geschrieben werden, um das Format auszuwählen, das die meisten Informationen bereitstellt, es sei denn, der Benutzer fordert explizit ein bestimmtes Format mithilfe von "Einfügen" an. Bevor Sie fortfahren, sollten Sie die Themen zu [Datenobjekten und Datenquellen (OLE)](data-objects-and-data-sources-ole.md) lesen. Sie beschreiben die Grundlagen der Funktionsweise von Datenübertragungen und deren Implementierung in Ihren Anwendungen.

Windows definiert eine Reihe von Standardformaten, die zum Übertragen von Daten über die Zwischenablage verwendet werden können. Dazu zählen Metadateien, Text, Bitmaps und andere. OLE definiert auch eine Reihe von OLE-spezifischen Formaten. Bei Anwendungen, die mehr Details benötigen, als von diesen Standardformaten angegeben werden, empfiehlt es sich, eigene benutzerdefinierte Zwischenablage Formate zu registrieren. Verwenden Sie hierfür die Win32-API-Funktion [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

Microsoft Excel registriert z. b. ein benutzerdefiniertes Format für Kalkulations Tabellen. Dieses Format enthält wesentlich mehr Informationen, als z. b. eine Bitmap. Wenn diese Daten in eine Anwendung eingefügt werden, die das Tabellenformat unterstützt, werden alle Formeln und Werte aus der Kalkulations Tabelle beibehalten und können bei Bedarf aktualisiert werden. In Microsoft Excel werden auch Daten in die Zwischenablage eingefügt, sodass Sie als OLE-Element eingefügt werden können. Diese Informationen können von jedem OLE-Dokument Container als eingebettetes Element eingefügt werden. Dieses eingebettete Element kann mithilfe von Microsoft Excel geändert werden. Die Zwischenablage enthält auch eine einfache Bitmap des Bilds des ausgewählten Bereichs in der Tabelle. Dies kann auch in OLE-Dokument Container oder in Bitmap-Editoren wie Paint eingefügt werden. Im Fall einer Bitmap gibt es jedoch keine Möglichkeit, die Daten als Kalkulations Tabelle zu bearbeiten.

Zum Abrufen der maximalen Menge von Informationen aus der Zwischenablage sollten Anwendungen vor dem Einfügen von Daten aus der Zwischenablage diese benutzerdefinierten Formate überprüfen.

Wenn Sie z. b. den Befehl "Ausschneiden" aktivieren möchten, können Sie einen Handler schreiben, der etwa wie folgt aussieht:

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Kopieren und Einfügen von Daten](clipboard-copying-and-pasting-data.md)

- [Hinzufügen anderer Formate](clipboard-adding-other-formats.md)

- [Verwenden der Windows-Zwischenablage](clipboard-using-the-windows-clipboard.md)

- [OLE](ole-background.md)

- [OLE-Datenobjekte und Datenquellen und einheitliche Datenübertragung](data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage](clipboard.md)
