---
title: Dialogdatenaustausch-Funktionen für CRecordView und CDaoRecordView
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365779"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Dialogdatenaustausch-Funktionen für CRecordView und CDaoRecordView

In diesem Thema werden die DDX_Field-Funktionen aufgelistet, die zum Austauschen von Daten zwischen einem [CRecordset](../../mfc/reference/crecordset-class.md) und einem [CRecordView](../../mfc/reference/crecordview-class.md) -Formular oder einem [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)-Formular und einem [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Formular verwendet werden.  DAO wird mit Access-Datenbanken verwendet und wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

> [!NOTE]
> DDX_Field Funktionen sind wie DDX-Funktionen, da sie Daten mit Steuerelementen in einem Formular austauschen. Im Gegensatz zu DDX tauschen sie jedoch Daten mit den Feldern des zugeordneten Recordset-Objekts der Ansicht aus und nicht mit Feldern der Datensatzansicht selbst. Weitere Informationen finden `CRecordView` Sie `CDaoRecordView`unter Klassen und .

### <a name="ddx_field-functions"></a>DDX_Field Funktionen

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Überträgt ganzzahlige Daten zwischen einem Recordset-Felddatenelement und dem Index der aktuellen Auswahl in einem Kombinationsfeld in einer [CRecordView](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Überträgt `CString` Daten zwischen einem Recordset-Felddatenelement und dem `CRecordView` `CDaoRecordView`Bearbeitungssteuerelement eines Kombinationsfelds in einem oder . Beim Verschieben von Daten aus dem Recordset in das Steuerelement wählt diese Funktion das Element im Kombinationsfeld aus, das mit den Zeichen in der angegebenen Zeichenfolge beginnt.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Überträgt `CString` Daten zwischen einem Recordset-Felddatenelement und dem `CRecordView` `CDaoRecordView`Bearbeitungssteuerelement eines Kombinationsfelds in einem oder . Beim Verschieben von Daten aus dem Recordset in das Steuerelement wählt diese Funktion das Element im Kombinationsfeld aus, das genau mit der angegebenen Zeichenfolge übereinstimmt.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Überträgt boolesche Daten zwischen einem Recordset-Felddatenelement und einem Kontrollkästchen in einem `CRecordView` oder `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Überträgt ganzzahlige Daten zwischen einem Recordset-Felddatenelement und dem Index `CRecordView` `CDaoRecordView`der aktuellen Auswahl in einem Listenfeld in einem oder .|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Verwaltet die Übertragung von [CString-Daten](../../atl-mfc-shared/reference/cstringt-class.md) zwischen einem Listenfeldsteuerelement und den Felddatenelementen eines Recordsets. Beim Verschieben von Daten aus dem Recordset in das Steuerelement wählt diese Funktion das Element im Listenfeld aus, das mit den Zeichen in der angegebenen Zeichenfolge beginnt.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Verwaltet die `CString` Datenübertragung zwischen einem Listenfeldsteuerelement und den Felddatenelementen eines Recordsets. Beim Verschieben von Daten aus dem Recordset in das Steuerelement wählt diese Funktion das erste Element aus, das genau mit der angegebenen Zeichenfolge übereinstimmt.|
|[DDX_FieldRadio](#ddx_fieldradio)|Überträgt ganzzahlige Daten zwischen einem Recordsetfelddatenmember und `CRecordView` `CDaoRecordView`einer Gruppe von Optionsfeldern in einem oder .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Legt die Bildlaufposition eines Bildlaufleistensteuerelements in einem `CRecordView` oder `CDaoRecordView`fest oder ruft sie ab. Aufruf von Ihrer [DoFieldExchange-Funktion.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronisiert die Daumenposition eines Schiebereglersteuerelements `int` in einer Datensatzansicht und eines Felddatenmembers eines Recordsets. |
|[DDX_FieldText](#ddx_fieldtext)|Überladene Versionen sind `int`für die Übertragung von `DWORD`, **UINT**, **long**, [, CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)und [COleCurrency-Daten](../../mfc/reference/colecurrency-class.md) zwischen einem Recordset-Felddatenmember und einem Bearbeitungsfeld in einem `CRecordView` oder `CDaoRecordView`verfügbar.|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

Die `DDX_FieldCBIndex` Funktion synchronisiert den Index des ausgewählten Elements im Listenfeldsteuerelement eines Kombinationsfeldsteuerelements in einer Datensatzansicht und eines `int` Felddatenmembers eines Datensatzes, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*Index*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten aus dem Recordset in das Steuerelement legt diese Funktion die Auswahl im Steuerelement basierend auf dem im *Index*angegebenen Wert fest. Wenn das Recordsetfeld bei einer Übertragung vom Recordset zum Steuerelement Null ist, legt MFC den Wert des Indexes auf 0 fest. Wenn bei einer Übertragung von Steuerelement zu Recordset das Steuerelement leer ist oder kein Element ausgewählt ist, wird das Recordset-Feld auf 0 gesetzt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Das Beispiel wäre `DDX_FieldCBIndex`ähnlich für .

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

Die `DDX_FieldCBString` Funktion verwaltet die Übertragung von [CString-Daten](../../atl-mfc-shared/reference/cstringt-class.md) zwischen dem Bearbeitungssteuerelement `CString` eines Kombinationsfeldsteuerelements in einer Datensatzansicht und einem Felddatenelement eines Datensatzes, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten aus dem Recordset in das Steuerelement legt diese Funktion die aktuelle Auswahl im Kombinationsfeld auf die erste Zeile fest, die mit den Zeichen in der im *Wert*angegebenen Zeichenfolge beginnt. Wenn das Recordsetfeld bei einer Übertragung vom Recordset in das Steuerelement Null ist, wird jede Auswahl aus dem Kombinationsfeld entfernt, und das Bearbeitungssteuerelement des Kombinationsfelds wird auf leer gesetzt. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordsetfeld auf Null gesetzt, wenn das Feld dies zulässt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Das Beispiel enthält `DDX_FieldCBString`einen Aufruf von .

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

Die `DDX_FieldCBStringExact` Funktion verwaltet die Übertragung von [CString-Daten](../../atl-mfc-shared/reference/cstringt-class.md) zwischen dem Bearbeitungssteuerelement `CString` eines Kombinationsfeldsteuerelements in einer Datensatzansicht und einem Felddatenelement eines Datensatzes, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten aus dem Recordset in das Steuerelement legt diese Funktion die aktuelle Auswahl im Kombinationsfeld auf die erste Zeile fest, die genau mit der im *Wert*angegebenen Zeichenfolge übereinstimmt. Wenn das Recordsetfeld bei einer Übertragung vom Recordset in das Steuerelement NULL ist, wird jede Auswahl aus dem Kombinationsfeld entfernt, und das Bearbeitungsfeld des Kombinationsfelds wird auf leer gesetzt. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordset-Feld auf NULL gesetzt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldCBStringExact` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

Die `DDX_FieldCheck` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Kontrollkästchen-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kontrollkästchen-Steuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_FieldCheck` aufgerufen wird, wird *der Wert* auf den aktuellen Status des Kontrollkästchen-Steuerelements festgelegt, oder der Status des Steuerelements wird abhängig von der Übertragungsrichtung auf *Wert*festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

Die `DDX_FieldLBIndex` Funktion synchronisiert den Index des ausgewählten Elements in einem Listenfeldsteuerelement in einer Datensatzansicht und einem **int-Felddatenelement** eines Datensatzes, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*Index*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten aus dem Recordset in das Steuerelement legt diese Funktion die Auswahl im Steuerelement basierend auf dem im *Index*angegebenen Wert fest. Wenn das Recordsetfeld bei einer Übertragung vom Recordset zum Steuerelement Null ist, legt MFC den Wert des Indexes auf 0 fest. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordset-Feld auf 0 gesetzt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext)

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

Der `DDX_FieldLBString` kopiert die aktuelle Auswahl eines Listenfeldsteuerelements in einer Datensatzansicht in ein [CString-Felddatenelement](../../atl-mfc-shared/reference/cstringt-class.md) eines Recordsets, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

In umgekehrter Richtung legt diese Funktion die aktuelle Auswahl im Listenfeld auf die erste Zeile fest, die mit den Zeichen in der Zeichenfolge beginnt, die durch *den Wert*angegeben wird. Wenn das Recordsetfeld bei einer Übertragung vom Recordset in das Steuerelement Null ist, wird jede Auswahl aus dem Listenfeld entfernt. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordset-Feld auf Null gesetzt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldLBString` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

Die `DDX_FieldLBStringExact` Funktion kopiert die aktuelle Auswahl eines Listenfeldsteuerelements in einer Datensatzansicht in ein [CString-Felddatenelement](../../atl-mfc-shared/reference/cstringt-class.md) eines Recordsets, das der Datensatzansicht zugeordnet ist.

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

In umgekehrter Richtung legt diese Funktion die aktuelle Auswahl im Listenfeld auf die erste Zeile fest, die genau mit der im *Wert*angegebenen Zeichenfolge übereinstimmt. Wenn das Recordsetfeld bei einer Übertragung vom Recordset in das Steuerelement Null ist, wird jede Auswahl aus dem Listenfeld entfernt. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordset-Feld auf Null gesetzt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldLBStringExact` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

Die `DDX_FieldRadio` Funktion ordnet eine nullbasierte **int-Membervariable** des Recordsets einer Datensatzeinstellung einer Datensatzansicht dem aktuell ausgewählten Optionsfeld in einer Gruppe von Optionsfeldern in der Datensatzansicht zu.

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID der ersten in einer Gruppe (mit Stil WS_GROUP) benachbarter Optionsfeldsteuerelemente im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Übertragen vom Recordset-Feld in die Ansicht schaltet diese Funktion den *n.-Optionsfeld* (Null-basiert) ein und schaltet die anderen Schaltflächen aus. In umgekehrter Richtung legt diese Funktion das Recordset-Feld auf die Ordinalnummer des Optionsfelds fest, das sich derzeit auf (geprüft) befindet. Bei einer Übertragung vom Recordset zum Steuerelement ist keine Schaltfläche ausgewählt, wenn das Recordset-Feld Null ist. Wenn bei einer Übertragung von der Steuerung zu Recordset kein Steuerelement ausgewählt ist, wird das Recordsetfeld auf Null gesetzt, wenn das Feld dies zulässt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldRadio` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

Die `DDX_FieldScroll` Funktion synchronisiert die Bildlaufposition eines Bildlaufleistensteuerelements in einer Datensatzansicht und eines **int-Felddatenmembers** eines Recordsets, das der Datensatzansicht zugeordnet ist (oder mit einer ganzzahligen Variablen, der Sie sie zuordnen möchten).

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID der ersten in einer Gruppe (mit Stil WS_GROUP) benachbarter Optionsfeldsteuerelemente im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten aus dem Recordset in das Steuerelement legt diese Funktion die Bildlaufposition des Bildlaufleistensteuerelements auf den im *Wert*angegebenen Wert fest. Wenn das Recordset-Feld bei einer Übertragung vom Recordset zum Steuerelement Null ist, wird das Scrollleistensteuerelement auf 0 gesetzt. Wenn bei einer Übertragung von steuerelement zu recordset das Steuerelement leer ist, ist der Wert des Recordset-Feldes 0.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldScroll` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

Die `DDX_FieldSlider` Funktion synchronisiert die Daumenposition eines Schiebereglersteuerelements in einer Datensatzansicht und eines **int-Felddatenmembers** eines Recordsets, das der Datensatzansicht zugeordnet ist (oder mit einer ganzzahligen Variablen, der Sie sie zuordnen möchten).

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Schiebereglersteuerelements.

*value*<br/>
Ein Verweis auf den zu tauschenden Wert. Dieser Parameter enthält oder wird verwendet, um die aktuelle Daumenposition des Schiebereglers festzulegen.

*pRecordset*<br/>
Ein Zeiger auf `CRecordset` das `CDaoRecordset` zugeordnete Objekt oder Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Beim Verschieben von Daten vom Recordset auf den Schieberegler legt diese Funktion die Position des Schiebereglers auf den im *Wert*angegebenen Wert fest. Wenn das Recordset-Feld bei einer Übertragung vom Recordset zum Steuerelement Null ist, wird die Position des Schiebereglersteuerelements auf 0 gesetzt. Wenn das Steuerelement bei einer Übertragung vom Steuerelement in das Recordset leer ist, ist der Wert des Recordset-Feldes 0.

`DDX_FieldSlider`tauscht keine Bereichsinformationen mit Schiebereglern aus, die einen Bereich und nicht nur eine Position festlegen können.

Verwenden Sie die erste Außerkraftsetzung der Funktion, wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die zweite Außerkraftsetzung mit den DAO-basierten Klassen.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu `CRecordView` `CDaoRecordView` DDX für und Feldern finden Sie unter [Datensatzansichten](../../data/record-views-mfc-data-access.md). Informationen zu Schiebereglern finden Sie unter [Verwenden von CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie in [DDX_FieldText.](#ddx_fieldtext) Die `DDX_FieldSlider` Rufe nach wären ähnlich.

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

Die `DDX_FieldText` Funktion verwaltet die Übertragung von **int**, **short**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**oder **BYTE** data zwischen einem Bearbeitungsfeldsteuerelement und den Felddatenelementen eines Recordsets.

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuerelements im [CRecordView-](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView-Objekt.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Ein Verweis auf ein Felddatenelement im zugeordneten `CRecordset` Objekt oder `CDaoRecordset` Objekt. Der Datentyp des Werts hängt davon `DDX_FieldText` ab, welche der überladenen Versionen von Ihnen verwendet wird.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset-](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) mit dem Daten ausgetauscht werden. Dieser Zeiger `DDX_FieldText` ermöglicht das Erkennen und Festlegen von Nullwerten.

### <a name="remarks"></a>Bemerkungen

Verwaltet für [CDaoRecordset-Objekte](../../mfc/reference/cdaorecordset-class.md) `DDX_FieldText` auch die Übertragung von [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)- und [COleCurrency-Werten.](../../mfc/reference/colecurrency-class.md) Ein leeres Bearbeitungsfeldsteuerelement gibt einen Nullwert an. Wenn das Recordset-Feld bei einer Übertragung vom Recordset in das Steuerelement Null ist, wird das Bearbeitungsfeld auf leer gesetzt. Wenn das Steuerelement bei einer Übertragung von der Steuerung zu Recordset leer ist, wird das Recordset-Feld auf Null gesetzt.

Verwenden Sie die Versionen mit [CRecordset-Parametern,](../../mfc/reference/crecordset-class.md) wenn Sie mit den ODBC-basierten Klassen arbeiten. Verwenden Sie die Versionen mit [CDaoRecordset-Parametern,](../../mfc/reference/cdaorecordset-class.md) wenn Sie mit den DAO-basierten Klassen arbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView-](../../mfc/reference/crecordview-class.md) und [CDaoRecordView-Felder](../../mfc/reference/cdaorecordview-class.md) finden Sie im Artikel [Datensatzansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Die `DoDataExchange` folgende Funktion für eine [CRecordView](../../mfc/reference/crecordview-class.md) enthält `DDX_FieldText` `IDC_COURSELIST` Funktionsaufrufe für drei Datentypen: ist ein Kombinationsfeld; Die anderen beiden Steuerelemente sind Bearbeitungsfelder. Bei der DAO-Programmierung ist der *parameter m_pSet* ein Zeiger auf ein [CRecordset](../../mfc/reference/crecordset-class.md) oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxdao.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)
