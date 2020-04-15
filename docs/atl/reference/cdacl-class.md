---
title: CDacl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327151"
---
# <a name="cdacl-class"></a>CDacl-Klasse

Diese Klasse ist ein Wrapper für eine DACL-Struktur (discretionary access-control list).

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CDacl : public CAcl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Der Konstruktor.|
|[CDacl::-CDacl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Fügt dem `CDacl` Objekt einen zulässigen ACE (Access-Control-Eintrag) hinzu.|
|[CDacl::AddDeniedAce](#adddeniedace)|Fügt dem `CDacl` Objekt einen verweigerten ACE hinzu.|
|[CDacl::GetAceCount](#getacecount)|Gibt die Anzahl der ACEs (Zugriffssteuerungseinträge) im `CDacl` Objekt zurück.|
|[CDacl::RemoveAce](#removeace)|Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CDacl` Objekt.|
|[CDacl::AlleAsse entfernen](#removeallaces)|Entfernt alle im `CDacl` Objekt enthaltenen ACEs.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDacl::Operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Die Sicherheitsbeschreibung eines Objekts kann eine DACL enthalten. Eine DACL enthält null oder mehr ACEs (Zugriffssteuerungseinträge), die die Benutzer und Gruppen identifizieren, die auf das Objekt zugreifen können. Wenn eine DACL leer ist (d. h., sie enthält Null-ACEs), wird kein Zugriff explizit gewährt, sodass der Zugriff implizit verweigert wird. Wenn jedoch der Sicherheitsdeskriptor eines Objekts nicht über eine DACL verfügt, ist das Objekt ungeschützt, und jeder hat vollständigen Zugriff.

Um die DACL eines Objekts abzurufen, müssen Sie der Besitzer des Objekts sein oder READ_CONTROL Zugriff auf das Objekt haben. Um die DACL eines Objekts zu ändern, müssen Sie WRITE_DAC Zugriff auf das Objekt haben.

Verwenden Sie die bereitgestellten Klassenmethoden, um ACEs `CDacl` zu erstellen, hinzuzufügen, zu entfernen und aus dem Objekt zu löschen. Siehe auch [AtlGetDacl](security-global-functions.md#atlgetdacl) und [AtlSetDacl](security-global-functions.md#atlsetdacl).

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cacl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce

Fügt dem `CDacl` Objekt einen zulässigen ACE (Access-Control-Eintrag) hinzu.

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Ein [CSid-Objekt.](../../atl/reference/csid-class.md)

*Accessmask*<br/>
Gibt die Maske der Zugriffsrechte an, `CSid` die für das angegebene Objekt zulässig sein soll.

*AceFlags*<br/>
Ein Satz von Bitflags, die die ACE-Vererbung steuern.

*pObjectType*<br/>
Der Objekttyp.

*pInheritedObjectType*<br/>
Der geerbte Objekttyp.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn `CDacl` der ACE zum Objekt hinzugefügt wird, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Ein `CDacl` Objekt enthält null oder mehr ACEs (Zugriffssteuerungseinträge), die die Benutzer und Gruppen identifizieren, die auf das Objekt zugreifen können. Diese Methode fügt einen ACE `CDacl` hinzu, der den Zugriff auf das Objekt ermöglicht.

Eine Beschreibung der verschiedenen Flags, die im `AceFlags` Parameter festgelegt werden können, [finden Sie in ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce

Fügt dem `CDacl` Objekt einen verweigerten ACE (Access-Control-Eintrag) hinzu.

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Ein `CSid` -Objekt.

*Accessmask*<br/>
Gibt die Maske der Zugriffsrechte an, `CSid` die für das angegebene Objekt verweigert werden sollen.

*AceFlags*<br/>
Ein Satz von Bitflags, die die ACE-Vererbung steuern. In der ersten Form der Methode wird standardmäßig 0 angezeigt.

*pObjectType*<br/>
Der Objekttyp.

*pInheritedObjectType*<br/>
Der geerbte Objekttyp.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn `CDacl` der ACE zum Objekt hinzugefügt wird, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Ein `CDacl` Objekt enthält null oder mehr ACEs (Zugriffssteuerungseinträge), die die Benutzer und Gruppen identifizieren, die auf das Objekt zugreifen können. Diese Methode fügt einen ACE `CDacl` hinzu, der den Zugriff auf das Objekt verweigert.

Eine Beschreibung der verschiedenen Flags, die im `AceFlags` Parameter festgelegt werden können, [finden Sie in ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl

Der Konstruktor.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Eine `ACL` vorhandene Struktur (Zugriffssteuerungsliste).

### <a name="remarks"></a>Bemerkungen

Das `CDacl` Objekt kann optional mit `ACL` einer vorhandenen Struktur erstellt werden. Es ist wichtig zu beachten, dass nur eine DACL (discretionary Access-Control List) und keine SACL (Systemzugriffssteuerungsliste) als dieser Parameter übergeben werden soll. Bei Debugbuilds führt das Übergeben einer SACL zu einem ASSERT. Bei Releasebuilds führt das Übergeben einer SACL dazu, dass die ACEs (Access-Control-Einträge) in der ACL ignoriert werden, und es tritt kein Fehler auf.

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl::-CDacl

Der Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle vom Objekt erworbenen Ressourcen frei, einschließlich aller ACEs (Access-Control-Einträge) mit [CDacl::RemoveAllAces](#removeallaces).

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount

Gibt die Anzahl der ACEs (Zugriffssteuerungseinträge) im `CDacl` Objekt zurück.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im `CDacl` Objekt enthaltenen ACEs zurück.

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::Operator =

Zuweisungsoperator.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Die ACL (Zugriffssteuerungsliste), die dem vorhandenen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CDacl` auf das aktualisierte Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Sie sollten sicherstellen, dass Sie nur eine DACL (discretionary access-control list) an diese Funktion übergeben. Das Übergeben einer SACL (Systemzugriffssteuerungsliste) an diese Funktion führt zu einem ASSERT in Debugbuilds, verursacht jedoch keinen Fehler in Releasebuilds.

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce

Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CDacl` Objekt.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index für den zu entfernenden ACE-Eintrag.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)abgeleitet.

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::AlleAsse entfernen

Entfernt alle acEs (Access-Control-Einträge), die `CDacl` im Objekt enthalten sind.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Bemerkungen

Entfernt jede `ACE` (Zugriffssteuerungseintrag) Struktur (falls vorhanden) im `CDacl` Objekt.

## <a name="see-also"></a>Siehe auch

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[CAcl-Klasse](../../atl/reference/cacl-class.md)<br/>
[ACLs](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Asse](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
