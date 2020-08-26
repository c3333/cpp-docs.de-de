---
title: Standard-Dialogdatenaustauschroutinen
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: bed60094b25bcc3b1994aa904a8c20324be2abae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844495"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standard-Dialogdatenaustauschroutinen

In diesem Thema werden die Standard Routinen für den Dialog Datenaustausch (DDX) aufgelistet, die für allgemeine MFC-Dialogfelder verwendet werden.

> [!NOTE]
> Die Standard Routinen für den Dialog Datenaustausch werden in der Header Datei afxdd_. h definiert. Anwendungen sollten jedoch AFXWIN. h enthalten.

### <a name="ddx-functions"></a>DDX-Funktionen

|Name|Beschreibung|
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Initialisiert oder Ruft den Index der aktuellen Auswahl eines Kombinations Feld-Steuer Elements ab.|
|[DDX_CBString](#ddx_cbstring)|Initialisiert oder Ruft den aktuellen Inhalt des Bearbeitungs Felds eines Kombinations Feld-Steuer Elements ab.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Initialisiert oder Ruft den aktuellen Inhalt des Bearbeitungs Felds eines Kombinations Feld-Steuer Elements ab.|
|[DDX_Check](#ddx_check)|Initialisiert oder Ruft den aktuellen Zustand eines Kontrollkästchen-Steuer Elements ab.|
|[DDX_Control](#ddx_control)|Unterklassen eines angegebenen Steuer Elements in einem Dialogfeld.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialisiert oder ruft Datums-und/oder Zeit Daten eines Steuer Elements für die Datums-und Uhrzeit Auswahl ab.|
|[DDX_IPAddress](#ddx_ipaddress)|Initialisiert oder Ruft den aktuellen Wert eines IP-Adress Steuer Elements ab.|
|[DDX_LBIndex](#ddx_lbindex)|Initialisiert oder Ruft den Index der aktuellen Auswahl eines Listenfeld-Steuer Elements ab.|
|[DDX_LBString](#ddx_lbstring)|Initialisiert oder ruft die aktuelle Auswahl in einem Listenfeld-Steuerelement ab.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialisiert oder ruft die aktuelle Auswahl in einem Listenfeld-Steuerelement ab.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Erstellt ein .NET-Steuerelement mit der Ressourcen-ID des Steuer Elements.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialisiert oder Ruft den aktuellen Wert eines Monatskalender-Steuer Elements ab.|
|[DDX_Radio](#ddx_radio)|Initialisiert oder Ruft den NULL basierten Index des Radio-Steuer Elements ab, das momentan innerhalb einer Radio-Steuerelement Gruppe aktiviert ist.|
|[DDX_Scroll](#ddx_scroll)|Initialisiert oder ruft die aktuelle Position des Zieh Punkts eines Bild Lauf Steuer Elements ab.|
|[DDX_Slider](#ddx_slider)|Initialisiert oder ruft die aktuelle Position des Zieh Punkts eines Schieberegler-Steuer Elements ab.|
|[DDX_Text](#ddx_text)|Initialisiert oder Ruft den aktuellen Wert eines Bearbeitungs Steuer Elements ab.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a> DDX_CBIndex

Die `DDX_CBIndex` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einem Kombinations Feld-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*Index*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBIndex` aufgerufen wird, wird der *Index* auf den Index der aktuellen Kombinations Feldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Index* auf 0 festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a> DDX_CBString

Die `DDX_CBString` -Funktion verwaltet die Übertragung von `CString` Daten zwischen dem Bearbeitungs Steuerelement eines Kombinations Feld-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem `CString` Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBString` aufgerufen wird, wird *value* auf die aktuelle Kombinations Feldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge 0 (null) festgelegt.

> [!NOTE]
> Wenn das Kombinations Feld ein Dropdown-Listenfeld ist, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a> DDX_CBStringExact

Die `DDX_CBStringExact` -Funktion verwaltet die Übertragung von `CString` Daten zwischen dem Bearbeitungs Steuerelement eines Kombinations Feld-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem `CString` Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBStringExact` aufgerufen wird, wird *value* auf die aktuelle Kombinations Feldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge 0 (null) festgelegt.

> [!NOTE]
> Wenn das Kombinations Feld ein Dropdown-Listenfeld ist, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_check"></a><a name="ddx_check"></a> DDX_Check

Die `DDX_Check` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einem Kontrollkästchen-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Kontrollkästchen-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Check` aufgerufen wird, wird der *Wert* auf den aktuellen Zustand des Kontrollkästchen-Steuer Elements festgelegt. Eine Liste der möglichen Zustands Werte finden Sie unter [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) in der Windows SDK.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_control"></a><a name="ddx_control"></a> DDX_Control

Die- `DDX_Control` Funktion Unterklassen das von *nidc*angegebene Steuerelement des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*nIDC*<br/>
Die Ressourcen-ID des Steuer Elements, das unter klassifiziert werden soll.

*rcontrol*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, das sich auf das angegebene Steuerelement bezieht.

### <a name="remarks"></a>Bemerkungen

Das *PDX* -Objekt wird vom Framework bereitgestellt, wenn die- `DoDataExchange` Funktion aufgerufen wird. Daher `DDX_Control` sollte nur innerhalb ihrer außer Kraft Setzung von aufgerufen werden `DoDataExchange` .

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a> DDX_DateTimeCtrl

Die `DDX_DateTimeCtrl` -Funktion verwaltet die Übertragung von Datums-und/oder Zeit Daten zwischen einem Steuerelement für die Datums-und Zeitauswahl ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) in einem Dialogfeld oder einem Formular Ansichts Objekt und entweder einem [ctime](../../atl-mfc-shared/reference/ctime-class.md) -oder einem [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Datenmember des Dialog Felds oder des Formular Ansichts Objekts.

```cpp
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*nIDC*<br/>
Die Ressourcen-ID des Steuer Elements für die Datums-und Uhrzeit Auswahl, das der Element Variablen zugeordnet ist.

*value*<br/>
In den ersten beiden Versionen ein Verweis auf eine- `CTime` oder-Element `COleDateTime` Variable, ein Dialogfeld, eine Formularansicht oder ein Steuerelement Ansichts Objekt, mit dem Daten ausgetauscht werden. In der dritten Version ein Verweis auf ein `CString` Datenmember-Steuerungs Ansichts Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_DateTimeCtrl` aufgerufen wird, wird der *Wert* auf den aktuellen Zustand des Steuer Elements für die Datums-und Uhrzeit Auswahl festgelegt, oder das Steuerelement wird auf *value*festgelegt, abhängig von der Richtung des Austauschs.

In der dritten Version von wird `DDX_DateTimeCtrl` die Übertragung von `CString` Daten zwischen einem Datums-/uhrzeitsteuerelement und einem [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Datenmember des Steuerelement Ansichts Objekts verwaltet. Die Zeichenfolge wird mit den Regeln des aktuellen Gebiets Schemas zum Formatieren von Datumsangaben und Uhrzeiten formatiert

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a> DDX_ManagedControl

Erstellt ein .NET-Steuerelement mit der Ressourcen-ID des Steuer Elements.

### <a name="syntax"></a>Syntax

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Klassen](cdataexchange-class.md) Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*control*<br/>
Ein Verweis auf ein [CWinFormsControl-Klassen](cwinformscontrol-class.md) Objekt.

### <a name="remarks"></a>Bemerkungen

`DDX_ManagedControl` Ruft [CWinFormsControl:: kreatemanagedcontrol](cwinformscontrol-class.md#createmanagedcontrol) auf, um ein Steuerelement zu erstellen, das mit der Ressourcen Steuerungs-ID übereinstimmt. Verwenden `DDX_ManagedControl` Sie, um Steuerelemente aus Ressourcen-IDs in " [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)" zu erstellen. Für den Datenaustausch müssen Sie die DDX/DDV-Funktionen nicht mit Windows Forms-Steuerelementen verwenden.

Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von DDX/DDV-Datenbindung mit Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms. h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a> DDX_IPAddress

Die `DDX_IPAddress` -Funktion verwaltet die Übertragung von Daten zwischen einem IP-Adress Steuerelement und einem Datenmember des Steuerelement Ansichts Objekts.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des IP-Adress Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf das DWORD-Element, das den vier-Feldwert des IP-Adress Steuer Elements enthält. Die Felder werden wie folgt ausgefüllt oder gelesen.

|Feld|Bits, die den Feldwert enthalten|
|-----------|-------------------------------------|
|3|0 bis 7|
|2|8 bis 15|
|1|16 bis 23|
|0|24 bis 31|

Verwenden Sie den Win32- [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) , um den Wert zu lesen, oder verwenden Sie [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) , um den Wert zu füllen. Diese Nachrichten werden in der Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_IPAddress` aufgerufen wird, wird der *Wert* entweder aus dem IP-Adress Steuerelement gelesen, oder der *Wert* wird in das Steuerelement geschrieben, abhängig von der Richtung des Austauschs.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a> DDX_LBIndex

Die `DDX_LBIndex` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einem Listenfeld-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*Index*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBIndex` aufgerufen wird, wird der *Index* auf den Index der aktuellen Listenfeld Auswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Index* auf-1 festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a> DDX_LBString

Die `DDX_LBString` -Funktion verwaltet die Übertragung von `CString` Daten zwischen einem Listenfeld-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem `CString` Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBString` aufgerufen wird, um Daten in ein Listenfeld-Steuerelement zu übertragen, wird das erste Element im-Steuerelement ausgewählt, dessen Anfangs *Wert dem Wert* entspricht. (Verwenden Sie [DDX_LBStringExact](#ddx_lbstringexact), um das gesamte Element und nicht nur ein Präfix abzugleichen.) Wenn keine Übereinstimmungen vorhanden sind, werden keine Elemente ausgewählt. Beim Vergleich wird die Groß-/Kleinschreibung nicht beachtet.

Wenn `DDX_LBString` aufgerufen wird, um Daten aus einem Listenfeld-Steuerelement zu übertragen, wird *value* auf die aktuelle Listenfeld Auswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge 0 (null) festgelegt.

> [!NOTE]
> Wenn das Listenfeld ein Dropdown-Listenfeld ist, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a> DDX_LBStringExact

Die `DDX_CBStringExact` -Funktion verwaltet die Übertragung von `CString` Daten zwischen dem Bearbeitungs Steuerelement eines Listenfeld-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem `CString` Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBStringExact` aufgerufen wird, um Daten in ein Listenfeld-Steuerelement zu übertragen, wird das erste Element im Steuerelement ausgewählt, das mit dem *Wert* übereinstimmt. (Verwenden Sie [DDX_LBString](#ddx_lbstring), um nur ein Präfix anstelle des gesamten Elements abzugleichen.) Wenn keine Übereinstimmungen vorhanden sind, werden keine Elemente ausgewählt. Beim Vergleich wird die Groß-/Kleinschreibung nicht beachtet.

Wenn `DDX_CBStringExact` aufgerufen wird, um Daten aus einem Listenfeld-Steuerelement zu übertragen, wird *value* auf die aktuelle Listenfeld Auswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge 0 (null) festgelegt.

> [!NOTE]
> Wenn das Listenfeld ein Dropdown-Listenfeld ist, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a> DDX_MonthCalCtrl

Die `DDX_MonthCalCtrl` -Funktion verwaltet die Übertragung von Datumsdaten zwischen einem Monatskalender-Steuerelement ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und entweder einem [ctime](../../atl-mfc-shared/reference/ctime-class.md) -oder einem [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*nIDC*<br/>
Die Ressourcen-ID des Monatskalender-Steuer Elements, das der Element Variablen zugeordnet ist.

*value*<br/>
Ein Verweis auf eine- `CTime` oder- `COleDateTime` Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das-Steuerelement verwaltet nur einen Datumswert. Die Zeitfelder im Zeit Objekt werden so festgelegt, dass Sie die Erstellungszeit des Steuerelement Fensters widerspiegeln, oder die Zeit, die im Steuerelement mit einem Aufruf von festgelegt wurde `CMonthCalCtrl::SetCurSel` .

Wenn `DDX_MonthCalCtrl` aufgerufen wird, wird der *Wert* auf den aktuellen Zustand des Monatskalender-Steuer Elements festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_radio"></a><a name="ddx_radio"></a> DDX_Radio

Die `DDX_Radio` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einer Radio-Steuerelement Gruppe in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts. Der Wert des **`int`** Datenmembers wird bestimmt, welches Optionsfeld innerhalb der Gruppe ausgewählt ist.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des ersten Options Felds in der Gruppe.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Radio` aufgerufen wird, wird der *Wert* auf den aktuellen Zustand der Optionsfeld-Steuerelement Gruppe festgelegt. Der Wert wird als 0-basierter Index des Options Felds festgelegt, das derzeit aktiviert ist, oder-1, wenn keine Options Felder aktiviert sind.

Wenn beispielsweise das erste Optionsfeld in der Gruppe (die Schaltfläche mit WS_GROUP Format) aktiviert ist, ist der Wert des Elements **`int`** 0 usw.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a> DDX_Scroll

Die `DDX_Scroll` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einem Bild Lauf leisten-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des ScrollBar-Steuer Elements, das der Steuerelement Eigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Scroll` aufgerufen wird, wird der *Wert* auf die aktuelle Position des Zieh Punkts des Steuer Elements festgelegt. Weitere Informationen zu den Werten, die der aktuellen Position des Steuer Elements des Steuer Elements zugeordnet sind, finden Sie unter [getscrollpos](/windows/win32/api/winuser/nf-winuser-getscrollpos) in der Windows SDK.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_slider"></a><a name="ddx_slider"></a> DDX_Slider

Die `DDX_Slider` -Funktion verwaltet die Übertragung von **`int`** Daten zwischen einem Schieberegler-Steuerelement in einem Dialogfeld oder einer Formularansicht und einem **`int`** Datenmember des Dialog Felds bzw. des Formular Ansichts Objekts.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Schieberegler-Steuer Elements.

*value*<br/>
Ein Verweis auf den auszutauschenden Wert. Dieser Parameter enthält die aktuelle Position des Schieberegler-Steuer Elements oder legt diese fest.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Slider` aufgerufen wird, wird der *Wert* auf die aktuelle Position des Thumb-Steuer Elements festgelegt, oder der Wert erhält die Position, abhängig von der Richtung des Austauschs.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Weitere Informationen zu Schieberegler-Steuerelementen finden [Sie unter Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddx_text"></a><a name="ddx_text"></a> DDX_Text

Die `DDX_Text` -Funktion verwaltet die Übertragung von **`int`** -, **uint**-, DWORD-,-,- **`long`** `CString` **`float`** oder **`double`** -Daten zwischen einem Bearbeitungs Steuerelement in einem Dialogfeld, einer Formularansicht oder einer Steuerelement Ansicht und einem [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Bearbeitungs Steuer Elements im Dialogfeld, in der Formularansicht oder im Steuerungs Ansichts Objekt.

*value*<br/>
Ein Verweis auf einen Datenmember im Dialogfeld, in der Formularansicht oder im Steuerungs Ansichts Objekt. Der Datentyp des *Werts* hängt davon ab, welche der überladenen Versionen von `DDX_Text` Sie verwenden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="see-also"></a>Weitere Informationen

[Validierungs Routinen für Standard Dialogfelder](standard-dialog-data-validation-routines.md)<br/>
[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CWinFormsControl:: kreatemanagedcontrol](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)
