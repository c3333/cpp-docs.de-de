---
title: CSacl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: d5a060555901361ef6c70c6a4f801605eafd92cf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746550"
---
# <a name="csacl-class"></a>CSacl-Klasse

Diese Klasse ist ein Wrapper für eine SACL-Struktur (Systemzugriffssteuerungsliste).

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CSacl : public CAcl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|Der Konstruktor.|
|[CSacl::-CSacl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Fügt dem `CSacl` Objekt einen Überwachungszugriffssteuerungseintrag (ACE) hinzu.|
|[CSacl::GetAceCount](#getacecount)|Gibt die Anzahl der Zugriffssteuerungseinträge (Access-Control Entries, ACEs) im `CSacl` Objekt zurück.|
|[CSacl::RemoveAce](#removeace)|Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CSacl` Objekt.|
|[CSacl::AlleAsse entfernen](#removeallaces)|Entfernt alle im `CSacl` Objekt enthaltenen ACEs.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSacl::Operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Eine SACL enthält Zugriffssteuerungseinträge (Access-Control Entries, ACEs), die die Typen von Zugriffsversuchen angeben, die Überwachungsdatensätze im Sicherheitsereignisprotokoll eines Domänencontrollers generieren. Beachten Sie, dass eine SACL Protokolleinträge nur auf dem Domänencontroller generiert, auf dem der Zugriffsversuch stattgefunden hat, nicht auf jedem Domänencontroller, der ein Replikat des Objekts enthält.

Um die SACL im Sicherheitsdeskriptor eines Objekts festzulegen oder abzurufen, muss die SE_SECURITY_NAME Berechtigung im Zugriffstoken des anfordernden Threads aktiviert sein. Die Administratorengruppe verfügt standardmäßig über diese Berechtigung, die anderen Benutzern oder Gruppen gewährt werden kann. Die Berechtigung ist nicht erforderlich: Bevor der durch die Berechtigung definierte Vorgang ausgeführt werden kann, muss die Berechtigung im Sicherheitszugriffstoken aktiviert sein, damit sie wirksam wird. Das Modell ermöglicht die Aktivierung von Berechtigungen nur für bestimmte Systemvorgänge und wird dann deaktiviert, wenn sie nicht mehr benötigt werden. Beispiele für die Aktivierung von SE_SECURITY_NAME finden Sie unter [AtlGetSacl](security-global-functions.md#atlgetsacl) und [AtlSetSacl.](security-global-functions.md#atlsetsacl)

Verwenden Sie die bereitgestellten Klassenmethoden, um ACEs `SACL` aus dem Objekt hinzuzufügen, zu entfernen, zu erstellen und zu löschen. Siehe auch [AtlGetSacl](security-global-functions.md#atlgetsacl) und [AtlSetSacl](security-global-functions.md#atlsetsacl).

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cacl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce

Fügt dem `CSacl` Objekt einen Überwachungszugriffssteuerungseintrag (ACE) hinzu.

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Das [CSid-Objekt.](../../atl/reference/csid-class.md)

*Accessmask*<br/>
Gibt die Maske der Zugriffsrechte an, `CSid` die für das angegebene Objekt überwacht werden sollen.

*bErfolg*<br/>
Gibt an, ob zulässige Zugriffsversuche überwacht werden sollen. Legen Sie dieses Flag auf true fest, um die Überwachung zu aktivieren. Andernfalls setzen Sie es auf false.

*bFehler*<br/>
Gibt an, ob verweigerte Zugriffsversuche überwacht werden sollen. Legen Sie dieses Flag auf true fest, um die Überwachung zu aktivieren. Andernfalls setzen Sie es auf false.

*AceFlags*<br/>
Ein Satz von Bitflags, die die ACE-Vererbung steuern.

*pObjectType*<br/>
Der Objekttyp.

*pInheritedObjectType*<br/>
Der geerbte Objekttyp.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn `CSacl` der ACE zum Objekt hinzugefügt wird, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Ein `CSacl` Objekt enthält Zugriffssteuerungseinträge (Access-Control Entries, ACEs), die die Typen von Zugriffsversuchen angeben, die Überwachungsdatensätze im Sicherheitsereignisprotokoll generieren. Diese Methode fügt dem `CSacl` Objekt einen solchen ACE hinzu.

Eine Beschreibung der verschiedenen Flags, die im *AceFlags-Parameter* festgelegt werden können, [finden Sie ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl

Der Konstruktor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Eine `ACL` vorhandene Struktur (Zugriffssteuerungsliste).

### <a name="remarks"></a>Bemerkungen

Das `CSacl` Objekt kann optional mit `ACL` einer vorhandenen Struktur erstellt werden. Stellen Sie sicher, dass es sich bei diesem Parameter um eine Systemzugriffssteuerungsliste (SACL) und nicht um eine DACL (Discretionary Access Control List) handelt. Wenn in Debugbuilds eine DACL bereitgestellt wird, tritt eine Assertion auf. In Release-Builds werden alle Einträge aus einer DACL ignoriert.

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl::-CSacl

Der Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle vom Objekt erworbenen Ressourcen frei, einschließlich aller Zugriffssteuerungseinträge (Access-Control Entries, ACEs).

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount

Gibt die Anzahl der Zugriffssteuerungseinträge (Access-Control Entries, ACEs) im `CSacl` Objekt zurück.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im `CSacl` Objekt enthaltenen ACEs zurück.

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::Operator =

Zuweisungsoperator.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Die `ACL` (Zugriffssteuerungsliste), die dem vorhandenen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CSacl` auf das aktualisierte Objekt zurück. Stellen Sie `ACL` sicher, dass es sich bei dem Parameter tatsächlich um eine Systemzugriffssteuerungsliste (SACL) und nicht um eine DACL (Discretionary Access Control List) handelt. Bei Debugbuilds tritt eine Assertion auf, `ACL` und in Release-Builds wird der Parameter ignoriert.

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::RemoveAce

Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CSacl` Objekt.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index für den zu entfernenden ACE-Eintrag.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)abgeleitet.

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::AlleAsse entfernen

Entfernt alle im `CSacl` Objekt enthaltenen Zugriffssteuerungseinträge (Access-Control Entries, ACEs).

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Bemerkungen

Entfernt jede `ACE` Struktur (falls vorhanden) im `CSacl` Objekt.

## <a name="see-also"></a>Weitere Informationen

[CAcl-Klasse](../../atl/reference/cacl-class.md)<br/>
[ACLs](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Asse](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
