---
title: CPropertyPage-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: f46566eb562f1515e98aedf938ca68b225ee1b67
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751105"
---
# <a name="cpropertypage-class"></a>CPropertyPage-Klasse

Stellt die einzelnen Seiten eines Eigenschaftenblatts dar; wird auch als "Dialogfeld im Registerformat" bezeichnet.

## <a name="syntax"></a>Syntax

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Erstellt ein `CPropertyPage`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertyPage::AbbrechenToClose](#canceltoclose)|Ändert die Schaltfläche OK, um Schließen zu lesen, und deaktiviert die Schaltfläche Abbrechen, nachdem die Seite eines modalen Eigenschaftenblatts nicht wiederhergestellt werden kann.|
|[CPropertyPage::Konstrukt](#construct)|Erstellt ein `CPropertyPage`-Objekt. Verwenden `Construct` Sie diese Option, wenn Sie Ihre Parameter zur Laufzeit angeben möchten oder wenn Sie Arrays verwenden.|
|[CPropertyPage::GetPSP](#getpsp)|Ruft die dem `CPropertyPage` Objekt zugeordnete Windows [PROPSHEETPAGE-Struktur](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) ab.|
|[CPropertyPage::OnApply](#onapply)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Jetzt anwenden geklickt wird.|
|[CPropertyPage::OnCancel](#oncancel)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Abbrechen geklickt wird.|
|[CPropertyPage::OnKillActive](#onkillactive)|Wird vom Framework aufgerufen, wenn die aktuelle Seite nicht mehr die aktive Seite ist. Führen Sie hier die Datenvalidierung durch.|
|[CPropertyPage::OnOK](#onok)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche OK, Jetzt anwenden oder Schließen geklickt wird.|
|[CPropertyPage::OnQuerycancel](#onquerycancel)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Abbrechen geklickt wird und bevor der Abbruch erfolgt ist.|
|[CPropertyPage::Zurücksetzen](#onreset)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Abbrechen geklickt wird.|
|[CPropertyPage::OnSetActive](#onsetactive)|Wird vom Framework aufgerufen, wenn die Seite zur aktiven Seite gemacht wird.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Zurück geklickt wird, während ein Eigenschaftenblatt vom Assistenten-Typ verwendet wird.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Fertig stellen geklickt wird, während ein Eigenschaftenblatt vom Assistenten-Typ verwendet wird.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Wird vom Framework aufgerufen, wenn auf die Schaltfläche Weiter geklickt wird, während ein Eigenschaftenblatt vom Assistenten-Typ verwendet wird.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Leitet die Nachricht an jede Seite des Eigenschaftenblatts weiter.|
|[CPropertyPage::SetModified](#setmodified)|Rufen Sie an, um die Schaltfläche Jetzt anwenden zu aktivieren oder zu deaktivieren.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Die Windows [PROPSHEETPAGE-Struktur.](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) Bietet Zugriff auf grundlegende Eigenschaftenseitenparameter.|

## <a name="remarks"></a>Bemerkungen

Wie bei Standarddialogfeldern leiten Sie `CPropertyPage` eine Klasse für jede Seite in Ihrem Eigenschaftenblatt ab. Um `CPropertyPage`-abgeleitete Objekte zu verwenden, erstellen Sie zuerst ein [CPropertySheet-Objekt,](../../mfc/reference/cpropertysheet-class.md) und erstellen Sie dann ein Objekt für jede Seite, die in das Eigenschaftenblatt geht. Rufen Sie [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) für jede Seite im Blatt auf, und zeigen Sie dann das Eigenschaftenblatt an, indem Sie [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) für ein modales Eigenschaftenblatt oder [CPropertySheet::Create](../../mfc/reference/cpropertysheet-class.md#create) für ein modusloses Eigenschaftenblatt aufrufen.

Sie können einen Typ von Registerkartendialogfeld namens Assistent erstellen, der aus einem Eigenschaftenblatt mit einer Sequenz von Eigenschaftenseiten besteht, die den Benutzer durch die Schritte eines Vorgangs führen, z. B. das Einrichten eines Geräts oder das Erstellen eines Newsletters. In einem Dialogfeld für den Assistenten-Registerkarte verfügen die Eigenschaftenseiten nicht über Registerkarten, und jeweils ist jeweils nur eine Eigenschaftenseite sichtbar. Anstatt über die Schaltflächen OK und Jetzt anwenden zu verfügen, verfügt das Dialogfeld "Registerkarte" vom Assistenten-Typ über eine Schaltfläche "Zurück", eine Schaltfläche "Weiter" oder "Beenden" und die Schaltfläche Abbrechen.

Weitere Informationen zum Einrichten eines Eigenschaftenblatts als Assistent finden Sie unter [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Weitere Informationen zur `CPropertyPage` Verwendung von Objekten finden Sie im Artikel [Eigenschaftenblätter und Eigenschaftenseiten](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::AbbrechenToClose

Rufen Sie diese Funktion auf, nachdem eine nicht wiederherstellbare Änderung an den Daten auf einer Seite eines modalen Eigenschaftenblatts vorgenommen wurde.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ändert die Schaltfläche OK in Schließen und Deaktivieren der Schaltfläche Abbrechen. Diese Änderung warnt den Benutzer, dass eine Änderung dauerhaft ist und die Änderungen nicht abgebrochen werden können.

Die `CancelToClose` Memberfunktion führt in einem moduslosen Eigenschaftenblatt nichts aus, da ein modusloses Eigenschaftenblatt standardmäßig nicht über eine Schaltfläche Abbrechen verfügt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertyPage::QuerySiblings](#querysiblings).

## <a name="cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Konstrukt

Rufen Sie diese Memberfunktion auf, um ein `CPropertyPage` Objekt zu erstellen.

```cpp
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>Parameter

*nIDTemplate*<br/>
ID der für diese Seite verwendeten Vorlage.

*nIDCaption*<br/>
ID des Namens, der auf der Registerkarte für diese Seite platziert werden soll. Wenn 0, wird der Name aus der Dialogvorlage für diese Seite übernommen.

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Vorlagenressource ist.

*nIDHeaderTitle*<br/>
ID des Namens, der am Titelspeicherort des Eigenschaftenseitenkopfes platziert werden soll. Standardmäßig 0.

*nIDHeaderSubTitle*<br/>
ID des Namens, der am Untertitelspeicherort des Eigenschaftenseitenkopfes platziert werden soll. Standardmäßig 0.

### <a name="remarks"></a>Bemerkungen

Das Objekt wird angezeigt, nachdem alle folgenden Bedingungen erfüllt sind:

- Die Seite wurde einem Eigenschaftenblatt mit [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)hinzugefügt.

- Die [Funktion DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) oder [Create](../../mfc/reference/cpropertysheet-class.md#create) des Eigenschaftenblatts wurde aufgerufen.

- Der Benutzer hat diese Seite ausgewählt (tabbed to).

Rufen `Construct` Sie auf, wenn einer der anderen Klassenkonstruktoren nicht aufgerufen wurde. Die `Construct` Memberfunktion ist flexibel, da Sie die Parameteranweisung leer lassen und dann mehrere Parameter und Konstruktionen an einem beliebigen Punkt im Code angeben können.

Sie müssen `Construct` verwenden, wenn Sie mit Arrays arbeiten, und Sie müssen für jedes Element des Arrays aufrufen, `Construct` damit den Datenmembern die richtigen Werte zugewiesen werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>CPropertyPage::CPropertyPage

Erstellt ein `CPropertyPage`-Objekt.

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>Parameter

*nIDTemplate*<br/>
ID der für diese Seite verwendeten Vorlage.

*nIDCaption*<br/>
ID des Namens, der auf der Registerkarte für diese Seite platziert werden soll. Wenn 0, wird der Name aus der Dialogvorlage für diese Seite übernommen.

*dwSize*<br/>
*lpszTemplateName* Zeigt auf eine Zeichenfolge, die den Namen der Vorlage für diese Seite enthält. Lässt keine NULL-Werte zu.

*nIDHeaderTitle*<br/>
ID des Namens, der am Titelspeicherort des Eigenschaftenseitenkopfes platziert werden soll.

*nIDHeaderSubTitle*<br/>
ID des Namens, der am Untertitelspeicherort des Eigenschaftenseitenkopfes platziert werden soll.

### <a name="remarks"></a>Bemerkungen

Das Objekt wird angezeigt, nachdem alle folgenden Bedingungen erfüllt sind:

- Die Seite wurde einem Eigenschaftenblatt mit [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)hinzugefügt.

- Die [Funktion DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) oder [Create](../../mfc/reference/cpropertysheet-class.md#create) des Eigenschaftenblatts wurde aufgerufen.

- Der Benutzer hat diese Seite ausgewählt (tabbed to).

Wenn Sie über mehrere Parameter verfügen (z. B. wenn Sie ein `CPropertyPage`Array verwenden), verwenden Sie [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) anstelle von .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>CPropertyPage::GetPSP

Ruft die dem `CPropertyPage` Objekt zugeordnete Windows [PROPSHEETPAGE-Struktur](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) ab.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis `PROPSHEETPAGE` auf die Struktur.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`ist eine Struktur, deren Member die Eigenschaften von [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)speichern.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Struktur, um die Darstellung einer Eigenschaftenseite nach dem Erstellen zu initialisieren.

Weitere Informationen zu dieser Struktur, einschließlich einer `PROPSHEETPAGE` Liste ihrer Mitglieder, finden Sie im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer die Schaltfläche OK oder Jetzt anwenden wählt.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Änderungen akzeptiert werden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Framework diese Funktion aufruft, werden Änderungen akzeptiert, die auf allen Eigenschaftenseiten im Eigenschaftenblatt vorgenommen wurden, das Eigenschaftenblatt behält den Fokus bei und `OnApply` gibt TRUE (den Wert 1) zurück. Bevor `OnApply` Sie vom Framework aufgerufen werden können, müssen Sie [SetModified](#setmodified) aufgerufen und den Parameter auf TRUE festgelegt haben. Dadurch wird die Schaltfläche Jetzt anwenden aktiviert, sobald der Benutzer eine Änderung auf der Eigenschaftenseite vornimmt.

Überschreiben Sie diese Memberfunktion, um anzugeben, welche Aktion Ihr Programm ausführt, wenn der Benutzer auf die Schaltfläche Jetzt anwenden klickt. Beim Überschreiben sollte die Funktion TRUE zurückgeben, um Änderungen und FALSE zu akzeptieren, um zu verhindern, dass Änderungen wirksam werden.

Die Standardimplementierung `OnApply` `OnOK`von Aufrufen .

Weitere Informationen zu Benachrichtigungen, die gesendet werden, wenn der Benutzer die Schaltfläche Jetzt oder OK in einem Eigenschaftenblatt drücken, finden Sie unter [PSN_APPLY](/windows/win32/Controls/psn-apply) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertyPage::OnOK](#onok).

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>CPropertyPage::OnCancel

Diese Memberfunktion wird vom Framework aufgerufen, wenn die Schaltfläche Abbrechen ausgewählt ist.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um Schaltflächenaktionen abbrechen auszuführen. Der Standardwert negiert alle vorgenommenen Änderungen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>CPropertyPage::OnKillActive

Diese Memberfunktion wird vom Framework aufgerufen, wenn die Seite nicht mehr die aktive Seite ist.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Daten erfolgreich aktualisiert wurden, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um spezielle Datenüberprüfungsaufgaben auszuführen.

Die Standardimplementierung dieser Memberfunktion kopiert Einstellungen von den Steuerelementen auf der Eigenschaftenseite in die Membervariablen der Eigenschaftenseite. Wenn die Daten aufgrund eines DDV-Fehlers (Dialogdatenvalidierung) nicht erfolgreich aktualisiert wurden, behält die Seite den Fokus bei.

Nachdem diese Memberfunktion erfolgreich zurückgegeben wurde, ruft das Framework die [OnOK-Funktion](#onok) der Seite auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer direkt nach dem Aufruf von [OnKillActive](#onkillactive)die Schaltfläche OK oder Jetzt anwenden wählt.

```
virtual void OnOK();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer entweder die Schaltfläche OK oder Jetzt anwenden wählt, erhält das Framework die [PSN_APPLY](/windows/win32/Controls/psn-apply) Benachrichtigung von der Eigenschaftenseite. Der Aufruf `OnOK` an wird nicht gesendet, wenn Sie [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) aufrufen, da die Eigenschaftenseite die Benachrichtigung in diesem Fall nicht sendet.

Überschreiben Sie diese Memberfunktion, um zusätzliches Verhalten zu implementieren, das für die aktuell aktive Seite spezifisch ist, wenn der Benutzer das gesamte Eigenschaftenblatt verwirft.

Die Standardimplementierung dieser Memberfunktion markiert die Seite als "sauber", um `OnKillActive` anzuzeigen, dass die Daten in der Funktion aktualisiert wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQuerycancel

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer auf die Schaltfläche Abbrechen klickt und bevor die Abbruchaktion ausgeführt wurde.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Rückgabewert

Gibt FALSE zurück, um den Abbruchvorgang zu verhindern, oder TRUE, um ihn zuzulassen.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die das Programm ausführt, wenn der Benutzer auf die Schaltfläche Abbrechen klickt.

Die Standardimplementierung `OnQueryCancel` von returns TRUE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::Zurücksetzen

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer die Schaltfläche Abbrechen auswählt.

```
virtual void OnReset();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Framework diese Funktion aufruft, werden Änderungen an allen Eigenschaftenseiten, die vom Benutzer vorgenommen wurden, der zuvor die Schaltfläche Jetzt anwenden ausgewählt hat, verworfen, und das Eigenschaftenblatt behält den Fokus bei.

Überschreiben Sie diese Memberfunktion, um anzugeben, welche Aktion das Programm ausführt, wenn der Benutzer auf die Schaltfläche Abbrechen klickt.

Die Standardimplementierung `OnReset` von bewirkt nichts.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertyPage::OnCancel](#oncancel).

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>CPropertyPage::OnSetActive

Diese Memberfunktion wird vom Framework aufgerufen, wenn die Seite vom Benutzer ausgewählt wird und zur aktiven Seite wird.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Seite erfolgreich aktiv festgelegt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um Aufgaben auszuführen, wenn eine Seite aktiviert ist. Ihre Außerkraftsetzung dieser Memberfunktion würde in der Regel die Standardversion nach dem Aktualisieren von Datenmembern aufrufen, um es zu ermöglichen, die Seitensteuerelemente mit den neuen Daten zu aktualisieren.

Die Standardimplementierung erstellt das Fenster für die Seite, sofern sie nicht zuvor erstellt wurde, und macht sie zur aktiven Seite.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>CPropertyPage::OnWizardBack

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche "Zurück" klickt.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Rückgabewert

0, um automatisch zur nächsten Seite zu gelangen; -1, um zu verhindern, dass die Seite geändert wird. Um zu einer anderen Seite als der nächsten zu springen, geben Sie den Bezeichner des anzuzeigenden Dialogfelds zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die der Benutzer ergreifen muss, wenn die Schaltfläche Zurück gedrückt wird.

Weitere Informationen zum Erstellen eines Eigenschaftenblatts vom Assistenten finden Sie unter [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche Fertig stellen klickt.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Eigenschaftenblatt zerstört wird, wenn der Assistent abgeschlossen ist. andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer in einem Assistenten auf die Schaltfläche **Fertig stellen** klickt, ruft das Framework diese Funktion auf. Wenn `OnWizardFinish` TRUE zurückgegeben wird (ein Wert ungleich Null), kann das Eigenschaftenblatt zerstört werden (aber nicht tatsächlich zerstört). Rufen `DestroyWindow` Sie den Aufruf auf, um das Eigenschaftenblatt zu zerstören. Rufen `DestroyWindow` Sie `OnWizardFinish`nicht von ; Dies führt zu Heap-Beschädigungen oder anderen Fehlern.

Sie können diese Memberfunktion überschreiben, um eine Aktion anzugeben, die der Benutzer ergreifen muss, wenn die Schaltfläche Fertig stellen gedrückt wird. Wenn Sie diese Funktion überschreiben, geben Sie FALSE zurück, um zu verhindern, dass das Eigenschaftenblatt zerstört wird.

Weitere Informationen zu Benachrichtigungen, die gesendet werden, wenn der Benutzer die Schaltfläche Fertig stellen in einem Eigenschaftenblatt des Assistenten drückt, finden Sie unter [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) im Windows SDK.

Weitere Informationen zum Erstellen eines Eigenschaftenblatts vom Assistenten finden Sie unter [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext

Diese Memberfunktion wird vom Framework aufgerufen, wenn der Benutzer in einem Assistenten auf die Schaltfläche Weiter klickt.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Rückgabewert

0, um automatisch zur nächsten Seite zu gelangen; -1, um zu verhindern, dass die Seite geändert wird. Um zu einer anderen Seite als der nächsten zu springen, geben Sie den Bezeichner des anzuzeigenden Dialogfelds zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um eine Aktion anzugeben, die der Benutzer ergreifen muss, wenn die Schaltfläche Weiter gedrückt wird.

Weitere Informationen zum Erstellen eines Eigenschaftenblatts vom Assistenten finden Sie unter [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings

Rufen Sie diese Memberfunktion auf, um eine Nachricht an jede Seite im Eigenschaftenblatt weiterzuleiten.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*wParam*<br/>
Gibt zusätzliche nachrichtenabhängige Informationen an.

*lParam*<br/>
Gibt zusätzliche nachrichtenabhängige Informationen an

### <a name="return-value"></a>Rückgabewert

Der Wert ungleich Null von einer Seite im Eigenschaftenblatt oder 0, wenn alle Seiten den Wert 0 zurückgeben.

### <a name="remarks"></a>Bemerkungen

Wenn eine Seite einen Wert ungleich Null zurückgibt, sendet das Eigenschaftenblatt die Nachricht nicht an nachfolgende Seiten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>CPropertyPage::SetModified

Rufen Sie diese Memberfunktion auf, um die Schaltfläche Jetzt anwenden zu aktivieren oder zu deaktivieren, je nachdem, ob die Einstellungen auf der Eigenschaftenseite auf das entsprechende externe Objekt angewendet werden sollen.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parameter

*bChanged*<br/>
TRUE, um anzugeben, dass die Eigenschaftenseiteneinstellungen seit der letzten Anwendung geändert wurden; FALSE, um anzugeben, dass die Eigenschaftenseiteneinstellungen angewendet wurden oder ignoriert werden sollten.

### <a name="remarks"></a>Bemerkungen

Das Framework verfolgt, welche Seiten "schmutzig" sind, d. h. Eigenschaftenseiten, für die Sie aufgerufen `SetModified( TRUE )`haben. Die Schaltfläche Jetzt anwenden wird immer `SetModified( TRUE )` aktiviert, wenn Sie eine der Seiten aufrufen. Die Schaltfläche Jetzt anwenden wird `SetModified( FALSE )` deaktiviert, wenn Sie eine der Seiten aufrufen, jedoch nur, wenn keine der anderen Seiten "schmutzig" ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet-Klasse](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
