---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: a749c5d8d676ac85c3c2085eb041328aff599ab8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508879"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite

Gelegentlich verfügt ein ActiveX-Steuerelement über mehr Eigenschaften, als auf eine Eigenschaften Seite angemessen angepasst werden können. In diesem Fall können Sie dem ActiveX-Steuerelement Eigenschaften Seiten hinzufügen, um diese Eigenschaften anzuzeigen.

In diesem Artikel wird das Hinzufügen neuer Eigenschaften Seiten zu einem ActiveX-Steuerelement erläutert, das bereits über mindestens eine Eigenschaften Seite verfügt. Weitere Informationen zum Hinzufügen von vordefinierten Eigenschaften Seiten (Schriftart, Bild oder Farbe) finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaften Seiten](mfc-activex-controls-using-stock-property-pages.md).

In den folgenden Verfahren wird ein vom ActiveX-Steuerelement-Assistenten erstelltes ActiveX-Steuerelement Framework verwendet. Daher sind die Klassennamen und Bezeichner für dieses Beispiel eindeutig.

Weitere Informationen zur Verwendung von Eigenschaften Seiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Eigenschaften Seiten](mfc-activex-controls-property-pages.md)

- [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaften Seiten](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Es wird dringend empfohlen, dass neue Eigenschaften Seiten den Größen Standard für die Eigenschaften Seiten des ActiveX-Steuer Elements entsprechen. Die Eigenschaften Seiten "Stock Picture" und "Color" messen 250 x 62 Dialog Einheiten (DLU). Die Eigenschaften Seite Standard Schriftart ist 250 x 110 DLUs. Die Standardeigenschaften Seite, die vom ActiveX-Steuerelement-Assistenten erstellt wurde, verwendet den dlu-Standard von 250 x 62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>So fügen Sie eine neue Eigenschaften Seitenvorlage in Ihr Projekt ein

1. Öffnen Sie Ihr Steuerelement Projekt, und öffnen Sie Ressourcenansicht im Projekt Arbeitsbereich.

1. Klicken Sie mit der rechten Maustaste auf Ressourcenansicht, um das Kontextmenü zu öffnen und auf **Ressource hinzufügen**.

1. Erweitern Sie den **Dialog** Knoten, und wählen Sie **IDD_OLE_PROPPAGE_SMALL**aus.

1. Klicken Sie auf **neu** , um die Ressource dem Projekt hinzuzufügen.

1. Wählen Sie die Vorlage neue Eigenschaften Seite aus, um das **Eigenschaften** Fenster (in **Ressourcenansicht**) zu aktualisieren.

1. Geben Sie einen neuen Wert für die **ID** -Eigenschaft ein. In diesem Beispiel wird **IDD_PROPPAGE_NEWPAGE**verwendet.

1. Klicken Sie in der Symbolleiste auf **Speichern** .

### <a name="to-associate-the-new-template-with-a-class"></a>So ordnen Sie die neue Vorlage einer Klasse zu

1. Öffnen Sie Klassenansicht.

1. Klicken Sie mit der rechten Maustaste auf Klassenansicht, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Klasse hinzufügen**.

   Dadurch wird das Dialogfeld [Klasse hinzufügen](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) geöffnet.

1. Doppelklicken Sie auf die **MFC-Klassen** Vorlage.

1. Geben Sie im [MFC-Klassen-Assistenten](reference/mfc-add-class-wizard.md)im Feld **Klassen Name** einen Namen für die neue Dialogfeld Klasse ein. (In diesem Beispiel `CAddtlPropPage` .)

1. Wenn Sie Dateinamen ändern möchten, klicken Sie auf **ändern**. Geben Sie die Namen für Ihre Implementierungs-und Header Dateien ein, oder übernehmen Sie die Standardnamen.

1. Wählen Sie im Feld **Basisklasse** die Option aus `COlePropertyPage` .

1. Wählen Sie im Dialog Feld mit der Dialog Feld- **ID** **IDD_PROPPAGE_NEWPAGE**aus.

1. Klicken Sie auf **Fertig** stellen, um die Klasse zu erstellen.

Damit die Benutzer des Steuer Elements auf diese neue Eigenschaften Seite zugreifen können, nehmen Sie die folgenden Änderungen am Makro Abschnitt der Eigenschaften Seiten-IDs des-Steuer Elements vor (in der Implementierungs Datei des Steuer Elements):

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Beachten Sie, dass Sie den zweiten Parameter des BEGIN_PROPPAGEIDS Makros (die Anzahl der Eigenschaften Seiten) von 1 auf 2 vergrößern müssen.

Sie müssen auch die Implementierungs Datei des Steuer Elements () ändern. Cpp-Datei zum Einschließen des Headers (. H) der neuen Eigenschaften Seiten Klasse.

Der nächste Schritt umfasst das Erstellen von zwei neuen Zeichen folgen Ressourcen, die einen Typnamen und eine Beschriftung für die neue Eigenschaften Seite bereitstellen.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>So fügen Sie einer Eigenschaften Seite neue Zeichen folgen Ressourcen hinzu

1. Öffnen Sie mit dem geöffneten Steuerelement Projekt Ressourcenansicht.

1. Doppelklicken Sie auf den Zeichen folgen- **Tabellen** Ordner, und doppelklicken Sie dann auf die vorhandene Zeichen folgen Tabellen Ressource, der Sie eine Zeichenfolge hinzufügen möchten.

   Dadurch wird die Zeichen folgen Tabelle in einem Fenster geöffnet.

1. Wählen Sie die leere Zeile am Ende der Zeichen folgen Tabelle aus, und geben Sie den Text oder die Beschriftung der Zeichenfolge ein, z. b. "zusätzliche Eigenschaften Seite."

   Dadurch wird eine **Zeichen folgen Eigenschaften** Seite geöffnet, auf der **Beschriftungen** und **IDs** angezeigt werden. Das **Beschriftungs** Feld enthält die Zeichenfolge, die Sie eingegeben haben.

1. Wählen Sie im Feld **ID** eine ID für die Zeichenfolge aus, oder geben Sie Sie ein. Drücken Sie nach Abschluss der EINGABETASTE.

   In diesem Beispiel wird **IDS_SAMPLE_ADDPAGE** für den Typnamen der neuen Eigenschaften Seite verwendet.

1. Wiederholen Sie die Schritte 3 und 4 mithilfe **IDS_SAMPLE_ADDPPG_CAPTION** für die ID und "zusätzliche Eigenschaften Seite" für die Beschriftung.

1. In der. Cpp-Datei der neuen Eigenschaften Seiten Klasse (in diesem Beispiel `CAddtlPropPage` ) ändern Sie den `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` , sodass IDS_SAMPLE_ADDPAGE von [afxoleregisterpropertypageclass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass)übergeben wird, wie im folgenden Beispiel gezeigt:

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Ändern Sie den Konstruktor von `CAddtlPropPage` so, dass IDS_SAMPLE_ADDPPG_CAPTION wie folgt an den- `COlePropertyPage` Konstruktor übergeben wird:

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Nachdem Sie die erforderlichen Änderungen vorgenommen haben, erstellen Sie das Projekt neu, und verwenden Sie den Test Container, um die neue Eigenschaften Seite zu testen. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
