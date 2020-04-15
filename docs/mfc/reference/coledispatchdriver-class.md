---
title: COleDispatchDriver-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: c22097c3a686857a6a5698033b7395c5d15f2570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366084"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver-Klasse

Implementiert die Clientseite der OLE-Automatisierung.

## <a name="syntax"></a>Syntax

```
class COleDispatchDriver
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Erstellt ein `COleDispatchDriver`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Fügt eine `IDispatch` Verbindung `COleDispatchDriver` mit dem Objekt an.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Erstellt `IDispatch` eine Verbindung und fügt `COleDispatchDriver` sie an das Objekt an.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Trennt eine `IDispatch` Verbindung, ohne sie freizugeben.|
|[COleDispatchDriver::GetProperty](#getproperty)|Ruft eine Automatisierungseigenschaft ab.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Helfer für den Aufruf von Automatisierungsmethoden.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Gibt `IDispatch` eine Verbindung frei.|
|[COleDispatchDriver::SetProperty](#setproperty)|Legt eine Automatisierungseigenschaft fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|Kopiert den Quellwert `COleDispatchDriver` in das Objekt.|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Greift auf `IDispatch` den zugrunde liegenden Zeiger zu.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Gibt an, ob `IDispatch` `ReleaseDispatch` die During- oder Object-Zerstörung freigegeben werden soll.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Gibt den Zeiger `IDispatch` auf die `COleDispatchDriver`Schnittstelle an, die an diese angefügt ist.|

## <a name="remarks"></a>Bemerkungen

`COleDispatchDriver`hat keine Basisklasse.

OLE-Dispatchschnittstellen ermöglichen den Zugriff auf die Methoden und Eigenschaften eines Objekts. Memberfunktionen `COleDispatchDriver` zum Anfügen, Trennen, Erstellen und Freigeben `IDispatch`einer Dispatchverbindung vom Typ . Andere Memberfunktionen verwenden Variablenargumentlisten, um das Aufrufen zu `IDispatch::Invoke`vereinfachen.

Diese Klasse kann direkt verwendet werden, wird jedoch im Allgemeinen nur von Klassen verwendet, die vom Assistenten zum Hinzufügen von Klassen erstellt wurden. Wenn Sie neue C++-Klassen erstellen, indem Sie eine `COleDispatchDriver`Typbibliothek importieren, werden die neuen Klassen von abgeleitet.

Weitere Informationen zur `COleDispatchDriver`Verwendung finden Sie in den folgenden Artikeln:

- [Automatisierungsclients](../../mfc/automation-clients.md)

- [Automatisierungsserver](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`COleDispatchDriver`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch

Rufen Sie die `AttachDispatch` -Memberfunktion auf, um dem `IDispatch` -Objekt einen `COleDispatchDriver` -Zeiger anzufügen. Weitere Informationen finden Sie unter [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parameter

*lpDispatch*<br/>
Zeiger auf ein `IDispatch` -OLE-Objekt, der an das `COleDispatchDriver` -Objekt angefügt werden soll.

*bAutoRelease*<br/>
Gibt an, ob die Verteilung freigegeben werden soll, wenn dieses Objekt den Gültigkeitsbereich verlässt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion gibt alle `IDispatch` -Zeiger zurück, die dem `COleDispatchDriver` -Objekt bereits angefügt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver

Erstellt ein `COleDispatchDriver`-Objekt.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parameter

*lpDispatch*<br/>
Zeiger auf ein `IDispatch` -OLE-Objekt, der an das `COleDispatchDriver` -Objekt angefügt werden soll.

*bAutoRelease*<br/>
Gibt an, ob die Verteilung freigegeben werden soll, wenn dieses Objekt den Gültigkeitsbereich verlässt.

*dispatchSrc*<br/>
Verweis auf `COleDispatchDriver` ein vorhandenes Objekt.

### <a name="remarks"></a>Bemerkungen

Das `COleDispatchDriver`Formular `LPDISPATCH lpDispatch`( , **BOOL**`bAutoRelease` = **TRUE**) verbindet die [IDispatch-Schnittstelle.](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

Das `COleDispatchDriver`Formular ( **const**`COleDispatchDriver`& `dispatchSrc` `COleDispatchDriver` ) kopiert ein vorhandenes Objekt und erhöht die Referenzanzahl.

Das `COleDispatchDriver`Formular ( `COleDispatchDriver` ) erstellt ein `IDispatch` Objekt, verbindet jedoch nicht die Schnittstelle. Bevor `COleDispatchDriver`Sie ( ) ohne Argumente `IDispatch` verwenden, sollten Sie eine verbindung mit [cOleDispatchDriver::CreateDispatch](#createdispatch) oder [COleDispatchDriver::AttachDispatch](#attachdispatch)herstellen. Weitere Informationen finden Sie unter [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver::CreateDispatch

Erstellt ein [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) -Schnittstellenobjekt und fügt es zum `COleDispatchDriver` -Objekt hinzu.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Die Klassen-ID, des zu erstellenden `IDispatch` -Verbindungsobjekts.

*pError*<br/>
Ein Zeiger auf ein OLE-Ausnahmeobjekt, das den Statuscode aufnimmt, der sich durch die Erstellung ergibt.

*lpszProgID*<br/>
Ein Zeiger auf den programmgesteuerten Bezeichner, z. B. „Excel.Document.5“, des Automatisierungsobjekts, für das das Dispatch-Objekt erstellt werden soll.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch

Trennt die aktuelle `IDispatch` Verbindung von diesem Objekt.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `IDispatch` zuvor angefügte OLE-Objekt.

### <a name="remarks"></a>Bemerkungen

Der `IDispatch` wird nicht freigegeben.

Weitere Informationen zum LPDISPATCH-Typ finden Sie unter [Implementieren der IDispatch-Schnittstelle](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver::GetProperty

Ruft die von *dwDispID*angegebene Objekteigenschaft ab.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Identifiziert die zu abrufende Eigenschaft.

*vtProp*<br/>
Gibt die zu abrufende Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Adresse der Variablen, die den Eigenschaftswert empfängt. Er muss mit dem von *vtProp*angegebenen Typ übereinstimmen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver::InvokeHelper

Ruft die von *dwDispID*angegebene Objektmethode oder -eigenschaft in dem von *wFlags*angegebenen Kontext auf.

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Bezeichnet die aufzurufende Methode oder Eigenschaft.

*wFlags*<br/>
Flags, die den Kontext `IDispatch::Invoke`des Aufrufs von beschreiben. . Eine Liste möglicher Werte finden Sie im *Parameter wFlags* in [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) im Windows SDK.

*vtRet*<br/>
Gibt den Typ des Rückgabewerts an. Mögliche Werte finden Sie im Abschnitt „Hinweise“.

*pvRet*<br/>
Die Adresse der Variablen, die den Eigenschaftswert oder Rückgabewert aufnimmt. Er muss mit dem von *vtRet*angegebenen Typ übereinstimmen.

*pbParamInfo*<br/>
Zeiger auf eine null-terminierte Bytes-Zeichenfolge, die die Typen der Parameter nach *pbParamInfo*angibt.

*...*<br/>
Variablenliste der Parameter der in *pbParamInfo*angegebenen Typen.

### <a name="remarks"></a>Bemerkungen

Der *Parameter pbParamInfo* gibt die Typen der Parameter an, die an die Methode oder Eigenschaft übergeben werden. Die variable Argumentliste wird in der Syntaxdeklaration durch **...** dargestellt.

Mögliche Werte für das *argument vtRet* werden der VARENUMeration entnommen. Folgende Werte sind möglich:

|Symbol|Rückgabetyp|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**Lange**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**Datum**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**Variante**|
|VT_UNKNOWN|LPUNKNOWN|

Das *argument pbParamInfo* ist eine durch Leerzeichen getrennte Liste **VTS_** Konstanten. Einer oder mehrere dieser Werte, durch Leerzeichen (nicht Kommas) getrennt, gibt bzw. geben die Parameterliste der Funktion an. Die möglichen Werte sind beim Makro [EVENT_CUSTOM](event-maps.md#event_custom) aufgelistet.

Diese Funktion konvertiert die Parameter in Werte von VARIANTARG und ruft anschließend die Methode [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) auf. Bei einem Fehler des Aufrufs von `Invoke` löst diese Funktion eine Ausnahme aus. Wenn der von `IDispatch::Invoke` SCODE (Statuscode) zurückgegebene SCODE DISP_E_EXCEPTION wird, löst diese Funktion ein [COleException-Objekt](../../mfc/reference/coleexception-class.md) aus. Andernfalls wird eine [COleDispatchException](../../mfc/reference/coledispatchexception-class.md)ausgelöst.

Weitere Informationen finden Sie unter [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [Implementieren der IDispatch-Schnittstelle](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)und [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

### <a name="example"></a>Beispiel

  Siehe dazu das Beispiel für [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease

Wenn TRUE, wird das COM-Objekt, auf das [m_lpDispatch](#m_lpdispatch) zugreifen, automatisch freigegeben, wenn [ReleaseDispatch](#releasedispatch) aufgerufen wird oder wenn dieses `COleDispatchDriver` Objekt zerstört wird.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig `m_bAutoRelease` ist im Konstruktor auf TRUE gesetzt.

Weitere Informationen zum Freigeben von COM-Objekten finden Sie unter [Implementieren von Referenzzählung](/windows/win32/com/implementing-reference-counting) und [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch

Der Zeiger auf `IDispatch` die Schnittstelle, die an diese `COleDispatchDriver`angefügt ist.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Bemerkungen

Der `m_lpDispatch` Datenmember ist eine öffentliche Variable vom Typ LPDISPATCH.

Weitere Informationen finden Sie unter [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver::operator =

Kopiert den Quellwert `COleDispatchDriver` in das Objekt.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parameter

*dispatchSrc*<br/>
Ein Zeiger auf `COleDispatchDriver` ein vorhandenes Objekt.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH

Greift auf `IDispatch` den zugrunde `COleDispatchDriver` liegenden Zeiger des Objekts zu.

```
operator LPDISPATCH();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch

Gibt `IDispatch` die Verbindung frei. Weitere Informationen finden Sie unter [Implementieren der IDispatch-Schnittstelle](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Bemerkungen

Wenn die automatische Freigabe für diese Verbindung `IDispatch::Release` festgelegt wurde, ruft diese Funktion auf, bevor die Schnittstelle freigegeben wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver::SetProperty

Legt die von *dwDispID*angegebene OLE-Objekteigenschaft fest.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parameter

*dwDispID*<br/>
Gibt die festzulegende Eigenschaft an.

*vtProp*<br/>
Gibt den Typ der festzulegenden Eigenschaft an. Informationen zu den möglichen Werten finden Sie im Abschnitt „Anmerkungen“ für [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Ein einzelner Parameter des von *vtProp*angegebenen Typs .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
