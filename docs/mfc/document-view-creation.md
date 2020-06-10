---
title: Dokument-Sicht Erstellung
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
ms.openlocfilehash: 5441827188f5bff98638cc85cd29e2efd79f8ae8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620340"
---
# <a name="documentview-creation"></a>Erstellen von Dokument/Ansicht

Das Framework stellt Implementierungen der **neuen** und **geöffneten** Befehle (unter anderem) im Menü **Datei** bereit. Die Erstellung eines neuen Dokuments und der zugehörigen Ansicht und des Rahmen Fensters ist ein kooperativer Aufwand zwischen dem Anwendungs Objekt, einer Dokument Vorlage, dem neu erstellten Dokument und dem neu erstellten Rahmen Fenster. In der folgenden Tabelle ist zusammengefasst, welche Objekte was erstellen.

### <a name="object-creators"></a>Objekt Ersteller

|Creator|Erstellt|
|-------------|-------------|
|Anwendungsobjekt|Dokument Vorlage|
|Dokument Vorlage|Dokument|
|Dokument Vorlage|Rahmen Fenster|
|Rahmen Fenster|Sicht|

## <a name="see-also"></a>Siehe auch

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokumentvorlagen](document-template-creation.md)<br/>
[Beziehungen zwischen MFC-Objekten](relationships-among-mfc-objects.md)<br/>
[Erstellen neuer Dokumente, Fenster und Ansichten](creating-new-documents-windows-and-views.md)
