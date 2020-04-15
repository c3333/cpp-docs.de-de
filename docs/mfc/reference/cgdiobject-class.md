---
title: CGdiObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373736"
---
# <a name="cgdiobject-class"></a>CGdiObject-Klasse

Stellt eine Basisklasse für verschiedene Arten von Objekten der Windows GDI (Graphics Device Interface) wie Bitmaps, Bereiche, Pinsel, Stifte, Paletten und Schriftwarten bereit.

## <a name="syntax"></a>Syntax

```
class CGdiObject : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Erstellt ein `CGdiObject`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGdiObject::Anfügen](#attach)|Fügt ein Windows GDI-Objekt an ein `CGdiObject` Objekt an.|
|[CGdiObject::CreateStockObject](#createstockobject)|Ruft ein Handle für einen der vordefinierten Windows-Lagerstifte, Pinsel oder Schriftarten ab.|
|[CGdiObject::DeleteObject](#deleteobject)|Löscht das an das `CGdiObject` Objekt andas Objekt angefügte Windows GDI-Objekt aus dem Speicher, indem der gesamte dem Objekt zugeordnete Systemspeicher freiwird.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Löscht alle `CGdiObject` temporären `FromHandle`Objekte, die von erstellt wurden.|
|[CGdiObject::Detach](#detach)|Trennt ein Windows GDI-Objekt `CGdiObject` von einem Objekt und gibt ein Handle an das Windows GDI-Objekt zurück.|
|[CGdiObject::FromHandle](#fromhandle)|Gibt einen Zeiger `CGdiObject` auf ein Objekt zurück, das einem Windows GDI-Objekt ein Handle gegeben hat.|
|[CGdiObject::GetObject](#getobject)|Füllt einen Puffer mit Daten, die das an `CGdiObject` das Objekt angefügte Windows GDI-Objekt beschreiben.|
|[CGdiObject::GetObjectType](#getobjecttype)|Ruft den Typ des GDI-Objekts ab.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Gibt `m_hObject` zurück, es sei denn, **dies** ist NULL, in diesem Fall wird NULL zurückgegeben.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Setzt den Ursprung eines Pinsels zurück oder setzt eine logische Palette zurück.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGdiObject::operator !=](#operator_neq)|Legt fest, ob zwei GDI-Objekte logisch nicht gleich sind.|
|[CGdiObject::operator ==](#operator_eq_eq)|Legt fest, ob zwei GDI-Objekte logisch gleich sind.|
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Ruft einen HANDLE für das angefügte Windows GDI-Objekt ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Ein HANDLE, der hBITMAP, HPALETTE, HRGN, HBRUSH, HPEN oder HFONT enthält, die an dieses Objekt angefügt sind.|

## <a name="remarks"></a>Bemerkungen

Sie erstellen `CGdiObject` nie direkt. Stattdessen erstellen Sie ein Objekt aus einer der `CPen` `CBrush`abgeleiteten Klassen, z. B. oder .

Weitere Informationen `CGdiObject`zu finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::Anfügen

Fügt ein Windows GDI-Objekt an ein `CGdiObject` Objekt an.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Ein HANDLE für ein Windows GDI-Objekt (z. B. HPEN oder HBRUSH).

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Anlage erfolgreich ist; andernfalls 0.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

Erstellt ein `CGdiObject`-Objekt.

```
CGdiObject();
```

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CGdiObject` nie direkt. Stattdessen erstellen Sie ein Objekt aus einer der `CPen` `Cbrush`abgeleiteten Klassen, z. B. oder .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

