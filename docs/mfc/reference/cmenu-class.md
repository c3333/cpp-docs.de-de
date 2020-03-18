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
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426240"
---
# <a name="cmenu-class"></a>CMenu-Klasse

Eine Kapselung von Windows- `HMENU`.

## <a name="syntax"></a>Syntax

```
class CMenu : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CMenu:: CMenu](#cmenu)|Erstellt ein `CMenu`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Fügt am Ende dieses Menüs ein neues Element an.|
|[CMenu:: Attach](#attach)|Fügt ein Windows-Menü Handle an ein `CMenu` Objekt an.|
|[CMenu:: checkmenuitem](#checkmenuitem)|Platziert ein Häkchen neben einem Menü Element im Popup Menü oder entfernt dieses.|
|[CMenu:: checkmenuradioitem](#checkmenuradioitem)|Platziert ein Optionsfeld neben einem Menü Element und entfernt das Optionsfeld aus allen anderen Menü Elementen in der Gruppe.|
|[CMenu:: kreatemenu](#createmenu)|Erstellt ein leeres Menü und fügt es an ein `CMenu` Objekt an.|
|[CMenu:: kreatepopupmenu](#createpopupmenu)|Erstellt ein leeres Popup Menü und fügt es an ein `CMenu` Objekt an.|
|[CMenu::D eletemenu](#deletemenu)|Löscht ein angegebenes Element aus dem Menü. Wenn das Menü Element über ein zugeordnetes Popup Menü verfügt, zerstört das Handle im Popup Menü und gibt den von ihm genutzten Arbeitsspeicher frei.|
|[CMenu::D eletetempmap](#deletetempmap)|Löscht alle temporären `CMenu`-Objekte, die von der `FromHandle` Member-Funktion erstellt wurden.|
|[CMenu::D estroymenu](#destroymenu)|Zerstört das an ein `CMenu` Objekt angefügte Menü und gibt den im Menü belegten Speicher frei.|
|[CMenu::D Etach](#detach)|Trennt ein Windows-Menü Handle von einem `CMenu`-Objekt und gibt das Handle zurück.|
|[CMenu::D rawitem](#drawitem)|Wird von Framework aufgerufen, wenn ein visueller Aspekt eines von einem Besitzer gezeichneten Menüs geändert wird.|
|[CMenu:: EnableMenuItem](#enablemenuitem)|Aktiviert, deaktiviert oder deaktiviert (gramt) ein Menü Element.|
|[CMenu:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CMenu` Objekt zurück, wenn ein Windows-Menü handle angegeben ist.|
|[CMenu:: getdefaultitem](#getdefaultitem)|Bestimmt das Standardmenü Element im angegebenen Menü.|
|[CMenu:: getmenucontexthelpid](#getmenucontexthelpid)|Ruft die dem Menü zugeordnete Hilfe Kontext-ID ab.|
|[CMenu:: getmenuinfo](#getmenuinfo)|Ruft Informationen über ein bestimmtes Menü ab.|
|[CMenu:: getmenuitemcount](#getmenuitemcount)|Bestimmt die Anzahl der Elemente in einem Popup-oder Menü der obersten Ebene.|
|[CMenu:: getmenuitemid](#getmenuitemid)|Ruft den Menü Element Bezeichner für ein Menü Element ab, das sich an der angegebenen Position befindet.|
|[CMenu:: getmenuiteminfo](#getmenuiteminfo)|Ruft Informationen zu einem Menü Element ab.|
|[CMenu:: getmenustate](#getmenustate)|Gibt den Status des angegebenen Menü Elements oder der Anzahl von Elementen in einem Popupmenü zurück.|
|[CMenu:: GetMenuString](#getmenustring)|Ruft die Bezeichnung des angegebenen Menü Elements ab.|
|[CMenu:: gezafehmenu](#getsafehmenu)|Gibt die `m_hMenu` zurück, die von diesem `CMenu` Objekt umschließt werden.|
|[CMenu:: getsubmenu](#getsubmenu)|Ruft einen Zeiger auf ein Popup Menü ab.|
|[CMenu::InsertMenu](#insertmenu)|Fügt ein neues Menü Element an der angegebenen Position ein und verschiebt andere Elemente im Menü.|
|[CMenu:: InsertMenuItem](#insertmenuitem)|Fügt ein neues Menü Element an der angegebenen Position in einem Menü ein.|
|[CMenu:: loadmenu](#loadmenu)|Lädt eine Menü Ressource aus der ausführbaren Datei und fügt Sie an ein `CMenu` Objekt an.|
|[CMenu:: loadmenuindirekte](#loadmenuindirect)|Lädt ein Menü aus einer Menüvorlage im Arbeitsspeicher und fügt es an ein `CMenu` Objekt an.|
|[CMenu:: MeasureItem](#measureitem)|Wird von Framework aufgerufen, um Menü Dimensionen zu ermitteln, wenn ein vom Besitzer gezeichnetes Menü erstellt wird.|
|[CMenu::ModifyMenu](#modifymenu)|Ändert ein vorhandenes Menü Element an der angegebenen Position.|
|[CMenu:: removemenu](#removemenu)|Löscht ein Menü Element mit einem zugeordneten Popup Menü aus dem angegebenen Menü.|
|[CMenu:: setdefaultitem](#setdefaultitem)|Legt das Standardmenü Element für das angegebene Menü fest.|
|[CMenu:: setmenucontexthelpid](#setmenucontexthelpid)|Legt die Hilfe Kontext-ID fest, die dem Menü zugeordnet werden soll.|
|[CMenu:: setmenuinfo](#setmenuinfo)|Legt Informationen über ein bestimmtes Menü fest.|
|[CMenu:: setmenuitembitmaps](#setmenuitembitmaps)|Ordnet die angegebenen Kontrollkästchen-Bitmaps einem Menü Element zu.|
|[CMenu:: setmenuiteminfo](#setmenuiteminfo)|Ändert Informationen zu einem Menü Element.|
|[CMenu:: TrackPopupMenu](#trackpopupmenu)|Zeigt ein unverankertes Popup Menü an der angegebenen Position an und verfolgt die Auswahl von Elementen im Popupmenü.|
|[CMenu:: TrackPopupMenuEx](#trackpopupmenuex)|Zeigt ein unverankertes Popup Menü an der angegebenen Position an und verfolgt die Auswahl von Elementen im Popupmenü.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CMenu:: Operator HMENU](#operator_hmenu)|Ruft das Handle des Menü Objekts ab.|
|[CMenu:: Operator! =](#operator_neq)|Bestimmt, ob zwei Menü Objekte nicht gleich sind.|
|[CMenu:: Operator = =](#operator_eq_eq)|Bestimmt, ob zwei Menü Objekte gleich sind.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CMenu:: m_hMenu](#m_hmenu)|Gibt das Handle für das Windows-Menü an, das an das `CMenu` Objekt angefügt ist.|

## <a name="remarks"></a>Hinweise

Er stellt Element Funktionen zum Erstellen, nachverfolgen, aktualisieren und zerstören eines Menüs bereit.

Erstellen Sie ein `CMenu` Objekt im Stapel Rahmen als Local, und rufen Sie dann die Member-Funktionen von `CMenu`auf, um das neue Menü nach Bedarf zu bearbeiten. Im nächsten Schritt wird [CWnd:: setMenu](../../mfc/reference/cwnd-class.md#setmenu) aufgerufen, um das Menü auf ein Fenster festzulegen, gefolgt von einem Aufrufen der [Trenn](#detach) Element Funktion des `CMenu` Objekts. Die `CWnd::SetMenu` Member-Funktion legt das Menü des Fensters auf das neue Menü fest, bewirkt, dass das Fenster neu gezeichnet wird, um die Menü Änderung widerzuspiegeln, und übergibt außerdem den Besitz des Menüs an das Fenster. Der-`Detach` trennt das HMENU vom `CMenu`-Objekt, sodass der `CMenu` objektdekonstruktor nicht versucht, ein Menü zu zerstören, das nicht mehr Besitzer ist, wenn die lokale `CMenu` Variable den Gültigkeitsbereich verlässt. Das Menü selbst wird automatisch zerstört, wenn das Fenster zerstört wird.

Mithilfe der [loadmenuindirekte](#loadmenuindirect) -Member-Funktion können Sie ein Menü aus einer Vorlage im Arbeitsspeicher erstellen, aber ein Menü, das von einer Ressource durch einen [loadmenu](#loadmenu) -Befehl erstellt wurde, wird leichter verwaltet, und die Menü Ressource selbst kann im Menü-Editor erstellt und geändert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="appendmenu"></a>CMenu:: AppendMenu

Fügt am Ende eines Menüs ein neues Element an.

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
Gibt Informationen zum Zustand des neuen Menü Elements an, wenn es dem Menü hinzugefügt wird. Sie besteht aus einem oder mehreren Werten, die im Abschnitt "Hinweise" aufgeführt sind.

*nidnetwitem*<br/>
Gibt entweder die Befehls-ID des neuen Menü Elements oder, wenn *nFlags* auf MF_POPUP festgelegt ist, das Menü handle (`HMENU`) eines Popup Menüs an. Der Parameter " *nidnetwitem* " wird ignoriert (nicht erforderlich), wenn " *nFlags* " auf "MF_SEPARATOR" festgelegt ist.

*lpsznetwitem*<br/>
Gibt den Inhalt des neuen Menü Elements an. Der *nFlags* -Parameter wird zur Interpretation von *lpsznetwitem* auf folgende Weise verwendet:

|nFlags|Interpretation von lpsznetwitem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, der von der Anwendung verwendet werden kann, um zusätzliche, dem Menü Element zugeordnete Daten zu verwalten. Dieser 32-Bit-Wert ist für die Anwendung verfügbar, wenn WM_MEASUREITEM und WM_DRAWITEM Meldungen verarbeitet werden. Der Wert wird im `itemData` Member der Struktur gespeichert, die mit diesen Meldungen bereitgestellt wird.|
|MF_STRING|Enthält einen Zeiger auf eine NULL-terminierte Zeichenfolge. Dies ist die Standardinterpretation.|
|MF_SEPARATOR|Der *lpsznetwitem* -Parameter wird ignoriert (nicht erforderlich).|

*pBmp*<br/>
Verweist auf ein `CBitmap` Objekt, das als Menü Element verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Die Anwendung kann den Zustand des Menü Elements angeben, indem Werte in *nFlags*festgelegt werden. Wenn " *nidnetwitem* " ein Popup Menü angibt, wird es Teil des Menüs, an das es angefügt wird. Wenn das Menü zerstört wird, wird das angefügte Menü ebenfalls zerstört. Ein angefügtes Menü sollte von einem `CMenu` Objekt getrennt werden, um Konflikte zu vermeiden. Beachten Sie, dass MF_STRING und MF_OWNERDRAW für die Bitmap-Version von `AppendMenu`nicht gültig sind.

In der folgenden Liste werden die Flags beschrieben, die in *nFlags*festgelegt werden können:

- MF_CHECKED fungiert als UMSCHALT Fläche, um das Standard Häkchen neben dem Element MF_UNCHECKED zu platzieren. Wenn die Anwendung Prüfzeichen-Bitmaps bereitstellt (siehe die Member-Funktion von [setmenuitembitmaps](#setmenuitembitmaps) ), wird die Bitmap "Häkchen für" angezeigt.

- MF_UNCHECKED fungiert als UMSCHALT Fläche mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen. Wenn die Anwendung Prüfzeichen-Bitmaps bereitstellt (siehe die `SetMenuItemBitmaps` Member-Funktion), wird die Bitmap "Häkchen" angezeigt.

- MF_DISABLED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, aber nicht.

- MF_ENABLED aktiviert das Menü Element, sodass es ausgewählt werden kann, und stellt es aus dem Abdichten Zustand wieder her.

- MF_GRAYED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, und abgeblendet.

- MF_MENUBARBREAK das Element in statischen Menüs oder in einer neuen Spalte in Popup Menüs in einer neuen Zeile platziert. Die neue Popup-Menü Spalte wird durch eine vertikale Trennlinie von der alten Spalte getrennt.

- MF_MENUBREAK das Element in statischen Menüs oder in einer neuen Spalte in Popup Menüs in einer neuen Zeile platziert. Zwischen den Spalten wird keine Trennlinie platziert.

- MF_OWNERDRAW gibt an, dass das Element ein Element ist, das vom Besitzer gezeichnet wird. Wenn das Menü zum ersten Mal angezeigt wird, empfängt das Fenster, das das Menü besitzt, eine WM_MEASUREITEM Nachricht, die die Höhe und Breite des Menü Elements abruft. Die WM_DRAWITEM Nachricht ist die Nachricht, die gesendet wird, wenn der Besitzer die visuelle Darstellung des Menü Elements aktualisieren muss. Diese Option ist für ein Menü Element der obersten Ebene ungültig.

- MF_POPUP gibt an, dass dem Menü Element ein Popup Menü zugeordnet ist. Der ID-Parameter gibt ein Handle für ein Popup Menü an, das dem Element zugeordnet werden soll. Diese Option wird zum Hinzufügen eines Popup Menüs der obersten Ebene oder eines hierarchischen Popup Menüs zu einem Popup Menü Element verwendet.

- MF_SEPARATOR zeichnet eine horizontale Trennlinie. Kann nur in einem Popupmenü verwendet werden. Diese Zeile kann nicht ausgeblendet, deaktiviert oder hervorgehoben werden. Andere Parameter werden ignoriert.

- MF_STRING gibt an, dass das Menü Element eine Zeichenfolge ist.

Jede der folgenden Gruppen listet Flags auf, die sich gegenseitig ausschließen und nicht gemeinsam verwendet werden können:

- MF_DISABLED, MF_ENABLED und MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR und die Bitmapversion

- MF_MENUBARBREAK und MF_MENUBREAK

- MF_CHECKED und MF_UNCHECKED

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird), sollte die Anwendung [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)abrufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: deatemenu](#createmenu).

##  <a name="attach"></a>CMenu:: Attach

Fügt ein vorhandenes Windows-Menü an ein `CMenu` Objekt an.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*HMENU*<br/>
Gibt ein Handle für ein Windows-Menü an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Vorgang erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion sollte nicht aufgerufen werden, wenn bereits ein Menü an das `CMenu` Objekt angefügt ist. Das Menü Handle wird im `m_hMenu` Datenmember gespeichert.

Wenn das Menü, das Sie bearbeiten möchten, bereits einem Fenster zugeordnet ist, können Sie die [CWnd:: getMenu](../../mfc/reference/cwnd-class.md#getmenu) -Funktion verwenden, um ein Handle für das Menü zu erhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu:: checkmenuitem

Fügt Häkchen aus Menü Elementen im Popupmenü hinzu oder entfernt Sie.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parameter

*nidcheckitem*<br/>
Gibt das zu überprüfende Menü Element an, das von *ncheck*bestimmt wird.

*nPrüfen*<br/>
Gibt an, wie das Menü Element überprüft wird und wie die Position des Elements im Menü bestimmt wird. Der *ncheck* -Parameter kann eine Kombination aus MF_CHECKED oder MF_UNCHECKED mit MF_BYPOSITION oder MF_BYCOMMAND Flags sein. Diese Flags können mit dem bitweisen OR-Operator kombiniert werden. Sie haben folgende Bedeutungen:

- MF_BYCOMMAND gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung.

- MF_BYPOSITION gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.

- MF_CHECKED fungiert als UMSCHALT Fläche, um das Standard Häkchen neben dem Element MF_UNCHECKED zu platzieren.

- MF_UNCHECKED fungiert als UMSCHALT Fläche mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen.

### <a name="return-value"></a>Rückgabewert

Der vorherige Zustand des Elements: MF_CHECKED oder MF_UNCHECKED oder 0xFFFFFFFF, wenn das Menü Element nicht vorhanden ist.

### <a name="remarks"></a>Hinweise

Der Parameter " *nidcheckitem* " gibt das zu ändernde Element an.

Mit dem Parameter " *nidcheckitem* " kann ein Popup-Menü Element und ein Menü Element identifiziert werden. Es sind keine speziellen Schritte erforderlich, um ein Popup Menü Element zu überprüfen. Menü Elemente der obersten Ebene können nicht geprüft werden. Ein Popup Menü Element muss anhand der Position überprüft werden, da ihm kein Menü Element Bezeichner zugeordnet ist.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: getmenustate](#getmenustate).

##  <a name="checkmenuradioitem"></a>CMenu:: checkmenuradioitem

Überprüft ein angegebenes Menü Element und legt es als Radio Element fest.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nidfirst*<br/>
Gibt das erste Menü Element in der Optionsfeld Gruppe an (als ID oder Offset, abhängig vom Wert von *nFlags*).

*nidlast*<br/>
Gibt das letzte Menü Element in der Optionsfeld Gruppe an (als ID oder Offset, abhängig vom Wert von *nFlags*).

*niditem*<br/>
Gibt das Element in der Gruppe an (ID oder Offset, abhängig vom Wert von *nFlags*), das mit einem Optionsfeld geprüft wird.

*nFlags*<br/>
Gibt die Interpretation von " *nidfirst*", " *nidlast*" und " *niditem* " wie folgt an:

|nFlags|Interpretation|
|------------|--------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; andernfalls 0

### <a name="remarks"></a>Hinweise

Gleichzeitig hebt die Funktion alle anderen Menü Elemente in der zugeordneten Gruppe auf und löscht das Flag für den Radio Elementtyp für diese Elemente. Das aktivierte Element wird mithilfe einer Optionsfeld-(oder Aufzählungs-) Bitmap anstelle einer Bitmap für das Häkchen angezeigt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>CMenu:: CMenu

Erstellt ein leeres Menü und fügt es an ein `CMenu` Objekt an.

```
CMenu();
```

### <a name="remarks"></a>Hinweise

Das Menü wird erst erstellt, wenn Sie eine der Funktionen zum Erstellen oder Laden eines Members von aufgerufen haben `CMenu:`

- ["Kreatemdeu"](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [Loadmenu](#loadmenu)

- [Loadmenuindirekte](#loadmenuindirect)

- [Anfügen](#attach)

##  <a name="createmenu"></a>CMenu:: kreatemenu

Erstellt ein Menü und fügt es an das `CMenu` Objekt an.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Menü erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Das Menü ist anfänglich leer. Menü Elemente können mithilfe der `AppendMenu`-oder `InsertMenu` Member-Funktion hinzugefügt werden.

Wenn das Menü einem Fenster zugewiesen ist, wird es automatisch zerstört, wenn das Fenster zerstört wird.

Vor dem beenden muss eine Anwendung Systemressourcen freigeben, die einem Menü zugeordnet sind, wenn das Menü keinem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü durch Aufrufen der [DestroyMenu](#destroymenu) -Member-Funktion frei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu:: kreatepopupmenu

Erstellt ein Popup Menü und fügt es an das `CMenu` Objekt an.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Popup Menü erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Das Menü ist anfänglich leer. Menü Elemente können mithilfe der `AppendMenu`-oder `InsertMenu` Member-Funktion hinzugefügt werden. Die Anwendung kann das Popup Menü einem vorhandenen Menü oder Popup Menü hinzufügen. Die `TrackPopupMenu` Member-Funktion kann verwendet werden, um dieses Menü als unverankertes Popup Menü anzuzeigen und die Auswahl im Popup Menü zu verfolgen.

Wenn das Menü einem Fenster zugewiesen ist, wird es automatisch zerstört, wenn das Fenster zerstört wird. Wenn das Menü einem vorhandenen Menü hinzugefügt wird, wird es automatisch zerstört, wenn das Menü zerstört wird.

Vor dem beenden muss eine Anwendung Systemressourcen freigeben, die einem Popupmenü zugeordnet sind, wenn das Menü keinem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü durch Aufrufen der [DestroyMenu](#destroymenu) -Member-Funktion frei.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: deatemenu](#createmenu).

##  <a name="deletemenu"></a>CMenu::D eletemenu

Löscht ein Element aus dem Menü.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das Menü Element an, das gelöscht werden soll, wie von *nFlags*festgelegt.

*nFlags*<br/>
Wird verwendet, um *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Wenn das Menü Element über ein zugeordnetes Popupmenü verfügt, `DeleteMenu` das Handle im Popup Menü zerstört und den vom Popup Menü verwendeten Arbeitsspeicher freigegeben.

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird), muss die Anwendung [CWnd::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)aufruft.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: getMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>CMenu::D eletetempmap

Wird automatisch vom `CWinApp` Leerlaufzeit Handler aufgerufen, löscht alle temporären `CMenu` Objekte, die von der [FromHandle](#fromhandle) -Member-Funktion erstellt wurden.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Hinweise

`DeleteTempMap` trennt das Windows-Menü Objekt, das an ein temporäres `CMenu` Objekt angefügt ist, bevor das `CMenu` Objekt gelöscht wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu::D estroymenu

Zerstört das Menü und alle verwendeten Windows-Ressourcen.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Menü zerstört wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Das Menü wird vom `CMenu` Objekt getrennt, bevor es zerstört wird. Die Windows `DestroyMenu`-Funktion wird automatisch im `CMenu` debugtor aufgerufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: deatemenu](#createmenu).

##  <a name="detach"></a>CMenu::D Etach

Trennt ein Windows-Menü von einem `CMenu`-Objekt und gibt das Handle zurück.

```
HMENU Detach();
```

### <a name="return-value"></a>Rückgabewert

Das Handle des Typs HMENU in ein Windows-Menü, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Der `m_hMenu` Datenmember ist auf NULL festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu::D rawitem

Wird von Framework aufgerufen, wenn ein visueller Aspekt eines von einem Besitzer gezeichneten Menüs geändert wird.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpdrawitemstruct*<br/>
Ein Zeiger auf eine [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) -Struktur, die Informationen über den erforderlichen Zeichentyp enthält.

### <a name="remarks"></a>Hinweise

Der `itemAction` Member der `DRAWITEMSTRUCT` Struktur definiert die auszuführende Zeichnungs Aktion. Überschreiben Sie diese Member-Funktion, um das Zeichnen für einen Besitzer `CMenu` Objekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface), die für den in *lpdrawitemstruct* angegebenen Anzeige Kontext ausgewählt wurden, vor der Beendigung dieser Element Funktion wiederherstellen.

Eine Beschreibung der `DRAWITEMSTRUCT` Struktur finden Sie unter [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

### <a name="example"></a>Beispiel

Der folgende Code wird aus dem MFC [CTRLTEST](../../overview/visual-cpp-samples.md) -Beispiel entnommen:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu:: EnableMenuItem

Aktiviert, deaktiviert oder deaktiviert ein Menü Element.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parameter

*nidenableitem*<br/>
Gibt das zu aktivierende Menü Element an, das von *nenable*bestimmt wird. Mit diesem Parameter können Popup Menü Elemente und Standardmenü Elemente angegeben werden.

*nenable*<br/>
Gibt die auszuführende Aktion an. Dabei kann es sich um eine Kombination aus MF_DISABLED, MF_ENABLED oder MF_GRAYED mit MF_BYCOMMAND oder MF_BYPOSITION handeln. Diese Werte können mit dem bitweisen OR-Operator kombiniert werden. Diese Werte haben die folgenden Bedeutungen:

- MF_BYCOMMAND gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung.

- MF_BYPOSITION gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.

- MF_DISABLED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, aber nicht.

- MF_ENABLED aktiviert das Menü Element, sodass es ausgewählt werden kann, und stellt es aus dem Abdichten Zustand wieder her.

- MF_GRAYED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, und abgeblendet.

### <a name="return-value"></a>Rückgabewert

Vorheriger Status (MF_DISABLED, MF_ENABLED oder MF_GRAYED) oder-1, falls ungültig.

### <a name="remarks"></a>Hinweise

Die Element Funktionen " [anatemenu](#createmenu)", " [InsertMenu](#insertmenu)", " [modifymenu](#modifymenu)" und " [loadmenuindirekte](#loadmenuindirect) " können auch den Zustand eines Menü Elements festlegen (aktiviert, deaktiviert oder ausgeblendet).

Die Verwendung des MF_BYPOSITION Werts erfordert, dass eine Anwendung die richtige `CMenu`verwendet. Wenn die `CMenu` der Menüleiste verwendet wird, ist ein Menü Element der obersten Ebene (ein Element in der Menüleiste) betroffen. Um den Zustand eines Elements in einem Popup-oder Popup Menü nach Position festzulegen, muss eine Anwendung den `CMenu` des Popup Menüs angeben.

Wenn eine Anwendung das MF_BYCOMMAND-Flag angibt, prüft Windows alle Popup-Menü Elemente, die der `CMenu`untergeordnet sind. Daher ist die Verwendung des `CMenu` der Menüleiste ausreichend, es sei denn, es sind doppelte Menü Elemente vorhanden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu:: FromHandle

Gibt einen Zeiger auf ein `CMenu` Objekt zurück, das ein Windows-Handle für ein Menü erhält.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*HMENU*<br/>
Ein Windows-Handle für ein Menü.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf einen `CMenu`, der temporär oder permanent sein kann.

### <a name="remarks"></a>Hinweise

Wenn ein `CMenu` Objekt noch nicht an das Windows-Menü Objekt angefügt ist, wird ein temporäres `CMenu` Objekt erstellt und angefügt.

Dieses temporäre `CMenu` Objekt ist erst gültig, wenn die Anwendung das nächste Mal in der Ereignisschleife eine Leerlaufzeit aufweist. zu diesem Zeitpunkt werden alle temporären Objekte gelöscht.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: deatemenu](#createmenu).

##  <a name="getdefaultitem"></a>CMenu:: getdefaultitem

Bestimmt das Standardmenü Element im angegebenen Menü.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*gmdiflags*<br/>
Ein Wert, der angibt, wie die Funktion nach Menü Elementen sucht. Dieser Parameter kann keine, eine oder eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Gibt an, dass die Funktion bei einem Standardelement, das ein Untermenü öffnet, im entsprechenden Untermenü rekursiv durchsucht werden soll. Wenn das Untermenü kein Standardelement aufweist, identifiziert der Rückgabewert das Element, das das Untermenü öffnet.<br /><br /> Standardmäßig gibt die-Funktion das erste Standardelement im angegebenen Menü zurück, unabhängig davon, ob es sich um ein Element handelt, das ein Untermenü öffnet.|
|GMDI_USEDISABLED|Gibt an, dass die Funktion ein Standardelement zurückgeben soll, auch wenn es deaktiviert ist.<br /><br /> Standardmäßig überspringt die Funktion deaktivierte oder ausgegraute Elemente.|

*"f"*<br/>
Ein Wert, der angibt, ob der Bezeichner des Menü Elements oder seine Position abgerufen werden soll. Wenn dieser Parameter false ist, wird der Bezeichner zurückgegeben. Andernfalls wird die Position zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert der Bezeichner oder die Position des Menü Elements. Wenn die Funktion fehlschlägt, ist der Rückgabewert-1.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Funktion [getmenudefaultitem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>CMenu:: getmenucontexthelpid

Ruft die Kontexthilfe-ID ab, die `CMenu`zugeordnet ist.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Rückgabewert

Die Kontexthilfe-ID, die derzeit `CMenu` zugeordnet ist, wenn Sie über eine verfügt. andernfalls NULL.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>CMenu:: getmenuinfo

Ruft Informationen für ein Menü ab.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parameter

*lpcmi*<br/>
Ein Zeiger auf eine [menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) -Struktur, die Informationen für das Menü enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null). Andernfalls ist der Rückgabewert 0 (null).

### <a name="remarks"></a>Hinweise

Rufen Sie diese Funktion auf, um Informationen über das Menü abzurufen.

##  <a name="getmenuitemcount"></a>CMenu:: getmenuitemcount

Bestimmt die Anzahl der Elemente in einem Popup-oder Menü der obersten Ebene.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Menü, wenn die Funktion erfolgreich ist. andernfalls-1.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CWnd:: getMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>CMenu:: getmenuitemid

Ruft den Menü Element Bezeichner für ein Menü Element ab, das sich an der durch *NPOs*definierten Position befindet.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Gibt die Position (null basiert) des Menü Elements an, dessen ID abgerufen wird.

### <a name="return-value"></a>Rückgabewert

Die Element-ID für das angegebene Element in einem Popup Menü, wenn die Funktion erfolgreich ausgeführt wurde. Wenn das angegebene Element ein Popup-Menü ist (im Gegensatz zu einem Element innerhalb des Popup Menüs), ist der Rückgabewert-1. Wenn *NPOs* einem Trenn Menü Element entsprechen, ist der Rückgabewert 0.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>CMenu:: getmenuiteminfo

Ruft Informationen zu einem Menü Element ab.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uitem*<br/>
Der Bezeichner oder die Position des Menü Elements, über das Informationen erhalten werden. Die Bedeutung dieses Parameters hängt vom Wert `ByPos`ab.

*lpmenuiteminfo*<br/>
Ein Zeiger auf ein [menuiteminfo](/windows/win32/api/winuser/ns-winuser-menuiteminfow)-Element, wie im Windows SDK beschrieben, das Informationen über das Menü enthält.

*"f"*<br/>
-Wert, der die Bedeutung von `nIDItem`angibt. Standardmäßig ist `ByPos` false. Dies bedeutet, dass uitem ein Bezeichner für den Menüeintrag ist. Wenn `ByPos` nicht auf false festgelegt ist, gibt es eine Position des Menü Elements an.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null). Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, verwenden Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), wie im Windows SDK beschrieben.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten des der Win32-Funktion [getmenuiteminfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), wie im Windows SDK beschrieben. Beachten Sie, dass Sie in der MFC-Implementierung von `GetMenuItemInfo`kein Handle für ein Menü verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu:: getmenustate

Gibt den Status des angegebenen Menü Elements oder der Anzahl von Elementen in einem Popupmenü zurück.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parameter

*NID*<br/>
Gibt die von *nFlags*festgelegte Menü Element-ID an.

*nFlags*<br/>
Gibt die Art *NID*an. Es kann sich um einen der folgenden Werte handeln:

- MF_BYCOMMAND gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung.

- MF_BYPOSITION gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.

### <a name="return-value"></a>Rückgabewert

Der Wert 0xFFFFFFFF, wenn das angegebene Element nicht vorhanden ist. Wenn *nId* ein Popup-Menü angibt, enthält das hochwertige Byte die Anzahl der Elemente im Popup Menü, und das nieder wertige Byte enthält die menüflags, die dem Popup Menü zugeordnet sind. Andernfalls ist der Rückgabewert eine Maske (boolescher Wert oder) der Werte aus der folgenden Liste (diese Maske beschreibt den Status des von *nId* identifizierten Menü Elements):

- MF_CHECKED fungiert als UMSCHALT Fläche, um das Standard Häkchen neben dem Element MF_UNCHECKED zu platzieren. Wenn die Anwendung Prüfzeichen-Bitmaps bereitstellt (siehe die `SetMenuItemBitmaps` Member-Funktion), wird die Bitmap "Häkchen für" angezeigt.

- MF_DISABLED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, aber nicht.

- MF_ENABLED aktiviert das Menü Element, sodass es ausgewählt werden kann, und stellt es aus dem Abdichten Zustand wieder her. Beachten Sie, dass der Wert dieser Konstante 0 ist. eine Anwendung sollte bei Verwendung dieses Werts nicht auf 0 testen.

- MF_GRAYED deaktiviert das Menü Element, sodass es nicht ausgewählt werden kann, und abgeblendet.

- MF_MENUBARBREAK das Element in statischen Menüs oder in einer neuen Spalte in Popup Menüs in einer neuen Zeile platziert. Die neue Popup-Menü Spalte wird durch eine vertikale Trennlinie von der alten Spalte getrennt.

- MF_MENUBREAK das Element in statischen Menüs oder in einer neuen Spalte in Popup Menüs in einer neuen Zeile platziert. Zwischen den Spalten wird keine Trennlinie platziert.

- MF_SEPARATOR zeichnet eine horizontale Trennlinie. Kann nur in einem Popupmenü verwendet werden. Diese Zeile kann nicht ausgeblendet, deaktiviert oder hervorgehoben werden. Andere Parameter werden ignoriert.

- MF_UNCHECKED fungiert als UMSCHALT Fläche mit MF_CHECKED, um ein Häkchen neben dem Element zu entfernen. Wenn die Anwendung Prüfzeichen-Bitmaps bereitstellt (siehe die `SetMenuItemBitmaps` Member-Funktion), wird die Bitmap "Häkchen" angezeigt. Beachten Sie, dass der Wert dieser Konstante 0 ist. eine Anwendung sollte bei Verwendung dieses Werts nicht auf 0 testen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu:: GetMenuString

Kopiert die Bezeichnung des angegebenen Menü Elements in den angegebenen Puffer.

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

*niditem*<br/>
Gibt abhängig vom Wert von *nFlags*den ganzzahligen Bezeichner des Menü Elements oder den Offset des Menü Elements im Menü an.

*LpString*<br/>
Zeigt auf den Puffer, der die Bezeichnung empfangen soll.

*RString*<br/>
Ein Verweis auf ein `CString` Objekt, das die kopierte Menü Zeichenfolge empfangen soll.

*nMaxCount*<br/>
Gibt die maximale Länge (in Zeichen) der zu kopierenden Bezeichnung an. Wenn die Bezeichnung länger als der in *nMaxCount*angegebene Höchstwert ist, werden die zusätzlichen Zeichen abgeschnitten.

*nFlags*<br/>
Gibt die Interpretation des *niditem* -Parameters an. Es kann sich um einen der folgenden Werte handeln:

|nFlags|Interpretation von niditem|
|------------|-------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

### <a name="return-value"></a>Rückgabewert

Gibt die tatsächliche Anzahl von Zeichen an, die in den Puffer kopiert werden, ohne das NULL-Terminator.

### <a name="remarks"></a>Hinweise

Der *nMaxCount* -Parameter muss größer als die Anzahl der Zeichen in der Bezeichnung sein, um das NULL-Zeichen zu berücksichtigen, das eine Zeichenfolge beendet.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>CMenu:: gezafehmenu

Gibt das von diesem `CMenu` Objekt umschließende HMENU oder einen NULL-`CMenu` Zeiger zurück.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: loadmenu](#loadmenu).

##  <a name="getsubmenu"></a>CMenu:: getsubmenu

Ruft das `CMenu`-Objekt eines Popup Menüs ab.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Gibt die Position des Popup Menüs an, das im Menü enthalten ist. Positionswerte beginnen bei 0 für das erste Menü Element. Der Bezeichner des Popup Menüs kann in dieser Funktion nicht verwendet werden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CMenu` Objekt, dessen `m_hMenu` Member ein Handle für das Popup Menü enthält, wenn ein Popup Menü an der angegebenen Position vorhanden ist. andernfalls NULL. Wenn kein `CMenu` Objekt vorhanden ist, wird ein temporäres Objekt erstellt. Der zurückgegebene `CMenu` Zeiger darf nicht gespeichert werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>CMenu:: InsertMenu

Fügt ein neues Menü Element an der durch *nPosition* angegebenen Position ein und verschiebt andere Elemente im Menü.

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
Gibt das Menü Element an, vor dem das neue Menü Element eingefügt werden soll. Der *nFlags* -Parameter kann verwendet werden, um die *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0. Wenn *nPosition* -1 ist, wird das neue Menü Element am Ende des Menüs angefügt.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird, und gibt Informationen zum Zustand des neuen Menü Elements an, wenn es dem Menü hinzugefügt wird. Eine Liste der Flags, die festgelegt werden können, finden Sie unter der [AppendMenu](#appendmenu) -Member-Funktion. Wenn Sie mehr als einen Wert angeben möchten, verwenden Sie den bitweisen OR-Operator, um Sie mit dem MF_BYCOMMAND oder MF_BYPOSITION-Flag zu kombinieren.

*nidnetwitem*<br/>
Gibt entweder die Befehls-ID des neuen Menü Elements oder, wenn *nFlags* auf MF_POPUP festgelegt ist, das Menü handle (HMENU) des Popup Menüs an. Der Parameter " *nidnetwitem* " wird ignoriert (nicht erforderlich), wenn " *nFlags* " auf "MF_SEPARATOR" festgelegt ist.

*lpsznetwitem*<br/>
Gibt den Inhalt des neuen Menü Elements an. *nFlags* können zur Interpretation von *lpsznetwitem* auf folgende Weise verwendet werden:

|nFlags|Interpretation von lpsznetwitem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, der von der Anwendung verwendet werden kann, um zusätzliche, dem Menü Element zugeordnete Daten zu verwalten. Dieser 32-Bit-Wert ist für die Anwendung in der `itemData`-Member der-Struktur verfügbar, die von den [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) -und [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) -Meldungen bereitgestellt wird. Diese Nachrichten werden gesendet, wenn das Menü Element anfänglich angezeigt oder geändert wird.|
|MF_STRING|Enthält einen Long-Zeiger auf eine NULL-terminierte Zeichenfolge. Dies ist die Standardinterpretation.|
|MF_SEPARATOR|Der *lpsznetwitem* -Parameter wird ignoriert (nicht erforderlich).|

*pBmp*<br/>
Verweist auf ein `CBitmap` Objekt, das als Menü Element verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Die Anwendung kann den Zustand des Menü Elements angeben, indem Werte in *nFlags*festgelegt werden.

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird), sollte die Anwendung `CWnd::DrawMenuBar`abrufen.

Wenn " *nidnetwitem* " ein Popupmenü angibt, wird es zu einem Teil des Menüs, in dem Sie eingefügt wird. Wenn das Menü zerstört wird, wird auch das eingefügte Menü zerstört. Ein eingefügtes Menü muss von einem `CMenu` Objekt getrennt werden, um Konflikte zu vermeiden.

Wenn das untergeordnete MDI (Multiple Document Interface)-Fenster maximiert ist und eine Anwendung im Menü der MDI-Anwendung ein Popupmenü einfügt, indem Sie diese Funktion aufrufen und das MF_BYPOSITION-Flag angibt, wird das Menü an einer anderen Position weiter Links eingefügt als erwartet. Dies liegt daran, dass das Steuerelement Menü des aktiven untergeordneten MDI-Fensters an der ersten Position der Menüleiste des MDI-Frame Fensters eingefügt wird. Um das Menü ordnungsgemäß zu positionieren, muss die Anwendung 1 dem Positionswert hinzufügen, der andernfalls verwendet würde. Eine Anwendung kann mithilfe der WM_MDIGETACTIVE Meldung feststellen, ob das momentan aktive untergeordnete Fenster maximiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu:: InsertMenuItem

Fügt ein neues Menü Element an der angegebenen Position in einem Menü ein.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uitem*<br/>
Weitere Informationen finden Sie in der Beschreibung von *uitem* in [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) in der Windows SDK.

*lpmenuiteminfo*<br/>
Weitere Informationen finden Sie unter Beschreibung von *lpmii* in `InsertMenuItem` im Windows SDK.

*"f"*<br/>
Weitere Informationen finden Sie in der Beschreibung von " *f-Position* " in `InsertMenuItem` im Windows SDK.

### <a name="remarks"></a>Hinweise

Diese Funktion umschließt [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), das in der Windows SDK beschrieben wird.

##  <a name="loadmenu"></a>CMenu:: loadmenu

Lädt eine Menü Ressource aus der ausführbaren Datei der Anwendung und fügt Sie an das `CMenu`-Objekt an.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszresourcename*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Namen der zu ladenden Menü Ressource enthält.

*nidresource*<br/>
Gibt die Menü-ID der zu ladenden Menü Ressource an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Menü Ressource erfolgreich geladen wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Vor dem beenden muss eine Anwendung Systemressourcen freigeben, die einem Menü zugeordnet sind, wenn das Menü keinem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü durch Aufrufen der [DestroyMenu](#destroymenu) -Member-Funktion frei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu:: loadmenuindirekte

Lädt eine Ressource aus einer Menüvorlage im Arbeitsspeicher und fügt Sie an das `CMenu` Objekt an.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parameter

*lpmenutemplate*<br/>
Verweist auf eine Menüvorlage (eine einzelne [menuitemtemplateheader](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) -Struktur und eine Auflistung von einer oder mehreren [menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) -Strukturen). Weitere Informationen zu diesen beiden Strukturen finden Sie in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Menü Ressource erfolgreich geladen wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Eine Menüvorlage ist eine Kopfzeile, auf die eine Auflistung von einer oder mehreren [menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) -Strukturen folgt, die jeweils ein oder mehrere Menü Elemente und Popup Menüs enthalten können.

Die Versionsnummer muss 0 sein.

Die `mtOption` Flags sollten MF_END für das letzte Element in einer Popup Liste und für das letzte Element in der Hauptliste enthalten. Weitere Informationen finden Sie unter `AppendMenu` Member-Funktion. Der `mtId` Member muss in der menuitemtemplate-Struktur ausgelassen werden, wenn MF_POPUP in `mtOption`angegeben wird.

Der für die menuitemtemplate-Struktur zugewiesene Speicherplatz muss groß genug sein, damit `mtString` den Namen des Menü Elements als eine auf NULL endende Zeichenfolge enthält.

Vor dem beenden muss eine Anwendung Systemressourcen freigeben, die einem Menü zugeordnet sind, wenn das Menü keinem Fenster zugewiesen ist. Eine Anwendung gibt ein Menü durch Aufrufen der [DestroyMenu](#destroymenu) -Member-Funktion frei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu:: m_hMenu

Gibt das HMENU-Handle des Windows-Menüs an, das an das `CMenu` Objekt angefügt ist.

```
HMENU m_hMenu;
```

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: loadmenu](#loadmenu).

##  <a name="measureitem"></a>CMenu:: MeasureItem

Wird von Framework aufgerufen, wenn ein Menü mit der Art des Besitzer Zeichnens erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameter

*lpmeasureitemstruct*<br/>
Ein Zeiger auf eine `MEASUREITEMSTRUCT`-Struktur.

### <a name="remarks"></a>Hinweise

Standardmäßig führt diese Member-Funktion keine Aktion aus. Überschreiben Sie diese Member-Funktion, und füllen Sie die `MEASUREITEMSTRUCT` Struktur aus, um Fenster über die Dimensionen des Menüs zu informieren.

Eine Beschreibung der `MEASUREITEMSTRUCT` Struktur finden Sie unter [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Beispiel

Der folgende Code wird aus dem MFC [CTRLTEST](../../overview/visual-cpp-samples.md) -Beispiel entnommen:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu:: modifymenu

Ändert ein vorhandenes Menü Element an der durch *nPosition*angegebenen Position.

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
Gibt das zu ändernde Menü Element an. Der *nFlags* -Parameter kann verwendet werden, um die *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird und enthält Informationen zu den Änderungen, die an dem Menü Element vorgenommen werden. Eine Liste der Flags, die festgelegt werden können, finden Sie unter der [AppendMenu](#appendmenu) -Member-Funktion.

*nidnetwitem*<br/>
Gibt entweder die Befehls-ID des geänderten Menü Elements oder, wenn *nFlags* auf MF_POPUP festgelegt ist, das Menü handle (HMENU) eines Popup Menüs an. Der Parameter " *nidnetwitem* " wird ignoriert (nicht erforderlich), wenn " *nFlags* " auf "MF_SEPARATOR" festgelegt ist.

*lpsznetwitem*<br/>
Gibt den Inhalt des neuen Menü Elements an. Der *nFlags* -Parameter kann zum Interpretieren von *lpsznetwitem* auf folgende Weise verwendet werden:

|nFlags|Interpretation von lpsznetwitem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Enthält einen von der Anwendung bereitgestellten 32-Bit-Wert, der von der Anwendung verwendet werden kann, um zusätzliche, dem Menü Element zugeordnete Daten zu verwalten. Dieser 32-Bit-Wert ist für die Anwendung verfügbar, wenn Sie MF_MEASUREITEM und MF_DRAWITEM verarbeitet.|
|MF_STRING|Enthält einen langen Zeiger auf eine NULL-terminierte Zeichenfolge oder auf eine `CString`.|
|MF_SEPARATOR|Der *lpsznetwitem* -Parameter wird ignoriert (nicht erforderlich).|

*pBmp*<br/>
Verweist auf ein `CBitmap` Objekt, das als Menü Element verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Die Anwendung gibt den neuen Zustand des Menü Elements an, indem Werte in *nFlags*festgelegt werden. Wenn diese Funktion ein Popupmenü ersetzt, das dem Menü Element zugeordnet ist, wird das alte Popup Menü zerstört, und der vom Popup Menü verwendete Arbeitsspeicher wird freigegeben.

Wenn " *nidnetwitem* " ein Popupmenü angibt, wird es zu einem Teil des Menüs, in dem Sie eingefügt wird. Wenn das Menü zerstört wird, wird auch das eingefügte Menü zerstört. Ein eingefügtes Menü muss von einem `CMenu` Objekt getrennt werden, um Konflikte zu vermeiden.

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird), sollte die Anwendung `CWnd::DrawMenuBar`abrufen. Um die Attribute vorhandener Menü Elemente zu ändern, ist es viel schneller, die `CheckMenuItem`-und `EnableMenuItem` Member-Funktionen zu verwenden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>CMenu:: Operator HMENU

Verwenden Sie diesen Operator, um das Handle des `CMenu` Objekts abzurufen.

```
operator HMENU() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle des `CMenu` Objekts. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Sie können das Handle verwenden, um Windows-APIs direkt aufzurufen.

##  <a name="operator_neq"></a>CMenu:: Operator! =

Bestimmt, ob zwei Menüs logisch nicht gleich sind.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parameter

*stehen*<br/>
Ein `CMenu`-Objekt für den Vergleich.

### <a name="remarks"></a>Hinweise

Testet, ob ein Menü Objekt auf der linken Seite nicht gleich einem Menü Objekt auf der rechten Seite ist.

##  <a name="operator_eq_eq"></a>CMenu:: Operator = =

Bestimmt, ob zwei Menüs logisch gleich sind.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parameter

*stehen*<br/>
Ein `CMenu`-Objekt für den Vergleich.

### <a name="remarks"></a>Hinweise

Testet, ob ein Menü Objekt auf der linken Seite mit einem Menü Objekt auf der rechten Seite gleich (im Hinblick auf den HMENU-Wert) ist.

##  <a name="removemenu"></a>CMenu:: removemenu

Löscht ein Menü Element mit einem zugeordneten Popup Menü aus dem Menü.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das zu entfernende Menü Element an. Der *nFlags* -Parameter kann verwendet werden, um die *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Dadurch wird das Handle für ein Popup Menü nicht zerstört, sodass das Menü wieder verwendet werden kann. Vor dem Aufrufen dieser Funktion kann die Anwendung die `GetSubMenu` Member-Funktion aufrufen, um das Popup `CMenu` Objekt für die Wiederverwendung abzurufen.

Wenn ein Menü, das sich in einem Fenster befindet, geändert wird (unabhängig davon, ob das Fenster angezeigt wird), muss die Anwendung `CWnd::DrawMenuBar`aufgerufen werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>CMenu:: setdefaultitem

Legt das Standardmenü Element für das angegebene Menü fest.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uitem*<br/>
Der Bezeichner oder die Position des neuen Standardmenü Elements oder-1 für kein Standardelement. Die Bedeutung dieses Parameters hängt vom Wert von " *f*" ab.

*"f"*<br/>
Ein-Wert, der die Bedeutung von *uitem*angibt. Wenn dieser Parameter false ist, ist *uitem* ein Bezeichner für den Menüeintrag. Andernfalls handelt es sich um eine Position des Menü Elements.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null). Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, verwenden Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), wie im Windows SDK beschrieben.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Funktion [setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>CMenu:: setmenucontexthelpid

Ordnet `CMenu`eine Kontexthilfe-ID zu.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parameter

*dwcontexthelpid*<br/>
Die Kontexthilfe-ID, die `CMenu`zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; andernfalls 0

### <a name="remarks"></a>Hinweise

Alle Elemente im Menü geben diesen Bezeichner frei – es ist nicht möglich, einen Hilfe Kontext Bezeichner an die einzelnen Menü Elemente anzufügen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMenu:: InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>CMenu:: setmenuinfo

Legt Informationen für ein Menü fest.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parameter

*lpcmi*<br/>
Ein Zeiger auf eine [menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) -Struktur, die Informationen für das Menü enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null). Andernfalls ist der Rückgabewert 0 (null).

### <a name="remarks"></a>Hinweise

Diese Funktion wird aufgerufen, um bestimmte Informationen über das Menü festzulegen.

##  <a name="setmenuitembitmaps"></a>CMenu:: setmenuitembitmaps

Ordnet die angegebenen Bitmaps einem Menü Element zu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parameter

*nPosition*<br/>
Gibt das zu ändernde Menü Element an. Der *nFlags* -Parameter kann verwendet werden, um die *nPosition* auf folgende Weise zu interpretieren:

|nFlags|Interpretation von nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Gibt an, dass der Parameter die Befehls-ID des vorhandenen Menü Elements angibt. Dies ist die Standardeinstellung, wenn weder MF_BYCOMMAND noch MF_BYPOSITION festgelegt ist.|
|MF_BYPOSITION|Gibt an, dass der-Parameter die Position des vorhandenen Menü Elements angibt. Das erste Element befindet sich an Position 0.|

*nFlags*<br/>
Gibt an, wie *nPosition* interpretiert wird.

*pbmpdeaktiviert*<br/>
Gibt die Bitmap an, die für nicht überprüfte Menü Elemente verwendet werden soll.

*pbmpcheck*<br/>
Gibt die Bitmap an, die für aktivierte Menü Elemente verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Unabhängig davon, ob das Menü Element aktiviert oder deaktiviert ist, zeigt Windows die entsprechende Bitmap neben dem Menü Element an.

Wenn *pbmpdeaktiviert* oder *pbmpcheck* NULL ist, zeigt Windows nichts neben dem Menü Element für das entsprechende Attribut an. Wenn beide Parameter NULL sind, verwendet Windows beim Aktivieren des Elements das Standard Häkchen und entfernt das Häkchen, wenn das Element deaktiviert ist.

Wenn das Menü zerstört wird, werden diese Bitmaps nicht zerstört. die Anwendung muss Sie zerstören.

Die Windows `GetMenuCheckMarkDimensions`-Funktion Ruft die Dimensionen des Standard Häkchens ab, das für Menü Elemente verwendet wird. Die Anwendung verwendet diese Werte, um die geeignete Größe für die mit dieser Funktion bereitgestellten Bitmaps zu ermitteln. Rufen Sie die Größe ab, erstellen Sie die Bitmaps, und legen Sie Sie dann fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu:: setmenuiteminfo

Ändert Informationen zu einem Menü Element.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parameter

*uitem*<br/>
Weitere Informationen finden Sie in der Beschreibung von *uitem* in [setmenuiteminfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) im Windows SDK.

*lpmenuiteminfo*<br/>
Weitere Informationen finden Sie unter Beschreibung von *lpmii* in `SetMenuItemInfo` im Windows SDK.

*"f"*<br/>
Weitere Informationen finden Sie in der Beschreibung von " *f-Position* " in `SetMenuItemInfo` im Windows SDK.

### <a name="remarks"></a>Hinweise

Diese Funktion umschließt [setmenuiteminfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), das in der Windows SDK beschrieben wird.

##  <a name="trackpopupmenu"></a>CMenu:: TrackPopupMenu

Zeigt ein unverankertes Popup Menü an der angegebenen Position an und verfolgt die Auswahl von Elementen im Popupmenü.

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
Gibt die Bildschirmposition und die Flags für die Mausposition an. Eine Liste der verfügbaren Flags finden Sie unter [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) .

*x*<br/>
Gibt die horizontale Position in Bildschirm Koordinaten des Popup Menüs an. Abhängig vom Wert des *nFlags* -Parameters kann das Menü linksbündig ausgerichtet, rechtsbündig ausgerichtet oder relativ zu dieser Position zentriert werden.

*y*<br/>
Gibt die vertikale Position in Bildschirm Koordinaten des oberen Rands des Menüs auf dem Bildschirm an.

*folgenden*<br/>
Identifiziert das Fenster, das das Popup Menü besitzt. Dieser Parameter darf nicht NULL sein, auch wenn das TPM_NONOTIFY-Flag angegeben wird. In diesem Fenster werden alle WM_COMMAND Meldungen aus dem Menü empfangen. In Windows, Version 3,1 und höher, empfängt das Fenster WM_COMMAND Nachrichten erst, wenn `TrackPopupMenu` zurückgibt. In Windows 3,0 empfängt das Fenster WM_COMMAND Meldungen, bevor `TrackPopupMenu` zurückgibt.

*lprect*<br/>
Ignoriert.

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt das Ergebnis des Aufrufs von [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) in der Windows SDK zurück.

### <a name="remarks"></a>Hinweise

Ein unverankertes Popup Menü kann an beliebiger Stelle auf dem Bildschirm angezeigt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu:: TrackPopupMenuEx

Zeigt ein unverankertes Popup Menü an der angegebenen Position an und verfolgt die Auswahl von Elementen im Popupmenü.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Parameter

*fuflags*<br/>
Gibt verschiedene Funktionen für das erweiterte Menü an. Eine Auflistung aller Werte und ihrer Bedeutung finden Sie unter [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Gibt die horizontale Position in Bildschirm Koordinaten des Popup Menüs an.

*y*<br/>
Gibt die vertikale Position in Bildschirm Koordinaten des oberen Rands des Menüs auf dem Bildschirm an.

*folgenden*<br/>
Ein Zeiger auf das Fenster, das das Popup Menü besitzt und die Meldungen aus dem erstellten Menü empfängt. Bei diesem Fenster kann es sich um ein beliebiges Fenster der aktuellen Anwendung, aber nicht um NULL handeln. Wenn Sie TPM_NONOTIFY im *fuflags* -Parameter angeben, sendet die Funktion keine Nachrichten an *pwnd*. Die Funktion muss für das Fenster zurückgeben, auf das von *pwnd* verwiesen wird, um die WM_COMMAND Nachricht zu empfangen.

*lptpm*<br/>
Ein Zeiger auf eine [tpmparameams](/windows/win32/api/winuser/ns-winuser-tpmparams) -Struktur, die einen Bereich des Bildschirms angibt, überlappen sich das Menü nicht. Dieser Parameter kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Wenn Sie TPM_RETURNCMD im *fuflags* -Parameter angeben, ist der Rückgabewert der Menü Element Bezeichner des Elements, das der Benutzer ausgewählt hat. Wenn der Benutzer das Menü abbricht, ohne eine Auswahl vorzunehmen, oder wenn ein Fehler auftritt, ist der Rückgabewert 0.

Wenn Sie TPM_RETURNCMD im *fuflags* -Parameter nicht angeben, ist der Rückgabewert ungleich 0 (null), wenn die Funktion erfolgreich ausgeführt wird, und 0, wenn ein Fehler auftritt. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Hinweise

Ein unverankertes Popup Menü kann an beliebiger Stelle auf dem Bildschirm angezeigt werden. Weitere Informationen zum Behandeln von Fehlern beim Erstellen des Popup Menüs finden Sie unter [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
