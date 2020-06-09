---
title: Dokumentvorlagen und der Erstellungs Vorgang für Dokumente
ms.date: 11/19/2018
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
ms.openlocfilehash: b96a11926927e89890ca268dcff7d347079b25fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615773"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten

Um den komplexen Prozess der Erstellung von Dokumenten mit den zugehörigen Sichten und Rahmen Fenstern zu verwalten, verwendet das Framework zwei Dokumentvorlagen Klassen: [CSingleDocTemplate](reference/csingledoctemplate-class.md) für SDI-Anwendungen und [CMultiDocTemplate](reference/cmultidoctemplate-class.md) für MDI-Anwendungen. Ein `CSingleDocTemplate` -Typ kann jeweils jeweils ein Dokument erstellen und speichern. Ein `CMultiDocTemplate` speichert eine Liste von vielen geöffneten Dokumenten eines Typs.

Einige Anwendungen unterstützen mehrere Dokumenttypen. Beispielsweise kann eine Anwendung Textdokumente und Grafik Dokumente unterstützen. Wenn der Benutzer in einer solchen Anwendung im Menü Datei den Befehl Neu auswählt, wird in einem Dialogfeld eine Liste der möglichen neuen Dokumenttypen angezeigt, die geöffnet werden können. Für jeden unterstützten Dokumenttyp verwendet die Anwendung ein unterschiedliches Dokumentvorlagen Objekt. Die folgende Abbildung veranschaulicht die Konfiguration einer MDI-Anwendung, die zwei Dokumenttypen unterstützt und mehrere geöffnete Dokumente anzeigt.

![MDI-Anwendung mit zwei Dokumenttypen](../mfc/media/vc387h1.gif "MDI-Anwendung mit zwei Dokumenttypen") <br/>
MDI-Anwendung mit zwei Dokumenttypen

Dokumentvorlagen werden vom Anwendungs Objekt erstellt und verwaltet. Eine der wichtigsten Aufgaben, die bei der Funktion der Anwendung ausgeführt werden `InitInstance` , besteht darin, eine oder mehrere Dokumentvorlagen der entsprechenden Art zu erstellen. Diese Funktion wird unter [Erstellen von Dokumentvorlagen](document-template-creation.md)beschrieben. Das Anwendungs Objekt speichert einen Zeiger auf jede Dokument Vorlage in der Vorlagenliste und stellt eine Schnittstelle zum Hinzufügen von Dokumentvorlagen bereit.

Wenn Sie zwei oder mehr Dokumenttypen unterstützen müssen, müssen Sie für jeden Dokumenttyp einen zusätzlichen [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate) -Rückruf hinzufügen.

Ein Symbol wird für jede Dokument Vorlage basierend auf der Position in der Liste der Dokumentvorlagen der Anwendung registriert. Die Reihenfolge der Dokumentvorlagen wird durch die Reihenfolge bestimmt, in der Sie mit Aufrufen von hinzugefügt werden `AddDocTemplate` . MFC geht davon aus, dass es sich bei der ersten Symbol Ressource in der Anwendung um das Anwendungssymbol handelt, die nächste Symbol Ressource das erste Dokument Symbol und so weiter.

Beispielsweise ist eine Dokument Vorlage das dritte von drei für die Anwendung. Wenn in der Anwendung am Index 3 eine Symbol Ressource vorhanden ist, wird dieses Symbol für die Dokument Vorlage verwendet. Wenn dies nicht der Wert ist, wird das Symbol bei Index 0 als Standard verwendet.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](general-mfc-topics.md)<br/>
[Erstellen von Dokumentvorlagen](document-template-creation.md)<br/>
[Erstellen von Dokument/Ansicht](document-view-creation.md)<br/>
[Beziehungen zwischen MFC-Objekten](relationships-among-mfc-objects.md)<br/>
[Erstellen neuer Dokumente, Fenster und Ansichten](creating-new-documents-windows-and-views.md)
