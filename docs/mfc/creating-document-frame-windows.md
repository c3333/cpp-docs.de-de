---
title: Erstellen von Dokumentrahmenfenstern
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: e15a2a6bc016bf23bc0decf529b4c3ffeecc3a4c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621947"
---
# <a name="creating-document-frame-windows"></a>Erstellen von Dokumentrahmenfenstern

Die [Dokument-](document-view-creation.md) /ansichterstellung zeigt, wie das [CDocTemplate](reference/cdoctemplate-class.md) -Objekt die Erstellung des Frame Fensters, des Dokuments und der Ansicht orchestriert. Drei [CRuntimeClass](reference/cruntimeclass-structure.md) -Argumente für den `CDocTemplate` Konstruktor geben das Frame Fenster, das Dokument und die Ansichts Klassen an, die von der Dokument Vorlage dynamisch erstellt werden, als Reaktion auf Benutzer Befehle wie den neuen Befehl im Menü Datei oder den Befehl neuer Fenster in einem MDI-Fenstermenü. Diese Informationen werden von der Dokument Vorlage für die spätere Verwendung gespeichert, wenn ein Rahmen Fenster für eine Ansicht und ein Dokument erstellt wird.

Damit der [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) Mechanismus ordnungsgemäß funktioniert, müssen die abgeleiteten Rahmen Fenster Klassen mit dem [DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate) -Makro deklariert werden. Dies liegt daran, dass das Framework Dokument Rahmen Fenster mithilfe des dynamischen Konstruktions Mechanismus der-Klasse erstellen muss `CObject` .

Wenn der Benutzer einen Befehl auswählt, mit dem ein Dokument erstellt wird, ruft das Framework die Dokument Vorlage auf, um das Dokument Objekt, seine Ansicht und das Rahmen Fenster zu erstellen, in dem die Ansicht angezeigt wird. Wenn das Dokument Rahmen Fenster erstellt wird, erstellt die Dokument Vorlage ein Objekt der entsprechenden Klasse – eine Klasse, die von [CFrameWnd](reference/cframewnd-class.md) für eine SDI-Anwendung oder von [CMDIChildWnd](reference/cmdichildwnd-class.md) für eine MDI-Anwendung abgeleitet wurde. Das Framework ruft dann die [LoadFrame](reference/cframewnd-class.md#loadframe) -Member-Funktion des Frame-Window-Objekts auf, um Erstellungs Informationen aus den Ressourcen zu erhalten und das Windows-Fenster zu erstellen. Das Framework fügt das Fenster Handle an das Rahmen Fenster Objekt an. Anschließend wird die Ansicht als untergeordnetes Fenster des Dokument Rahmen Fensters erstellt.

Verwenden Sie Vorsicht bei der Entscheidung [, wann das von](when-to-initialize-cwnd-objects.md) abgeleitete Objekt initialisiert werden soll `CWnd` .

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Ableiten einer Klasse von CObject (der dynamische Erstellungs Mechanismus)](deriving-a-class-from-cobject.md)

- [Dokument-/ansichterstellung (Vorlagen und Rahmen Fenster Erstellung)](document-view-creation.md)

- [Zerstören von Rahmenfenstern](destroying-frame-windows.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
