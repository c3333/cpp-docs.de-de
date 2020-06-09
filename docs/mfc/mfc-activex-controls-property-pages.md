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
ms.openlocfilehash: 3d22085daa503a7c778111718445920f98b98a89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615439"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC-ActiveX-Steuerelemente: Eigenschaftenseite

Eigenschaften Seiten ermöglichen einem ActiveX-Steuerelement Benutzer das Anzeigen und Ändern der Eigenschaften von ActiveX-Steuerelementen. Sie können auf diese Eigenschaften zugreifen, indem Sie das Dialogfeld Steuerelement Eigenschaften aufrufen, das eine oder mehrere Eigenschaften Seiten enthält, die eine angepasste grafische Oberfläche zum Anzeigen und Bearbeiten der Steuerelement Eigenschaften bereitstellen.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Die Eigenschaften Seiten des ActiveX-Steuer Elements werden auf zwei Arten angezeigt:

- Wenn das Eigenschaften Verb (**OLEIVERB_PROPERTIES**) des-Steuer Elements aufgerufen wird, öffnet das-Steuerelement ein modales Eigenschaften Dialogfeld, das die Eigenschaften Seiten des-Steuer Elements enthält.

- Der Container kann ein eigenes nicht modalem Dialogfeld anzeigen, in dem die Eigenschaften Seiten des ausgewählten Steuer Elements angezeigt werden.

Das Dialogfeld Eigenschaften (in der folgenden Abbildung dargestellt) besteht aus einem Bereich zum Anzeigen der aktuellen Eigenschaften Seite, Registerkarten zum Wechseln zwischen Eigenschaften Seiten und einer Auflistung von Schaltflächen, die allgemeine Aufgaben ausführen, wie z. b. das Schließen des Dialog Felds der Eigenschaften Seite, das Abbrechen vorgenommene Änderungen oder das sofortige Anwenden von Änderungen auf das ActiveX-Steuerelement.

![Eigenschaftendialogfeld für Circ3](../mfc/media/vc373i1.gif "Eigenschaftendialogfeld für Circ3") <br/>
Eigenschaften (Dialog Feld)

Dieser Artikel behandelt Themen im Zusammenhang mit der Verwendung von Eigenschaften Seiten in einem ActiveX-Steuerelement. Dazu gehören:

