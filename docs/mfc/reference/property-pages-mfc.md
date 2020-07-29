---
title: Eigenschaftenseiten (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 9689d511760752903b83b34199fb035c0e7a8d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214047"
---
# <a name="property-pages-mfc"></a>Eigenschaftenseiten (MFC)

Eigenschaften Seiten zeigen die aktuellen Werte spezifischer OLE-Steuerelement Eigenschaften in einer anpassbaren grafischen Oberfläche für die Anzeige und Bearbeitung an, indem Sie einen Daten Zuordnungsmechanismus auf der Grundlage von Dialog Datenaustausch (DDX) unterstützen.

Dieser Daten Zuordnungs Mechanismus ordnet Eigenschaften Seiten-Steuerelemente den einzelnen Eigenschaften des OLE-Steuer Elements zu. Der Wert der Steuerelement Eigenschaft gibt den Status oder den Inhalt des Eigenschaften Seiten-Steuer Elements wieder. Die Zuordnung zwischen Steuerelementen und Eigenschaften der Eigenschaften Seite wird durch **DDP_** Funktionsaufrufe in der Member-Funktion der Eigenschaften Seite angegeben `DoDataExchange` . Im folgenden finden Sie eine Liste von **DDP_** Funktionen, die Daten austauschen, die auf der Eigenschaften Seite Ihres Steuer Elements eingegeben werden:

### <a name="property-page-data-transfer"></a>Eigenschaften Seite Datenübertragung

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Verknüpft den Index der ausgewählten Zeichenfolge in einem Kombinations Feld mit der-Eigenschaft eines-Steuer Elements.|
|[DDP_CBString](#ddp_cbstring)|Verknüpft die ausgewählte Zeichenfolge in einem Kombinations Feld mit der-Eigenschaft eines-Steuer Elements. Die ausgewählte Zeichenfolge kann mit denselben Buchstaben wie der Eigenschafts Wert beginnen, muss jedoch nicht vollständig übereinstimmen.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Verknüpft die ausgewählte Zeichenfolge in einem Kombinations Feld mit der-Eigenschaft eines-Steuer Elements. Die ausgewählte Zeichenfolge und der Zeichen folgen Wert der Eigenschaft müssen exakt übereinstimmen.|
|[DDP_Check](#ddp_check)|Verknüpft ein Kontrollkästchen auf der Eigenschaften Seite des-Steuer Elements mit der-Eigenschaft eines-Steuer Elements.|
|[DDP_LBIndex](#ddp_lbindex)|Verknüpft den Index der ausgewählten Zeichenfolge in einem Listenfeld mit der-Eigenschaft eines-Steuer Elements.|
|[DDP_LBString](#ddp_lbstring)|Verknüpft die ausgewählte Zeichenfolge in einem Listenfeld mit der-Eigenschaft eines-Steuer Elements. Die ausgewählte Zeichenfolge kann mit denselben Buchstaben wie der Eigenschafts Wert beginnen, aber Sie muss nicht vollständig übereinstimmen.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Verknüpft die ausgewählte Zeichenfolge in einem Listenfeld mit der-Eigenschaft eines-Steuer Elements. Die ausgewählte Zeichenfolge und der Zeichen folgen Wert der Eigenschaft müssen exakt übereinstimmen.|
|[DDP_PostProcessing](#ddp_postprocessing)|Schließt die Übertragung von Eigenschafts Werten aus dem Steuerelement ab.|
|[DDP_Radio](#ddp_radio)|Verknüpft eine Optionsfeld Gruppe in der Eigenschaften Seite des-Steuer Elements mit der-Eigenschaft eines-Steuer Elements.|
|[DDP_Text](#ddp_text)|Verknüpft ein Steuerelement in der Eigenschaften Seite des-Steuer Elements mit der-Eigenschaft eines-Steuer Elements. Diese Funktion verarbeitet verschiedene Typen von Eigenschaften, z. b **`double`** **`short`** .,, BSTR und **`long`** .|

Weitere Informationen zu den `DoDataExchange` Funktionen und Eigenschaften Seiten finden Sie im Artikel ActiveX-Steuer [Elemente: Eigenschaften Seiten](../../mfc/mfc-activex-controls-property-pages.md).

Im folgenden finden Sie eine Liste der Makros, die zum Erstellen und Verwalten von Eigenschaften Seiten für ein OLE-Steuerelement verwendet werden:

### <a name="property-pages"></a>Eigenschaftenseiten

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Startet die Liste der Eigenschaften Seiten-IDs.|
|[END_PROPPAGEIDS](#end_proppageids)|Beendet die Liste der Eigenschaften Seiten-IDs.|
|[PROPPAGEID](#proppageid)|Deklariert eine Eigenschaften Seite der Steuerelement Klasse.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer ganzzahligen Eigenschaft mit dem Index der aktuellen Auswahl in einem Kombinations Feld auf der Eigenschaften Seite zu synchronisieren.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit dem durch die *ID*angegebenen Kombinations Feld-Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_CBIndex` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer Zeichen folgen Eigenschaft mit der aktuellen Auswahl in einem Kombinations Feld auf der Eigenschaften Seite zu synchronisieren.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit der durch die *ID*angegebenen Kombinations Feld Zeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_CBString` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer Zeichen folgen Eigenschaft zu synchronisieren, die exakt mit der aktuellen Auswahl in einem Kombinations Feld auf der Eigenschaften Seite übereinstimmt.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kombinations Feld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit der durch die *ID*angegebenen Kombinations Feld Zeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_CBStringExact` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Mit dieser Funktion können Sie in der- `DoDataExchange` Funktion der Eigenschaften Seite den Wert der-Eigenschaft mit dem Kontrollkästchen-Steuerelement der zugehörigen Eigenschaften Seite synchronisieren.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Kontrollkästchen-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit dem durch die *ID*angegebenen Kontrollkästchen-Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_Check` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer ganzzahligen Eigenschaft mit dem Index der aktuellen Auswahl in einem Listenfeld auf der Eigenschaften Seite zu synchronisieren.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit der durch die *ID*angegebenen Listenfeld Zeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_LBIndex` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer Zeichen folgen Eigenschaft mit der aktuellen Auswahl in einem Listenfeld auf der Eigenschaften Seite zu synchronisieren.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit der durch die *ID*angegebenen Listenfeld Zeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_LBString` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um den Wert einer Zeichen folgen Eigenschaft zu synchronisieren, die exakt mit der aktuellen Auswahl in einem Listenfeld auf der Eigenschaften Seite übereinstimmt.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Listenfeld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit der durch die *ID*angegebenen Listenfeld Zeichenfolge ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_LBStringExact` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Diese Funktion wird in der-Funktion der Eigenschaften Seite aufgerufen `DoDataExchange` , um die Übertragung von Eigenschafts Werten von der Eigenschaften Seite zum-Steuerelement abzuschließen, wenn Eigenschaftswerte gespeichert werden.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte aufgerufen werden, nachdem alle Datenaustauschfunktionen abgeschlossen wurden. Beispiel:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Diese Funktion wird in der-Funktion des Steuer Elements aufgerufen `DoPropExchange` , um den Wert der-Eigenschaft mit dem entsprechenden Optionsfeld-Steuerelement der Eigenschaften Seite zu synchronisieren.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Optionsfeld-Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit dem durch die *ID*angegebenen Optionsfeld-Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_Radio` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Mit dieser Funktion können Sie in der-Funktion des Steuer Elements `DoDataExchange` den Wert der-Eigenschaft mit dem zugeordneten Eigenschaften Seiten-Steuerelement synchronisieren.

```cpp
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
Zeiger auf ein- `CDataExchange` Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*id*<br/>
Die Ressourcen-ID des Steuer Elements, das der von *pszPropName*angegebenen Steuerelement Eigenschaft zugeordnet ist.

*Kollege*<br/>
Die Element Variable, die dem von der *ID* angegebenen Eigenschaften Seiten Steuerelement und der durch *pszPropName*angegebenen Eigenschaft zugeordnet ist.

*pszPropName*<br/>
Der Eigenschaftsname der Steuerelement Eigenschaft, die mit dem durch die *ID*angegebenen Steuerelement ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte vor dem entsprechenden `DDX_Text` Funktionsaufruf aufgerufen werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Beginnt die Definition der Liste der Eigenschaften Seiten-IDs Ihres Steuer Elements.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, für die Eigenschaften Seiten angegeben werden.

*count*<br/>
Die Anzahl von Eigenschaften Seiten, die von der Steuerelement Klasse verwendet werden.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungs Datei (. cpp), in der die Element Funktionen für die Klasse definiert sind, die Eigenschaften Seitenliste mit dem BEGIN_PROPPAGEIDS-Makro, fügen Sie anschließend Makro Einträge für jede Eigenschaften Seite hinzu, und vervollständigen Sie die Eigenschaften Seitenliste mit dem END_PROPPAGEIDS-Makro.

Weitere Informationen zu Eigenschaften Seiten finden Sie im Artikel ActiveX-Steuer [Elemente: Eigenschaften Seiten](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Beendet die Definition der Eigenschaften Seiten-ID-Liste.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, die die Eigenschaften Seite besitzt.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="proppageid"></a><a name="proppageid"></a>Proppageid

Fügt eine Eigenschaften Seite für die Verwendung durch das OLE-Steuerelement hinzu.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
Die eindeutige Klassen-ID einer Eigenschaften Seite.

### <a name="remarks"></a>Bemerkungen

Alle proppageid-Makros müssen zwischen den BEGIN_PROPPAGEIDS-und END_PROPPAGEIDS-Makros in der Implementierungs Datei des Steuer Elements platziert werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxctl. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
