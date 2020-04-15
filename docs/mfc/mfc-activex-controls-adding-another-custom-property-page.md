---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364738"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC-ActiveX-Steuerelemente: Hinzufügen einer weiteren benutzerdefinierten Eigenschaftenseite

Gelegentlich verfügt ein ActiveX-Steuerelement über mehr Eigenschaften, als vernünftigerweise auf eine Eigenschaftenseite passen. In diesem Fall können Sie dem ActiveX-Steuerelement Eigenschaftenseiten hinzufügen, um diese Eigenschaften anzuzeigen.

In diesem Artikel wird das Hinzufügen neuer Eigenschaftenseiten zu einem ActiveX-Steuerelement erläutert, das bereits über mindestens eine Eigenschaftenseite verfügt. Weitere Informationen zum Hinzufügen von Bestandseigenschaftenseiten (Schriftart, Bild oder Farbe) finden Sie im Artikel [MFC ActiveX Controls: Using Stock Property Pages](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Die folgenden Verfahren verwenden ein ActiveX-Beispielsteuerelement, das vom ActiveX-Steuerelement-Assistenten erstellt wurde. Daher sind die Klassennamen und Bezeichner für dieses Beispiel eindeutig.

Weitere Informationen zur Verwendung von Eigenschaftenseiten in einem ActiveX-Steuerelement finden Sie in den folgenden Artikeln:

- [MFC-ActiveX-Steuerelemente: Eigenschaftenseite](../mfc/mfc-activex-controls-property-pages.md)

- [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Es wird dringend empfohlen, dass neue Eigenschaftenseiten dem Größenstandard für ActiveX-Steuerelementeigenschaftenseiten entsprechen. Die Bestandsbild- und Farbeigenschaftenseiten messen 250x62 Dialogeinheiten (DLU). Die Standard-Schriftart-Eigenschaftsseite ist 250x110 DLUs. Die vom ActiveX-Steuerelement-Assistenten erstellte Standardeigenschaftsseite verwendet den DLU-Standard 250x62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>So fügen Sie eine neue Eigenschaftenseitenvorlage in Ihr Projekt ein

1. Öffnen Sie die Ressourcenansicht im Projektarbeitsbereich, wenn Das Steuerelementprojekt geöffnet ist.

1. Klicken Sie mit der rechten Maustaste in der Ressourcenansicht, um das Kontextmenü zu öffnen, und klicken Sie auf **Ressource hinzufügen**.

1. Erweitern Sie den **Dialogknoten,** und wählen Sie **IDD_OLE_PROPPAGE_SMALL**aus.

1. Klicken Sie auf **Neu,** um die Ressource zu Ihrem Projekt hinzuzufügen.

1. Wählen Sie die neue Eigenschaftenseitenvorlage aus, um das **Eigenschaftenfenster** zu aktualisieren (in **Resource View**).

1. Geben Sie einen neuen Wert für die **ID-Eigenschaft** ein. In diesem Beispiel wird **IDD_PROPPAGE_NEWPAGE verwendet.**

1. Klicken Sie in der Symbolleiste auf **Speichern** .

### <a name="to-associate-the-new-template-with-a-class"></a>So ordnen Sie die neue Vorlage einer Klasse zu

1. Öffnen Sie die Klassenansicht.

1. Klicken Sie mit der rechten Maustaste in der Klassenansicht, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Klasse hinzufügen**.

   Dadurch wird das Dialogfeld [Klassen hinzufügen](../ide/add-class-dialog-box.md) geöffnet.

1. Doppelklicken Sie auf die **Vorlage mFC-Klasse.**

1. Geben Sie im Feld **Klassenname** im [MFC-Klassen-Assistenten](../mfc/reference/mfc-add-class-wizard.md)einen Namen für die neue Dialogklasse ein. (In diesem `CAddtlPropPage`Beispiel .)

1. Wenn Sie Dateinamen ändern möchten, klicken Sie auf **Ändern**. Geben Sie die Namen für Die Implementierungs- und Headerdateien ein, oder akzeptieren Sie die Standardnamen.

1. Wählen Sie `COlePropertyPage`im Feld **Basisklasse** aus.

1. Wählen Sie im Feld **Dialog-ID** **IDD_PROPPAGE_NEWPAGE**aus.

1. Klicken Sie auf **Fertig stellen,** um die Klasse zu erstellen.

Um den Benutzern des Steuerelements den Zugriff auf diese neue Eigenschaftenseite zu ermöglichen, nehmen Sie die folgenden Änderungen am Makroabschnitt der Eigenschaftenseite iDs des Steuerelements vor (in der Steuerelementimplementierungsdatei):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Beachten Sie, dass Sie den zweiten Parameter des BEGIN_PROPPAGEIDS Makros (Anzahl der Eigenschaftenseiten) von 1 auf 2 erhöhen müssen.

Sie müssen auch die Steuerelementimplementierungsdatei (. CPP)-Datei, um den Header (. H) Datei der neuen Eigenschaftenseitenklasse.

Im nächsten Schritt werden zwei neue Zeichenfolgenressourcen erstellt, die einen Typnamen und eine Beschriftung für die neue Eigenschaftenseite bereitstellen.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>So fügen Sie einer Eigenschaftenseite neue Zeichenfolgenressourcen hinzu

1. Öffnen Sie die Ressourcenansicht, wenn Das Steuerungsprojekt geöffnet ist.

1. Doppelklicken Sie auf den Ordner **Stringtable,** und doppelklicken Sie dann auf die vorhandene Zeichenfolgentabellenressource, der Sie eine Zeichenfolge hinzufügen möchten.

   Dadurch wird die Zeichenfolgentabelle in einem Fenster geöffnet.

1. Wählen Sie die leere Zeile am Ende der Zeichenfolgentabelle aus, und geben Sie den Text oder die Beschriftung der Zeichenfolge ein: z. B. "Zusätzliche Eigenschaftenseite".

   Dadurch wird eine Seite mit **den Zeichenfolgeneigenschaften** geöffnet, auf der **Beschriftungs-** und **ID-Felder** angezeigt werden. Das Feld **Beschriftung** enthält die eingegebene Zeichenfolge.

1. Wählen Sie im Feld **ID** eine ID für die Zeichenfolge aus, oder geben Sie sie ein. Drücken Sie die Eingabetaste, wenn Sie fertig sind.

   In diesem Beispiel wird **IDS_SAMPLE_ADDPAGE** für den Typnamen der neuen Eigenschaftenseite verwendet.

1. Wiederholen Sie die Schritte 3 und 4 mit **IDS_SAMPLE_ADDPPG_CAPTION** für die ID und "Zusätzliche Eigenschaftenseite" für die Beschriftung.

1. In der . Die CPP-Datei Ihrer neuen Eigenschaftenseitenklasse `CAddtlPropPage`(in `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` diesem Beispiel ) ändert die so, dass IDS_SAMPLE_ADDPAGE von [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)übergeben wird, wie im folgenden Beispiel:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Ändern Sie den `CAddtlPropPage` Konstruktor von so, dass IDS_SAMPLE_ADDPPG_CAPTION an den `COlePropertyPage` Konstruktor übergeben wird, wie folgt:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Nachdem Sie die erforderlichen Änderungen vorgenommen haben, erstellen Sie das Projekt neu, und verwenden Sie Testcontainer, um die neue Eigenschaftenseite zu testen. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
