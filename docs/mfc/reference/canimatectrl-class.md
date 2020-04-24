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
ms.openlocfilehash: e570681c899d58e8659635d55da843c23d1e95ee
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752881"
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
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Erstellt ein `CAnimateCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimateCtrl::Schließen](#close)|Schließt den AVI-Clip.|
|[CAnimateCtrl::Erstellen](#create)|Erstellt ein Animationssteuerelement und fügt `CAnimateCtrl` es an ein Objekt an.|
|[CAnimateCtrl::CreateEx](#createex)|Erstellt ein Animationssteuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein `CAnimateCtrl` Objekt an.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Gibt an, ob ein Audio-Video Interleaved (AVI)-Clip wiedergegeben wird.|
|[CAnimateCtrl::Öffnen](#open)|Öffnet einen AVI-Clip aus einer Datei oder Ressource und zeigt den ersten Frame an.|
|[CAnimateCtrl::PLay](#play)|Spielt den AVI-Clip ohne Ton ab.|
|[CAnimateCtrl::Suchen](#seek)|Zeigt einen ausgewählten Einzelframe des AVI-Clips an.|
|[CAnimateCtrl::Stopp](#stop)|Beendet die Wiedergabe des AVI-Clips.|

## <a name="remarks"></a>Bemerkungen

Dieses Steuerelement (und `CAnimateCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95, Windows 98 und Windows NT Version 3.51 und höher ausgeführt werden.

Ein Animationssteuerelement ist ein rechteckiges Fenster, das einen Clip im AVI-Format (Audio Video Interleaved) anzeigt – das Standard-Windows-Video-/Audioformat. Ein AVI-Clip ist eine Reihe von Bitmap-Frames, wie ein Film.

Animationssteuerelemente können nur einfache AVI-Clips wiedergeben. Insbesondere müssen die Clips, die von einem Animationssteuerelement abgespielt werden sollen, die folgenden Anforderungen erfüllen:

- Es muss genau ein Videostream vorhanden sein, und er muss mindestens einen Frame haben.

- Es können höchstens zwei Streams in der Datei vorhanden sein (in der Regel ist der andere Stream, falls vorhanden, ein Audiostream, obwohl das Animationssteuerelement Audioinformationen ignoriert).

- Der Clip muss entweder unkomprimiert oder mit RLE8-Komprimierung komprimiert werden.

- Im Videostream sind keine Palettenänderungen zulässig.

Sie können den AVI-Clip Ihrer Anwendung als AVI-Ressource hinzufügen oder Ihrer Anwendung als separate AVI-Datei beiliegen.

Da der Thread weiterhin ausgeführt wird, während der AVI-Clip angezeigt wird, wird eine häufige Verwendung für ein Animationssteuerelement darin bestehen, die Systemaktivität während eines längeren Vorgangs anzugeben. Im Dialogfeld Suchen des Datei-Explorers wird beispielsweise eine bewegliche Lupe angezeigt, während das System nach einer Datei sucht.

Wenn Sie `CAnimateCtrl` ein Objekt in einem Dialogfeld oder aus einer Dialogfeldressource mithilfe des Dialogfeld-Editors erstellen, wird es automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CAnimateCtrl` ein Objekt in einem Fenster erstellen, müssen Sie es möglicherweise zerstören. Wenn Sie `CAnimateCtrl` das Objekt auf dem Stapel erstellen, wird es automatisch zerstört. Wenn Sie `CAnimateCtrl` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen, um es zu zerstören. Wenn Sie eine neue `CAnimateCtrl` Klasse ableiten und einen Speicher `CAnimateCtrl` in dieser Klasse zuweisen, überschreiben Sie den Destruktor, um die Zuordnungen zu entsorgen.

Weitere Informationen zur `CAnimateCtrl`Verwendung von finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl

Erstellt ein `CAnimateCtrl`-Objekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen die Memberfunktion [Erstellen](#create) aufrufen, bevor Sie andere Vorgänge für das von Ihnen erstellte Objekt ausführen können.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Schließen

Schließt den AVI-Clip, der zuvor im Animationssteuerelement geöffnet wurde (falls vorhanden), und entfernt ihn aus dem Speicher.

```
BOOL Close();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Erstellen

Erstellt ein Animationssteuerelement und fügt `CAnimateCtrl` es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Animationssteuerelements an. Wenden Sie eine beliebige Kombination der Fensterstile an, die im Abschnitt "Hinweise" unten beschrieben sind, und der Animationssteuerungsstile, die unter [Animationssteuerungsstile](/windows/win32/Controls/animation-control-styles) im Windows SDK beschrieben werden.

