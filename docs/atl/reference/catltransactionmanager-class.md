---
title: CAtlTransactionManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321322"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager-Klasse

Die CAtlTransactionManager-Klasse stellt einen Wrapper für Kernel Transaction Manager (KTM)-Funktionen bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlTransactionManager;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlTransactionManager](#dtor)|CAtlTransactionManager-Destruktor.|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager-Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Schließen](#close)|Schließt ein Transaktionshandle.|
|[Commit](#commit)|Fordert an, dass die Transaktion festgeschrieben wird.|
|[Erstellen](#create)|Erstellt das Transaktionshandle.|
|[CreateFile](#createfile)|Erstellt oder öffnet eine Datei, einen Dateistream oder ein Verzeichnis als transacted-Vorgang.|
|[DeleteFile](#deletefile)|Löscht eine vorhandene Datei als transacted-Vorgang.|
|[FindFirstFile](#findfirstfile)|Durchsucht ein Verzeichnis nach einer Datei oder einem Unterverzeichnis als transacted-Vorgang.|
|[GetFileAttributes](#getfileattributes)|Ruft Dateisystemattribute für eine angegebene Datei oder ein bestimmtes Verzeichnis als transacted-Vorgang ab.|
|[GetFileAttributesEx](#getfileattributesex)|Ruft Dateisystemattribute für eine angegebene Datei oder ein bestimmtes Verzeichnis als transacted-Vorgang ab.|
|[GetHandle](#gethandle)|Gibt das Transaktionshandle zurück.|
|[IsFallback](#isfallback)|Bestimmt, ob die Fallbackaufrufe aktiviert sind.|
|[MoveFile](#movefile)|Verschiebt eine vorhandene Datei oder ein Verzeichnis, einschließlich ihrer untergeordneten Dateien, als transacted-Vorgang.|
|[RegCreateKeyEx](#regcreatekeyex)|Erstellt den angegebenen Registrierungsschlüssel und ordnet ihn einer Transaktion zu. Wenn der Schlüssel bereits vorhanden ist, wird er von der Funktion geöffnet.|
|[RegDeleteKey](#regdeletekey)|Löscht einen Unterschlüssel und seine Werte aus der angegebenen plattformspezifischen Ansicht der Registrierung als transacted-Vorgang.|
|[RegOpenKeyEx](#regopenkeyex)|Öffnet den angegebenen Registrierungsschlüssel und ordnet ihn einer Transaktion zu.|
|[Rollback](#rollback)|Fordert an, dass für die Transaktion ein Rollback ausgeführt wird.|
|[SetFileAttributes](#setfileattributes)|Legt die Attribute für eine Datei oder ein Verzeichnis als transacted-Vorgang fest.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|TRUE, wenn der Fallback unterstützt wird; FALSE sonst.|
|[m_hTransaction](#m_htransaction)|Das Transaktionshandle.|

## <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltransactionmanager.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>CAtlTransactionManager

CAtlTransactionManager-Destruktor.

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Bemerkungen

Bei der normalen Verarbeitung wird die Transaktion automatisch festgeschrieben und geschlossen. Wenn der Destruktor während einer Ausnahmeabsladung aufgerufen wird, wird ein Rollback für die Transaktion ausgeführt und geschlossen.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

CAtlTransactionManager-Konstruktor.

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parameter

*bFallback*<br/>
TRUE gibt unterstützungs-Fallback an. Wenn die transacted-Funktion fehlschlägt, ruft die Klasse automatisch die Funktion "nicht transacted" auf. FALSE gibt keine "Fallback"-Aufrufe an.

*bAutoCreateTransaction*<br/>
TRUE gibt an, dass der Transaktionshandler automatisch im Konstruktor erstellt wird. FALSE gibt an, dass dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

## <a name="close"></a><a name="close"></a>Schließen

Schließt das Transaktionshandle.

```
inline BOOL Close();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `CloseHandle` ruft die Funktion auf. Die Methode wird automatisch im Destruktor aufgerufen.

## <a name="commit"></a><a name="commit"></a>begehen

Fordert an, dass die Transaktion festgeschrieben wird.

```
inline BOOL Commit();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `CommitTransaction` ruft die Funktion auf. Die Methode wird automatisch im Destruktor aufgerufen.

## <a name="create"></a><a name="create"></a>Erstellen

Erstellt das Transaktionshandle.

```
inline BOOL Create();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `CreateTransaction` ruft die Funktion auf. Prüfen Sie es auf

## <a name="createfile"></a><a name="createfile"></a>Createfile

Erstellt oder öffnet eine Datei, einen Dateistream oder ein Verzeichnis als transacted-Vorgang.

```
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Der Name eines Objekts, das erstellt oder geöffnet werden soll.

*dwDesiredAccess*<br/>
Der Zugriff auf das Objekt, der als Lesen, Schreiben, beides oder beides (Null) zusammengefasst werden kann. Die am häufigsten verwendeten Werte sind GENERIC_READ, GENERIC_WRITE oder beides: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
Der Freigabemodus eines Objekts, das gelesen, geschrieben, beide, löschen, alle diese oder keine: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Ein Zeiger auf eine SECURITY_ATTRIBUTES Struktur, die eine optionale Sicherheitsbeschreibung enthält und außerdem bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Der Parameter kann NULL sein.

*dwCreationDisposition*<br/>
Eine Aktion zum Übernehmen von Dateien, die vorhanden sind und nicht vorhanden sind. Dieser Parameter muss einer der folgenden Werte sein, der nicht kombiniert werden kann: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING oder TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Die Dateiattribute und -flags. Dieser Parameter kann eine beliebige Kombination der verfügbaren Dateiattribute (FILE_ATTRIBUTE_*) enthalten. Alle anderen Dateiattribute überschreiben FILE_ATTRIBUTE_NORMAL. Dieser Parameter kann auch Kombinationen\*von Flags (FILE_FLAG_ ) zur Steuerung des Pufferverhaltens, Zugriffsmodi und anderer spezieller Flags enthalten. Diese werden mit\* FILE_ATTRIBUTE_ Werten kombiniert.

*hTemplateFile*<br/>
Ein gültiges Handle für eine Vorlagendatei mit dem GENERIC_READ Zugriffsrecht. Die Vorlagendatei stellt Dateiattribute und erweiterte Attribute für die Datei bereit, die erstellt wird. Dieser Parameter kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle zurück, das für den Zugriff auf das Objekt verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `CreateFileTransacted` ruft die Funktion auf.

## <a name="deletefile"></a><a name="deletefile"></a>Deletefile

Löscht eine vorhandene Datei als transacted-Vorgang.

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Der Name der zu löschenden Datei.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `DeleteFileTransacted` ruft die Funktion auf.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

Durchsucht ein Verzeichnis nach einer Datei oder einem Unterverzeichnis als transacted-Vorgang.

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Das Verzeichnis oder der Pfad und der Dateiname, nach dem gesucht werden soll. Dieser Parameter kann Platzhalterzeichen enthalten, z. B. ein Sternchen (*) oder ein Fragezeichen ().

*pNextInfo*<br/>
Ein Zeiger auf die WIN32_FIND_DATA Struktur, die Informationen zu einer gefundenen Datei oder einem gefundenen Unterverzeichnis empfängt.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ein `FindNextFile` `FindClose`Suchhandle, das in einem nachfolgenden Aufruf von oder verwendet wird. Wenn die Funktion fehlschlägt oder Dateien aus der Suchzeichenfolge im Parameter *lpFileName* nicht gefunden werden kann, wird der Rückgabewert INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `FindFirstFileTransacted` ruft die Funktion auf.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Ruft Dateisystemattribute für eine angegebene Datei oder ein bestimmtes Verzeichnis als transacted-Vorgang ab.

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Der Name der Datei oder des Verzeichnisses.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `GetFileAttributesTransacted` ruft die Funktion auf.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Ruft Dateisystemattribute für eine angegebene Datei oder ein bestimmtes Verzeichnis als transacted-Vorgang ab.

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Der Name der Datei oder des Verzeichnisses.

*fInfoLevelId*<br/>
Die Ebene der abzurufenden Attributinformationen.

*lpFileInformation*<br/>
Ein Zeiger auf einen Puffer, der die Attributinformationen empfängt. Der Typ der Attributinformationen, die in diesem Puffer gespeichert werden, wird durch den Wert von *fInfoLevelId*bestimmt. Wenn der *FInfoLevelId-Parameter* GetFileExInfoStandard ist, verweist dieser Parameter auf eine WIN32_FILE_ATTRIBUTE_DATA Struktur.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `GetFileAttributesTransacted` ruft die Funktion auf.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle

Gibt das Transaktionshandle zurück.

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Transaktionshandle für eine Klasse zurück. Gibt NULL `CAtlTransactionManager` zurück, wenn der nicht an ein Handle angefügt ist.

### <a name="remarks"></a>Bemerkungen

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback

Bestimmt, ob die Fallbackaufrufe aktiviert sind.

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, da die Klasse Fallbackaufrufe unterstützt. FALSE sonst.

### <a name="remarks"></a>Bemerkungen

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

TRUE, wenn der Fallback unterstützt wird; FALSE sonst.

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Bemerkungen

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Das Transaktionshandle.

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Bemerkungen

## <a name="movefile"></a><a name="movefile"></a>Movefile

Verschiebt eine vorhandene Datei oder ein Verzeichnis, einschließlich ihrer untergeordneten Dateien, als transacted-Vorgang.

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parameter

*lpOldFileName*<br/>
Der aktuelle Name der vorhandenen Datei oder des vorhandenen Verzeichnisses auf dem lokalen Computer.

*lpNewFileName*<br/>
Der neue Name für die Datei oder das Verzeichnis. Dieser Name darf noch nicht vorhanden sein. Eine neue Datei kann sich auf einem anderen Dateisystem oder Laufwerk befinden. Ein neues Verzeichnis muss sich auf demselben Laufwerk befinden.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `MoveFileTransacted` ruft die Funktion auf.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Erstellt den angegebenen Registrierungsschlüssel und ordnet ihn einer Transaktion zu. Wenn der Schlüssel bereits vorhanden ist, wird er von der Funktion geöffnet.

```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name eines Unterschlüssels, den diese Funktion öffnet oder erstellt.

*dwReserved*<br/>
Dieser Parameter ist reserviert und muss Null sein.

*lpKlasse*<br/>
Die benutzerdefinierte Klasse dieses Schlüssels. Dieser Parameter kann ignoriert werden. Dieser Parameter kann NULL sein.

*Dwoptions*<br/>
Dieser Parameter kann einer der folgenden Werte sein: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE oder REG_OPTION_VOLATILE.

*samDesired*<br/>
Eine Maske, die die Zugriffsrechte für den Schlüssel angibt.

*lpSecurityAttributes*<br/>
Zeiger auf eine SECURITY_ATTRIBUTES-Struktur, die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Wenn *lpSecurityAttributes* NULL ist, kann das Handle nicht vererbt werden.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle an den geöffneten oder erstellten Schlüssel empfängt. Wenn der Schlüssel nicht einer der vordefinierten `RegCloseKey` Registrierungsschlüssel ist, rufen Sie die Funktion auf, nachdem Sie das Handle verwendet haben.

*lpdwDisposition*<br/>
Ein Zeiger auf eine Variable, die einen der folgenden Dispositionswerte empfängt: REG_CREATED_NEW_KEY oder REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `RegCreateKeyTransacted` ruft die Funktion auf.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Löscht einen Unterschlüssel und seine Werte aus der angegebenen plattformspezifischen Ansicht der Registrierung als transacted-Vorgang.

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Hkey*|Ein Handle für einen geöffneten Registrierungsschlüssel.|
|*lpSubKey*|Der Name des zu löschenden Schlüssels.|

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `RegDeleteKeyTransacted` ruft die Funktion auf.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

Öffnet den angegebenen Registrierungsschlüssel und ordnet ihn einer Transaktion zu.

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parameter

*Hkey*<br/>
Ein Handle für einen geöffneten Registrierungsschlüssel.

*lpSubKey*<br/>
Der Name des zu öffnenden Registrierungsunterschlüssels.

*ulOptions*<br/>
Dieser Parameter ist reserviert und muss Null sein.

*samDesired*<br/>
Eine Maske, die die Zugriffsrechte für den Schlüssel angibt.

*phkResult*<br/>
Ein Zeiger auf eine Variable, die ein Handle an den geöffneten oder erstellten Schlüssel empfängt. Wenn der Schlüssel nicht einer der vordefinierten `RegCloseKey` Registrierungsschlüssel ist, rufen Sie die Funktion auf, nachdem Sie das Handle verwendet haben.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, wird der Rückgabewert ERROR_SUCCESS. Wenn die Funktion fehlschlägt, ist der Rückgabewert ein Fehlercode ungleich Null, der in Winerror.h definiert ist.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `RegOpenKeyTransacted` ruft die Funktion auf.

## <a name="rollback"></a><a name="rollback"></a>Rollback

Fordert an, dass für die Transaktion ein Rollback ausgeführt wird.

```
inline BOOL Rollback();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `RollbackTransaction` ruft die Funktion auf.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

Legt die Attribute für eine Datei oder ein Verzeichnis als transacted-Vorgang fest.

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parameter

*lpFileName*<br/>
Der Name der Datei oder des Verzeichnisses.

*dwAttributes*<br/>
Die Dateiattribute, die für die Datei festgelegt werden sollen. Weitere Informationen finden Sie unter [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Bemerkungen

Dieser Wrapper `SetFileAttributesTransacted` ruft die Funktion auf.

## <a name="see-also"></a>Siehe auch

[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)
