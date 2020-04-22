---
title: CRegKey-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: d3bdb2e7c3ab0ef56ef7f6fba5d43f1ba0bb7fc6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746511"
---
# <a name="cregkey-class"></a>CRegKey-Klasse

Diese Klasse stellt Methoden zum Bearbeiten von Einträgen in der Systemregistrierung bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CRegKey
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Der Konstruktor.|
|[CRegKey::-CRegKey](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRegKey::Anfügen](#attach)|Rufen Sie diese Methode auf, `CRegKey` um dem Objekt einen `hKey`HKEY anzufügen, indem Sie das [m_hKey](#m_hkey) Memberhandle auf .|
|[CRegKey::Schließen](#close)|Rufen Sie diese Methode auf, um das [m_hKey](#m_hkey) Memberhandle freizugeben, und legen Sie es auf NULL fest.|
|[CRegKey::Erstellen](#create)|Rufen Sie diese Methode auf, um den angegebenen Schlüssel `hKeyParent`zu erstellen, wenn er nicht als Unterschlüssel von vorhanden ist.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Rufen Sie diese Methode auf, um den angegebenen Schlüssel aus der Registrierung zu entfernen.|
|[CRegKey::DeleteValue](#deletevalue)|Rufen Sie diese Methode auf, um ein Wertfeld aus [m_hKey](#m_hkey)zu entfernen.|
|[CRegKey::Detach](#detach)|Rufen Sie diese Methode auf, um `CRegKey` das `m_hKey` [m_hKey](#m_hkey) Memberhandle vom Objekt zu trennen, und legen Sie auf NULL fest.|
|[CRegKey::EnumKey](#enumkey)|Rufen Sie diese Methode auf, um die Unterschlüssel des geöffneten Registrierungsschlüssels aufzuzählen.|
|[CRegKey::Flush](#flush)|Rufen Sie diese Methode auf, um alle Attribute des geöffneten Registrierungsschlüssels in die Registrierung zu schreiben.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Rufen Sie diese Methode auf, um eine Kopie der Sicherheitsbeschreibung zum Schutz des geöffneten Registrierungsschlüssels abzurufen.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Diese Methode benachrichtigt den Aufrufer über Änderungen an den Attributen oder Inhalten des geöffneten Registrierungsschlüssels.|
|[CRegKey::Öffnen](#open)|Rufen Sie diese Methode auf, um den angegebenen Schlüssel zu öffnen, und legen [Sie m_hKey](#m_hkey) auf das Handle dieses Schlüssels fest.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Rufen Sie diese Methode auf, um die Binärdaten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Rufen Sie diese Methode auf, um die DWORD-Daten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Rufen Sie diese Methode auf, um die GUID-Daten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Rufen Sie diese Methode auf, um die Multistring-Daten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Rufen Sie diese Methode auf, um die QWORD-Daten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryStringValue](#querystringvalue)|Rufen Sie diese Methode auf, um die Zeichenfolgendaten für einen angegebenen Wertnamen abzurufen.|
|[CRegKey::QueryValue](#queryvalue)|Rufen Sie diese Methode auf, um die Daten für das angegebene Wertfeld [von m_hKey](#m_hkey)abzurufen. Frühere Versionen dieser Methode werden nicht mehr unterstützt und als ATL_DEPRECATED markiert.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Rufen Sie diese Methode auf, um den angegebenen Schlüssel aus der Registrierung zu entfernen und alle Unterschlüssel explizit zu entfernen.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Rufen Sie diese Methode auf, um den Binärwert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Rufen Sie diese Methode auf, um den DWORD-Wert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Rufen Sie diese Methode auf, um den GUID-Wert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Rufen Sie diese Methode auf, um die Sicherheit des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Rufen Sie diese Methode auf, um Daten in einem angegebenen Wertfeld eines angegebenen Schlüssels zu speichern.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Rufen Sie diese Methode auf, um den Multistring-Wert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Rufen Sie diese Methode auf, um den QWORD-Wert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetStringValue](#setstringvalue)|Rufen Sie diese Methode auf, um den Zeichenfolgenwert des Registrierungsschlüssels festzulegen.|
|[CRegKey::SetValue](#setvalue)|Rufen Sie diese Methode auf, um Daten im angegebenen Wertfeld [von m_hKey](#m_hkey)zu speichern. Frühere Versionen dieser Methode werden nicht mehr unterstützt und als ATL_DEPRECATED markiert.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|Konvertiert ein `CRegKey` Objekt in einen HKEY.|
|[CRegKey::operator =](#operator_eq)|Zuweisungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Enthält ein Handle des Registrierungsschlüssels, der dem `CRegKey` Objekt zugeordnet ist.|
|[CRegKey::m_pTM](#m_ptm)|Zeiger auf `CAtlTransactionManager` Objekt|

## <a name="remarks"></a>Bemerkungen

`CRegKey`bietet Methoden zum Erstellen und Löschen von Schlüsseln und Werten in der Systemregistrierung. Die Registrierung enthält einen installationsspezifischen Satz von Definitionen für Systemkomponenten, z. B. Softwareversionsnummern, logisch-physische Zuordnungen der installierten Hardware und COM-Objekte.

`CRegKey`bietet eine Programmierschnittstelle zur Systemregistrierung für einen bestimmten Computer. Um beispielsweise einen bestimmten Registrierungsschlüssel `CRegKey::Open`zu öffnen, rufen Sie auf. Um einen Datenwert abzurufen `CRegKey::QueryValue` `CRegKey::SetValue`oder zu ändern, rufen Sie bzw. an. Um einen Schlüssel `CRegKey::Close`zu schließen, rufen Sie an.

Wenn Sie einen Schlüssel schließen, werden seine Registrierungsdaten auf die Festplatte geschrieben (geleert). Dieser Vorgang kann mehrere Sekunden dauern. Wenn Ihre Anwendung Registrierungsdaten explizit auf die Festplatte schreiben muss, können Sie die [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32-Funktion aufrufen. `RegFlushKey` Verwendet jedoch viele Systemressourcen und sollte nur aufgerufen werden, wenn dies unbedingt erforderlich ist.

> [!IMPORTANT]
> Alle Methoden, die es dem Aufrufer ermöglichen, einen Registrierungsspeicherort anzugeben, haben das Potenzial, Daten zu lesen, denen nicht vertraut werden kann. Methoden, die [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) verwenden, sollten berücksichtigen, dass diese Funktion nicht explizit Zeichenfolgen verarbeitet, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey::Anfügen

Rufen Sie diese Methode auf, `CRegKey` um einen HKEY an das Objekt anzufügen, indem Sie das [m_hKey](#m_hkey) Memberhandle auf *hKey*festlegen.

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Das Handle eines Registrierungsschlüssels.

### <a name="remarks"></a>Bemerkungen

`Attach`wird behaupten, wenn `m_hKey` es sich um nicht-NULL handelt.

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey::Schließen

Rufen Sie diese Methode auf, um das [m_hKey](#m_hkey) Memberhandle freizugeben, und legen Sie es auf NULL fest.

```
LONG Close() throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. andernfalls wird ein Fehlerwert zurückgegeben.

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey::Erstellen

Rufen Sie diese Methode auf, um den angegebenen Schlüssel zu erstellen, wenn er nicht als Unterschlüssel von *hKeyParent*vorhanden ist.

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>Parameter

*hKeyParent*<br/>
Das Handle eines geöffneten Schlüssels.

*lpszKeyName*<br/>
Gibt den Namen eines Schlüssels an, der erstellt oder geöffnet werden soll. Dieser Name muss ein Unterschlüssel von *hKeyParent*sein.

*lpszKlasse*<br/>
Gibt die Klasse des zu erstellenden oder zu öffnenden Schlüssels an. Der Standardwert ist REG_NONE.

*Dwoptions*<br/>
Optionen für den Schlüssel. Der Standardwert ist REG_OPTION_NON_VOLATILE. Eine Liste möglicher Werte und Beschreibungen finden Sie unter [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) im Windows SDK.

*samDesired*<br/>
Der Sicherheitszugriff für den Schlüssel. Der Standardwert ist KEY_READ &#124; KEY_WRITE. Eine Liste möglicher Werte und Beschreibungen finden Sie unter `RegCreateKeyEx`.

*lpSecAttr*<br/>
Ein Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die angibt, ob das Handle des Schlüssels von einem untergeordneten Prozess geerbt werden kann. Standardmäßig ist dieser Parameter NULL (d. h., das Handle kann nicht vererbt werden).

*lpdwDisposition*<br/>
[out] Wenn nicht NULL, ruft entweder REG_CREATED_NEW_KEY (wenn der Schlüssel nicht vorhanden war und erstellt wurde) oder REG_OPENED_EXISTING_KEY (wenn der Schlüssel vorhanden war und geöffnet wurde).

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, gibt ERROR_SUCCESS zurück und öffnet den Schlüssel. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

`Create`legt das [m_hKey-Member](#m_hkey) auf das Handle dieses Schlüssels fest.

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey::CRegKey

Der Konstruktor.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Ein Verweis auf ein `CRegKey`-Objekt.

*Hkey*<br/>
Ein Handle für einen Registrierungsschlüssel.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

Erstellt ein neues `CRegKey`-Objekt. Das Objekt kann aus `CRegKey` einem vorhandenen Objekt oder aus einem Handle zu einem Registrierungsschlüssel erstellt werden.

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey::-CRegKey

Der Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor wird freigegeben. `m_hKey`

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

Rufen Sie diese Methode auf, um den angegebenen Schlüssel aus der Registrierung zu entfernen.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parameter

*lpszSubKey*<br/>
Gibt den Namen des zu löschenden Schlüssels an. Dieser Name muss ein Unterschlüssel [von m_hKey](#m_hkey)sein.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

`DeleteSubKey`kann nur einen Schlüssel löschen, der keine Unterschlüssel hat. Wenn der Schlüssel Überunterschlüssel hat, rufen Sie stattdessen [RecurseDeleteKey](#recursedeletekey) auf.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::DeleteValue

Rufen Sie diese Methode auf, um ein Wertfeld aus [m_hKey](#m_hkey)zu entfernen.

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parameter

*lpszValue*<br/>
Gibt das zu entfernende Wertfeld an.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::Detach

Rufen Sie diese Methode auf, um `CRegKey` das `m_hKey` [m_hKey](#m_hkey) Memberhandle vom Objekt zu trennen, und legen Sie auf NULL fest.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Der hKEY, `CRegKey` der dem Objekt zugeordnet ist.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CRegKey::EnumKey

Rufen Sie diese Methode auf, um die Unterschlüssel des geöffneten Registrierungsschlüssels aufzuzählen.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parameter

*iIndex*<br/>
Der Unterschlüsselindex. Dieser Parameter sollte für den ersten Aufruf Null sein und dann für nachfolgende Aufrufe erhöht werden.

*pszName*<br/>
Zeiger auf einen Puffer, der den Namen des Unterschlüssels empfängt, einschließlich des beendenden Nullzeichens. Nur der Name des Unterschlüssels wird in den Puffer kopiert, nicht in die vollständige Schlüsselhierarchie.

*pnNameLength*<br/>
Zeiger auf eine Variable, die in TCHARs die Größe des puffers angibt, der durch den *Parameter pszName* angegeben wird. Diese Größe sollte das beendende Nullzeichen enthalten. Wenn die Methode zurückgegeben wird, enthält die Variable, auf die *pnNameLength* zeigt, die Anzahl der im Puffer gespeicherten Zeichen. Die zurückgegebene Anzahl enthält nicht das beendende Nullzeichen.

*pftLastWriteTime*<br/>
Zeiger auf eine Variable, die die Zeit empfängt, in die der aufgezählte Unterschlüssel zuletzt geschrieben wurde.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Um die Unterschlüssel aufzuzählen, rufen Sie mit einem Index von Null auf. `CRegKey::EnumKey` Erhöhen Sie den Indexwert, und wiederholen Sie ihn, bis die Methode ERROR_NO_MORE_ITEMS zurückgibt. Weitere Informationen finden Sie unter [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) im Windows SDK.

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::Flush

Rufen Sie diese Methode auf, um alle Attribute des geöffneten Registrierungsschlüssels in die Registrierung zu schreiben.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) im Windows SDK.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey::GetKeySecurity

Rufen Sie diese Methode auf, um eine Kopie der Sicherheitsbeschreibung zum Schutz des geöffneten Registrierungsschlüssels abzurufen.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parameter

*Si*<br/>
Der [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Wert, der die angeforderten Sicherheitsinformationen angibt.

*Psd*<br/>
Ein Zeiger auf einen Puffer, der eine Kopie der angeforderten Sicherheitsbeschreibung empfängt.

*pnBytes*<br/>
Die Größe des Puffers in Bytes, auf den *psd*zeigt.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null in WINERROR definiert. H.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey::m_hKey

Enthält ein Handle des Registrierungsschlüssels, der dem `CRegKey` Objekt zugeordnet ist.

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey::m_pTM

Zeiger auf `CAtlTransactionManager` ein Objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

Diese Methode benachrichtigt den Aufrufer über Änderungen an den Attributen oder Inhalten des geöffneten Registrierungsschlüssels.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parameter

*bWatchSubtree*<br/>
Gibt ein Flag an, das angibt, ob Änderungen am angegebenen Schlüssel und an allen Unterschlüsseln oder nur im angegebenen Schlüssel gemeldet werden sollen. Wenn dieser Parameter TRUE ist, meldet die Methode Änderungen im Schlüssel und seinen Unterschlüsseln. Wenn der Parameter FALSE ist, meldet die Methode nur Änderungen im Schlüssel.

*dwNotifyFilter*<br/>
Gibt einen Satz von Flags an, die steuern, welche Änderungen gemeldet werden sollen. Dieser Parameter kann eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Benachrichtigen Sie den Aufrufer, wenn ein Unterschlüssel hinzugefügt oder gelöscht wird.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Benachrichtigen Sie den Aufrufer über Änderungen an den Attributen des Schlüssels, z. B. die Informationen zur Sicherheitsbeschreibung.|
|REG_NOTIFY_CHANGE_LAST_SET|Benachrichtigen Sie den Aufrufer über Änderungen an einem Wert des Schlüssels. Dies kann das Hinzufügen oder Löschen eines Werts oder das Ändern eines vorhandenen Werts umfassen.|
|REG_NOTIFY_CHANGE_SECURITY|Benachrichtigen Sie den Aufrufer über Änderungen am Sicherheitsdeskriptor des Schlüssels.|

*hEvent*<br/>
Handle für ein Ereignis. Wenn der *bAsync-Parameter* TRUE ist, wird die Methode sofort zurückgegeben, und Änderungen werden durch Signalisierung dieses Ereignisses gemeldet. Wenn *bAsync* FALSE ist, wird *hEvent* ignoriert.

*bAsync*<br/>
Gibt ein Flag an, das angibt, wie sich die Methode ändert. Wenn dieser Parameter TRUE ist, gibt die Methode sofort zurück und meldet Änderungen, indem das angegebene Ereignis signalisiert wird. Wenn dieser Parameter FALSE ist, wird die Methode erst zurückgegeben, wenn eine Änderung aufgetreten ist. Wenn *hEvent* kein gültiges Ereignis angibt, kann der *bAsync-Parameter* nicht TRUE sein.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Methode benachrichtigt den Aufrufer nicht, wenn der angegebene Schlüssel gelöscht wird.

Weitere Informationen und ein Beispielprogramm finden Sie unter [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::Öffnen

Rufen Sie diese Methode auf, um den angegebenen Schlüssel zu öffnen, und legen [Sie m_hKey](#m_hkey) auf das Handle dieses Schlüssels fest.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parameter

*hKeyParent*<br/>
Das Handle eines geöffneten Schlüssels.

*lpszKeyName*<br/>
Gibt den Namen eines Schlüssels an, der erstellt oder geöffnet werden soll. Dieser Name muss ein Unterschlüssel von *hKeyParent*sein.

*samDesired*<br/>
Der Sicherheitszugriff für den Schlüssel. Der Standardwert ist KEY_ALL_ACCESS. Eine Liste möglicher Werte und Beschreibungen finden Sie unter [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Andernfalls ein Fehlerwert ungleich Null, der in WINERROR definiert ist. H.

### <a name="remarks"></a>Bemerkungen

Wenn der Parameter *lpszKeyName* NULL ist oder `Open` auf eine leere Zeichenfolge verweist, wird ein neues Handle des schlüsselidentifizierten Schlüssels geöffnet, der von *hKeyParent*identifiziert wird, aber kein zuvor geöffnetes Handle geschlossen.

Im Gegensatz zu [CRegKey::Create](#create) `Open` wird der angegebene Schlüssel nicht erstellt, wenn er nicht vorhanden ist.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::operator HKEY

Konvertiert ein `CRegKey` Objekt in einen HKEY.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::operator =

Zuweisungsoperator.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zu kopierende Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den neuen Schlüssel zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Operator trennt den *Schlüssel* vom aktuellen Objekt `CRegKey` und weist ihn stattdessen dem Objekt zu.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

Rufen Sie diese Methode auf, um die Binärdaten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*pValue*<br/>
Zeiger auf einen Puffer, der die Daten des Werts empfängt.

*pnBytes*<br/>
Zeiger auf eine Variable, die die Größe des Puffers in Bytes angibt, auf den der *parameter pValue* zeigt. Wenn die Methode zurückgegeben wird, enthält diese Variable die Größe der in den Puffer kopierten Daten.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn die Daten, auf die verwiesen wird, nicht vom Typ REG_BINARY sind, wird ERROR_INVALID_DATA zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `RegQueryValueEx` und bestätigt, dass der richtige Datentyp zurückgegeben wird. Weitere Informationen finden Sie unter [RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete [RegQueryValueEx-Funktion](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

Rufen Sie diese Methode auf, um die DWORD-Daten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*dwValue*<br/>
Zeiger auf einen Puffer, der das DWORD empfängt.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn die Daten, auf die verwiesen wird, nicht vom Typ REG_DWORD sind, wird ERROR_INVALID_DATA zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `RegQueryValueEx` und bestätigt, dass der richtige Datentyp zurückgegeben wird. Weitere Informationen finden Sie unter [RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete [RegQueryValueEx-Funktion](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

Rufen Sie diese Methode auf, um die GUID-Daten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*guidValue*<br/>
Zeiger auf eine Variable, die die GUID empfängt.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn es sich bei den daten, auf die verwiesen wird, keine gültige GUID handelt, wird ERROR_INVALID_DATA zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `CRegKey::QueryStringValue` und konvertiert die Zeichenfolge mithilfe von [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)in eine GUID .

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

Rufen Sie diese Methode auf, um die Multistring-Daten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*pszValue*<br/>
Zeiger auf einen Puffer, der die Multistring-Daten empfängt. Ein Multistring ist ein Array von null-terminierten Zeichenfolgen, das durch zwei Nullzeichen beendet wird.

*pnChars*<br/>
Die Größe des Puffers in TCHARs, auf den *pszValue*zeigt. Wenn die Methode zurückgegeben wird, enthält *pnChars* die Größe des abgerufenen Multistrings in TCHARs, einschließlich eines beendenden Nullzeichens.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn die Daten, auf die verwiesen wird, nicht vom Typ REG_MULTI_SZ sind, wird ERROR_INVALID_DATA zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `RegQueryValueEx` und bestätigt, dass der richtige Datentyp zurückgegeben wird. Weitere Informationen finden Sie unter [RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete [RegQueryValueEx-Funktion](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

Rufen Sie diese Methode auf, um die QWORD-Daten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*qwValue*<br/>
Zeiger auf einen Puffer, der das QWORD empfängt.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn die Daten, auf die verwiesen wird, nicht vom Typ REG_QWORD sind, wird ERROR_INVALID_DATA zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `RegQueryValueEx` und bestätigt, dass der richtige Datentyp zurückgegeben wird. Weitere Informationen finden Sie unter [RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete [RegQueryValueEx-Funktion](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey::QueryStringValue

Rufen Sie diese Methode auf, um die Zeichenfolgendaten für einen angegebenen Wertnamen abzurufen.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält.

*pszValue*<br/>
Zeiger auf einen Puffer, der die Zeichenfolgendaten empfängt.

*pnChars*<br/>
Die Größe des Puffers in TCHARs, auf den *pszValue*zeigt. Wenn die Methode zurückgegeben wird, enthält *pnChars* die Größe der abgerufenen Zeichenfolge in TCHARs, einschließlich eines beendenden Nullzeichens.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Wenn die Methode einen Wert nicht lesen kann, gibt sie einen Fehlercode ungleich Null zurück, der in WINERROR definiert ist. H. Wenn die Daten, auf die verwiesen wird, nicht vom Typ REG_SZ sind, wird ERROR_INVALID_DATA zurückgegeben. Wenn die Methode ERROR_MORE_DATA zurückgibt, ist *pnChars* gleich Null und nicht die erforderliche Puffergröße in Bytes.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `RegQueryValueEx` und bestätigt, dass der richtige Datentyp zurückgegeben wird. Weitere Informationen finden Sie unter [RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete [RegQueryValueEx-Funktion](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::QueryValue

Rufen Sie diese Methode auf, um die Daten für das angegebene Wertfeld [von m_hKey](#m_hkey)abzurufen. Frühere Versionen dieser Methode werden nicht mehr unterstützt und als ATL_DEPRECATED markiert.

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des abzufragenden Werts enthält. Wenn *pszValueName* NULL oder eine leere Zeichenfolge ist, ruft die Methode den Typ und die Daten für den unbenannten oder Standardwert des Schlüssels ab.

*pdwType*<br/>
Zeiger auf eine Variable, die einen Code empfängt, der den Typ der im angegebenen Wert gespeicherten Daten angibt. Der *Parameter pdwType* kann NULL sein, wenn der Typcode nicht erforderlich ist.

*pData*<br/>
Zeiger auf einen Puffer, der die Daten des Werts empfängt. Dieser Parameter kann NULL sein, wenn die Daten nicht erforderlich sind.

*pnBytes*<br/>
Zeiger auf eine Variable, die die Größe des Puffers in Bytes angibt, auf den der *Parameter pData* zeigt. Wenn die Methode zurückgegeben wird, enthält diese Variable die Größe der in pData kopierten *Daten.*

*dwValue*<br/>
Die numerischen Daten des Wertfelds.

*lpszValueName*<br/>
Gibt das wertfeldumwälte feld an.

*szValue*<br/>
Die Zeichenfolgendaten des Wertfelds.

*pdwCount*<br/>
Die Größe der Zeichenfolgendaten. Der Wert wird zunächst auf die Größe des *szValue-Puffers* festgelegt.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Andernfalls ein Fehlercode ungleich Null, der in WINERROR definiert ist. H.

### <a name="remarks"></a>Bemerkungen

Die beiden Originalversionen von `QueryValue` werden nicht mehr unterstützt und als ATL_DEPRECATED markiert. Der Compiler gibt eine Warnung aus, wenn diese Formulare verwendet werden.

Die verbleibende Methode ruft RegQueryValueEx auf.

> [!IMPORTANT]
> Mit dieser Methode kann der Aufrufer einen BeliebigenRegistrierungsspeicherort angeben und möglicherweise Daten lesen, denen nicht vertraut werden kann. Außerdem verarbeitet die von dieser Methode verwendete RegQueryValueEx-Funktion nicht explizit Zeichenfolgen, die NULL beendet sind. Beide Bedingungen sollten durch den aufrufenden Code überprüft werden.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

Rufen Sie diese Methode auf, um den angegebenen Schlüssel aus der Registrierung zu entfernen und alle Unterschlüssel explizit zu entfernen.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parameter

*lpszKey*<br/>
Gibt den Namen des zu löschenden Schlüssels an. Dieser Name muss ein Unterschlüssel [von m_hKey](#m_hkey)sein.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Andernfalls ein Fehlerwert ungleich Null, der in WINERROR definiert ist. H.

### <a name="remarks"></a>Bemerkungen

Wenn der Schlüssel Überunterschlüssel hat, müssen Sie diese Methode aufrufen, um den Schlüssel zu löschen.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

Rufen Sie diese Methode auf, um den Binärwert des Registrierungsschlüssels festzulegen.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*pValue*<br/>
Zeiger auf einen Puffer, der die Daten enthält, die mit dem angegebenen Wertnamen gespeichert werden sollen.

*nBytes*<br/>
Gibt die Größe der Informationen, auf die der *Parameter pValue* zeigt, in Bytes an.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet [RegSetValueEx,](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) um den Wert in die Registrierung zu schreiben.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CRegKey::SetDWORDValue

Rufen Sie diese Methode auf, um den DWORD-Wert des Registrierungsschlüssels festzulegen.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*dwValue*<br/>
Die DWORD-Daten, die mit dem angegebenen Wertnamen gespeichert werden sollen.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet [RegSetValueEx,](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) um den Wert in die Registrierung zu schreiben.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey::SetGUIDValue

Rufen Sie diese Methode auf, um den GUID-Wert des Registrierungsschlüssels festzulegen.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*guidValue*<br/>
Verweis auf die GUID, die mit dem angegebenen Wertnamen gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet `CRegKey::SetStringValue` und konvertiert die GUID mithilfe von [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)in eine Zeichenfolge.

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey::SetKeyValue

Rufen Sie diese Methode auf, um Daten in einem angegebenen Wertfeld eines angegebenen Schlüssels zu speichern.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parameter

*lpszKeyName*<br/>
Gibt den Namen des zu erstellenden oder zu öffnenden Schlüssels an. Dieser Name muss ein Unterschlüssel [von m_hKey](#m_hkey)sein.

*lpszValue*<br/>
Gibt die zu speichernden Daten an. Dieser Parameter muss nicht NULL sein.

*lpszValueName*<br/>
Gibt das festzulegende Wertfeld an. Wenn im Schlüssel noch kein Wertfeld mit diesem Namen vorhanden ist, wird es hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Andernfalls ein Fehlercode ungleich Null, der in WINERROR definiert ist. H.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den *Schlüssel lpszKeyName* zu erstellen oder zu öffnen und die *lpszValue-Daten* im Wertfeld *lpszValueName* zu speichern.

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::SetKeySecurity

Rufen Sie diese Methode auf, um die Sicherheit des Registrierungsschlüssels festzulegen.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parameter

*Si*<br/>
Gibt die Komponenten des zu setzenden Sicherheitsdeskriptors an. Der Wert kann eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Legt die DACL (Discretionary Access Control List) des Schlüssels fest. Der Schlüssel muss über WRITE_DAC Zugriff verfügen, oder der aufrufende Prozess muss der Besitzer des Objekts sein.|
|GROUP_SECURITY_INFORMATION|Legt die primäre Gruppensicherheitskennung (SID) des Schlüssels fest. Der Schlüssel muss über WRITE_OWNER Zugriff verfügen, oder der aufrufende Prozess muss der Besitzer des Objekts sein.|
|OWNER_SECURITY_INFORMATION|Legt die Besitzer-SID des Schlüssels fest. Der Schlüssel muss über WRITE_OWNER Zugriff verfügen, oder der aufrufende Prozess muss der Besitzer des Objekts sein oder die SE_TAKE_OWNERSHIP_NAME Berechtigung aktiviert haben.|
|SACL_SECURITY_INFORMATION|Legt die Systemzugriffssteuerungsliste (SACL) des Schlüssels fest. Der Schlüssel muss ACCESS_SYSTEM_SECURITY Zugriff haben. Die richtige Möglichkeit, diesen Zugriff zu erhalten, besteht darin, die [SE_SECURITY_NAME-Berechtigung](/windows/win32/secauthz/privileges) im aktuellen Zugriffstoken des Aufrufers zu aktivieren, das Handle für ACCESS_SYSTEM_SECURITY-Zugriffs zu öffnen und dann die Berechtigung zu deaktivieren.|

*Psd*<br/>
Zeiger auf eine [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) Struktur, die die Sicherheitsattribute angibt, die für den angegebenen Schlüssel festgelegt werden sollen.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Legt die Sicherheitsattribute des Schlüssels fest. Weitere Informationen finden Sie unter [RegSetKeySecurity.](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity)

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

Rufen Sie diese Methode auf, um den Multistring-Wert des Registrierungsschlüssels festzulegen.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*pszValue*<br/>
Zeiger auf die Multistring-Daten, die mit dem angegebenen Wertnamen gespeichert werden sollen. Ein Multistring ist ein Array von null-terminierten Zeichenfolgen, das durch zwei Nullzeichen beendet wird.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet [RegSetValueEx,](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) um den Wert in die Registrierung zu schreiben.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::SetQWORDValue

Rufen Sie diese Methode auf, um den QWORD-Wert des Registrierungsschlüssels festzulegen.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*qwValue*<br/>
Die QWORD-Daten, die mit dem angegebenen Wertnamen gespeichert werden sollen.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet [RegSetValueEx,](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) um den Wert in die Registrierung zu schreiben.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::SetStringValue

Rufen Sie diese Methode auf, um den Zeichenfolgenwert des Registrierungsschlüssels festzulegen.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu.

*pszValue*<br/>
Zeiger zu den mit dem angegebenen Wertnamen zu speichernden Zeichenfolgendaten.

*dwType*<br/>
Der Typ der Zeichenfolge, die in die Registrierung geschrieben werden muss: entweder REG_SZ (Standard) oder REG_EXPAND_SZ (für mehrteiligen Zeichenfolgen).

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert ERROR_SUCCESS. Wenn die Methode fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich 0 (null), der in WINERROR.H definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet [RegSetValueEx,](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) um den Wert in die Registrierung zu schreiben.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::SetValue

Rufen Sie diese Methode auf, um Daten im angegebenen Wertfeld [von m_hKey](#m_hkey)zu speichern. Frühere Versionen dieser Methode werden nicht mehr unterstützt und als ATL_DEPRECATED markiert.

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>Parameter

*pszValueName*<br/>
Zeiger zu einer Zeichenfolge, die den Namen des festzulegenden Wert enthält. Wenn ein Wert mit diesem Namen nicht bereits im Schlüssel vorhanden ist, fügt die Methode ihn dem Schlüssel hinzu. Wenn *pszValueName* NULL oder eine leere Zeichenfolge ist, "", legt die Methode den Typ und die Daten für den unbenannten oder Standardwert des Schlüssels fest.

*dwType*<br/>
Gibt einen Code an, der den Datentyp angibt, auf den der *Parameter pValue* verweist.

*pValue*<br/>
Zeiger auf einen Puffer, der die Daten enthält, die mit dem angegebenen Wertnamen gespeichert werden sollen.

*nBytes*<br/>
Gibt die Größe der Informationen, auf die der *Parameter pValue* zeigt, in Bytes an. Wenn die Daten vom Typ REG_SZ, REG_EXPAND_SZ oder REG_MULTI_SZ sind, muss *nBytes* die Größe des beendenden Nullzeichens enthalten.

*hKeyParent*<br/>
Das Handle eines geöffneten Schlüssels.

*lpszKeyName*<br/>
Gibt den Namen eines Schlüssels an, der erstellt oder geöffnet werden soll. Dieser Name muss ein Unterschlüssel von *hKeyParent*sein.

*lpszValue*<br/>
Gibt die zu speichernden Daten an. Dieser Parameter muss nicht NULL sein.

*lpszValueName*<br/>
Gibt das festzulegende Wertfeld an. Wenn im Schlüssel noch kein Wertfeld mit diesem Namen vorhanden ist, wird es hinzugefügt.

*dwValue*<br/>
Gibt die zu speichernden Daten an.

*bMulti*<br/>
Wenn false, gibt an, dass die Zeichenfolge vom Typ REG_SZ ist. Wenn true, gibt an, dass es sich bei der Zeichenfolge um eine Multizeichenfolge vom Typ REG_MULTI_SZ handelt.

*nValueLen*<br/>
Wenn *bMulti* true ist, ist *nValueLen* die Länge der *lpszValue-Zeichenfolge* in Zeichen. Wenn *bMulti* false ist, gibt ein Wert von -1 an, dass die Methode die Länge automatisch berechnet.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird ERROR_SUCCESS zurückgegeben. Andernfalls ein Fehlercode ungleich Null, der in WINERROR definiert ist. H.

### <a name="remarks"></a>Bemerkungen

Die beiden Originalversionen von `SetValue` sind als ATL_DEPRECATED gekennzeichnet und sollten nicht mehr verwendet werden. Der Compiler gibt eine Warnung aus, wenn diese Formulare verwendet werden.

Die dritte Methode ruft [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)auf.

## <a name="see-also"></a>Weitere Informationen

[DCOM-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
