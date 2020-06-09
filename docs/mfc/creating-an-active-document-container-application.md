---
title: Erstellen einer Containeranwendung für aktive Dokumente
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616354"
---
# <a name="creating-an-active-document-container-application"></a>Erstellen einer Containeranwendung für aktive Dokumente

Die einfachste und am meisten empfohlene Methode zum Erstellen einer aktiven Dokument Containeranwendung ist das Erstellen einer MFC-exe-Containeranwendung mithilfe des MFC-Anwendungs-Assistenten und das anschließende Ändern der Anwendung zur Unterstützung der aktiven Dokument Kapselung.

#### <a name="to-create-an-active-document-container-application"></a>So erstellen Sie eine aktive Dokument Containeranwendung

1. Klicken Sie im Menü **Datei** im Menü " **neu** " auf **Projekt**.

1. Klicken Sie im linken Bereich auf **Visual C++** Projekttyp.

1. Wählen Sie im rechten Bereich die Option **MFC-Anwendung** aus.

1. Nennen Sie das Projekt *MyProj*, und klicken Sie auf **OK**.

1. Wählen Sie die Seite **Verbund Dokument Unterstützung** aus.

1. Wählen Sie die Option **Container** oder **Container/voll Server** aus.

1. Aktivieren Sie das Kontrollkästchen **Container für aktive Dokumente** .

1. Klicken Sie auf **Fertig stellen**.

1. Wenn der MFC-Anwendungs-Assistent das Erstellen der Anwendung abgeschlossen hat, öffnen Sie die folgenden Dateien mit Projektmappen-Explorer:

   - *Myprojview. cpp*

1. Nehmen Sie in *myprojview. cpp*die folgenden Änderungen vor:

   - Ersetzen Sie in `CMyProjView::OnPreparePrinting` den Funktions Inhalt durch den folgenden Code:

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting`bietet Druckunterstützung. Dieser Code ersetzt `DoPreparePrinting` , d. h. die Standarddruck Vorbereitung.

   Die aktive Dokument Kapselung bietet ein verbessertes Druck Schema:

   - Sie können zuerst das aktive Dokument über seine `IPrint` -Schnittstelle aufzurufen und es an sich selbst drucken. Dies unterscheidet sich von der vorherigen OLE-Kapselung, bei der der Container ein Bild des enthaltenen Elements auf dem Drucker Objekt Rendering musste `CDC` .

   - Wenn dies nicht möglich ist, weisen Sie das enthaltene Element an, sich selbst über seine `IOleCommandTarget` Schnittstelle auszugeben

   - Wenn dies nicht möglich ist, erstellen Sie ein eigenes Rendering des Elements.

   Die statischen Member `COleDocObjectItem::OnPrint` -Funktionen und `COleDocObjectItem::OnPreparePrinting` , wie im vorherigen Code implementiert, dieses verbesserte Druck Schema verarbeiten.

1. Fügen Sie eine beliebige Implementierung Ihrer eigenen hinzu, und erstellen Sie die Anwendung.

## <a name="see-also"></a>Siehe auch

[Active Document-Container](active-document-containment.md)
