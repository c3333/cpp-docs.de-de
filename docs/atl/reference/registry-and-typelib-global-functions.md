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
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326079"
---
# <a name="registry-and-typelib-global-functions"></a>Registrierung und TypeLib globale Funktionen

Diese Funktionen unterstützen das Laden und Registrieren einer Typbibliothek.

> [!IMPORTANT]
> Die in den folgenden Tabellen aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Erstellt den angegebenen Registrierungsschlüssel.|
|[AfxRegDeleteKey](#afxregdeletekey)|Löscht den angegebenen Registrierungsschlüssel.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Ein Helfer zum Registrieren eines Vorschauhandlers.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Ein Helfer, der die Registrierung eines Vorschauhandlers aufheben kann. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Diese Funktion wird aufgerufen, um eine Typbibliothek zu registrieren.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Diese Funktion wird aufgerufen, um die Registrierung einer Typbibliothek aufzuheben.|
|[AfxRegOpenKey](#afxregopenkey)|Öffnet den angegebenen Registrierungsschlüssel.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Öffnet den angegebenen Registrierungsschlüssel.|
|[AtlLoadTypeLib](#atlloadtypelib)|Mit dieser Funktion wird eine Typbibliothek geladen.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Mit dieser Funktion können Sie die Registrierung von der angegebenen Ressource aus aktualisieren.|
|[RegistryDataExchange](#registrydataexchange)|Mit dieser Funktion können Sie Lese- und Schreibvorgänge in der Systemregistrierung vornehmen. Aufruf durch die [Registrierungsdatenaustauschmakros](../../atl/reference/registry-data-exchange-macros.md).|

Diese Funktionen steuern, welchen Knoten in der Registrierung das Programm zum Speichern von Informationen verwendet.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Ruft ab, ob die Anwendung den Registrierungszugriff auf den **HKEY_CURRENT_USER** - **HKCU**) -Knoten umleitet.|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Legt fest, ob die Anwendung den Registrierungszugriff auf den **HKEY_CURRENT_USER** - **HKCU**) -Knoten umleitet.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Verwenden Sie diese Funktion, um zu bestimmen, ob die Anwendung den Registrierungszugriff auf den **Knoten HKEY_CURRENT_USER** (**HKCU**) umleitet.

### <a name="syntax"></a>Syntax

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parameter

*pAktiviert*<br/>
[out] TRUE gibt an, dass die Registrierungsinformationen an den **HKCU-Knoten** weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen auf den Standardknoten schreibt. Der Standardknoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist, andernfalls der HRESULT-Fehlercode, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die Registrierungsumleitung ist standardmäßig nicht aktiviert. Wenn Sie diese Option aktivieren, wird der Registrierungszugriff an **HKEY_CURRENT_USER.-Software-Klassen**umgeleitet.

Die Umleitung ist nicht global. Nur die MFC- und ATL-Frameworks sind von dieser Registrierungsumleitung betroffen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxRegCreateKey

Erstellt den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name eines Schlüssels, den diese Funktion öffnet oder erstellt.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle an den geöffneten oder erstellten Schlüssel empfängt.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxRegDeleteKey

Löscht den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name des zu löschenden Schlüssels.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxregisterpreviewhandler"></a>

Ein Helfer zum Registrieren eines Vorschauhandlers.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parameter

*lpszCLSID*<br/>
Gibt die CLSID des Handlers an.

*lpszShortTypeName*<br/>
Gibt die ProgID des Handlers an.

*lpszFilterExt*<br/>
Gibt die Dateierweiterung an, die bei diesem Handler registriert ist.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib

Diese Funktion wird aufgerufen, um eine Typbibliothek zu registrieren.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*hInstTypeLib*<br/>
Das Handle für die Modulinstanz.

*lpszIndex*<br/>
Zeichenfolge im Format\\"N", wobei N der Ganzzahlindex der Typbibliotheksressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) und [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)verwendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey

Öffnet den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name eines Schlüssels, den diese Funktion öffnet oder erstellt.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle für den erstellten Schlüssel empfängt.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Öffnet den angegebenen Registrierungsschlüssel.

### <a name="syntax"></a>Syntax

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name eines Schlüssels, den diese Funktion öffnet oder erstellt.

*ulOptions*<br/>
Dieser Parameter ist reserviert und muss Null sein.

*samDesired*<br/>
Eine Maske, die die gewünschten Zugriffsrechte für den Schlüssel angibt.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle für den geöffneten Schlüssel empfängt.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="requirements"></a>Anforderungen

**Header:** „afxpriv.h“

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Ein Helfer, der die Registrierung eines Vorschauhandlers aufheben kann.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parameter

*lpszCLSID*<br/>
Gibt die CLSID des Handlers an, der nicht registriert werden soll.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistrierung

Legt fest, ob die Anwendung den Registrierungszugriff auf den **HKEY_CURRENT_USER** -**HKCU**) -Knoten umleitet.

