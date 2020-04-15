---
title: Standard-Dialogdatenaustauschroutinen
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372932"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standard-Dialogdatenaustauschroutinen

In diesem Thema werden die Standard-Dialogdatenaustauschroutinen (DDX) aufgeführt, die für allgemeine MFC-Dialogsteuerelemente verwendet werden.

> [!NOTE]
> Die Standardmäßigen Dialogdatenaustauschroutinen sind in der Headerdatei afxdd_.h definiert. Die Anwendungen sollten jedoch afxwin.h enthalten.

### <a name="ddx-functions"></a>DDX-Funktionen

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Initialisiert oder ruft den Index der aktuellen Auswahl eines Kombinationsfeldsteuerelements ab.|
|[DDX_CBString](#ddx_cbstring)|Initialisiert oder ruft den aktuellen Inhalt des Bearbeitungsfelds eines Kombinationsfeldsteuerelements ab.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Initialisiert oder ruft den aktuellen Inhalt des Bearbeitungsfelds eines Kombinationsfeldsteuerelements ab.|
|[DDX_Check](#ddx_check)|Initialisiert oder ruft den aktuellen Status eines Kontrollkästchen-Steuerelements ab.|
|[DDX_Control](#ddx_control)|Unterklassen eines bestimmten Steuerelements in einem Dialogfeld.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialisiert oder ruft Datums- und/oder Uhrzeitdaten eines Datums- und Uhrzeitauswahlsteuerelements ab.|
|[DDX_IPAddress](#ddx_ipaddress)|Initialisiert oder ruft den aktuellen Wert eines IP-Adresssteuerelements ab.|
|[DDX_LBIndex](#ddx_lbindex)|Initialisiert oder ruft den Index der aktuellen Auswahl eines Listenfeldsteuerelements ab.|
|[DDX_LBString](#ddx_lbstring)|Initialisiert oder ruft die aktuelle Auswahl innerhalb eines Listenfeldsteuerelements ab.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialisiert oder ruft die aktuelle Auswahl innerhalb eines Listenfeldsteuerelements ab.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Erstellt ein .NET-Steuerelement, das der Ressourcen-ID des Steuerelements entspricht.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialisiert oder ruft den aktuellen Wert eines Monatskalendersteuerelements ab.|
|[DDX_Radio](#ddx_radio)|Initialisiert oder ruft den 0-basierten Index des Funksteuerelements ab, das derzeit in einer Funksteuerungsgruppe überprüft wird.|
|[DDX_Scroll](#ddx_scroll)|Initialisiert oder ruft die aktuelle Position des Daumens eines Bildlaufsteuerelements ab.|
|[DDX_Slider](#ddx_slider)|Initialisiert oder ruft die aktuelle Position des Daumens eines Schiebereglers ab.|
|[DDX_Text](#ddx_text)|Initialisiert oder ruft den aktuellen Wert eines Bearbeitungssteuerelements ab.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

Die `DDX_CBIndex` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Kombinationsfeldsteuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*Index*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBIndex` aufgerufen wird, wird *der Index* auf den Index der aktuellen Kombinationsfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Index* auf 0 gesetzt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

Die `DDX_CBString` Funktion verwaltet `CString` die Datenübertragung zwischen dem Bearbeitungssteuerelement eines Kombinationsfeldsteuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem `CString` Datenelement des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBString` aufgerufen wird, wird *der Wert* auf die aktuelle Kombinationsfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge Null festgelegt.

> [!NOTE]
> Wenn es sich bei dem Kombinationsfeld um ein Dropdown-Listenfeld handelt, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

Die `DDX_CBStringExact` Funktion verwaltet `CString` die Datenübertragung zwischen dem Bearbeitungssteuerelement eines Kombinationsfeldsteuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem `CString` Datenelement des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_CBStringExact` aufgerufen wird, wird *der Wert* auf die aktuelle Kombinationsfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge Null festgelegt.

> [!NOTE]
> Wenn es sich bei dem Kombinationsfeld um ein Dropdown-Listenfeld handelt, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

Die `DDX_Check` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Kontrollkästchen-Steuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Kontrollkästchen-Steuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Check` aufgerufen wird, wird *der Wert* auf den aktuellen Status des Kontrollkästchen-Steuerelements festgelegt. Eine Liste der möglichen Statuswerte finden Sie unter [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) im Windows SDK.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

Die `DDX_Control` Funktion unterklassen das Steuerelement, das durch *nIDC*angegeben wird, des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md)

*nIDC*<br/>
Die Ressourcen-ID des Steuerelements, das unterklassifiziert werden soll.

*rControl*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, das sich auf das angegebene Steuerelement bezieht.

### <a name="remarks"></a>Bemerkungen

Das *pDX-Objekt* wird vom `DoDataExchange` Framework bereitgestellt, wenn die Funktion aufgerufen wird. Daher `DDX_Control` sollte nur innerhalb Ihrer Außerkraftsetzung von `DoDataExchange`aufgerufen werden.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

Die `DDX_DateTimeCtrl` Funktion verwaltet die Übertragung von Datums- und/oder Zeitdaten zwischen einem Datums- und Uhrzeitauswahlsteuerelement ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) in einem Dialogfeld oder Formularansichtsobjekt und entweder einem [CTime-](../../atl-mfc-shared/reference/ctime-class.md) oder einem [COleDateTime-Datenelement](../../atl-mfc-shared/reference/coledatetime-class.md) des Dialogfelds oder Formularansichtsobjekts.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*nIDC*<br/>
Die Ressourcen-ID des Datums- und Uhrzeitauswahlsteuerelements, das der Membervariablen zugeordnet ist.

*value*<br/>
In den ersten beiden Versionen `CTime` ein `COleDateTime` Verweis auf eine oder eine Elementvariable, ein Dialogfeld, eine Formularansicht oder ein Steuerelementansichtsobjekt, mit dem Daten ausgetauscht werden. In der dritten Version ein `CString` Verweis auf ein Datenmembersteuerelementansichtsobjekt.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_DateTimeCtrl` aufgerufen wird, wird der *Wert* auf den aktuellen Status des Datums- und Uhrzeitauswahlsteuerelements festgelegt, oder das Steuerelement wird auf *Wert*festgelegt, abhängig von der Richtung des Austauschs.

Verwaltet in der `DDX_DateTimeCtrl` dritten obigen `CString` Version die Datenübertragung zwischen einem Datumszeitmesser und einem [CString-Datenmember](../../atl-mfc-shared/reference/cstringt-class.md) des Steuerelementansichtsobjekts. Die Zeichenfolge wird mithilfe der Regeln des aktuellen Gebietsschemas für die Formatierung von Datums- und Uhrzeitangaben formatiert.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

Erstellt ein .NET-Steuerelement, das der Ressourcen-ID des Steuerelements entspricht.

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
Ein Zeiger auf ein [CDataExchange-Klassenobjekt.](cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Steuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*Steuerung*<br/>
Ein Verweis auf ein [CWinFormsControl-Klassenobjekt.](cwinformscontrol-class.md)

### <a name="remarks"></a>Bemerkungen

`DDX_ManagedControl`ruft [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) auf, um ein Steuerelement zu erstellen, das der Ressourcensteuerungs-ID entspricht. Verwenden `DDX_ManagedControl` Sie diese Datei zum Erstellen von Steuerelementen aus Ressourcen-IDs in [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Für den Datenaustausch müssen Sie die DDX/DDV-Funktionen nicht mit Windows Forms-Steuerelementen verwenden.

Weitere Informationen finden Sie unter [Gewusst wie: DDX/DDV-Datenbindung mit Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Anforderungen

**Kopf:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

Die `DDX_IPAddress` Funktion verwaltet die Datenübertragung zwischen einem IP-Adresssteuerelement und einem Datenmember des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des IP-Adresssteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf das DWORD, das den Vier-Feld-Wert des IP-Adresssteuerelements enthält. Die Felder werden wie folgt gefüllt oder gelesen.

|Feld|Bits, die den Feldwert enthalten|
|-----------|-------------------------------------|
|3|0 bis 7|
|2|8 bis 15|
|1|16 bis 23|
|0|24 bis 31|

Verwenden Sie die Win32-IPM_GETADDRESS, um den Wert zu lesen, oder verwenden Sie [IPM_SETADDRESS,](/windows/win32/Controls/ipm-setaddress) um den Wert zu füllen. [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Diese Meldungen werden im Windows SDK beschrieben.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_IPAddress` aufgerufen wird, wird *der Wert* entweder aus dem IP-Adresssteuerelement gelesen, oder *der Wert* wird in das Steuerelement geschrieben, abhängig von der Richtung des Austauschs.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

Die `DDX_LBIndex` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Listenfeldsteuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Listenfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*Index*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBIndex` der *Index* aufgerufen wird, wird er auf den Index der aktuellen Listenfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Index* auf -1 festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

Die `DDX_LBString` Funktion verwaltet `CString` die Übertragung von Daten zwischen einem Listenfeldsteuerelement in einem `CString` Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem Datenelement des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Listenfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBString` aufgerufen wird, um Daten an ein Listenfeldsteuerelement zu übertragen, wird das erste Element im Steuerelement ausgewählt, dessen *Anfangsübereinstimmungswert* ausgewählt ist. (Um das gesamte Element und nicht nur ein Präfix abzugleichen, verwenden Sie [DDX_LBStringExact](#ddx_lbstringexact).) Wenn keine Übereinstimmungen vorhanden sind, werden keine Elemente ausgewählt. Bei der Übereinstimmung wird die Groß-/Kleinschreibung nicht berücksichtigt.

Wenn `DDX_LBString` aufgerufen wird, um Daten von einem Listenfeldsteuerelement zu übertragen, wird der *Wert* auf die aktuelle Listenfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge Null festgelegt.

> [!NOTE]
> Wenn es sich bei dem Listenfeld um ein Dropdown-Listenfeld handelt, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

Die `DDX_CBStringExact` Funktion verwaltet `CString` die Datenübertragung zwischen dem Bearbeitungssteuerelement eines Listenfeldsteuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem `CString` Datenelement des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Listenfeldsteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_LBStringExact` zum Übertragen von Daten an ein Listenfeldsteuerelement aufgerufen wird, wird das erste Element im Steuerelement ausgewählt, das dem *Wert* entspricht. (Um nur ein Präfix statt des gesamten Elements zu entsprechen, verwenden Sie [DDX_LBString](#ddx_lbstring).) Wenn keine Übereinstimmungen vorhanden sind, werden keine Elemente ausgewählt. Bei der Übereinstimmung wird die Groß-/Kleinschreibung nicht berücksichtigt.

Wenn `DDX_CBStringExact` aufgerufen wird, um Daten von einem Listenfeldsteuerelement zu übertragen, wird der *Wert* auf die aktuelle Listenfeldauswahl festgelegt. Wenn kein Element ausgewählt ist, wird der *Wert* auf eine Zeichenfolge mit der Länge Null festgelegt.

> [!NOTE]
> Wenn es sich bei dem Listenfeld um ein Dropdown-Listenfeld handelt, ist der ausgetauschte Wert auf 255 Zeichen beschränkt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

Die `DDX_MonthCalCtrl` Funktion verwaltet die Übertragung von Datumsdaten zwischen einem Monatskalendersteuerelement ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und entweder einem [CTime-](../../atl-mfc-shared/reference/ctime-class.md) oder einem [COleDateTime-Datenelement](../../atl-mfc-shared/reference/coledatetime-class.md) des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*nIDC*<br/>
Die Ressourcen-ID des Monatskalendersteuerelements, das der Membervariablen zugeordnet ist.

*value*<br/>
Ein Verweis `CTime` auf `COleDateTime` eine oder member variable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das Steuerelement verwaltet nur einen Datumswert. Die Zeitfelder im Zeitobjekt werden so festgelegt, dass sie die Erstellungszeit des Steuerfensters oder die Zeit widerspiegeln, die im Steuerelement mit einem Aufruf von `CMonthCalCtrl::SetCurSel`festgelegt wurde.

Wenn `DDX_MonthCalCtrl` aufgerufen wird, wird *der Wert* auf den aktuellen Status des Monatskalendersteuerelements festgelegt.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

Die `DDX_Radio` Funktion verwaltet die Übertragung von **int-Daten** zwischen einer Funksteuerungsgruppe in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts. Der Wert des **int-Datenelements** wird bestimmt, je nachdem, welcher Optionsfeld innerhalb der Gruppe ausgewählt ist.

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
Die Ressourcen-ID des ersten Funksteuerelements in der Gruppe.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Radio` aufgerufen wird, wird *der Wert* auf den aktuellen Status der Funksteuerungsgruppe festgelegt. Der Wert wird als 0-basierter Index des derzeit überprüften Funksteuerelements festgelegt, oder -1, wenn keine Funksteuerungen überprüft werden.

Wenn z. B. das erste Optionsfeld in der Gruppe aktiviert ist (die Schaltfläche mit WS_GROUP Stil), ist der Wert des **int-Members** 0 usw.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

Die `DDX_Scroll` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Bildlaufleistensteuerelement in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int-Datenelement** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Die Ressourcen-ID des Bildlaufleistensteuerelements, das der Steuerelementeigenschaft zugeordnet ist.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Scroll` aufgerufen wird, wird der *Wert* auf die aktuelle Position des Daumens des Steuerelements festgelegt. Weitere Informationen zu den Werten, die der aktuellen Position des Daumens des Steuerelements zugeordnet sind, finden Sie unter [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) im Windows SDK.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

Die `DDX_Slider` Funktion verwaltet die Übertragung von **int-Daten** zwischen einem Schieberegler-Steuerelement in einem Dialogfeld oder einer Formularansicht und einem **int-Datenmember** des Dialogfelds oder Formularansichtsobjekts.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die Ressourcen-ID des Schiebereglersteuerelements.

*value*<br/>
Ein Verweis auf den zu tauschenden Wert. Dieser Parameter enthält die aktuelle Position des Schiebereglersteuerelements oder legt sie fest.

### <a name="remarks"></a>Bemerkungen

Wenn `DDX_Slider` aufgerufen wird, wird der *Wert* auf die aktuelle Position des Daumens des Steuerelements gesetzt, oder der Wert erhält die Position, abhängig von der Richtung des Austauschs.

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md). Informationen zu Schiebereglern finden Sie unter [Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

Die `DDX_Text` Funktion verwaltet die Übertragung von **int**, **UINT**, **long**, `CString`DWORD, , **float**oder **double** data zwischen einem Bearbeitungssteuerelement in einem Dialogfeld, einer Formularansicht oder Einer Steuerelementansicht und einem [CString-Datenmember](../../atl-mfc-shared/reference/cstringt-class.md) des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines Bearbeitungssteuerelements im Dialogfeld, in der Formularansicht oder im Steuerelementansichtsobjekt.

*value*<br/>
Ein Verweis auf ein Datenelement im Dialogfeld, in der Formularansicht oder im Steuerelementansichtsobjekt. Der Datentyp des *Werts* hängt davon `DDX_Text` ab, welche der überladenen Versionen von Ihnen verwendet wird.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="see-also"></a>Siehe auch

[Standardroutinen zur Prüfung der Dialogfelddaten](standard-dialog-data-validation-routines.md)<br/>
[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
