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
ms.openlocfilehash: 9bb70acb43f2e73ade86b753ebbb7949759ce88d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754602"
---
# <a name="cdbvariant-class"></a>CDBVariant-Klasse

Stellt einen varianten Datentyp für die MFC-ODBC-Klassen dar.

## <a name="syntax"></a>Syntax

```
class CDBVariant
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Erstellt ein `CDBVariant`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDBVariant::Löschen](#clear)|Löscht das `CDBVariant` Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Enthält den Datentyp des aktuell gespeicherten Werts. Geben Sie `DWORD` ein.|

### <a name="public-union-members"></a>Mitglieder der Öffentlichen Union

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Enthält einen Wert vom Typ **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Enthält einen Wert vom Typ **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Enthält einen Wert vom Typ **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Enthält einen Wert vom Typ **float**.|
|[CDBVariant::m_iVal](#m_ival)|Enthält einen Wert vom Typ **short**.|
|[CDBVariant::m_lVal](#m_lval)|Enthält einen Wert vom Typ **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Enthält einen Zeiger auf ein `CLongBinary`Objekt vom Typ .|
|[CDBVariant::m_pdate](#m_pdate)|Enthält einen Zeiger auf ein Objekt vom Typ **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Enthält einen Zeiger auf ein `CString`Objekt vom Typ .|
|[CDBVariant::m_pstringA](#m_pstringa)|Speichert einen Zeiger auf ein ASCII [CString-Objekt.](../../atl-mfc-shared/reference/cstringt-class.md)|
|[CDBVariant::m_pstringW](#m_pstringw)|Speichert einen Zeiger auf ein breites [CString-Objekt.](../../atl-mfc-shared/reference/cstringt-class.md)|

## <a name="remarks"></a>Bemerkungen

`CDBVariant`hat keine Basisklasse.

`CDBVariant`ist ähnlich wie [COleVariant](../../mfc/reference/colevariant-class.md); `CDBVariant` verwendet jedoch keine OLE. `CDBVariant`ermöglicht es Ihnen, einen Wert zu speichern, ohne sich um den Datentyp des Werts zu kümmern. `CDBVariant`verfolgt den Datentyp des aktuellen Werts, der in einer Union gespeichert wird.

Klasse [CRecordset](../../mfc/reference/crecordset-class.md) `CDBVariant` verwendet Objekte in `GetFieldValue`drei `GetBookmark`Memberfunktionen: , , und `SetBookmark`. Ermöglicht `GetFieldValue` z. B. das dynamische Abrufen von Daten in einer Spalte. Da der Datentyp der Spalte zur Laufzeit `GetFieldValue` möglicherweise `CDBVariant` nicht bekannt ist, wird ein Objekt zum Speichern der Spaltendaten verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDBVariant`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Erstellt ein `CDBVariant` NULL-Objekt.

