---
title: CAcl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 458f7cd50462a145d005f3f81d87cc06fc7e01b1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748775"
---
# <a name="cacl-class"></a>CAcl-Klasse

Diese Klasse ist ein `ACL` Wrapper für eine Struktur (Zugriffssteuerungsliste).

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAcl
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Ein Array von ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Ein Array von BYTEs.|
|[CAcl::CAceTypeArray](#cacetypearray)|Ein Array von BYTEs.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Der Konstruktor.|
|[CAcl::-CAcl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Gibt die Anzahl der ACE-Objekte (Access-Control Entry) zurück.|
|[CAcl::GetAclEinträge](#getaclentries)|Ruft die ACL-Einträge (Access-Control `CAcl` List) aus dem Objekt ab.|
|[CAcl::GetAclEntry](#getaclentry)|Ruft alle Informationen zu einem Eintrag `CAcl` in einem Objekt ab.|
|[CAcl::GetLength](#getlength)|Gibt die Länge der ACL zurück.|
|[CAcl::GetPACL](#getpacl)|Gibt einen PACL zurück (Zeiger auf eine ACL).|
|[CAcl::IsEmpty](#isempty)|Testet `CAcl` das Objekt auf Einträge.|
|[CAcl::IsNull](#isnull)|Gibt den Status `CAcl` des Objekts zurück.|
|[CAcl::RemoveAce](#removeace)|Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CAcl` Objekt.|
|[CAcl::RemoveAces](#removeaces)|Entfernt alle ACEs (Zugriffssteuerungseinträge) `CAcl` aus der, `CSid`die für die angegebene gelten.|
|[CAcl::SetEmpty](#setempty)|Markiert `CAcl` das Objekt als leer.|
|[CAcl::SetNull](#setnull)|Markiert `CAcl` das Objekt als NULL.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAcl::operator const ACL *](#operator_const_acl__star)|Gibt ein `CAcl` Objekt `ACL` in eine Struktur um.|
|[CAcl::operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Die `ACL` Struktur ist der Header einer ACL (Zugriffssteuerungsliste). Eine ACL enthält eine sequenzielle Liste von null oder mehr [ACEs](/windows/win32/SecAuthZ/access-control-entries) (Zugriffssteuerungseinträge). Die einzelnen ACEs in einer ACL sind von 0 bis *n-1*nummeriert, wobei *n* die Anzahl der ACEs in der ACL ist. Beim Bearbeiten einer ACL bezieht sich eine Anwendung durch ihren Index auf einen Zugriffssteuerungseintrag (Access-Control Entry, ACE) innerhalb der ACL.

Es gibt zwei ACL-Typen:

- Ermessensabhängiger

- System

Eine diskretionäre ACL wird vom Besitzer eines Objekts oder von jemandem kontrolliert, der WRITE_DAC Zugriff auf das Objekt gewährt wird. Es gibt den Zugriff an, den bestimmte Benutzer und Gruppen auf ein Objekt haben können. Beispielsweise kann der Besitzer einer Datei eine diskretionäre Zugriffssteuerungsweite verwenden, um zu steuern, welche Benutzer und Gruppen zugriff auf die Datei haben können und welche nicht.

Einem Objekt können auch Sicherheitsinformationen auf Systemebene zugeordnet sein, und zwar in Form einer System-ACL, die von einem Systemadministrator gesteuert wird. Eine System-ACL kann es dem Systemadministrator ermöglichen, alle Versuche, auf ein Objekt zuzugreifen, zu überwachen.

Weitere Informationen finden Sie in der [ACL-Diskussion](/windows/win32/SecAuthZ/access-control-lists) im Windows SDK.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Ein Array von ACCESS_MASK Objekten.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Bemerkungen

Dieser typedef gibt den Arraytyp an, der zum Speichern von Zugriffsrechten verwendet werden kann, die in Zugriffssteuerungseinträgen (Access-Control Entries, ACEs) verwendet werden.

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray

Ein Array von BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Bemerkungen

Dieser typedef gibt den Arraytyp an, der zum Definieren der typspezifischen Steuerungsflags (Access-Control Entry, ACE) verwendet wird. Die [vollständige](/windows/win32/api/winnt/ns-winnt-ace_header) Liste der möglichen Flags finden Sie in der ACE_HEADER-Definition.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray

Ein Array von BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Bemerkungen

Dieser typedef gibt den Arraytyp an, der zum Definieren der Art der ACE-Objekte (Access-Control Entry) verwendet wird, z. B. ACCESS_ALLOWED_ACE_TYPE oder ACCESS_DENIED_ACE_TYPE. Die [vollständige](/windows/win32/api/winnt/ns-winnt-ace_header) Liste der möglichen Typen finden Sie in der ACE_HEADER-Definition.

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

Der Konstruktor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Ein vorhandenes `CAcl`-Objekt.

### <a name="remarks"></a>Bemerkungen

Das `CAcl` Objekt kann optional mit `CAcl` einem vorhandenen Objekt erstellt werden.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl::-CAcl

Der Destruktor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle Ressourcen frei, die vom Objekt erworben wurden.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount

Gibt die Anzahl der ACE-Objekte (Access-Control Entry) zurück.

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der `CAcl` ACE-Einträge im Objekt zurück.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEinträge

Ruft die ACL-Einträge (Access-Control `CAcl` List) aus dem Objekt ab.

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSids*<br/>
Ein Zeiger auf ein Array von [CSid-Objekten.](../../atl/reference/csid-class.md)

*pAccessMasks*<br/>
Die Zugriffsmasken.

*pAceTypes*<br/>
Die Typisierungs- und Zugriffssteuerungseintrag (ACCESS-Control Entry, ACE).

*pAceFlags*<br/>
Die ACE-Flags.

### <a name="remarks"></a>Bemerkungen

Diese Methode füllt die Arrayparameter mit den Details `CAcl` jedes ACE-Objekts, das im Objekt enthalten ist. Verwenden Sie NULL, wenn die Details für dieses bestimmte Array nicht erforderlich sind.

Der Inhalt jedes Arrays entspricht einander, d. h., das erste Element des `CAccessMaskArray` Arrays entspricht dem ersten Element im `CSidArray` Array usw.

Weitere Informationen zu ACE-Typen und -Flags finden Sie [in ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry

Ruft alle Informationen zu einem Eintrag in einer Zugriffssteuerungsliste (Access-Control List, ACL) ab.

```cpp
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index für den abzurufenden ACL-Eintrag.

*pSid*<br/>
Das [CSid-Objekt,](../../atl/reference/csid-class.md) auf das der ACL-Eintrag angewendet wird.

*pMaske*<br/>
Die Maske, die Berechtigungen zum Gewähren oder Verweigern des Zugriffs angibt.

*pType*<br/>
Der ACE-Typ.

*pFlags*<br/>
Die ACE-Flags.

*pObjectType*<br/>
Der Objekttyp. Dies wird auf GUID_NULL festgelegt, wenn der Objekttyp nicht im ACE angegeben ist oder wenn der ACE kein OBJECT ACE ist.

*pInheritedObjectType*<br/>
Der geerbte Objekttyp. Dies wird auf GUID_NULL festgelegt, wenn der geerbte Objekttyp nicht im ACE angegeben ist oder wenn der ACE kein OBJECT ACE ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft alle Informationen über einen einzelnen ACE ab und stellt mehr Informationen bereit, als [CAcl::GetAclEntries](#getaclentries) allein zur Verfügung stellt.

Weitere Informationen zu ACE-Typen und -Flags finden Sie [in ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl::GetLength

Gibt die Länge der Zugriffssteuerungsliste (Access-Control List, ACL) zurück.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die erforderliche Länge in `ACL` Bytes zurück, die erforderlich ist, um die Struktur zu halten.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Gibt einen Zeiger an eine Zugriffssteuerungsliste (Access-Control List, ACL) zurück.

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `ACL` auf die Struktur zurück.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty

Testet `CAcl` das Objekt auf Einträge.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt TRUE `CAcl` zurück, wenn das Objekt nicht NULL ist und keine Einträge enthält. Gibt FALSE `CAcl` zurück, wenn das Objekt entweder NULL ist oder mindestens einen Eintrag enthält.

## <a name="caclisnull"></a><a name="isnull"></a>CAcl::IsNull

Gibt den Status `CAcl` des Objekts zurück.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE `CAcl` zurück, wenn das Objekt NULL ist, andernfalls FALSE.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::operator const ACL *

Gibt ein `CAcl` Objekt `ACL` in eine Struktur (Zugriffssteuerungsliste) um.

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt die Adresse `ACL` der Struktur zurück.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::operator =

Zuweisungsoperator.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Der, `CAcl` der dem vorhandenen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CAcl` auf das aktualisierte Objekt zurück.

## <a name="caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce

Entfernt einen bestimmten ACE (Access-Control-Eintrag) aus dem `CAcl` Objekt.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index für den zu entfernenden ACE-Eintrag.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)abgeleitet.

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Entfernt alle ACEs (Zugriffssteuerungseinträge) aus `CAcl` dem, die `CSid`für die angegebene gelten.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Ein Verweis auf ein `CSid`-Objekt.

## <a name="caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty

Markiert `CAcl` das Objekt als leer.

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>Bemerkungen

Der `CAcl` kann auf leer oder auf NULL gesetzt werden: Die beiden Zustände sind unterschiedlich.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::SetNull

Markiert `CAcl` das Objekt als NULL.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Bemerkungen

Der `CAcl` kann auf leer oder auf NULL gesetzt werden: Die beiden Zustände sind unterschiedlich.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
