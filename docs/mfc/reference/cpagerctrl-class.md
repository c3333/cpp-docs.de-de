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
ms.openlocfilehash: 9b3af31e7d352e93144cde0c321620693111e145
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561907"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl-Klasse

Die Klasse `CPagerCtrl` kapselt das Windows-Pagersteuerelement, in dem der Benutzer einen Bildlauf durchführen kann, um ein Fenster innerhalb eines anderen Fensters in den sichtbaren Bereich zu verschieben, sofern es größer ist als das umgebende Fenster.

## <a name="syntax"></a>Syntax

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CPagerCtrl:: CPagerCtrl](#cpagerctrl)|Erstellt ein `CPagerCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CPagerCtrl:: Create](#create)|Erstellt ein Pager-Steuerelement mit angegebenen Stilen und fügt es an das aktuelle- `CPagerCtrl` Objekt an.|
|[CPagerCtrl:: kreateex](#createex)|Erstellt ein Pager-Steuerelement mit den angegebenen erweiterten Stilen und fügt es an das aktuelle- `CPagerCtrl` Objekt an.|
|[CPagerCtrl:: forwardmouse](#forwardmouse)|Aktiviert oder deaktiviert die Weiterleitung [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) Meldungen an das Fenster, das im aktuellen Pager-Steuerelement enthalten ist.|
|[CPagerCtrl:: GetBkColor](#getbkcolor)|Ruft die Hintergrundfarbe des aktuellen Pager-Steuer Elements ab.|
|[CPagerCtrl:: GetBorder](#getborder)|Ruft die Rahmengröße des aktuellen Pager-Steuer Elements ab.|
|[CPagerCtrl:: getbuttonsize](#getbuttonsize)|Ruft die Schaltflächen Größe des aktuellen Pager-Steuer Elements ab.|
|[CPagerCtrl:: GetButtonState](#getbuttonstate)|Ruft den Zustand der angegebenen Schaltfläche im aktuellen Pager-Steuerelement ab.|
|[CPagerCtrl:: getdroptarget](#getdroptarget)|Ruft die [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) -Schnittstelle für das aktuelle Pager-Steuerelement ab.|
|[CPagerCtrl:: getscrollpos](#getscrollpos)|Ruft die Bild Lauf Position des aktuellen Pager-Steuer Elements ab.|
|[CPagerCtrl:: isbuttondepressiv](#isbuttondepressed)|Gibt an, ob sich die angegebene Schaltfläche des aktuellen Pager-Steuer Elements im `pressed` Zustand befindet.|
|[CPagerCtrl:: isbuttongraut](#isbuttongrayed)|Gibt an, ob sich die angegebene Schaltfläche des aktuellen Pager-Steuer Elements im `grayed` Zustand befindet.|
|[CPagerCtrl:: isbuttonhot](#isbuttonhot)|Gibt an, ob sich die angegebene Schaltfläche des aktuellen Pager-Steuer Elements im `hot` Zustand befindet.|
|[CPagerCtrl:: isbuttonunsichtbar](#isbuttoninvisible)|Gibt an, ob sich die angegebene Schaltfläche des aktuellen Pager-Steuer Elements im `invisible` Zustand befindet.|
|[CPagerCtrl:: isbuttonnormal](#isbuttonnormal)|Gibt an, ob sich die angegebene Schaltfläche des aktuellen Pager-Steuer Elements im `normal` Zustand befindet.|
|[CPagerCtrl:: recalcsize](#recalcsize)|Bewirkt, dass das aktuelle Pager-Steuerelement die Größe des enthaltenen Fensters neu berechnet.|
|[CPagerCtrl:: SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe des aktuellen Pager-Steuer Elements fest.|
|[CPagerCtrl:: setborder](#setborder)|Legt die Rahmengröße des aktuellen Pager-Steuer Elements fest.|
|[CPagerCtrl:: setbuttonsize](#setbuttonsize)|Legt die Schaltflächen Größe des aktuellen Pager-Steuer Elements fest.|
|[CPagerCtrl:: setchild](#setchild)|Legt das enthaltene Fenster für das aktuelle Pager-Steuerelement fest.|
|[CPagerCtrl:: setscrollpos](#setscrollpos)|Legt die Bild Lauf Position des aktuellen Pager-Steuer Elements fest.|

## <a name="remarks"></a>Bemerkungen

Ein Pager-Steuerelement ist ein Fenster, das ein anderes Fenster enthält, das linear und größer als das enthaltende Fenster ist, und es Ihnen ermöglicht, das enthaltene Fenster in die Ansicht zu scrollen. Das Pager-Steuerelement zeigt zwei Bild Lauf Schaltflächen an, die automatisch ausgeblendet werden, wenn das enthaltene Fenster in seinen äußersten Block gescrollt wird, und andernfalls erneut angezeigt wird. Sie können ein Pager-Steuerelement erstellen, das entweder horizontal oder vertikal einen Bildlauf ausführt.

Wenn die Anwendung beispielsweise über eine Symbolleiste verfügt, die nicht breit genug ist, um alle Elemente anzuzeigen, können Sie die Symbolleiste einem Pager-Steuerelement zuweisen, und Benutzer können einen Bildlauf in der Symbolleiste nach links oder rechts durchführen, um auf alle Elemente zuzugreifen. Microsoft Internet Explorer Version 4,0 (commctrl.dll Version 4,71) führt das Pager-Steuerelement ein.

Die- `CPagerCtrl` Klasse wird von der [CWnd](../../mfc/reference/cwnd-class.md) -Klasse abgeleitet. Weitere Informationen und eine Abbildung eines Pager-Steuer Elements finden Sie unter [Pager](/windows/win32/Controls/pager-controls)-Steuerelemente.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a> CPagerCtrl:: CPagerCtrl

Erstellt ein `CPagerCtrl`-Objekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CPagerCtrl:: Create](#create) -Methode oder die [CPagerCtrl::](#createex) up-Methode, um ein Pager-Steuerelement zu erstellen und es an das-Objekt anzufügen `CPagerCtrl` .

## <a name="cpagerctrlcreate"></a><a name="create"></a> CPagerCtrl:: Create

Erstellt ein Pager-Steuerelement mit angegebenen Stilen und fügt es an das aktuelle- `CPagerCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*\
in Eine bitweise Kombination (or) von [Fenster Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [Pager-Steuerelement Stilen](/windows/win32/Controls/pager-control-styles) , die auf das-Steuerelement angewendet werden sollen.

*Rect*\
in Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Position und die Größe des Steuer Elements in Client Koordinaten enthält.

*pparser*\
in Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das das übergeordnete Fenster des Steuer Elements ist. Dieser Parameter darf nicht NULL sein.

*NID*\
in Die ID des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Um ein Pager-Steuerelement zu erstellen, deklarieren Sie eine `CPagerCtrl` Variable, und rufen Sie dann die [CPagerCtrl:: Create](#create) -Methode oder die [CPagerCtrl::](#createex) -Methode für diese Variable auf.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pager-Steuerelement erstellt. Anschließend wird die [CPagerCtrl:: setchild](#setchild) -Methode verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächen-Steuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl:: setbuttonsize](#setbuttonsize) -Methode verwendet, um die Höhe des Pager-Steuer Elements auf 20 Pixel festzulegen, und die [CPagerCtrl:: setborder](#setborder) -Methode, um die Rahmen Stärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a> CPagerCtrl:: kreateex

Erstellt ein Pager-Steuerelement mit den angegebenen erweiterten Stilen und fügt es an das aktuelle- `CPagerCtrl` Objekt an.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*\
in Eine bitweise Kombination erweiterter Stile, die auf das-Steuerelement angewendet werden sollen. Weitere Informationen finden Sie unter dem *dwExStyle* -Parameter der Funktion " [deatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) ".

*dwstyle*\
in Eine bitweise Kombination (or) von [Fenster Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [Pager-Steuerelement Stilen](/windows/win32/Controls/pager-control-styles) , die auf das-Steuerelement angewendet werden sollen.

*Rect*\
in Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Position und die Größe des Steuer Elements in Client Koordinaten enthält.

*pparser*\
in Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das das übergeordnete Fenster des Steuer Elements ist. Dieser Parameter darf nicht NULL sein.

*NID*\
in Die ID des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Um ein Pager-Steuerelement zu erstellen, deklarieren Sie eine `CPagerCtrl` Variable, und rufen Sie dann die [CPagerCtrl:: Create](#create) -Methode oder die [CPagerCtrl::](#createex) -Methode für diese Variable auf.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a> CPagerCtrl:: forwardmouse

Aktiviert oder deaktiviert die Weiterleitung [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) Meldungen an das Fenster, das im aktuellen Pager-Steuerelement enthalten ist.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parameter

*bForward*\
in TRUE, um Maus Meldungen weiterzuleiten, oder false, um keine Maus Meldungen weiterzuleiten.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a> CPagerCtrl:: GetBorder

Ruft die Rahmengröße des aktuellen Pager-Steuer Elements ab.

```
int GetBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Rahmengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: GetBorder](#getborder) -Methode verwendet, um die Stärke des Rahmens des Pager-Steuer Elements abzurufen.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a> CPagerCtrl:: GetBkColor

Ruft die Hintergrundfarbe des aktuellen Pager-Steuer Elements ab.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die aktuelle Hintergrundfarbe des Pager-Steuer Elements enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: SetBkColor](#setbkcolor) -Methode verwendet, um die Hintergrundfarbe des Pager-Steuer Elements auf rot festzulegen, und die [CPagerCtrl:: GetBkColor](#getbkcolor) -Methode, um zu bestätigen, dass die Änderung vorgenommen wurde.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a> CPagerCtrl:: getbuttonsize

Ruft die Schaltflächen Größe des aktuellen Pager-Steuer Elements ab.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Schaltflächen Größe, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) Nachricht, die in der Windows SDK beschrieben wird.

Wenn das Pager-Steuerelement den PGS_HORZ Stil hat, bestimmt die Schaltflächen Größe die Breite der Pager-Schaltflächen, und wenn das Pager-Steuerelement den PGS_VERT Stil hat, bestimmt die Schaltflächen Größe die Höhe der Pager-Schaltflächen. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a> CPagerCtrl:: GetButtonState

Ruft den Zustand der angegebenen Bild Lauf Schaltfläche im aktuellen Pager-Steuerelement ab.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

Der Zustand der Schaltfläche, die durch den *iButton* -Parameter angegeben wird. Der Status ist entweder PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED oder PGF_HOT. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a> CPagerCtrl:: getdroptarget

Ruft die [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) -Schnittstelle für das aktuelle Pager-Steuerelement ab.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die- `IDropTarget` Schnittstelle für das aktuelle Pager-Steuerelement.

### <a name="remarks"></a>Bemerkungen

`IDropTarget` ist eine der Schnittstellen, die Sie implementieren, um Drag & Drop-Vorgänge in Ihrer Anwendung zu unterstützen.

Diese Methode sendet die [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) Nachricht, die in der Windows SDK beschrieben wird. Der Aufrufer dieser Methode ist dafür verantwortlich, den `Release` Member der [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) -Schnittstelle aufzurufenden, wenn die Schnittstelle nicht mehr benötigt wird.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a> CPagerCtrl:: getscrollpos

Ruft die Bild Lauf Position des aktuellen Pager-Steuer Elements ab.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Bild Lauf Position, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: getscrollpos](#getscrollpos) -Methode verwendet, um die aktuelle Bild Lauf Position des Pager-Steuer Elements abzurufen. Wenn das Pager-Steuerelement nicht bereits auf 0 (null), die am weitesten links stehende Position, zeigt, verwendet das Beispiel die [CPagerCtrl:: setscrollpos](#setscrollpos) -Methode, um die Scrollposition auf NULL festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a> CPagerCtrl:: isbuttondepressiv

Gibt an, ob die angegebene Bild Lauf Schaltfläche des aktuellen Pager-Steuer Elements im gedrückten Zustand ist.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im gedrückten Zustand befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird. Anschließend testet er, ob der zurückgegebene Status PGF_DEPRESSED ist. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a> CPagerCtrl:: isbuttongraut

Gibt an, ob die angegebene Bild Lauf Schaltfläche des aktuellen Pager-Steuer Elements in einem ausgefallenen Zustand ist.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche in einem ausgefallenen Zustand befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird. Anschließend testet er, ob der zurückgegebene Status PGF_GRAYED ist. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a> CPagerCtrl:: isbuttonhot

Gibt an, ob sich die angegebene Bild Lauf Schaltfläche des aktuellen Pager-Steuer Elements im aktiven Zustand befindet.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im aktiven Zustand befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird. Anschließend testet er, ob der zurückgegebene Status PGF_HOT ist. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a> CPagerCtrl:: isbuttonunsichtbar

Gibt an, ob die angegebene Bild Lauf Schaltfläche des aktuellen Pager-Steuer Elements im nicht aktiven Zustand ist.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im nicht sichtbaren Zustand befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Windows bewirkt, dass die Bild Lauf Schaltfläche in einer bestimmten Richtung unsichtbar wird, wenn das enthaltene Fenster in einen gewissen Bereich gescrollt wird, da durch Klicken auf die Schaltfläche nicht mehr der enthaltene Fenster angezeigt werden kann.

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird. Anschließend testet er, ob der zurückgegebene Status PGF_INVISIBLE ist. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: isbuttonunsichtbar](#isbuttoninvisible) -Methode verwendet, um zu bestimmen, ob die linken und rechten scrollschaltflächen des Pager-Steuer Elements sichtbar sind.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a> CPagerCtrl:: isbuttonnormal

Gibt an, ob sich die angegebene Bild Lauf Schaltfläche des aktuellen Pager-Steuer Elements im normalen Zustand befindet.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parameter

*iButton*\
in Gibt die Schaltfläche an, für die der Zustand abgerufen wird. Wenn der Stil des Pager-Steuer Elements PGS_HORZ ist, geben Sie PGB_TOPORLEFT für die linke Schaltfläche an, und PGB_BOTTOMORRIGHT für die Rechte Schaltfläche. Wenn der Stil des Pager-Steuer Elements PGS_VERT ist, geben Sie PGB_TOPORLEFT für die oberste Schaltfläche an, und PGB_BOTTOMORRIGHT für die untere Schaltfläche. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich die angegebene Schaltfläche im normalen Zustand befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Nachricht, die in der Windows SDK beschrieben wird. Anschließend testet er, ob der zurückgegebene Status PGF_NORMAL ist. Weitere Informationen finden Sie im Abschnitt "Rückgabewert" der [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) Meldung.

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a> CPagerCtrl:: recalcsize

Bewirkt, dass das aktuelle Pager-Steuerelement die Größe des enthaltenen Fensters neu berechnet.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) Nachricht, die in der Windows SDK beschrieben wird. Folglich sendet das Pager-Steuerelement die [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) Benachrichtigung, um die scrollbaren Dimensionen des enthaltenen Fensters zu erhalten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: recalcsize](#recalcsize) -Methode verwendet, um das aktuelle Pager-Steuerelement aufzufordern, seine Größe neu zu berechnen.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [Nachrichten Reflektion](../../mfc/tn062-message-reflection-for-windows-controls.md) verwendet, damit das Pager-Steuerelement seine eigene Größe neu berechnen kann, anstatt dass das übergeordnete Dialogfeld des Steuer Elements die Berechnung ausführen muss. Das Beispiel leitet die- `MyPagerCtrl` Klasse von der [CPagerCtrl-Klasse](../../mfc/reference/cpagerctrl-class.md)ab und verwendet dann eine Meldungs Zuordnung, um die [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) Benachrichtigung dem `OnCalcsize` Benachrichtigungs Handler zuzuordnen. In diesem Beispiel legt der Benachrichtigungs Handler die Breite und Höhe des Pager-Steuer Elements auf festgelegte Werte fest.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a> CPagerCtrl:: SetBkColor

Legt die Hintergrundfarbe des aktuellen Pager-Steuer Elements fest.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parameter

*clrbk*\
in Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die neue Hintergrundfarbe des Pager-Steuer Elements enthält.

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die vorherige Hintergrundfarbe des Pager-Steuer Elements enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die [CPagerCtrl:: SetBkColor](#setbkcolor) -Methode verwendet, um die Hintergrundfarbe des Pager-Steuer Elements auf rot festzulegen, und die [CPagerCtrl:: GetBkColor](#getbkcolor) -Methode, um zu bestätigen, dass die Änderung vorgenommen wurde.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a> CPagerCtrl:: setborder

Legt die Rahmengröße des aktuellen Pager-Steuer Elements fest.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parameter

*iborder*\
in Die neue Rahmengröße, gemessen in Pixel. Wenn der *iborder* -Parameter negativ ist, wird die Rahmengröße auf 0 (null) festgelegt.

### <a name="return-value"></a>Rückgabewert

Die vorherige Rahmengröße, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pager-Steuerelement erstellt. Anschließend wird die [CPagerCtrl:: setchild](#setchild) -Methode verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächen-Steuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl:: setbuttonsize](#setbuttonsize) -Methode verwendet, um die Höhe des Pager-Steuer Elements auf 20 Pixel festzulegen, und die [CPagerCtrl:: setborder](#setborder) -Methode, um die Rahmen Stärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a> CPagerCtrl:: setbuttonsize

Legt die Schaltflächen Größe des aktuellen Pager-Steuer Elements fest.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parameter

*ibuttonsize*\
in Die neue Schaltflächen Größe, gemessen in Pixel.

### <a name="return-value"></a>Rückgabewert

Die vorherige Schaltflächen Größe, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) Nachricht, die in der Windows SDK beschrieben wird.

Wenn das Pager-Steuerelement den PGS_HORZ Stil hat, bestimmt die Schaltflächen Größe die Breite der Pager-Schaltflächen, und wenn das Pager-Steuerelement den PGS_VERT Stil hat, bestimmt die Schaltflächen Größe die Höhe der Pager-Schaltflächen. Die Standard Schaltflächen Größe beträgt drei Zehntel der Breite der Bild Lauf Leiste, und die minimale Schaltflächen Größe beträgt 12 Pixel. Weitere Informationen finden Sie unter [Pager-Steuerelement Stile](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pager-Steuerelement erstellt. Anschließend wird die [CPagerCtrl:: setchild](#setchild) -Methode verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächen-Steuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl:: setbuttonsize](#setbuttonsize) -Methode verwendet, um die Höhe des Pager-Steuer Elements auf 20 Pixel festzulegen, und die [CPagerCtrl:: setborder](#setborder) -Methode, um die Rahmen Stärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a> CPagerCtrl:: setchild

Legt das enthaltene Fenster für das aktuelle Pager-Steuerelement fest.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parameter

*hwndchild*\
in Handle für das Fenster, das enthalten sein soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) Nachricht, die in der Windows SDK beschrieben wird.

Mit dieser Methode wird das übergeordnete Element des enthaltenen Fensters nicht geändert. dem Pager-Steuerelement wird nur ein Fenster Handle für den Bildlauf zugewiesen. In den meisten Fällen ist das enthaltene Fenster ein untergeordnetes Fenster des Pager-Steuer Elements.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Pager-Steuerelement erstellt. Anschließend wird die [CPagerCtrl:: setchild](#setchild) -Methode verwendet, um dem Pager-Steuerelement ein sehr langes Schaltflächen-Steuerelement zuzuordnen. Im Beispiel wird dann die [CPagerCtrl:: setbuttonsize](#setbuttonsize) -Methode verwendet, um die Höhe des Pager-Steuer Elements auf 20 Pixel festzulegen, und die [CPagerCtrl:: setborder](#setborder) -Methode, um die Rahmen Stärke auf 1 Pixel festzulegen.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a> CPagerCtrl:: setscrollpos

Legt die Bild Lauf Position des aktuellen Pager-Steuer Elements fest.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parameter

*IPOs*\
in Die neue Scrollposition, gemessen in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="see-also"></a>Weitere Informationen

[CPagerCtrl-Klasse](../../mfc/reference/cpagerctrl-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Pager-Steuerelemente](/windows/win32/Controls/pager-controls)