```
CDBVariant();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_dwType](#m_dwtype) Datenmember auf DBVT_NULL fest.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant::Löschen

Rufen Sie diese Memberfunktion auf, um das `CDBVariant` Objekt zu löschen.

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Wert des [m_dwType](#m_dwtype) Datenmembers DBVT_DATE ist, gibt DBVT_STRING oder DBVT_BINARY den Speicher frei, `Clear` der dem Union-Zeigermember zugeordnet ist. `Clear`setzt `m_dwType` auf DBVT_NULL.

Der `CDBVariant` Destruktor ruft `Clear`auf.

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant::m_boolVal

Speichert einen Wert vom Typ BOOL.

### <a name="remarks"></a>Bemerkungen

Das `m_boolVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_boolVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_BOOL festgelegt `m_boolVal` ist, enthält sie einen gültigen Wert. Andernfalls führt `m_boolVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant::m_chVal

Speichert einen Wert vom Typ **unsigned char**.

### <a name="remarks"></a>Bemerkungen

Das `m_chVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_chVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_UCHAR festgelegt `m_chVal` ist, enthält ein gültiger Wert. Andernfalls führt `m_chVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant::m_dblVal

Speichert einen Wert vom Typ **double**.

### <a name="remarks"></a>Bemerkungen

Das `m_dblVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_dblVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_DOUBLE festgelegt `m_dblVal` ist, enthält ein gültiger Wert. Andernfalls führt `m_dblVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant::m_dwType

Dieser Datenmember enthält den Datentyp für den `CDBVariant` Wert, der derzeit im Union-Datenmember des Objekts gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Bevor Sie auf diese Union zugreifen, `m_dwType` müssen Sie den Wert von überprüfen, um zu bestimmen, auf welches Union-Datenmitglied zugreifen soll. In der folgenden Tabelle `m_dwType` sind die möglichen Werte für und das entsprechende Union-Datenelement aufgeführt.

|m_dwType|Mitglied der Unionsdaten|
|---------------|-----------------------|
|DBVT_NULL|Kein Gewerkschaftsmitglied ist für den Zugriff gültig.|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant::m_fltVal

Speichert einen Wert vom Typ **float**.

### <a name="remarks"></a>Bemerkungen

Das `m_fltVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_fltVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_SINGLE festgelegt `m_fltVal` ist, enthält ein gültiger Wert. Andernfalls führt `m_fltVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant::m_iVal

Speichert einen Wert vom Typ **short**.

### <a name="remarks"></a>Bemerkungen

Das `m_iVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_iVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_SHORT festgelegt `m_iVal` ist, enthält ein gültiger Wert. Andernfalls führt `m_iVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant::m_lVal

Speichert einen Wert vom Typ **long**.

### <a name="remarks"></a>Bemerkungen

Das `m_lVal` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_lVal`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_LONG festgelegt `m_lVal` ist, enthält ein gültiger Wert. Andernfalls führt `m_lVal` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant::m_pbinary

Speichert einen Zeiger auf ein Objekt vom Typ [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Bemerkungen

Das `m_pbinary` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_pbinary`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_BINARY festgelegt `m_pbinary` ist, enthält ein gültiger Zeiger. Andernfalls führt `m_pbinary` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant::m_pdate

Speichert einen Zeiger auf ein Objekt vom Typ TIMESTAMP_STRUCT.

### <a name="remarks"></a>Bemerkungen

Das `m_pdate` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_pdate`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_DATE festgelegt `m_pdate` ist, enthält ein gültiger Zeiger. Andernfalls führt `m_pdate` der Zugriff zu unzuverlässigen Ergebnissen.

Weitere Informationen zum TIMESTAMP_STRUCT Datentyps finden Sie im Thema [C-Datentypen](/sql/odbc/reference/appendixes/c-data-types) in Anhang D der *ODBC-Programmiererreferenz* im Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant::m_pstring

Speichert einen Zeiger auf ein Objekt vom Typ [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Bemerkungen

Das `m_pstring` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_pstring`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_STRING festgelegt `m_pstring` ist, enthält ein gültiger Zeiger. Andernfalls führt `m_pstring` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant::m_pstringA

Speichert einen Zeiger auf ein ASCII [CString-Objekt.](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>Bemerkungen

Das `m_pstringA` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_pstringA`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_ASTRING festgelegt `m_pstringA` ist, enthält ein gültiger Zeiger. Andernfalls führt `m_pstringA` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant::m_pstringW

Speichert einen Zeiger auf ein breites [CString-Objekt.](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>Bemerkungen

Das `m_pstringW` Datenmitglied gehört einer Gewerkschaft an. Überprüfen Sie `m_pstringW`vor dem Zugriff zunächst den Wert von [CDBVariant::m_dwType](#m_dwtype). Wenn `m_dwType` auf DBVT_WSTRING festgelegt `m_pstringW` ist, enthält ein gültiger Zeiger. Andernfalls führt `m_pstringW` der Zugriff zu unzuverlässigen Ergebnissen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
