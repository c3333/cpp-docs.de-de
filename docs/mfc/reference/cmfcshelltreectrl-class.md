---
title: CMFCShellTreeCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 41d9a14e379c566f001eda8b10b2669b95beb171
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376139"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl-Klasse

Die `CMFCShellTreeCtrl` Klasse erweitert die Funktionalität der [CTreeCtrl-Klasse,](../../mfc/reference/ctreectrl-class.md) indem eine Hierarchie von Shell-Elementen angezeigt wird.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Aktiviert oder deaktiviert das Kontextmenü.|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|Gibt eine Kombination von Flags zurück, die an [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)übergeben werden.|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|Ruft den Pfad zu einem Element ab.|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|Gibt einen Zeiger auf das [CMFCShellListCtrl-Klassenobjekt](../../mfc/reference/cmfcshelllistctrl-class.md) `CMFCShellTreeCtrl` zurück, das zusammen mit diesem Objekt zum Erstellen eines Explorer-ähnlichen Fensters verwendet wird.|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|Diese Memberfunktion wird vom übergeordneten Fenster dieses Fensters aufgerufen, wenn sie eine Benachrichtigung erhält, die für dieses Fenster gilt. (Überschreibt [CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Aktualisieren](#refresh)|Aktualisiert und zeichnet das `CMFCShellTreeCtrl` aktuelle Objekt neu.|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|Wählt das entsprechende Struktursteuerelement element basierend auf einem bereitgestellten PIDL- oder Zeichenfolgenpfad aus.|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|Legt Flags fest, um den Strukturkontext `IShellFolder::EnumObjects`zu filtern (ähnlich den von verwendeten Flags ).|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|Legt eine Beziehung `CMFCShellTreeCtrl` zwischen dem `CMFCShellListCtrl` aktuellen Objekt und einem Objekt fest.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse erweitert `CTreeCtrl` die Klasse, indem es dem Programm ermöglicht, Windows Shell-Elemente in die Struktur aufzunehmen. Diese Klasse kann einem `CMFCShellListCtrl` Objekt zugeordnet werden, um ein vollständiges Explorer-Fenster zu erstellen. Wenn Sie dann ein Element in der Struktur auswählen, wird eine Liste der Windows-Shell-Elemente in der zugeordneten Liste angezeigt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxshelltreeCtrl.h

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie ein Objekt der `CMFCShellTreeCtrl`-Klasse erstellt wird. Dieser Codeausschnitt ist Teil des [Explorer-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

Aktiviert das Kontextmenü.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Ein boolescher Wert, der angibt, ob das Kontextmenü aktiviert werden soll.

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::GetFlags

Gibt die für das [CMFCShellTreeCtrl-Klassenobjekt](../../mfc/reference/cmfcshelltreectrl-class.md) festgelegten Flags zurück.

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die Kombination der aktuell festgelegten Flags angibt.

### <a name="remarks"></a>Bemerkungen

Die in der `CMFCShellTreeCtrl` festgelegten Flags werden an die Methode [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) gesendet, wenn das Objekt aktualisiert wird. Sie können die Flags mit der [CMFCShellTreeCtrl::SetFlags-Methode](#setflags) ändern.

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

Ruft den Pfad eines Elements im [CMFCShellTreeCtrl-Klassenobjekt](../../mfc/reference/cmfcshelltreectrl-class.md) ab.

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>Parameter

*strPath*<br/>
[out] Ein Verweis auf einen Zeichenfolgenparameter. Die Methode schreibt den Pfad des Elements in diesen Parameter.

*htreeItem*<br/>
[in] Die Methode ruft den Pfad für dieses Struktursteuerelement ab.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0 sonst.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode fehlschlägt, enthält *strPath* die leere Zeichenfolge.

Wenn Sie *hTreeItem*nicht angeben, versucht diese Methode, die Zeichenfolge für das aktuell ausgewählte Element abzusuchen. Wenn kein Element ausgewählt ist und *hTreeItem* NULL ist, schlägt diese Methode fehl.

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

Gibt einen Zeiger auf das [CMFCShellListCtrl-Klassenobjekt](../../mfc/reference/cmfcshelllistctrl-class.md) zurück, das diesem [CMFCShellTreeCtrl-Objekt](../../mfc/reference/cmfcshelltreectrl-class.md) zugeordnet ist.

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CMFCShellListCtrl` das Objekt, das diesem Struktursteuerelementobjekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Wenn Sie `CMFCShellListCtrl` ein Objekt `CMFCShellTreeCtrl` zusammen mit einem Objekt verwenden, können Sie ein Explorer-ähnliches Fenster erstellen. Verwenden Sie die Methode [CMFCShellTreeCtrl::SetRelatedList,](#setrelatedlist) um die beiden Klassen zuzuordnen. Nachdem sie zugeordnet wurden, aktualisiert `CMFCShellListCtrl` das Framework `CMFCShellTreeCtrl` automatisch die, wenn die Auswahl in den Änderungen.

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>Parameter

[in] *Nachricht*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>Parameter

[in] *pItem*<br/>
[in] *bAusgewählt*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parameter

[in] *pItem*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFCShellTreeCtrl::Aktualisieren

Aktualisiert und zeichnet die [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)neu.

```
void Refresh();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um `CMFCShellTreeCtrl`die Hierarchie der elemente zu aktualisieren, die im angezeigt werden.

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

Wählt ein Element in der [CMFCShellTreeCtrl-Klasse](../../mfc/reference/cmfcshelltreectrl-class.md) basierend auf dem angegebenen Pfad aus.

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>Parameter

*lpszPath*<br/>
[in] Eine Zeichenfolge, die den Pfad eines Elements angibt.

*lpidl*<br/>
[in] Eine PIDL, die das Element angibt

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; E_FAIL sonst.

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

Legt Flags fest, um den Strukturkontext zu filtern.

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
[in] Die zu setzenden Flags.

*bRefresh*<br/>
[in] Ein boolescher Wert, `CMFCShellTreeCtrl` der angibt, ob der sofort aktualisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Die `CMFCShellTreeCtrl` übergibt alle set flags an [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects). Weitere Informationen zu den Werten verschiedener Flags finden Sie unter [IShellFolder::EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects).

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

Ordnet ein [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) einem [CMFCShellTreeCtrl-Objekt](../../mfc/reference/cmfcshelltreectrl-class.md) zu.

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>Parameter

*pShellList*<br/>
[in] Ein Zeiger auf `CMFCShellListCtrl` ein Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Methode `CMFCShellListCtrl` ordnet `CMFCShellTreeCtrl`eine mit einer zu. Diese Objekte können als Explorer-ähnliches Fenster angezeigt werden: Wenn `CMFCShellTreeCtrl`der Benutzer ein `CMFCShellListCtrl` Objekt im auswählt, werden die zugeordneten Elemente im automatisch aktualisiert.

Verwenden Sie die Methode [CMFCShellTreeCtrl::GetRelatedList,](#getrelatedlist) um die `CMFCShellListCtrl` zugeordnete mit einer `CMFCShellTreeCtrl`abzurufen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl-Klasse](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl-Klasse](../../mfc/reference/cmfcshelllistctrl-class.md)