### <a name="syntax"></a>Syntax

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE gibt an, dass die Registrierungsinformationen an den **HKCU-Knoten** weitergeleitet werden. FALSE gibt an, dass die Anwendung Registrierungsinformationen auf den Standardknoten schreibt. Der Standardknoten ist **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die Methode erfolgreich ist, andernfalls der HRESULT-Fehlercode, wenn ein Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Die Registrierungsumleitung ist standardmäßig nicht aktiviert. Wenn Sie diese Option aktivieren, wird der Registrierungszugriff an **HKEY_CURRENT_USER.-Software-Klassen**umgeleitet.

Die Umleitung ist nicht global. Nur die MFC- und ATL-Frameworks sind von dieser Registrierungsumleitung betroffen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Diese Funktion wird aufgerufen, um die Registrierung einer Typbibliothek aufzuheben.

### <a name="syntax"></a>Syntax

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parameter

*hInstTypeLib*<br/>
Das Handle für die Modulinstanz.

*lpszIndex*<br/>
Zeichenfolge im Format\\"N", wobei N der Ganzzahlindex der Typbibliotheksressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) und [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)verwendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib

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

*hInstTypeLib*<br/>
Behandeln Sie das Modul, das der Typbibliothek zugeordnet ist.

*lpszIndex*<br/>
Zeichenfolge im Format\\"N", wobei N der Ganzzahlindex der Typbibliotheksressource ist. Kann NULL sein, wenn kein Index erforderlich ist.

*pbstrPath*<br/>
Enthält bei erfolgreicher Rückgabe den vollständigen Pfad des Moduls, das der Typbibliothek zugeordnet ist.

*ppTypeLib*<br/>
Enthält bei erfolgreicher Rückgabe einen Zeiger auf einen Zeiger auf die geladene Typbibliothek.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [AtlRegisterTypeLib](#atlregistertypelib) und [AtlUnRegisterTypeLib](#atlunregistertypelib)verwendet.

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Diese Funktion war in Visual Studio 2013 veraltet und wird in Visual Studio 2015 entfernt.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange

Mit dieser Funktion können Sie Lese- und Schreibvorgänge in der Systemregistrierung vornehmen.

### <a name="syntax"></a>Syntax

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein Zeiger auf das aktuelle Objekt.

*rdxOp*<br/>
Ein Enumeratwert, der angibt, welchen Vorgang die Funktion ausführen soll. Die zulässigen Werte finden Sie in der Tabelle im Abschnitt "Bemerkungen".

*pItem*<br/>
Zeiger auf die Daten, die aus der Registrierung gelesen oder in diese geschrieben werden sollen. Die Daten können auch einen Schlüssel darstellen, der aus der Registrierung gelöscht werden soll. Der Standardwert ist NULL.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die Makros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) und [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) zu `RegistryDataExchange`einer Funktion erweitern, die aufruft.

Die möglichen Enumerumwerte, die den Vorgang angeben, den die Funktion ausführen soll, sind in der folgenden Tabelle dargestellt:

|Enumeratwert|Vorgang|
|----------------|---------------|
|eReadFromReg|Lesen Sie Daten aus der Registrierung.|
|eWriteToReg|Schreiben Sie Daten in die Registrierung.|
|eDeleteFromReg|Löschen Sie den Schlüssel aus der Registrierung.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="see-also"></a>Siehe auch

[Functions](atl-functions.md)<br/>
[Registrierungsdatenaustauschmakros](registry-data-exchange-macros.md)
