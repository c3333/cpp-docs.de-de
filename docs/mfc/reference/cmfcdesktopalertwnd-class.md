---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: f9c59258cf757b5468985a954640ccec1543512b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367633"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

Die `CMFCDesktopAlertWnd` Klasse implementiert die Funktionalität eines moduslosen Dialogfelds, das auf dem Bildschirm angezeigt wird, um den Benutzer über ein Ereignis zu informieren.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Erstellen](#create)|Erstellt und initialisiert das Desktop-Warnfenster.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Gibt die Animationsgeschwindigkeit zurück.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Gibt den Animationstyp zurück.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Gibt das Zeitout für das automatische Schließen zurück.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Gibt die Höhe der Beschriftung zurück.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Gibt die letzte gültige Position des Desktopwarnungsfensters auf dem Bildschirm zurück.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Gibt die Transparenzebene zurück.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Bestimmt, ob das Desktop-Warnfenster mit der kleinen Beschriftung angezeigt wird.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Wird vom Framework aufgerufen, wenn der Benutzer auf eine Linkschaltfläche im Desktop-Warnungsmenü klickt.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Das Framework ruft diese Memberfunktion auf, wenn der Benutzer ein Element aus einem Menü auswählt, wenn ein untergeordnetes Steuerelement eine Benachrichtigung sendet oder wenn ein Beschleunigertastenanschlag übersetzt wird. (Überschreibt [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Legt die neue Animationsgeschwindigkeit fest.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Legt den Animationstyp fest.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Legt die Zeitfürst beim automatischen Schließen fest.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Wechselt zwischen kleinen und normalen Beschriftungen.|
|[CMFCDesktopAlertWnd::SetTransparenz](#settransparency)|Legt die Transparenzebene fest.|

## <a name="remarks"></a>Bemerkungen

Ein Desktop-Warnfenster kann transparent sein, es kann mit Animationseffekten angezeigt werden, und es kann verschwinden (nach einer angegebenen Verzögerung oder wenn der Benutzer es durch Klicken auf die Schaltfläche Schließen schließt schließt) schließt.

Ein Desktop-Warnfenster kann auch ein Standarddialogfeld enthalten, das wiederum ein Symbol, einen Nachrichtentext (eine Beschriftung) und einen Link enthält. Alternativ kann ein Desktop-Warnfenster ein benutzerdefiniertes Dialogfeld aus den Ressourcen der Anwendung enthalten.

Sie erstellen ein Desktop-Warnfenster in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, um das `CMFCDesktopAlertWnd` Objekt zu erstellen. Rufen Sie zweitens die [Memberfunktion CMFCDesktopAlertWnd::Create](#create) auf, `CMFCDesktopAlertWnd` um das Fenster zu erstellen und es an das Objekt anzufügen.

Das `CMFCDesktopAlertWnd` Objekt erstellt ein spezielles untergeordnetes Dialogfeld, das den Clientbereich des Desktopwarnungsfensters ausfüllt. Das Dialogfeld besitzt alle Steuerelemente, die darauf positioniert sind.

Führen Sie die folgenden Schritte aus, um ein benutzerdefiniertes Dialogfeld im Popupfenster anzuzeigen:

1. Leiten Sie eine Klasse von `CMFCDesktopAlertDialog` ab.

1. Erstellen Sie eine untergeordnete Dialogfeldvorlage in den Ressourcen.

1. Rufen Sie [CMFCDesktopAlertWnd::Create](#create) mit der Ressourcen-ID der Dialogfeldvorlage und einem Zeiger auf die Laufzeitklasseninformationen der abgeleiteten Klasse auf.

1. Programmieren Sie das benutzerdefinierte Dialogfeld, um alle Benachrichtigungen zu verarbeiten, die von den gehosteten Steuerelementen stammen, oder programmieren Sie die gehosteten Steuerelemente, um diese Benachrichtigungen direkt zu verarbeiten.

Verwenden Sie die folgenden Funktionen, um das Verhalten des Desktopwarnungsfensters zu steuern:

- Legen Sie den Animationstyp fest, indem Sie [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)aufrufen. Gültige Optionen umfassen Entfalten, Verschieben und Ausblenden.

- Legen Sie die Animationsframegeschwindigkeit fest, indem Sie [CMFCDesktopAlertWnd::SetAnimationSpeed aufrufen.](#setanimationspeed)

- Legen Sie die Transparenzebene fest, indem Sie [CMFCDesktopAlertWnd::SetTransparency](#settransparency)aufrufen.

- Ändern Sie die Größe der Beschriftung in klein, indem Sie [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)aufrufen. Die kleine Beschriftung ist 7 Pixel hoch.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CMFCDesktopAlertWnd` verschiedene Methoden `CMFCDesktopAlertWnd` in der Klasse zum Konfigurieren eines Objekts verwendet werden. Das Beispiel zeigt, wie Sie einen Animationstyp festlegen, die Transparenz des Popupfensters festlegen, angeben, dass im Warnfenster eine kleine Beschriftung angezeigt wird, und die Zeit festlegen, die verstreicht, bevor das Warnungsfenster automatisch geschlossen wird. Im Beispiel wird auch veranschaulicht, wie das Desktopwarnungsfenster erstellt und initialisiert wird. Dieser Codeausschnitt ist Teil des [Desktop alert Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxDesktopAlertWnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Erstellen

Erstellt und initialisiert das Desktop-Warnfenster.

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>Parameter

*pWndOwner*<br/>
[in, out] Gibt den Besitzer des Warnungsfensters an. Dieser Besitzer erhält dann alle Benachrichtigungen für das Desktop-Warnfenster. Dieser Wert kann nicht NULL sein.

*uiDlgResID*<br/>
[in] Gibt die Ressourcen-ID des Warnungsfensters an.

*Hmenu*<br/>
[in] Gibt das Menü an, das angezeigt wird, wenn der Benutzer auf die Menüschaltfläche klickt. Wenn NULL, wird die Menüschaltfläche nicht angezeigt.

*ptPos*<br/>
[in] Gibt die Anfangsposition an, an der das Warnfenster mithilfe von Bildschirmkoordinaten angezeigt wird. Wenn dieser Parameter (-1, -1) lautet, wird das Warnfenster in der unteren rechten Ecke des Bildschirms angezeigt.

*pRTIDlgBar*<br/>
[in] Laufzeitklasseninformationen für eine benutzerdefinierte Dialogfeldklasse, die den Clientbereich des Warnungsfensters abdeckt.

*params*<br/>
[in] Gibt Parameter an, die zum Erstellen eines Warnungsfensters verwendet werden.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Warnungsfenster erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um ein Warnungsfenster zu erstellen. Der Clientbereich des Warnungsfensters enthält ein untergeordnetes Dialogfeld, in dem alle Steuerelemente gehostet werden, die dem Benutzer angezeigt werden.

Die erste Methodenüberladung erstellt ein Warnungsfenster, das ein untergeordnetes Dialogfeld enthält, das aus den Ressourcen der Anwendung geladen wird. Die erste Methodenüberladung kann auch Laufzeitklasseninformationen für eine benutzerdefinierte Dialogfeldklasse angeben.

Die zweite Methodenüberladung erstellt ein Warnungsfenster, das Standardsteuerelemente enthält. Sie können angeben, welche Steuerelemente angezeigt werden sollen, indem Sie die [CMFCDesktopAlertWndInfo-Klasse](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)ändern.

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed

Gibt die Animationsgeschwindigkeit zurück.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Rückgabewert

Die Animationsgeschwindigkeit des Warnungsfensters in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Die Animationsgeschwindigkeit beschreibt, wie schnell das Warnfenster geöffnet und geschlossen wird.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType

Gibt den Animationstyp zurück.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Rückgabewert

Einer der folgenden Animationstypen:

- NO_ANIMATION

- Entfalten

- Folie

- Verblassen

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime

Gibt das Zeitout für das automatische Schließen zurück.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeit in Millisekunden, nach der das Warnungsfenster automatisch geschlossen wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um zu bestimmen, wie viel Zeit verstreichen soll, bevor das Warnungsfenster automatisch geschlossen wird.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight

Gibt die Höhe der Beschriftung zurück.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe der Beschriftung in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann in einer abgeleiteten Klasse überschrieben werden. Die Standardimplementierung gibt entweder den Wert für die geringe Beschriftungshöhe (7 Pixel) zurück, wenn im `GetSystemMetrics(SM_CYSMCAPTION)`Popupfenster die kleine Beschriftung oder der von der Windows-API-Funktion erhaltene Wert angezeigt werden soll.

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos

Gibt die letzte Position des Desktop-Warnfensters auf dem Bildschirm zurück.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Punkt in Bildschirmkoordinaten.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt die letzte gültige Position des Warnungsfensters auf dem Bildschirm zurück.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency

Gibt die Transparenzebene zurück.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Transparenzstufe zwischen 0 und 255, einschließlich. Je größer der Wert, desto undurchsichtiger das Fenster.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die aktuelle Transparenzebene des Warnungsfensters abzurufen.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption

Bestimmt, ob das Desktop-Warnfenster über eine kleine Beschriftung oder eine Beschriftung in normaler Größe verfügt.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Popupfenster mit einer kleinen Beschriftung angezeigt wird; FALSE, wenn das Popupfenster mit einer Beschriftung in normaler Größe angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um zu bestimmen, ob das Popupfenster eine kleine Beschriftung oder eine Beschriftung in normaler Größe enthält. Standardmäßig ist die kleine Beschriftung 7 Pixel hoch. Sie können die Höhe der Beschriftung in normaler `GetSystemMetrics(SM_CYCAPTION)`Größe abrufen, indem Sie die Windows-API-Funktion aufrufen.

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parameter

[in] *CPoint-&*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton

Wird vom Framework aufgerufen, wenn der Benutzer auf eine Linkschaltfläche im Desktop-Warnungsmenü klickt.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parameter

*uiCmdID*<br/>
[in] Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Immer FALSE

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie benachrichtigt werden möchten, wenn ein Benutzer im Warnungsfenster auf den Link klickt.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

[in] *wParam*<br/>

[in] *lParam*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parameter

[in] *hwnd*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed

Legt die neue Animationsgeschwindigkeit fest.

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parameter

*nSpeed*<br/>
[in] Gibt die neue Animationsgeschwindigkeit in Millisekunden an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Animationsgeschwindigkeit für das Warnungsfenster festzulegen. Die Standardanimationsgeschwindigkeit beträgt 30 Millisekunden.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType

Legt den Animationstyp fest.

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parameter

*type*<br/>
[in] Gibt den Animationstyp an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Animationstyp festzulegen. Sie können einen der folgenden Werte angeben:

- NO_ANIMATION

- Entfalten

- Folie

- Verblassen

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime

Legt die Zeitfürst beim automatischen Schließen fest.

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parameter

*nZeit*<br/>
[in] Die Zeit in Millisekunden, die verstreicht, bevor das Warnungsfenster automatisch geschlossen wird.

### <a name="remarks"></a>Bemerkungen

Das Warnungsfenster wird automatisch nach der angegebenen Zeit geschlossen, wenn der Benutzer nicht mit dem Fenster interagiert.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption

Wechselt zwischen kleinen und regulären Beschriftungen.

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parameter

*bSmallCaption*<br/>
[in] TRUE, um anzugeben, dass im Warnungsfenster eine kleine Beschriftung angezeigt wird; Andernfalls false, um anzugeben, dass im Warnungsfenster eine Beschriftung in normaler Größe angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die kleine oder normale Beschriftung anzuzeigen. Standardmäßig ist die kleine Beschriftung 7 Pixel hoch. Sie können die Größe der regulären Beschriftung `GetSystemMetrics(SM_CYCAPTION)`abrufen, indem Sie die Windows-API-Funktion aufrufen.

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparenz

Legt die Transparenzebene des Popupfensters fest.

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parameter

*nTransparenz*<br/>
[in] Gibt die Transparenzebene an. Dieser Wert muss zwischen 0 und 255 liegen, einschließlich. Je größer der Wert, desto undurchsichtiger das Fenster.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die Transparenzebene des Popupfensters festzulegen.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo-Klasse](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog-Klasse](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)
