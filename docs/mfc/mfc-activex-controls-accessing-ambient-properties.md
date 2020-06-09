---
title: 'MFC-ActiveX-Steuerelemente: Zugreifen auf Umgebungseigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: e5c78c9943f8baeadcc1198ee8c96f2023ac0215
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625444"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC-ActiveX-Steuerelemente: Zugreifen auf Umgebungseigenschaften

In diesem Artikel wird erläutert, wie ein ActiveX-Steuerelement auf die Umgebungs Eigenschaften seines Steuerelement Containers zugreifen kann.

Ein Steuerelement kann Informationen über den Container abrufen, indem er auf die Umgebungs Eigenschaften des Containers zugreift. Diese Eigenschaften machen visuelle Merkmale verfügbar, wie z. b. die Hintergrundfarbe des Containers, die aktuelle vom Container verwendete Schriftart und Betriebsmerkmale, wie z. b. ob sich der Container derzeit im Benutzermodus oder im Designer Modus befindet. Ein Steuerelement kann Umgebungs Eigenschaften verwenden, um seine Darstellung und das Verhalten an den jeweiligen Container anzupassen, in dem er eingebettet ist. Ein Steuerelement sollte jedoch niemals davon ausgehen, dass sein Container eine bestimmte Ambient-Eigenschaft unterstützt. Tatsächlich unterstützen einige Container eventuell keine Umgebungs Eigenschaften. Wenn keine Ambient-Eigenschaft vorhanden ist, sollte ein Steuerelement einen angemessenen Standardwert annehmen.

Um auf eine Ambient-Eigenschaft zuzugreifen, führen Sie einen aufzurufenden [COleControl:: getAmbientProperty](reference/colecontrol-class.md#getambientproperty)-Befehl aus. Diese Funktion erwartet die Dispatch-ID für die Ambient-Eigenschaft als ersten Parameter (die Datei OLECTL. H definiert Dispatch-IDs für den Standardsatz von Ambient-Eigenschaften.

Die Parameter der `GetAmbientProperty` Funktion sind die Dispatch-ID, ein Variant-Tag, das den erwarteten Eigenschaftentyp angibt, und ein Zeiger auf den Arbeitsspeicher, in dem der Wert zurückgegeben werden soll. Der Datentyp, auf den dieser Zeiger verweist, hängt vom Variant-Tag ab. Die-Funktion gibt **true** zurück, wenn der Container die-Eigenschaft unterstützt; andernfalls wird **false**zurückgegeben.

Im folgenden Codebeispiel wird der Wert der Ambient-Eigenschaft mit dem Namen "Usermode" abgerufen. Wenn die Eigenschaft nicht vom Container unterstützt wird, wird der Standardwert **true** angenommen:

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Zur Unterstützung stellt `COleControl` Hilfsfunktionen bereit, die auf viele der häufig verwendeten Ambient-Eigenschaften zugreifen und geeignete Standardwerte zurückgeben, wenn die Eigenschaften nicht verfügbar sind. Diese Hilfsfunktionen lauten wie folgt:

- [COleControl:: ambientbackcolor](reference/colecontrol-class.md#ambientbackcolor)

- [Ambientdisplayname](reference/colecontrol-class.md#ambientdisplayname)

- [Ambientfont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  Der Aufrufer muss `Release( )` für die zurückgegebene Schriftart aufruft.

- [Ambientforecolor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [Ambientscaleunits](reference/colecontrol-class.md#ambientscaleunits)

- [Ambienttextalign](reference/colecontrol-class.md#ambienttextalign)

- [Ambientusermode](reference/colecontrol-class.md#ambientusermode)

- [Ambientuidead](reference/colecontrol-class.md#ambientuidead)

- [Ambientshowhatching](reference/colecontrol-class.md#ambientshowhatching)

- [Ambientshowgrabhandles](reference/colecontrol-class.md#ambientshowgrabhandles)

Wenn sich der Wert einer Ambient-Eigenschaft ändert (durch eine Aktion des Containers), `OnAmbientPropertyChanged` wird die Member-Funktion des Steuer Elements aufgerufen. Überschreiben Sie diese Member-Funktion, um eine solche Benachrichtigung zu verarbeiten. Der-Parameter für `OnAmbientPropertyChanged` ist die Dispatch-ID der betroffenen Ambient-Eigenschaft. Der Wert dieser Dispatch-ID kann DISPID_UNKNOWN sein, was darauf hinweist, dass sich eine oder mehrere Umgebungs Eigenschaften geändert haben, aber die Informationen zu den betroffenen Eigenschaften sind nicht verfügbar.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
