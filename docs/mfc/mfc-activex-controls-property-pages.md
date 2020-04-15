---
title: 'MFC-ActiveX-Steuerelemente: Eigenschaftenseite'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364565"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC-ActiveX-Steuerelemente: Eigenschaftenseite

Eigenschaftenseiten ermöglichen es einem ActiveX-Steuerelementbenutzer, ActiveX-Steuerelementeigenschaften anzuzeigen und zu ändern. Auf diese Eigenschaften wird zugegriffen, indem ein Dialogfeld mit Steuerelementeigenschaften aufgerufen wird, das eine oder mehrere Eigenschaftenseiten enthält, die eine angepasste, grafische Oberfläche zum Anzeigen und Bearbeiten der Steuerelementeigenschaften bereitstellen.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

ActiveX-Steuerelementeigenschaftenseiten werden auf zwei Arten angezeigt:

- Wenn das Eigenschaftenverb (**OLEIVERB_PROPERTIES**) des Steuerelements aufgerufen wird, öffnet das Steuerelement ein Dialogfeld für modale Eigenschaften, das die Eigenschaftenseiten des Steuerelements enthält.

- Der Container kann sein eigenes modusloses Dialogfeld anzeigen, das die Eigenschaftenseiten des ausgewählten Steuerelements anzeigt.

Das Dialogfeld Eigenschaften (in der folgenden Abbildung dargestellt) besteht aus einem Bereich zum Anzeigen der aktuellen Eigenschaftenseite, Registerkarten zum Wechseln zwischen Eigenschaftenseiten und einer Auflistung von Schaltflächen, die allgemeine Aufgaben ausführen, wie z. B. das Schließen des Eigenschaftenseitendialogs, das Abbrechen aller vorgenommenen Änderungen oder das sofortige Anwenden von Änderungen am ActiveX-Steuerelement.

![Eigenschaftendialogfeld für Circ3](../mfc/media/vc373i1.gif "Eigenschaftendialogfeld für Circ3") <br/>
Eigenschaften Dialogfeld

In diesem Artikel werden Themen behandelt, die sich auf die Verwendung von Eigenschaftenseiten in einem ActiveX-Steuerelement beziehen. Dazu gehören:

