---
title: 'MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358197"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten

In diesem Artikel werden die für ActiveX-Steuerelemente verfügbaren Bestandseigenschaftenseiten erläutert und deren Verwendung erläutert.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Weitere Informationen zur Verwendung von Eigenschaftenseiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Eigenschaftenseite](../mfc/mfc-activex-controls-property-pages.md)

- [MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC stellt drei Bestandseigenschaftenseiten für `CLSID_CColorPropPage`die `CLSID_CFontPropPage`Verwendung `CLSID_CPicturePropPage`mit ActiveX-Steuerelementen bereit: , , und . Auf diesen Seiten wird eine Benutzeroberfläche für Bestandsfarbe, Schriftart bzw. Bildeigenschaften angezeigt.

Um diese Eigenschaftenseiten in ein Steuerelement zu integrieren, fügen Sie deren IDs dem Code hinzu, der das Array von Eigenschaftenseiten-IDs des Steuerelements initialisiert. Im folgenden Beispiel befindet sich dieser Code in der Steuerelementimplementierungsdatei (. CPP), initialisiert das Array, das alle drei Bestandseigenschaftenseiten `CMyPropPage` und die Standardeigenschaftsseite (in diesem Beispiel genannt) enthält:

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Beachten Sie, dass die Anzahl der Eigenschaftenseiten im BEGIN_PROPPAGEIDS Makro 4 beträgt. Dies stellt die Anzahl der Eigenschaftenseiten dar, die vom ActiveX-Steuerelement unterstützt werden.

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie das Projekt neu. Das Steuerelement verfügt nun über Eigenschaftenseiten für die Schriftart-, Bild- und Farbeigenschaften.

> [!NOTE]
> Wenn auf die Eigenschaftenseiten des Steuerelements nicht zugegriffen werden kann, kann dies daran liegen, dass die MFC-DLL (MFCxx.DLL) nicht ordnungsgemäß beim aktuellen Betriebssystem registriert wurde. Dies ergibt sich in der Regel aus der Installation von Visual C++ unter einem Betriebssystem, das sich von dem derzeit ausgeführten unterscheidet.

> [!TIP]
> Wenn Ihre Bestandseigenschaftenseiten nicht sichtbar sind (siehe vorherige Anmerkung), registrieren Sie die DLL, indem Sie RegSvr32.exe über die Befehlszeile mit dem vollständigen Pfadnamen zur DLL ausführen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften](../mfc/mfc-activex-controls-adding-stock-properties.md)
