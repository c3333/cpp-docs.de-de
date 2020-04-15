---
title: CPagerCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: b2c4f1ac99735953f4832226b840ced4ea4c509a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376975"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl-Klasse

Die Klasse `CPagerCtrl` kapselt das Windows-Pagersteuerelement, in dem der Benutzer einen Bildlauf durchführen kann, um ein Fenster innerhalb eines anderen Fensters in den sichtbaren Bereich zu verschieben, sofern es größer ist als das umgebende Fenster.

## <a name="syntax"></a>Syntax

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Erstellt ein `CPagerCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPagerCtrl::Erstellen](#create)|Erstellt ein Pagersteuerelement mit angegebenen Formatvorlagen `CPagerCtrl` und fügt es an das aktuelle Objekt an.|
|[CPagerCtrl::CreateEx](#createex)|Erstellt ein Pagersteuerelement mit angegebenen erweiterten Stilen `CPagerCtrl` und fügt es an das aktuelle Objekt an.|
|[CPagerCtrl::VorwärtsMaus](#forwardmouse)|Aktiviert oder deaktiviert die Weiterleitung [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) Nachrichten an das Fenster, das im aktuellen Pagersteuerelement enthalten ist.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Ruft die Hintergrundfarbe des aktuellen Pagersteuerelements ab.|
|[CPagerCtrl::GetBorder](#getborder)|Ruft die Rahmengröße des aktuellen Pagersteuerelements ab.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Ruft die Schaltflächengröße des aktuellen Pager-Steuerelements ab.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Ruft den Status der angegebenen Schaltfläche im aktuellen Pager-Steuerelement ab.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Ruft die [IDropTarget-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-idroptarget) für das aktuelle Pager-Steuerelement ab.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Ruft die Bildlaufposition des aktuellen Pager-Steuerelements ab.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Gibt an, ob sich die angegebene `pressed` Schaltfläche des aktuellen Pager-Steuerelements im Status befindet.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Gibt an, ob sich die angegebene `grayed` Schaltfläche des aktuellen Pager-Steuerelements im Status befindet.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Gibt an, ob sich die angegebene `hot` Schaltfläche des aktuellen Pager-Steuerelements im Status befindet.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Gibt an, ob sich die angegebene `invisible` Schaltfläche des aktuellen Pager-Steuerelements im Status befindet.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Gibt an, ob sich die angegebene `normal` Schaltfläche des aktuellen Pager-Steuerelements im Status befindet.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Bewirkt, dass das aktuelle Pager-Steuerelement die Größe des enthaltenen Fensters neu berechnet.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe des aktuellen Pager-Steuerelements fest.|
|[CPagerCtrl::SetBorder](#setborder)|Legt die Rahmengröße des aktuellen Pagersteuerelements fest.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Legt die Schaltflächengröße des aktuellen Pager-Steuerelements fest.|
|[CPagerCtrl::SetChild](#setchild)|Legt das enthaltene Fenster für das aktuelle Pagersteuerelement fest.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Legt die Bildlaufposition des aktuellen Pager-Steuerelements fest.|

## <a name="remarks"></a>Bemerkungen

Ein Pager-Steuerelement ist ein Fenster, das ein anderes Fenster enthält, das linear und größer als das enthaltende Fenster ist, und ermöglicht es Ihnen, das enthaltene Fenster in die Ansicht zu scrollen. Das Pager-Steuerelement zeigt zwei Bildlaufschaltflächen an, die automatisch verschwinden, wenn das enthaltene Fenster bis zu seiner weitesten Ausdehnung gescrollt wird, und andernfalls wieder angezeigt werden. Sie können ein Pager-Steuerelement erstellen, das entweder horizontal oder vertikal scrollt.

Wenn Ihre Anwendung beispielsweise über eine Symbolleiste verfügt, die nicht breit genug ist, um alle Elemente anzuzeigen, können Sie die Symbolleiste einem Pagersteuerelement zuweisen, und Benutzer können die Symbolleiste nach links oder rechts scrollen, um auf alle Elemente zuzugreifen. Microsoft Internet Explorer Version 4.0 (commctrl.dll Version 4.71) führt das Pager-Steuerelement ein.

Die `CPagerCtrl` Klasse wird von der [CWnd-Klasse](../../mfc/reference/cwnd-class.md) abgeleitet. Weitere Informationen und eine Illustration eines Pagersteuerelements finden Sie unter [Pager-Steuerelemente](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl

Erstellt ein `CPagerCtrl`-Objekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CPagerCtrl::Create-](#create) oder [CPagerCtrl::CreateEx-Methode,](#createex) um `CPagerCtrl` ein Pager-Steuerelement zu erstellen und es an das Objekt anzufügen.

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Erstellen

Erstellt ein Pagersteuerelement mit angegebenen Formatvorlagen `CPagerCtrl` und fügt es an das aktuelle Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwStyle*|[in] Eine bitweise Kombination (OR) von [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [Pager-Steuerelementstilen,](/windows/win32/Controls/pager-control-styles) die auf das Steuerelement angewendet werden sollen.|
|*Rect*|[in] Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Position und Größe des Steuerelements in Clientkoordinaten enthält.|
|*pParentWnd*|[in] Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Steuerelements ist. Dieser Parameter darf nicht NULL sein.|
|*nID*|[in] Die ID des Steuerelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Um ein Pager-Steuerelement `CPagerCtrl` zu erstellen, deklarieren Sie eine Variable, und rufen Sie dann die [CPagerCtrl::Create-](#create) oder [CPagerCtrl::CreateEx-Methode](#createex) für diese Variable auf.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pagersteuerelement erstellt und anschließend die [CPagerCtrl::SetChild-Methode](#setchild) verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächensteuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl::SetButtonSize-Methode](#setbuttonsize) verwendet, um die Höhe des Pagersteuerelements auf 20 Pixel festzulegen, und die [CPagerCtrl::SetBorder-Methode,](#setborder) um die Rahmenstärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx

Erstellt ein Pagersteuerelement mit angegebenen erweiterten Stilen `CPagerCtrl` und fügt es an das aktuelle Objekt an.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwExStyle*|[in] Eine bitweise Kombination erweiterter Stile, die auf das Steuerelement angewendet werden sollen. Weitere Informationen finden Sie im *dwExStyle-Parameter* der [CreateWindowEx-Funktion.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyle*|[in] Eine bitweise Kombination (OR) von [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [Pager-Steuerelementstilen,](/windows/win32/Controls/pager-control-styles) die auf das Steuerelement angewendet werden sollen.|
|*Rect*|[in] Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Position und Größe des Steuerelements in Clientkoordinaten enthält.|
|*pParentWnd*|[in] Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Steuerelements ist. Dieser Parameter darf nicht NULL sein.|
|*nID*|[in] Die ID des Steuerelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Um ein Pager-Steuerelement `CPagerCtrl` zu erstellen, deklarieren Sie eine Variable, und rufen Sie dann die [CPagerCtrl::Create-](#create) oder [CPagerCtrl::CreateEx-Methode](#createex) für diese Variable auf.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::VorwärtsMaus

Aktiviert oder deaktiviert die Weiterleitung [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) Nachrichten an das Fenster, das im aktuellen Pagersteuerelement enthalten ist.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*bForward*|[in] TRUE, um Mausnachrichten weiterzuleiten, oder FALSE, um Mausnachrichten nicht weiterzuleiten.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder

Ruft die Rahmengröße des aktuellen Pagersteuerelements ab.

```
int GetBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Rahmengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::GetBorder-Methode](#getborder) verwendet, um die Dicke des Rahmens des Pager-Steuerelements abzurufen.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor

Ruft die Hintergrundfarbe des aktuellen Pagersteuerelements ab.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die aktuelle Hintergrundfarbe des Pagersteuerelements enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::SetBkColor-Methode](#setbkcolor) verwendet, um die Hintergrundfarbe des Pager-Steuerelements auf Rot festzulegen, und die [CPagerCtrl::GetBkColor-Methode,](#getbkcolor) um zu bestätigen, dass die Änderung vorgenommen wurde.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize

Ruft die Schaltflächengröße des aktuellen Pager-Steuerelements ab.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Schaltflächengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) Nachricht, die im Windows SDK beschrieben wird.

