---
title: CPropExchange-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363966"
---
# <a name="cpropexchange-class"></a>CPropExchange-Klasse

Unterstützt die Implementierung der Dauerhaftigkeit für die OLE-Steuerelemente.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Tauscht eine bLOB-Eigenschaft (Binary Large Object).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Tauscht eine Schriftarteigenschaft aus.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Tauscht eine Eigenschaft zwischen einem Steuerelement und einer Datei.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Tauscht Eigenschaften eines beliebigen integrierten Typs aus.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Tauscht die Versionsnummer eines OLE-Steuerelements aus.|
|[CPropExchange::GetVersion](#getversion)|Ruft die Versionsnummer eines OLE-Steuerelements ab.|
|[CPropExchange::IsAsynchron](#isasynchronous)|Legt fest, ob der Austausch von Eigenschaften asynchron erfolgt.|
|[CPropExchange::IsLoading](#isloading)|Gibt an, ob Eigenschaften in das Steuerelement geladen oder darin gespeichert werden.|

## <a name="remarks"></a>Bemerkungen

`CPropExchange`hat keine Basisklasse.

Legt den Kontext und die Richtung eines Immobilienaustauschs fest.

Persistenz ist der Austausch der Statusinformationen des Steuerelements, die normalerweise durch seine Eigenschaften dargestellt werden, zwischen dem Steuerelement selbst und einem Medium.

Das Framework erstellt ein `CPropExchange` Objekt, das von der Benachrichtigung abgeleitet wird, dass die Eigenschaften eines OLE-Steuerelements aus persistentem Speicher geladen oder dort gespeichert werden sollen.

Das Framework übergibt einen `CPropExchange` Zeiger auf dieses `DoPropExchange` Objekt an die Funktion des Steuerelements. Wenn Sie einen Assistenten verwendet haben, um die Startdateien für ihr Steuerelement zu erstellen, ruft die Funktion des Steuerelements `DoPropExchange` auf. `COleControl::DoPropExchange` Die Basisklasse-Version tauscht die Bestandseigenschaften des Steuerelements aus. Sie ändern die Version der abgeleiteten Klasse, um Eigenschaften auszutauschen, die Sie dem Steuerelement hinzugefügt haben.

`CPropExchange`kann verwendet werden, um die Eigenschaften eines Steuerelements zu serialisieren oder die Eigenschaften eines Steuerelements beim Laden oder Erstellen eines Steuerelements zu initialisieren. Die `ExchangeProp` `ExchangeFontProp` und Memberfunktionen von `CPropExchange` sind in der Lage, Eigenschaften auf verschiedenen Medien zu speichern und von ihnen zu laden.

Weitere Informationen zur `CPropExchange`Verwendung finden Sie im Artikel [MFC ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CPropExchange`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Serialisiert eine Eigenschaft, die bLOB-Daten (Binary Large Object) speichert.

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*phBlob*<br/>
Zeiger auf eine Variable, die auf die Stelle zeigt, an der die Eigenschaft gespeichert ist (Variable ist in der Regel ein Member Ihrer Klasse).

*hBlobDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *phBlob*verwiesen wird. Wenn *hBlobDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn die Serialisierung des Steuerelements aus irgendeinem Grund fehlschlägt.

Die `CArchivePropExchange::ExchangeBlobProp`Funktionen `CResetPropExchange::ExchangeBlobProp`, `CPropsetPropExchange::ExchangeBlobProp` , und überschreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Tauscht eine Schriftarteigenschaft zwischen einem Speichermedium und dem Steuerelement aus.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*Schriftart*<br/>
Ein Verweis auf ein [CFontHolder-Objekt,](../../mfc/reference/cfontholder-class.md) das die font-Eigenschaft enthält.

*pFontDesc*<br/>
Ein Zeiger auf eine [FONTDESC-Struktur,](/windows/win32/api/olectl/ns-olectl-fontdesc) die Werte zum Initialisieren des Standardstatus der font-Eigenschaft enthält, wenn *pFontDispAmbient* NULL ist.

*pFontDispAmbient*<br/>
Ein Zeiger auf `IFontDisp` die Schnittstelle einer Schriftart, die zum Initialisieren des Standardstatus der font-Eigenschaft verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die font-Eigenschaft vom Medium in das Steuerelement geladen wird, werden die `CFontHolder` Eigenschaften der Schriftart vom Medium abgerufen und das Objekt, auf das von *der Schriftart* verwiesen wird, mit ihnen initialisiert. Wenn die font-Eigenschaft gespeichert wird, werden die Merkmale im Font-Objekt auf das Medium geschrieben.

Die `CArchivePropExchange::ExchangeFontProp`Funktionen `CResetPropExchange::ExchangeFontProp`, `CPropsetPropExchange::ExchangeFontProp` , und überschreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Tauscht eine Eigenschaft zwischen dem Steuerelement und einer Datei aus.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*ppUnk*<br/>
Ein Zeiger auf eine Variable, die einen `IUnknown` Zeiger auf die Schnittstelle der Eigenschaft enthält (diese Variable ist in der Regel ein Member Ihrer Klasse).

*Iid*<br/>
Schnittstellen-ID der Schnittstelle auf der Eigenschaft, die das Steuerelement verwendet.

*pUnkDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft aus der Datei in das Steuerelement geladen wird, wird die Eigenschaft erstellt und aus der Datei initialisiert. Wenn die Eigenschaft gespeichert wird, wird ihr Wert in die Datei geschrieben.

Die `CArchivePropExchange::ExchangePersistentProp`Funktionen `CResetPropExchange::ExchangePersistentProp`, `CPropsetPropExchange::ExchangePersistentProp` , und überschreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

Tauscht eine Eigenschaft zwischen einem Speichermedium und dem Steuerelement aus.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*vtProp*<br/>
Ein Symbol, das den Typ der ausgetauschten Eigenschaft angibt. Mögliche Werte:

|Symbol|Eigenschaftentyp|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**Lange**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
Ein Zeiger auf den Wert der Eigenschaft.

*pvDefault*<br/>
Zeiger auf einen Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft vom Medium in das Steuerelement geladen wird, wird der Wert der Eigenschaft vom Medium abgerufen und im Objekt gespeichert, auf das von *pvProp*verwiesen wird. Wenn die Eigenschaft auf dem Medium gespeichert wird, wird der Wert des Objekts, auf das *pvProp* zeigt, auf das Medium geschrieben.

Die `CArchivePropExchange::ExchangeProp`Funktionen `CResetPropExchange::ExchangeProp`, `CPropsetPropExchange::ExchangeProp` , und überschreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Wird vom Framework aufgerufen, um die Persistenz einer Versionsnummer zu behandeln.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parameter

*dwVersionLoaded*<br/>
Verweis auf eine Variable, bei der die Versionsnummer der geladenen persistenten Daten gespeichert wird.

*dwVersionDefault*<br/>
Die aktuelle Versionsnummer des Steuerelements.

*bKonvertieren*<br/>
Gibt an, ob persistente Daten in die aktuelle Version konvertiert oder auf derselben Version beibehalten werden sollen, die geladen wurde.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; 0 sonst.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion

Rufen Sie diese Funktion auf, um die Versionsnummer des Steuerelements abzurufen.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Die Versionsnummer des Steuerelements.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange::IsAsynchron

Legt fest, ob der Austausch von Eigenschaften asynchron erfolgt.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn Eigenschaften asynchron ausgetauscht werden, andernfalls FALSE.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange::IsLoading

Rufen Sie diese Funktion auf, um zu bestimmen, ob Eigenschaften in das Steuerelement geladen oder von diesem gespeichert werden.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Eigenschaften geladen werden; andernfalls 0.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
