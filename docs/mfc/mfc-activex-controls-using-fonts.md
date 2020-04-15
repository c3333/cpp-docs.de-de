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
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358270"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten

Wenn das ActiveX-Steuerelement Text anzeigt, können Sie dem Steuerelementbenutzer erlauben, die Textdarstellung zu ändern, indem Sie eine Schriftarteigenschaft ändern. Schriftarteneigenschaften werden als Schriftartobjekte implementiert und können einer von zwei Typen sein: Lager oder benutzerdefiniert. Stock Font-Eigenschaften sind vorimplementierte Schriftarteigenschaften, die Sie mit dem Eigenschaften-Assistenten hinzufügen können. Benutzerdefinierte Font-Eigenschaften sind nicht vorimplementiert, und der Steuerelemententwickler bestimmt das Verhalten und die Verwendung der Eigenschaft.

In diesem Artikel werden die folgenden Themen behandelt:

- [Verwenden der Stock Font-Eigenschaft](#_core_using_the_stock_font_property)

- [Verwenden von custom Font-Eigenschaften in Ihrem Steuerelement](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Verwenden der Stock Font-Eigenschaft

Stock Font-Eigenschaften werden von der Klasse [COleControl](../mfc/reference/colecontrol-class.md)vorimplementiert. Darüber hinaus ist eine Standardmäßige Font-Eigenschaftsseite verfügbar, die es dem Benutzer ermöglicht, verschiedene Attribute des Schriftartobjekts zu ändern, z. B. Name, Größe und Stil.

Greifen Sie über die Funktionen [GetFont](../mfc/reference/colecontrol-class.md#getfont), [SetFont](../mfc/reference/colecontrol-class.md#setfont) `COleControl`und [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) von auf das Schriftartobjekt zu. Der Steuerelementbenutzer greift über die `GetFont` `SetFont` auf das Font-Objekt zu und funktioniert auf die gleiche Weise wie jede andere Get/Set-Eigenschaft. Wenn der Zugriff auf das Font-Objekt innerhalb `InternalGetFont` eines Steuerelements erforderlich ist, verwenden Sie die Funktion.

Wie in [MFC ActiveX Controls: Properties](../mfc/mfc-activex-controls-properties.md)erläutert, ist das Hinzufügen von Bestandseigenschaften mit dem Assistenten zum Hinzufügen von [Eigenschaften](../ide/names-add-property-wizard.md)einfach. Sie wählen die Font-Eigenschaft aus, und der Eigenschaften-Assistent hinzufügen fügt den Eintrag "Lagerschriftart" automatisch in die Dispatch-Map des Steuerelements ein.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>So fügen Sie die Eigenschaft "Bestand Font" mithilfe des Eigenschaften-Assistenten hinzufügen hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Eigenschaften-Assistent hinzufügen geöffnet.

1. Klicken Sie im Feld **Eigenschaftenname** auf **Schriftart**.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften fügt der Dispatchzuordnung des Steuerelements die folgende Zeile hinzu, die sich in der Implementierungsdatei der Steuerelementklassen befindet:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Darüber hinaus fügt der Assistent eigenschaften hinzufügen dem Steuerelement die folgende Zeile hinzu. IDL-Datei:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Die Stock Caption-Eigenschaft ist ein Beispiel für eine Texteigenschaft, die mithilfe der Eigenschaftsinformationen "Schriftart" gezeichnet werden kann. Durch das Hinzufügen der stock Caption-Eigenschaft zum Steuerelement werden Schritte verwendet, die denen für die Eigenschaft "Font" ähneln.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>So fügen Sie die Stock Caption-Eigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Eigenschaften-Assistent hinzufügen geöffnet.

1. Klicken Sie im Feld **Eigenschaftenname** auf **Beschriftung**.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften fügt der Dispatchzuordnung des Steuerelements die folgende Zeile hinzu, die sich in der Implementierungsdatei der Steuerelementklassen befindet:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Ändern der OnDraw-Funktion

Die Standardimplementierung `OnDraw` von verwendet die Windows-Systemschriftart für den gesamten Text, der im Steuerelement angezeigt wird. Dies bedeutet, dass `OnDraw` Sie den Code ändern müssen, indem Sie das Schriftartobjekt im Gerätekontext auswählen. Rufen Sie dazu [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) auf und übergeben Sie den Gerätekontext des Steuerelements, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Nachdem `OnDraw` die Funktion geändert wurde, um das Font-Objekt zu verwenden, wird jeder Text innerhalb des Steuerelements mit Merkmalen aus der Eigenschaft "Stock Font" des Steuerelements angezeigt.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Verwenden von custom Font-Eigenschaften in Ihrem Steuerelement

Zusätzlich zur Eigenschaft "Bestände Font" kann das ActiveX-Steuerelement benutzerdefinierte Font-Eigenschaften aufweisen. Um eine benutzerdefinierte Schriftarteigenschaft hinzuzufügen, müssen Sie:

- Verwenden Sie den Assistenten zum Hinzufügen von Eigenschaften, um die benutzerdefinierte Font-Eigenschaft zu implementieren.

- [Verarbeiten von Schriftartbenachrichtigungen](#_core_processing_font_notifications).

- [Implementieren einer neuen Schriftartbenachrichtigungsschnittstelle](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementieren einer custom Font-Eigenschaft

Um eine benutzerdefinierte Font-Eigenschaft zu implementieren, verwenden Sie den Eigenschaften-Assistenten hinzufügen, um die Eigenschaft hinzuzufügen und dann einige Änderungen am Code vorzunehmen. In den folgenden Abschnitten wird `HeadingFont` beschrieben, wie sie dem Sample-Steuerelement die benutzerdefinierte Eigenschaft hinzufügt.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>So fügen Sie die benutzerdefinierte Font-Eigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der Eigenschaften-Assistent hinzufügen geöffnet.

1. Geben Sie im Feld **Eigenschaftenname** einen Namen für die Eigenschaft ein. Verwenden Sie in diesem Beispiel **HeadingFont**.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** **IDispatch** <strong>\*</strong> für den Eigenschaftstyp aus.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von `HeadingFont` Eigenschaften erstellt `CSampleCtrl` den Code, um die benutzerdefinierte Eigenschaft der Klasse und der SAMPLE hinzuzufügen. IDL-Datei. Da `HeadingFont` es sich um einen Get/Set-Eigenschaftstyp `CSampleCtrl` handelt, ändert der Erweiterungseigenschafts-Assistent die Dispatchzuordnung der Klasse so, dass sie einen DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX-Makroeintrag](../mfc/reference/dispatch-maps.md#disp_property_ex) enthält:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Das DISP_PROPERTY_EX Makro `HeadingFont` ordnet den `CSampleCtrl` Eigenschaftennamen den entsprechenden `GetHeadingFont` `SetHeadingFont`Methoden der Klasse Get and Set zu, und . Der Typ des Eigenschaftswerts wird ebenfalls angegeben. in diesem Fall VT_FONT.

Der Assistent zum Hinzufügen von Eigenschaften fügt auch eine Deklaration in der Steuerelementheaderdatei hinzu (. H) für `GetHeadingFont` `SetHeadingFont` die und Funktionen und fügt deren Funktionsvorlagen in der Steuerungsimplementierungsdatei (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Schließlich ändert der Eigenschaften-Assistent zum Hinzufügen das Steuerelement . IDL-Datei durch Hinzufügen `HeadingFont` eines Eintrags für die Eigenschaft:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Änderungen am Steuercode

Nachdem Sie die `HeadingFont` Eigenschaft dem Steuerelement hinzugefügt haben, müssen Sie einige Änderungen an den Steuerelementheader- und Implementierungsdateien vornehmen, um die neue Eigenschaft vollständig zu unterstützen.

In der Steuerelementheaderdatei (. H), fügen Sie die folgende Deklaration einer geschützten Membervariablen hinzu:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

In der Kontrollimplementierungsdatei (. CPP), führen Sie die folgenden Schritte aus:

- Initialisieren Sie *m_fontHeading* im Steuerelementkonstruktor.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Deklarieren Sie eine statische FONTDESC-Struktur, die Standardattribute der Schriftart enthält.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- Fügen Sie `DoPropExchange` in der Steuerelementmemberfunktion `PX_Font` einen Aufruf zur Funktion hinzu. Dies bietet Initialisierung und Persistenz für Ihre benutzerdefinierte Font-Eigenschaft.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Beenden Sie `GetHeadingFont` die Implementierung der Steuerelementmemberfunktion.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Beenden Sie `SetHeadingFont` die Implementierung der Steuerelementmemberfunktion.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Ändern Sie `OnDraw` die Steuerelementmemberfunktion, um eine Variable zu definieren, die die zuvor ausgewählte Schriftart enthalten soll.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Ändern Sie `OnDraw` die Steuerelementmemberfunktion, um die benutzerdefinierte Schriftart im Gerätekontext auszuwählen, indem Sie die folgende Zeile überall dort hinzufügen, wo die Schriftart verwendet werden soll.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Ändern Sie `OnDraw` die Steuerelementmemberfunktion, um die vorherige Schriftart wieder in den Gerätekontext auszuwählen, indem Sie die folgende Zeile hinzufügen, nachdem die Schriftart verwendet wurde.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Nachdem die benutzerdefinierte Font-Eigenschaft implementiert wurde, sollte die standardmäßige Font-Eigenschaftsseite implementiert werden, sodass Steuerelementbenutzer die aktuelle Schriftart des Steuerelements ändern können. Um die Eigenschaftenseiten-ID für die Standard-Font-Eigenschaftsseite hinzuzufügen, fügen Sie die folgende Zeile nach dem BEGIN_PROPPAGEIDS-Makro ein:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Sie müssen auch den Zählparameter Ihres BEGIN_PROPPAGEIDS Makros um eins erhöhen. Die folgende Zeile veranschaulicht dies:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie das gesamte Projekt neu, um die zusätzliche Funktionalität zu integrieren.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Verarbeiten von Schriftartbenachrichtigungen

In den meisten Fällen muss das Steuerelement wissen, wann die Eigenschaften des Schriftartobjekts geändert wurden. Jedes Font-Objekt kann Benachrichtigungen bereitstellen, wenn es sich `IFontNotification` ändert, `COleControl`indem es eine Memberfunktion der Schnittstelle aufruft, die von implementiert wird.

Wenn das Steuerelement die Eigenschaft stock Font verwendet, `OnFontChanged` werden seine `COleControl`Benachrichtigungen von der Memberfunktion von behandelt. Wenn Sie benutzerdefinierte Schriftarteigenschaften hinzufügen, können Sie festlegen, dass sie dieselbe Implementierung verwenden. Im Beispiel im vorherigen Abschnitt wurde dies durch Übergeben &*m_xFontNotification* beim Initialisieren der *m_fontHeading* Membervariablen erreicht.

![Implementieren mehrerer Font-Objektschnittstellen](../mfc/media/vc373q1.gif "Mehrere Schnittstellen für Schriftartobjekte werden implementiert") <br/>
Implementieren mehrerer Schnittstellen für Schriftartobjekte

Die durchgezogenen Linien in der Abbildung oben zeigen, `IFontNotification`dass beide Schriftartobjekte die gleiche Implementierung von verwenden. Dies kann zu Problemen führen, wenn Sie unterscheiden möchten, welche Schriftart geändert wurde.

Eine Möglichkeit, zwischen den Schriftartobjektbenachrichtigungen des Steuerelements zu `IFontNotification` unterscheiden, besteht darin, eine separate Implementierung der Schnittstelle für jedes Schriftartobjekt im Steuerelement zu erstellen. Mit dieser Technik können Sie den Zeichnungscode optimieren, indem Sie nur die Zeichenfolge oder Zeichenfolgen aktualisieren, die die kürzlich geänderte Schriftart verwenden. In den folgenden Abschnitten werden die Schritte veranschaulicht, die zum Implementieren separater Benachrichtigungsschnittstellen für eine zweite Font-Eigenschaft erforderlich sind. Die zweite font-Eigenschaft wird `HeadingFont` als die Eigenschaft angenommen, die im vorherigen Abschnitt hinzugefügt wurde.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementieren einer neuen Font Notification-Schnittstelle

Um zwischen den Benachrichtigungen von zwei oder mehr Schriftarten zu unterscheiden, muss für jede Schriftart, die im Steuerelement verwendet wird, eine neue Benachrichtigungsschnittstelle implementiert werden. In den folgenden Abschnitten wird beschrieben, wie Sie eine neue Schriftartbenachrichtigungsschnittstelle implementieren, indem Sie den Steuerelementheader und die Implementierungsdateien ändern.

### <a name="additions-to-the-header-file"></a>Ergänzungen zur Headerdatei

In der Steuerelementheaderdatei (. H), fügen Sie der Klassendeklaration die folgenden Zeilen hinzu:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Dadurch wird eine `IPropertyNotifySink` Implementierung `HeadingFontNotify`der Schnittstelle mit dem Namen erstellt. Diese neue Schnittstelle enthält `OnChanged`eine Methode namens .

### <a name="additions-to-the-implementation-file"></a>Ergänzungen zur Implementierungsdatei

Ändern Sie im Code, der die Überschriftenschriftart (im Steuerelementkonstruktor) initialisiert, &*m_xFontNotification* in &*m_xHeadingFontNotify*. Fügen Sie dann den folgenden Code hinzu:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Die `AddRef` `Release` und Methoden `IPropertyNotifySink` in der Schnittstelle verfolgen die Referenzanzahl für das ActiveX-Steuerelementobjekt. Wenn das Steuerelement Zugriff auf den Schnittstellenzeiger `AddRef` erhält, ruft das Steuerelement auf, um die Verweisanzahl zu erhöhen. Wenn das Steuerelement mit dem Zeiger `Release`abgeschlossen ist, ruft `GlobalFree` es auf die gleiche Weise auf, wie es aufgerufen werden könnte, um einen globalen Speicherblock freizugeben. Wenn die Referenzanzahl für diese Schnittstelle auf Null geht, kann die Schnittstellenimplementierung freigegeben werden. In diesem Beispiel `QueryInterface` gibt die Funktion `IPropertyNotifySink` einen Zeiger auf eine Schnittstelle für ein bestimmtes Objekt zurück. Diese Funktion ermöglicht es einem ActiveX-Steuerelement, ein Objekt abzufragen, um zu bestimmen, welche Schnittstellen es unterstützt.

Nachdem diese Änderungen an Ihrem Projekt vorgenommen wurden, erstellen Sie das Projekt neu, und verwenden Sie Testcontainer, um die Schnittstelle zu testen. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Verwenden von Bildern in einem ActiveX-Steuerelement](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](../mfc/mfc-activex-controls-using-stock-property-pages.md)
