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
ms.openlocfilehash: 27fed55ac8a5fc8b95f81c1bfd2c6edb3da6227d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502249"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften

Die Eigenschaften von Aktien unterscheiden sich von benutzerdefinierten Eigenschaften darin, dass Sie bereits von der-Klasse implementiert werden `COleControl` . `COleControl` enthält vordefinierte Element Funktionen, die allgemeine Eigenschaften für das-Steuerelement unterstützen. Zu den allgemeinen Eigenschaften gehören die Beschriftung des Steuer Elements und die Vordergrund-und Hintergrundfarben. Weitere Informationen zu anderen Aktien Eigenschaften finden Sie weiter unten in diesem Artikel [unter vom Assistenten zum Hinzufügen von Eigenschaften unterstützte Eigenschaften](#_core_stock_properties_supported_by_classwizard) . Die dispatchzuordnungs Einträge für die vordefinierten Eigenschaften werden immer DISP_STOCKPROP vorangestellt.

In diesem Artikel wird beschrieben, wie Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine vordefinierte Eigenschaft (in diesem Fall eine Beschriftung) einem ActiveX-Steuerelement hinzufügen und die resultierenden Codeänderungen erläutern. Dabei werden folgende Themen behandelt:

- [Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer Aktien Eigenschaft](#_core_using_classwizard_to_add_a_stock_property)

- [Hinzufügen von Eigenschaften-Assistenten Änderungen für Bestands Eigenschaften](#_core_classwizard_changes_for_stock_properties)

- [Vom Assistenten zum Hinzufügen von Eigenschaften unterstützte Eigenschaften](#_core_stock_properties_supported_by_classwizard)

- [Bestands Eigenschaften und Benachrichtigung](#_core_stock_properties_and_notification)

- [Farbeigenschaften](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic benutzerdefinierten Steuerelementen verfügen in der Regel über Eigenschaften wie z. b. Top, Left, Width, Height, align, Tag, Name, TabIndex, Tabstopps und Parent. ActiveX-Steuerelement Container sind jedoch für die Implementierung dieser Steuerelement Eigenschaften zuständig. Daher sollten ActiveX-Steuerelemente diese Eigenschaften nicht unterstützen.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a> Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer Aktien Eigenschaft

Das Hinzufügen von vordefinierten Eigenschaften erfordert weniger Code als das Hinzufügen von benutzerdefinierten Eigenschaften, da die Unterstützung für die Eigenschaft `COleControl` automatisch von erfolgt Im folgenden Verfahren wird veranschaulicht, wie Sie die Eigenschaft Stock Caption zu einem ActiveX-Steuerelement Framework hinzufügen und auch zum Hinzufügen von weiteren vordefinierten Eigenschaften verwendet werden können. Ersetzen Sie den Namen der ausgewählten Aktien Eigenschaft durch die Beschriftung.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>So fügen Sie die Eigenschaft Stock Caption mithilfe des Assistenten zum Hinzufügen von Eigenschaften hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Assistent zum Hinzufügen von Eigenschaften](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)geöffnet.

1. Klicken Sie im Feld **Eigenschafts Name** auf **Beschriftung**.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a> Hinzufügen von Eigenschaften-Assistenten Änderungen für Bestands Eigenschaften

Da `COleControl` vordefinierte Eigenschaften unterstützt, ändert der Assistent zum Hinzufügen von Eigenschaften die Klassen Deklaration in keiner Weise. die Eigenschaft wird der dispatchmap hinzugefügt. Der Assistent zum Hinzufügen von Eigenschaften fügt der Dispatchzuordnung des-Steuer Elements die folgende Zeile hinzu, die sich in der-Implementierung befindet (. Cpp-Datei:

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Die folgende Zeile wird der Schnittstellen Beschreibung Ihres Steuer Elements hinzugefügt (. IDL-Datei):

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Diese Zeile weist die Caption-Eigenschaft einer bestimmten ID zu. Beachten Sie, dass die-Eigenschaft bindbar ist und vor der Änderung des-Werts eine Berechtigung aus der Datenbank anfordert.

Dadurch ist die Caption-Eigenschaft für Benutzer Ihres Steuer Elements verfügbar. Um den Wert einer Aktien Eigenschaft zu verwenden, greifen Sie auf eine Member-oder Member-Funktion der `COleControl` Basisklasse zu. Weitere Informationen zu diesen Element Variablen und Element Funktionen finden Sie im nächsten Abschnitt, die vom Assistenten zum Hinzufügen von Eigenschaften unterstützt werden.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a> Vom Assistenten zum Hinzufügen von Eigenschaften unterstützte Eigenschaften

Die- `COleControl` Klasse stellt neun Aktien Eigenschaften bereit. Mithilfe des Assistenten zum Hinzufügen von Eigenschaften können Sie die gewünschten Eigenschaften hinzufügen.

|Eigenschaft|Dispatch-Zuordnungs Eintrag|Zugreifen auf den Wert|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ()|Wert, der als verfügbar ist `m_sAppearance` .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ()|Der Zugriff ist durch Aufrufen von möglich `GetBackColor` .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ()|Wert, der als verfügbar ist `m_sBorderStyle` .|
|`Caption`|DISP_STOCKPROP_CAPTION ()|Der Zugriff ist durch Aufrufen von möglich `InternalGetText` .|
|`Enabled`|DISP_STOCKPROP_ENABLED ()|Wert, der als verfügbar ist `m_bEnabled` .|
|`Font`|DISP_STOCKPROP_FONT ()|Weitere Informationen finden [Sie unter MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten](mfc-activex-controls-using-fonts.md) zur Verwendung|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ()|Der Zugriff ist durch Aufrufen von möglich `GetForeColor` .|
|`hWnd`|DISP_STOCKPROP_HWND ()|Wert, der als verfügbar ist `m_hWnd` .|
|`Text`|DISP_STOCKPROP_TEXT ()|Der Zugriff ist durch Aufrufen von möglich `InternalGetText` . Diese Eigenschaft ist `Caption` mit Ausnahme des Eigenschafts namens identisch.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ()|Wert, der als oder verfügbar ist `m_lReadyState``GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a> Bestands Eigenschaften und Benachrichtigung

Die meisten Aktien Eigenschaften verfügen über Benachrichtigungsfunktionen, die überschrieben werden können. Wenn z. b. die- `BackColor` Eigenschaft geändert wird, wird die- `OnBackColorChanged` Funktion (eine Member-Funktion der Steuerelement Klasse) aufgerufen. Die Standard Implementierung (in `COleControl` ) Ruft auf `InvalidateControl` . Überschreiben Sie diese Funktion, wenn Sie zusätzliche Aktionen als Reaktion auf diese Situation ausführen möchten.

## <a name="color-properties"></a><a name="_core_color_properties"></a> Farbeigenschaften

Wenn Sie das Steuerelement zeichnen, können Sie die Eigenschaften "Stock" `ForeColor` und " `BackColor` Properties" oder Ihre eigenen benutzerdefinierten Farbeigenschaften verwenden. Um eine Color-Eigenschaft zu verwenden, wenden Sie die [COleControl:: TranslateColor](reference/colecontrol-class.md#translatecolor) -Member-Funktion an. Die Parameter dieser Funktion sind der Wert der Color-Eigenschaft und ein optionales Palettenhandle. Der Rückgabewert ist ein **COLORREF** -Wert, der an GDI-Funktionen (z `SetTextColor` . b. und) übermittelt werden kann `CreateSolidBrush` .

Der Zugriff auf die Farbwerte für den Bestand `ForeColor` und die `BackColor` Eigenschaften erfolgt durch Aufrufen der- `GetForeColor` Funktion oder der- `GetBackColor` Funktion.

Im folgenden Beispiel wird veranschaulicht, wie diese beiden Farbeigenschaften beim Zeichnen eines-Steuer Elements verwendet werden. Sie Initialisiert eine temporäre **COLORREF** -Variable und ein- `CBrush` Objekt mit Aufrufen von `TranslateColor` : eine, die die `ForeColor` -Eigenschaft verwendet, und die andere mit der- `BackColor` Eigenschaft. Ein temporäres `CBrush` Objekt wird dann verwendet, um das Rechteck des Steuer Elements zu zeichnen, und die Textfarbe wird mithilfe der-Eigenschaft festgelegt `ForeColor` .

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