- [Implementieren der Standardeigenschaftsseite für ein ActiveX-Steuerelement](#_core_implementing_the_default_property_page)

- [Hinzufügen von Steuerelementen zu einer Eigenschaftenseite](#_core_adding_controls_to_a_property_page)

- [Anpassen der DoDataExchange-Funktion](#_core_customizing_the_dodataexchange_function)

Weitere Informationen zur Verwendung von Eigenschaftenseiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Informationen zur Verwendung von Eigenschaftenblättern in einer anderen MFC-Anwendung als einem ActiveX-Steuerelement finden Sie unter [Eigenschaftenblätter](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementieren der Standardeigenschaftsseite

Wenn Sie den ActiveX Control-Assistenten zum Erstellen des Steuerelementprojekts verwenden, stellt der ActiveX Control-Assistent eine Standardeigenschaftenseitenklasse für das von der [COlePropertyPage-Klasse](../mfc/reference/colepropertypage-class.md)abgeleitete Steuerelement bereit. Anfangs ist diese Eigenschaftenseite leer, Sie können jedoch ein beliebiges Dialogfeldsteuerelement oder eine Reihe von Steuerelementen hinzufügen. Da der ActiveX Control-Assistent standardmäßig nur eine Eigenschaftenseitenklasse erstellt, `COlePropertyPage`müssen mithilfe der Klassenansicht zusätzliche Eigenschaftenseitenklassen (ebenfalls abgeleitet von ) erstellt werden. Weitere Informationen zu diesem Verfahren finden Sie unter [MFC ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

Das Implementieren einer Eigenschaftenseite (in diesem Fall die Standardeinstellung) ist ein dreistufiger Prozess:

#### <a name="to-implement-a-property-page"></a>So implementieren Sie eine Eigenschaftenseite

1. Fügen `COlePropertyPage`Sie dem Steuerelementprojekt eine -abgeleitete Klasse hinzu. Wenn das Projekt mit dem ActiveX Control Wizard erstellt wurde (wie in diesem Fall), ist die Standardeigenschaftenseitenklasse bereits vorhanden.

1. Verwenden Sie den Dialogdialogeditor, um der Eigenschaftenseitenvorlage Steuerelemente hinzuzufügen.

1. Passen `DoDataExchange` Sie die `COlePropertyPage`Funktion der -derived-Klasse an, um Werte zwischen dem Eigenschaftenseitensteuerelement und dem ActiveX-Steuerelement auszutauschen.

Die folgenden Verfahren verwenden z. B. ein einfaches Steuerelement (mit dem Namen "Beispiel"). Das Beispiel wurde mit dem ActiveX Control Wizard erstellt und enthält nur die Stock Caption-Eigenschaft.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Hinzufügen von Steuerelementen zu einer Eigenschaftenseite

#### <a name="to-add-controls-to-a-property-page"></a>So fügen Sie Steuerelemente zu einer Eigenschaftenseite hinzu

1. Öffnen Sie die Ressourcenansicht, wenn Das Steuerungsprojekt geöffnet ist.

1. Doppelklicken Sie **Dialog** auf das Dialog-Verzeichnissymbol.

1. Öffnen Sie das Dialogfeld IDD_PROPPAGE_SAMPLE.

   Der ActiveX-Steuerelement-Assistent fügt den Namen des Projekts an das Ende der Dialog-ID an, in diesem Fall Beispiel.

1. Ziehen Sie das ausgewählte Steuerelement aus der Toolbox in den Dialogfeldbereich.

1. Für dieses Beispiel sind ein Textbeschriftungssteuerelement "Caption :" und ein Bearbeitungsfeldsteuerelement mit einem IDC_CAPTION Bezeichner ausreichend.

1. Klicken Sie auf der Symbolleiste auf **Speichern,** um Ihre Änderungen zu speichern.

Nachdem die Benutzeroberfläche geändert wurde, müssen Sie das Bearbeitungsfeld mit der Caption-Eigenschaft verknüpfen. Dies geschieht im folgenden Abschnitt, `CSamplePropPage::DoDataExchange` indem Sie die Funktion bearbeiten.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Anpassen der DoDataExchange-Funktion

Mit der Eigenschaftsseite [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) können Sie Eigenschaftenseitenwerte mit den tatsächlichen Werten der Eigenschaften im Steuerelement verknüpfen. Um Verknüpfungen herzustellen, müssen Sie die entsprechenden Eigenschaftenseitenfelder ihren jeweiligen Steuerelementeigenschaften zuordnen.

Diese Zuordnungen werden mithilfe der Eigenschaftenseite **DDP_-Funktionen** implementiert. Die **DDP_** Funktionen funktionieren wie die **DDX_** Funktionen, die in Standard-MFC-Dialogen verwendet werden, mit einer Ausnahme. Zusätzlich zum Verweis auf eine Membervariable nehmen **DDP_** Funktionen den Namen der Steuerelementeigenschaft an. Im Folgenden finden Sie `DoDataExchange` einen typischen Eintrag in der Funktion für eine Eigenschaftenseite.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Diese Funktion ordnet die *m_caption* Membervariable der Eigenschaftenseite `DDP_TEXT` der Beschriftung mithilfe der Funktion zu.

Nachdem Sie das Eigenschaftenseitensteuerelement eingefügt haben, müssen Sie mithilfe der `DDP_Text` oben beschriebenen Funktion eine Verknüpfung zwischen dem Eigenschaftenseitensteuerelement IDC_CAPTION und der tatsächlichen Steuerelementeigenschaft Beschriftung herstellen.

[Eigenschaftenseiten](../mfc/reference/property-pages-mfc.md) sind für andere Dialogsteuerelementtypen verfügbar, z. B. Kontrollkästchen, Optionsfelder und Listenfelder. In der folgenden Tabelle sind die gesamten Eigenschaftenseiten **DDP_** Funktionen und deren Zwecke aufgeführt:

### <a name="property-page-functions"></a>Eigenschaftenseitenfunktionen

|Funktionsname|Verwenden Sie diese Funktion, um|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Der Index der ausgewählten Zeichenfolge in einem Kombinationsfeld mit einer Steuerelementeigenschaft.|
|`DDP_CBString`|Die ausgewählte Zeichenfolge in einem Kombinationsfeld mit einer Steuerelementeigenschaft. Die ausgewählte Zeichenfolge kann mit den gleichen Buchstaben wie der Wert der Eigenschaft beginnen, muss sie jedoch nicht vollständig übereinstimmen.|
|`DDP_CBStringExact`|Die ausgewählte Zeichenfolge in einem Kombinationsfeld mit einer Steuerelementeigenschaft. Die ausgewählte Zeichenfolge und der Zeichenfolgenwert der Eigenschaft müssen genau übereinstimmen.|
|`DDP_Check`|Ein Kontrollkästchen mit einer Steuerelementeigenschaft.|
|`DDP_LBIndex`|Der Index der ausgewählten Zeichenfolge in einem Listenfeld mit einer Steuerelementeigenschaft.|
|`DDP_LBString`|Die ausgewählte Zeichenfolge in einem Listenfeld mit einer Steuerelementeigenschaft. Die ausgewählte Zeichenfolge kann mit den gleichen Buchstaben wie der Wert der Eigenschaft beginnen, muss sie jedoch nicht vollständig übereinstimmen.|
|`DDP_LBStringExact`|Die ausgewählte Zeichenfolge in einem Listenfeld mit einer Steuerelementeigenschaft. Die ausgewählte Zeichenfolge und der Zeichenfolgenwert der Eigenschaft müssen genau übereinstimmen.|
|`DDP_Radio`|Ein Optionsfeld mit einer Steuereigenschaft.|
|`DDP_Text`|Text mit einer Steuerelementeigenschaft.|

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage-Klasse](../mfc/reference/colepropertypage-class.md)
