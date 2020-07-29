---
title: CDBVariant-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 45a478a5ca6cfb4d9b976a29eae2ae7d98fdd6ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223082"
---
# <a name="cdbvariant-class"></a>CDBVariant-Klasse

Stellt einen varianten Datentyp für die MFC-ODBC-Klassen dar.

## <a name="syntax"></a>Syntax

```
class CDBVariant
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDBVariant:: CDBVariant](#cdbvariant)|Erstellt ein `CDBVariant`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CDBVariant:: Clear](#clear)|Löscht das- `CDBVariant` Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CDBVariant:: m_dwType](#m_dwtype)|Enthält den Datentyp des aktuell gespeicherten-Werts. Geben Sie `DWORD` ein.|

### <a name="public-union-members"></a>Öffentliche Unionmember

|Name|Beschreibung|
|----------|-----------------|
|[CDBVariant:: m_boolVal](#m_boolval)|Enthält einen Wert vom Typ **bool**.|
|[CDBVariant:: m_chVal](#m_chval)|Enthält einen Wert vom Typ **`unsigned char`** .|
|[CDBVariant:: m_dblVal](#m_dblval)|Enthält einen Wert vom Typ **`double`** .|
|[CDBVariant:: m_fltVal](#m_fltval)|Enthält einen Wert vom Typ **`float`** .|
|[CDBVariant:: m_iVal](#m_ival)|Enthält einen Wert vom Typ **`short`** .|
|[CDBVariant:: m_lVal](#m_lval)|Enthält einen Wert vom Typ **`long`** .|
|[CDBVariant:: m_pbinary](#m_pbinary)|Enthält einen Zeiger auf ein Objekt vom Typ `CLongBinary` .|
|[CDBVariant:: m_pdate](#m_pdate)|Enthält einen Zeiger auf ein Objekt vom Typ **TIMESTAMP_STRUCT**.|
|[CDBVariant:: m_pstring](#m_pstring)|Enthält einen Zeiger auf ein Objekt vom Typ `CString` .|
|[CDBVariant:: m_pstringA](#m_pstringa)|Speichert einen Zeiger auf ein ASCII- [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt.|
|[CDBVariant:: m_pstringW](#m_pstringw)|Speichert einen Zeiger auf ein breites [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt.|

## <a name="remarks"></a>Bemerkungen

`CDBVariant`weist keine Basisklasse auf.

`CDBVariant`ähnelt [COleVariant](../../mfc/reference/colevariant-class.md); Allerdings wird von `CDBVariant` OLE nicht verwendet. `CDBVariant`ermöglicht das Speichern eines Werts, ohne sich Gedanken über den Datentyp des Werts machen zu müssen. `CDBVariant`verfolgt den Datentyp des aktuellen-Werts, der in einer Union gespeichert wird.

[CRecordset](../../mfc/reference/crecordset-class.md) -Klasse verwendet `CDBVariant` Objekte in drei Element Funktionen: `GetFieldValue` , `GetBookmark` und `SetBookmark` . Ermöglicht beispielsweise das `GetFieldValue` dynamische Abrufen von Daten in einer Spalte. Da der Datentyp der Spalte zur Laufzeit möglicherweise nicht bekannt ist, `GetFieldValue` verwendet ein- `CDBVariant` Objekt, um die Daten der Spalte zu speichern.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDBVariant`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant:: CDBVariant

Erstellt ein NULL- `CDBVariant` Objekt.

