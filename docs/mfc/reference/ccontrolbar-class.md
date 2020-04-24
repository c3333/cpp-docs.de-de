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
ms.openlocfilehash: c2f8ea48bf9a1f015928650085b07198b152771a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754796"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

Die Basisklasse für die Steuerleistenklassen [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)und [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntax

```
class CControlBar : public CWnd
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Erstellt ein `CControlBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Gibt die Größe einer dynamischen Steuerleiste als [CSize-Objekt](../../atl-mfc-shared/reference/csize-class.md) zurück.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Gibt die Größe der Steuerleiste als [CSize-Objekt](../../atl-mfc-shared/reference/csize-class.md) zurück.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Gibt die aktuellen Maße des Steuerleistenbereichs, einschließlich der Rahmen, zurück.|
|[CControlBar::DoPaint](#dopaint)|Rendert die Rahmen und das Ziehelement der Steuerleiste.|
|[CControlBar::DrawBorders](#drawborders)|Rendert die Rahmen der Steuerleiste.|
|[CControlBar::DrawGripper](#drawgripper)|Rendert das Ziehelement der Steuerleiste.|
|[CControlBar::EnableDocking](#enabledocking)|Ermöglicht das Andocken bzw. eine unverankerte Steuerleiste.|
|[CControlBar::GetBarStyle](#getbarstyle)|Ruft die Formatvorlagen der Steuerleiste ab.|
|[CControlBar::GetBorders](#getborders)|Ruft die Rahmenwerte der Steuerleiste ab.|
|[CControlBar::GetCount](#getcount)|Gibt die Anzahl der Nicht-HWND-Elemente in der Steuerleiste zurück.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Gibt einen Zeiger auf den Frame zurück, an den eine Steuerleiste angedockt ist.|
|[CControlBar::Isfloating](#isfloating)|Gibt einen Wert ungleich 0 (null) zurück, wenn die fragliche Steuerleiste unverankert ist.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Ruft die Befehlshandler der Benutzeroberfläche ab.|
|[CControlBar::SetBarStyle](#setbarstyle)|Ändert die Formatvorlagen der Steuerleiste.|
|[CControlBar::SetBorders](#setborders)|Legt die Rahmenwerte der Steuerleiste fest.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Ändert den direkten Besitzer einer Steuerleiste.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Wenn der Wert ungleich 0 (null) ist, wird das `CControlBar`-Objekt gelöscht, sobald die Windows-Steuerleiste zerstört wird.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Der direkte Besitzer der Steuerleiste.|

## <a name="remarks"></a>Bemerkungen

Eine Steuerleiste ist ein Fenster, das normalerweise am linken oder rechten Rand eines Rahmenfensters ausgerichtet wird. Es kann untergeordnete Elemente enthalten, die entweder HWND-basierte Steuerelemente sind, d. h. Fenster, die Windows-Nachrichten generieren und darauf reagieren, oder nicht HWND-basierte Elemente, die keine Fenster sind und von Anwendungscode oder Frameworkcode verwaltet werden. Listenfelder und Bearbeitungssteuerelemente sind Beispiele für HWND-basierte Steuerelemente. Statusleistenbereiche und Bitmap-Schaltflächen sind Beispiele für nicht HWND-basierte Steuerelemente.

Bei Steuerleistenfenstern handelt es sich normalerweise um untergeordnete Fenster eines übergeordneten Rahmenfensters, und es sind normalerweise nebengeordnete Elemente der Clientansicht oder des MDI-Clients des Rahmenfensters. Ein `CControlBar`-Objekt verwendet zum eigenen Positionieren Informationen über das Clientrechteck des übergeordneten Fensters. Dem übergeordneten Fenster wird dann die Menge des Speicherplatzes im Clientbereich des übergeordneten Fensters mitgeteilt, die unzugeordnet bleibt.

Weitere Informationen zu `CControlBar` finden Sie unter:

- [Steuerleisten](../../mfc/control-bars.md)

- [Technische Anmerkung 31: Steuerleisten](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout

Das Framework ruft diese Memberfunktion auf, um die Dimensionen einer dynamischen Symbolleiste zu berechnen.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parameter

*nLänge*<br/>
Die angeforderte Dimension der Steuerleiste, entweder horizontal oder vertikal, abhängig von *dwMode*.

*nMode*<br/>
Die folgenden vordefinierten Flags werden verwendet, um die Höhe und Breite der dynamischen Steuerleiste zu bestimmen. Verwenden Sie den Operator bitwise-OR (&#124;), um die Flags zu kombinieren.

|Layoutmodus-Flags|Bedeutung|
|-----------------------|-------------------|
|LM_STRETCH|Gibt an, ob die Steuerleiste auf die Größe des Rahmens gestreckt werden soll. Legen Sie fest, ob es sich bei der Leiste nicht um eine Dockingleiste handelt (nicht zum Andocken verfügbar). Nicht festgelegt, wenn die Leiste angedockt oder schwebend ist (verfügbar zum Andocken). Wenn diese Option festgelegt ist, ignoriert LM_STRETCH *nLength* und gibt Dimensionen basierend auf dem LM_HORZ Status zurück. LM_STRETCH funktioniert ähnlich wie der in [CalcFixedLayout](#calcfixedlayout)verwendete *bStretch-Parameter;* Weitere Informationen zur Beziehung zwischen Dehnung und Ausrichtung finden Sie in dieser Memberfunktion.|
|LM_HORZ|Gibt an, dass der Balken horizontal oder vertikal ausgerichtet ist. Legen Sie fest, ob der Balken horizontal ausgerichtet ist und wenn er vertikal ausgerichtet ist, wird er nicht festgelegt. LM_HORZ funktioniert ähnlich wie der in [CalcFixedLayout](#calcfixedlayout)verwendete *bHorz-Parameter;* Weitere Informationen zur Beziehung zwischen Dehnung und Ausrichtung finden Sie in dieser Memberfunktion.|
|LM_MRUWIDTH|Zuletzt verwendete dynamische Breite. Ignoriert den Parameter *nLength* und verwendet die zuletzt verwendete breite.|
|LM_HORZDOCK|Horizontale angedockte Bemaßungen. Ignoriert den *Parameter nLength* und gibt die dynamische Größe mit der größten Breite zurück.|
|LM_VERTDOCK|Vertikale angedockte Bemaßungen. Ignoriert *den Parameter nLength* und gibt die dynamische Größe mit der größten Höhe zurück.|
|LM_LENGTHY|Legen Sie fest, ob *nLength* die Höhe (Y-Richtung) anstelle der Breite angibt.|
|LM_COMMIT|Setzt LM_MRUWIDTH auf die aktuelle Breite der schwebenden Steuerleiste zurück.|

### <a name="return-value"></a>Rückgabewert

Die Größe der Steuerleiste (in [CSize](../../atl-mfc-shared/reference/csize-class.md) Pixel) eines CSize-Objekts.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Memberfunktion, um Ihr eigenes `CControlBar`dynamisches Layout in Klassen bereitzustellen, die Sie von ableiten. Von `CControlBar`, z. B. [CToolbar](../../mfc/reference/ctoolbar-class.md), abgeleitete MFC-Klassen überschreiben diese Memberfunktion und stellen ihre eigene Implementierung bereit.

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout

Rufen Sie diese Memberfunktion auf, um die horizontale Größe einer Steuerleiste zu berechnen.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

*bStretch*<br/>
Gibt an, ob die Leiste auf die Größe des Rahmens gestreckt werden soll. Der *parameter bStretch* ist ungleich Null, wenn die Leiste keine Dockingleiste ist (nicht zum Andocken verfügbar) und ist 0, wenn sie angedockt oder schwebend ist (verfügbar für das Andocken).

*bHorz*<br/>
Gibt an, dass der Balken horizontal oder vertikal ausgerichtet ist. Der *parameter bHorz* ist ungleich Null, wenn der Balken horizontal ausgerichtet ist, und ist 0, wenn er vertikal ausgerichtet ist.

### <a name="return-value"></a>Rückgabewert

Die Größe der Steuerleiste (in `CSize` Pixel) eines Objekts.

### <a name="remarks"></a>Bemerkungen

Steuerleisten wie Symbolleisten können horizontal oder vertikal gestreckt werden, um die in der Steuerleiste enthaltenen Schaltflächen aufzunehmen.

Wenn *bStretch* TRUE ist, dehnen Sie die Bemaßung entlang der von *bHorz*bereitgestellten Ausrichtung. Mit anderen Worten, wenn *bHorz* FALSE ist, wird die Steuerleiste vertikal gestreckt. Wenn *bStretch* FALSE ist, tritt keine Dehnung auf. Die folgende Tabelle zeigt die möglichen Permutationen und resultierenden Steuerleistenstile von *bStretch* und *bHorz*.

|bStretch|bHorz|Stretching|Ausrichtung|Andocken/Nicht Andocken|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Horizontale Dehnung|Horizontal ausgerichtet|Nicht andocken|
|TRUE|FALSE|Vertikale Dehnung|Vertikal ausgerichtet|Nicht andocken|
|FALSE|TRUE|Keine Dehnung verfügbar|Horizontal ausgerichtet|Andocken|
|FALSE|FALSE|Keine Dehnung verfügbar|Vertikal ausgerichtet|Andocken|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect

Das Framework ruft diese Funktion auf, um den Clientbereich der Steuerleiste zu berechnen.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält die aktuellen Dimensionen der Steuerleiste; einschließlich der Grenzen.

*bHorz*<br/>
Gibt an, dass der Balken horizontal oder vertikal ausgerichtet ist. Der *parameter bHorz* ist ungleich Null, wenn der Balken horizontal ausgerichtet ist, und ist 0, wenn er vertikal ausgerichtet ist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, bevor die Steuerleiste lackiert wird.

Überschreiben Sie diese Funktion, um das Rendern der Rahmen und der Greifstange der Kontrollleiste anzupassen.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::CControlBar

Erstellt ein `CControlBar`-Objekt.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint

Wird vom Framework aufgerufen, um die Rahmen und die Greifstange der Kontrollleiste zu rendern.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern der Rahmen und des Greifers der Steuerleiste verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um das Zeichnungsverhalten der Steuerleiste anzupassen.

Eine weitere Anpassungsmethode `DrawBorders` besteht `DrawGripper` darin, die und-Funktionen zu überschreiben und benutzerdefinierter Zeichnungscode für die Rahmen und den Greifer hinzuzufügen. Da diese Methoden von `DoPaint` der Standardmethode aufgerufen `DoPaint` werden, ist keine Außerkraftsetzung von erforderlich.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders

Wird vom Framework aufgerufen, um die Rahmen der Kontrollleiste zu rendern.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern der Ränder der Kontrollleiste verwendet werden soll.

*Rect*<br/>
Ein `CRect` Objekt, das die Abmessungen der Steuerleiste enthält.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Darstellung der Kontrollleistenrahmen anzupassen.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::DrawGripper

Wird vom Framework aufgerufen, um den Greifer der Steuerleiste zu rendern.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeigt auf den Gerätekontext, der zum Rendern des Steuerleistengreifers verwendet werden soll.

*Rect*<br/>
Ein `CRect` Objekt, das die Abmessungen des Steuerleistengreifers enthält.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um das Erscheinungsbild des Steuerleistengreifers anzupassen.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking

Rufen Sie diese Funktion auf, damit eine Steuerleiste angedockt werden kann.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parameter

*dwDockStyle*<br/>
Gibt an, ob die Steuerleiste das Andocken unterstützt und die Seiten des übergeordneten Fensters, an das die Steuerleiste angedockt werden kann, sofern unterstützt. Kann einer oder mehrere der folgenden sein:

- CBRS_ALIGN_TOP Ermöglicht das Andocken am oberen Rand des Clientbereichs.

- CBRS_ALIGN_BOTTOM Ermöglicht das Andocken am unteren Rand des Clientbereichs.

- CBRS_ALIGN_LEFT Ermöglicht das Andocken auf der linken Seite des Clientbereichs.

- CBRS_ALIGN_RIGHT Ermöglicht das Andocken auf der rechten Seite des Clientbereichs.

- CBRS_ALIGN_ANY Ermöglicht das Andocken auf jeder Seite des Clientbereichs.

- CBRS_FLOAT_MULTI Ermöglicht das Schweben mehrerer Steuerleisten in einem einzelnen Minirahmenfenster.

Wenn 0 (d. h. keine Flags) angegeben ist, dockt die Steuerleiste nicht an.

### <a name="remarks"></a>Bemerkungen

Die angegebenen Seiten müssen mit einer der Seiten übereinstimmen, die für das Andocken im Zielrahmenfenster aktiviert sind, oder die Steuerleiste kann nicht an dieses Rahmenfenster angedockt werden.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetBarStyle

Rufen Sie diese Funktion auf, um zu bestimmen, welche **CBRS_** (Steuerleistenstilen) Einstellungen derzeit für die Steuerleiste festgelegt sind.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Rückgabewert

Die aktuellen **einstellungen für die CBRS_** (Steuerleistenstile) für die Steuerleiste. Die vollständige Liste der verfügbaren Stile finden Sie unter [CControlBar::SetBarStyle.](#setbarstyle)

### <a name="remarks"></a>Bemerkungen

Behandelt **WS_** (Fensterstil)-Stile nicht.

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders

Gibt die aktuellen Rahmenwerte für die Kontrollleiste zurück.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CRect` Objekt, das die aktuelle Breite (in Pixel) jeder Seite des Steuerelementleistenobjekts enthält. Der Wert des *linken* Elements des [CRect-Objekts](../../atl-mfc-shared/reference/crect-class.md) ist beispielsweise die Breite des linken Rahmens.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount

Gibt die Anzahl der Nicht-HWND-Elemente für das `CControlBar` Objekt zurück.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Nicht-HWND-Elemente für das `CControlBar` Objekt. Diese Funktion gibt 0 für ein [CDialogBar-Objekt](../../mfc/reference/cdialogbar-class.md) zurück.

### <a name="remarks"></a>Bemerkungen

Der Typ des Elements hängt vom abgeleiteten Objekt ab: Bereiche für [CStatusBar-Objekte](../../mfc/reference/cstatusbar-class.md) und Schaltflächen und Trennzeichen für [CToolBar-Objekte.](../../mfc/reference/ctoolbar-class.md)

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf das aktuelle Rahmenfenster zu erhalten, an das die Steuerleiste angedockt ist.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Rahmenfenster, wenn erfolgreich; andernfalls NULL.

Wenn die Steuerleiste nicht an ein Rahmenfenster angedockt ist (d. h., wenn die Steuerleiste unverankert ist), gibt diese Funktion einen Zeiger auf das übergeordnete [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu dockbaren Steuerleisten finden Sie unter [CControlBar::EnableDocking](#enabledocking) und [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::Isfloating

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob die Steuerleiste unverankert oder angedockt ist.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Steuerleiste unverankert ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Um den Status einer Steuerleiste von docked zu floating zu ändern, rufen Sie [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)auf.

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar::m_bAutoDelete

Wenn der Wert ungleich 0 (null) ist, wird das `CControlBar`-Objekt gelöscht, sobald die Windows-Steuerleiste zerstört wird.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Bemerkungen

*m_bAutoDelete* ist eine öffentliche Variable vom Typ BOOL.

Ein Steuerelementleistenobjekt wird in der Regel in ein Frame-Window-Objekt eingebettet. In diesem Fall *ist m_bAutoDelete* 0, da das eingebettete Steuerelementleistenobjekt zerstört wird, wenn das Rahmenfenster zerstört wird.

Legen Sie diese Variable auf einen `CControlBar` Wert ungleich Null fest, wenn Sie ein Objekt auf dem Heap zuweisen und nicht beabsichtigen, **delete**aufzurufen.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner

Der direkte Besitzer der Steuerleiste.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI

Diese Memberfunktion wird vom Framework aufgerufen, um den Status der Symbolleiste oder Statusleiste zu aktualisieren.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parameter

*pTarget*<br/>
Zeigt auf das Hauptrahmenfenster der Anwendung. Dieser Zeiger wird zum Routing von Aktualisierungsmeldungen verwendet.

*bDisableIfNoHndler*<br/>
Flag, das angibt, ob ein Steuerelement ohne Aktualisierungshandler automatisch als deaktiviert angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Um eine einzelne Schaltfläche oder einen einzelnen Bereich zu aktualisieren, verwenden Sie das ON_UPDATE_COMMAND_UI-Makro in der Nachrichtenzuordnung, um einen Aktualisierungshandler entsprechend festzulegen. Weitere Informationen zur Verwendung dieses Makros finden Sie in [ON_UPDATE_COMMAND_UI.](message-map-macros-mfc.md#on_update_command_ui)

`OnUpdateCmdUI`wird vom Framework aufgerufen, wenn sich die Anwendung im Leerlauf befindet. Das zu aktualisierende Rahmenfenster muss ein untergeordnetes Fenster sein, zumindest indirekt, eines sichtbaren Rahmenfensters. `OnUpdateCmdUI`ist ein fortgeschrittener Überridable.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle

Rufen Sie diese Funktion auf, um die gewünschten **CBRS_** Stile für die Steuerleiste festzulegen.

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Die gewünschten Stile für die Steuerleiste. Kann einer oder mehrere der folgenden sein:

- CBRS_ALIGN_TOP Ermöglicht das Andocken der Steuerleiste an den oberen Rand des Clientbereichs eines Rahmenfensters.

- CBRS_ALIGN_BOTTOM Ermöglicht das Andocken der Steuerleiste an den unteren Rand des Clientbereichs eines Rahmenfensters.

- CBRS_ALIGN_LEFT Ermöglicht das Andocken der Steuerleiste an die linke Seite des Clientbereichs eines Rahmenfensters.

- CBRS_ALIGN_RIGHT Ermöglicht das Andocken der Steuerleiste an die rechte Seite des Clientbereichs eines Rahmenfensters.

- CBRS_ALIGN_ANY Ermöglicht das Andocken der Steuerleiste an eine beliebige Seite des Clientbereichs eines Rahmenfensters.

- CBRS_BORDER_TOP Bewirkt, dass ein Rahmen am oberen Rand der Kontrollleiste gezeichnet wird, wenn er sichtbar ist.

- CBRS_BORDER_BOTTOM Bewirkt, dass ein Rahmen am unteren Rand der Kontrollleiste gezeichnet wird, wenn er sichtbar ist.

- CBRS_BORDER_LEFT Bewirkt, dass ein Rahmen am linken Rand der Kontrollleiste gezeichnet wird, wenn er sichtbar ist.

- CBRS_BORDER_RIGHT Bewirkt, dass ein Rahmen am rechten Rand der Kontrollleiste gezeichnet wird, wenn er sichtbar ist.

- CBRS_FLOAT_MULTI Ermöglicht das Schweben mehrerer Steuerleisten in einem einzelnen Minirahmenfenster.

- CBRS_TOOLTIPS Bewirkt, dass Werkzeugtipps für die Steuerleiste angezeigt werden.

- CBRS_FLYBY Bewirkt, dass Nachrichtentext gleichzeitig mit DenTool-Tipps aktualisiert wird.

- CBRS_GRIPPER Bewirkt, dass ein Greifer, `CReBar` ähnlich dem, der `CControlBar`auf Bändern in einem Objekt verwendet wird, für eine beliebige -abgeleitete Klasse gezeichnet wird.

### <a name="remarks"></a>Bemerkungen

Wirkt sich nicht auf die **einstellungen für WS_** (Fensterstil) aus.

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders

Rufen Sie diese Funktion auf, um die Größe der Ränder der Kontrollleiste festzulegen.

```cpp
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*cxLeft*<br/>
Die Breite (in Pixel) des linken Rahmens der Steuerleiste.

*cyTop*<br/>
Die Höhe (in Pixel) des oberen Rahmens der Steuerleiste.

*cxRight*<br/>
Die Breite (in Pixel) des rechten Rahmens der Steuerleiste.

*cyBottom*<br/>
Die Höhe (in Pixel) des unteren Rahmens der Steuerleiste.

*lpRect*<br/>
Ein Zeiger auf ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die aktuelle Breite (in Pixel) jedes Rahmens des Steuerelementleistenobjekts enthält.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden der obere und untere Rand der Kontrollleiste auf 5 Pixel und der linke und rechte Rahmen auf 2 Pixel festgelegt:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner

Ändert den direkten Besitzer einer Steuerleiste.

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf ein `CWnd`-Objekt.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel STRGBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBar-Klasse](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar-Klasse](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar-Klasse](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar-Klasse](../../mfc/reference/crebar-class.md)
