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
ms.openlocfilehash: 479f5d47d9cff72d36dbd25e434182af1ba01ef4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754655"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty-Klasse

Implementiert eine OLE-Steuerelementeigenschaft, die asynchron geladen werden kann.

## <a name="syntax"></a>Syntax

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Erstellt ein `CDataPathProperty`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|Ruft das asynchrone OLE-Steuerelement `CDataPathProperty` ab, das dem Objekt zugeordnet ist.|
|[CDataPathProperty::GetPath](#getpath)|Ruft den Pfadnamen der Eigenschaft ab.|
|[CDataPathProperty::Öffnen](#open)|Initiiert das Laden der asynchronen Eigenschaft für das zugehörige ActiveX-Steuerelement (OLE).|
|[CDataPathProperty::ResetData](#resetdata)|Aufrufe, `CAsyncMonikerFile::OnDataAvailable` um den Container zu benachrichtigen, dass sich die Steuerelementeigenschaften geändert haben.|
|[CDataPathProperty::SetControl](#setcontrol)|Legt das asynchrone ActiveX-Steuerelement (OLE) fest, das der Eigenschaft zugeordnet ist.|
|[CDataPathProperty::SetPath](#setpath)|Legt den Pfadnamen der Eigenschaft fest.|

## <a name="remarks"></a>Bemerkungen

Asynchrone Eigenschaften werden nach der synchronen Initiierung geladen.

Die `CDataPathProperty` Klasse wird `CAysncMonikerFile`von abgeleitet. Um asynchrone Eigenschaften in Ihren OLE-Steuerelementen `CDataPathProperty`zu implementieren, leiten Sie eine Klasse von ab, und überschreiben [Sie OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Weitere Informationen zur Verwendung asynchroner Moniker und ActiveX-Steuerelemente in Internetanwendungen finden Sie in den folgenden Artikeln:

- [Erste Schritte im Internet: ActiveX-Steuerelemente](../../mfc/activex-controls-on-the-internet.md)

- [Erste Schritte im Internet: Asynchrone Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty

Erstellt ein `CDataPathProperty`-Objekt.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
Ein Zeiger auf das OLE-Steuerelementobjekt, `CDataPathProperty` das diesem Objekt zugeordnet werden soll.

*lpszPath*<br/>
Der Pfad, der absolut oder relativ sein kann, wird verwendet, um einen asynchronen Moniker zu erstellen, der auf die tatsächliche absolute Position der Eigenschaft verweist. `CDataPathProperty`verwendet URLs, nicht Dateinamen. Wenn Sie `CDataPathProperty` ein Objekt für eine `file://` Datei benötigen, stellen Sie dem Pfad einen Voranstellen an.

### <a name="remarks"></a>Bemerkungen

Das `COleControl` Objekt, auf das *pControl* zeigt, wird von `Open` abgeleiteten Klassen verwendet und von diesen abgerufen. Wenn *pControl* NULL ist, `Open` sollte das `SetControl`verwendete Steuerelement mit festgelegt werden. Wenn *lpszPath* NULL ist, können Sie `Open` den Pfad `SetPath`durchgehen oder mit festlegen.

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPathProperty::GetControl

Rufen Sie diese Memberfunktion auf, um das `COleControl` dem `CDataPathProperty` Objekt zugeordnete Objekt abzurufen.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das OLE-Steuerelement zurück, das dem `CDataPathProperty` Objekt zugeordnet ist. NULL, wenn nicht das Steuerelement zugeordnet ist.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPathProperty::GetPath

Rufen Sie diese Memberfunktion auf, `CDataPathProperty` um den Pfad abzurufen, festzulegen, wann das Objekt erstellt wurde, oder in angegeben `Open`oder in einem vorherigen Aufruf der `SetPath` Memberfunktion angegeben wurde.

```
CString GetPath() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den Pfadnamen an die Eigenschaft selbst zurück. Kann leer sein, wenn kein Pfad angegeben wurde.

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Öffnen

Rufen Sie diese Memberfunktion auf, um das Laden der asynchronen Eigenschaft für das zugeordnete Steuerelement zu initiieren.

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

*pControl*<br/>
Ein Zeiger auf das OLE-Steuerelementobjekt, `CDataPathProperty` das diesem Objekt zugeordnet werden soll.

*pError*<br/>
Ein Zeiger auf eine Dateiausnahme. Im Falle eines Fehlers, wird auf die Ursache gesetzt.

*lpszPath*<br/>
Der Pfad, der absolut oder relativ sein kann, wird verwendet, um einen asynchronen Moniker zu erstellen, der auf die tatsächliche absolute Position der Eigenschaft verweist. `CDataPathProperty`verwendet URLs, nicht Dateinamen. Wenn Sie `CDataPathProperty` ein Objekt für eine `file://` Datei benötigen, stellen Sie dem Pfad einen Voranstellen an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Funktion versucht, `IBindHost` die Schnittstelle vom Steuerelement abzuholen.

Vor `Open` dem Aufruf ohne Pfad muss der Wert für den Pfad der Eigenschaft festgelegt werden. Dies kann geschehen, wenn das Objekt `SetPath` erstellt wird, oder durch Aufrufen der Memberfunktion.

Vor `Open` dem Aufruf ohne Steuerelement kann dem Objekt ein ActiveX-Steuerelement (früher als OLE-Steuerelement bezeichnet) zugeordnet werden. Dies kann geschehen, wenn das Objekt `SetControl`erstellt wird, oder durch Aufrufen von .

Alle Überladungen von [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) sind auch ab `CDataPathProperty`verfügbar.

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPathProperty::ResetData

Rufen Sie diese `CAsyncMonikerFile::OnDataAvailable` Funktion auf, um den Container darüber zu informieren, dass sich die Steuerelementeigenschaften geändert haben und alle asynchron geladenen Informationen nicht mehr nützlich sind.

```
virtual void ResetData();
```

### <a name="remarks"></a>Bemerkungen

Die Öffnung sollte neu gestartet werden. Abgeleitete Klassen können diese Funktion für verschiedene Standardeinstellungen überschreiben.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl

Rufen Sie diese Memberfunktion auf, um `CDataPathProperty` dem Objekt ein asynchrones OLE-Steuerelement zuzuordnen.

```cpp
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
Ein Zeiger auf das asynchrone OLE-Steuerelement, das der Eigenschaft zugeordnet werden soll.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath

Rufen Sie diese Memberfunktion auf, um den Pfadnamen der Eigenschaft festzulegen.

```cpp
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parameter

*lpszPath*<br/>
Ein Pfad, der absolut oder relativ sein kann, auf die Eigenschaft, die asynchron geladen wird. `CDataPathProperty`verwendet URLs, nicht Dateinamen. Wenn Sie `CDataPathProperty` ein Objekt für eine `file://` Datei benötigen, stellen Sie dem Pfad einen Voranstellen an.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispielbild](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile-Klasse](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile-Klasse](../../mfc/reference/casyncmonikerfile-class.md)
