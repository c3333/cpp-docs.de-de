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
ms.openlocfilehash: 09fb1bd34f3b5eadb78d8f9081450c042fe22f9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226866"
---
# <a name="cpropexchange-class"></a>CPropExchange-Klasse

Unterstützt die Implementierung der Dauerhaftigkeit für die OLE-Steuerelemente.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CPropExchange:: exchangeblobprop](#exchangeblobprop)|Tauscht eine Binary Large Object-Eigenschaft (BLOB) aus.|
|[CPropExchange:: exchangefontprop](#exchangefontprop)|Tauscht eine Schriftart Eigenschaft aus.|
|[CPropExchange:: exchangepersistentprop](#exchangepersistentprop)|Tauscht eine Eigenschaft zwischen einem Steuerelement und einer Datei aus.|
|[CPropExchange:: exchangeprop](#exchangeprop)|Tauscht Eigenschaften beliebiger integrierter Typen aus.|
|[CPropExchange:: ExchangeVersion](#exchangeversion)|Tauscht die Versionsnummer eines OLE-Steuer Elements aus.|
|[CPropExchange:: GetVersion](#getversion)|Ruft die Versionsnummer eines OLE-Steuer Elements ab.|
|[CPropExchange:: IsAsynchronous](#isasynchronous)|Bestimmt, ob der Austausch von Eigenschaften asynchron erfolgt.|
|[CPropExchange:: isload](#isloading)|Gibt an, ob Eigenschaften in das Steuerelement geladen oder daraus gespeichert werden.|

## <a name="remarks"></a>Bemerkungen

`CPropExchange`weist keine Basisklasse auf.

Legt den Kontext und die Richtung eines Eigenschaften Austauschs fest.

Persistenz ist der Austausch der Zustandsinformationen des Steuer Elements (in der Regel durch seine Eigenschaften dargestellt) zwischen dem Steuerelement selbst und einem Mittel.

Das Framework erstellt ein Objekt, das von abgeleitet `CPropExchange` wird, wenn benachrichtigt wird, dass die Eigenschaften eines OLE-Steuer Elements aus dem permanenten Speicher geladen oder in den persistenten Speicher gespeichert werden sollen.

Das Framework übergibt einen Zeiger auf dieses `CPropExchange` -Objekt an die-Funktion des Steuer Elements `DoPropExchange` . Wenn Sie einen Assistenten zum Erstellen der Starter Dateien für das Steuerelement verwendet haben, ruft die-Funktion des Steuer Elements auf `DoPropExchange` `COleControl::DoPropExchange` . Die Basisklassen Version tauscht die vordefinierten Eigenschaften des Steuer Elements aus. Sie ändern die Version der abgeleiteten Klasse in Exchange-Eigenschaften, die Sie dem Steuerelement hinzugefügt haben.

`CPropExchange`kann verwendet werden, um die Eigenschaften eines Steuer Elements zu serialisieren oder die Eigenschaften eines Steuer Elements beim Laden oder Erstellen eines Steuer Elements zu initialisieren. Die `ExchangeProp` -und- `ExchangeFontProp` Member-Funktionen von `CPropExchange` können Eigenschaften in speichern und von anderen Medien laden.

Weitere Informationen zur Verwendung von `CPropExchange` finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Eigenschaften Seiten](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CPropExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxctl. h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange:: exchangeblobprop

Serialisiert eine Eigenschaft, die Binary Large Object (BLOB)-Daten speichert.

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*phblob*<br/>
Ein Zeiger auf eine Variable, die auf den Speicherort der Eigenschaft zeigt (Variable ist in der Regel ein Member der Klasse).

*hblobdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird nach Bedarf aus der von *phblob*referenzierten Variablen gelesen oder in diese geschrieben. Wenn *hblobdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn die Serialisierung des Steuer Elements aus irgendeinem Grund fehlschlägt.

Die Funktionen `CArchivePropExchange::ExchangeBlobProp` , `CResetPropExchange::ExchangeBlobProp` und über `CPropsetPropExchange::ExchangeBlobProp` schreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange:: exchangefontprop

Tauscht eine Schriftart Eigenschaft zwischen einem Speichermedium und dem Steuerelement aus.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Parameter

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Raster*<br/>
Ein Verweis auf ein [cfontholder](../../mfc/reference/cfontholder-class.md) -Objekt, das die Eigenschaft Schriftart enthält.

*pfontde*<br/>
Ein Zeiger auf eine [fontdebug](/windows/win32/api/olectl/ns-olectl-fontdesc) -Struktur, die Werte zum Initialisieren des Standardstatus der Schriftart Eigenschaft enthält, wenn *pfontdispambient* NULL ist.

*pfontdispambient*<br/>
Ein Zeiger auf die- `IFontDisp` Schnittstelle einer Schriftart, die zum Initialisieren des Standardstatus der Schriftart Eigenschaft verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die Font-Eigenschaft vom Medium in das-Steuerelement geladen wird, werden die Merkmale der Schriftart vom Medium abgerufen, und das `CFontHolder` Objekt, auf das von *Font* verwiesen wird, wird mit Ihnen initialisiert. Wenn die Eigenschaft Schriftart gespeichert wird, werden die Merkmale im Schriftart Objekt auf das Medium geschrieben.

Die Funktionen `CArchivePropExchange::ExchangeFontProp` , `CResetPropExchange::ExchangeFontProp` und über `CPropsetPropExchange::ExchangeFontProp` schreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange:: exchangepersistentprop

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
Der Name der Eigenschaft, die ausgetauscht wird.

*ppUnk*<br/>
Ein Zeiger auf eine Variable, die einen Zeiger auf die- `IUnknown` Schnittstelle der Eigenschaft enthält (diese Variable ist in der Regel ein Member der-Klasse).

*IID*<br/>
Schnittstellen-ID der Schnittstelle für die Eigenschaft, die vom Steuerelement verwendet wird.

*punkdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft aus der Datei in das-Steuerelement geladen wird, wird die-Eigenschaft aus der Datei erstellt und initialisiert. Wenn die Eigenschaft gespeichert wird, wird der Wert in die Datei geschrieben.

Die Funktionen `CArchivePropExchange::ExchangePersistentProp` , `CResetPropExchange::ExchangePersistentProp` und über `CPropsetPropExchange::ExchangePersistentProp` schreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange:: exchangeprop

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
Der Name der Eigenschaft, die ausgetauscht wird.

*vtprop*<br/>
Ein Symbol, das den Typ der ausgetauschten Eigenschaft angibt. Mögliche Werte:

|Symbol|Eigenschaftstyp|
|------------|-------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_BOOL|**BOOL**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|

*pvprop*<br/>
Ein Zeiger auf den Wert der Eigenschaft.

*pvdefault*<br/>
Zeiger auf einen Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft vom Medium in das-Steuerelement geladen wird, wird der Wert der Eigenschaft vom Medium abgerufen und in dem Objekt gespeichert, auf das von *pvprop*verwiesen wird. Wenn die Eigenschaft auf dem Medium gespeichert wird, wird der Wert des Objekts, auf das *pvprop* zeigt, auf das Medium geschrieben.

Die Funktionen `CArchivePropExchange::ExchangeProp` , `CResetPropExchange::ExchangeProp` und über `CPropsetPropExchange::ExchangeProp` schreiben diese reine virtuelle Funktion.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange:: ExchangeVersion

Wird von Framework aufgerufen, um die Persistenz einer Versionsnummer zu verarbeiten.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Parameter

*dwversionloaded*<br/>
Verweis auf eine Variable, bei der die Versionsnummer der persistenten Daten, die geladen werden, gespeichert wird.

*dwversiondefault*<br/>
Die aktuelle Versionsnummer des Steuer Elements.

*bconvert*<br/>
Gibt an, ob persistente Daten in die aktuelle Version konvertiert oder in derselben Version aufbewahrt werden sollen, die geladen wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Funktion erfolgreich war. andernfalls 0.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange:: GetVersion

Rufen Sie diese Funktion auf, um die Versionsnummer des Steuer Elements abzurufen.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Rückgabewert

Die Versionsnummer des Steuer Elements.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange:: IsAsynchronous

Bestimmt, ob der Austausch von Eigenschaften asynchron erfolgt.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn Eigenschaften asynchron ausgetauscht werden, andernfalls false.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange:: isload

Diese Funktion wird aufgerufen, um zu bestimmen, ob Eigenschaften in das Steuerelement geladen oder daraus gespeichert werden.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn Eigenschaften geladen werden. andernfalls 0.

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControl::D opropexchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
