---
title: CAnimateCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: 651b5775886374f3fcc95ab6b2cb3d892d9d77e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183382"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Animationssteuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimateCtrl:: CAnimateCtrl](#canimatectrl)|Erstellt ein `CAnimateCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimateCtrl:: Close](#close)|Schließt den AVI-Clip.|
|[CAnimateCtrl:: Create](#create)|Erstellt ein Animations Steuerelement und fügt es an ein- `CAnimateCtrl` Objekt an.|
|[CAnimateCtrl:: anforateex](#createex)|Erstellt ein Animations Steuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein- `CAnimateCtrl` Objekt an.|
|[CAnimateCtrl:: isplay](#isplaying)|Gibt an, ob ein Audiovideo Interleaved (AVI)-Clip abgespielt wird.|
|[CAnimateCtrl:: Open](#open)|Öffnet einen AVI-Clip aus einer Datei oder einer Ressource und zeigt den ersten Rahmen an.|
|[CAnimateCtrl::P Lay](#play)|Gibt den AVI-Clip ohne Sound wieder.|
|[CAnimateCtrl:: Seek](#seek)|Zeigt einen ausgewählten einzelnen Frame des AVI-Clips an.|
|[CAnimateCtrl:: Beendigung](#stop)|Beendet die Wiedergabe des AVI-Clips.|

## <a name="remarks"></a>Bemerkungen

Dieses Steuerelement (und damit auch die- `CAnimateCtrl` Klasse) ist nur für Programme verfügbar, die unter Windows 95, Windows 98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Ein Animations Steuerelement ist ein rechteckiges Fenster, das einen Clip im AVI-Format (Audio Video Interleaved) anzeigt – das standardmäßige Windows-Video-/Audio-Format. Ein AVI-Clip ist eine Reihe von bitmapframes, wie z. b. ein Film.

Animations Steuerelemente können nur einfache AVI-Clips abspielen. Insbesondere müssen die von einem Animations Steuerelement zu verwendenden Clips die folgenden Anforderungen erfüllen:

- Es muss genau ein Videostream vorhanden sein, und es muss mindestens ein Frame vorhanden sein.

- Es können höchstens zwei Streams in der Datei vorhanden sein (in der Regel ist der andere Stream, falls vorhanden, ein Audiostream, obwohl das Animations Steuerelement Audioinformationen ignoriert).

- Der Clip muss entweder unkomprimiert oder mit der RLE8-Komprimierung komprimiert werden.

- Im Videostream sind keine Palettenänderungen zulässig.

Sie können den AVI-Clip als AVI-Ressource zu Ihrer Anwendung hinzufügen, oder Sie können Ihre Anwendung als separate AVI-Datei begleiten.

Da der Thread weiterhin ausgeführt wird, während der AVI-Clip angezeigt wird, besteht eine häufige Verwendung eines Animations Steuer Elements darin, die Systemaktivität während eines langen Vorgangs anzuzeigen. Beispielsweise wird im Dialogfeld Suchen des Datei-Explorers ein beweglicher Vergrößerungsglas angezeigt, während das System nach einer Datei sucht.

Wenn Sie ein- `CAnimateCtrl` Objekt in einem Dialogfeld oder über eine Dialogfeld Ressource mithilfe des Dialog-Editors erstellen, wird es automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie ein- `CAnimateCtrl` Objekt in einem-Fenster erstellen, müssen Sie es möglicherweise zerstören. Wenn Sie das `CAnimateCtrl` Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie das- `CAnimateCtrl` Objekt auf dem Heap mithilfe der- **`new`** Funktion erstellen, müssen Sie für das-Objekt aufzurufen, **`delete`** um es zu zerstören. Wenn Sie eine neue Klasse von ableiten `CAnimateCtrl` und in dieser Klasse Arbeitsspeicher zuordnen, überschreiben Sie den `CAnimateCtrl` Dekonstruktor, um die Zuweisungen zu verwerfen.

Weitere Informationen zum Verwenden von finden Sie unter Steuer `CAnimateCtrl` [Elemente](../../mfc/controls-mfc.md) und [Verwenden von CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl:: CAnimateCtrl

Erstellt ein `CAnimateCtrl`-Objekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen die [Create](#create) Member-Funktion aufzurufen, bevor Sie andere Vorgänge für das von Ihnen erstellte Objekt ausführen können.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl:: Close

Schließt den AVI-Clip, der zuvor im Animations Steuerelement geöffnet war (sofern vorhanden), und entfernt ihn aus dem Arbeitsspeicher.

```
BOOL Close();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl:: Create

Erstellt ein Animations Steuerelement und fügt es an ein- `CAnimateCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil des Animations Steuer Elements an. Wenden Sie eine beliebige Kombination der Windows Windows SDK-Stile an [, die im](/windows/win32/Controls/animation-control-styles) Abschnitt "Hinweise" unten beschrieben werden

*Rect*<br/>
Gibt die Position und die Größe des Animations Steuer Elements an. Dabei kann es sich entweder um ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt oder um eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur handeln.

*pparser*<br/>
Gibt das übergeordnete Fenster des Animations Steuer Elements an, in der Regel ein `CDialog` . Er darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Animations Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen einen `CAnimateCtrl` in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen, und dann `Create` wird aufgerufen, wodurch das Animations Steuerelement erstellt und an das-Objekt angefügt wird `CAnimateCtrl` .

Wenden Sie die folgenden [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Animations Steuerelement an.

- Immer WS_CHILD

- WS_VISIBLE in der Regel

- WS_DISABLED selten

Wenn Sie erweiterte Windows-Stile mit dem Animations Steuerelement verwenden möchten, müssen Sie anstelle von den Befehl " [kreateex](#createex) " aufrufen `Create` .

Zusätzlich zu den oben aufgeführten Fenster Stilen empfiehlt es sich, einen oder mehrere der Animations Steuerelement Stile auf ein Animations Steuerelement anzuwenden. Weitere Informationen zu [Animations Steuerelement Stilen](/windows/win32/Controls/animation-control-styles)finden Sie in der Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl:: anforateex

Erstellt ein-Steuerelement (ein untergeordnetes Fenster) und ordnet es dem- `CAnimateCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt die erweiterte Art des zu erstellenden Steuer Elements an. Eine Liste erweiterter Windows-Stile finden Sie unter dem *dwExStyle* -Parameter für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

*dwstyle*<br/>
Gibt den Stil des Animations Steuer Elements an. Wenden Sie eine beliebige Kombination der Fenster-und Animations Steuerelement Stile an, die in den [Animations Steuerelement Stilen](/windows/win32/Controls/animation-control-styles) der Windows SDK beschrieben werden

*Rect*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Größe und Position des zu erstellenden Fensters in Client Koordinaten von *pparser*beschreibt.

*pparser*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Element des Steuer Elements ist.

*nID*<br/>
Die ID des untergeordneten Fensters des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Create](#create) , um erweiterte Windows-Stile anzuwenden, die durch den erweiterten Windows-Stil **WS_EX_** angegeben werden.

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl:: isplay

Gibt an, ob ein Audiovideo Interleaved (AVI)-Clip abgespielt wird.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein AVI-Clip wiedergegeben wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl:: Open

Mit dieser Funktion können Sie einen AVI-Clip öffnen und seinen ersten Frame anzeigen.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszfilename*<br/>
Ein- `CString` Objekt oder ein Zeiger auf eine NULL-terminierte Zeichenfolge, die entweder den Namen der AVI-Datei oder den Namen einer AVI-Ressource enthält. Wenn dieser Parameter NULL ist, schließt das System den AVI-Clip, der zuvor für das Animations Steuerelement geöffnet war, sofern vorhanden.

*nID*<br/>
Der AVI-Ressourcen Bezeichner. Wenn dieser Parameter NULL ist, schließt das System den AVI-Clip, der zuvor für das Animations Steuerelement geöffnet war, sofern vorhanden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die AVI-Ressource wird aus dem Modul geladen, das das Animations Steuerelement erstellt hat.

`Open`Sound in einem AVI-Clip wird von nicht unterstützt. Sie können nur unbeaufsichtigte AVI-Clips öffnen.

Wenn das Animations Steuerelement den `ACS_AUTOPLAY` Stil hat, beginnt das Animations Steuerelement automatisch mit der Wiedergabe des Clips, sobald es geöffnet wird. Der Clip wird weiterhin im Hintergrund abgespielt, während der Thread weiterhin ausgeführt wird. Wenn die Wiedergabe des Clips abgeschlossen ist, wird es automatisch wiederholt.

Wenn das Animations Steuerelement über den `ACS_CENTER` Stil verfügt, wird der AVI-Clip im Steuerelement zentriert, und die Größe des Steuer Elements wird nicht geändert. Wenn das Animations Steuerelement nicht über den `ACS_CENTER` Stil verfügt, wird die Größe des Steuer Elements geändert, wenn der AVI-Clip mit der Größe der Bilder im AVI-Clip geöffnet wird. Die Position der linken oberen Ecke des Steuer Elements ändert sich nicht, sondern nur die Größe des Steuer Elements.

Wenn das Animations Steuerelement über den `ACS_TRANSPARENT` Stil verfügt, wird der erste Frame mit einem transparenten Hintergrund und nicht mit der im Animations Clip angegebenen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::P Lay

Diese Funktion wird aufgerufen, um einen AVI-Clip in einem Animations Steuerelement wiederzugeben.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parameter

*nfrom*<br/>
NULL basierter Index des Frames, bei dem die Wiedergabe beginnt. Der Wert muss kleiner als 65.536 sein. Der Wert 0 bedeutet, dass mit dem ersten Frame im AVI-Clip begonnen werden soll.

*Joins nicht*<br/>
NULL basierter Index des Frames, in dem die Wiedergabe endet. Der Wert muss kleiner als 65.536 sein. Der Wert-1 bedeutet, dass er mit dem letzten Frame im AVI-Clip endet.

*Nrep*<br/>
Gibt an, wie oft der AVI-Clip wiedergegeben werden soll. Der Wert-1 bedeutet, dass die Datei unbegrenzt wiedergegeben wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Animations Steuerelement spielt den Clip im Hintergrund, während der Thread weiterhin ausgeführt wird. Wenn das Animations Steuerelement `ACS_TRANSPARENT` Style hat, wird der AVI-Clip mit einem transparenten Hintergrund und nicht mit der im Animations Clip angegebenen Hintergrundfarbe wiedergegeben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl:: Seek

Aufrufen Sie diese Funktion, um einen einzelnen Frame des AVI-Clips statisch anzuzeigen.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parameter

*Joins nicht*<br/>
Der null basierte Index des Frames, der angezeigt werden soll. Der Wert muss kleiner als 65.536 sein. Der Wert 0 bedeutet, dass der erste Frame im AVI-Clip angezeigt wird. Der Wert-1 bedeutet, dass der letzte Frame im AVI-Clip angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Animations Steuerelement `ACS_TRANSPARENT` Style hat, wird der AVI-Clip mit einem transparenten Hintergrund und nicht mit der im Animations Clip angegebenen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl:: Beendigung

Diese Funktion wird aufgerufen, um das Abspielen eines AVI-Clips in einem Animations Steuerelement zu beenden.

```
BOOL Stop();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl:: Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
