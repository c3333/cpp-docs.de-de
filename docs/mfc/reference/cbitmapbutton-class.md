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
ms.openlocfilehash: 0cf4554f86f4a9275e4d96b3db519fde7fb05b22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231870"
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
|[CBitmapButton:: CBitmapButton](#cbitmapbutton)|Erstellt ein `CBitmapButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapButton:: Autoload](#autoload)|Ordnet eine Schaltfläche in einem Dialogfeld einem Objekt der `CBitmapButton` Klasse zu, lädt die Bitmap (s) nach Namen und passt die Größe der Schaltfläche an die Bitmap an.|
|[CBitmapButton:: LoadBitmaps](#loadbitmaps)|Initialisiert das-Objekt, indem eine oder mehrere benannte Bitmapressourcen aus der Ressourcen Datei der Anwendung geladen und die Bitmaps an das-Objekt angehängt werden.|
|[CBitmapButton:: sizedecontent](#sizetocontent)|Passt die Größe der Schaltfläche an, um die Bitmap anzupassen.|

## <a name="remarks"></a>Bemerkungen

`CBitmapButton`-Objekte enthalten bis zu vier Bitmaps, die Bilder für die verschiedenen Zustände enthalten, die eine Schaltfläche annehmen kann: up (oder normal), Down (oder ausgewählt), Fokus und deaktiviert. Nur die erste Bitmap ist erforderlich. die anderen sind optional.

Bitmap-Schaltflächen Bilder enthalten den Rahmen um das Bild und das Bild selbst. Der Rahmen spielt in der Regel einen Teil, in dem der Zustand der Schaltfläche angezeigt wird. Beispielsweise ist die Bitmap für den Fokus Zustand in der Regel mit der für den Status "up" vergleichbar, aber mit einem gestrichelten Rechteck, das vom Rahmen oder einer Thick-Solid-Linie am Rahmen festgelegt ist. Die Bitmap für den deaktivierten Zustand ähnelt in der Regel der für den Status "up", aber hat einen niedrigeren Kontrast (z. b. eine Abbild-oder Abbild Auswahl).

Diese Bitmaps können eine beliebige Größe aufweisen, aber alle werden so behandelt, als wären Sie dieselbe Größe wie die Bitmap für den Zustand "up".

Verschiedene Anwendungen erfordern unterschiedliche Kombinationen von Bitmapbildern:

|Nach oben|Nach unten|Focused|Deaktiviert|Anwendung|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Schaltfläche ohne WS_TABSTOP Stil|
|×|×|×|×|Dialog Feld Schaltfläche mit allen Zuständen|
|×|×|×||Dialog Feld Schaltfläche mit WS_TABSTOP Stil|

Wenn Sie ein Bitmap-Button-Steuerelement erstellen, legen Sie den BS_OWNERDRAW Stil fest, um anzugeben, dass die Schaltfläche vom Besitzer gezeichnet wird. Dies bewirkt, dass Windows die WM_MEASUREITEM und WM_DRAWITEM Meldungen für die Schaltfläche sendet. Das Framework verarbeitet diese Nachrichten und verwaltet die Darstellung der Schaltfläche.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>So erstellen Sie ein Bitmap-Button-Steuerelement im Client Bereich eines Fensters

1. Erstellen Sie ein bis vier Bitmap-Bilder für die Schaltfläche.

1. Erstellen Sie das [CBitmapButton](#cbitmapbutton) -Objekt.

1. Rufen Sie die [Create](../../mfc/reference/cbutton-class.md#create) -Funktion auf, um das Windows-Schaltflächen-Steuerelement zu erstellen, und fügen Sie es `CBitmapButton`

1. Ruft die [LoadBitmaps](#loadbitmaps) -Member-Funktion auf, um die Bitmapressourcen nach dem Konstruieren der Bitmap-Schaltfläche zu laden.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>So schließen Sie ein Bitmap-Schaltflächen-Steuerelement in einem Dialogfeld ein

1. Erstellen Sie ein bis vier Bitmap-Bilder für die Schaltfläche.

1. Erstellen Sie eine Dialogfeld Vorlage mit einer Schaltfläche zum Zeichnen von Besitzern, an der sich die Schaltfläche "Bitmap" befindet. Die Größe der Schaltfläche in der Vorlage spielt keine Rolle.

1. Legen Sie die Beschriftung der Schaltfläche auf einen Wert wie "MyImage" fest, und definieren Sie ein Symbol für die Schaltfläche, z. b. IDC_MYIMAGE.

1. Weisen Sie im Ressourcen Skript Ihrer Anwendung jedem der für die Schaltfläche erstellten Images eine ID zu, die durch Anhängen eines der Buchstaben "U", "D", "F" oder "X" (für nach oben, nach unten, Fokus und deaktiviert) der Zeichenfolge für die Schaltflächen Beschriftung in Schritt 3 erstellt wurde. Für die Schaltflächen Beschriftung "MyImage" lauten die IDs z. b. "myimageu", "myimaing", "myimagef" und "myimagex". Sie **müssen** die ID der Bitmaps in doppelten Anführungszeichen angeben. Andernfalls weist der Ressourcen-Editor der Ressource eine Ganzzahl zu, und MFC schlägt fehl, wenn das Image geladen wird.

1. Fügen Sie in der Dialogfeld-Klasse Ihrer Anwendung (abgeleitet von `CDialog` ) ein `CBitmapButton` Member-Objekt hinzu.

1. In der `CDialog` [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) -Routine des Objekts wird die `CBitmapButton` [autoload](#autoload) -Funktion des Objekts aufgerufen, wobei als Parameter die Steuerelement-ID der Schaltfläche und der Zeiger des Objekts verwendet werden `CDialog` **`this`** .

Wenn Sie Windows-Benachrichtigungs Meldungen verarbeiten möchten, z. b. BN_CLICKED, die von einem Bitmap-Button-Steuerelement an das übergeordnete Element gesendet werden (normalerweise eine von abgeleitete Klasse `CDialog` ), fügen Sie dem von `CDialog` abgeleiteten Objekt einen Meldungs Zuordnungs Eintrag und eine nachrichtenhandlermember-Funktion für jede Nachricht Die von einem-Objekt gesendeten Benachrichtigungen `CBitmapButton` sind identisch mit denen, die von einem [CButton](../../mfc/reference/cbutton-class.md) -Objekt gesendet werden.

Die Klasse [CToolBar](../../mfc/reference/ctoolbar-class.md) führt einen anderen Ansatz für Bitmapschaltflächen aus.

Weitere Informationen zu finden Sie unter Steuer `CBitmapButton` [Elemente](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxext. h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton:: Autoload

Ordnet eine Schaltfläche in einem Dialogfeld einem Objekt der `CBitmapButton` Klasse zu, lädt die Bitmap (s) nach Namen und passt die Größe der Schaltfläche an die Bitmap an.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Die Steuerelement-ID der Schaltfläche.

*pparent*<br/>
Zeiger auf das-Objekt, das die Schaltfläche besitzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `AutoLoad` Sie die-Funktion, um in einem Dialogfeld eine Schaltfläche zum Zeichnen von Besitzern als Bitmap-Schaltfläche zu initialisieren. Anweisungen zur Verwendung dieser Funktion finden Sie in den Hinweisen für die- `CBitmapButton` Klasse.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton:: CBitmapButton

Erstellt ein `CBitmapButton`-Objekt.

```
CBitmapButton();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie nach dem Erstellen des C++ `CBitmapButton` -Objekts [CButton:: Create](../../mfc/reference/cbutton-class.md#create) auf, um das Windows-Schaltflächen-Steuerelement zu erstellen und an das-Objekt anzufügen `CBitmapButton`

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton:: LoadBitmaps

Verwenden Sie diese Funktion, wenn Sie Bitmapbilder laden möchten, die durch ihre Ressourcennamen oder ID-Nummern identifiziert werden, oder wenn Sie die Funktion nicht verwenden können, `AutoLoad` da Sie z. b. eine Bitmap-Schaltfläche erstellen, die nicht Teil eines Dialog Felds ist.

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

*lpszbitmapresource*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die den Namen der Bitmap für den normalen oder "aufwärts"-Zustand einer Bitmap-Schaltfläche enthält. Erforderlich.

*lpszbitmapresourcesel*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die den Namen der Bitmap für den ausgewählten oder "nach-unten"-Zustand einer Bitmap-Schaltfläche enthält. Kann NULL sein.

*lpszbitmapresourcefocus*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die den Namen der Bitmap für den Fokus Zustand einer Bitmap-Schaltfläche enthält. Kann NULL sein.

*lpszbitmapresourcedeaktiviert*<br/>
Verweist auf die auf NULL endenden Zeichenfolge, die den Namen der Bitmap für den deaktivierten Zustand einer Bitmap-Schaltfläche enthält. Kann NULL sein.

*nidbitmapresource*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmap-Ressource für den normalen oder "up"-Zustand einer Bitmap-Schaltfläche an. Erforderlich.

*nidbitmapresourcesel*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmap-Ressource für den ausgewählten oder "nach-unten"-Zustand einer Bitmap-Schaltfläche an. Kann 0 sein.

*nidbitmapresourcefocus*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmap-Ressource für den Fokus Zustand einer Bitmap-Schaltfläche an. Kann 0 sein.

*nidbitmapresourcedeaktiviert*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmap-Ressource für den deaktivierten Zustand einer Bitmap-Schaltfläche an. Kann 0 sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton:: sizedecontent

Mit dieser Funktion können Sie die Größe einer Bitmap-Schaltfläche auf die Größe der Bitmap ändern.

```cpp
void SizeToContent();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
