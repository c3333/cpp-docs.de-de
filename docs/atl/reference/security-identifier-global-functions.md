---
title: Globale Funktionen von Security Identifier
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325995"
---
# <a name="security-identifier-global-functions"></a>Globale Funktionen von Security Identifier

Diese Funktionen geben gängige bekannte SID-Objekte zurück.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Gibt die DOMAIN_ALIAS_RID_ACCOUNT_OPS-SID zurück.|
|[Sids::Admins](#admins)|Gibt die DOMAIN_ALIAS_RID_ADMINS-SID zurück.|
|[Sids::AnonymousLogon](#anonymouslogon)|Gibt die SECURITY_ANONYMOUS_LOGON_RID-SID zurück.|
|[Sids::AuthenticatedUser](#authenticateduser)|Gibt die SECURITY_AUTHENTICATED_USER_RID-SID zurück.|
|[Sids::BackupOps](#backupops)|Gibt die DOMAIN_ALIAS_RID_BACKUP_OPS-SID zurück.|
|[Sids::Batch](#batch)|Gibt die SECURITY_BATCH_RID-SID zurück.|
|[Sids::CreatorGroup](#creatorgroup)|Gibt die SECURITY_CREATOR_GROUP_RID-SID zurück.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Gibt die SECURITY_CREATOR_GROUP_SERVER_RID-SID zurück.|
|[Sids::CreatorOwner](#creatorowner)|Gibt die SECURITY_CREATOR_OWNER_RID-SID zurück.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Gibt die SECURITY_CREATOR_OWNER_SERVER_RID-SID zurück.|
|[Sids::Dialup](#dialup)|Gibt die SECURITY_DIALUP_RID-SID zurück.|
|[Sids::Guests](#guests)|Gibt die DOMAIN_ALIAS_RID_GUESTS-SID zurück.|
|[Sids::Interactive](#interactive)|Gibt die SECURITY_INTERACTIVE_RID-SID zurück.|
|[Sids::Local](#local)|Gibt die SECURITY_LOCAL_RID-SID zurück.|
|[Sids::Network](#network)|Gibt die SECURITY_NETWORK_RID-SID zurück.|
|[Sids::NetworkService](#networkservice)|Gibt die SECURITY_NETWORK_SERVICE_RID-SID zurück.|
|[Sids::Null](#null)|Gibt die SECURITY_NULL_RID-SID zurück.|
|[Sids::PreW2KAccess](#prew2kaccess)|Gibt die DOMAIN_ALIAS_RID_PREW2KCOMPACCESS-SID zurück.|
|[Sids::PowerUsers](#powerusers)|Gibt die DOMAIN_ALIAS_RID_POWER_USERS-SID zurück.|
|[Sids::PrintOps](#printops)|Gibt die DOMAIN_ALIAS_RID_PRINT_OPS-SID zurück.|
|[Sids::Proxy](#proxy)|Gibt die SECURITY_PROXY_RID-SID zurück.|
|[Sids::RasServers](#rasservers)|Gibt die DOMAIN_ALIAS_RID_RAS_SERVERS-SID zurück.|
|[Sids::Replicator](#replicator)|Gibt die DOMAIN_ALIAS_RID_REPLICATOR-SID zurück.|
|[Sids::RestrictedCode](#restrictedcode)|Gibt die SECURITY_RESTRICTED_CODE_RID-SID zurück.|
|[Sids::Self](#self)|Gibt die SECURITY_PRINCIPAL_SELF_RID-SID zurück.|
|[Sids::ServerLogon](#serverlogon)|Gibt die SECURITY_SERVER_LOGON_RID-SID zurück.|
|[Sids::Service](#service)|Gibt die SECURITY_SERVICE_RID-SID zurück.|
|[Sids::System](#system)|Gibt die SECURITY_LOCAL_SYSTEM_RID-SID zurück.|
|[Sids::SystemOps](#systemops)|Gibt die DOMAIN_ALIAS_RID_SYSTEM_OPS-SID zurück.|
|[Sids::TerminalServer](#terminalserver)|Gibt die SECURITY_TERMINAL_SERVER_RID-SID zurück.|
|[Sids::Users](#users)|Gibt die DOMAIN_ALIAS_RID_USERS-SID zurück.|
|[Sids::World](#world)|Gibt die SECURITY_WORLD_RID-SID zurück.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids::AccountOps

Gibt die DOMAIN_ALIAS_RID_ACCOUNT_OPS-SID zurück.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids::Admins

Gibt die DOMAIN_ALIAS_RID_ADMINS-SID zurück.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::AnonymousLogon

Gibt die SECURITY_ANONYMOUS_LOGON_RID-SID zurück.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::AuthenticatedUser

Gibt die SECURITY_AUTHENTICATED_USER_RID-SID zurück.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids::BackupOps

Gibt die DOMAIN_ALIAS_RID_BACKUP_OPS-SID zurück.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids::Batch

Gibt die SECURITY_BATCH_RID-SID zurück.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::CreatorGroup

Gibt die SECURITY_CREATOR_GROUP_RID-SID zurück.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::CreatorGroupServer

Gibt die SECURITY_CREATOR_GROUP_SERVER_RID-SID zurück.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids::CreatorOwner

Gibt die SECURITY_CREATOR_OWNER_RID-SID zurück.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::CreatorOwnerServer

Gibt die SECURITY_CREATOR_OWNER_SERVER_RID-SID zurück.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>Sids::Dialup

Gibt die SECURITY_DIALUP_RID-SID zurück.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>Sids::Gäste

Gibt die DOMAIN_ALIAS_RID_GUESTS-SID zurück.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids::Interaktiv

Gibt die SECURITY_INTERACTIVE_RID-SID zurück.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids::Lokal

Gibt die SECURITY_LOCAL_RID-SID zurück.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids::Netzwerk

Gibt die SECURITY_NETWORK_RID-SID zurück.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids::NetworkService

Gibt die SECURITY_NETWORK_SERVICE_RID-SID zurück.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie NetworkService, um dem NT AUTHORITY-NetworkService-Benutzer das Lesen eines CPerfMon-Sicherheitsobjekts zu ermöglichen. NetworkService fügt dem ATLServer-Code ein SecurityAttribute hinzu, mit dem sich die DLL unter dem NetworkService-Konto unter Windows XP Home Edition, Windows XP Professional, Windows Server 2003 und einem größeren Betriebssystem anmelden kann.

Wenn benutzerdefinierte Protokollindikatoren mit der ATLServer CPerfMon-Klasse in der Perfmon MMC erstellt werden, werden die Leistungsindikatoren möglicherweise nicht angezeigt, wenn die Protokolldatei angezeigt wird, obwohl sie in der Echtzeitansicht korrekt angezeigt werden. Benutzerdefinierte Leistungsindikatoren von CPerfMon verfügen nicht über die erforderlichen Berechtigungen, um unter dem Dienst "Leistungsprotokolle und Warnungen" (smlogsvc.exe) unter Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (oder höher) Betriebssystemen ausgeführt zu werden. Dieser Dienst wird unter dem Konto "NT AUTHORITY-NetworkService" ausgeführt.

## <a name="sidsnull"></a><a name="null"></a>Sids::Null

Gibt die SECURITY_NULL_RID-SID zurück.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess

Gibt die DOMAIN_ALIAS_RID_PREW2KCOMPACCESS-SID zurück.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids::PowerBenutzer

Gibt die DOMAIN_ALIAS_RID_POWER_USERS-SID zurück.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>Sids::PrintOps

Gibt die DOMAIN_ALIAS_RID_PRINT_OPS-SID zurück.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>Sids::Proxy

Gibt die SECURITY_PROXY_RID-SID zurück.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids::RasServers

Gibt die DOMAIN_ALIAS_RID_RAS_SERVERS-SID zurück.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids::Replikator

Gibt die DOMAIN_ALIAS_RID_REPLICATOR-SID zurück.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::RestrictedCode

Gibt die SECURITY_RESTRICTED_CODE_RID-SID zurück.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>Sids::Selbst

Gibt die SECURITY_PRINCIPAL_SELF_RID-SID zurück.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids::ServerLogon

Gibt die SECURITY_SERVER_LOGON_RID-SID zurück.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>Sids::Service

Gibt die SECURITY_SERVICE_RID-SID zurück.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids::System

Gibt die SECURITY_LOCAL_SYSTEM_RID-SID zurück.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids::SystemOps

Gibt die DOMAIN_ALIAS_RID_SYSTEM_OPS-SID zurück.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids::TerminalServer

Gibt die SECURITY_TERMINAL_SERVER_RID-SID zurück.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids::Benutzer

Gibt die DOMAIN_ALIAS_RID_USERS-SID zurück.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>Sids::Welt

Gibt die SECURITY_WORLD_RID-SID zurück.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
