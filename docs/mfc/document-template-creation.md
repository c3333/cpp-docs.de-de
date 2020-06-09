---
title: Erstellen von Dokumentvorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 952a383792eb3a4d0a4ed1b3e24dd82f7fa644cf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615785"
---
# <a name="document-template-creation"></a>Erstellen von Dokumentvorlagen

Wenn Sie ein neues Dokument als Reaktion auf einen **neuen** oder **geöffneten** Befehl im Menü **Datei** erstellen, erstellt die Dokument Vorlage auch ein neues Rahmen Fenster, über das das Dokument angezeigt wird.

Der Document-Template-Konstruktor gibt an, welche Typen von Dokumenten, Fenstern und Ansichten von der Vorlage erstellt werden können. Dies wird durch die Argumente bestimmt, die Sie an den Dokumentvorlagen-Konstruktor übergeben. Der folgende Code veranschaulicht die Erstellung einer [CMultiDocTemplate](reference/cmultidoctemplate-class.md) für eine Beispielanwendung:

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

Der Zeiger auf ein neues- `CMultiDocTemplate` Objekt wird als Argument für [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate)verwendet. Die Argumente für den `CMultiDocTemplate` Konstruktor enthalten die Ressourcen-ID, die den Menüs und Zugriffstasten des Dokument Typs zugeordnet ist, und drei Verwendungsmöglichkeiten des [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) Makros. `RUNTIME_CLASS`Gibt das [CRuntimeClass](reference/cruntimeclass-structure.md) -Objekt für die C++-Klasse mit dem Namen als-Argument zurück. Die drei `CRuntimeClass` Objekte, die an den Dokumentvorlagen-Konstruktor übergeben werden, stellen die Informationen bereit, die zum Erstellen neuer Objekte der angegebenen Klassen während der Dokument Erstellung erforderlich sind. Das Beispiel zeigt die Erstellung einer Dokument Vorlage, die `CScribDoc` Objekte mit `CScribView` angefügten Objekten erstellt. Die Sichten werden durch standardmäßige untergeordnete MDI-Rahmen Fenster eingeschlossen.

## <a name="see-also"></a>Siehe auch

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokument/Ansicht](document-view-creation.md)<br/>
[Beziehungen zwischen MFC-Objekten](relationships-among-mfc-objects.md)<br/>
[Erstellen neuer Dokumente, Fenster und Ansichten](creating-new-documents-windows-and-views.md)
