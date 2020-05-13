---
title: CShellManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 1c2f9ac1658f50f0ec5bd9e2f53d270c09bfcb6a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750325"
---
# <a name="cshellmanager-class"></a>CShellManager-Klasse

Implementiert mehrere Möglichkeiten für die Verwendung von Zeigern auf Bezeichnerlisten (PIDLs).

## <a name="syntax"></a>Syntax

```
class CShellManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Erstellt ein `CShellManager`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Zeigt ein Dialogfeld an, in dem der Benutzer einen Shellordner auswählen kann.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Verkettet zwei PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Erstellt eine neue PIDL und kopiert die mitgelieferte PIDL darauf.|
|[CShellManager::CreateItem](#createitem)|Erstellt eine neue PIDL der angegebenen Größe.|
|[CShellManager::FreeItem](#freeitem)|Löscht die mitgelieferte PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Gibt die Anzahl der Elemente in der angegebenen PIDL zurück.|
|[CShellManager::GetItemSize](#getitemsize)|Gibt die Größe der bereitgestellten PIDL zurück.|
|[CShellManager::GetNextItem](#getnextitem)|Gibt das nächste Element aus der PIDL zurück.|
|[CShellManager::GetParentItem](#getparentitem)|Ruft das übergeordnete Element des angegebenen Elements ab.|
|[CShellManager::ItemFromPath](#itemfrompath)|Ruft die PIDL für das Element ab, das durch den angegebenen Pfad identifiziert wurde.|

## <a name="remarks"></a>Bemerkungen

Die Methoden `CShellManager` der Klasse befassen sich alle mit PIDLs. Eine PIDL ist ein eindeutiger Bezeichner für ein Shellobjekt.

Sie sollten ein `CShellManager` Objekt nicht manuell erstellen. Sie wird automatisch durch das Framework Ihrer Anwendung erstellt. Sie sollten jedoch [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) während des Initialisierungsprozesses Ihrer Anwendung aufrufen. Um einen Zeiger auf den Shell-Manager für Ihre Anwendung zu erhalten, rufen Sie [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)an.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxshellmanager.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShellManager::BrowseForFolder

Zeigt ein Dialogfeld an, in dem der Benutzer einen Shellordner auswählen kann.

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>Parameter

*strOutFolder*<br/>
[out] Die Zeichenfolge, die von der Methode zum Speichern des Pfads des ausgewählten Ordners verwendet wird.

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster.

*lplszInitialFolder*<br/>
[in] Eine Zeichenfolge, die den Ordner enthält, der standardmäßig ausgewählt ist, wenn das Dialogfeld angezeigt wird.

*lpszTitle*<br/>
[in] Der Titel für das Dialogfeld.

*ulFlags*<br/>
[in] Flags, die Optionen für das Dialogfeld angeben. Eine ausführliche Beschreibung finden Sie unter [BROWSEINFO.](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow)

*piFolderImage*<br/>
[out] Ein Zeiger auf den Ganzzahlwert, bei dem die Methode den Bildindex des ausgewählten Ordners schreibt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Benutzer einen Ordner aus dem Dialogfeld auswählt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, erstellt und zeigt die Anwendung ein Dialogfeld an, in dem der Benutzer einen Ordner auswählen kann. Die Methode schreibt den Pfad des Ordners in den Parameter *strOutFolder.*

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CShellManager` wie ein `CWinAppEx::GetShellManager` Verweis auf ein `BrowseForFolder` Objekt mithilfe der Methode abgerufen und die Methode verwendet wird. Dieser Codeausschnitt ist Teil des [Explorer-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager::ConcatenateItem

Erstellt eine neue Liste mit zwei PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parameter

*pidl1*<br/>
[in] Der erste Punkt.

*pidl2*<br/>
[in] Der zweite Punkt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neue Elementliste, wenn die Funktion erfolgreich ist, andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt eine neue [ITEMIDLIST,](/windows/win32/api/shtypes/ns-shtypes-itemidlist) die groß genug ist, um sowohl *pidl1* als auch *pidl2*zu enthalten. Anschließend werden *pidl1* und *pidl2* in die neue Liste kopiert.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>CShellManager::CopyItem

Kopiert eine Elementliste.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parameter

*pidlSource*<br/>
[in] Die ursprüngliche Elementliste.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die neu erstellte Elementliste, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Die neu erstellte Elementliste hat die gleiche Größe wie die Quellelementliste.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShellManager::CreateItem

Erstellt eine neue PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parameter

*cbSize*<br/>
[in] Die Größe der Elementliste.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die erstellte Elementliste, wenn erfolgreich; andernfalls NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>CShellManager::CShellManager

Erstellt ein `CShellManager`-Objekt.

```
CShellManager();
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen müssen Sie `CShellManager` keine direkt erstellen. Standardmäßig erstellt das Framework eine für Sie. Um einen Zeiger auf `CShellManager`die zu erhalten, rufen Sie [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)auf. Wenn Sie eine `CShellManager` manuell erstellen, müssen Sie sie mit der Methode [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)initialisieren.

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager::FreeItem

Löscht eine Elementliste.

```cpp
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parameter

*Pidl*<br/>
[in] Eine zu löschende Elementliste.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShellManager::GetItemCount

Gibt die Anzahl der Elemente in einer Elementliste zurück.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parameter

*Pidl*<br/>
[in] Ein Zeiger auf eine Elementliste.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Artikelliste.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShellManager::GetItemSize

Gibt die Größe einer Elementliste zurück.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parameter

*Pidl*<br/>
[in] Ein Zeiger auf eine Elementliste.

### <a name="return-value"></a>Rückgabewert

Die Größe der Elementliste.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager::GetNextItem

Ruft das nächste Element von einem Zeiger auf eine Elementbezeichnerliste (PIDL) ab.

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parameter

*Pidl*<br/>
[in] Die Liste der zu iterierenden Elemente.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Element in der Liste.

### <a name="remarks"></a>Bemerkungen

Wenn keine weiteren Elemente in der Liste vorhanden sind, gibt diese Methode NULL zurück.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager::GetParentItem

Ruft das übergeordnete Element eines Zeigers auf eine Elementbezeichnerliste (PIDL) ab.

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parameter

*lpidl*<br/>
[in] Eine PIDL, deren übergeordnetes Element abgerufen wird.

*lpidlEltern*<br/>
[out] Ein Verweis auf eine PIDL, bei der die Methode das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

Die Ebene der übergeordneten PIDL.

### <a name="remarks"></a>Bemerkungen

Die Ebene einer PIDL ist relativ zum Desktop. Die Desktop-PIDL wird als eine Stufe von 0 betrachtet.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShellManager::ItemFromPath

Ruft den Zeiger auf eine Elementbezeichnerliste (PIDL) aus dem Element ab, das durch einen Zeichenfolgenpfad identifiziert wurde.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parameter

*lpszPath*<br/>
[in] Eine Zeichenfolge, die den Pfad für das Element angibt.

*Pidl*<br/>
[out] Ein Verweis auf eine PIDL. Die Methode verwendet diese PIDL, um den Zeiger auf den Rückgabewert zu speichern.

### <a name="return-value"></a>Rückgabewert

Gibt NOERROR zurück, wenn es erfolgreich ist; einen OLE-definierten Fehlerwert.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
