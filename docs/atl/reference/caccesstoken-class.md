---
title: CAccessToken-Klasse
ms.date: 07/02/2019
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: 9ae63946dfa6244e97c376f9eccd9bab93586990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319038"
---
# <a name="caccesstoken-class"></a>CAccessToken-Klasse

Diese Klasse ist ein Wrapper für ein Zugriffstoken.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAccessToken
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAccessToken::-CAccessToken](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAccessToken::Anfügen](#attach)|Rufen Sie diese Methode auf, um den Besitz des angegebenen Zugriffstokenhandles zu übernehmen.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Rufen Sie diese Methode auf, um `CAccessToken` zu bestimmen, ob eine angegebene SID im Objekt aktiviert ist.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Rufen Sie diese Methode auf, um ein neues Identitätswechselzugriffstoken zu erstellen.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Rufen Sie diese Methode auf, um ein neues primäres Token zu erstellen.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Rufen Sie diese Methode auf, um einen neuen Prozess `CAccessToken` zu erstellen, der im Sicherheitskontext des benutzerisch dargestellten Benutzers ausgeführt wird.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Rufen Sie diese Methode auf, um ein neues, eingeschränktes `CAccessToken` Objekt zu erstellen.|
|[CAccessToken::Detach](#detach)|Rufen Sie diese Methode auf, um den Besitz des Zugriffstokens zu widerrufen.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Rufen Sie diese Methode auf, um eine Berechtigung im `CAccessToken` Objekt zu deaktivieren.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Rufen Sie diese Methode auf, um `CAccessToken` eine oder mehrere Berechtigungen im Objekt zu deaktivieren.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Rufen Sie diese Methode auf, um eine Berechtigung im `CAccessToken` Objekt zu aktivieren.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Rufen Sie diese Methode auf, um `CAccessToken` eine oder mehrere Berechtigungen im Objekt zu aktivieren.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Rufen Sie diese `CAccessToken` Methode auf, um die Standard-DACL des Objekts zurückzugeben.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Rufen Sie diese `CAccessToken` Methode auf, um das Objekt gleich dem Fürden token für den aktuellen Thread zu erhalten.|
|[CAccessToken::GetGroups](#getgroups)|Rufen Sie diese `CAccessToken` Methode auf, um die Tokengruppen des Objekts zurückzugeben.|
|[CAccessToken::GetHandle](#gethandle)|Rufen Sie diese Methode auf, um ein Handle für das Zugriffstoken abzurufen.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Rufen Sie diese Methode auf, um die Identitätswechselebene vom Zugriffstoken abzurufen.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Rufen Sie diese Methode auf, um `CAccessToken` die dem Objekt zugeordnete Anmeldesitzungs-ID abzurufen.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Rufen Sie diese Methode auf, um `CAccessToken` die Anmelde-SID abzurufen, die dem Objekt zugeordnet ist.|
|[CAccessToken::Besitzer abrufen](#getowner)|Rufen Sie diese Methode auf, `CAccessToken` um den Besitzer abzurufen, der dem Objekt zugeordnet ist.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Rufen Sie diese Methode auf, `CAccessToken` um die primäre Gruppe abzurufen, die dem Objekt zugeordnet ist.|
|[CAccessToken::GetPrivileges](#getprivileges)|Rufen Sie diese Methode auf, `CAccessToken` um die dem Objekt zugeordneten Berechtigungen abzurufen.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Rufen Sie diese Methode auf, um `CAccessToken` mit dem Zugriffstoken aus einem Prozess zu initialisieren.|
|[CAccessToken::GetProfile](#getprofile)|Rufen Sie diese Methode auf, um das `CAccessToken` Handle abzurufen, das auf das dem Objekt zugeordnete Benutzerprofil verweist.|
|[CAccessToken::GetSource](#getsource)|Rufen Sie diese Methode auf, um die Quelle des `CAccessToken` Objekts abzurufen.|
|[CAccessToken::GetStatistics](#getstatistics)|Rufen Sie diese Methode auf, um Informationen abzurufen, die dem `CAccessToken` Objekt zugeordnet sind.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Rufen Sie diese Methode auf, um `CAccessToken` die Terminaldienstesitzungs-ID abzurufen, die dem Objekt zugeordnet ist.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Rufen Sie diese Methode `CAccessToken` auf, um das mit dem Token aus dem angegebenen Thread zu initialisieren.|
|[CAccessToken::GetTokenId](#gettokenid)|Rufen Sie diese Methode auf, `CAccessToken` um die Token-ID abzurufen, die dem Objekt zugeordnet ist.|
|[CAccessToken::GetType](#gettype)|Rufen Sie diese Methode auf, `CAccessToken` um den Tokentyp des Objekts abzurufen.|
|[CAccessToken::GetUser](#getuser)|Rufen Sie diese Methode auf, `CAccessToken` um den Benutzer zu identifizieren, der dem Objekt zugeordnet ist.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Rufen Sie diese Methode auf, um das `CAccessToken` Handle abzurufen, das auf das dem Objekt zugeordnete Benutzerprofil verweist.|
|[CAccessToken::Identitätswechsel](#impersonate)|Rufen Sie diese Methode auf, um einem Thread eine Identitätswechsel `CAccessToken` zuzuweisen.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Rufen Sie diese Methode auf, damit der aufrufende Thread die Identität des Sicherheitskontexts eines angemeldeten Benutzers freigibt.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Rufen Sie diese Methode `CAccessToken` auf, um zu testen, ob das Objekt eine Liste eingeschränkter SIDs enthält.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Rufen Sie diese Methode auf, `CAccessToken` um das dem Objekt zugeordnete Benutzerprofil zu laden.|
|[CAccessToken::LogonUser](#logonuser)|Rufen Sie diese Methode auf, um eine Anmeldesitzung für den Benutzer zu erstellen, der den angegebenen Anmeldeinformationen zugeordnet ist.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Rufen Sie diese Methode innerhalb eines COM-Servers auf, `CAccessToken` der einen Aufruf von einem Client verarbeitet, um den mit dem Zugriffstoken vom COM-Client zu initialisieren.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Rufen Sie diese Methode innerhalb eines Servers auf, `CAccessToken` der Anforderungen über eine Named Pipe übernimmt, um die mit dem Zugriffstoken vom Client zu initialisieren.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Rufen Sie diese Methode innerhalb eines Servers auf, der `CAccessToken` einen Aufruf von einem RPC-Client verarbeitet, um den mit dem Zugriffstoken vom Client zu initialisieren.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Rufen Sie diese Methode auf, um die `CAccessToken` Identitätswechselebene festzulegen, und initialisieren Sie dann die mit dem Token aus dem angegebenen Thread.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Rufen Sie diese Methode auf, um zu bestimmen, ob ein bestimmter Satz von Berechtigungen im `CAccessToken` Objekt aktiviert ist.|
|[CAccessToken::Zurücksetzen](#revert)|Rufen Sie diese Methode auf, um einen Thread zu beenden, der ein Identitätswechseltoken verwendet.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Rufen Sie diese Methode auf, `CAccessToken` um die Standard-DACL des Objekts festzulegen.|
|[CAccessToken::SetOwner](#setowner)|Rufen Sie diese Methode auf, um den Besitzer des `CAccessToken` Objekts festzulegen.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Rufen Sie diese Methode auf, `CAccessToken` um die primäre Gruppe des Objekts festzulegen.|

## <a name="remarks"></a>Bemerkungen

Ein [Zugriffstoken](/windows/win32/SecAuthZ/access-tokens) ist ein Objekt, das den Sicherheitskontext eines Prozesses oder Threads beschreibt und jedem Benutzer zugewiesen wird, der bei einem Windows-System angemeldet ist.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::Anfügen

Rufen Sie diese Methode auf, um den Besitz des angegebenen Zugriffstokenhandles zu übernehmen.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parameter

*hToken*<br/>
Ein Handle für das Zugriffstoken.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn das `CAccessToken` Objekt bereits über den Besitz eines Zugriffstokens verfügt.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken::-CAccessToken

Der Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Rufen Sie diese Methode auf, um `CAccessToken` zu bestimmen, ob eine angegebene SID im Objekt aktiviert ist.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Verweis auf ein [CSid-Klassenobjekt.](../../atl/reference/csid-class.md)

*pbIsMember*<br/>
Zeiger auf eine Variable, die die Ergebnisse der Prüfung empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die `CheckTokenMembership` Methode überprüft, ob die SID in den Benutzer- und Gruppen-SIDs des Zugriffstokens angezeigt wird. Wenn die SID vorhanden ist und das attribut SE_GROUP_ENABLED hat, wird *pbIsMember* auf TRUE festgelegt. Andernfalls wird sie auf FALSE gesetzt.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pbIsMember* kein gültiger Zeiger ist.

> [!NOTE]
> Das `CAccessToken` Objekt muss ein Identitätswechseltoken und kein primäres Token sein.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Rufen Sie diese Methode auf, um ein Identitätswechselzugriffstoken zu erstellen.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parameter

*Pimp*<br/>
Zeiger auf das `CAccessToken` neue Objekt.

*Sil*<br/>
Gibt einen [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) aufgezählten Typ an, der die Identitätswechselebene des neuen Tokens bereitstellt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`CreateImpersonationToken`ruft [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) auf, um ein neues Identitätswechseltoken zu erstellen.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Rufen Sie diese Methode auf, um ein neues primäres Token zu erstellen.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pPri*<br/>
Zeiger auf das `CAccessToken` neue Objekt.

*dwDesiredAccess*<br/>
Gibt die angeforderten Zugriffsrechte für das neue Token an. Der Standardwert MAXIMUM_ALLOWED fordert alle Zugriffsrechte an, die für den Aufrufer gültig sind. Weitere Informationen zu Zugriffsrechten finden Sie unter [Zugriffsrechte und Zugriffsmasken.](/windows/win32/SecAuthZ/access-rights-and-access-masks)

*pTokenAttributes*<br/>
Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die eine Sicherheitsbeschreibung für das neue Token angibt und bestimmt, ob untergeordnete Prozesse das Token erben können. Wenn *pTokenAttributes* NULL ist, erhält das Token eine Standardsicherheitsbeschreibung, und das Handle kann nicht vererbt werden.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`CreatePrimaryToken`fordert [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) auf, um ein neues primäres Token zu erstellen.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser

Rufen Sie diese Methode auf, um einen neuen Prozess `CAccessToken` zu erstellen, der im Sicherheitskontext des benutzerisch dargestellten Benutzers ausgeführt wird.

```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>Parameter

*pApplicationName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die das auszuführende Modul angibt. Dieser Parameter ist möglicherweise nicht NULL.

*pCommandLine*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die die auszuführende Befehlszeile angibt.

*pProcessInformation*<br/>
Zeiger auf eine [PROCESS_INFORMATION Struktur,](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) die Identifikationsinformationen über den neuen Prozess empfängt.

*pStartupInfo*<br/>
Zeiger auf eine [STARTUPINFO-Struktur,](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) die angibt, wie das Hauptfenster für den neuen Prozess angezeigt werden soll.

*dwCreationFlags*<br/>
Gibt zusätzliche Flags an, die die Prioritätsklasse und die Erstellung des Prozesses steuern. Eine Liste der Flags finden Sie in der Win32-Funktion [CreateProcessAsUser.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)

*bLoadProfile*<br/>
Wenn TRUE, wird das Profil des Benutzers mit [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)geladen.

*pProcessAttributes*<br/>
Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die eine Sicherheitsbeschreibung für den neuen Prozess angibt und bestimmt, ob untergeordnete Prozesse das zurückgegebene Handle erben können. Wenn *pProcessAttributes* NULL ist, erhält der Prozess eine Standardsicherheitsbeschreibung, und das Handle kann nicht geerbt werden.

*pThreadAttributes*<br/>
Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die eine Sicherheitsbeschreibung für den neuen Thread angibt und bestimmt, ob untergeordnete Prozesse das zurückgegebene Handle erben können. Wenn *pThreadAttributes* NULL ist, erhält der Thread eine Standardsicherheitsbeschreibung, und das Handle kann nicht geerbt werden.

*bInherit*<br/>
Gibt an, ob der neue Prozess Handles vom aufrufenden Prozess erbt. Wenn TRUE, wird jedes vererbbare offene Handle im aufrufenden Prozess vom neuen Prozess geerbt. Vererbte Handles haben denselben Wert und dieselben Zugriffsberechtigungen wie die ursprünglichen Handles.

*pCurrentDirectory*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die das aktuelle Laufwerk und Verzeichnis für den neuen Prozess angibt. Die Zeichenfolge muss ein vollständiger Pfad sein, der einen Laufwerkbuchstaben enthält. Wenn dieser Parameter NULL ist, verfügt der neue Prozess über das gleiche aktuelle Laufwerk und Verzeichnis wie der aufrufende Prozess.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`CreateProcessAsUser`verwendet `CreateProcessAsUser` die Win32-Funktion, um einen neuen Prozess zu erstellen, `CAccessToken` der im Sicherheitskontext des durch das Objekt dargestellten Benutzers ausgeführt wird. Eine vollständige Beschreibung der erforderlichen Parameter finden Sie in der Beschreibung der [CreateProcessAsUser-Funktion.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)

Damit diese Methode erfolgreich `CAccessToken` ist, muss das Objekt AssignPrimaryToken (es sei denn, es handelt sich um ein eingeschränktes Token) und IncreaseQuota-Berechtigungen enthalten.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Rufen Sie diese Methode auf, um ein neues, eingeschränktes `CAccessToken` Objekt zu erstellen.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parameter

*pRestrictedToken*<br/>
Das neue, `CAccessToken` eingeschränkte Objekt.

*SidsToDisable*<br/>
Ein `CTokenGroups` Objekt, das die Randverweigerungs-SIDs angibt.

*SidsToRestrict*<br/>
Ein `CTokenGroups` Objekt, das die einschränkenden SIDs angibt.

*BerechtigungenToDelete*<br/>
Ein `CTokenPrivileges` Objekt, das die Berechtigungen angibt, die im eingeschränkten Token gelöscht werden sollen. Der Standardwert erstellt ein leeres Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`CreateRestrictedToken`verwendet die [Funktion CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32, um ein neues `CAccessToken` Objekt mit Einschränkungen zu erstellen.

> [!IMPORTANT]
> Stellen `CreateRestrictedToken`Sie bei der Verwendung Folgendes sicher: Das vorhandene Token ist gültig (und wird vom Benutzer nicht eingegeben) und *SidsToDisable* und *PrivilegesToDelete* sind beide gültig (und werden vom Benutzer nicht eingegeben). Wenn die Methode FALSE zurückgibt, verweigern Sie die Funktionalität.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

Rufen Sie diese Methode auf, um den Besitz des Zugriffstokens zu widerrufen.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Handle `CAccessToken` an das zurück, das getrennt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode widerruft `CAccessToken`den Besitz des Zugriffstokens.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege

Rufen Sie diese Methode auf, um eine Berechtigung im `CAccessToken` Objekt zu deaktivieren.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*pszPrivilege*<br/>
Zeigen Sie mit dem Zeiger auf `CAccessToken` eine Zeichenfolge, die die Berechtigung zum Deaktivieren im Objekt enthält.

*pPreviousState*<br/>
Zeiger auf `CTokenPrivileges` ein Objekt, das den vorherigen Status der Berechtigungen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::DisablePrivileges

Rufen Sie diese Methode auf, um `CAccessToken` eine oder mehrere Berechtigungen im Objekt zu deaktivieren.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*rPrivileges*<br/>
Zeigen Sie auf ein Array von Zeichenfolgen, `CAccessToken` die die Berechtigungen enthalten, die im Objekt deaktiviert werden sollen.

*pPreviousState*<br/>
Zeiger auf `CTokenPrivileges` ein Objekt, das den vorherigen Status der Berechtigungen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Rufen Sie diese Methode auf, um eine Berechtigung im `CAccessToken` Objekt zu aktivieren.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*pszPrivilege*<br/>
Zeiger auf eine Zeichenfolge, die die `CAccessToken` Berechtigung zum Aktivieren im Objekt enthält.

*pPreviousState*<br/>
Zeiger auf `CTokenPrivileges` ein Objekt, das den vorherigen Status der Berechtigungen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Rufen Sie diese Methode auf, um `CAccessToken` eine oder mehrere Berechtigungen im Objekt zu aktivieren.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*rPrivileges*<br/>
Zeiger auf ein Array von Zeichenfolgen, die `CAccessToken` die Berechtigungen enthalten, die im Objekt aktiviert werden sollen.

*pPreviousState*<br/>
Zeiger auf `CTokenPrivileges` ein Objekt, das den vorherigen Status der Berechtigungen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Rufen Sie diese `CAccessToken` Methode auf, um die Standard-DACL des Objekts zurückzugeben.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parameter

*pDacl*<br/>
Zeiger auf das [CDacl-Class-Objekt,](../../atl/reference/cdacl-class.md) das die `CAccessToken` Standard-DACL des Objekts empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Standard-DACL wiederhergestellt wurde, andernfalls FALSE.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Rufen Sie diese `CAccessToken` Methode auf, um das Objekt gleich dem Fürden token für den aktuellen Thread zu erhalten.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parameter

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::GetGroups

Rufen Sie diese `CAccessToken` Methode auf, um die Tokengruppen des Objekts zurückzugeben.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parameter

*pGruppen*<br/>
Zeiger auf das [CTokenGroups-Klassenobjekt,](../../atl/reference/ctokengroups-class.md) das die Gruppeninformationen empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle

Rufen Sie diese Methode auf, um ein Handle für das Zugriffstoken abzurufen.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle `CAccessToken` für das Zugriffstoken des Objekts zurück.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Rufen Sie diese Methode auf, um die Identitätswechselebene vom Zugriffstoken abzurufen.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parameter

*pImpersonationLevel*<br/>
Zeiger auf einen [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) Enumerationstyp, der die Informationen auf Identitätswechselebene empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Rufen Sie diese Methode auf, um `CAccessToken` die dem Objekt zugeordnete Anmeldesitzungs-ID abzurufen.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pluid*<br/>
Zeiger auf eine [LUID,](/windows/win32/api/winnt/ns-winnt-luid) die die Anmeldesitzungs-ID empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pluid* ein ungültiger Wert ist.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Rufen Sie diese Methode auf, um `CAccessToken` die Anmelde-SID abzurufen, die dem Objekt zugeordnet ist.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf ein [CSid-Klassenobjekt.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pSid* ein ungültiger Wert ist.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::Besitzer abrufen

Rufen Sie diese Methode auf, `CAccessToken` um den Besitzer abzurufen, der dem Objekt zugeordnet ist.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf ein [CSid-Klassenobjekt.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Der Besitzer wird standardmäßig für alle Objekte festgelegt, die erstellt werden, während dieses Zugriffstoken aktiviert ist.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Rufen Sie diese Methode auf, `CAccessToken` um die primäre Gruppe abzurufen, die dem Objekt zugeordnet ist.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf ein [CSid-Klassenobjekt.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die Gruppe wird standardmäßig für alle Objekte festgelegt, die während dieses Zugriffstokens erstellt wurden.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Rufen Sie diese Methode auf, `CAccessToken` um die dem Objekt zugeordneten Berechtigungen abzurufen.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parameter

*pPrivileges*<br/>
Zeiger auf ein [CTokenPrivileges-Klassenobjekt,](../../atl/reference/ctokenprivileges-class.md) das die Berechtigungen erhält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Rufen Sie diese Methode auf, um `CAccessToken` mit dem Zugriffstoken aus einem Prozess zu initialisieren.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parameter

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*hProzess*<br/>
Handle an den Prozess, dessen Zugriffstoken geöffnet ist. Wenn der Standardwert NULL verwendet wird, wird der aktuelle Prozess verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Ruft die [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32-Funktion auf.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile

Rufen Sie diese Methode auf, um das `CAccessToken` Handle abzurufen, das auf das dem Objekt zugeordnete Benutzerprofil verweist.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle zurück, das auf das Benutzerprofil verweist, oder NULL, wenn kein Profil vorhanden ist.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource

Rufen Sie diese Methode auf, um die Quelle des `CAccessToken` Objekts abzurufen.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSource*<br/>
Zeiger auf eine [TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Rufen Sie diese Methode auf, um Informationen abzurufen, die dem `CAccessToken` Objekt zugeordnet sind.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parameter

*pStatistiken*<br/>
Zeiger auf eine [TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Rufen Sie diese Methode auf, um `CAccessToken` die Terminaldienstesitzungs-ID abzurufen, die dem Objekt zugeordnet ist.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parameter

*pdwSessionId*<br/>
Die Terminaldienstesitzungs-ID.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Rufen Sie diese Methode `CAccessToken` auf, um das mit dem Token aus dem angegebenen Thread zu initialisieren.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parameter

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*hThread*<br/>
Handle für den Thread, dessen Zugriffstoken geöffnet wird.

*bOpenAsSelf*<br/>
Gibt an, ob die Zugriffsüberprüfung für den Sicherheitskontext `GetThreadToken` des Threads, der die Methode aufruft, oder für den Sicherheitskontext des Prozesses für den aufrufenden Thread erfolgen soll.

Wenn dieser Parameter FALSE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts für den aufrufenden Thread durchgeführt. Wenn der Thread die Identität eines Clients annimmt, kann dieser Sicherheitskontext der eines Clientprozesses sein. Wenn dieser Parameter TRUE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts des Prozesses für den aufrufenden Thread durchgeführt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Rufen Sie diese Methode auf, `CAccessToken` um die Token-ID abzurufen, die dem Objekt zugeordnet ist.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pluid*<br/>
Zeiger auf eine [LUID,](/windows/win32/api/winnt/ns-winnt-luid) die die Token-ID empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType

Rufen Sie diese Methode auf, `CAccessToken` um den Tokentyp des Objekts abzurufen.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parameter

*pType*<br/>
Adresse der [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) TOKEN_TYPE-Variablen, die bei Erfolg den Typ des Tokens empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Der TOKEN_TYPE Enumerationstyp enthält Werte, die zwischen einem primären Token und einem Identitätswechseltoken unterscheiden.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser

Rufen Sie diese Methode auf, `CAccessToken` um den Benutzer zu identifizieren, der dem Objekt zugeordnet ist.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf ein [CSid-Klassenobjekt.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Rufen Sie diese Methode auf, um das `CAccessToken` Handle abzurufen, das auf das dem Objekt zugeordnete Benutzerprofil verweist.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Handle zurück, das auf das Benutzerprofil verweist, oder NULL, wenn kein Profil vorhanden ist.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Identitätswechsel

Rufen Sie diese Methode auf, um einem Thread eine Identitätswechsel `CAccessToken` zuzuweisen.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*hThread*<br/>
Handle an den Thread, dem das Identitätswechseltoken zugewiesen werden soll. Dieses Handle muss mit TOKEN_IMPERSONATE Zugriffsrechten geöffnet worden sein. Wenn *hThread* NULL ist, bewirkt die Methode, dass der Thread kein Identitätswechseltoken mehr verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn `CAccessToken` kein gültiger Zeiger auf ein Token vorhanden ist.

Die [CAutoRevertImpersonation-Klasse](../../atl/reference/cautorevertimpersonation-class.md) kann verwendet werden, um imitierte Zugriffstoken automatisch wiederzugeben.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser

Rufen Sie diese Methode auf, damit der aufrufende Thread die Identität des Sicherheitskontexts eines angemeldeten Benutzers freigibt.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

> [!IMPORTANT]
> Wenn ein Aufruf einer Identitätswechselfunktion aus irgendeinem Grund fehlschlägt, wird der Client nicht imitiert, und die Clientanforderung wird im Sicherheitskontext des Prozesses gestellt, von dem aus der Aufruf erfolgt ist. Wenn der Prozess als Konto mit hohen Berechtigungen oder als Mitglied einer administrativen Gruppe ausgeführt wird, kann der Benutzer möglicherweise Aktionen ausführen, die andernfalls nicht zulässig wären. Daher sollte der Rückgabewert für diese Funktion immer bestätigt werden.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Rufen Sie diese Methode `CAccessToken` auf, um zu testen, ob das Objekt eine Liste eingeschränkter SIDs enthält.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Objekt eine Liste mit einschränkenden SIDs enthält, FALSE, wenn keine einschränkenden SIDs vorhanden sind oder wenn die Methode fehlschlägt.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile

Rufen Sie diese Methode auf, `CAccessToken` um das dem Objekt zugeordnete Benutzerprofil zu laden.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn der `CAccessToken` kein gültiges Token enthält oder wenn bereits ein Benutzerprofil vorhanden ist.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUser

Rufen Sie diese Methode auf, um eine Anmeldesitzung für den Benutzer zu erstellen, der den angegebenen Anmeldeinformationen zugeordnet ist.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parameter

*pszUserName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Benutzernamen angibt. Dies ist der Name des Benutzerkontos, bei dem Sie sich anmelden möchten.

*pszDomain*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Domäne oder des Servers angibt, deren Kontodatenbank das *pszUserName-Konto* enthält.

*pszPassword*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die das Klartextkennwort für das von *pszUserName*angegebene Benutzerkonto angibt.

*dwLogonType*<br/>
Gibt den Typ des auszuführenden Anmeldevorgangs an. Weitere Informationen finden Sie unter [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

*dwLogonProvider*<br/>
Gibt den Anmeldeanbieter an. Weitere Informationen finden Sie unter [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Das aus der Anmeldung resultierende Zugriffstoken `CAccessToken`wird der zugeordnet. Damit diese Methode erfolgreich `CAccessToken` ist, muss das Objekt SE_TCB_NAME Berechtigungen enthalten und den Inhaber als Teil der vertrauenswürdigen Computerbasis identifizieren. Weitere Informationen zu den erforderlichen Berechtigungen finden Sie unter [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Rufen Sie diese Methode innerhalb eines COM-Servers auf, `CAccessToken` der einen Aufruf von einem Client verarbeitet, um den mit dem Zugriffstoken vom COM-Client zu initialisieren.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parameter

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*bImpersonate*<br/>
Wenn TRUE, nimmt der aktuelle Thread die Identität des aufrufenden COM-Clients an, wenn dieser Aufruf erfolgreich abgeschlossen wird. Wenn FALSE, wird das Zugriffstoken geöffnet, aber der Thread verfügt nach Abschluss dieses Aufrufs nicht über ein Identitätswechseltoken.

*bOpenAsSelf*<br/>
Gibt an, ob die Zugriffsüberprüfung für den Sicherheitskontext des Threads, der die [GetThreadToken-Methode](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) aufruft, oder für den Sicherheitskontext des Prozesses für den aufrufenden Thread durchgeführt werden soll.

Wenn dieser Parameter FALSE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts für den aufrufenden Thread durchgeführt. Wenn der Thread die Identität eines Clients annimmt, kann dieser Sicherheitskontext der eines Clientprozesses sein. Wenn dieser Parameter TRUE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts des Prozesses für den aufrufenden Thread durchgeführt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md) kann verwendet werden, um imitierte Zugriffstoken, die durch Festlegen des *flag bImpersonate* auf TRUE erstellt wurden, automatisch umzukehren.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Rufen Sie diese Methode innerhalb eines Servers auf, `CAccessToken` der Anforderungen über eine Named Pipe übernimmt, um die mit dem Zugriffstoken vom Client zu initialisieren.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parameter

*hPipe*<br/>
Handle zu einer benannten Pipe.

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*bImpersonate*<br/>
Wenn TRUE, nimmt der aktuelle Thread die Identität des aufrufenden Pipeclients an, wenn dieser Aufruf erfolgreich abgeschlossen wird. Wenn FALSE, wird das Zugriffstoken geöffnet, aber der Thread verfügt nach Abschluss dieses Aufrufs nicht über ein Identitätswechseltoken.

*bOpenAsSelf*<br/>
Gibt an, ob die Zugriffsüberprüfung für den Sicherheitskontext des Threads, der die [GetThreadToken-Methode](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) aufruft, oder für den Sicherheitskontext des Prozesses für den aufrufenden Thread durchgeführt werden soll.

Wenn dieser Parameter FALSE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts für den aufrufenden Thread durchgeführt. Wenn der Thread die Identität eines Clients annimmt, kann dieser Sicherheitskontext der eines Clientprozesses sein. Wenn dieser Parameter TRUE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts des Prozesses für den aufrufenden Thread durchgeführt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md) kann verwendet werden, um imitierte Zugriffstoken, die durch Festlegen des *flag bImpersonate* auf TRUE erstellt wurden, automatisch umzukehren.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Rufen Sie diese Methode innerhalb eines Servers auf, der `CAccessToken` einen Aufruf von einem RPC-Client verarbeitet, um den mit dem Zugriffstoken vom Client zu initialisieren.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parameter

*BindingHandle*<br/>
Bindungshandle auf dem Server, der eine Bindung an einen Client darstellt.

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*bImpersonate*<br/>
Wenn TRUE, nimmt der aktuelle Thread die Identität des aufrufenden RPC-Clients an, wenn dieser Aufruf erfolgreich abgeschlossen wird. Wenn FALSE, wird das Zugriffstoken geöffnet, aber der Thread verfügt nach Abschluss dieses Aufrufs nicht über ein Identitätswechseltoken.

*bOpenAsSelf*<br/>
Gibt an, ob die Zugriffsüberprüfung für den Sicherheitskontext des Threads, der die [GetThreadToken-Methode](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) aufruft, oder für den Sicherheitskontext des Prozesses für den aufrufenden Thread durchgeführt werden soll.

Wenn dieser Parameter FALSE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts für den aufrufenden Thread durchgeführt. Wenn der Thread die Identität eines Clients annimmt, kann dieser Sicherheitskontext der eines Clientprozesses sein. Wenn dieser Parameter TRUE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts des Prozesses für den aufrufenden Thread durchgeführt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md) kann verwendet werden, um imitierte Zugriffstoken, die durch Festlegen des *flag bImpersonate* auf TRUE erstellt wurden, automatisch umzukehren.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken

Rufen Sie diese Methode auf, um die `CAccessToken` Identitätswechselebene festzulegen, und initialisieren Sie dann die mit dem Token aus dem angegebenen Thread.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parameter

*dwDesiredAccess*<br/>
Gibt eine Zugriffsmaske an, die die angeforderten Zugriffstypen für den Zugriff auf das Zugriffstoken identifiziert. Diese angeforderten Zugriffstypen werden mit der DACL des Tokens verglichen, um zu bestimmen, welche Zugriffe gewährt oder verweigert werden.

*bImpersonate*<br/>
Wenn TRUE, wird der Thread nach Abschluss dieser Methode auf der angeforderten Identitätswechselebene belassen. Wenn FALSE, wird der Thread auf seine ursprüngliche Identitätswechselebene zurückgesetzt.

*bOpenAsSelf*<br/>
Gibt an, ob die Zugriffsüberprüfung für den Sicherheitskontext des Threads, der die [GetThreadToken-Methode](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) aufruft, oder für den Sicherheitskontext des Prozesses für den aufrufenden Thread durchgeführt werden soll.

Wenn dieser Parameter FALSE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts für den aufrufenden Thread durchgeführt. Wenn der Thread die Identität eines Clients annimmt, kann dieser Sicherheitskontext der eines Clientprozesses sein. Wenn dieser Parameter TRUE ist, wird die Zugriffsüberprüfung mithilfe des Sicherheitskontexts des Prozesses für den aufrufenden Thread durchgeführt.

*Sil*<br/>
Gibt einen [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) aufgezählten Typ an, der die Identitätswechselebene des Tokens bereitstellt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`OpenThreadToken`ist ähnlich wie [CAccessToken::GetThreadToken](#getthreadtoken), legt jedoch die `CAccessToken` Identitätswechselebene fest, bevor die vom Zugriffstoken des Threads initialisiert wird.

Die [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md) kann verwendet werden, um imitierte Zugriffstoken, die durch Festlegen des *flag bImpersonate* auf TRUE erstellt wurden, automatisch umzukehren.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck

Rufen Sie diese Methode auf, um zu bestimmen, ob ein bestimmter Satz von Berechtigungen im `CAccessToken` Objekt aktiviert ist.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parameter

*RequiredPrivileges*<br/>
Zeiger auf eine [PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) Struktur.

*pbResult*<br/>
Zeiger auf einen Wert, den die Methode festlegt, um anzugeben, `CAccessToken` ob eine oder alle der angegebenen Berechtigungen im Objekt aktiviert sind.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Bei `PrivilegeCheck` rückgaben `Attributes` wird das Element jeder [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) Struktur auf SE_PRIVILEGE_USED_FOR_ACCESS festgelegt, wenn die entsprechende Berechtigung aktiviert ist. Diese Methode ruft die [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32-Funktion auf.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Zurücksetzen

Rufen Sie diese Methode auf, um zu verhindern, dass ein Thread ein Identitätswechseltoken verwendet.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parameter

*hThread*<br/>
Behandeln Sie den Thread, um vom Identitätswechsel zurückgesetzt zu werden. Wenn *hThread* NULL ist, wird der aktuelle Thread angenommen.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die Umkehrung von Identitätswechseltoken kann automatisch mit der [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md)durchgeführt werden.

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Rufen Sie diese Methode auf, `CAccessToken` um die Standard-DACL des Objekts festzulegen.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parameter

*rDacl*<br/>
Die neuen Standardinformationen der [CDacl-Klasse.](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die Standard-DACL ist die DACL, die standardmäßig verwendet wird, wenn neue Objekte mit diesem Zugriffstoken erstellt werden.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Rufen Sie diese Methode auf, um den Besitzer des `CAccessToken` Objekts festzulegen.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Das [CSid-Klassenobjekt,](../../atl/reference/csid-class.md) das die Besitzerinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Der Besitzer ist der Standardbesitzer, der für neue Objekte verwendet wird, die erstellt wurden, während dieses Zugriffstoken aktiviert ist.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Rufen Sie diese Methode auf, `CAccessToken` um die primäre Gruppe des Objekts festzulegen.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Das [CSid-Klassenobjekt,](../../atl/reference/csid-class.md) das die primären Gruppeninformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Die primäre Gruppe ist die Standardgruppe für neue Objekte, die erstellt wurden, während dieses Zugriffstoken aktiviert ist.

## <a name="see-also"></a>Siehe auch

[ATLSecurity-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Zugriffstoken](/windows/win32/SecAuthZ/access-tokens)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
