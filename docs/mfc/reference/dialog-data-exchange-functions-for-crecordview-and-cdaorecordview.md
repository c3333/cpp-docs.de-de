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
ms.openlocfilehash: 8b216941837cd79492aa6cb707481073b5321bce
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426714"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Dialogdatenaustausch-Funktionen für CRecordView und CDaoRecordView

In diesem Thema werden die DDX_Field-Funktionen aufgelistet, die zum Austauschen von Daten zwischen einem [CRecordset](../../mfc/reference/crecordset-class.md) und einem [CRecordView](../../mfc/reference/crecordview-class.md) -Formular oder einem [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)-Formular und einem [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Formular verwendet werden. DAO wird für Access-Datenbanken verwendet und wird von Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.

> [!NOTE]
>  DDX_Field Funktionen ähneln DDX-Funktionen darin, dass Sie Daten mit Steuerelementen in einem Formular austauschen. Aber im Gegensatz zu DDX tauschen Sie Daten mit den Feldern des zugeordneten Recordsetobjekt der Ansicht anstelle der Felder der Daten Satz Ansicht selbst aus. Weitere Informationen finden Sie Unterklassen `CRecordView` und `CDaoRecordView`.

### <a name="ddx_field-functions"></a>DDX_Field Funktionen

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Überträgt ganzzahlige Daten zwischen einem Recordset-Felddatenmember und dem Index der aktuellen Auswahl in einem Kombinations Feld in einer [CRecordView](../../mfc/reference/crecordview-class.md) oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Überträgt `CString` Daten zwischen einem Recordset-Felddatenmember und dem Bearbeitungs Steuerelement eines Kombinations Felds in einer `CRecordView` oder `CDaoRecordView`. Beim Verschieben von Daten aus dem Recordset in das-Steuerelement wählt diese Funktion das Element im Kombinations Feld aus, das mit den Zeichen in der angegebenen Zeichenfolge beginnt.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Überträgt `CString` Daten zwischen einem Recordset-Felddatenmember und dem Bearbeitungs Steuerelement eines Kombinations Felds in einer `CRecordView` oder `CDaoRecordView`. Beim Verschieben von Daten aus dem Recordset in das-Steuerelement wählt diese Funktion das Element im Kombinations Feld aus, das exakt mit der angegebenen Zeichenfolge übereinstimmt.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Überträgt boolesche Daten zwischen einem Recordset-Felddatenmember und einem Kontrollkästchen in einem `CRecordView` oder `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Überträgt ganzzahlige Daten zwischen einem Recordset-Felddatenmember und dem Index der aktuellen Auswahl in einem Listenfeld in einem `CRecordView` oder `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Verwaltet die Übertragung von [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Daten zwischen einem Listenfeld-Steuerelement und den Felddatenmembern eines Recordsets. Beim Verschieben von Daten aus dem Recordset in das-Steuerelement wählt diese Funktion das Element im Listenfeld aus, das mit den Zeichen in der angegebenen Zeichenfolge beginnt.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Verwaltet die Übertragung von `CString` Daten zwischen einem Listenfeld-Steuerelement und den Felddatenmembern eines Recordsets. Beim Verschieben von Daten aus dem Recordset in das-Steuerelement wählt diese Funktion das erste Element aus, das genau mit der angegebenen Zeichenfolge übereinstimmt.|
|[DDX_FieldRadio](#ddx_fieldradio)|Überträgt ganzzahlige Daten zwischen einem Recordset-Felddatenmember und einer Gruppe von Options Feldern in einem `CRecordView` oder `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Legt die Scrollposition eines Schiebe leisten-Steuer Elements in einem `CRecordView` oder `CDaoRecordView`fest oder ruft diese ab. Aufrufe von Ihrer [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) -Funktion.|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronisiert die Ziehpunkt Position eines Schieberegler-Steuer Elements in einer Daten Satz Ansicht und einen `int` Felddatenmember eines Recordsets. |
|[DDX_FieldText](#ddx_fieldtext)|Überladene Versionen stehen zum Übertragen von `int`-, **uint**-, **Long**-, `DWORD`-, [CString](../../atl-mfc-shared/reference/cstringt-class.md)-, **float**-, **Double**-, **Short**-, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)-und [COleCurrency](../../mfc/reference/colecurrency-class.md) -Daten zwischen einem Recordset-Felddatenmember und einem Bearbeitungsfeld in einem `CRecordView` oder `CDaoRecordView`zur Verfügung.|

##  <a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

Die `DDX_FieldCBIndex`-Funktion synchronisiert den Index des ausgewählten Elements im Listenfeld-Steuerelement eines Kombinations Feld-Steuer Elements in einer Daten Satz Ansicht und einen `int` Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*index*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in das-Steuerelement verschieben, legt diese Funktion die Auswahl im-Steuerelement auf Grundlage des in *Index*angegebenen Werts fest. Bei einer Übertragung vom Recordset an das-Steuerelement legt MFC den Wert des Indexes auf 0 fest, wenn das Recordsetfeld NULL ist. Wenn das Steuerelement bei einer Übertragung von einem Steuerelement zu einem Recordset leer ist oder wenn kein Element ausgewählt ist, wird das Recordsetfeld auf 0 festgelegt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Das Beispiel wäre für `DDX_FieldCBIndex`ähnlich.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdao.h

##  <a name="ddx_fieldcbstring"></a>DDX_FieldCBString

Die `DDX_FieldCBString`-Funktion verwaltet die Übertragung von [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Daten zwischen dem Bearbeitungs Steuerelement eines Kombinations Feld-Steuer Elements in einer Daten Satz Ansicht und einem `CString` Field-Datenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in das-Steuerelement verschieben, legt diese Funktion die aktuelle Auswahl im Kombinations Feld auf die erste Zeile fest, die mit den Zeichen in der Zeichenfolge beginnt, die unter *Wert*angegeben ist. Wenn bei einer Übertragung vom Recordset an das-Steuerelement das Recordsetfeld NULL ist, wird eine beliebige Auswahl aus dem Kombinations Feld entfernt, und das Bearbeitungs Steuerelement des Kombinations Felds wird auf leer festgelegt. Wenn das Steuerelement bei einer Übertragung von einem Steuerelement zu einem Recordset leer ist, wird das Recordsetfeld auf NULL festgelegt, wenn das Feld dies zulässt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Das Beispiel enthält einen `DDX_FieldCBString`aufzurufenden.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

## <a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

Die `DDX_FieldCBStringExact`-Funktion verwaltet die Übertragung von [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Daten zwischen dem Bearbeitungs Steuerelement eines Kombinations Feld-Steuer Elements in einer Daten Satz Ansicht und einem `CString` Field-Datenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in das-Steuerelement verschieben, legt diese Funktion die aktuelle Auswahl im Kombinations Feld auf die erste Zeile fest, die exakt mit der in *value*angegebenen Zeichenfolge übereinstimmt. Wenn bei einer Übertragung vom Recordset an das-Steuerelement das Recordsetfeld NULL ist, wird eine beliebige Auswahl aus dem Kombinations Feld entfernt, und das Bearbeitungsfeld des Kombinations Felds wird auf leer festgelegt. Wenn das Steuerelement leer ist, wird das Recordsetfeld bei einer Übertragung von einem Steuerelement zu einem Recordset auf NULL festgelegt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldCBStringExact` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldcheck"></a>DDX_FieldCheck

Die `DDX_FieldCheck`-Funktion verwaltet die Übertragung von **int** -Daten zwischen einem Kontrollkästchen-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **int** -Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kontrollkästchen-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn `DDX_FieldCheck` aufgerufen wird, wird der *Wert* auf den aktuellen Zustand des Kontrollkästchen-Steuer Elements festgelegt, oder der Zustand des-Steuer Elements wird abhängig von der Übertragungsrichtung auf *value*festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

Die `DDX_FieldLBIndex`-Funktion synchronisiert den Index des ausgewählten Elements in einem Listenfeld-Steuerelement in einer Daten Satz Ansicht und einen **int** -Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*index*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in das-Steuerelement verschieben, legt diese Funktion die Auswahl im-Steuerelement auf Grundlage des in *Index*angegebenen Werts fest. Bei einer Übertragung vom Recordset an das-Steuerelement legt MFC den Wert des Indexes auf 0 fest, wenn das Recordsetfeld NULL ist. Wenn das-Steuerelement leer ist, wird bei einer Übertragung von einem Steuerelement zum Recordset das Recordsetfeld auf 0 festgelegt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) .

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldlbstring"></a>DDX_FieldLBString

Der `DDX_FieldLBString` kopiert die aktuelle Auswahl eines Listenfeld-Steuer Elements in einer Daten Satz Ansicht in ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

In umgekehrter Richtung legt diese Funktion die aktuelle Auswahl im Listenfeld auf die erste Zeile fest, die mit den Zeichen in der durch *value*angegebenen Zeichenfolge beginnt. Bei einer Übertragung vom Recordset an das-Steuerelement wird eine beliebige Auswahl aus dem Listenfeld entfernt, wenn das Recordsetfeld NULL ist. Wenn das Steuerelement leer ist, wird das Recordsetfeld bei einer Übertragung von einem Steuerelement zu einem Recordset auf NULL festgelegt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldLBString` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

Die `DDX_FieldLBStringExact`-Funktion kopiert die aktuelle Auswahl eines Listenfeld-Steuer Elements in einer Daten Satz Ansicht in ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

In umgekehrter Richtung legt diese Funktion die aktuelle Auswahl im Listenfeld auf die erste Zeile fest, die exakt mit der in *value*angegebenen Zeichenfolge übereinstimmt. Bei einer Übertragung vom Recordset an das-Steuerelement wird eine beliebige Auswahl aus dem Listenfeld entfernt, wenn das Recordsetfeld NULL ist. Wenn das Steuerelement leer ist, wird das Recordsetfeld bei einer Übertragung von einem Steuerelement zu einem Recordset auf NULL festgelegt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldLBStringExact` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldradio"></a>DDX_FieldRadio

Die `DDX_FieldRadio`-Funktion ordnet eine Null basierte **int** -Member-Variable des Recordsets einer Daten Satz Ansicht mit dem aktuell ausgewählten Optionsfeld in einer Gruppe von Options Feldern in der Daten Satz Ansicht zu.

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID des ersten in einer Gruppe (mit Stil WS_GROUP) der angrenzenden Optionsfeld-Steuerelemente im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Bei der Übertragung aus dem Recordsetfeld in die Ansicht aktiviert diese *Funktion das Options* Feld (null basiert) und deaktiviert die anderen Schaltflächen. In umgekehrter Richtung legt diese Funktion das Recordsetfeld auf die Ordinalzahl des Options Felds fest, das zurzeit aktiviert ist (aktiviert). Wenn bei einer Übertragung vom Recordset zum-Steuerelement das Recordsetfeld NULL ist, wird keine Schaltfläche ausgewählt. Wenn beim Übertragen von Steuerelementen zu Recordsets kein Steuerelement ausgewählt ist, wird das Recordsetfeld auf NULL festgelegt, wenn das Feld dies zulässt.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldRadio` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

##  <a name="ddx_fieldscroll"></a>DDX_FieldScroll

Die `DDX_FieldScroll`-Funktion synchronisiert die Bild Lauf Position eines Schiebe leisten-Steuer Elements in einer Daten Satz Ansicht und einen **int** -Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist (oder mit einer beliebigen ganzzahligen Variablen, der Sie zugeordnet werden).

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID des ersten in einer Gruppe (mit Stil WS_GROUP) der angrenzenden Optionsfeld-Steuerelemente im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in das-Steuerelement verschieben, legt diese Funktion die Bild Lauf Position des Schiebe leisten-Steuer Elements auf den in *value*angegebenen Wert fest. Bei einer Übertragung vom Recordset an das-Steuerelement wird das ScrollBar-Steuerelement auf 0 festgelegt, wenn das Recordsetfeld NULL ist. Wenn das Steuerelement bei einer Übertragung von einem Steuerelement zu einem Recordset leer ist, ist der Wert des Recordset-Felds 0.

Verwenden Sie die erste Version, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite Version, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldScroll` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

  ## <a name="ddx_fieldslider"></a>DDX_FieldSlider
Die `DDX_FieldSlider`-Funktion synchronisiert die Ziehpunkt Position eines Schieberegler-Steuer Elements in einer Daten Satz Ansicht und einen **int** -Felddatenmember eines Recordsets, das der Daten Satz Ansicht zugeordnet ist (oder mit einer beliebigen ganzzahligen Variablen, der Sie zugeordnet werden).

### <a name="syntax"></a>Syntax

  ```
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
Ein Zeiger auf ein [CDataExchange](cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Schieberegler-Steuer Elements.

*value*<br/>
Ein Verweis auf den auszutauschenden Wert. Dieser Parameter enthält oder wird verwendet, um die aktuelle Thumb-Position des Schieberegler-Steuer Elements festzulegen.

*pRecordset*<br/>
Ein Zeiger auf den zugeordneten `CRecordset` oder `CDaoRecordset` Objekt, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Hinweise

Wenn Sie Daten aus dem Recordset in den Schieberegler verschieben, legt diese Funktion die Position des Schiebereglers auf den in *value*angegebenen Wert fest. Wenn bei einer Übertragung vom Recordset zum-Steuerelement das Recordsetfeld NULL ist, wird die Position des Schieberegler-Steuer Elements auf 0 festgelegt. Wenn das Steuerelement bei einer Übertragung vom-Steuerelement an das Recordset leer ist, ist der Wert des Recordset-Felds 0.

`DDX_FieldSlider` tauschen keine Bereichs Informationen mit Schieberegler-Steuerelementen aus, die einen Bereich anstatt einfach eine Position festlegen können.

Verwenden Sie die erste außer Kraft setzung der-Funktion, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die zweite außer Kraft setzung mit den DAO-basierten Klassen.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für `CRecordView`-und `CDaoRecordView` Felder finden Sie unter [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md). Weitere Informationen zu Schieberegler-Steuerelementen finden [Sie unter Verwenden von CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Beispiel

Ein allgemeines DDX_Field Beispiel finden Sie unter [DDX_FieldText](#ddx_fieldtext) . Aufrufe an `DDX_FieldSlider` wären ähnlich.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdao.h

##  <a name="ddx_fieldtext"></a>DDX_FieldText

Die `DDX_FieldText`-Funktion verwaltet die Übertragung von Daten vom Typ " **int**", " **Short**", " **Long**", "DWORD", " [CString](../../atl-mfc-shared/reference/cstringt-class.md)", " **float**", " **Double**", " **bool**" oder " **Byte** " zwischen einem Bearbeitungsfeld-Steuerelement

```
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
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Steuer Elements im [CRecordView](../../mfc/reference/crecordview-class.md) -oder [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Objekt.

*value*<br/>
Ein Verweis auf einen Felddatenmember im zugeordneten `CRecordset` oder `CDaoRecordset`-Objekt. Der Datentyp des Werts hängt davon ab, welche der überladenen Versionen von `DDX_FieldText` Sie verwenden.

*pRecordset*<br/>
Ein Zeiger auf das [CRecordset](../../mfc/reference/crecordset-class.md) -oder [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, mit dem Daten ausgetauscht werden. Dieser Zeiger ermöglicht `DDX_FieldText` das erkennen und Festlegen von NULL-Werten.

### <a name="remarks"></a>Hinweise

Für [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekte `DDX_FieldText` auch die Übertragung von [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)-und [COleCurrency](../../mfc/reference/colecurrency-class.md) -Werten verwaltet. Ein leeres Bearbeitungsfeld-Steuerelement gibt einen NULL-Wert an. Bei einer Übertragung vom Recordset zum-Steuerelement ist das Feld "Bearbeiten" auf "leer" festgelegt, wenn das Recordsetfeld NULL ist. Wenn das Steuerelement leer ist, wird das Recordsetfeld bei einer Übertragung von einem Steuerelement zu einem Recordset auf NULL festgelegt.

Verwenden Sie die-Versionen mit [CRecordset](../../mfc/reference/crecordset-class.md) -Parametern, wenn Sie mit den ODBC-basierten Klassenarbeiten. Verwenden Sie die-Versionen mit [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Parametern, wenn Sie mit den DAO-basierten Klassenarbeiten.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Beispiele und weitere Informationen zu DDX für [CRecordView](../../mfc/reference/crecordview-class.md) -und [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) -Felder finden Sie im Artikel [Daten Satz Ansichten](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Beispiel

Die folgende `DoDataExchange` Funktion für eine [CRecordView](../../mfc/reference/crecordview-class.md) enthält `DDX_FieldText` Funktionsaufrufe für drei Datentypen: `IDC_COURSELIST` ist ein Kombinations Feld. die anderen beiden Steuerelemente sind Bearbeitungsfelder. Bei der DAO-Programmierung ist der *m_pSet* -Parameter ein Zeiger auf ein [CRecordset](../../mfc/reference/crecordset-class.md) oder ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Voraussetzungen

  **Header** afxdao. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](mfc-macros-and-globals.md)
