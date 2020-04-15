---
title: 'ActiveX-Steuerelementcontainer: Manuelles Aktivieren von ActiveX-Steuerelementcontainern'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322068"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX-Steuerelementcontainer: Manuelles Aktivieren von ActiveX-Steuerelementcontainern

Wenn Sie die ActiveX-Steuerelementunterstützung nicht aktiviert haben, als Sie den MFC-Anwendungs-Assistenten zum Generieren Ihrer Anwendung verwendet haben, müssen Sie diese Unterstützung manuell hinzufügen. In diesem Artikel wird der Prozess zum manuellen Hinzufügen der ActiveX-Steuerelementbeschränkung zu einer vorhandenen OLE-Containeranwendung beschrieben. Wenn Sie im Voraus wissen, dass ActiveX-Steuerelementunterstützung in Ihrem OLE-Container angezeigt werden soll, lesen Sie den Artikel [Erstellen eines MFC ActiveX Control Containers](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

> [!NOTE]
> In diesem Artikel wird ein dialogbasiertes ActiveX-Steuerelementcontainerprojekt mit dem Namen Container und ein eingebettetes Steuerelement mit dem Namen Circ als Beispiele in den Prozeduren und dem Code verwendet.

Um ActiveX-Steuerelemente zu unterstützen, müssen Sie zwei Projektdateien eine Codezeile hinzufügen.

- Ändern Sie die `InitInstance` Funktion Des Hauptdialogs (in CONTAINER. CPP) durch den MFC-Anwendungs-Assistenten, der einen Aufruf von [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)ausführt, wie im folgenden Beispiel:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Fügen Sie dem STDAFX Ihres Projekts Folgendes hinzu. H-Headerdatei:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Nachdem Sie diese Schritte abgeschlossen haben, erstellen Sie das Projekt neu, indem Sie im Menü **Erstellen** auf **Erstellen** klicken.

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](../mfc/activex-control-containers.md)
