---
title: 'ActiveX-Steuerelementcontainer: Manuelles Aktivieren von ActiveX-Steuerelementcontainern'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625104"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX-Steuerelementcontainer: Manuelles Aktivieren von ActiveX-Steuerelementcontainern

Wenn Sie die Unterstützung für ActiveX-Steuerelemente beim Verwenden des MFC-Anwendungs-Assistenten zum Generieren der Anwendung nicht aktiviert haben, müssen Sie diese Unterstützung manuell hinzufügen. In diesem Artikel wird der Prozess zum manuellen Hinzufügen von ActiveX-Steuerelement Containment zu einer vorhandenen OLE-Containeranwendung beschrieben. Wenn Sie im Voraus wissen, dass Sie Unterstützung für ActiveX-Steuerelemente im OLE-Container wünschen, lesen Sie den Artikel [Erstellen eines MFC-ActiveX-Steuerelement Containers](reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

> [!NOTE]
> In diesem Artikel wird ein Dialogfeld basiertes ActiveX-Steuerelement Container Projekt mit dem Namen Container und ein eingebettetes Steuerelement namens CIRC als Beispiele in den Prozeduren und Codes verwendet.

Um ActiveX-Steuerelemente zu unterstützen, müssen Sie eine Codezeile zu zwei Dateien des Projekts hinzufügen.

- Ändern Sie die Funktion des Haupt Dialogfelds `InitInstance` (im Container gefunden. Cpp) durch den MFC-Anwendungs-Assistenten, um [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)aufzurufen, wie im folgenden Beispiel gezeigt:

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Fügen Sie dem stdafx Ihres Projekts Folgendes hinzu: H-Header Datei:

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Nachdem Sie diese Schritte ausgeführt haben, erstellen Sie das Projekt neu, indem Sie im Menü **Erstellen** auf **Erstellen** klicken.

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](activex-control-containers.md)