Ruft ein Handle an einen der vordefinierten Windows GDI-Stifte, Pinsel oder Schriftarten ab `CGdiObject` und fügt das GDI-Objekt an das Objekt an.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Eine Konstante, die den gewünschten Lagerobjekttyp angibt. Eine Beschreibung der entsprechenden Werte finden Sie im Parameter *fnObject* für [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion mit einer der abgeleiteten Klassen auf, `CPen` die dem Windows GDI-Objekttyp entspricht, z. B. für einen Stockpen.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

Löscht das angefügte Windows GDI-Objekt aus dem Speicher, indem der gesamte Systemspeicher freiwird, der dem Windows GDI-Objekt zugeordnet ist.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das GDI-Objekt erfolgreich gelöscht wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der dem `CGdiObject` Objekt zugeordnete Speicher ist von diesem Aufruf nicht betroffen. Eine Anwendung sollte `DeleteObject` kein `CGdiObject` Objekt aufrufen, das derzeit in einem Gerätekontext ausgewählt ist.

Wenn ein Musterpinsel gelöscht wird, wird die dem Pinsel zugeordnete Bitmap nicht gelöscht. Die Bitmap muss unabhängig voneinander gelöscht werden.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

Wird automatisch `CWinApp` vom Leerlaufhandler `DeleteTempMap` aufgerufen, `CGdiObject` werden alle `FromHandle`temporären Objekte gelöscht, die von erstellt wurden.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Bemerkungen

`DeleteTempMap`trennt das Windows GDI-Objekt, `CGdiObject` das an `CGdiObject` ein temporäres Objekt angefügt ist, bevor das Objekt gelöscht wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::Detach

Trennt ein Windows GDI-Objekt `CGdiObject` von einem Objekt und gibt ein Handle an das Windows GDI-Objekt zurück.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Rückgabewert

A `HANDLE` zum Windows GDI-Objekt getrennt; andernfalls NULL, wenn kein GDI-Objekt angefügt ist.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::FromHandle

Gibt einen Zeiger `CGdiObject` auf ein Objekt zurück, das einem Windows GDI-Objekt ein Handle gegeben hat.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Ein HANDLE für ein Windows GDI-Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CGdiObject` ein, das vorübergehend oder dauerhaft sein kann.

### <a name="remarks"></a>Bemerkungen

Wenn `CGdiObject` ein Objekt noch nicht an das Windows `CGdiObject` GDI-Objekt angefügt ist, wird ein temporäres Objekt erstellt und angefügt.

Dieses `CGdiObject` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Eine andere Möglichkeit, dies zu sagen, ist, dass das temporäre Objekt nur während der Verarbeitung einer Fensternachricht gültig ist.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject::GetObject

Füllt einen Puffer mit Daten, die ein angegebenes Objekt definieren.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parameter

*nCount*<br/>
Gibt die Anzahl der Bytes an, die in den *lpObject-Puffer* kopiert werden sollen.

*lpObject*<br/>
Verweist auf einen vom Benutzer bereitgestellten Puffer, der die Informationen empfangen soll.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der abgerufenen Bytes; andernfalls 0, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die Funktion ruft eine Datenstruktur ab, deren Typ vom Typ des Grafikobjekts abhängt, wie in der folgenden Liste dargestellt:

|Object|Puffertyp|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[Logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[Bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Nicht unterstützt|

Wenn es sich `CBitmap` bei `GetObject` dem Objekt um ein Objekt handelt, werden nur die Informationen zum Breiten-, Höhen- und Farbformat der Bitmap zurückgegeben. Die eigentlichen Bits können mit [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)abgerufen werden.

Wenn es sich `CPalette` bei `GetObject` dem Objekt um ein Objekt handelt, ruft ein WORD ab, das die Anzahl der Einträge in der Palette angibt. Die Funktion ruft nicht die [LOGPALETTE-Struktur](/windows/win32/api/wingdi/ns-wingdi-logpalette) ab, die die Palette definiert. Eine Anwendung kann Informationen zu Paletteneinträgen abrufen, indem [sie CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)aufruft.

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

Ruft den Typ des GDI-Objekts ab.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Rückgabewert

Der Typ des Objekts, falls erfolgreich; andernfalls 0. Der Wert kann in folgenden Formen vorliegen:

- OBJ_BITMAP Bitmap

- OBJ_BRUSH Pinsel

- OBJ_FONT Schriftart

- OBJ_PAL Palette

- OBJ_PEN Pen

- OBJ_EXTPEN Erweiterter Stift

- OBJ_REGION Region

- OBJ_DC-Gerätekontext

- OBJ_MEMDC Speichergerätekontext

- OBJ_METAFILE Metafile

- OBJ_METADC Metafile-Gerätekontext

- OBJ_ENHMETAFILE Erweiterte Metadatei

- OBJ_ENHMETADC Enhanced-metafile-Gerätekontext

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Gibt `m_hObject` zurück, es sei denn, **dies** ist NULL, in diesem Fall wird NULL zurückgegeben.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein HANDLE mit dem angefügten Windows GDI-Objekt; ANDERNFALLS NULL, wenn kein Objekt angefügt ist.

### <a name="remarks"></a>Bemerkungen

Dies ist Teil des allgemeinen Handleschnittstellenparadigmas und ist nützlich, wenn NULL ein gültiger oder spezieller Wert für ein Handle ist.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject::m_hObject

Ein HANDLE, der hBITMAP, HRGN, HBRUSH, HPEN, HPALETTE oder HFONT enthält, die an dieses Objekt angefügt sind.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::operator !=

Legt fest, ob zwei GDI-Objekte logisch nicht gleich sind.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parameter

*obj*<br/>
Ein Zeiger auf `CGdiObject`eine vorhandene .

### <a name="remarks"></a>Bemerkungen

Legt fest, ob ein GDI-Objekt auf der linken Seite nicht gleich einem GDI-Objekt auf der rechten Seite ist.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::operator ==

Legt fest, ob zwei GDI-Objekte logisch gleich sind.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parameter

*obj*<br/>
Ein Verweis auf `CGdiObject`eine vorhandene .

### <a name="remarks"></a>Bemerkungen

Legt fest, ob ein GDI-Objekt auf der linken Seite einem GDI-Objekt auf der rechten Seite gleichist.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::operator HGDIOBJ

Ruft einen HANDLE für das angehängte Windows GDI-Objekt ab. ANDERNFALLS NULL, wenn kein Objekt angefügt ist.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

Setzt den Ursprung eines Pinsels zurück oder setzt eine logische Palette zurück.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Obwohl `UnrealizeObject` es sich um `CGdiObject` eine Memberfunktion der Klasse `CBrush` `CPalette` handelt, sollte sie nur für oder für Objekte aufgerufen werden.

Weist `CBrush` das `UnrealizeObject` System bei Objekten an, den Ursprung des angegebenen Pinsels zurückzusetzen, wenn er das nächste Mal in einem Gerätekontext ausgewählt wird. Wenn es sich `CPalette` bei `UnrealizeObject` dem Objekt um ein Objekt handelt, weist das System an, die Palette so zu realisieren, als ob sie zuvor nicht realisiert worden wäre. Wenn die Anwendung das nächste Mal die [CDC::RealizePalette-Funktion](../../mfc/reference/cdc-class.md#realizepalette) für die angegebene Palette aufruft, ordnet das System die logische Palette vollständig der Systempalette neu zu.

Die `UnrealizeObject` Funktion sollte nicht mit Lagerobjekten verwendet werden. Die `UnrealizeObject` Funktion muss aufgerufen werden, wenn ein neuer Pinselursprung gesetzt wird (mit Hilfe der [CDC::SetBrushOrg-Funktion).](../../mfc/reference/cdc-class.md#setbrushorg) Die `UnrealizeObject` Funktion darf nicht für den aktuell ausgewählten Pinsel oder die aktuell ausgewählte Palette eines Anzeigekontexts aufgerufen werden.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CBitmap-Klasse](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush-Klasse](../../mfc/reference/cbrush-class.md)<br/>
[CFont-Klasse](../../mfc/reference/cfont-class.md)<br/>
[CPalette-Klasse](../../mfc/reference/cpalette-class.md)<br/>
[CPen-Klasse](../../mfc/reference/cpen-class.md)<br/>
[CRgn-Klasse](../../mfc/reference/crgn-class.md)
