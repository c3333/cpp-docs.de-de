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
ms.openlocfilehash: 18e482ca93166246df7569be9babff93d983dfd5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618064"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten

In diesem Artikel werden die für ActiveX-Steuerelemente verfügbaren Aktien Eigenschaften Seiten und deren Verwendung erläutert.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Weitere Informationen zur Verwendung von Eigenschaften Seiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Eigenschaftenseite](mfc-activex-controls-property-pages.md)

- [MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite](mfc-activex-controls-adding-another-custom-property-page.md)

MFC stellt drei Aktien Eigenschaften Seiten zur Verwendung mit ActiveX-Steuerelementen bereit: `CLSID_CColorPropPage` , `CLSID_CFontPropPage` und `CLSID_CPicturePropPage` . Auf diesen Seiten wird eine Benutzeroberfläche für die Eigenschaften der vordefinierten Farbe, Schriftart und Bild angezeigt.

Um diese Eigenschaften Seiten in ein Steuerelement einzubinden, fügen Sie Ihre IDs dem Code hinzu, der das Array von Eigenschaften Seiten-IDs des Steuer Elements initialisiert. Im folgenden Beispiel befindet sich dieser Code in der Implementierungs Datei des Steuer Elements (. Cpp), initialisiert das Array so, dass alle drei vordefinierten Eigenschaften Seiten und die Standardeigenschaften Seite ( `CMyPropPage` in diesem Beispiel genannt) enthalten sind:

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Beachten Sie, dass die Anzahl der Eigenschaften Seiten im BEGIN_PROPPAGEIDS-Makro 4 ist. Diese gibt die Anzahl von Eigenschaften Seiten an, die vom ActiveX-Steuerelement unterstützt werden.

Nachdem Sie diese Änderungen vorgenommen haben, erstellen Sie das Projekt neu. Das Steuerelement verfügt jetzt über Eigenschaften Seiten für die Eigenschaften Schriftart, Bild und Farbe.

> [!NOTE]
> Wenn nicht auf die Eigenschaften Seiten der Steuerelemente zugegriffen werden kann, liegt dies möglicherweise daran, dass die MFC-DLL (MFCxx. dll) nicht ordnungsgemäß beim aktuellen Betriebssystem registriert wurde. Dies führt normalerweise dazu, dass Visual C++ unter einem Betriebssystem installiert wird, das sich von dem derzeit aktuell aktuell aktuell ausgeführt

> [!TIP]
> Wenn die Eigenschaften Seiten für Aktien nicht sichtbar sind (siehe vorheriger Hinweis), registrieren Sie die dll, indem Sie regsvr32. exe von der Befehlszeile mit dem vollständigen Pfadnamen der dll ausführen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften](mfc-activex-controls-adding-stock-properties.md)
