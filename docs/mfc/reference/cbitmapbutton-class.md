---
title: CBitmapButton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: c052f913f68d1890a470ed8a6aae2882ed181863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352713"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton-Klasse

Erstellt Pushbutton-Steuerelemente, die mit Bitmapbildern statt mit Text bezeichnet sind.

## <a name="syntax"></a>Syntax

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Erstellt ein `CBitmapButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Ordnet eine Schaltfläche in einem Dialogfeld `CBitmapButton` einem Objekt der Klasse zu, lädt die Bitmap(n) nach Namen und passt die Schaltfläche an die Bitmap an.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Initialisiert das Objekt, indem eine oder mehrere benannte Bitmapressourcen aus der Ressourcendatei der Anwendung geladen und die Bitmaps an das Objekt angefügt werden.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Größe der Schaltfläche für die Bitmap.|

## <a name="remarks"></a>Bemerkungen

`CBitmapButton`Objekte enthalten bis zu vier Bitmaps, die Bilder für die verschiedenen Zustände enthalten, die eine Schaltfläche annehmen kann: nach oben (oder normal), nach unten (oder ausgewählt), fokussiert und deaktiviert. Es ist nur die erste Bitmap erforderlich. die anderen sind optional.

Bitmap-Button-Bilder enthalten den Rahmen um das Bild sowie das Bild selbst. Der Rahmen spielt in der Regel eine Rolle bei der Anzeige des Zustands der Schaltfläche. Beispielsweise ist die Bitmap für den fokussierten Zustand in der Regel wie die für den Up-Zustand, jedoch mit einem gestrichelten Rechteck, das vom Rahmen oder einer dicken durchgezogenen Linie am Rahmen eingesteckt ist. Die Bitmap für den deaktivierten Status ähnelt in der Regel der für den Up-Status, weist jedoch einen niedrigeren Kontrast auf (z. B. eine abgeblendete oder graue Menüauswahl).

Diese Bitmaps können beeinen Stückgrößen haben, aber alle werden so behandelt, als hätten sie die gleiche Größe wie die Bitmap für den Up-Status.

Verschiedene Anwendungen erfordern unterschiedliche Kombinationen von Bitmap-Bildern:

|Nach oben|Nach unten|Mit Fokus|Disabled|Application|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Button ohne WS_TABSTOP Stil|
|×|×|×|×|Dialog-Taste mit allen Zuständen|
|×|×|×||Dialog-Taste mit WS_TABSTOP-Stil|

Legen Sie beim Erstellen eines Bitmap-Schaltflächensteuerelements den stil BS_OWNERDRAW fest, um anzugeben, dass die Schaltfläche vom Besitzer gezeichnet wird. Dies bewirkt, dass Windows die WM_MEASUREITEM und WM_DRAWITEM Nachrichten für die Schaltfläche sendet. Das Framework verarbeitet diese Meldungen und verwaltet die Darstellung der Schaltfläche für Sie.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>So erstellen Sie ein Bitmap-Schaltflächensteuerelement im Clientbereich eines Fensters

1. Erstellen Sie ein bis vier Bitmap-Bilder für die Schaltfläche.

1. Erstellen Sie das [CBitmapButton-Objekt.](#cbitmapbutton)

1. Rufen Sie die [Funktion Erstellen](../../mfc/reference/cbutton-class.md#create) auf, um `CBitmapButton` das Windows-Schaltflächensteuerelement zu erstellen und es an das Objekt anzuhängen.

1. Rufen Sie die [LoadBitmaps-Memberfunktion](#loadbitmaps) auf, um die Bitmapressourcen zu laden, nachdem die Bitmap-Schaltfläche erstellt wurde.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>So schließen Sie ein Bitmap-Schaltflächensteuerelement in ein Dialogfeld ein

1. Erstellen Sie ein bis vier Bitmap-Bilder für die Schaltfläche.

1. Erstellen Sie eine Dialogvorlage mit einer Besitzer-Zeichnungsschaltfläche, die an der Stelle positioniert ist, an der sie die Bitmap-Schaltfläche verwenden möchten. Die Größe der Schaltfläche in der Vorlage spielt keine Rolle.

1. Legen Sie die Beschriftung der Schaltfläche auf einen Wert wie "MYIMAGE" fest, und definieren Sie ein Symbol für die Schaltfläche, z. B. IDC_MYIMAGE.

1. Geben Sie im Ressourcenskript Ihrer Anwendung jedem der für die Schaltfläche erstellten Bilder eine ID, die durch Anfügen eines der Buchstaben "U", "D", "F" oder "X" (für Nachoben, Nachunten, Fokussiert und Deaktiviert) an die Zeichenfolge erstellt wurde, die für die Schaltflächenbeschriftung in Schritt 3 verwendet wird. Für die Schaltflächenbeschriftung "MYIMAGE" wären die IDs beispielsweise "MYIMAGEU", " MYIMAGED", " MYIMAGEF" und " MYIMAGEX". Sie **müssen** die ID Ihrer Bitmaps in doppelten Anführungszeichen angeben. Andernfalls weist der Ressourceneditor der Ressource eine ganze Zahl zu, und MFC schlägt beim Laden des Bildes fehl.

1. Fügen Sie in der Dialogklasse `CDialog`Ihrer `CBitmapButton` Anwendung (abgeleitet von ) ein Memberobjekt hinzu.

1. Rufen `CDialog` Sie in der [OnInitDialog-Routine](../../mfc/reference/cdialog-class.md#oninitdialog) des Objekts die `CBitmapButton` [AutoLoad-Funktion](#autoload) des Objekts `CDialog` auf, indem Sie als Parameter die Steuerungs-ID der Schaltfläche und den **diesem** Zeiger des Objekts verwenden.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, z. B. BN_CLICKED, die von einem Bitmap-Schaltflächensteuerelement an das übergeordnete Element (in der Regel eine von `CDialog`abgeleitete Klasse) gesendet werden, fügen Sie dem `CDialog`-abgeleiteten Objekt einen Message-Map-Eintrag und eine Message-Handler-Memberfunktion für jede Nachricht hinzu. Die von einem `CBitmapButton` Objekt gesendeten Benachrichtigungen entsprechen denen, die von einem [CButton-Objekt](../../mfc/reference/cbutton-class.md) gesendet werden.

Die Klasse [CToolBar](../../mfc/reference/ctoolbar-class.md) verfolgt einen anderen Ansatz für Bitmap-Schaltflächen.

Weitere Informationen `CBitmapButton`zu finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton::AutoLoad

Ordnet eine Schaltfläche in einem Dialogfeld `CBitmapButton` einem Objekt der Klasse zu, lädt die Bitmap(n) nach Namen und passt die Schaltfläche an die Bitmap an.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Die Steuer-ID der Schaltfläche.

*pParent*<br/>
Zeiger auf das Objekt, das die Schaltfläche besitzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `AutoLoad` Sie die Funktion, um eine Besitzer-Zeichnungsschaltfläche in einem Dialogfeld als Bitmap-Schaltfläche zu initialisieren. Anweisungen für die Verwendung dieser Funktion `CBitmapButton` finden Sie in den Anmerkungen für die Klasse.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Erstellt ein `CBitmapButton` -Objekt.

```
CBitmapButton();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie nach `CBitmapButton` dem Erstellen des C++-Objekts [CButton::Create](../../mfc/reference/cbutton-class.md#create) `CBitmapButton` auf, um das Windows-Schaltflächensteuerelement zu erstellen und es an das Objekt anzuhängen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Verwenden Sie diese Funktion, wenn Sie Bitmapbilder laden möchten, die durch `AutoLoad` ihre Ressourcennamen oder ID-Nummern gekennzeichnet sind, oder wenn Sie die Funktion nicht verwenden können, da Sie z. B. eine Bitmapschaltfläche erstellen, die nicht Teil eines Dialogfelds ist.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>Parameter

*lpszBitmapRessource*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die den Namen der Bitmap für den normalen oder "up"-Status einer Bitmap-Schaltfläche enthält. Erforderlich.

*lpszBitmapResourceSel*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die den Namen der Bitmap für den ausgewählten oder "down"-Status einer Bitmap-Schaltfläche enthält. Kann NULL sein.

*lpszBitmapResourceFocus*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die den Namen der Bitmap für den fokussierten Status einer Bitmapschaltfläche enthält. Kann NULL sein.

*lpszBitmapResourceDisabled*<br/>
Zeigt auf die null-terminierte Zeichenfolge, die den Namen der Bitmap für den deaktivierten Status einer Bitmapschaltfläche enthält. Kann NULL sein.

*nIDBitmapRessource*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmapressource für den normalen oder "up"-Status einer Bitmap-Schaltfläche an. Erforderlich.

*nIDBitmapResourceSel*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmapressource für den ausgewählten oder "down"-Status einer Bitmap-Schaltfläche an. Kann 0 sein.

*nIDBitmapResourceFocus*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmapressource für den fokussierten Status einer Bitmapschaltfläche an. Kann 0 sein.

*nIDBitmapResourceDisabled*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmapressource für den deaktivierten Status einer Bitmapschaltfläche an. Kann 0 sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Rufen Sie diese Funktion auf, um die Größe einer Bitmap-Schaltfläche auf die Größe der Bitmap zu ändern.

```
void SizeToContent();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
