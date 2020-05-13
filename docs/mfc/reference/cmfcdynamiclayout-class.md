---
title: CMFCDynamicLayout-Klasse
ms.date: 08/29/2019
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: 77dd3a84a0c76b92495bb062eeb83ff013933087
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752387"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout-Klasse

Gibt an, wie Steuerelemente in einem Fenster verschoben und verkleinert oder vergrößert werden, wenn Benutzer die Größe des Fensters ändern.

## <a name="syntax"></a>Syntax

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Erstellt ein `CMFCDynamicLayout`-Objekt.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Fügt der Liste von Fenstern, die vom dynamischen Layout-Manager gesteuert werden, ein untergeordnetes Fenster hinzu, in der Regel ein Steuerelement.|
|[CMFCDynamicLayout::Adjust](#adjust)|Fügt der Liste von Fenstern, die vom dynamischen Layout-Manager gesteuert werden, ein untergeordnetes Fenster hinzu, in der Regel ein Steuerelement.|
|[CMFCDynamicLayout::Create](#create)|Speichert und überprüft das Hostfenster.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Gibt einen Zeiger auf ein Hostfenster zurück.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Gibt die Größe des Fensters zurück, unterhalb derer das Layout nicht angepasst wird.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Ruft das Rechteck für den aktuellen Client-Bereich des Fensters ab.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Überprüft, ob dem dynamischen Layout ein untergeordnetes Steuerelement hinzugefügt wurde.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Überprüft, ob einem dynamischen Layout keine untergeordneten Fenster hinzugefügt wurden.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Liest das dynamische Layout aus der AFX_DIALOG_LAYOUT-Ressource und wendet das Layout dann auf das Hostfenster an.|
|statisches [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|
|statisches [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|
|statisches [CMFCDynamicLayout::MoveNone](#movenone)|Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der keine vertikale oder horizontale Bewegung für ein untergeordnetes Steuerelement darstellt.|
|statisches [CMFCDynamicLayout::MoveVertical](#movevertical)|Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement vertikal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Legt die Größe des Fensters fest, unterhalb derer das Layout nicht angepasst wird.|
|statisches [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements horizontal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|
|statisches [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements horizontal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|
|statisches [CMFCDynamicLayout::SizeNone](#sizenone)|Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der keine Größenänderung für ein untergeordnetes Steuerelement darstellt.|
|statisches [CMFCDynamicLayout::SizeVertical](#sizevertical)|Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements vertikal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.|

## <a name="nested-types"></a>Geschachtelte Typen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDynamicLayout::MoveSettings-Struktur](#movesettings_structure)|Kapselt Daten für die Verschiebung für Steuerelemente in einem dynamischen Layout.|
|[CMFCDynamicLayout::SizeSettings Structure](#sizesettings_structure)|Kapselt Daten für die Größenänderung für Steuerelemente in einem dynamischen Layout.|

## <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxlayout.h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a>CMFCDynamicLayout::AddItem

Fügt der Liste von Fenstern, die vom dynamischen Layout-Manager gesteuert werden, ein untergeordnetes Fenster hinzu, in der Regel ein Steuerelement.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
Das Handle zum hinzuzufügenden Fenster.

*nID*<br/>
Die ID des hinzuzufügenden untergeordneten Steuerelements.

*moveSettings*<br/>
Eine Struktur, die beschreibt, wie das Steuerelement verschoben werden soll, wenn sich die Fenstergröße ändert.

*sizeEinstellungen*<br/>
Eine Struktur, die beschreibt, wie die Größe des Steuerelements geändert werden soll, wenn sich die Fenstergröße ändert.

### <a name="return-value"></a>Rückgabewert

„True“, wenn das Element erfolgreich hinzugefügt wurde, andernfalls „false“.

### <a name="remarks"></a>Bemerkungen

Die Position und Größe eines untergeordneten Steuerelements werden dynamisch geändert, wenn die Größe eines Hostingfensters geändert wird.

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a>CMFCDynamicLayout::Anpassen

Fügt der Liste von Fenstern, die vom dynamischen Layout-Manager gesteuert werden, ein untergeordnetes Fenster hinzu, in der Regel ein Steuerelement.

```cpp
void Adjust();
```

### <a name="remarks"></a>Bemerkungen

Die Position und Größe eines untergeordneten Steuerelements werden dynamisch geändert, wenn die Größe eines Hostingfensters geändert wird.

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a>CMFCDynamicLayout::Erstellen

Speichert und überprüft das Hostfenster.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parameter

*pHostWnd*<br/>
Ein Zeiger zum Hostfenster.

### <a name="return-value"></a>Rückgabewert

„True“, wenn die Erstellung erfolgreich war, andernfalls „false“.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd

Gibt einen Zeiger auf ein Hostfenster zurück.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger zum Hostfenster.

### <a name="remarks"></a>Bemerkungen

Standardmäßig alle untergeordneten Steuerelementpositionen, die in Bezug auf dieses Fenster neuberechnet wurden.

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a>CMFCDynamicLayout::GetMinSize

Gibt die Größe des Fensters zurück, unterhalb derer das Layout nicht angepasst wird.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Rückgabewert

Legt die Größe des Fensters fest, unterhalb derer das Layout nicht angepasst wird.

### <a name="remarks"></a>Bemerkungen

Die Position und Größe eines untergeordneten Steuerelements werden dynamisch geändert, wenn die Größe eines Hostingfensters geändert wird. Es gibt jedoch eine Mindestgröße, unterhalb derer das Layout nicht angepasst wird. Der Benutzer kann die Größe des Fensters auf eine kleinere Größe ändern, Teile des Fensters werden jedoch aus der Ansicht ausgeblendet.

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect

Ruft das Rechteck für den aktuellen Client-Bereich des Fensters ab.

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Nach Rückgabe der Funktion enthält dieser Parameter das umschließende Rechteck für den Layoutbereich. Dies ist ein out-Parameter; der Eingabewert wird überschrieben.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a>CMFCDynamicLayout::HasItem

Überprüft, ob dem dynamischen Layout ein untergeordnetes Steuerelement hinzugefügt wurde.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
Erstellt ein Handle für das Steuerelement-Fenster.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Layout bereits dieses Element besitzt; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a>CMFCDynamicLayout::IsEmpty

Überprüft, ob einem dynamischen Layout keine untergeordneten Fenster hinzugefügt wurden.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Layout keine Elemente aufweist, ansonsten FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a>CMFCDynamicLayout::LoadResource

Liest das dynamische Layout aus der AFX_DIALOG_LAYOUT-Ressource und wendet das Layout dann auf das Hostfenster an.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parameter

*pHostWnd*<br/>
Ein Zeiger zum Hostfenster.

*lpResource*<br/>
Ein Zeiger zum Puffer, der die AFX_DIALOG_LAYOUT-Ressource enthält.

*dwSize*<br/>
Die Puffergröße in Byte.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource geladen und auf das Hostfenster angewendet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a>CMFCDynamicLayout::MoveHorizontal

Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parameter

*nRatio*<br/>
Definiert einen Prozentwert, der angibt, wie weit ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [MoveSettings-Wert,](#movesettings_structure) der das angeforderte Verschiebungsverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical

Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parameter

*nXRatio*<br/>
Definiert einen Prozentwert, der angibt, wie weit ein untergeordnetes Steuerelement horizontal verschoben wird, wenn der Benutzer die Größe des Hostfensters ändert.

*nYRatio*<br/>
Definiert einen Prozentwert, der angibt, wie weit ein untergeordnetes Steuerelement vertikal verschoben wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [MoveSettings-Wert,](#movesettings_structure) der das angeforderte Verschiebungsverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a>CMFCDynamicLayout::MoveNone

Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der keine vertikale oder horizontale Bewegung für ein untergeordnetes Steuerelement darstellt.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Rückgabewert

Ein [MoveSettings-Wert,](#movesettings_structure) der das Steuerelement fixiert, sodass es nicht verschoben wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a>CMFCDynamicLayout::MoveSettings-Struktur

Kapselt Daten für die Verschiebung für Steuerelemente in einem dynamischen Layout.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Bemerkungen

Dies ist eine geschachtelte Klasse innerhalb von `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Überprüft, ob die Verschiebungsdaten eine horizontale Verschiebung ungleich null angeben.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Rückgabewert

„True“, wenn das `MoveSettings`-Objekt eine horizontale Verschiebung ungleich null angibt.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Überprüft, ob die Verschiebungsdaten keine Verschiebung angeben.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Rückgabewert

TRUE, wenn das `MoveSettings`-Objekt keine Veschiebung angibt.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

Überprüft, ob die Verschiebungsdaten eine vertikale Verschiebung ungleich 0 angeben.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Rückgabewert

TRUE, wenn das `MoveSettings`-Objekt eine vertikale Verschiebung ungleich 0 angibt.

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a>CMFCDynamicLayout::MoveVertical

Ruft einen [MoveSettings-Wert](#movesettings_structure) ab, der definiert, wie stark ein untergeordnetes Steuerelement vertikal verschoben wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parameter

*nRatio*<br/>
Definiert einen Prozentwert, der angibt, wie weit ein untergeordnetes Steuerelement vertikal verschoben wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [MoveSettings-Wert,](#movesettings_structure) der das angeforderte Verschiebungsverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a>CMFCDynamicLayout::SetMinSize

Legt die Größe des Fensters fest, unterhalb derer das Layout nicht angepasst wird.

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die gewünschte Fenstergröße, unterhalb derer das Layout nicht angepasst wird.

### <a name="remarks"></a>Bemerkungen

Die Position und Größe eines untergeordneten Steuerelements werden dynamisch geändert, wenn die Größe eines Hostingfensters geändert wird. Es gibt jedoch eine Mindestgröße, unterhalb derer das Layout nicht angepasst wird. Der Benutzer kann die Größe des Fensters auf eine kleinere Größe ändern, Teile des Fensters werden jedoch aus der Ansicht ausgeblendet.

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a>CMFCDynamicLayout::SizeHorizontal

Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements horizontal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parameter

*nRatio*<br/>
Definiert einen Prozentwert, der angibt, inwieweit die Größe eines untergeordneten Steuerelements horizontal angepasst wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [SizeSettings-Wert,](#sizesettings_structure) der das angeforderte Größenverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical

Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements horizontal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parameter

*nXRatio*<br/>
Definiert einen Prozentwert, der angibt, inwieweit die Größe eines untergeordneten Steuerelements horizontal angepasst wird, wenn der Benutzer die Größe des Hostfensters ändert.

*nYRatio*<br/>
Definiert einen Prozentwert, der angibt, inwieweit die Größe eines untergeordneten Steuerelements vertikal angepasst wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [SizeSettings-Wert,](#sizesettings_structure) der das angeforderte Größenverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a>CMFCDynamicLayout::SizeNone

Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der keine Größenänderung für ein untergeordnetes Steuerelement darstellt.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Rückgabewert

Ein [SizeSettings-Wert,](#sizesettings_structure) der das Steuerelement mit einer bestimmten Größe fixiert, sodass er die Größe nicht ändert, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a>CMFCDynamicLayout::SizeSettings-Struktur

Kapselt Daten für die Größenänderung für Steuerelemente in einem dynamischen Layout.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Bemerkungen

Dies ist eine geschachtelte Klasse innerhalb von `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Überprüft, ob die Größenanpassungsdaten eine horizontale Größenanpassung ungleich null angeben.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Rückgabewert

TRUE, wenn das `SizeSettings`-Objekt eine horizontale Größenanpassung ungleich null angibt.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Überprüft, ob die Größenanpassungsdaten keine Größenanpassung angeben.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Rückgabewert

TRUE, wenn das `SizeSettings`-Objekt keine Größenanpassung angibt.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Überprüft, ob die Größenanpassungsdaten eine vertikale Größenanpassung ungleich null angeben.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Rückgabewert

TRUE, wenn das `SizeSettings`-Objekt eine vertikale Größenanpassung ungleich null angibt.

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical

Ruft einen [SizeSettings-Wert](#sizesettings_structure) ab, der definiert, wie stark die Größe eines untergeordneten Steuerelements vertikal geändert wird, wenn der Benutzer die Größe seines Hostingfensters ändert.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parameter

*nRatio*<br/>
Definiert einen Prozentwert, der angibt, inwieweit die Größe eines untergeordneten Steuerelements vertikal angepasst wird, wenn der Benutzer die Größe des Hostfensters ändert.

### <a name="return-value"></a>Rückgabewert

Ein [SizeSettings-Wert,](#sizesettings_structure) der das angeforderte Größenverhältnis kapselt.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