*Rect*<br/>
Gibt die Position und Größe des Animationssteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Animationssteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Animationssteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CAnimateCtrl` eine in zwei Schritten. Rufen Sie zunächst den Konstruktor `Create`auf, und rufen Sie dann `CAnimateCtrl` auf, das das Animationssteuerelement erstellt und an das Objekt anfügt.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Animationssteuerelement an.

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

Wenn Sie erweiterte Fensterstile mit ihrem Animationssteuerelement verwenden `Create`möchten, rufen Sie [CreateEx](#createex) anstelle von auf.

Zusätzlich zu den oben aufgeführten Fensterstilen können Sie einen oder mehrere der Animationssteuerelementstile auf ein Animationssteuerelement anwenden. Weitere Informationen [zu Animationssteuerungsstilen](/windows/win32/Controls/animation-control-styles)finden Sie im Windows SDK .

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CAnimateCtrl` Objekt zu.

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
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Animationssteuerelements an. Wenden Sie eine beliebige Kombination der Fenster- und Animationssteuerungsstile an, die unter [Animationssteuerungsstile](/windows/win32/Controls/animation-control-styles) im Windows SDK beschrieben sind.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::IsPlaying

Gibt an, ob ein Audio-Video Interleaved (AVI)-Clip wiedergegeben wird.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein AVI-Clip abgespielt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) Nachricht, die im Windows SDK beschrieben wird.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Öffnen

Rufen Sie diese Funktion auf, um einen AVI-Clip zu öffnen und den ersten Frame anzuzeigen.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Ein `CString` Objekt oder ein Zeiger auf eine null-terminierte Zeichenfolge, die entweder den Namen der AVI-Datei oder den Namen einer AVI-Ressource enthält. Wenn dieser Parameter NULL ist, schließt das System den AVI-Clip, der zuvor für das Animationssteuerelement geöffnet wurde.

*nID*<br/>
Der AVI-Ressourcenbezeichner. Wenn dieser Parameter NULL ist, schließt das System den AVI-Clip, der zuvor für das Animationssteuerelement geöffnet wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die AVI-Ressource wird aus dem Modul geladen, das das Animationssteuerelement erstellt hat.

`Open`unterstützt keinen Ton in einem AVI-Clip; Sie können nur stille AVI-Clips öffnen.

Wenn das Animationssteuerelement `ACS_AUTOPLAY` über den Stil verfügt, beginnt das Animationssteuerelement automatisch die Wiedergabe des Clips unmittelbar nach dem Öffnen. Der Clip wird weiterhin im Hintergrund wiedergegeben, während der Thread weiter ausgeführt wird. Wenn der Clip abgespielt ist, wird er automatisch wiederholt.

Wenn das Animationssteuerelement `ACS_CENTER` den Stil hat, wird der AVI-Clip im Steuerelement zentriert, und die Größe des Steuerelements ändert sich nicht. Wenn das Animationssteuerelement nicht `ACS_CENTER` über den Stil verfügt, wird die Größe des Steuerelements geändert, wenn der AVI-Clip auf die Größe der Bilder im AVI-Clip geöffnet wird. Die Position der oberen linken Ecke des Steuerelements ändert sich nicht, sondern nur die Größe des Steuerelements.

Wenn das Animationssteuerelement `ACS_TRANSPARENT` den Stil hat, wird der erste Frame mit einem transparenten Hintergrund und nicht mit der im Animationsclip angegebenen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::PLay

Rufen Sie diese Funktion auf, um einen AVI-Clip in einem Animationssteuerelement abzuspielen.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parameter

*nVon*<br/>
Nullbasierter Index des Frames, in dem das Spielen beginnt. Der Wert muss kleiner als 65.536 sein. Der Wert 0 beginnt mit dem ersten Frame im AVI-Clip.

*Nto*<br/>
Nullbasierter Index des Frames, in dem die Wiedergabe endet. Der Wert muss kleiner als 65.536 sein. Ein Wert von - 1 bedeutet Ende mit dem letzten Frame im AVI-Clip.

*nRep*<br/>
Anzahl der Wiederholungen des AVI-Clips. Ein Wert von - 1 bedeutet, die Datei auf unbestimmte Zeit wiederzugeben.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Animationssteuerelement spielt den Clip im Hintergrund ab, während der Thread weiter ausgeführt wird. Wenn das Animationssteuerelement einen Stil hat, `ACS_TRANSPARENT` wird der AVI-Clip mit einem transparenten Hintergrund und nicht mit der im Animationsclip angegebenen Hintergrundfarbe wiedergegeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Suchen

Rufen Sie diese Funktion auf, um einen einzelnen Frame Ihres AVI-Clips statisch anzuzeigen.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parameter

*Nto*<br/>
Nullbasierter Index des anzuzeigenden Rahmens. Der Wert muss kleiner als 65.536 sein. Der Wert 0 bedeutet, dass der erste Frame im AVI-Clip angezeigt wird. Ein Wert von -1 bedeutet, dass der letzte Frame im AVI-Clip angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Animationssteuerelement einen Stil hat, `ACS_TRANSPARENT` wird der AVI-Clip mit einem transparenten Hintergrund und nicht mit der im Animationsclip angegebenen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Stopp

Rufen Sie diese Funktion auf, um die Wiedergabe eines AVI-Clips in einem Animationssteuerelement zu beenden.

```
BOOL Stop();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Erstellen](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
