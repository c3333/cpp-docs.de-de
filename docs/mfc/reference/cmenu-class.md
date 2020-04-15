---
title: CMenu-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369978"
---
# <a name="cmenu-class"></a>CMenu-Klasse

Eine Kapselung von Windows- `HMENU`.

## <a name="syntax"></a>Syntax

```
class CMenu : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Erstellt ein `CMenu`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Fügt ein neues Element am Ende dieses Menüs an.|
|[CMenu::Anfügen](#attach)|Fügt ein Windows-Menühandle `CMenu` an ein Objekt an.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Platziert ein Häkchen neben oder entfernt ein Häkchen aus einem Menüpunkt im Popupmenü.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Platziert ein Optionsfeld neben einem Menüpunkt und entfernt das Optionsfeld aus allen anderen Menüelementen in der Gruppe.|
|[CMenu::CreateMenu](#createmenu)|Erstellt ein leeres Menü und `CMenu` fügt es an ein Objekt an.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Erstellt ein leeres Popupmenü und `CMenu` fügt es an ein Objekt an.|
|[CMenu::DeleteMenu](#deletemenu)|Löscht ein angegebenes Element aus dem Menü. Wenn das Menüelement über ein zugeordnetes Popupmenü verfügt, wird das Handle im Popupmenü zerstört und der von ihm verwendete Speicher frei.|
|[CMenu::DeleteTempMap](#deletetempmap)|Löscht alle `CMenu` temporären Objekte, die von der `FromHandle` Memberfunktion erstellt wurden.|
|[CMenu::DestroyMenu](#destroymenu)|Zerstört das an ein `CMenu` Objekt angehängte Menü und gibt jeglichen Speicher frei, den das Menü belegt hat.|
|[CMenu::Detach](#detach)|Trennt ein Windows-Menühandle `CMenu` von einem Objekt und gibt das Handle zurück.|
|[CMenu::DrawItem](#drawitem)|Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines vom Besitzer gezeichneten Menüs ändert.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Aktiviert, deaktiviert oder verdunkelt (grau) ein Menüelement.|
|[CMenu::FromHandle](#fromhandle)|Gibt einen Zeiger `CMenu` auf ein Objekt zurück, das ein Windows-Menühandle erhält.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Bestimmt das Standardmenüelement im angegebenen Menü.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Ruft die dem Menü zugeordnete Hilfekontext-ID ab.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Ruft Informationen in einem bestimmten Menü ab.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Bestimmt die Anzahl der Elemente in einem Popup- oder Menü der obersten Ebene.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Ruft die Menüelementkennung für ein Menüelement an der angegebenen Position ab.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Ruft Informationen zu einem Menüelement ab.|
|[CMenu::GetMenuState](#getmenustate)|Gibt den Status des angegebenen Menüelements oder die Anzahl der Elemente in einem Popupmenü zurück.|
|[CMenu::GetMenuString](#getmenustring)|Ruft die Bezeichnung des angegebenen Menüelements ab.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Gibt `m_hMenu` die umschlossene Datei durch dieses `CMenu` Objekt zurück.|
|[CMenu::GetSubMenu](#getsubmenu)|Ruft einen Zeiger auf ein Popupmenü ab.|
|[CMenu::InsertMenu](#insertmenu)|Fügt ein neues Menüelement an der angegebenen Position ein, wodurch andere Elemente im Menü nach unten bewegt werden.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Fügt ein neues Menüelement an der angegebenen Position in einem Menü ein.|
|[CMenu::LoadMenu](#loadmenu)|Lädt eine Menüressource aus der ausführbaren Datei und fügt sie an ein `CMenu` Objekt an.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Lädt ein Menü aus einer Menüvorlage in `CMenu` den Speicher und fügt es an ein Objekt an.|
|[CMenu::MeasureItem](#measureitem)|Wird vom Framework aufgerufen, um Menüdimensionen zu bestimmen, wenn ein vom Besitzer gezeichnetes Menü erstellt wird.|
|[CMenu::ModifyMenu](#modifymenu)|Ändert ein vorhandenes Menüelement an der angegebenen Position.|
|[CMenu::RemoveMenu](#removemenu)|Löscht ein Menüelement mit einem zugeordneten Popupmenü aus dem angegebenen Menü.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Legt das Standardmenüelement für das angegebene Menü fest.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Legt fest, dass die Hilfekontext-ID dem Menü zugeordnet werden soll.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Legt Informationen in einem bestimmten Menü fest.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Ordnet die angegebenen Häkchen-Bitmaps einem Menüelement zu.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Ändert Informationen zu einem Menüelement.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Zeigt ein unverankertes Popupmenü an der angegebenen Position an und verfolgt die Auswahl der Elemente im Popupmenü.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Zeigt ein unverankertes Popupmenü an der angegebenen Position an und verfolgt die Auswahl der Elemente im Popupmenü.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenu::operator HMENU](#operator_hmenu)|Ruft das Handle des Menüobjekts ab.|
|[CMenu::operator !=](#operator_neq)|Legt fest, ob zwei Menüobjekte nicht gleich sind.|
|[CMenu::operator ==](#operator_eq_eq)|Bestimmt, ob zwei Menüobjekte gleich sind.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Gibt das Handle für das Windows-Menü an, das an das `CMenu` Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Es bietet Memberfunktionen zum Erstellen, Nachverfolgen, Aktualisieren und Zerstören eines Menüs.

Erstellen `CMenu` Sie ein Objekt auf dem Stapelrahmen als Local, und rufen Sie `CMenu`dann die Memberfunktionen von auf, um das neue Menü nach Bedarf zu bearbeiten. Rufen Sie als Nächstes [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) auf, um das Menü `CMenu` auf ein Fenster festzulegen, gefolgt von einem sofortigen Aufruf der [Detach-Memberfunktion](#detach) des Objekts. Die `CWnd::SetMenu` Memberfunktion legt das Menü des Fensters auf das neue Menü fest, bewirkt, dass das Fenster neu gezeichnet wird, um die Menüänderung widerzuspiegeln, und übergibt auch den Besitz des Menüs an das Fenster. Der Aufruf, den HMENU `Detach` vom `CMenu` Objekt zu trennen, `CMenu` sodass der `CMenu` Objektdestruktor nicht versucht, ein Menü zu zerstören, das er nicht mehr besitzt, wenn die lokale Variable den Gültigkeitsbereich verlässt. Das Menü selbst wird automatisch zerstört, wenn das Fenster zerstört wird.

Sie können die [LoadMenuIndirect-Memberfunktion](#loadmenuindirect) verwenden, um ein Menü aus einer Vorlage im Arbeitsspeicher zu erstellen, aber ein Menü, das von einer Ressource durch einen Aufruf von [LoadMenu](#loadmenu) erstellt wurde, ist einfacher zu verwalten, und die Menüressource selbst kann vom Menüeditor erstellt und geändert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::AppendMenu

Fügt ein neues Element am Ende eines Menüs an.

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parameter

*nFlags*<br/>
Gibt Informationen zum Status des neuen Menüelements an, wenn es dem Menü hinzugefügt wird. Er besteht aus einem oder mehreren der im Abschnitt "Bemerkungen" aufgeführten Werte.

*nIDNewItem*<br/>
Gibt entweder die Befehls-ID des neuen Menüelements oder, wenn *nFlags* auf MF_POPUP eingestellt ist, das Menühandle ( `HMENU`) eines Popupmenüs an. Der Parameter *nIDNewItem* wird ignoriert (nicht benötigt), wenn *nFlags* auf MF_SEPARATOR festgelegt ist.

*lpszNewItem*<br/>
Gibt den Inhalt des neuen Menüelements an. Der Parameter *nFlags* wird verwendet, um *lpszNewItem* wie folgt zu interpretieren:

|nFlags|Interpretation von lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, den die Anwendung verwenden kann, um zusätzliche Daten zu verwalten, die dem Menüelement zugeordnet sind. Dieser 32-Bit-Wert steht der Anwendung bei der Verarbeiteten WM_MEASUREITEM und WM_DRAWITEM Nachrichten zur Verfügung. Der Wert wird `itemData` im Member der Struktur gespeichert, die mit diesen Nachrichten geliefert wird.|
|MF_STRING|Enthält einen Zeiger auf eine null-terminierte Zeichenfolge. Dies ist die Standardinterpretation.|
|MF_SEPARATOR|Der Parameter *lpszNewItem* wird ignoriert (nicht benötigt).|

*pBmp*<br/>
Zeigt auf `CBitmap` ein Objekt, das als Menüelement verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Anwendung kann den Status des Menüelements angeben, indem sie Werte in *nFlags*festlegt. Wenn *nIDNewItem* ein Popupmenü angibt, wird es Teil des Menüs, an das es angehängt wird. Wenn dieses Menü zerstört wird, wird auch das angehängte Menü zerstört. Ein angehängtes Menü sollte `CMenu` von einem Objekt getrennt werden, um Konflikte zu vermeiden. Beachten Sie, dass MF_STRING und MF_OWNERDRAW für `AppendMenu`die Bitmapversion von ungültig sind.

In der folgenden Liste werden die Flags beschrieben, die in *nFlags*festgelegt werden können:

- MF_CHECKED fungiert als Umschalter mit MF_UNCHECKED, um das Standardhäkchen neben dem Element zu platzieren. Wenn die Anwendung Prüfzeichen-Bitmaps bereitstellt (siehe [die Elementfunktion SetMenuItemBitmaps),](#setmenuitembitmaps) wird die Bitmap "Prüfzeichen auf" angezeigt.

- MF_UNCHECKED fungiert als Umschalter mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen. Wenn die Anwendung Häkchen-Bitmaps `SetMenuItemBitmaps` bereitstellt (siehe Memberfunktion), wird die Bitmap "Check-Mark".

- MF_DISABLED Deaktiviert das Menüelement, sodass es nicht ausgewählt, aber nicht abgeseut wird.

- MF_ENABLED Aktiviert das Menüelement, damit es ausgewählt werden kann, und stellt es aus dem abgeblendeten Zustand wieder her.

- MF_GRAYED Deaktiviert das Menüelement, sodass es nicht ausgewählt werden kann, und dimt es.

- MF_MENUBARBREAK Platziert das Element in einer neuen Zeile in statischen Menüs oder in einer neuen Spalte in Popupmenüs. Die neue Popupmenüspalte wird durch eine vertikale Trennlinie von der alten Spalte getrennt.

- MF_MENUBREAK Platziert das Element in einer neuen Zeile in statischen Menüs oder in einer neuen Spalte in Popupmenüs. Zwischen den Spalten wird keine Trennlinie platziert.

- MF_OWNERDRAW Gibt an, dass es sich bei dem Element um ein Besitzerzeichnungselement handelt. Wenn das Menü zum ersten Mal angezeigt wird, erhält das Fenster, dem das Menü gehört, eine WM_MEASUREITEM Nachricht, die die Höhe und Breite des Menüelements abruft. Die WM_DRAWITEM Nachricht wird gesendet, wenn der Besitzer die visuelle Darstellung des Menüelements aktualisieren muss. Diese Option ist für ein Menüelement der obersten Ebene nicht gültig.

- MF_POPUP Gibt an, dass dem Menüelement ein Popupmenü zugeordnet ist. Der PARAMETER ID gibt ein Handle für ein Popupmenü an, das dem Element zugeordnet werden soll. Dies wird zum Hinzufügen eines Popupmenüs der obersten Ebene oder eines hierarchischen Popupmenüs zu einem Popupmenüelement verwendet.

- MF_SEPARATOR Zeichnet eine horizontale Trennlinie. Kann nur in einem Popup-Menü verwendet werden. Diese Zeile kann nicht abgeblendet, deaktiviert oder hervorgehoben werden. Andere Parameter werden ignoriert.

- MF_STRING Gibt an, dass es sich bei dem Menüelement um eine Zeichenfolge handelt.

Jede der folgenden Gruppen listet Flags auf, die sich gegenseitig ausschließen und nicht zusammen verwendet werden können:

- MF_DISABLED, MF_ENABLED und MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR und die Bitmap-Version

- MF_MENUBARBREAK und MF_MENUBREAK

- MF_CHECKED und MF_UNCHECKED

Jedes Mal, wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird oder nicht), sollte die Anwendung [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)aufrufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::CreateMenu](#createmenu).

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::Anfügen

Fügt ein vorhandenes Windows-Menü an ein `CMenu` Objekt an.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
Gibt ein Handle für ein Windows-Menü an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nicht aufgerufen werden, wenn `CMenu` bereits ein Menü an das Objekt angefügt ist. Das Menühandle wird `m_hMenu` im Datenmember gespeichert.

Wenn das Menü, das Sie bearbeiten möchten, bereits einem Fenster zugeordnet ist, können Sie die [Funktion CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) verwenden, um ein Handle in das Menü zu bringen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem

Fügt Häkchen zu oder entfernt Häkchen aus Menüelementen im Popupmenü.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parameter

*nIDCheckItem*<br/>
Gibt das zu überprüfende Menüelement an, wie von *nCheck*festgelegt.

*nCheck*<br/>
Gibt an, wie das Menüelement überprüft und die Position des Elements im Menü bestimmt werden soll. Der *nCheck-Parameter* kann eine Kombination aus MF_CHECKED oder MF_UNCHECKED mit MF_BYPOSITION oder MF_BYCOMMAND-Flags sein. Diese Flags können mithilfe des bitweisen ODER-Operators kombiniert werden. Sie haben folgende Bedeutungen:

- MF_BYCOMMAND Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardoption.

- MF_BYPOSITION Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.

- MF_CHECKED fungiert als Umschalter mit MF_UNCHECKED, um das Standardhäkchen neben dem Element zu platzieren.

- MF_UNCHECKED fungiert als Umschalter mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen.

### <a name="return-value"></a>Rückgabewert

Der vorherige Status des Elements: MF_CHECKED oder MF_UNCHECKED oder 0xFFFFFFFF, wenn der Menüpunkt nicht vorhanden war.

### <a name="remarks"></a>Bemerkungen

Der Parameter *nIDCheckItem* gibt das zu ändernde Element an.

Der Parameter *nIDCheckItem* kann ein Popupmenüelement sowie ein Menüelement identifizieren. Es sind keine speziellen Schritte erforderlich, um ein Popup-Menüelement zu überprüfen. Menüelemente der obersten Ebene können nicht überprüft werden. Ein Popupmenüelement muss nach Position überprüft werden, da ihm kein Menüelementbezeichner zugeordnet ist.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CMenu::GetMenuState](#getmenustate).

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem

Überprüft ein angegebenes Menüelement und macht es zu einem Radioelement.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nIDFirst*<br/>
Gibt (als ID oder Offset, abhängig vom Wert von *nFlags*) das erste Menüelement in der Optionsfeldgruppe an.

*nIDLast*<br/>
Gibt (als ID oder Offset, abhängig vom Wert von *nFlags*) das letzte Menüelement in der Optionsfeldgruppe an.

*nIDItem*<br/>
Gibt (als ID oder Offset, abhängig vom Wert von *nFlags*) das Element in der Gruppe an, das mit einem Optionsfeld überprüft wird.

*nFlags*<br/>
Gibt die Interpretation von *nIDFirst*, *nIDLast*und *nIDItem* wie folgt an:

|nFlags|Interpretation|
|------------|--------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; sonst 0

### <a name="remarks"></a>Bemerkungen

Gleichzeitig wird die Funktion alle anderen Menüelemente in der zugeordneten Gruppe deaktivieren und das Radioelementtypflag für diese Elemente löscht. Das ausgecheckte Element wird mit einer Optionsfeld- (oder Aufzählungszeichen-)Bitmap anstelle einer Häkchen-Bitmap angezeigt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu

Erstellt ein leeres Menü und `CMenu` fügt es an ein Objekt an.

```
CMenu();
```

### <a name="remarks"></a>Bemerkungen

Das Menü wird erst erstellt, wenn Sie eine der Create- oder Load-Member-Funktionen von`CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Anfügen](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu

Erstellt ein Menü und fügt `CMenu` es an das Objekt an.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Menü erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Menü ist zunächst leer. Menüelemente können mithilfe der `AppendMenu` `InsertMenu` oder Memberfunktion hinzugefügt werden.

Wenn das Menü einem Fenster zugewiesen ist, wird es automatisch zerstört, wenn das Fenster zerstört wird.

Vor dem Beenden muss eine Anwendung Systemressourcen freisetzen, die einem Menü zugeordnet sind, wenn das Menü nicht einem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü frei, indem sie die [DestroyMenu-Memberfunktion](#destroymenu) aufruft.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::CreatePopupMenu

Erstellt ein Popupmenü und fügt `CMenu` es an das Objekt an.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Popupmenü erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Menü ist zunächst leer. Menüelemente können mithilfe der `AppendMenu` `InsertMenu` oder Memberfunktion hinzugefügt werden. Die Anwendung kann das Popup-Menü zu einem vorhandenen Menü oder Popup-Menü hinzufügen. Die `TrackPopupMenu` Memberfunktion kann verwendet werden, um dieses Menü als unverankertes Popup-Menü anzuzeigen und die Auswahl im Popup-Menü nachzuverfolgen.

Wenn das Menü einem Fenster zugewiesen ist, wird es automatisch zerstört, wenn das Fenster zerstört wird. Wenn das Menü zu einem vorhandenen Menü hinzugefügt wird, wird es automatisch zerstört, wenn dieses Menü zerstört wird.

Vor dem Beenden muss eine Anwendung Systemressourcen freilassen, die einem Popupmenü zugeordnet sind, wenn das Menü nicht einem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü frei, indem sie die [DestroyMenu-Memberfunktion](#destroymenu) aufruft.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::CreateMenu](#createmenu).

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

Löscht ein Element aus dem Menü.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das Menüelement an, das gelöscht werden soll, wie von *nFlags*bestimmt.

*nFlags*<br/>
Wird verwendet, um *nPosition* wie folgt zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Wenn das Menüelement über ein zugeordnetes Popupmenü verfügt, `DeleteMenu` wird das Handle zum Popupmenü zerstört und der vom Popupmenü verwendete Speicher frei.

Jedes Mal, wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird oder nicht), muss die Anwendung [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)aufrufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap

Alle temporären `CWinApp` `CMenu` Objekte, die von der [FromHandle-Memberfunktion](#fromhandle) erstellt wurden, werden automatisch vom Leerlaufzeithandler aufgerufen.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Bemerkungen

`DeleteTempMap`löst das Windows-Menüobjekt, das `CMenu` an ein `CMenu` temporäres Objekt angefügt ist, bevor das Objekt gelöscht wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu

Zerstört das Menü und alle verwendeten Windows-Ressourcen.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Menü zerstört wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das Menü wird `CMenu` vom Objekt getrennt, bevor es zerstört wird. Die `DestroyMenu` Windows-Funktion wird `CMenu` automatisch im Destruktor aufgerufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::CreateMenu](#createmenu).

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::Detach

Trennt ein Windows-Menü `CMenu` von einem Objekt und gibt das Handle zurück.

```
HMENU Detach();
```

### <a name="return-value"></a>Rückgabewert

Das Handle vom Typ HMENU zu einem Windows-Menü, falls erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Das `m_hMenu` Datenelement ist auf NULL festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines vom Besitzer gezeichneten Menüs ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll. Überschreiben Sie diese Memberfunktion, um `CMenu` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den anzeigekontext ausgewählt wurden, der in *lpDrawItemStruct* vor dem Beenden dieser Memberfunktion angegeben wurde.

Eine Beschreibung der `DRAWITEMSTRUCT` Struktur finden Sie unter [CWnd::OnDrawItem.](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>Beispiel

Der folgende Code stammt aus dem MFC [CTRLTEST-Beispiel:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu::EnableMenuItem

Aktiviert, deaktiviert oder verdorn ein Menüelement.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parameter

*nIDEnableItem*<br/>
Gibt das zu aktivierende Menüelement an, wie von *nEnable*festgelegt. Dieser Parameter kann Popup-Menüelemente sowie Standardmenüelemente angeben.

*nAktivieren*<br/>
Gibt die zu ergreifende Aktion an. Es kann eine Kombination aus MF_DISABLED, MF_ENABLED oder MF_GRAYED mit MF_BYCOMMAND oder MF_BYPOSITION sein. Diese Werte können mithilfe des bitweisen ODER-Operators kombiniert werden. Diese Werte haben die folgenden Bedeutungen:

- MF_BYCOMMAND Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardoption.

- MF_BYPOSITION Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.

- MF_DISABLED Deaktiviert das Menüelement, sodass es nicht ausgewählt, aber nicht abgeseut wird.

- MF_ENABLED Aktiviert das Menüelement, damit es ausgewählt werden kann, und stellt es aus dem abgeblendeten Zustand wieder her.

- MF_GRAYED Deaktiviert das Menüelement, sodass es nicht ausgewählt werden kann, und dimt es.

### <a name="return-value"></a>Rückgabewert

Vorheriger Status ( MF_DISABLED, MF_ENABLED oder MF_GRAYED) oder -1, wenn nicht gültig.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)und [LoadMenuIndirect](#loadmenuindirect) können auch den Status (aktiviert, deaktiviert oder abgeblendet) eines Menüelements festlegen.

Die Verwendung des MF_BYPOSITION-Werts `CMenu`erfordert, dass eine Anwendung die richtige verwendet. Wenn `CMenu` die Menüleiste verwendet wird, wird ein Menüelement der obersten Ebene (ein Element in der Menüleiste) betroffen. Um den Status eines Elements in einem Popup- oder verschachtelten Popupmenü `CMenu` nach Position festzulegen, muss eine Anwendung das Popupmenü angeben.

Wenn eine Anwendung das MF_BYCOMMAND-Flag angibt, überprüft Windows alle `CMenu`Popupmenüelemente, die dem . Daher ist die Verwendung der `CMenu` Menüleiste ausreichend, es sei denn, doppelte Menüelemente vorhanden sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::FromHandle

Gibt einen Zeiger `CMenu` auf ein Objekt zurück, das ein Windows-Handle für ein Menü erhält.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
Ein Windows-Handle für ein Menü.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CMenu` ein, das vorübergehend oder dauerhaft sein kann.

### <a name="remarks"></a>Bemerkungen

Wenn `CMenu` ein Objekt noch nicht an das Windows-Menüobjekt angefügt ist, wird ein temporäres `CMenu` Objekt erstellt und angefügt.

Dieses `CMenu` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Objekte gelöscht werden.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::CreateMenu](#createmenu).

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem

Bestimmt das Standardmenüelement im angegebenen Menü.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*gmdiFlags*<br/>
Wert, der angibt, wie die Funktion nach Menüelementen sucht. Dieser Parameter kann keiner, einer oder eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Gibt an, dass, wenn das Standardelement ein Untermenü öffnet, die Funktion darin besteht, rekursiv im entsprechenden Untermenü zu suchen. Wenn das Untermenü kein Standardelement enthält, identifiziert der Rückgabewert das Element, das das Untermenü öffnet.<br /><br /> Standardmäßig gibt die Funktion das erste Standardelement im angegebenen Menü zurück, unabhängig davon, ob es sich um ein Element handelt, das ein Untermenü öffnet.|
|GMDI_USEDISABLED|Gibt an, dass die Funktion ein Standardelement zurückgeben soll, auch wenn es deaktiviert ist.<br /><br /> Standardmäßig überspringt die Funktion deaktivierte oder ergraute Elemente.|

*fByPos*<br/>
Wert, der angibt, ob der Bezeichner des Menüelements oder seine Position abgerufen werden soll. Wenn dieser Parameter FALSE ist, wird der Bezeichner zurückgegeben. Andernfalls wird die Position zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert der Bezeichner oder die Position des Menüelements. Wenn die Funktion fehlschlägt, ist der Rückgabewert - 1.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Funktion [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId

Ruft die Kontexthilfe-ID `CMenu`ab, die mit verknüpft ist.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Rückgabewert

Die Kontexthilfe-ID, `CMenu` der derzeit zugeordnet ist, wenn sie über eine enthält. Null sonst.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo

Ruft Informationen für ein Menü ab.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parameter

*lpcmi*<br/>
Ein Zeiger auf eine [MENUINFO-Struktur,](/windows/win32/api/winuser/ns-winuser-menuinfo) die Informationen für das Menü enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null. Andernfalls ist der Rückgabewert Null.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um Informationen über das Menü abzurufen.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount

Bestimmt die Anzahl der Elemente in einem Popup- oder Menü der obersten Ebene.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Menü, wenn die Funktion erfolgreich ist; andernfalls -1.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu::GetMenuItemID

Ruft die Menüelementkennung für ein Menüelement an der von nPos definierten Position *ab.*

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt die Position (nullbasiert) des Menüelements an, dessen ID abgerufen wird.

### <a name="return-value"></a>Rückgabewert

Die Element-ID für das angegebene Element in einem Popupmenü, wenn die Funktion erfolgreich ist. Wenn es sich bei dem angegebenen Element um ein Popupmenü handelt (im Gegensatz zu einem Element im Popupmenü), beträgt der Rückgabewert -1. Wenn *nPos* einem SEPARATOR-Menüelement entspricht, ist der Rückgabewert 0.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo

Ruft Informationen zu einem Menüelement ab.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uItem*<br/>
Identifikator oder Position des Menüelements, über das Informationen erhalten werden sollen. Die Bedeutung dieses Parameters hängt `ByPos`vom Wert von ab.

*lpMenuItemInfo*<br/>
Ein Zeiger auf ein [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), wie im Windows SDK beschrieben, der Informationen zum Menü enthält.

*fByPos*<br/>
Wert, der die `nIDItem`Bedeutung von angibt. Standardmäßig `ByPos` ist FALSE, was angibt, dass uItem ein Menüelementbezeichner ist. Wenn `ByPos` nicht auf FALSE festgelegt ist, wird eine Menüelementposition angezeigt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null. Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, verwenden Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), wie im Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Funktion [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), wie im Windows SDK beschrieben. Beachten Sie, dass Sie `GetMenuItemInfo`in der MFC-Implementierung von kein Handle für ein Menü verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState

Gibt den Status des angegebenen Menüelements oder die Anzahl der Elemente in einem Popupmenü zurück.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Gibt die Menüelement-ID an, wie von *nFlags*bestimmt.

*nFlags*<br/>
Gibt die Art von *nID*an. Es kann sich um einen der folgenden Werte handeln:

- MF_BYCOMMAND Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardoption.

- MF_BYPOSITION Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.

### <a name="return-value"></a>Rückgabewert

Der Wert 0xFFFFFFFF, wenn das angegebene Element nicht vorhanden ist. Wenn *nId* ein Popupmenü identifiziert, enthält das Byte hoher Ordnung die Anzahl der Elemente im Popupmenü und das Byte niedriger Ordnung die Menüflags, die dem Popupmenü zugeordnet sind. Andernfalls ist der Rückgabewert eine Maske (Boolean OR) der Werte aus der folgenden Liste (diese Maske beschreibt den Status des Menüelements, das *nId* identifiziert):

- MF_CHECKED fungiert als Umschalter mit MF_UNCHECKED, um das Standardhäkchen neben dem Element zu platzieren. Wenn die Anwendung Häkchen-Bitmaps `SetMenuItemBitmaps` bereitstellt (siehe Memberfunktion), wird die Bitmap "Prüfzeichen ein" angezeigt.

- MF_DISABLED Deaktiviert das Menüelement, sodass es nicht ausgewählt, aber nicht abgeseut wird.

- MF_ENABLED Aktiviert das Menüelement, damit es ausgewählt werden kann, und stellt es aus dem abgeblendeten Zustand wieder her. Beachten Sie, dass der Wert dieser Konstante 0 ist. Eine Anwendung sollte bei Verwendung dieses Werts nicht mit 0 auf Fehler testen.

- MF_GRAYED Deaktiviert das Menüelement, sodass es nicht ausgewählt werden kann, und dimt es.

- MF_MENUBARBREAK Platziert das Element in einer neuen Zeile in statischen Menüs oder in einer neuen Spalte in Popupmenüs. Die neue Popupmenüspalte wird durch eine vertikale Trennlinie von der alten Spalte getrennt.

- MF_MENUBREAK Platziert das Element in einer neuen Zeile in statischen Menüs oder in einer neuen Spalte in Popupmenüs. Zwischen den Spalten wird keine Trennlinie platziert.

- MF_SEPARATOR Zeichnet eine horizontale Trennlinie. Kann nur in einem Popup-Menü verwendet werden. Diese Zeile kann nicht abgeblendet, deaktiviert oder hervorgehoben werden. Andere Parameter werden ignoriert.

- MF_UNCHECKED fungiert als Umschalter mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen. Wenn die Anwendung Häkchen-Bitmaps `SetMenuItemBitmaps` bereitstellt (siehe Memberfunktion), wird die Bitmap "Check-Mark". Beachten Sie, dass der Wert dieser Konstante 0 ist. Eine Anwendung sollte bei Verwendung dieses Werts nicht mit 0 auf Fehler testen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::GetMenuString

Kopiert die Bezeichnung des angegebenen Menüelements in den angegebenen Puffer.

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parameter

*nIDItem*<br/>
Gibt die ganzzahlige Kennung des Menüelements oder den Versatz des Menüelements im Menü an, abhängig vom Wert von *nFlags*.

*lpString*<br/>
Zeigt auf den Puffer, der die Bezeichnung empfangen soll.

*rString*<br/>
Ein Verweis `CString` auf ein Objekt, das die kopierte Menüzeichenfolge empfangen soll.

*nMaxCount*<br/>
Gibt die maximale Länge (in Zeichen) der zu kopierenden Beschriftung an. Wenn die Bezeichnung länger als das in *nMaxCount*angegebene Maximum ist, werden die zusätzlichen Zeichen abgeschnitten.

*nFlags*<br/>
Gibt die Interpretation des *Parameters nIDItem* an. Es kann sich um einen der folgenden Werte handeln:

|nFlags|Interpretation von nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Gibt die tatsächliche Anzahl der in den Puffer kopierten Zeichen an, ohne den Nullabschlusszeichen.

### <a name="remarks"></a>Bemerkungen

Der Parameter *nMaxCount* sollte größer als die Anzahl der Zeichen in der Bezeichnung sein, um das Nullzeichen aufzunehmen, das eine Zeichenfolge beendet.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu

Gibt den hMENU-Umschlag durch `CMenu` `CMenu` dieses Objekt oder einen NULL-Zeiger zurück.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::LoadMenu](#loadmenu).

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetSubMenu

Ruft das `CMenu` Objekt eines Popupmenüs ab.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt die Position des Popupmenüs im Menü an. Positionswerte beginnen bei 0 für das erste Menüelement. Der Bezeichner des Popupmenüs kann in dieser Funktion nicht verwendet werden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CMenu` ein `m_hMenu` Objekt, dessen Member ein Handle zum Popupmenü enthält, wenn an der angegebenen Position ein Popupmenü vorhanden ist. andernfalls NULL. Wenn `CMenu` kein Objekt vorhanden ist, wird ein temporäres Objekt erstellt. Der `CMenu` zurückgegebene Zeiger sollte nicht gespeichert werden.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CMenu::TrackPopupMenu](#trackpopupmenu).

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu

Fügt ein neues Menüelement an der von *nPosition* angegebenen Position ein und verschiebt andere Elemente im Menü nach unten.

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das Menüelement an, vor dem das neue Menüelement eingefügt werden soll. Der Parameter *nFlags* kann verwendet werden, um *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0. Wenn *nPosition* -1 ist, wird das neue Menüelement an das Ende des Menüs angehängt.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird, und gibt Informationen über den Status des neuen Menüelements an, wenn es dem Menü hinzugefügt wird. Eine Liste der Flags, die festgelegt werden können, finden Sie in der [Memberfunktion AppendMenu.](#appendmenu) Um mehr als einen Wert anzugeben, verwenden Sie den bitweisen ODER-Operator, um sie mit dem MF_BYCOMMAND- oder MF_BYPOSITION-Flag zu kombinieren.

*nIDNewItem*<br/>
Gibt entweder die Befehls-ID des neuen Menüelements oder, wenn *nFlags* auf MF_POPUP eingestellt ist, den Menühandle ( HMENU) des Popupmenüs an. Der Parameter *nIDNewItem* wird ignoriert (nicht benötigt), wenn *nFlags* auf MF_SEPARATOR festgelegt ist.

*lpszNewItem*<br/>
Gibt den Inhalt des neuen Menüelements an. *nFlags* kann verwendet werden, um *lpszNewItem* wie folgt zu interpretieren:

|nFlags|Interpretation von lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, den die Anwendung verwenden kann, um zusätzliche Daten zu verwalten, die dem Menüelement zugeordnet sind. Dieser 32-Bit-Wert steht der `itemData` Anwendung im Member der Struktur zur Verfügung, die von den [WM_MEASUREITEM-](/windows/win32/Controls/wm-measureitem) und [WM_DRAWITEM-Nachrichten](/windows/win32/Controls/wm-drawitem) bereitgestellt wird. Diese Nachrichten werden gesendet, wenn das Menüelement zum ersten Öffnen angezeigt oder geändert wird.|
|MF_STRING|Enthält einen langen Zeiger auf eine null-terminierte Zeichenfolge. Dies ist die Standardinterpretation.|
|MF_SEPARATOR|Der Parameter *lpszNewItem* wird ignoriert (nicht benötigt).|

*pBmp*<br/>
Zeigt auf `CBitmap` ein Objekt, das als Menüelement verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Anwendung kann den Status des Menüelements angeben, indem sie Werte in *nFlags*festlegt.

Jedes Mal, wenn ein Menü, das sich in einem Fenster befindet, `CWnd::DrawMenuBar`geändert wird (unabhängig davon, ob das Fenster angezeigt wird oder nicht), sollte die Anwendung aufrufen.

Wenn *nIDNewItem* ein Popupmenü angibt, wird es Teil des Menüs, in das es eingefügt wird. Wenn dieses Menü zerstört wird, wird auch das eingefügte Menü zerstört. Ein eingefügtes Menü sollte `CMenu` von einem Objekt getrennt werden, um Konflikte zu vermeiden.

Wenn das untergeordnete Fenster der aktiven Multi document Interface (MDI) maximiert wird und eine Anwendung ein Popupmenü in das Menü der MDI-Anwendung einfügt, indem diese Funktion aufgerufen und das MF_BYPOSITION-Flag angegeben wird, wird das Menü eine Position weiter links als erwartet eingefügt. Dies geschieht, weil das Control-Menü des aktiven untergeordneten MDI-Fensters an der ersten Position der Menüleiste des MDI-Rahmenfensters eingefügt wird. Um das Menü richtig zu positionieren, muss die Anwendung 1 zu dem Positionswert hinzufügen, der andernfalls verwendet würde. Eine Anwendung kann die WM_MDIGETACTIVE-Nachricht verwenden, um zu bestimmen, ob das aktuell aktive untergeordnete Fenster maximiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem

Fügt ein neues Menüelement an der angegebenen Position in einem Menü ein.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uItem*<br/>
Siehe Beschreibung von *uItem* in [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) im Windows SDK.

*lpMenuItemInfo*<br/>
Siehe Beschreibung von *lpmii* in `InsertMenuItem` im Windows SDK.

*fByPos*<br/>
Siehe Beschreibung von *fByPosition* in `InsertMenuItem` im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Diese Funktion umschließt [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), wie im Windows SDK beschrieben.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu

Lädt eine Menüressource aus der ausführbaren Datei `CMenu` der Anwendung und fügt sie an das Objekt an.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Namen der zu ladenden Menüressource enthält.

*nIDResource*<br/>
Gibt die Menü-ID der zu ladenden Menüressource an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Menüressource erfolgreich geladen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Vor dem Beenden muss eine Anwendung Systemressourcen freisetzen, die einem Menü zugeordnet sind, wenn das Menü nicht einem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü frei, indem sie die [DestroyMenu-Memberfunktion](#destroymenu) aufruft.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect

Lädt eine Ressource aus einer Menüvorlage in `CMenu` den Arbeitsspeicher und fügt sie an das Objekt an.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parameter

*lpMenuTemplate*<br/>
Zeigt auf eine Menüvorlage (die eine einzelne [MENUITEMTEMPLATEHEADER-Struktur](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) und eine Auflistung einer oder mehrerer [MENUITEMTEMPLATE-Strukturen](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) ist). Weitere Informationen zu diesen beiden Strukturen finden Sie im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Menüressource erfolgreich geladen wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Menüvorlage ist eine Kopfzeile, gefolgt von einer Auflistung einer oder mehrerer [MENUITEMTEMPLATE-Strukturen,](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) von denen jede ein oder mehrere Menüpunkte und Popupmenüs enthalten kann.

Die Versionsnummer sollte 0 sein.

Die `mtOption` Flags sollten MF_END für das letzte Element in einer Popupliste und für das letzte Element in der Hauptliste enthalten. Weitere `AppendMenu` Flags finden Sie in der Memberfunktion. Der `mtId` Member muss in der MENUITEMTEMPLATE-Struktur `mtOption`weggelassen werden, wenn MF_POPUP in angegeben ist.

Der für die MENUITEMTEMPLATE-Struktur zugewiesene `mtString` Speicherplatz muss groß genug sein, um den Namen des Menüelements als null-terminierte Zeichenfolge zu enthalten.

Vor dem Beenden muss eine Anwendung Systemressourcen freisetzen, die einem Menü zugeordnet sind, wenn das Menü nicht einem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü frei, indem sie die [DestroyMenu-Memberfunktion](#destroymenu) aufruft.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

Gibt das HMENU-Handle des Windows-Menüs an, das an das `CMenu` Objekt angefügt ist.

```
HMENU m_hMenu;
```

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMenu::LoadMenu](#loadmenu).

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem

Wird vom Framework aufgerufen, wenn ein Menü mit dem Besitzerzeichnungsstil erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameter

*lpMeasureItemStruct*<br/>
Ein Zeiger auf `MEASUREITEMSTRUCT` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, und füllen Sie die `MEASUREITEMSTRUCT` Struktur aus, um Windows über die Dimensionen des Menüs zu informieren.

Eine Beschreibung der `MEASUREITEMSTRUCT` Struktur finden Sie unter [CWnd::OnMeasureItem.](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>Beispiel

Der folgende Code stammt aus dem MFC [CTRLTEST-Beispiel:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifyMenu

Ändert ein vorhandenes Menüelement an der von *nPosition*angegebenen Position .

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das zu ändernde Menüelement an. Der Parameter *nFlags* kann verwendet werden, um *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird, und gibt Informationen zu den Änderungen, die am Menüelement vorgenommen werden sollen. Eine Liste der Flags, die festgelegt werden können, finden Sie in der [Memberfunktion AppendMenu.](#appendmenu)

*nIDNewItem*<br/>
Gibt entweder die Befehls-ID des geänderten Menüelements oder, wenn *nFlags* auf MF_POPUP eingestellt ist, den Menühandle (HMENU) eines Popupmenüs an. Der Parameter *nIDNewItem* wird ignoriert (nicht benötigt), wenn *nFlags* auf MF_SEPARATOR festgelegt ist.

*lpszNewItem*<br/>
Gibt den Inhalt des neuen Menüelements an. Der Parameter *nFlags* kann verwendet werden, um *lpszNewItem* wie folgt zu interpretieren:

|nFlags|Interpretation von lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, den die Anwendung verwenden kann, um zusätzliche Daten zu verwalten, die dem Menüelement zugeordnet sind. Dieser 32-Bit-Wert steht der Anwendung bei der Verarbeiteten MF_MEASUREITEM und MF_DRAWITEM zur Verfügung.|
|MF_STRING|Enthält einen langen Zeiger auf eine null-terminierte Zeichenfolge oder auf eine `CString`.|
|MF_SEPARATOR|Der Parameter *lpszNewItem* wird ignoriert (nicht benötigt).|

*pBmp*<br/>
Zeigt auf `CBitmap` ein Objekt, das als Menüelement verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Anwendung gibt den neuen Status des Menüelements an, indem Werte in *nFlags*festgelegt werden. Wenn diese Funktion ein Popup-Menü ersetzt, das dem Menüpunkt zugeordnet ist, zerstört sie das alte Popupmenü und gibt den vom Popupmenü verwendeten Speicher frei.

Wenn *nIDNewItem* ein Popupmenü angibt, wird es Teil des Menüs, in das es eingefügt wird. Wenn dieses Menü zerstört wird, wird auch das eingefügte Menü zerstört. Ein eingefügtes Menü sollte `CMenu` von einem Objekt getrennt werden, um Konflikte zu vermeiden.

Jedes Mal, wenn ein Menü, das sich in einem Fenster befindet, `CWnd::DrawMenuBar`geändert wird (unabhängig davon, ob das Fenster angezeigt wird oder nicht), sollte die Anwendung aufrufen. Um die Attribute vorhandener Menüelemente zu ändern, `CheckMenuItem` ist `EnableMenuItem` es viel schneller, die und Memberfunktionen zu verwenden.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::operator HMENU

Verwenden Sie diesen Operator, `CMenu` um das Handle des Objekts abzurufen.

```
operator HMENU() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das `CMenu` Handle des Objekts; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Sie können das Handle verwenden, um Windows-APIs direkt aufzurufen.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::operator !=

Bestimmt, ob zwei Menüs logisch nicht gleich sind.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parameter

*Menü*<br/>
Ein `CMenu`-Objekt für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob ein Menüobjekt auf der linken Seite nicht gleich einem Menüobjekt auf der rechten Seite ist.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::operator ==

Bestimmt, ob zwei Menüs logisch gleich sind.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parameter

*Menü*<br/>
Ein `CMenu`-Objekt für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Testet, ob ein Menüobjekt auf der linken Seite (in Bezug auf den HMENU-Wert) gleich mit einem Menüobjekt auf der rechten Seite ist.

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::RemoveMenu

Löscht ein Menüelement mit einem zugeordneten Popupmenü aus dem Menü.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das zu entfernende Menüelement an. Der Parameter *nFlags* kann verwendet werden, um *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Es zerstört nicht das Handle für ein Popup-Menü, so dass das Menü wiederverwendet werden kann. Vor dem Aufruf dieser Funktion `GetSubMenu` kann die Anwendung die `CMenu` Memberfunktion aufrufen, um das Popupobjekt zur Wiederverwendung abzurufen.

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird `CWnd::DrawMenuBar`(unabhängig davon, ob das Fenster angezeigt wird oder nicht), muss die Anwendung aufrufen.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem

Legt das Standardmenüelement für das angegebene Menü fest.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uItem*<br/>
Bezeichner oder Position des neuen Standardmenüelements oder - 1 für kein Standardelement. Die Bedeutung dieses Parameters hängt vom Wert von *fByPos*ab.

*fByPos*<br/>
Wert, der die Bedeutung von *uItem*angibt. Wenn dieser Parameter FALSE ist, ist *uItem* ein Menüelementbezeichner. Andernfalls handelt es sich um eine Menüpunktposition.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null. Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, verwenden Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), wie im Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Funktion [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId

Ordnet eine Kontexthilfe-ID mit `CMenu`zu.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parameter

*dwContextHelpId*<br/>
Kontexthilfe-ID, `CMenu`die mit zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; sonst 0

### <a name="remarks"></a>Bemerkungen

Alle Elemente im Menü teilen diesen Bezeichner – es ist nicht möglich, den einzelnen Menüelementen einen Hilfekontextbezeichner anzufügen.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo

Legt Informationen für ein Menü fest.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parameter

*lpcmi*<br/>
Ein Zeiger auf eine [MENUINFO-Struktur,](/windows/win32/api/winuser/ns-winuser-menuinfo) die Informationen für das Menü enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null. Andernfalls ist der Rückgabewert Null.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um bestimmte Informationen über das Menü festzulegen.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps

Ordnet die angegebenen Bitmaps einem Menüelement zu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das zu ändernde Menüelement an. Der Parameter *nFlags* kann verwendet werden, um *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menüelements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der Parameter die Position des vorhandenen Menüelements angibt. Der erste Punkt befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird.

*pBmpUnchecked*<br/>
Gibt die Bitmap an, die für Nicht aktivierte Menüelemente verwendet werden soll.

*pBmpGeprüft*<br/>
Gibt die Bitmap an, die für aktivierte Menüelemente verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Unabhängig davon, ob das Menüelement aktiviert oder deaktiviert ist, zeigt Windows die entsprechende Bitmap neben dem Menüelement an.

Wenn *pBmpUnchecked* oder *pBmpChecked* NULL ist, zeigt Windows nichts neben dem Menüelement für das entsprechende Attribut an. Wenn beide Parameter NULL sind, verwendet Windows das Standardhäkchen, wenn das Element aktiviert ist, und entfernt das Häkchen, wenn das Element deaktiviert ist.

Wenn das Menü zerstört wird, werden diese Bitmaps nicht zerstört. die Anwendung muss sie zerstören.

Die `GetMenuCheckMarkDimensions` Windows-Funktion ruft die Dimensionen des Standardhäkchens ab, das für Menüelemente verwendet wird. Die Anwendung verwendet diese Werte, um die geeignete Größe für die mit dieser Funktion bereitgestellten Bitmaps zu bestimmen. Rufen Sie die Größe ab, erstellen Sie Ihre Bitmaps, und legen Sie sie dann fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo

Ändert Informationen zu einem Menüelement.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uItem*<br/>
Siehe Beschreibung von *uItem* in [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) im Windows SDK.

*lpMenuItemInfo*<br/>
Siehe Beschreibung von *lpmii* in `SetMenuItemInfo` im Windows SDK.

*fByPos*<br/>
Siehe Beschreibung von *fByPosition* in `SetMenuItemInfo` im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Diese Funktion umschließt [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), die im Windows SDK beschrieben wird.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu

Zeigt ein unverankertes Popupmenü an der angegebenen Position an und verfolgt die Auswahl der Elemente im Popupmenü.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parameter

*nFlags*<br/>
Gibt Bildschirmpositions- und Mauspositionsflags an. Eine Liste der verfügbaren Flags finden Sie unter [TrackPopupMenu.](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)

*X*<br/>
Gibt die horizontale Position in den Bildschirmkoordinaten des Popupmenüs an. Abhängig vom Wert des *nFlags-Parameters* kann das Menü linksbündig, rechtsbündig oder relativ zu dieser Position zentriert sein.

*y*<br/>
Gibt die vertikale Position in den Bildschirmkoordinaten am oberen Rand des Menüs auf dem Bildschirm an.

*pWnd*<br/>
Identifiziert das Fenster, das das Popupmenü besitzt. Dieser Parameter kann nicht NULL sein, auch wenn das TPM_NONOTIFY-Flag angegeben ist. Dieses Fenster empfängt alle WM_COMMAND Nachrichten aus dem Menü. In Windows-Versionen 3.1 und höher empfängt das `TrackPopupMenu` Fenster erst WM_COMMAND Nachrichten, wenn es zurückgegeben wird. In Windows 3.0 empfängt das `TrackPopupMenu` Fenster WM_COMMAND Nachrichten, bevor es zurückgegeben wird.

*lpRect*<br/>
Ignoriert.

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt das Ergebnis des Aufrufs von [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) im Windows SDK zurück.

### <a name="remarks"></a>Bemerkungen

Ein unverankertes Popupmenü kann an einer beliebigen Stelle auf dem Bildschirm angezeigt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx

Zeigt ein unverankertes Popupmenü an der angegebenen Position an und verfolgt die Auswahl der Elemente im Popupmenü.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Parameter

*fuFlags*<br/>
Gibt verschiedene Funktionen für das erweiterte Menü an. Eine Auflistung aller Werte und ihrer Bedeutung finden Sie unter [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*X*<br/>
Gibt die horizontale Position in den Bildschirmkoordinaten des Popupmenüs an.

*y*<br/>
Gibt die vertikale Position in den Bildschirmkoordinaten am oberen Rand des Menüs auf dem Bildschirm an.

*pWnd*<br/>
Ein Zeiger auf das Fenster, das das Popupmenü besitzt und die Nachrichten aus dem erstellten Menü empfängt. Dieses Fenster kann ein beliebiges Fenster aus der aktuellen Anwendung sein, aber nicht NULL sein. Wenn Sie TPM_NONOTIFY im Parameter *fuFlags* angeben, sendet die Funktion keine Nachrichten an *pWnd*. Die Funktion muss für das Fenster zurückgegeben werden, auf das *pWnd* zeigt, um die WM_COMMAND Nachricht zu empfangen.

*lptpm*<br/>
Zeiger auf eine [TPMPARAMS-Struktur,](/windows/win32/api/winuser/ns-winuser-tpmparams) die einen Bereich des Bildschirms angibt, sollte sich das Menü nicht überlappen. Dieser Parameter kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Wenn Sie TPM_RETURNCMD im *Parameter fuFlags* angeben, ist der Rückgabewert der Menüelementbezeichner des Elements, das der Benutzer ausgewählt hat. Wenn der Benutzer das Menü abbricht, ohne eine Auswahl zu treffen, oder wenn ein Fehler auftritt, ist der Rückgabewert 0.

Wenn Sie TPM_RETURNCMD im *Parameter fuFlags* nicht angeben, ist der Rückgabewert ungleich Null, wenn die Funktion erfolgreich ist, und 0, wenn sie fehlschlägt. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)an.

### <a name="remarks"></a>Bemerkungen

Ein unverankertes Popupmenü kann an einer beliebigen Stelle auf dem Bildschirm angezeigt werden. Weitere Informationen zur Behandlung von Fehlern beim Erstellen des Popupmenüs finden Sie unter [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