Wenn das Pager-Steuerelement über den Stil PGS_HORZ verfügt, bestimmt die Schaltflächengröße die Breite der Pagerschaltflächen, und wenn das Pagersteuerelement den Stil PGS_VERT hat, bestimmt die Schaltflächengröße die Höhe der Pagerschaltflächen. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState

Ruft den Status der angegebenen Bildlaufschaltfläche im aktuellen Pager-Steuerelement ab.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

Der Status der Schaltfläche, die durch den *iButton-Parameter* angegeben wird. Der Staat ist entweder PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED oder PGF_HOT. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget

Ruft die [IDropTarget-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-idroptarget) für das aktuelle Pager-Steuerelement ab.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IDropTarget` die Schnittstelle für das aktuelle Pagersteuerelement.

### <a name="remarks"></a>Bemerkungen

`IDropTarget`ist eine der Schnittstellen, die Sie implementieren, um Drag-and-Drop-Vorgänge in Ihrer Anwendung zu unterstützen.

Diese Methode sendet die [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) Nachricht, die im Windows SDK beschrieben wird. Der Aufrufer dieser Methode ist `Release` für den Aufruf des Members der [IDropTarget-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-idroptarget) verantwortlich, wenn die Schnittstelle nicht mehr benötigt wird.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos

Ruft die Bildlaufposition des aktuellen Pager-Steuerelements ab.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Bildlaufposition, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::GetScrollPos-Methode](#getscrollpos) verwendet, um die aktuelle Bildlaufposition des Pagersteuerelements abzurufen. Wenn das Pager-Steuerelement noch nicht auf Null, die linke Position, gescrollt ist, verwendet das Beispiel die [CPagerCtrl::SetScrollPos-Methode,](#setscrollpos) um die Bildlaufposition auf Null festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed

Gibt an, ob sich die angegebene Bildlaufschaltfläche des aktuellen Pager-Steuerelements im gedrückten Zustand befindet.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Taste im gedrückten Zustand befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird. Anschließend wird überprüft, ob der zurückgegebene Status PGF_DEPRESSED ist. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed

Gibt an, ob sich die angegebene Bildlaufschaltfläche des aktuellen Pager-Steuerelements im grauer Zustand befindet.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im grauer Zustand befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird. Anschließend wird getestet, ob der zurückgegebene Status PGF_GRAYED ist. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot

Gibt an, ob sich die angegebene Bildlaufschaltfläche des aktuellen Pager-Steuerelements im Hot-Zustand befindet.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im Hot-Zustand befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird. Anschließend wird überprüft, ob der zurückgegebene Zustand PGF_HOT ist. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible

Gibt an, ob sich die angegebene Bildlaufschaltfläche des aktuellen Pager-Steuerelements im unsichtbaren Zustand befindet.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im unsichtbaren Zustand befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Windows macht die Bildlaufschaltfläche in einer bestimmten Richtung unsichtbar, wenn das enthaltene Fenster in die weiteste Ausdehnung gescrollt wird, da ein weiteres Klicken auf die Schaltfläche nicht mehr des enthaltenen Fensters in Senderichtung bringen kann.

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird. Anschließend wird überprüft, ob der zurückgegebene Status PGF_INVISIBLE ist. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::IsButtonInvisible-Methode](#isbuttoninvisible) verwendet, um zu bestimmen, ob die linken und rechten Bildlaufschaltflächen des Pagersteuerelements sichtbar sind.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal

Gibt an, ob sich die angegebene Bildlaufschaltfläche des aktuellen Pager-Steuerelements im Normalzustand befindet.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ibutton*|[in] Gibt die Schaltfläche an, für die der Status abgerufen wird. Wenn der Pager-Steuerelementstil PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche und PGB_BOTTOMORRIGHT für die rechte Schaltfläche an. Wenn der Pager-Steuerelementstil PGS_VERT ist, geben Sie PGB_TOPORLEFT für die obere Schaltfläche und PGB_BOTTOMORRIGHT für die untere Schaltfläche an. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im Normalzustand befindet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die im Windows SDK beschrieben wird. Anschließend wird überprüft, ob der zurückgegebene Status PGF_NORMAL ist. Weitere Informationen finden Sie im Abschnitt Rückgabewert der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht.

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize

Bewirkt, dass das aktuelle Pager-Steuerelement die Größe des enthaltenen Fensters neu berechnet.

```
void RecalcSize();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) Nachricht, die im Windows SDK beschrieben wird. Folglich sendet das Pager-Steuerelement die [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) Benachrichtigung, um die bildlisbaren Dimensionen des enthaltenen Fensters zu erhalten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::RecalcSize-Methode](#recalcsize) verwendet, um das aktuelle Pager-Steuerelement anzufordern, seine Größe neu zu berechnen.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird [die Nachrichtenreflektion](../../mfc/tn062-message-reflection-for-windows-controls.md) verwendet, damit das Pagersteuerelement seine eigene Größe neu berechnen kann, anstatt das übergeordnete Dialogfeld des Steuerelements zum Ausführen der Berechnung zu benötigen. Das Beispiel leitet `MyPagerCtrl` die Klasse von der [CPagerCtrl-Klasse](../../mfc/reference/cpagerctrl-class.md)ab und verwendet `OnCalcsize` dann eine Nachrichtenzuordnung, um die [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) Benachrichtigung dem Benachrichtigungshandler zuzuordnen. In diesem Beispiel legt der Benachrichtigungshandler die Breite und Höhe des Pagersteuerelements auf feste Werte fest.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor

Legt die Hintergrundfarbe des aktuellen Pager-Steuerelements fest.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*clrBk*|[in] Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die neue Hintergrundfarbe des Pagersteuerelements enthält.|

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die vorherige Hintergrundfarbe des Pagersteuerelements enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl::SetBkColor-Methode](#setbkcolor) verwendet, um die Hintergrundfarbe des Pager-Steuerelements auf Rot festzulegen, und die [CPagerCtrl::GetBkColor-Methode,](#getbkcolor) um zu bestätigen, dass die Änderung vorgenommen wurde.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder

Legt die Rahmengröße des aktuellen Pagersteuerelements fest.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iBorder*|[in] Die neue Rahmengröße, gemessen in Pixel. Wenn der *iBorder-Parameter* negativ ist, wird die Rahmengröße auf Null gesetzt.|

### <a name="return-value"></a>Rückgabewert

Die vorherige Rahmengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pagersteuerelement erstellt und anschließend die [CPagerCtrl::SetChild-Methode](#setchild) verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächensteuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl::SetButtonSize-Methode](#setbuttonsize) verwendet, um die Höhe des Pagersteuerelements auf 20 Pixel festzulegen, und die [CPagerCtrl::SetBorder-Methode,](#setborder) um die Rahmenstärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize

Legt die Schaltflächengröße des aktuellen Pager-Steuerelements fest.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iButtonSize*|[in] Die neue Schaltflächengröße, gemessen in Pixel.|

### <a name="return-value"></a>Rückgabewert

Die vorherige Schaltflächengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) Nachricht, die im Windows SDK beschrieben wird.

Wenn das Pager-Steuerelement über den Stil PGS_HORZ verfügt, bestimmt die Schaltflächengröße die Breite der Pagerschaltflächen, und wenn das Pagersteuerelement den Stil PGS_VERT hat, bestimmt die Schaltflächengröße die Höhe der Pagerschaltflächen. Die Standard-Schaltflächengröße beträgt drei Viertel der Breite der Bildlaufleiste, und die minimale Schaltflächengröße beträgt 12 Pixel. Weitere Informationen finden Sie unter [Pager-Steuerelementvorlagen](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pagersteuerelement erstellt und anschließend die [CPagerCtrl::SetChild-Methode](#setchild) verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächensteuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl::SetButtonSize-Methode](#setbuttonsize) verwendet, um die Höhe des Pagersteuerelements auf 20 Pixel festzulegen, und die [CPagerCtrl::SetBorder-Methode,](#setborder) um die Rahmenstärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild

Legt das enthaltene Fenster für das aktuelle Pagersteuerelement fest.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*hwndChild*|[in] Handle zum zu enthaltenden Fenster.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) Nachricht, die im Windows SDK beschrieben wird.

Diese Methode ändert das übergeordnete Element des enthaltenen Fensters nicht. Nur dem Pager-Steuerelement wird ein Fensterhandle zum Scrollen zugewiesen. In den meisten Fällen ist das enthaltene Fenster ein untergeordnetes Fenster des Pager-Steuerelements.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pagersteuerelement erstellt und anschließend die [CPagerCtrl::SetChild-Methode](#setchild) verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächensteuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl::SetButtonSize-Methode](#setbuttonsize) verwendet, um die Höhe des Pagersteuerelements auf 20 Pixel festzulegen, und die [CPagerCtrl::SetBorder-Methode,](#setborder) um die Rahmenstärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos

Legt die Bildlaufposition des aktuellen Pager-Steuerelements fest.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ipos*|[in] Die neue Bildlaufposition, gemessen in Pixel.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) Nachricht, die im Windows SDK beschrieben wird.

## <a name="see-also"></a>Siehe auch

[CPagerCtrl-Klasse](../../mfc/reference/cpagerctrl-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Pager-Steuerelemente](/windows/win32/Controls/pager-controls)
