---
title: CDataPathProperty-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890823"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty-Klasse

Implementiert eine OLE-Steuerelementeigenschaft, die asynchron geladen werden kann.

## <a name="syntax"></a>Syntax

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataPathProperty:: CDataPathProperty](#cdatapathproperty)|Erstellt ein `CDataPathProperty`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataPathProperty:: GetControl](#getcontrol)|Ruft das asynchrone OLE-Steuerelement ab, das dem `CDataPathProperty` Objekt zugeordnet ist.|
|[CDataPathProperty:: getpath](#getpath)|Ruft den Pfadnamen der Eigenschaft ab.|
|[CDataPathProperty:: Open](#open)|Initiiert das Laden der asynchronen-Eigenschaft für das zugeordnete ActiveX (OLE)-Steuerelement.|
|[CDataPathProperty:: ResetData](#resetdata)|Ruft `CAsyncMonikerFile::OnDataAvailable` auf, um den Container zu benachrichtigen, dass die Steuerelement Eigenschaften geändert wurden.|
|[CDataPathProperty:: setcontrol](#setcontrol)|Legt das der-Eigenschaft zugeordnete asynchrone ActiveX (OLE)-Steuerelement fest.|
|[CDataPathProperty:: setpath](#setpath)|Legt den Pfadnamen der Eigenschaft fest.|

## <a name="remarks"></a>Bemerkungen

Asynchrone Eigenschaften werden nach der synchronen Initiierung geladen.

Die Klassen `CDataPathProperty` wird von `CAysncMonikerFile`abgeleitet. Um asynchrone Eigenschaften in ihren OLE-Steuerelementen zu implementieren, leiten Sie eine Klasse von `CDataPathProperty`ab, und überschreiben Sie [ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Weitere Informationen zur Verwendung von asynchronen Monikern und ActiveX-Steuerelementen in Internet Anwendungen finden Sie in den folgenden Artikeln:

- [Internet First-Schritte: ActiveX-Steuerelemente](../../mfc/activex-controls-on-the-internet.md)

- [Internet First-Schritte: asynchrone Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[Colestreamfile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxctl. h

##  <a name="cdatapathproperty"></a>CDataPathProperty:: CDataPathProperty

Erstellt ein `CDataPathProperty`-Objekt.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parameter

*pcontrol*<br/>
Ein Zeiger auf das OLE-Steuerelement Objekt, das diesem `CDataPathProperty` Objekt zugeordnet werden soll.

*lpszpath*<br/>
Der Pfad (absolut oder relativ), der verwendet wird, um einen asynchronen Moniker zu erstellen, der auf die tatsächliche absolute Position der Eigenschaft verweist. `CDataPathProperty` verwendet URLs, nicht Dateinamen. Wenn Sie ein `CDataPathProperty` Objekt für eine Datei benötigen, stellen Sie `file://` dem Pfad voran.

### <a name="remarks"></a>Bemerkungen

Das `COleControl` Objekt, auf das *pcontrol* verweist, wird von `Open` verwendet und von abgeleiteten Klassen abgerufen. Wenn *pcontrol* den Wert NULL hat, sollte das mit `Open` verwendete Steuerelement mit `SetControl`festgelegt werden. Wenn *lpszpath* den Wert NULL hat, können Sie den Pfad über `Open` übergeben oder mit `SetPath`festlegen.

##  <a name="getcontrol"></a>CDataPathProperty:: GetControl

Rufen Sie diese Member-Funktion auf, um das `COleControl` Objekt abzurufen, das mit dem `CDataPathProperty` Objekt verknüpft ist.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das OLE-Steuerelement zurück, das dem `CDataPathProperty` Objekt zugeordnet ist. NULL, wenn kein Steuerelement zugeordnet ist.

##  <a name="getpath"></a>CDataPathProperty:: getpath

Rufen Sie diese Member-Funktion auf, um den Pfad abzurufen, der bei der Erstellung des `CDataPathProperty` Objekts festgelegt oder in `Open`oder in einem vorherigen Aufrufen der `SetPath` Member-Funktion angegeben wurde.

```
CString GetPath() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Pfadnamen an die Eigenschaft selbst zurück. Kann leer sein, wenn kein Pfad angegeben wurde.

##  <a name="open"></a>CDataPathProperty:: Open

Diese Member-Funktion wird aufgerufen, um das Laden der asynchronen Eigenschaft für das zugeordnete Steuerelement zu initiieren.

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*pcontrol*<br/>
Ein Zeiger auf das OLE-Steuerelement Objekt, das diesem `CDataPathProperty` Objekt zugeordnet werden soll.

*pError*<br/>
Ein Zeiger auf eine Datei Ausnahme. Wenn ein Fehler auftritt, wird auf die Ursache festgelegt.

*lpszpath*<br/>
Der Pfad (absolut oder relativ), der verwendet wird, um einen asynchronen Moniker zu erstellen, der auf die tatsächliche absolute Position der Eigenschaft verweist. `CDataPathProperty` verwendet URLs, nicht Dateinamen. Wenn Sie ein `CDataPathProperty` Objekt für eine Datei benötigen, stellen Sie `file://` dem Pfad voran.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Funktion versucht, die `IBindHost`-Schnittstelle aus dem-Steuerelement abzurufen.

Bevor Sie `Open` ohne Pfad aufrufen, muss der Wert für den Pfad der Eigenschaft festgelegt werden. Dies kann erreicht werden, wenn das Objekt erstellt wird, oder indem die `SetPath` Member-Funktion aufgerufen wird.

Vor dem Aufrufen von `Open` ohne Steuerelement kann ein ActiveX-Steuerelement (früher als OLE-Steuerelement bezeichnet) dem-Objekt zugeordnet werden. Dies kann erreicht werden, wenn das Objekt erstellt wird, oder indem `SetControl`aufgerufen wird.

Alle über Ladungen von [CAsyncMonikerFile:: Open](../../mfc/reference/casyncmonikerfile-class.md#open) sind auch über `CDataPathProperty`verfügbar.

##  <a name="resetdata"></a>CDataPathProperty:: ResetData

Mit dieser Funktion können Sie `CAsyncMonikerFile::OnDataAvailable` den Container darüber informieren, dass sich die Steuerelement Eigenschaften geändert haben. alle Informationen, die asynchron geladen werden, sind nicht mehr nützlich.

```
virtual void ResetData();
```

### <a name="remarks"></a>Bemerkungen

Das Öffnen sollte neu gestartet werden. Abgeleitete Klassen können diese Funktion für verschiedene Standardwerte überschreiben.

##  <a name="setcontrol"></a>CDataPathProperty:: setcontrol

Diese Member-Funktion wird aufgerufen, um dem `CDataPathProperty` Objekt ein asynchrones OLE-Steuerelement zuzuordnen.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parameter

*pcontrol*<br/>
Ein Zeiger auf das asynchrone OLE-Steuerelement, das der-Eigenschaft zugeordnet werden soll.

##  <a name="setpath"></a>CDataPathProperty:: setpath

Mit dieser Member-Funktion können Sie den Pfadnamen der Eigenschaft festlegen.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parameter

*lpszpath*<br/>
Ein Pfad (absolut oder relativ) für die Eigenschaft, die asynchron geladen wird. `CDataPathProperty` verwendet URLs, nicht Dateinamen. Wenn Sie ein `CDataPathProperty` Objekt für eine Datei benötigen, stellen Sie `file://` dem Pfad voran.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Bild](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile-Klasse](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile-Klasse](../../mfc/reference/casyncmonikerfile-class.md)
