---
title: 'MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: 58f387ba6f4d7cdffb3ffc1f7be6f9acde8314f4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618164"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten

Wenn das ActiveX-Steuerelement Text anzeigt, können Sie dem Steuerelement Benutzer gestatten, die Textdarstellung zu ändern, indem Sie eine Schriftart Eigenschaft ändern. Schriftart Eigenschaften werden als Schriftart Objekte implementiert und können einen von zwei Typen aufweisen: Stock oder Custom. Die Eigenschaften der Kurs Schriftart sind vordefinierte Schriftart Eigenschaften, die Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften hinzufügen können. Benutzerdefinierte Schriftart Eigenschaften werden nicht vordefiniert, und der Steuerelement Entwickler bestimmt das Verhalten und die Verwendung der Eigenschaft.

In diesem Artikel werden die folgenden Themen behandelt:

- [Verwenden der Eigenschaft "Stock Font"](#_core_using_the_stock_font_property)

- [Verwenden von benutzerdefinierten Schriftart Eigenschaften im Steuerelement](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Verwenden der Eigenschaft "Stock Font"

Die Eigenschaften der vordefinierten Schriftart werden von der Klasse [COleControl](reference/colecontrol-class.md)vorrätig. Außerdem ist eine standardmäßige Schriftart Eigenschaften Seite verfügbar, die es dem Benutzer ermöglicht, verschiedene Attribute des Schriftart Objekts, z. b. Name, Größe und Stil, zu ändern.

Greifen Sie über die Funktionen [getFont](reference/colecontrol-class.md#getfont), [setFont](reference/colecontrol-class.md#setfont)und [InternalGetFont](reference/colecontrol-class.md#internalgetfont) von auf das Schriftart Objekt zu `COleControl` . Der Benutzer des Steuer Elements greift auf das Schriftart Objekt über die `GetFont` -und- `SetFont` Funktionen auf dieselbe Weise wie jede andere Get/Set-Eigenschaft zu. Wenn der Zugriff auf das Schriftart Objekt innerhalb eines Steuer Elements erforderlich ist, verwenden Sie die- `InternalGetFont` Funktion.

Wie unter [MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md)erläutert, ist das Hinzufügen von vordefinierten Eigenschaften mit dem [Assistenten zum Hinzufügen](../ide/names-add-property-wizard.md)von Eigenschaften einfach Sie wählen die Eigenschaft Schriftart aus, und der Assistent zum Hinzufügen von Eigenschaften fügt automatisch den Eintrag für die Eingabe in die Dispatchzuordnung des Steuer Elements ein.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>So fügen Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften die Eigenschaft "Lager Schriftart

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Assistent zum Hinzufügen von Eigenschaften geöffnet.

1. Klicken Sie im Feld **Eigenschafts Name** auf **Schriftart**.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften fügt dem dispatchmap des Steuer Elements die folgende Zeile hinzu, die sich in der Implementierungs Datei der Steuerelement Klasse befindet:

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Außerdem fügt der Assistent zum Hinzufügen von Eigenschaften dem-Steuerelement die folgende Zeile hinzu. IDL-Datei:

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Die Eigenschaft Stock Caption ist ein Beispiel für eine Text Eigenschaft, die mit den Eigenschaften Informationen für die Kurs Schriftart gezeichnet werden kann. Beim Hinzufügen der Eigenschaft Stock Caption zum-Steuerelement werden ähnliche Schritte verwendet wie für die Eigenschaft Stock Font.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>So fügen Sie die Eigenschaft Stock Caption mithilfe des Assistenten zum Hinzufügen von Eigenschaften hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Assistent zum Hinzufügen von Eigenschaften geöffnet.

1. Klicken Sie im Feld **Eigenschafts Name** auf **Beschriftung**.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften fügt dem dispatchmap des Steuer Elements die folgende Zeile hinzu, die sich in der Implementierungs Datei der Steuerelement Klasse befindet:

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Ändern der OnDraw-Funktion

Die Standard Implementierung von `OnDraw` verwendet die Windows-System Schriftart für den gesamten Text, der im-Steuerelement angezeigt wird. Dies bedeutet, dass Sie den Code ändern müssen, `OnDraw` indem Sie das Schriftart Objekt in den Gerätekontext auswählen. Um dies zu erreichen, wenden Sie [COleControl:: SelectStockFont](reference/colecontrol-class.md#selectstockfont) an, und übergeben Sie den Gerätekontext des Steuer Elements, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Nachdem die `OnDraw` Funktion so geändert wurde, dass das Schriftart Objekt verwendet wird, wird sämtlicher Text im Steuerelement mit Merkmalen aus der Stock Font-Eigenschaft des Steuer Elements angezeigt.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Verwenden von benutzerdefinierten Schriftart Eigenschaften im Steuerelement

Neben der Eigenschaft Stock Font kann das ActiveX-Steuerelement über benutzerdefinierte Schriftart Eigenschaften verfügen. Zum Hinzufügen einer benutzerdefinierten Schriftart Eigenschaft müssen Sie folgende Schritte ausführen:

- Mit dem Assistenten zum Hinzufügen von Eigenschaften können Sie die Eigenschaft benutzerdefinierte Schriftart implementieren.

- [Schriftart Benachrichtigungen werden verarbeitet](#_core_processing_font_notifications).

- [Implementieren einer neuen Schriftart Benachrichtigungs Schnittstelle](#_core_implementing_a_new_font_notification_interface)

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementieren einer benutzerdefinierten Schriftart Eigenschaft

Um eine benutzerdefinierte Schriftart Eigenschaft zu implementieren, verwenden Sie den Assistenten zum Hinzufügen von Eigenschaften, um die Eigenschaft hinzuzufügen, und nehmen Sie dann einige Änderungen am Code vor. In den folgenden Abschnitten wird beschrieben, wie Sie die benutzerdefinierte `HeadingFont` Eigenschaft zum Beispiel Steuerelement hinzufügen.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>So fügen Sie die benutzerdefinierte Schriftart Eigenschaft mithilfe des Assistenten zum Hinzufügen von Eigenschaften

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Assistent zum Hinzufügen von Eigenschaften geöffnet.

1. Geben Sie im Feld **Eigenschaftsname** einen Namen für die Eigenschaft ein. Verwenden Sie für dieses Beispiel **HeadingFont**.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** die Option **IDispatch** <strong>\*</strong> für den Eigenschaftentyp aus.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften erstellt den Code, um der `HeadingFont` `CSampleCtrl` -Klasse und dem-Beispiel die benutzerdefinierte Eigenschaft hinzuzufügen. IDL-Datei. Da `HeadingFont` ein Get/Set-Eigenschaftentyp ist, ändert der Assistent zum Hinzufügen von Eigenschaften die `CSampleCtrl` Dispatchzuordnung der Klasse so, dass ein DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) -Makro Eintrag enthalten ist:

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Das DISP_PROPERTY_EX-Makro ordnet den `HeadingFont` Eigenschaftsnamen der `CSampleCtrl` entsprechenden Klasse Get-und Set-Methoden `GetHeadingFont` und zu `SetHeadingFont` . Der Typ des Eigenschafts Werts wird ebenfalls angegeben. in diesem Fall VT_FONT.

Der Assistent zum Hinzufügen von Eigenschaften fügt auch eine Deklaration in der Header Datei des Steuer Elements (. H) für die `GetHeadingFont` -und `SetHeadingFont` -Funktionen und fügt ihre Funktions Vorlagen in der Implementierungs Datei des Steuer Elements hinzu (. Cpp):

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Schließlich ändert der Assistent zum Hinzufügen von Eigenschaften das-Steuerelement. IDL-Datei durch Hinzufügen eines Eintrags für die `HeadingFont` Eigenschaft:

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Änderungen am Steuerelement Code

Nachdem Sie dem Steuerelement die Eigenschaft hinzugefügt haben `HeadingFont` , müssen Sie einige Änderungen an den Steuerelement Headern und den Implementierungs Dateien vornehmen, um die neue Eigenschaft vollständig zu unterstützen.

In der Header Datei des Steuer Elements (. H) fügen Sie die folgende Deklaration einer geschützten Element Variablen hinzu:

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

In der Implementierungs Datei des Steuer Elements (. Cpp), führen Sie die folgenden Schritte aus:

- Initialisieren Sie *m_fontHeading* im steuerelementkonstruktor.

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Deklarieren Sie eine statische fontdebug-Struktur, die die Standard Attribute der Schriftart enthält.

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- `DoPropExchange`Fügen Sie in der Steuerelementmember-Funktion einen-Rückruf der- `PX_Font` Funktion hinzu. Dadurch wird die Initialisierung und Persistenz für Ihre benutzerdefinierte Schriftart Eigenschaft bereitstellt.

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Beenden Sie die Implementierung der `GetHeadingFont` Steuerelementmember-Funktion.

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Beenden Sie die Implementierung der `SetHeadingFont` Steuerelementmember-Funktion.

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Ändern Sie die Funktion des Steuer Elements `OnDraw` , um eine Variable zu definieren, die die zuvor ausgewählte Schriftart enthalten soll.

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Ändern Sie die Funktion des Steuer Elements `OnDraw` , um die benutzerdefinierte Schriftart in den Gerätekontext auszuwählen, indem Sie die folgende Zeile hinzufügen, wo die Schriftart verwendet werden soll.

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Ändern Sie die Funktion des Steuer Elements `OnDraw` , um die vorherige Schriftart wieder in den Gerätekontext auszuwählen, indem Sie die folgende Zeile hinzufügen, nachdem die Schriftart verwendet wurde.

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Nachdem die Eigenschaft für die benutzerdefinierte Schriftart implementiert wurde, sollte die Eigenschaften Seite Standard Schriftart implementiert werden, sodass Steuerelement Benutzer die aktuelle Schriftart des Steuer Elements ändern können. Um die Eigenschaften Seiten-ID für die Eigenschaften Seite Standard Schriftart hinzuzufügen, fügen Sie die folgende Zeile nach dem BEGIN_PROPPAGEIDS-Makro ein:

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Außerdem müssen Sie den count-Parameter des BEGIN_PROPPAGEIDS-Makros um 1 erhöhen. Die folgende Zeile veranschaulicht dies:

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Nachdem Sie diese Änderungen vorgenommen haben, erstellen Sie das gesamte Projekt neu, um die zusätzlichen Funktionen zu integrieren.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Verarbeiten von Schriftart Benachrichtigungen

In den meisten Fällen muss das Steuerelement wissen, wenn die Eigenschaften des Schriftart Objekts geändert wurden. Jedes Schriftart Objekt kann Benachrichtigungen bereitstellen, wenn es geändert wird, indem eine Member-Funktion der- `IFontNotification` Schnittstelle aufgerufen wird, die von implementiert wird `COleControl` .

Wenn das Steuerelement die Eigenschaft Stock Font verwendet, werden seine Benachrichtigungen von der `OnFontChanged` Member-Funktion von verarbeitet `COleControl` . Wenn Sie benutzerdefinierte Schriftart Eigenschaften hinzufügen, können Sie die gleiche Implementierung verwenden. Im Beispiel im vorherigen Abschnitt wurde dies erreicht, indem beim Initialisieren der *m_fontHeading* Member-Variable &*m_xFontNotification* übergeben wird.

![Implementieren von mehreren Schriftart Objekt Schnittstellen](../mfc/media/vc373q1.gif "Mehrere Schnittstellen für Schriftartobjekte werden implementiert") <br/>
Implementieren mehrerer Schnittstellen für Schriftartobjekte

Die voll tonlinien in der obigen Abbildung zeigen, dass beide Schriftart Objekte dieselbe Implementierung von verwenden `IFontNotification` . Dies kann zu Problemen führen, wenn Sie unterscheiden möchten, welche Schriftart geändert wurde.

Eine Möglichkeit, zwischen den Benachrichtigungen des Schriftart Objekts des-Steuer Elements zu unterscheiden, besteht darin, eine separate Implementierung der- `IFontNotification` Schnittstelle für jedes Schriftart Objekt im-Steuerelement zu erstellen. Mit dieser Technik können Sie Ihren Zeichnungs Code optimieren, indem Sie nur die Zeichenfolge oder Zeichen folgen aktualisieren, die die zuletzt geänderte Schriftart verwenden. In den folgenden Abschnitten werden die erforderlichen Schritte zum Implementieren separater Benachrichtigungs Schnittstellen für eine zweite Schriftart Eigenschaft veranschaulicht. Die zweite Schriftart Eigenschaft wird als `HeadingFont` Eigenschaft angenommen, die im vorherigen Abschnitt hinzugefügt wurde.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementieren einer neuen Schriftart Benachrichtigungs Schnittstelle

Um zwischen den Benachrichtigungen von zwei oder mehr Schriftarten zu unterscheiden, muss für jede im Steuerelement verwendete Schriftart eine neue Benachrichtigungs Schnittstelle implementiert werden. In den folgenden Abschnitten wird beschrieben, wie Sie eine neue Schriftart Benachrichtigungs Schnittstelle implementieren, indem Sie die Steuerelement Header-und Implementierungs Dateien ändern.

### <a name="additions-to-the-header-file"></a>Ergänzungen zur Header Datei

In der Header Datei des Steuer Elements (. H) fügen Sie der Klassen Deklaration die folgenden Zeilen hinzu:

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Dadurch wird eine Implementierung der- `IPropertyNotifySink` Schnittstelle mit dem Namen erstellt `HeadingFontNotify` . Diese neue Schnittstelle enthält eine Methode mit dem Namen `OnChanged` .

### <a name="additions-to-the-implementation-file"></a>Ergänzungen zur Implementierungs Datei

Ändern Sie in dem Code, der die Überschrift Schriftart initialisiert (im steuerelementkonstruktor), &*m_xFontNotification* in &*m_xHeadingFontNotify*. Fügen Sie dann den folgenden Code hinzu:

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Die `AddRef` -Methode und die- `Release` Methode in der- `IPropertyNotifySink` Schnittstelle verfolgen den Verweis Zähler für das ActiveX-Steuerelement Objekt. Wenn das Steuerelement Zugriff auf den Schnittstellen Zeiger erhält, ruft das-Steuerelement `AddRef` auf, um den Verweis Zähler zu erhöhen. Wenn das Steuerelement mit dem Zeiger fertig ist, ruft es `Release` auf die gleiche Weise auf, wie `GlobalFree` aufgerufen werden kann, um einen globalen Speicherblock freizugeben. Wenn der Verweis Zähler für diese Schnittstelle auf NULL wechselt, kann die Implementierung der-Schnittstelle freigegeben werden. In diesem Beispiel gibt die- `QueryInterface` Funktion einen Zeiger auf eine- `IPropertyNotifySink` Schnittstelle für ein bestimmtes-Objekt zurück. Mit dieser Funktion kann ein ActiveX-Steuerelement ein Objekt Abfragen, um zu bestimmen, welche Schnittstellen es unterstützt.

Nachdem diese Änderungen am Projekt vorgenommen wurden, erstellen Sie das Projekt neu, und testen Sie die Schnittstelle mit dem Test Container. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Verwenden von Bildern in einem ActiveX-Steuerelement](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](mfc-activex-controls-using-stock-property-pages.md)