- [Implementieren der Standardeigenschaften Seite für ein ActiveX-Steuerelement](#_core_implementing_the_default_property_page)

- [Hinzufügen von Steuerelementen zu einer Eigenschaften Seite](#_core_adding_controls_to_a_property_page)

- [Anpassen der DoDataExchange-Funktion](#_core_customizing_the_dodataexchange_function)

Weitere Informationen zur Verwendung von Eigenschaften Seiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite](mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](mfc-activex-controls-using-stock-property-pages.md)

Informationen zur Verwendung von Eigenschaften Blättern in einer MFC-Anwendung, die kein ActiveX-Steuerelement ist, finden Sie unter [Eigenschaften Blätter](property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementieren der Standardeigenschaften Seite

Wenn Sie das Steuerelement Projekt mit dem ActiveX-Steuerelement-Assistenten erstellen, stellt der ActiveX-Steuerelement-Assistent eine Standardeigenschaften Seiten Klasse für das von der [COlePropertyPage-Klasse](reference/colepropertypage-class.md)abgeleitete Steuerelement bereit. Diese Eigenschaften Seite ist zunächst leer, Sie können jedoch ein beliebiges Dialogfeld-Steuerelement oder einen Satz von Steuerelementen hinzufügen. Da der ActiveX-Steuerelement-Assistent standardmäßig nur eine Eigenschaften Seiten Klasse erstellt, müssen zusätzliche Eigenschaften Seiten Klassen (auch von abgeleitet `COlePropertyPage` ) mit Klassenansicht erstellt werden. Weitere Informationen zu diesem Verfahren finden Sie unter [MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaften Seite](mfc-activex-controls-adding-another-custom-property-page.md).

Das Implementieren einer Eigenschaften Seite (in diesem Fall die Standardeinstellung) ist ein dreistufiger Prozess:

#### <a name="to-implement-a-property-page"></a>So implementieren Sie eine Eigenschaften Seite

1. Fügen Sie `COlePropertyPage` dem Steuerelement Projekt eine von abgeleitete Klasse hinzu. Wenn das Projekt mit dem ActiveX-Steuerelement-Assistenten erstellt wurde (wie in diesem Fall), ist die Standardeigenschaften Seiten Klasse bereits vorhanden.

1. Verwenden Sie den Dialog-Editor, um der Eigenschaften Seitenvorlage beliebige Steuerelemente hinzuzufügen.

1. Passen `DoDataExchange` Sie die Funktion der von `COlePropertyPage` abgeleiteten Klasse an, um Werte zwischen dem Steuerelement der Eigenschaften Seite und dem ActiveX-Steuerelement auszutauschen.

Die folgenden Prozeduren verwenden z. b. ein einfaches Steuerelement (mit dem Namen "Sample"). Das Beispiel wurde mithilfe des ActiveX-Steuerelement-Assistenten erstellt und enthält nur die Eigenschaft Stock Caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Hinzufügen von Steuerelementen zu einer Eigenschaften Seite

#### <a name="to-add-controls-to-a-property-page"></a>So fügen Sie einer Eigenschaften Seite Steuerelemente hinzu

1. Öffnen Sie mit dem geöffneten Steuerelement Projekt Ressourcenansicht.

1. Doppelklicken Sie auf das Symbol für den **Dialog** Verzeichnis.

1. Öffnen Sie das Dialogfeld IDD_PROPPAGE_SAMPLE.

   Der ActiveX-Steuerelement-Assistent fügt den Namen des Projekts an das Ende der Dialog-ID an, in diesem Fallbeispiel.

1. Ziehen Sie das ausgewählte Steuerelement per Drag & amp; Drop aus der Toolbox in den Dialogfeld Bereich.

1. In diesem Beispiel sind ein Text Bezeichnungs Steuerelement "Caption:" und ein Bearbeitungsfeld-Steuerelement mit einem IDC_CAPTION Bezeichner ausreichend.

1. Klicken Sie auf der Symbolleiste auf **Speichern** , um die Änderungen zu speichern.

Nachdem die Benutzeroberfläche geändert wurde, müssen Sie das Bearbeitungsfeld mit der Beschriftung-Eigenschaft verknüpfen. Dies erfolgt im folgenden Abschnitt, indem Sie die- `CSamplePropPage::DoDataExchange` Funktion bearbeiten.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Anpassen der DoDataExchange-Funktion

Die Eigenschaften Seite [CWnd::D odataexchange](reference/cwnd-class.md#dodataexchange) -Funktion ermöglicht es Ihnen, Eigenschafts Seiten Werte mit den tatsächlichen Werten von Eigenschaften im Steuerelement zu verknüpfen. Zum Einrichten von Links müssen Sie die entsprechenden Eigenschaften Seiten Felder den jeweiligen Steuerelement Eigenschaften zuordnen.

Diese Zuordnungen werden mithilfe der Eigenschaften Seite **DDP_** Funktionen implementiert. Die **DDP_** Funktionen funktionieren wie die **DDX_** Funktionen, die in MFC-Standard Dialogfeldern verwendet werden, mit einer Ausnahme. Zusätzlich zum Verweis auf eine Member-Variable verwenden **DDP_** Funktionen den Namen der Steuerelement Eigenschaft. Der folgende Eintrag ist ein typischer Eintrag in der- `DoDataExchange` Funktion für eine Eigenschaften Seite.

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Diese Funktion ordnet die *m_caption* Member-Variable der Eigenschaften Seite der Beschriftung mithilfe der- `DDP_TEXT` Funktion zu.

Nachdem Sie das Eigenschaften Seiten-Steuerelement eingefügt haben, müssen Sie mithilfe der- `DDP_Text` Funktion wie oben beschrieben eine Verknüpfung zwischen dem Eigenschaften Seiten-Steuerelement, IDC_CAPTION und der eigentlichen Steuerelement Eigenschaft (Beschriftung) herstellen.

[Eigenschaften Seiten](reference/property-pages-mfc.md) sind für andere Dialogfeld-Steuerelement Typen verfügbar, z. b. Kontrollkästchen, Options Felder und Listenfelder. In der folgenden Tabelle sind die gesamten Eigenschaften Seiten **DDP_** Funktionen und deren Zwecke aufgeführt:

### <a name="property-page-functions"></a>Eigenschaften Seitenfunktionen

|Funktionsname|Diese Funktion verwenden, um zu verknüpfen|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Der Index der ausgewählten Zeichenfolge in einem Kombinations Feld mit einer Steuerelement Eigenschaft.|
|`DDP_CBString`|Die ausgewählte Zeichenfolge in einem Kombinations Feld mit einer Steuerelement Eigenschaft. Die ausgewählte Zeichenfolge kann mit denselben Buchstaben wie der Eigenschafts Wert beginnen, aber Sie muss nicht vollständig übereinstimmen.|
|`DDP_CBStringExact`|Die ausgewählte Zeichenfolge in einem Kombinations Feld mit einer Steuerelement Eigenschaft. Die ausgewählte Zeichenfolge und der Zeichen folgen Wert der Eigenschaft müssen exakt übereinstimmen.|
|`DDP_Check`|Ein Kontrollkästchen mit einer Steuerelement Eigenschaft.|
|`DDP_LBIndex`|Der Index der ausgewählten Zeichenfolge in einem Listenfeld mit einer Steuerelement Eigenschaft.|
|`DDP_LBString`|Die ausgewählte Zeichenfolge in einem Listenfeld mit einer Steuerelement Eigenschaft. Die ausgewählte Zeichenfolge kann mit denselben Buchstaben wie der Eigenschafts Wert beginnen, aber Sie muss nicht vollständig übereinstimmen.|
|`DDP_LBStringExact`|Die ausgewählte Zeichenfolge in einem Listenfeld mit einer Steuerelement Eigenschaft. Die ausgewählte Zeichenfolge und der Zeichen folgen Wert der Eigenschaft müssen exakt übereinstimmen.|
|`DDP_Radio`|Ein Optionsfeld mit einer Steuerelement Eigenschaft.|
|`DDP_Text`|Text mit einer Steuerelement Eigenschaft.|

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[COlePropertyPage-Klasse](reference/colepropertypage-class.md)
