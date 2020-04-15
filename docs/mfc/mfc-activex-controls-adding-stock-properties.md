---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364662"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften

Bestandseigenschaften unterscheiden sich von benutzerdefinierten Eigenschaften `COleControl`dadurch, dass sie bereits von der Klasse implementiert wurden. `COleControl`enthält vordefinierte Memberfunktionen, die allgemeine Eigenschaften für das Steuerelement unterstützen. Zu den allgemeinen Eigenschaften gehören die Beschriftung des Steuerelements sowie die Vordergrund- und Hintergrundfarben. Weitere Informationen zu anderen Bestandseigenschaften finden Sie weiter unten in diesem Artikel unter [Bestandseigenschaften, die vom Eigenschaften-Assistenten hinzufügen unterstützt](#_core_stock_properties_supported_by_classwizard) werden. Den Dispatch-Map-Einträgen für Bestandseigenschaften wird immer DISP_STOCKPROP vorangestellt.

In diesem Artikel wird beschrieben, wie einem ActiveX-Steuerelement mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine Bestandseigenschaft (in diesem Fall Caption) hinzugefügt wird, und die resultierenden Codeänderungen erläutert. Dabei werden folgende Themen behandelt:

- [Verwenden des Eigenschaften-Assistenten hinzufügen zum Hinzufügen einer Bestandseigenschaft](#_core_using_classwizard_to_add_a_stock_property)

- [Eigenschaften-Assistenten-Änderungen für Bestandseigenschaften hinzufügen](#_core_classwizard_changes_for_stock_properties)

- [Vom Eigenschaften-Assistenten zum Hinzufügen von Eigenschaften unterstützten Bestandseigenschaften](#_core_stock_properties_supported_by_classwizard)

- [Bestandseigenschaften und Benachrichtigung](#_core_stock_properties_and_notification)

- [Farbeigenschaften](#_core_color_properties)

    > [!NOTE]
    >  Benutzerdefinierte Steuerelemente von Visual Basic verfügen in der Regel über Eigenschaften wie Oben, Links, Breite, Höhe, Ausrichtung, Tag, Name, TabIndex, TabStop und Parent. ActiveX-Steuerelementcontainer sind jedoch für die Implementierung dieser Steuerelementeigenschaften verantwortlich, und daher sollten ActiveX-Steuerelemente diese Eigenschaften nicht unterstützen.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Verwenden des Eigenschaften-Assistenten hinzufügen zum Hinzufügen einer Stock-Eigenschaft

Das Hinzufügen von Bestandseigenschaften erfordert weniger Code als das `COleControl`Hinzufügen benutzerdefinierter Eigenschaften, da die Unterstützung für die Eigenschaft automatisch von verarbeitet wird. Das folgende Verfahren veranschaulicht das Hinzufügen der stock Caption-Eigenschaft zu einem ActiveX-Steuerelementframework und kann auch zum Hinzufügen anderer Bestandseigenschaften verwendet werden. Ersetzen Sie den ausgewählten Bestandseigenschaftsnamen durch Caption.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>So fügen Sie die Stock Caption-Eigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Eigenschaften-Assistent hinzufügen](../ide/names-add-property-wizard.md)geöffnet.

1. Klicken Sie im Feld **Eigenschaftenname** auf **Beschriftung**.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Eigenschaften-Assistenten-Änderungen für Aktieneigenschaften hinzufügen

Da `COleControl` Bestandseigenschaften unterstützt werden, ändert der Add Property Wizard die Klassendeklaration in keiner Weise. die Eigenschaft wird der Dispatchzuordnung hinzugefügt. Der Eigenschaften-Assistent hinzufügen fügt der Dispatchzuordnung des Steuerelements die folgende Zeile hinzu, die sich in der Implementierung befindet (. CPP)-Datei:

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Die folgende Zeile wird der Schnittstellenbeschreibung des Steuerelements hinzugefügt (. IDL)-Datei:

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Diese Zeile weist der Caption-Eigenschaft eine bestimmte ID zu. Beachten Sie, dass die Eigenschaft bindbar ist und die Berechtigung von der Datenbank anfordert, bevor Sie den Wert ändern.

Dadurch wird die Caption-Eigenschaft für Benutzer des Steuerelements verfügbar. Um den Wert einer stock-Eigenschaft zu verwenden, greifen `COleControl` Sie auf eine Membervariable oder Memberfunktion der Basisklasse zu. Weitere Informationen zu diesen Membervariablen und Memberfunktionen finden Sie im nächsten Abschnitt, Stock Properties Supported by the Add Property Wizard.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Vom Eigenschaften-Assistenten zum Hinzufügen werden Aktieneigenschaften

Die `COleControl` Klasse bietet neun Bestandseigenschaften. Sie können die gewünschten Eigenschaften mithilfe des Eigenschaften-Assistenten hinzufügen hinzufügen.

|Eigenschaft|Dispatch-Map-Eintrag|So greifen Sie auf den Wert zu|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Wert, `m_sAppearance`auf den als zugegriffen werden kann.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Auf den `GetBackColor`Wert, auf den durch Aufrufen zugegriffen werden kann.|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Wert, `m_sBorderStyle`auf den als zugegriffen werden kann.|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Auf den `InternalGetText`Wert, auf den durch Aufrufen zugegriffen werden kann.|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Wert, `m_bEnabled`auf den als zugegriffen werden kann.|
|`Font`|DISP_STOCKPROP_FONT( )|Siehe Den Artikel [MFC ActiveX Controls: Verwenden von Schriftarten](../mfc/mfc-activex-controls-using-fonts.md) für die Verwendung.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Auf den `GetForeColor`Wert, auf den durch Aufrufen zugegriffen werden kann.|
|`hWnd`|DISP_STOCKPROP_HWND( )|Wert, `m_hWnd`auf den als zugegriffen werden kann.|
|`Text`|DISP_STOCKPROP_TEXT( )|Auf den `InternalGetText`Wert, auf den durch Aufrufen zugegriffen werden kann. Diese Eigenschaft ist `Caption`die gleiche wie , mit Ausnahme des Eigenschaftsnamens.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Wert zugänglich `m_lReadyState` als oder`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Bestandseigenschaften und Benachrichtigungen

Die meisten Bestandseigenschaften verfügen über Benachrichtigungsfunktionen, die überschrieben werden können. Wenn z. `BackColor` B. die `OnBackColorChanged` Eigenschaft geändert wird, wird die Funktion (eine Memberfunktion der Steuerelementklasse) aufgerufen. Die Standardimplementierung `COleControl`(in `InvalidateControl`) ruft auf. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Aktionen als Reaktion auf diese Situation ausführen möchten.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Farbeigenschaften

Sie können den `ForeColor` `BackColor` Bestand und die Eigenschaften oder Ihre eigenen benutzerdefinierten Farbeigenschaften beim Malen des Steuerelements verwenden. Um eine color-Eigenschaft zu verwenden, rufen Sie die [Memberfunktion COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) auf. Die Parameter dieser Funktion sind der Wert der color-Eigenschaft und ein optionales Palettenhandle. Der Rückgabewert ist ein **COLORREF-Wert,** der an `SetTextColor` GDI-Funktionen übergeben werden kann, z. B. und `CreateSolidBrush`.

Auf die Farbwerte `ForeColor` `BackColor` für den Bestand und `GetForeColor` die `GetBackColor` Eigenschaften wird entweder die oder die Funktion zugegriffen.

Im folgenden Beispiel wird die Verwendung dieser beiden Farbeigenschaften beim Malen eines Steuerelements veranschaulicht. Es initialisiert eine temporäre **COLORREF-Variable** `CBrush` und `TranslateColor`ein Objekt `ForeColor` mit Aufrufen von: eines, das die Eigenschaft verwendet, und das andere mit der `BackColor` Eigenschaft. Ein `CBrush` temporäres Objekt wird dann verwendet, um das Rechteck des `ForeColor` Steuerelements zu malen, und die Textfarbe wird mithilfe der Eigenschaft festgelegt.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](../mfc/reference/colecontrol-class.md)
