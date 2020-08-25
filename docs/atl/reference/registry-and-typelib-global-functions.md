---
title: Registrierung und TypeLib globale Funktionen
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: 0f29f8cac62a7452781e8fde697cdf992db00b8c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834617"
---
# <a name="registry-and-typelib-global-functions"></a>Registrierung und TypeLib globale Funktionen

Diese Funktionen bieten Unterstützung für das Laden und Registrieren einer Typbibliothek.

> [!IMPORTANT]
> Die in den folgenden Tabellen aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Name|Beschreibung|
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Erstellt den angegebenen Registrierungsschlüssel.|
|[AfxRegDeleteKey](#afxregdeletekey)|Löscht den angegebenen Registrierungsschlüssel.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Ein Hilfsprogramm zum Registrieren eines Vorschau Handlers.|
|[Afxunregisterpreviewhandler](#afxunregisterpreviewhandler)| Ein Hilfsprogramm zum Aufheben der Registrierung eines Vorschau Handlers. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Diese Funktion wird aufgerufen, um eine Typbibliothek zu registrieren.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Diese Funktion wird aufgerufen, um die Registrierung einer Typbibliothek aufzuheben.|
|[AfxRegOpenKey](#afxregopenkey)|Öffnet den angegebenen Registrierungsschlüssel.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Öffnet den angegebenen Registrierungsschlüssel.|
|[AtlLoadTypeLib](#atlloadtypelib)|Mit dieser Funktion wird eine Typbibliothek geladen.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Mit dieser Funktion können Sie die Registrierung von der angegebenen Ressource aus aktualisieren.|
|[RegistryDataExchange](#registrydataexchange)|Mit dieser Funktion können Sie Lese- und Schreibvorgänge in der Systemregistrierung vornehmen. Wird von den [Registrierungsdaten Austausch-Makros](../../atl/reference/registry-data-exchange-macros.md)aufgerufen.|

Diese Funktionen steuern den Knoten in der Registrierung, den das Programm zum Speichern von Informationen verwendet.

|Name|Beschreibung|
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Ruft ab, ob die Anwendung den Registrierungs Zugriff auf den Knoten **HKEY_CURRENT_USER** ( **HKCU**) umleitet.|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Legt fest, ob die Anwendung den Registrierungs Zugriff auf den Knoten **HKEY_CURRENT_USER** ( **HKCU**) umleitet.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a> Atlgetperuserregistration

Verwenden Sie diese Funktion, um zu bestimmen, ob die Anwendung den Registrierungs Zugriff auf den Knoten **HKEY_CURRENT_USER** (**HKCU**) umleitet.

### <a name="syntax"></a>Syntax

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parameter

*nach oben*<br/>
vorgenommen TRUE gibt an, dass die Registrierungsinformationen an den **HKCU** -Knoten weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen in den Standard Knoten schreibt. Der Standard Knoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist, andernfalls der HRESULT-Fehlercode, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die Registrierungs Umleitung ist standardmäßig nicht aktiviert. Wenn Sie diese Option aktivieren, wird der Registrierungs Zugriff an **HKEY_CURRENT_USER \software\classes**umgeleitet.

Die Umleitung ist nicht global. Diese Registrierungs Umleitung wirkt sich nur auf MFC-und ATL-Frameworks aus.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a> Afxregkreatekey

Erstellt den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*HKEY*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpsubkey*<br/>
Der Name eines Schlüssels, der von dieser Funktion geöffnet oder erstellt wird.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle für den geöffneten oder erstellten Schlüssel empfängt.

*pTM*<br/>
Zeiger auf ein- `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WinError. h definiert ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „afxpriv.h“

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a> Afxregdeletekey

Löscht den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*HKEY*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpsubkey*<br/>
Der Name des zu löschenden Schlüssels.

*pTM*<br/>
Zeiger auf ein- `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WinError. h definiert ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „afxpriv.h“

## <a name="afxregisterpreviewhandler"></a>

Ein Hilfsprogramm zum Registrieren eines Vorschau Handlers.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parameter

*lpszclsid*<br/>
Gibt die CLSID des Handlers an.

*lpszshorttypame*<br/>
Gibt die ProgID des Handlers an.

*lpszfilterext*<br/>
Gibt die Dateierweiterung an, die bei diesem Handler registriert ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a> Atlregistertypelib

Diese Funktion wird aufgerufen, um eine Typbibliothek zu registrieren.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*hinsttypelib*<br/>
Das Handle für die Modul Instanz.

*lpszindex*<br/>
Zeichenfolge im Format " \\ \n", wobei N der ganzzahlige Index der Typbibliotheks Ressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von " [atlcommoduleunregisterserver](server-registration-global-functions.md#atlcommoduleunregisterserver) " und " [catlcommodule:: RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)" verwendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a> Afxregopenkey

Öffnet den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*HKEY*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpsubkey*<br/>
Der Name eines Schlüssels, der von dieser Funktion geöffnet oder erstellt wird.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle für den erstellten Schlüssel empfängt.

*pTM*<br/>
Zeiger auf ein- `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WinError. h definiert ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „afxpriv.h“

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a> Afxregopenkeyex

Öffnet den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*HKEY*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpsubkey*<br/>
Der Name eines Schlüssels, der von dieser Funktion geöffnet oder erstellt wird.

*uloptions*<br/>
Dieser Parameter ist reserviert und muss NULL sein.

*samerwünscht*<br/>
Eine Maske, die die gewünschten Zugriffsrechte für den Schlüssel angibt.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle für den geöffneten Schlüssel empfängt.

*pTM*<br/>
Zeiger auf ein- `CAtlTransactionManager` Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WinError. h definiert ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „afxpriv.h“

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a> Afxunregisterpreviewhandler

Ein Hilfsprogramm zum Aufheben der Registrierung eines Vorschau Handlers.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parameter

*lpszclsid*<br/>
Gibt die CLSID des Handlers an, dessen Registrierung aufgehoben werden soll.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a> Atlsetperuserregistration

Legt fest, ob die Anwendung den Registrierungs Zugriff auf den Knoten **HKEY_CURRENT_USER** (**HKCU**) umleitet.

### <a name="syntax"></a>Syntax

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in TRUE gibt an, dass die Registrierungsinformationen an den **HKCU** -Knoten weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen in den Standard Knoten schreibt. Der Standard Knoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist, andernfalls der HRESULT-Fehlercode, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die Registrierungs Umleitung ist standardmäßig nicht aktiviert. Wenn Sie diese Option aktivieren, wird der Registrierungs Zugriff an **HKEY_CURRENT_USER \software\classes**umgeleitet.

Die Umleitung ist nicht global. Diese Registrierungs Umleitung wirkt sich nur auf MFC-und ATL-Frameworks aus.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a> Atlunregistertypelib

Diese Funktion wird aufgerufen, um die Registrierung einer Typbibliothek aufzuheben.

### <a name="syntax"></a>Syntax

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*hinsttypelib*<br/>
Das Handle für die Modul Instanz.

*lpszindex*<br/>
Zeichenfolge im Format " \\ \n", wobei N der ganzzahlige Index der Typbibliotheks Ressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [catlcommodule:: unregistertypelib](../../atl/reference/catlcommodule-class.md#unregistertypelib) und [atlcommoduleunregisterserver](server-registration-global-functions.md#atlcommoduleunregisterserver)verwendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a> Atlloadtypelib

Mit dieser Funktion wird eine Typbibliothek geladen.

### <a name="syntax"></a>Syntax

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>Parameter

*hinsttypelib*<br/>
Handle für das Modul, das der Typbibliothek zugeordnet ist.

*lpszindex*<br/>
Zeichenfolge im Format " \\ \n", wobei N der ganzzahlige Index der Typbibliotheks Ressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

*pbstrinpath*<br/>
Bei erfolgreicher Rückgabe ist der vollständige Pfad des Moduls enthalten, das der Typbibliothek zugeordnet ist.

*pptypelib*<br/>
Enthält bei erfolgreicher Rückgabe einen Zeiger auf einen Zeiger auf die geladene Typbibliothek.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von " [atlregistertypelib](#atlregistertypelib) " und " [atlunregistertypelib](#atlunregistertypelib)" verwendet.

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a> Atlupdateregistryfromresource

Diese Funktion war in Visual Studio 2013 veraltet und wird in Visual Studio 2015 entfernt.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a> Registrydataexchange

Mit dieser Funktion können Sie Lese- und Schreibvorgänge in der Systemregistrierung vornehmen.

### <a name="syntax"></a>Syntax

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parameter

*PT*<br/>
Ein Zeiger auf das aktuelle-Objekt.

*rdxop*<br/>
Ein Enumerationswert, der angibt, welcher Vorgang von der Funktion durchgeführt werden soll. Die zulässigen Werte finden Sie in der Tabelle im Abschnitt "Hinweise".

*pitem*<br/>
Ein Zeiger auf die Daten, die aus der Registrierung gelesen oder in diese geschrieben werden sollen. Die Daten können auch einen Schlüssel darstellen, der aus der Registrierung gelöscht werden soll. Der Standardwert ist NULL.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Die Makros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) und [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) auf eine Funktion erweitert, die aufruft `RegistryDataExchange` .

Die möglichen Enumerationswerte, die den Vorgang angeben, den die Funktion ausführen soll, sind in der folgenden Tabelle aufgeführt:

|Enumerationswert|Vorgang|
|----------------|---------------|
|ereadfromreg|Lesen von Daten aus der Registrierung.|
|eWrite-scripeg|Schreiben von Daten in die Registrierung.|
|edeletefromreg|Löschen Sie den Schlüssel aus der Registrierung.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="see-also"></a>Siehe auch

[Funktionen](atl-functions.md)<br/>
[Registrierungsdaten Austausch-Makros](registry-data-exchange-macros.md)
