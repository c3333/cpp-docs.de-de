---
title: CMiniFrameWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319819"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd-Klasse

Stellt ein Rahmenfenster mit halber Höhe dar, das in der Regel um unverankerte Symbolleisten sichtbar ist.

## <a name="syntax"></a>Syntax

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Erstellt ein `CMiniFrameWnd`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMiniFrameWnd::Erstellen](#create)|Erstellt `CMiniFrameWnd` ein Objekt nach dem Bau.|
|[CMiniFrameWnd::CreateEx](#createex)|Erstellt `CMiniFrameWnd` ein Objekt (mit zusätzlichen Optionen) nach der Konstruktion.|

## <a name="remarks"></a>Bemerkungen

Diese Mini-Rahmenfenster verhalten sich wie normale Rahmenfenster, außer dass sie keine Schaltflächen oder Menüs minimieren/maximieren und Sie müssen nur auf das Systemmenü klicken, um sie zu schließen.

Um ein `CMiniFrameWnd` Objekt zu verwenden, definieren Sie zuerst das Objekt. Rufen Sie dann die Funktion Member [erstellen](#create) auf, um das Miniframefenster anzuzeigen.

Weitere Informationen zur Verwendung `CMiniFrameWnd` von Objekten finden Sie im Artikel [Docking and Floating Toolbars](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Erstellt ein `CMiniFrameWnd` Objekt, erstellt jedoch kein Fenster.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Bemerkungen

Um das Fenster zu erstellen, rufen Sie [CMiniFrameWnd::Create](#create)auf.

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Erstellen

Erstellt das Windows-Miniframefenster und fügt `CMiniFrameWnd` es an das Objekt an.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parameter

*lpClassName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die die Windows-Klasse benennt. Der Klassenname kann ein beliebiger Name sein, der mit der globalen [AfxRegisterWndClass-Funktion](application-information-and-management.md#afxregisterwndclass) registriert ist. Wenn NULL, wird die Fensterklasse vom Framework für Sie registriert. MFC gibt der Standardklasse die folgenden Stile und Attribute:

- Legt Stilbit-CS_DBLCLKS fest, der Doppelklicknachrichten an die Fensterprozedur sendet, wenn der Benutzer mit der Maus doppelklickt.

- Legt Stilbits CS_HREDRAW und CS_VREDRAW fest, die den Inhalt des Clientbereichs anleiten, neu gezeichnet zu werden, wenn das Fenster die Größe ändert.

- Legt den Klassencursor auf den Windows-Standard IDC_ARROW.

- Legt den Klassenhintergrundpinsel auf NULL fest, sodass der Hintergrund nicht aus dem Fenster löscht wird.

- Legt das Klassensymbol auf das Windows-Logo-Symbol mit dem Schwenken von Schwenkflags fest.

- Legt das Fenster auf die Standardgröße und -position fest, wie von Windows angegeben.

*lpWindowName*<br/>
Verweist auf eine null-terminierte Zeichenfolge, die den Fensternamen enthält.

*dwStyle*<br/>
Gibt die Fensterstilattribute an. Dazu können Standardfensterstile und einer oder mehrere der folgenden speziellen Stile gehören:

- MFS_MOVEFRAME Ermöglicht das Verschieben des Minirahmenfensters, indem Sie auf eine beliebige Kante des Fensters klicken, nicht nur auf die Beschriftung.

- MFS_4THICKFRAME Deaktiviert die Größenänderung des Miniframefensters.

- MFS_SYNCACTIVE Synchronisiert die Aktivierung des Miniframefensters mit der Aktivierung des übergeordneten Fensters.

- MFS_THICKFRAME Ermöglicht die Größe des Minirahmenfensters, die so klein ist, wie es der Inhalt des Clientbereichs zulässt.

- MFS_BLOCKSYSMENU Deaktiviert den Zugriff auf das Systemmenü und das Steuerelementmenü und konvertiert sie in einen Teil der Beschriftung (Titelleiste).

Unter [CWnd::Create](../../mfc/reference/cwnd-class.md#create) finden Sie eine Beschreibung möglicher Fensterstilwerte. Die typische Kombination für Minirahmenfenster ist WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.

*Rect*<br/>
Eine `RECT` Struktur, die die gewünschten Abmessungen des Fensters angibt.

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fenster. Verwenden Sie NULL für Fenster der obersten Ebene.

*nID*<br/>
Wenn das Miniframefenster als untergeordnetes Fenster erstellt wird, ist dies der Bezeichner des untergeordneten Steuerelements. andernfalls 0.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

`Create`initialisiert den Klassennamen und den Fensternamen des Fensters und registriert Standardwerte für den Stil und das übergeordnete Element.

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx

Erstellt ein `CMiniFrameWnd` -Objekt.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil `CMiniFrameWnd` des Erstellten an. Wenden Sie einen der [erweiterten Fensterstile](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) auf das Fenster an.

*lpClassName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die die Windows-Klasse benennt (eine [WNDCLASS-Struktur).](/windows/win32/api/winuser/ns-winuser-wndclassw) Der Klassenname kann ein beliebiger Name sein, der mit der globalen [AfxRegisterWndClass-Funktion](application-information-and-management.md#afxregisterwndclass) oder einem der vordefinierten Steuerelementklassennamen registriert ist. Es darf nicht NULL sein.

*lpWindowName*<br/>
Verweist auf eine null-terminierte Zeichenfolge, die den Fensternamen enthält.

*dwStyle*<br/>
Gibt die Fensterstilattribute an. Unter [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [CWnd::Create](../../mfc/reference/cwnd-class.md#create) finden Sie eine Beschreibung der möglichen Werte.

*Rect*<br/>
Die Größe und Position des Fensters in den Clientkoordinaten von *pParentWnd*.

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fensterobjekt.

*nID*<br/>
Der Bezeichner des untergeordneten Fensters.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die `CreateEx` Parameter geben die WNDCLASS, den Fensterstil und (optional) die Anfangsposition und Größe des Fensters an. `CreateEx`gibt auch das übergeordnete Fenster (falls vorhanden) und die ID an.

Bei `CreateEx` der Ausführung sendet Windows die [Nachrichten WM_GETMINMAXINFO ,](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)und [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) Nachrichten an das Fenster.

Um die Standardnachrichtenbehandlung zu erweitern, `CMiniFrameWnd`leiten Sie eine Klasse von ab , fügen Sie der neuen Klasse eine Nachrichtenzuordnung hinzu, und stellen Sie Memberfunktionen für die oben genannten Nachrichten bereit. Überschreiben `OnCreate`Sie z. B., um die erforderliche Initialisierung für eine neue Klasse durchzuführen.

Überschreiben `On`Sie weitere *Nachrichtennachrichtenhandler,* um der abgeleiteten Klasse weitere Funktionen hinzuzufügen.

Wenn der WS_VISIBLE-Stil angegeben ist, sendet Windows dem Fenster alle Nachrichten, die zum Aktivieren und Anzeigen des Fensters erforderlich sind. Wenn der Fensterstil eine Titelleiste angibt, wird der Fenstertitel, auf den der Parameter *lpszWindowName* zeigt, in der Titelleiste angezeigt.

Der *parameter dwStyle* kann eine beliebige Kombination von [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles)sein.

Die Fenster der Palette-Toolbox im alten Stil werden nicht mehr unterstützt. Der alte Stil, der keine Schaltfläche "X" Schließen hatte, wurde beim Ausführen einer MFC-Anwendung unter früheren Windows-Versionen unterstützt, wird jedoch in Visual C++.NET nicht mehr unterstützt. Nur der neue WS_EX_TOOLWINDOW-Stil wird jetzt unterstützt. Eine Beschreibung dieses Stils finden Sie unter [Erweiterte Fensterstile](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Siehe auch

[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)
