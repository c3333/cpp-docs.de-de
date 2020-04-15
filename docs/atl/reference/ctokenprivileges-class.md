---
title: CTokenPrivileges-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: ceb9aeca6b99e7fc9d08625e11cbdb182fb3dc9e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330544"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges-Klasse

Diese Klasse ist ein `TOKEN_PRIVILEGES` Wrapper für die Struktur.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CTokenPrivileges
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Der Konstruktor.|
|[CTokenPrivileges::'CTokenPrivileges](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenPrivileges::Hinzufügen](#add)|Fügt dem `CTokenPrivileges` Objekt eine oder mehrere Berechtigungen hinzu.|
|[CTokenPrivileges::Delete](#delete)|Löscht eine Berechtigung `CTokenPrivileges` aus dem Objekt.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Löscht alle Berechtigungen aus `CTokenPrivileges` dem Objekt.|
|[CTokenPrivileges::GetCount](#getcount)|Gibt die Anzahl der `CTokenPrivileges` Berechtigungseinträge im Objekt zurück.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Ruft Anzeigenamen für die im `CTokenPrivileges` Objekt enthaltenen Berechtigungen ab.|
|[CTokenPrivileges::GetLength](#getlength)|Gibt die Puffergröße in Bytes `TOKEN_PRIVILEGES` zurück, `CTokenPrivileges` die erforderlich ist, um die durch das Objekt dargestellte Struktur zu halten.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Ruft die lokal eindeutigen Bezeichner (LUIDs) und Attributflags aus dem `CTokenPrivileges` Objekt ab.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Ruft die Berechtigungsnamen und `CTokenPrivileges` Attributflags aus dem Objekt ab.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Gibt einen Zeiger `TOKEN_PRIVILEGES` auf die Struktur zurück.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Ruft das Attribut ab, das einem bestimmten Berechtigungsnamen zugeordnet ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Gibt einen Wert auf einen `TOKEN_PRIVILEGES` Zeiger auf die Struktur um.|
|[CTokenPrivileges::operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Ein [Zugriffstoken](/windows/win32/SecAuthZ/access-tokens) ist ein Objekt, das den Sicherheitskontext eines Prozesses oder Threads beschreibt und jedem Benutzer zugewiesen wird, der bei einem Windows-System angemeldet ist.

Das Zugriffstoken wird verwendet, um die verschiedenen Sicherheitsberechtigungen zu beschreiben, die jedem Benutzer gewährt werden. Eine Berechtigung besteht aus einer 64-Bit-Nummer, die als lokal eindeutiger Bezeichner ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) bezeichnet wird, und einer Deskriptorzeichenfolge.

Die `CTokenPrivileges` Klasse ist ein Wrapper für die [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) Struktur und enthält 0 oder mehr Berechtigungen. Berechtigungen können mithilfe der bereitgestellten Klassenmethoden hinzugefügt, gelöscht oder abgefragt werden.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Hinzufügen

Fügt dem `CTokenPrivileges` Zugriffstokenobjekt eine oder mehrere Berechtigungen hinzu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parameter

*pszPrivilege*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Berechtigung angibt, wie in WINNT definiert. H-Headerdatei.

*bEnable*<br/>
Wenn true, ist die Berechtigung aktiviert. Wenn false, ist die Berechtigung deaktiviert.

*rPrivileges*<br/>
Verweis auf eine [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) Struktur. Die Berechtigungen und Attribute werden aus dieser Struktur `CTokenPrivileges` kopiert und dem Objekt hinzugefügt.

### <a name="return-value"></a>Rückgabewert

Die erste Form dieser Methode gibt true zurück, wenn die Berechtigungen erfolgreich hinzugefügt wurden, andernfalls false.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

Der Konstruktor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CTokenPrivileges` Objekt, das dem neuen Objekt zugewiesen werden soll.

*rPrivileges*<br/>
Die [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) Struktur, die `CTokenPrivileges` dem neuen Objekt zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Das `CTokenPrivileges` Objekt kann optional mit `TOKEN_PRIVILEGES` einer Struktur `CTokenPrivileges` oder einem zuvor definierten Objekt erstellt werden.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges::'CTokenPrivileges

Der Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle zugewiesenen Ressourcen frei.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete

Löscht eine Berechtigung `CTokenPrivileges` aus dem Zugriffstokenobjekt.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parameter

*pszPrivilege*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Berechtigung angibt, wie in WINNT definiert. H-Headerdatei. Dieser Parameter könnte z. B. die Konstante SE_SECURITY_NAME oder die entsprechende Zeichenfolge "SeSecurityPrivilege" angeben.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Berechtigung erfolgreich gelöscht wurde, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist als Werkzeug zum Erstellen eingeschränkter Token nützlich.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll

Löscht alle Berechtigungen aus `CTokenPrivileges` dem Zugriffstokenobjekt.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Löscht alle im `CTokenPrivileges` Zugriffstokenobjekt enthaltenen Berechtigungen.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Ruft Anzeigenamen für die im `CTokenPrivileges` Zugriffstokenobjekt enthaltenen Berechtigungen ab.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parameter

*pDisplayNames*<br/>
Ein Zeiger auf ein Array von `CString`-Objekten. `CNames`ist definiert als typedef: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Bemerkungen

Der `pDisplayNames` Parameter ist ein Zeiger `CString` auf ein Array von Objekten, die die `CTokenPrivileges` Anzeigenamen erhalten, die den im Objekt enthaltenen Berechtigungen entsprechen. Diese Methode ruft Anzeigenamen nur für die berechtigungen ab, die im Abschnitt Definierte Berechtigungen von WINNT angegeben sind. H.

Diese Methode ruft einen anzeigebaren Namen ab: Wenn der Attributname beispielsweise SE_REMOTE_SHUTDOWN_NAME ist, lautet der anzeigebare Name "Das Herunterfahren von einem Remotesystem erzwingen". Um den Systemnamen zu erhalten, verwenden Sie [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount

Gibt die Anzahl der `CTokenPrivileges` Berechtigungseinträge im Objekt zurück.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im `CTokenPrivileges` Objekt enthaltenen Berechtigungen zurück.

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength

Gibt die Länge `CTokenPrivileges` des Objekts zurück.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Bytes `TOKEN_PRIVILEGES` zurück, `CTokenPrivileges` die erforderlich sind, um eine Struktur zu enthalten, die durch das Objekt dargestellt wird, einschließlich aller darin enthaltenen Berechtigungseinträge.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Ruft die lokal eindeutigen Bezeichner (LUIDs) und Attributflags aus dem `CTokenPrivileges` Objekt ab.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pPrivileges*<br/>
Zeiger auf ein Array von [LUID-Objekten.](/windows/win32/api/winnt/ns-winnt-luid) `CLUIDArray`ist ein typedef, der als `CAtlArray<LUID> CLUIDArray`definiert ist.

*pAttributes*<br/>
Zeiger auf ein Array von DWORD-Objekten. Wenn dieser Parameter weggelassen wird oder NULL, werden die Attribute nicht abgerufen. `CAttributes`ist ein typedef, der als `CAtlArray <DWORD> CAttributes`definiert ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt alle im `CTokenPrivileges` Zugriffstokenobjekt enthaltenen Berechtigungen auf und platziert die einzelnen LUIDs und (optional) die Attributflags in Arrayobjekten.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Ruft den Namen und die `CTokenPrivileges` Attributflags aus dem Objekt ab.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pNamen*<br/>
Zeiger auf ein `CString` Array von Objekten. `CNames`ist ein typedef, der als `CAtlArray <CString> CNames`definiert ist.

*pAttributes*<br/>
Zeiger auf ein Array von DWORD-Objekten. Wenn dieser Parameter weggelassen wird oder NULL, werden die Attribute nicht abgerufen. `CAttributes`ist ein typedef, der als `CAtlArray <DWORD> CAttributes`definiert ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt alle im `CTokenPrivileges` Objekt enthaltenen Berechtigungen auf und platziert den Namen und (optional) die Attributflags in Arrayobjekten.

Diese Methode ruft den Attributnamen und nicht den anzeigebaren Namen ab: Wenn der Attributname beispielsweise SE_REMOTE_SHUTDOWN_NAME ist, lautet der Systemname "SeRemoteShutdownPrivilege". Um den anzeigebaren Namen zu erhalten, verwenden Sie die Methode [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Gibt einen Zeiger `TOKEN_PRIVILEGES` auf die Struktur zurück.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die [TOKEN_PRIVILEGES-Struktur](/windows/win32/api/winnt/ns-winnt-token_privileges) zurück.

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege

Ruft das Attribut ab, das einem bestimmten Berechtigungsnamen zugeordnet ist.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pszPrivilege*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Berechtigung angibt, wie in WINNT definiert. H-Headerdatei. Dieser Parameter könnte z. B. die Konstante SE_SECURITY_NAME oder die entsprechende Zeichenfolge "SeSecurityPrivilege" angeben.

*pdwAttributes*<br/>
Zeiger auf eine Variable, die die Attribute empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das Attribut erfolgreich abgerufen wurde, andernfalls false.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::operator =

Zuweisungsoperator.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rPrivileges*<br/>
Die [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) Struktur, `CTokenPrivileges` die dem Objekt zugewiesen werden soll.

*rhs*<br/>
Das `CTokenPrivileges` Objekt, das dem Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das `CTokenPrivileges` aktualisierte Objekt zurück.

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES\*

Gibt einen Wert auf einen `TOKEN_PRIVILEGES` Zeiger auf die Struktur um.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Wert auf einen [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) Zeiger auf die TOKEN_PRIVILEGES-Struktur.

## <a name="see-also"></a>Siehe auch

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[Luid](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
