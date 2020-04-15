---
title: Eigenschaftenseiten (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 1064cd99d1820ae8865fa632c3097441172c78c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372996"
---
# <a name="property-pages-mfc"></a>Eigenschaftenseiten (MFC)

Eigenschaftenseiten zeigen die aktuellen Werte bestimmter OLE-Steuerelementeigenschaften in einer anpassbaren, grafischen Oberfläche zum Anzeigen und Bearbeiten an, indem ein Datenzuordnungsmechanismus unterstützt wird, der auf dem Dialogdatenaustausch (DDX) basiert.

Dieser Datenzuordnungsmechanismus ordnet Eigenschaftenseitensteuerelemente den einzelnen Eigenschaften des OLE-Steuerelements zu. Der Wert der Steuerelementeigenschaft gibt den Status oder Inhalt des Eigenschaftenseitensteuerelements an. Die Zuordnung zwischen Eigenschaftenseitensteuerelementen **DDP_** und Eigenschaften wird durch DDP_ `DoDataExchange` Funktionsaufrufe in der Memberfunktion der Eigenschaftenseite angegeben. Im Folgenden finden Sie eine Liste von **DDP_** Funktionen, die Daten austauschen, die über die Eigenschaftenseite Ihres Steuerelements eingegeben wurden:

### <a name="property-page-data-transfer"></a>Eigenschaftenseite Datenübertragung

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Verknüpft den Index der ausgewählten Zeichenfolge in einem Kombinationsfeld mit der Eigenschaft eines Steuerelements.|
|[DDP_CBString](#ddp_cbstring)|Verknüpft die ausgewählte Zeichenfolge in einem Kombinationsfeld mit der Eigenschaft eines Steuerelements. Die ausgewählte Zeichenfolge kann mit den gleichen Buchstaben wie der Wert der Eigenschaft beginnen, muss sie jedoch nicht vollständig abgleichen.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Verknüpft die ausgewählte Zeichenfolge in einem Kombinationsfeld mit der Eigenschaft eines Steuerelements. Die ausgewählte Zeichenfolge und der Zeichenfolgenwert der Eigenschaft müssen genau übereinstimmen.|
|[DDP_Check](#ddp_check)|Verknüpft ein Kontrollkästchen auf der Eigenschaftenseite des Steuerelements mit der Eigenschaft eines Steuerelements.|
|[DDP_LBIndex](#ddp_lbindex)|Verknüpft den Index der ausgewählten Zeichenfolge in einem Listenfeld mit der Eigenschaft eines Steuerelements.|
|[DDP_LBString](#ddp_lbstring)|Verknüpft die ausgewählte Zeichenfolge in einem Listenfeld mit der Eigenschaft eines Steuerelements. Die ausgewählte Zeichenfolge kann mit den gleichen Buchstaben wie der Wert der Eigenschaft beginnen, muss sie jedoch nicht vollständig übereinstimmen.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Verknüpft die ausgewählte Zeichenfolge in einem Listenfeld mit der Eigenschaft eines Steuerelements. Die ausgewählte Zeichenfolge und der Zeichenfolgenwert der Eigenschaft müssen genau übereinstimmen.|
|[DDP_PostProcessing](#ddp_postprocessing)|Beendet die Übertragung von Eigenschaftswerten von Ihrem Steuerelement.|
|[DDP_Radio](#ddp_radio)|Verknüpft eine Optionsfeldgruppe auf der Eigenschaftenseite des Steuerelements mit der Eigenschaft eines Steuerelements.|
|[DDP_Text](#ddp_text)|Verknüpft ein Steuerelement auf der Eigenschaftenseite des Steuerelements mit der Eigenschaft eines Steuerelements. Diese Funktion behandelt verschiedene Arten von Eigenschaften, z. B. **double**, **short**, BSTR und **long**.|

Weitere Informationen zu `DoDataExchange` den Funktions- und Eigenschaftenseiten finden Sie im Artikel [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

Im Folgenden finden Sie eine Liste von Makros, die zum Erstellen und Verwalten von Eigenschaftenseiten für ein OLE-Steuerelement verwendet werden:

### <a name="property-pages"></a>Eigenschaftenseiten

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Beginnt die Liste der Eigenschaftenseiten-IDs.|
|[END_PROPPAGEIDS](#end_proppageids)|Beendet die Liste der Eigenschaftenseiten-IDs.|
|[PROPPAGEID](#proppageid)|Deklariert eine Eigenschaftenseite der Steuerelementklasse.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer ganzzahligen Eigenschaft mit dem Index der aktuellen Auswahl in einem Kombinationsfeld auf der Eigenschaftenseite zu synchronisieren.

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit dem von *id*angegebenen Kombinationsfeldsteuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_CBIndex` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer Zeichenfolgeneigenschaft mit der aktuellen Auswahl in einem Kombinationsfeld auf der Eigenschaftenseite zu synchronisieren.

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit der kombinationsfeldzeichenfolge ausgetauscht werden soll, die durch *id*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_CBString` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer Zeichenfolgeneigenschaft zu synchronisieren, die genau mit der aktuellen Auswahl in einem Kombinationsfeld auf der Eigenschaftenseite übereinstimmt.

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinationsfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit der kombinationsfeldzeichenfolge ausgetauscht werden soll, die durch *id*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_CBStringExact` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert der Eigenschaft mit dem zugeordneten Kontrollkästchen-Kontrollkästchen-Steuerelement für Eigenschaftenseiten zu synchronisieren.

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kontrollkästchen-Steuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit dem von *id*angegebenen Kontrollkästchen-Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_Check` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer Ganzzahleigenschaft mit dem Index der aktuellen Auswahl in einem Listenfeld auf der Eigenschaftenseite zu synchronisieren.

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit der von *id*angegebenen Listenfeldzeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_LBIndex` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer Zeichenfolgeneigenschaft mit der aktuellen Auswahl in einem Listenfeld auf der Eigenschaftenseite zu synchronisieren.

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit der von *id*angegebenen Listenfeldzeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_LBString` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um den Wert einer Zeichenfolgeneigenschaft zu synchronisieren, die genau mit der aktuellen Auswahl in einem Listenfeld auf der Eigenschaftenseite übereinstimmt.

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit der von *id*angegebenen Listenfeldzeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_LBStringExact` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Rufen Sie diese Funktion in `DoDataExchange` der Funktion Ihrer Eigenschaftenseite auf, um die Übertragung von Eigenschaftswerten von der Eigenschaftenseite auf das Steuerelement zu beenden, wenn Eigenschaftswerte gespeichert werden.

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte aufgerufen werden, nachdem alle Datenaustauschfunktionen abgeschlossen sind. Beispiel:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Rufen Sie diese Funktion `DoPropExchange` in der Funktion des Steuerelements auf, um den Wert der Eigenschaft mit dem zugehörigen Optionsfeldsteuerelement der Eigenschaftenseite zu synchronisieren.

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Optionsfeldsteuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit dem durch *id*angegebenen Optionsfeldsteuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_Radio` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Rufen Sie diese Funktion `DoDataExchange` in der Funktion des Steuerelements auf, um den Wert der Eigenschaft mit dem zugehörigen Eigenschaftenseitensteuerelement zu synchronisieren.

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf `CDataExchange` ein Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Steuerelements, das der von *pszPropName*angegebenen Steuerelementeigenschaft zugeordnet ist.

*Mitglied*<br/>
Die Membervariable, die dem Eigenschaftenseitensteuerelement zugeordnet ist, das durch *id* angegeben wird, und die Eigenschaft, die von *pszPropName*angegeben wird.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelementeigenschaft, die mit dem von *id*angegebenen Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor `DDX_Text` dem entsprechenden Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Beginnt die Definition der Liste der Eigenschaftenseiten-IDs des Steuerelements.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, für die Eigenschaftenseiten angegeben werden.

*count*<br/>
Die Anzahl der Eigenschaftenseiten, die von der Steuerelementklasse verwendet werden.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungsdatei (.cpp), die die Memberfunktionen für Ihre Klasse definiert, die Eigenschaftenseitenliste mit dem BEGIN_PROPPAGEIDS-Makro, fügen Sie dann Makroeinträge für jede Ihrer Eigenschaftenseiten hinzu, und vervollständigen Sie die Eigenschaftenseitenliste mit dem END_PROPPAGEIDS-Makro.

Weitere Informationen zu Eigenschaftenseiten finden Sie im Artikel [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Beendet die Definition der Eigenschaftenseiten-ID-Liste.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, die die Eigenschaftenseite besitzt.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

Fügt eine Eigenschaftenseite für die Verwendung durch das OLE-Steuerelement hinzu.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Die eindeutige Klassen-ID einer Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Alle PROPPAGEID-Makros müssen zwischen dem BEGIN_PROPPAGEIDS und END_PROPPAGEIDS Makros in der Implementierungsdatei des Steuerelements platziert werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
