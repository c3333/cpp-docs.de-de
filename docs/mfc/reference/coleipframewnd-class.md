---
title: COleIPFrameWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374958"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd-Klasse

Die Basis für der Fenster zur direkten Bearbeitung der Anwendung.

## <a name="syntax"></a>Syntax

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Erstellt ein `COleIPFrameWnd`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Wird vom Framework aufgerufen, wenn ein Element für die ortsspezifische Bearbeitung aktiviert ist.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Wird vom Framework aufgerufen, um das ortsnahe Bearbeitungsfenster neu zu positionieren.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse erstellt und positioniert Steuerleisten im Dokumentfenster der Containeranwendung. Es verarbeitet auch Benachrichtigungen, die von einem eingebetteten [COleResizeBar-Objekt](../../mfc/reference/coleresizebar-class.md) generiert werden, wenn der Benutzer die Größe des an Ort ändernden Bearbeitungsfensters ändert.

Weitere Informationen zur `COleIPFrameWnd`Verwendung finden Sie im Artikel [Aktivierung](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

Erstellt ein `COleIPFrameWnd` Objekt und initialisiert seine in-Place-Statusinformationen, die in einer Struktur vom Typ OLEINPLACEFRAMEINFO gespeichert sind.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) im Windows SDK.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars

Das Framework `OnCreateControlBars` ruft die Funktion auf, wenn ein Element für die ortsspezifische Bearbeitung aktiviert wird.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parameter

*pWndFrame*<br/>
Zeigen Sie mit dem Zeiger auf das Rahmenfenster der Containeranwendung.

*pWndDoc*<br/>
Zeigen Sie auf das Fenster auf Dokumentebene des Containers. Kann NULL sein, wenn es sich bei dem Container um eine SDI-Anwendung handelt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null auf Erfolg; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um eine spezielle Verarbeitung durchzuführen, die beim Erstellen von Steuerleisten erforderlich ist.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame

Das Framework `RepositionFrame` ruft die Memberfunktion auf, um Kontrollleisten zu legen und das an Ort und Stelle neu positionierte Bearbeitungsfenster neu zu positionieren, damit alles sichtbar ist.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parameter

*lpPosRect*<br/>
Zeigen Sie `RECT` mit dem `CRect` Zeiger auf eine Struktur oder ein Objekt, das die aktuellen Positionskoordinaten des ortsplatzierten Rahmenfensters in Pixel relativ zum Clientbereich enthält.

*lpClipRect*<br/>
Zeigen Sie `RECT` mit dem `CRect` Zeiger auf eine Struktur oder ein Objekt, das die aktuellen Clipping-Rechteck-Koordinaten des ortsplatzierten Rahmenfensters in Pixel relativ zum Clientbereich enthält.

### <a name="remarks"></a>Bemerkungen

Das Layout der Steuerleisten im Containerfenster unterscheidet sich von dem Layout eines Nicht-OLE-Rahmenfensters. Das Nicht-OLE-Rahmenfenster berechnet die Positionen von Steuerleisten und anderen Objekten aus einer bestimmten Frame-Fenstergröße, wie bei einem Aufruf von [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Der Clientbereich ist das, was nach dem Platz für Steuerleisten verbleibt und andere Objekte subtrahiert werden. Ein `COleIPFrameWnd` Fenster hingegen positioniert Symbolleisten entsprechend einem bestimmten Clientbereich. Mit anderen `CFrameWnd::RecalcLayout` Worten, Werke "von außen `COleIPFrameWnd::RepositionFrame` nach innen", während Werke "von innen nach außen".

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)
