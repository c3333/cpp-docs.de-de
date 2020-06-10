---
title: 'Beispiel für einen Active Document-Container: Office Binder'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: fe9ccb5b78d9a60c5b8b2a19fe0818a8e1682f00
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623121"
---
# <a name="example-of-active-document-containment-office-binder"></a>Beispiel für einen Active Document-Container: Office Binder

Der Microsoft Office Binder ist ein Beispiel für einen aktiven Dokument Container. Ein Office-Binder umfasst zwei Hauptbereiche, wie Container in der Regel. Der linke Bereich enthält Symbole, die aktiven Dokumenten im Binder entsprechen. Jedes Dokument wird als *Abschnitt* innerhalb des Binders bezeichnet. Beispielsweise kann ein Binder Word-Dokumente, PowerPoint-Dateien, Excel-Kalkulations Tabellen usw. enthalten.

Wenn Sie im linken Bereich auf ein Symbol klicken, wird das entsprechende aktive Dokument aktiviert. Im rechten Bereich des Binders wird dann der Inhalt des derzeit ausgewählten aktiven Dokuments angezeigt.

Wenn Sie ein Word-Dokument in einem Binder öffnen und aktivieren, werden die Word-Menüleiste und Symbolleisten oben im Ansichts Rahmen angezeigt, und Sie können den Inhalt des Dokuments mit einem beliebigen Word-Befehl oder-Tool bearbeiten. Die Menüleiste ist jedoch eine Kombination aus den Menüleisten des Binders und des Worts. Da sowohl Binder als auch Word **Hilfe** Menüs aufweisen, werden die Inhalte der entsprechenden Menüs zusammengeführt. Aktive Dokument Container, wie z. b. Office-Binder, bieten automatisch **Hilfe** Menü Zusammenführung; Weitere Informationen finden Sie unter Zusammenführen von [Hilfe Menüs](help-menu-merging.md).

Wenn Sie ein aktives Dokument mit einem anderen Anwendungstyp auswählen, ändert sich die Schnittstelle des Binders, damit Sie dem Anwendungstyp des aktiven Dokuments entspricht. Wenn ein Binder z. b. eine Excel-Tabelle enthält, werden Sie feststellen, dass sich die Menüs im Binder ändern, wenn Sie den Excel-Tabellenbereich auswählen.

Es gibt natürlich andere mögliche Arten von Containern neben Binders. Im Datei-Explorer wird die typische Dual-Pane-Schnittstelle verwendet, in der im linken Bereich ein Struktur Steuerelement verwendet wird, um eine hierarchische Liste der Verzeichnisse in einem Laufwerk oder Netzwerk anzuzeigen, während im rechten Bereich die Dateien angezeigt werden, die im aktuell ausgewählten Verzeichnis enthalten sind. Ein Internet Browser-Containertyp (z. b. Microsoft Internet Explorer), anstatt eine Dual-Pane-Schnittstelle zu verwenden, verfügt normalerweise über einen einzelnen Frame und ermöglicht die Navigation mithilfe von Hyperlinks.

## <a name="see-also"></a>Siehe auch

[Active Document-Container](active-document-containment.md)
