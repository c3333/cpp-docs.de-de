---
title: CAutoRevertImpersonation-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: ea119436fd36d0814c05f1b48380028ad3f63f0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748241"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation-Klasse

Diese Klasse setzt [CAccessToken-Objekte](../../atl/reference/caccesstoken-class.md) in einen Status zurück, der nicht mit dem Namen "Impersonieren" ausgeführt wird, wenn der Gültigkeitsbereich nicht mehr angezeigt wird.

## <a name="syntax"></a>Syntax

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Konstrukte `CAutoRevertImpersonation` eines Objekts|
|[CAutoRevertImpersonation::'CAutoRevertImpersonation](#dtor)|Zerstört das Objekt und kehrt den Identitätswechsel mit Zugriffstoken zurück.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAutoRevertImpersonation::Anfügen](#attach)|Automatisiert die Identitätswechsel-Reversion eines Zugriffstokens.|
|[CAutoRevertImpersonation::Detach](#detach)|Bricht die automatische Identitätswechsel-Reversion ab.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Ruft das diesem Objekt zugeordnete Zugriffstoken ab.|

## <a name="remarks"></a>Bemerkungen

Ein [Zugriffstoken](/windows/win32/SecAuthZ/access-tokens) ist ein Objekt, das den Sicherheitskontext eines Prozesses oder Threads beschreibt und jedem Benutzer zugewiesen wird, der an einem Windows NT- oder Windows 2000-System angemeldet ist. Diese Zugriffstoken können mit `CAccessToken` der Klasse dargestellt werden.

Manchmal ist es notwendig, zugriffstoken zu imitieren. Diese Klasse wird als Annehmlichkeit bereitgestellt, führt jedoch keine Identitätswechsel von Zugriffstoken durch. Es führt nur die automatische Umkehrung in einen nicht mit Personen personierten Zustand aus. Dies liegt daran, dass Tokenzugriffsidentitätswechsel auf verschiedene Arten ausgeführt werden können.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>CAutoRevertImpersonation::Anfügen

Automatisiert die Identitätswechsel-Reversion eines Zugriffstokens.

```cpp
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parameter

*Pat*<br/>
Die Adresse des [CAccessToken-Objekts,](../../atl/reference/caccesstoken-class.md) das automatisch zurückgesetzt werden soll

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte nur verwendet werden, wenn das [CAutoRevertImpersonation-Objekt](../../atl/reference/cautorevertimpersonation-class.md) mit einem NULL-Zeiger `CAccessToken` erstellt wurde oder wenn [Detach](#detach) zuvor aufgerufen wurde. In einfachen Fällen ist es nicht erforderlich, diese Methode zu verwenden.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Erstellt ein `CAutoRevertImpersonation`-Objekt.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parameter

*Pat*<br/>
Die Adresse des [CAccessToken-Objekts,](../../atl/reference/caccesstoken-class.md) das automatisch wiederhergestellt werden soll.

### <a name="remarks"></a>Bemerkungen

Die tatsächliche Identitätswechsel des Zugriffstokens sollte getrennt von und vorzugsweise `CAutoRevertImpersonation` vor der Erstellung eines Objekts ausgeführt werden. Diese Identitätswechsel werden automatisch wiederhergestellt, wenn das `CAutoRevertImpersonation` Objekt den Gültigkeitsbereich verlässt.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>CAutoRevertImpersonation::'CAutoRevertImpersonation

Zerstört das Objekt und kehrt den Identitätswechsel mit Zugriffstoken zurück.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Bemerkungen

Kehrt alle Identitätswechsel zurück, die derzeit für das [CAccessToken-Objekt](../../atl/reference/caccesstoken-class.md) wirksam sind, das entweder bei der Konstruktion oder über die [Attach-Methode](#attach) bereitgestellt wird. Wenn `CAccessToken` nein zugeordnet ist, hat der Destruktor keine Auswirkungen.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>CAutoRevertImpersonation::Detach

Bricht die automatische Identitätswechsel-Reversion ab.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des zuvor zugeordneten [CAccessToken](../../atl/reference/caccesstoken-class.md), oder NULL, wenn keine Zuordnung vorhanden war.

### <a name="remarks"></a>Bemerkungen

Durch Aufrufen von `CAutoRevertImpersonation` **Detach** wird verhindert, dass das Objekt alle Identitätswechsel zurücksetzt, die derzeit für das diesem Objekt zugeordnete [CAccessToken-Objekt](../../atl/reference/caccesstoken-class.md) wirksam sind. `CAutoRevertImpersonation`kann dann ohne Wirkung zerstört oder mit `CAccessToken` [Attach](#attach)wieder mit demselben oder einem anderen Objekt verknüpft werden.

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Ruft das diesem Objekt zugeordnete Zugriffstoken ab.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des zuvor zugeordneten [CAccessToken](../../atl/reference/caccesstoken-class.md), oder NULL, wenn keine Zuordnung vorhanden war.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode für die Zwecke aufgerufen wird, die die `CAccessToken` Umkehrung einer Identitätswechsel des Objekts umfassen, sollte stattdessen die [Detach-Methode](#detach) verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[ATLSecurity-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Zugriffstoken](/windows/win32/SecAuthZ/access-tokens)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
