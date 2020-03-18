---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426006"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

Die Basisklasse für die Steuer leisten Klassen [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [krebar](../../mfc/reference/crebar-class.md)und [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntax

```
class CControlBar : public CWnd
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CControlBar:: CControlBar](#ccontrolbar)|Erstellt ein `CControlBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CControlBar:: calcdynamiclayout](#calcdynamiclayout)|Gibt die Größe einer dynamischen Steuerleiste als [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekt zurück.|
|[CControlBar:: calcfixedlayout](#calcfixedlayout)|Gibt die Größe der Steuerleiste als [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekt zurück.|
|[CControlBar:: CalcInsideRect](#calcinsiderect)|Gibt die aktuellen Maße des Steuerleistenbereichs, einschließlich der Rahmen, zurück.|
|[CControlBar::D opaint](#dopaint)|Rendert die Rahmen und das Ziehelement der Steuerleiste.|
|[CControlBar::D rawrahmens](#drawborders)|Rendert die Rahmen der Steuerleiste.|
|[CControlBar::D rawgripper](#drawgripper)|Rendert das Ziehelement der Steuerleiste.|
|[CControlBar:: EnableDocking](#enabledocking)|Ermöglicht das Andocken bzw. eine unverankerte Steuerleiste.|
|[CControlBar:: getbarstyle](#getbarstyle)|Ruft die Formatvorlagen der Steuerleiste ab.|
|[CControlBar:: getrahmens](#getborders)|Ruft die Rahmenwerte der Steuerleiste ab.|
|[CControlBar:: GetCount](#getcount)|Gibt die Anzahl der nicht-HWND-Elemente in der Steuerleiste zurück.|
|[CControlBar:: getdockingframe](#getdockingframe)|Gibt einen Zeiger auf den Frame zurück, an den eine Steuerleiste angedockt ist.|
|[CControlBar:: IsFloating](#isfloating)|Gibt einen Wert ungleich 0 (null) zurück, wenn die fragliche Steuerleiste unverankert ist.|
|[CControlBar:: OnUpdateCmdUI](#onupdatecmdui)|Ruft die Befehlshandler der Benutzeroberfläche ab.|
|[CControlBar:: setbarstyle](#setbarstyle)|Ändert die Formatvorlagen der Steuerleiste.|
|[CControlBar:: SetBorders](#setborders)|Legt die Rahmenwerte der Steuerleiste fest.|
|[CControlBar:: "*"](#setinplaceowner)|Ändert den direkten Besitzer einer Steuerleiste.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CControlBar:: m_bAutoDelete](#m_bautodelete)|Wenn der Wert ungleich 0 (null) ist, wird das `CControlBar`-Objekt gelöscht, sobald die Windows-Steuerleiste zerstört wird.|
|[CControlBar:: m_pInPlaceOwner](#m_pinplaceowner)|Der direkte Besitzer der Steuerleiste.|

## <a name="remarks"></a>Hinweise

Eine Steuerleiste ist ein Fenster, das normalerweise am linken oder rechten Rand eines Rahmenfensters ausgerichtet wird. Sie kann untergeordnete Elemente enthalten, die entweder HWND-basierte Steuerelemente sind, bei denen es sich um Fenster handelt, die Windows-Meldungen generieren und auf diese reagieren, oder nicht-HWND-basierte Elemente, die nicht Windows sind und durch Anwendungscode oder Frameworkcode verwaltet werden. Listenfelder und Bearbeitungs Steuerelemente sind Beispiele für HWND-basierte Steuerelemente. Status leisten-Bereiche und Bitmapschaltflächen sind Beispiele für nicht-HWND-basierte Steuerelemente.

Bei Steuerleistenfenstern handelt es sich normalerweise um untergeordnete Fenster eines übergeordneten Rahmenfensters, und es sind normalerweise nebengeordnete Elemente der Clientansicht oder des MDI-Clients des Rahmenfensters. Ein `CControlBar`-Objekt verwendet zum eigenen Positionieren Informationen über das Clientrechteck des übergeordneten Fensters. Dem übergeordneten Fenster wird dann die Menge des Speicherplatzes im Clientbereich des übergeordneten Fensters mitgeteilt, die unzugeordnet bleibt.

Weitere Informationen zu `CControlBar` finden Sie unter:

- [Steuerleisten](../../mfc/control-bars.md)

- [Technischer Hinweis 31: Steuer leisten](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Voraussetzungen

**Header:** Afxext. h

##  <a name="calcdynamiclayout"></a>CControlBar:: calcdynamiclayout

Das Framework ruft diese Member-Funktion auf, um die Dimensionen einer dynamischen Symbolleiste zu berechnen.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parameter

*nlength*<br/>
Die angeforderte Dimension der Steuerleiste (horizontal oder vertikal), abhängig von *dwmode*.

*nmode*<br/>
Die folgenden vordefinierten Flags werden verwendet, um die Höhe und Breite der dynamischen Steuerleiste zu bestimmen. Verwenden Sie den bitweisen or (&#124;)-Operator, um die Flags zu kombinieren.

|Layoutmodusflags|Bedeutung|
|-----------------------|-------------------|
|LM_STRETCH|Gibt an, ob die Steuerleiste auf die Größe des Frames gestreckt werden soll. Legen Sie fest, wenn die Leiste keine andockbare Leiste ist (zum Andocken nicht verfügbar). Wird nicht festgelegt, wenn die Leiste angedockt oder unverankert (zum Andocken verfügbar) ist. Wenn festgelegt, ignoriert LM_STRETCH *nlength* und gibt Dimensionen auf der Grundlage des LM_HORZ Zustands zurück. LM_STRETCH funktioniert ähnlich wie der *bstretch* -Parameter, der in " [calcfixedlayout](#calcfixedlayout)" verwendet wird. Weitere Informationen über die Beziehung zwischen Streckung und Ausrichtung finden Sie unter dieser Member-Funktion.|
|LM_HORZ|Gibt an, dass die Leiste horizontal oder vertikal ausgerichtet ist. Legen Sie fest, wenn die Leiste horizontal ausgerichtet ist, und wenn Sie vertikal ausgerichtet ist, wird Sie nicht festgelegt. LM_HORZ funktioniert ähnlich wie der *bhorz* -Parameter, der in " [calcfixedlayout](#calcfixedlayout)" verwendet wird. Weitere Informationen über die Beziehung zwischen Streckung und Ausrichtung finden Sie unter dieser Member-Funktion.|
|LM_MRUWIDTH|Zuletzt verwendete dynamische Breite. Ignoriert den *nlength* -Parameter und verwendet die zuletzt verwendete Breite, die gespeichert wurde.|
|LM_HORZDOCK|Horizontale angedockte Dimensionen. Ignoriert den *nlength* -Parameter und gibt die dynamische Größe mit der größten Breite zurück.|
|LM_VERTDOCK|Vertikale angedockte Dimensionen. Ignoriert den *nlength* -Parameter und gibt die dynamische Größe mit der größten Höhe zurück.|
|LM_LENGTHY|Legen Sie fest, wenn " *nlength* " eine Höhe (Y-Richtung) anstelle der Breite angibt.|
|LM_COMMIT|Setzt LM_MRUWIDTH auf die aktuelle Breite der gleitenden Steuerleiste zurück.|

### <a name="return-value"></a>Rückgabewert

Die Größe der Steuerleiste eines [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekts in Pixel.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Member-Funktion, um ein eigenes dynamisches Layout in Klassen bereitzustellen, die Sie von `CControlBar`ableiten. Von `CControlBar`abgeleitete MFC-Klassen, z. b. [CToolBar](../../mfc/reference/ctoolbar-class.md), überschreiben diese Element Funktion und stellen ihre eigene Implementierung bereit.

##  <a name="calcfixedlayout"></a>CControlBar:: calcfixedlayout

Mit dieser Member-Funktion können Sie die horizontale Größe einer Steuerleiste berechnen.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*bstretch*<br/>
Gibt an, ob die Leiste auf die Größe des Frames gestreckt werden soll. Der *bstretch* -Parameter ist ungleich 0 (null), wenn der Balken keine Docking Leiste ist (nicht zum Andocken verfügbar) und 0 ist, wenn er angedockt oder unverankert (zum Andocken verfügbar) ist.

*bhorz*<br/>
Gibt an, dass die Leiste horizontal oder vertikal ausgerichtet ist. Der *bhorz* -Parameter ist ungleich 0 (null), wenn der Balken horizontal ausgerichtet ist, und ist 0, wenn er vertikal ausgerichtet ist.

### <a name="return-value"></a>Rückgabewert

Die Größe der Steuerleiste eines `CSize` Objekts in Pixel.

### <a name="remarks"></a>Hinweise

Steuer leisten (z. b. Symbolleisten) können horizontal oder vertikal gestreckt werden, um die Schaltflächen in der Steuerleiste anzuzeigen.

Wenn *bstretch* den Wert true hat, wird die Dimension entlang der von *bhorz*bereitgestellten Ausrichtung gestreckt. Anders ausgedrückt: Wenn *bhorz* false ist, wird die Steuerleiste vertikal gestreckt. Wenn *bstretch* den Wert false hat, erfolgt keine Streckung. In der folgenden Tabelle werden die möglichen Permutationen und die resultierenden Steuer leisten Stile von *bstretch* und *bhorz*angezeigt.

|bstretch|bHorz|Dehnung|Ausrichtung|Andock/nicht Andocken|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Horizontale Streckung|Horizontal ausgerichtet|Nicht Andocken|
|TRUE|FALSE|Vertikale Streckung|Vertikal orientiert|Nicht Andocken|
|FALSE|TRUE|Keine Streckung verfügbar|Horizontal ausgerichtet|Docking|
|FALSE|FALSE|Keine Streckung verfügbar|Vertikal orientiert|Docking|

##  <a name="calcinsiderect"></a>CControlBar:: CalcInsideRect

Das Framework ruft diese Funktion auf, um den Client Bereich der Steuerleiste zu berechnen.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält die aktuellen Dimensionen der Steuerleiste. einschließlich der Rahmen.

*bhorz*<br/>
Gibt an, dass die Leiste horizontal oder vertikal ausgerichtet ist. Der *bhorz* -Parameter ist ungleich 0 (null), wenn der Balken horizontal ausgerichtet ist, und ist 0, wenn er vertikal ausgerichtet ist.

### <a name="remarks"></a>Hinweise

Diese Funktion wird aufgerufen, bevor die Steuerleiste gezeichnet wird.

Überschreiben Sie diese Funktion, um das Rendering der Rahmen-und Zieh Punkt Leiste der Steuerleiste anzupassen.

##  <a name="ccontrolbar"></a>CControlBar:: CControlBar

Erstellt ein `CControlBar`-Objekt.

```
CControlBar();
```

##  <a name="dopaint"></a>CControlBar::D opaint

Wird von Framework aufgerufen, um die Rahmen-und Zieh Punkt Leiste der Steuerleiste zu Rendering.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern der Rahmen und des Zieh Punkts der Steuerleiste verwendet werden soll.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um das Zeichnungs Verhalten der Steuerleiste anzupassen.

Eine weitere Anpassungs Methode besteht darin, die Funktionen `DrawBorders` und `DrawGripper` zu überschreiben und benutzerdefinierten Zeichnungs Code für die Rahmen und den Zieh Punkt hinzuzufügen. Da diese Methoden von der Standard `DoPaint`-Methode aufgerufen werden, ist eine außer Kraft Setzung von `DoPaint` nicht erforderlich.

##  <a name="drawborders"></a>CControlBar::D rawrahmens

Wird von Framework aufgerufen, um die Ränder der Steuerleiste zu erzeugen.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Verweist auf den Gerätekontext, der zum Rendern der Rahmen der Steuerleiste verwendet werden soll.

*Rect*<br/>
Ein `CRect`-Objekt, das die Dimensionen der Steuerleiste enthält.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um die Darstellung der Rahmen der Steuerleiste anzupassen.

##  <a name="drawgripper"></a>CControlBar::D rawgripper

Wird von Framework aufgerufen, um den Zieh Punkt der Steuerleiste zu Rendering.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern des Steuer leisten-Zieh Punkts verwendet werden soll.

*Rect*<br/>
Ein `CRect`-Objekt, das die Abmessungen des Steuer leisten-Zieh Elements enthält.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um die Darstellung des Steuer leisten-Zieh Elements anzupassen.

##  <a name="enabledocking"></a>CControlBar:: EnableDocking

Mit dieser Funktion kann eine Steuerleiste angedockt werden.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parameter

*dwdockstyle*<br/>
Gibt an, ob die Steuerleiste Andocken und die Seiten des übergeordneten Fensters unterstützt, an die die Steuerleiste angedockt werden kann. Kann eine oder mehrere der folgenden sein:

- CBRS_ALIGN_TOP ermöglicht das Andocken am oberen Rand des Client Bereichs.

- CBRS_ALIGN_BOTTOM ermöglicht das Andocken am unteren Rand des Client Bereichs.

- CBRS_ALIGN_LEFT ermöglicht das Andocken auf der linken Seite des Client Bereichs.

- CBRS_ALIGN_RIGHT ermöglicht das Andocken auf der rechten Seite des Client Bereichs.

- CBRS_ALIGN_ANY ermöglicht das Andocken auf einer beliebigen Seite des Client Bereichs.

- CBRS_FLOAT_MULTI ermöglicht, dass mehrere Steuer leisten in einem einzelnen Mini Rahmen Fenster angezeigt werden.

Wenn 0 (d. h. keine Flags angibt), wird die Steuerleiste nicht andocken.

### <a name="remarks"></a>Hinweise

Die angegebenen Seiten müssen einer der Seiten entsprechen, die im Zielrahmen Fenster zum Andocken aktiviert sind, oder die Steuerleiste kann nicht an dieses Rahmen Fenster angedockt werden.

##  <a name="getbarstyle"></a>CControlBar:: getbarstyle

Mit dieser Funktion können Sie bestimmen, welche **CBRS_** -Einstellungen (Steuer leisten Stile) derzeit für die Steuerleiste festgelegt sind.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Rückgabewert

Die aktuellen **CBRS_** (Steuer leisten Stile) Einstellungen für die Steuerleiste. Eine komplette Liste der verfügbaren Stile finden Sie unter [CControlBar:: setbarstyle](#setbarstyle) .

### <a name="remarks"></a>Hinweise

Behandelt keine **WS_** Stile (Fenster Stil).

##  <a name="getborders"></a>CControlBar:: getrahmens

Gibt die aktuellen Rahmen Werte für die Steuerleiste zurück.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CRect`-Objekt, das die aktuelle Breite (in Pixel) jeder Seite des Steuer leisten Objekts enthält. Beispielsweise ist der Wert des *linken* Members des [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekts die Breite des linken Rahmens.

##  <a name="getcount"></a>CControlBar:: GetCount

Gibt die Anzahl der nicht-HWND-Elemente für das `CControlBar` Objekt zurück.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der nicht-HWND-Elemente für das `CControlBar` Objekt. Diese Funktion gibt 0 für ein [CDialogBar](../../mfc/reference/cdialogbar-class.md) -Objekt zurück.

### <a name="remarks"></a>Hinweise

Der Typ des Elements hängt vom abgeleiteten Objekt ab: Bereiche für [CStatusBar](../../mfc/reference/cstatusbar-class.md) -Objekte und Schaltflächen und Trennzeichen für [CToolBar](../../mfc/reference/ctoolbar-class.md) -Objekte.

##  <a name="getdockingframe"></a>CControlBar:: getdockingframe

Rufen Sie diese Member-Funktion auf, um einen Zeiger auf das aktuelle Rahmen Fenster zu erhalten, an das die Steuerleiste angedockt ist.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Rahmen Fenster, wenn erfolgreich. andernfalls NULL.

Wenn die Steuerleiste nicht an ein Rahmen Fenster angedockt ist (d. h., wenn die Steuerleiste unverankert ist), gibt diese Funktion einen Zeiger auf das übergeordnete [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)zurück.

### <a name="remarks"></a>Hinweise

Weitere Informationen zu andockbaren Steuer leisten finden Sie unter [CControlBar:: EnableDocking](#enabledocking) und [CFrameWnd::D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>CControlBar:: IsFloating

Mit dieser Member-Funktion können Sie feststellen, ob die Steuerleiste unverankert oder angedockt ist.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Steuerleiste nicht verankert ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Um den Zustand einer Steuerleiste von angedockt in Floating zu ändern, nennen Sie [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>CControlBar:: m_bAutoDelete

Wenn der Wert ungleich 0 (null) ist, wird das `CControlBar`-Objekt gelöscht, sobald die Windows-Steuerleiste zerstört wird.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Hinweise

*m_bAutoDelete* ist eine öffentliche Variable des Typs bool.

Ein Steuer leisten Objekt ist in der Regel in ein Rahmen Fenster Objekt eingebettet. In diesem Fall ist *m_bAutoDelete* 0, da das eingebettete Steuer leisten Objekt zerstört wird, wenn das Rahmen Fenster zerstört wird.

Legen Sie diese Variable auf einen Wert ungleich 0 (null) fest, wenn Sie ein `CControlBar` Objekt auf dem Heap zuordnen, und Sie nicht beabsichtigen, **Delete**aufzurufen.

##  <a name="m_pinplaceowner"></a>CControlBar:: m_pInPlaceOwner

Der direkte Besitzer der Steuerleiste.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>CControlBar:: OnUpdateCmdUI

Diese Member-Funktion wird vom Framework aufgerufen, um den Status der Symbolleiste oder der Statusleiste zu aktualisieren.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parameter

*pTARGET*<br/>
Verweist auf das Hauptrahmen Fenster der Anwendung. Dieser Zeiger wird zum Weiterleiten von Update Nachrichten verwendet.

*bdisableifnohndler*<br/>
Flag, das angibt, ob ein Steuerelement ohne Update Handler automatisch als deaktiviert angezeigt werden soll.

### <a name="remarks"></a>Hinweise

Um eine einzelne Schaltfläche oder einen einzelnen Bereich zu aktualisieren, verwenden Sie das ON_UPDATE_COMMAND_UI-Makro in der Meldungs Zuordnung, um einen Update Handler entsprechend festzulegen. Weitere Informationen zur Verwendung dieses Makros finden Sie unter [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) .

`OnUpdateCmdUI` wird vom Framework aufgerufen, wenn sich die Anwendung im Leerlauf befindet. Das zu Aktualisier Ende Rahmen Fenster muss ein untergeordnetes Fenster (zumindest indirekt) eines sichtbaren Rahmen Fensters sein. `OnUpdateCmdUI` ist eine erweiterte über schreibbare.

##  <a name="setbarstyle"></a>CControlBar:: setbarstyle

Mit dieser Funktion können Sie die gewünschten **CBRS_** Stile für die Steuerleiste festlegen.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Die gewünschten Stile für die Steuerleiste. Kann eine oder mehrere der folgenden sein:

- CBRS_ALIGN_TOP ermöglicht, dass die Steuerleiste am oberen Rand des Client Bereichs eines Rahmen Fensters angedockt wird.

- CBRS_ALIGN_BOTTOM ermöglicht, dass die Steuerleiste am unteren Rand des Client Bereichs eines Rahmen Fensters angedockt wird.

- CBRS_ALIGN_LEFT ermöglicht, dass die Steuerleiste Links vom Client Bereich eines Rahmen Fensters angedockt wird.

- CBRS_ALIGN_RIGHT ermöglicht, dass die Steuerleiste an der rechten Seite des Client Bereichs eines Rahmen Fensters angedockt wird.

- CBRS_ALIGN_ANY ermöglicht es, dass die Steuerleiste an eine beliebige Seite des Client Bereichs eines Rahmen Fensters angedockt wird.

- CBRS_BORDER_TOP bewirkt, dass ein Rahmen am oberen Rand der Steuerleiste gezeichnet wird, wenn er sichtbar wäre.

- CBRS_BORDER_BOTTOM bewirkt, dass ein Rahmen am unteren Rand der Steuerleiste gezeichnet wird, wenn er sichtbar wäre.

- CBRS_BORDER_LEFT bewirkt, dass ein Rahmen am linken Rand der Steuerleiste gezeichnet wird, wenn er sichtbar wäre.

- CBRS_BORDER_RIGHT bewirkt, dass ein Rahmen am rechten Rand der Steuerleiste gezeichnet wird, wenn er sichtbar wäre.

- CBRS_FLOAT_MULTI ermöglicht, dass mehrere Steuer leisten in einem einzelnen Mini Rahmen Fenster angezeigt werden.

- CBRS_TOOLTIPS bewirkt, dass Quick Infos für die Steuerleiste angezeigt werden.

- CBRS_FLYBY bewirkt, dass der Nachrichtentext zur gleichen Zeit wie Quick Infos aktualisiert wird.

- CBRS_GRIPPER bewirkt, dass ein Zieh Punkt ähnlich dem, der auf Bändern in einem `CReBar`-Objekt verwendet wird, für jede `CControlBar`abgeleitete Klasse gezeichnet wird.

### <a name="remarks"></a>Hinweise

Hat keine Auswirkung auf die Einstellungen für **WS_** (Fenster Stil).

##  <a name="setborders"></a>CControlBar:: SetBorders

Diese Funktion wird aufgerufen, um die Größe der Rahmen der Steuerleiste festzulegen.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*cxleft*<br/>
Die Breite (in Pixel) des linken Rahmens der Steuerleiste.

*cytop*<br/>
Die Höhe des oberen Rahmens der Steuerleiste in Pixel.

*cxright*<br/>
Die Breite des rechten Rahmens der Steuerleiste (in Pixel).

*cybottom*<br/>
Die Höhe (in Pixel) des unteren Rahmens der Steuerleiste.

*lprect*<br/>
Ein Zeiger auf ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt, das die aktuelle Breite (in Pixel) der einzelnen Rahmen des Steuer leisten Objekts enthält.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden die oberen und unteren Ränder der Steuerleiste auf 5 Pixel und die linken und rechten Ränder auf 2 Pixel festgelegt:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>CControlBar:: "*"

Ändert den direkten Besitzer einer Steuerleiste.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf ein `CWnd` -Objekt.

### <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBar-Klasse](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar-Klasse](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar-Klasse](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar-Klasse](../../mfc/reference/crebar-class.md)