```
CDBVariant();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_dwType](#m_dwtype) Datenmember auf DBVT_NULL fest.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant:: Clear

Diese Member-Funktion zum Löschen des-Objekts aufzurufen `CDBVariant` .

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Wert des [m_dwType](#m_dwtype) Datenmembers DBVT_DATE, DBVT_STRING oder DBVT_BINARY ist, gibt den Arbeitsspeicher frei, der `Clear` dem Union-Zeiger Element zugeordnet ist. `Clear`legt `m_dwType` auf DBVT_NULL fest.

Der `CDBVariant` Dekonstruktor Ruft auf `Clear` .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant:: m_boolVal

Speichert einen Wert vom Typ bool.

### <a name="remarks"></a>Bemerkungen

Der `m_boolVal` Datenmember gehört zu einer Union. `m_boolVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_BOOL festgelegt ist, `m_boolVal` enthält einen gültigen Wert. andernfalls führt der Zugriff auf `m_boolVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant:: m_chVal

Speichert einen Wert vom Typ **`unsigned char`** .

### <a name="remarks"></a>Bemerkungen

Der `m_chVal` Datenmember gehört zu einer Union. `m_chVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_UCHAR festgelegt ist, `m_chVal` enthält einen gültigen-Wert. andernfalls führt der Zugriff auf `m_chVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant:: m_dblVal

Speichert einen Wert vom Typ **`double`** .

### <a name="remarks"></a>Bemerkungen

Der `m_dblVal` Datenmember gehört zu einer Union. `m_dblVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_DOUBLE festgelegt ist, `m_dblVal` enthält einen gültigen-Wert. andernfalls führt der Zugriff auf `m_dblVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant:: m_dwType

Dieser Datenmember enthält den Datentyp für den Wert, der derzeit im `CDBVariant` Union-Datenmember des Objekts gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Vor dem Zugriff auf diese Union müssen Sie den Wert von überprüfen, um `m_dwType` zu bestimmen, auf welches Union-Datenmember zugegriffen werden soll. In der folgenden Tabelle sind die möglichen Werte für `m_dwType` und das entsprechende Union-Datenmember aufgeführt.

|m_dwType|Union-Datenmember|
|---------------|-----------------------|
|DBVT_NULL|Kein Unionmember ist für den Zugriff gültig.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant:: m_fltVal

Speichert einen Wert vom Typ **`float`** .

### <a name="remarks"></a>Bemerkungen

Der `m_fltVal` Datenmember gehört zu einer Union. `m_fltVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_SINGLE festgelegt ist, `m_fltVal` enthält einen gültigen-Wert. andernfalls führt der Zugriff auf `m_fltVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant:: m_iVal

Speichert einen Wert vom Typ **`short`** .

### <a name="remarks"></a>Bemerkungen

Der `m_iVal` Datenmember gehört zu einer Union. `m_iVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_SHORT festgelegt ist, `m_iVal` enthält einen gültigen-Wert. andernfalls führt der Zugriff auf `m_iVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant:: m_lVal

Speichert einen Wert vom Typ **`long`** .

### <a name="remarks"></a>Bemerkungen

Der `m_lVal` Datenmember gehört zu einer Union. `m_lVal`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_LONG festgelegt ist, `m_lVal` enthält einen gültigen-Wert. andernfalls führt der Zugriff auf `m_lVal` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant:: m_pbinary

Speichert einen Zeiger auf ein Objekt des Typs [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Bemerkungen

Der `m_pbinary` Datenmember gehört zu einer Union. `m_pbinary`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_BINARY festgelegt ist, `m_pbinary` enthält einen gültigen Zeiger; andernfalls führt der Zugriff auf `m_pbinary` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant:: m_pdate

Speichert einen Zeiger auf ein Objekt vom Typ TIMESTAMP_STRUCT.

### <a name="remarks"></a>Bemerkungen

Der `m_pdate` Datenmember gehört zu einer Union. `m_pdate`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_DATE festgelegt ist, `m_pdate` enthält einen gültigen Zeiger; andernfalls führt der Zugriff auf `m_pdate` unzuverlässige Ergebnisse.

Weitere Informationen zum TIMESTAMP_STRUCT-Datentyp finden Sie im Thema [C-Datentypen](/sql/odbc/reference/appendixes/c-data-types) in Anhang D der *ODBC-Programmier Referenz* im Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant:: m_pstring

Speichert einen Zeiger auf ein Objekt vom Typ [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Bemerkungen

Der `m_pstring` Datenmember gehört zu einer Union. `m_pstring`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_STRING festgelegt ist, `m_pstring` enthält einen gültigen Zeiger; andernfalls führt der Zugriff auf `m_pstring` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant:: m_pstringA

Speichert einen Zeiger auf ein ASCII- [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Der `m_pstringA` Datenmember gehört zu einer Union. `m_pstringA`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_ASTRING festgelegt ist, `m_pstringA` enthält einen gültigen Zeiger; andernfalls führt der Zugriff auf `m_pstringA` unzuverlässige Ergebnisse.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant:: m_pstringW

Speichert einen Zeiger auf ein breites [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Der `m_pstringW` Datenmember gehört zu einer Union. `m_pstringW`Überprüfen Sie vor dem Zugriff zuerst den Wert von [CDBVariant:: m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_WSTRING festgelegt ist, `m_pstringW` enthält einen gültigen Zeiger; andernfalls führt der Zugriff auf `m_pstringW` unzuverlässige Ergebnisse.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
