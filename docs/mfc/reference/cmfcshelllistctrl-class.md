---
title: CMFCShellListCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 445556535217b0887a02227a0773c287911922a2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753487"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl-Klasse

Die `CMFCShellListCtrl` Klasse bietet Windows-Listensteuerungsfunktionen und erweitert sie um die Möglichkeit, eine Liste von Shellelementen anzuzeigen.

## <a name="syntax"></a>Syntax

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Zeigt eine Liste der Elemente an, die in einem bereitgestellten Ordner enthalten sind.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Zeigt eine Liste der Elemente an, die sich in dem Ordner befinden, der das übergeordnete Element des aktuell angezeigten Ordners ist.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Aktiviert oder deaktiviert das Kontextmenü.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Ruft den Pfad des aktuellen Ordners ab.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Ruft den Namen des aktuellen Ordners ab.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Gibt die PIDL des aktuellen Listensteuerelements zurück.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Gibt einen Zeiger auf den aktuellen Shell-Ordner zurück.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Gibt den Textpfad eines Elements zurück.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Gibt Shell-Elementtypen zurück, die vom Listensteuerelement angezeigt werden.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Überprüft, ob der aktuell ausgewählte Ordner der Desktopordner ist.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Das Framework ruft diese Methode auf, wenn es zwei Elemente vergleicht. (Überschreibt [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Wird aufgerufen, wenn das Framework das vom Listensteuerelement angezeigte Dateidatum abruft.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Wird aufgerufen, wenn das Framework die Dateigröße eines Listensteuerelements konvertiert.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Wird aufgerufen, wenn das Framework das Symbol eines Listensteuerelements abruft.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Wird aufgerufen, wenn das Framework den Text eines Listensteuerelements konvertiert.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Wird vom Framework aufgerufen, wenn die Namen der Spalten festgelegt werden.|
|[CMFCShellListCtrl::Aktualisieren](#refresh)|Aktualisiert und zeichnet das Listensteuerelement neu.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Legt den Typ der Elemente fest, die vom Listensteuerelement angezeigt werden.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCShellListCtrl` Klasse erweitert die Funktionalität der [CMFCListCtrl-Klasse,](../../mfc/reference/cmfclistctrl-class.md) indem sie dem Programm ermöglicht, Windows-Shellelemente aufzulisten. Das verwendete Anzeigeformat ähnelt dem einer Listenansicht für ein Explorer-Fenster.

Ein [CMFCShellTreeCtrl-Objekt](../../mfc/reference/cmfcshelltreectrl-class.md) kann `CMFCShellListCtrl` einem Objekt zugeordnet werden, um ein vollständiges Explorer-Fenster zu erstellen. Wenn Sie dann ein `CMFCShellTreeCtrl` Element `CMFCShellListCtrl` im auswählen, wird das Objekt den Inhalt des ausgewählten Elements auflisten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCShellListCtrl` wie ein Objekt der Klasse erstellt und der übergeordnete Ordner des aktuell angezeigten Ordners angezeigt wird. Dieser Codeausschnitt ist Teil des [Explorer-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

Zeigt eine Liste der Elemente an, die im bereitgestellten Ordner enthalten sind.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parameter

*lpszPath*<br/>
[in] Eine Zeichenfolge, die den Pfad eines Ordners enthält.

*lpItemInfo*<br/>
[in] Ein Zeiger auf `LPAFX_SHELLITEMINFO` eine Struktur, die einen anzuzeigenden Ordner beschreibt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; E_FAIL sonst.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder

Aktualisiert das [CMFCShellListCtrl-Objekt,](../../mfc/reference/cmfcshelllistctrl-class.md) um den übergeordneten Ordner des aktuell angezeigten Ordners anzuzeigen.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; E_FAIL sonst.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Aktiviert das Kontextmenü.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Ein boolescher Wert, der angibt, ob das Framework das Kontextmenü aktiviert.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Ruft den Pfad des aktuell ausgewählten Ordners im [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) ab.

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parameter

*strPath*<br/>
[out] Ein Verweis auf einen Zeichenfolgenparameter, bei dem die Methode den Pfad schreibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0 sonst.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn `CMFCShellListCtrl`im Ordner kein Ordner ausgewählt ist.

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Ruft den Namen des aktuell ausgewählten Ordners im [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) ab.

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parameter

*strName*<br/>
[out] Ein Verweis auf einen Zeichenfolgenparameter, bei dem die Methode den Namen schreibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0 sonst.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn `CMFCShellListCtrl`im Ordner kein Ordner ausgewählt ist.

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Gibt die PIDL des aktuell ausgewählten Elements zurück.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Rückgabewert

Die PIDL des aktuellen Elements.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Ruft einen Zeiger auf das aktuell ausgewählte Element im [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) ab.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [IShellFolder-Schnittstelle](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) für das ausgewählte Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt NULL zurück, wenn derzeit kein Objekt ausgewählt ist.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Ruft den Pfad für ein Element ab.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parameter

*strPath*<br/>
[out] Ein Verweis auf eine Zeichenfolge, die den Pfad empfängt.

*iItem*<br/>
[in] Der Index des Listenelements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Der von *iItem* bereitgestellte Index basiert auf den Elementen, die derzeit vom [CMFCShellListCtrl-Klassenobjekt](../../mfc/reference/cmfcshelllistctrl-class.md) angezeigt werden.

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Gibt den Typ der Elemente zurück, die vom [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) angezeigt werden.

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [SHCONTF-Wert,](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) der den Typ `CMFCShellListCtrl`der im aufgelisteten Elemente enthält.

### <a name="remarks"></a>Bemerkungen

Um den Typ der in `CMFCShellListCtrl`einem aufgelisteten Elemente festzulegen, rufen Sie [CMFCShellListCtrl::SetItemTypes](#setitemtypes)auf.

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

Legt fest, ob der Ordner, der im [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) angezeigt wird, der Desktopordner ist.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der angezeigte Ordner der Desktopordner ist; FALSE sonst.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parameter

[in] *lParam1*<br/>
[in] *lParam2*<br/>
[in] *iColumn*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

Das Framework ruft diese Methode auf, wenn es das einem Objekt zugeordnete Datum in eine Zeichenfolge konvertieren muss.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parameter

*tmFile*<br/>
[in] Das Datum, das einer Datei zugeordnet ist.

*Str*<br/>
[out] Eine Zeichenfolge, die das formatierte Dateidatum enthält.

### <a name="remarks"></a>Bemerkungen

Wenn ein Objekt der [CMFCShellListCtrl-Klasse](../../mfc/reference/cmfcshelllistctrl-class.md) das einer Datei zugeordnete Datum anzeigt, muss es dieses Datum in ein Zeichenfolgenformat konvertieren. Der `CMFCShellListCtrl` verwendet diese Methode, um diese Konvertierung vorzunehmen. Standardmäßig verwendet diese Methode das aktuelle Gebietsschema, um das Datum in eine Zeichenfolge zu formatieren.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

Das Framework ruft diese Methode auf, wenn die Größe eines Objekts in eine Zeichenfolge konvertiert wird.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parameter

*lFileSize*<br/>
[in] Die Größe der Datei, die im Framework angezeigt wird.

*Str*<br/>
[out] Eine Zeichenfolge, die die formatierte Dateigröße enthält.

### <a name="remarks"></a>Bemerkungen

Wenn ein Objekt der [CMFCShellListCtrl-Klasse](../../mfc/reference/cmfcshelllistctrl-class.md) die Größe einer Datei anzeigen muss, muss es die Dateigröße in ein Zeichenfolgenformat konvertieren. Der `CMFCShellListCtrl` verwendet diese Methode, um diese Konvertierung vorzunehmen. Standardmäßig konvertiert diese Methode die Dateigröße von Bytes in Kilobyte und verwendet dann das aktuelle Gebietsschema, um die Größe in Zeichenfolge zu formatieren.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

Das Framework ruft diese Methode auf, um das Symbol abzurufen, das einem Shelllistenelement zugeordnet ist.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parameter

*iItem*<br/>
[in] Der Elementindex.

*pItem*<br/>
[in] Ein LPAFX_SHELLITEMINFO Parameter, der das Element beschreibt.

### <a name="return-value"></a>Rückgabewert

Der Index des Symbolbildes, wenn erfolgreich; -1, wenn die Funktion fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Der Symbolbildindex basiert auf der Systembildliste.

Standardmäßig basiert diese Methode auf dem *pItem-Parameter.* Der Wert von *iItem* wird in der Standardimplementierung nicht verwendet. Sie können *iItem* verwenden, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

Das Framework ruft diese Methode auf, wenn es den Text eines Shellelements abrufen muss.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parameter

*iItem*<br/>
[in] Der Elementindex.

*iColumn*<br/>
[in] Die Spalte von Interesse.

*pItem*<br/>
[in] Ein LPAFX_SHELLITEMINFO Parameter, der das Element beschreibt.

### <a name="return-value"></a>Rückgabewert

A, `CString` das den dem Element zugeordneten Text enthält.

### <a name="remarks"></a>Bemerkungen

Jedes Element `CMFCShellListCtrl` im Objekt kann Text in einer oder mehreren Spalten enthalten. Wenn das Framework diese Methode aufruft, gibt es die Spalte an, an der es interessiert ist. Wenn Sie diese Funktion manuell aufrufen, müssen Sie auch die Spalte angeben, an der Sie interessiert sind.

Standardmäßig basiert diese Methode auf dem *pItem-Parameter,* um zu bestimmen, welches Element verarbeitet werden soll. Der Wert von *iItem* wird in der Standardimplementierung nicht verwendet.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Das Framework ruft diese Methode auf, wenn die Namen der Spalten festgelegt werden.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig erstellt das Framework vier `CMFCShellListCtrl` Spalten in einem Objekt. Die Namen dieser Spalten lauten **Name**, **Größe**, **Typ**und **Geändert**. Sie können diese Methode überschreiben, um die Anzahl der Spalten und deren Namen anzupassen.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Aktualisieren

Aktualisiert und zeichnet das [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) neu.

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Rückgabewert

`S_OK`wenn sie erfolgreich sind; andernfalls ein Fehlerwert.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um `CMFCShellListCtrl` die Liste der vom Objekt angezeigten Elemente zu aktualisieren.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Legt den Typ der Elemente fest, die im [CMFCShellListCtrl-Objekt](../../mfc/reference/cmfcshelllistctrl-class.md) aufgeführt sind.

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parameter

*nTypen*<br/>
[in] Eine Liste der Elementtypen, die vom `CMFCShellListCtrl` Objekt unterstützt werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Liste der Elementtypen finden Sie unter [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl-Klasse](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl-Klasse](../../mfc/reference/cmfcshelltreectrl-class.md)
