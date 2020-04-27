---
title: CaCl-Klasse
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
ms.openlocfilehash: 3beef0fc6a75a952956f032d3e0e4cbe4faed86b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168448"
---
# <a name="cacl-class"></a>CaCl-Klasse

Diese Klasse ist ein Wrapper für eine `ACL` (Access-Control List)-Struktur.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAcl
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CaCl:: caccessmaskarray](#caccessmaskarray)|Ein Array von ACCESS_MASKs.|
|[CaCl:: caceflagarray](#caceflagarray)|Ein Bytearray.|
|[CaCl:: cacetypeer Array](#cacetypearray)|Ein Bytearray.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CaCl:: CAcl](#cacl)|Der Konstruktor.|
|[CaCl:: ~ CAcl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CaCl:: getacecount](#getacecount)|Gibt die Anzahl der ACE (Access Control Entry)-Objekte zurück.|
|[CaCl:: getaclentries](#getaclentries)|Ruft die Einträge in der Zugriffs Steuerungs Liste (Access Control List, ACL) aus dem `CAcl` -Objekt ab.|
|[CaCl:: getaclentry](#getaclentry)|Ruft alle Informationen zu einem Eintrag in einem `CAcl` -Objekt ab.|
|[CaCl:: GetLength](#getlength)|Gibt die Länge der ACL zurück.|
|[CaCl:: getpacl](#getpacl)|Gibt eine Pacl (Zeiger auf eine ACL) zurück.|
|[CaCl:: IsEmpty](#isempty)|Testet das `CAcl` -Objekt auf Einträge.|
|[CaCl:: IsNull](#isnull)|Gibt den Status des- `CAcl` Objekts zurück.|
|[CaCl:: RemoveAce](#removeace)|Entfernt einen bestimmten ACE (Zugriffs Steuerungs Eintrag) aus dem `CAcl` -Objekt.|
|[CaCl:: removeaces](#removeaces)|Entfernt alle ACEs (Zugriffs Steuerungs Einträge) aus der `CAcl` , die auf den angegebenen `CSid`angewendet werden.|
|[CaCl:: * tempty](#setempty)|Markiert das `CAcl` -Objekt als leer.|
|[CaCl:: SetNull](#setnull)|Markiert das `CAcl` Objekt als NULL.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CaCl:: Operator Konstanten ACL *](#operator_const_acl__star)|Wandelt ein `CAcl` -Objekt in `ACL` eine-Struktur um.|
|[CaCl:: Operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Die `ACL` -Struktur ist der Header einer Zugriffs Steuerungs Liste (Access Control List, ACL). Eine ACL enthält eine sequenzielle Liste von NULL oder mehr [ACEs](/windows/win32/SecAuthZ/access-control-entries) (Access-Control-Einträge). Die einzelnen ACEs in einer ACL sind von 0 bis *n-1*nummeriert, wobei *n* die Anzahl der ACEs in der ACL ist. Wenn eine ACL bearbeitet wird, bezieht sich eine Anwendung auf einen Zugriffs Steuerungs Eintrag (ACE) innerhalb der ACL durch ihren Index.

Es gibt zwei ACL-Typen:

- Räumen

- System

Eine freigegebene Zugriffs Steuerungs Liste wird vom Besitzer eines Objekts gesteuert, oder jeder Person, der WRITE_DAC Zugriff auf das Objekt gewährt wurde. Er gibt den Zugriff an, den bestimmte Benutzer und Gruppen auf ein Objekt haben können. Der Besitzer einer Datei kann z. b. eine freigegebene ACL verwenden, um zu steuern, welche Benutzer und Gruppen Zugriff auf die Datei haben können.

Einem Objekt können auch Sicherheitsinformationen auf Systemebene in Form einer System-ACL zugeordnet werden, die von einem Systemadministrator gesteuert wird. Eine System-ACL kann es dem Systemadministrator ermöglichen, alle Versuche, Zugriff auf ein Objekt zu erhalten, zu überwachen.

Weitere Informationen finden Sie in der [ACL](/windows/win32/SecAuthZ/access-control-lists) -Diskussion in der Windows SDK.

Eine Einführung zum Zugriffs Steuerungsmodell in Windows finden Sie unter [Access Control](/windows/win32/SecAuthZ/access-control) in der Windows SDK.

## <a name="requirements"></a>Anforderungen

**Header:** ATLSecurity. h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CaCl:: caccessmaskarray

Ein Array von ACCESS_MASK-Objekten.

```cpp
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Bemerkungen

Diese Typdefinition gibt den Arraytyp an, der zum Speichern der in Zugriffs Steuerungs Einträgen (ACEs) verwendeten Zugriffsrechte verwendet werden kann.

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CaCl:: caceflagarray

Ein Bytearray.

```cpp
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Bemerkungen

Diese Typdefinition gibt den Arraytyp an, der verwendet wird, um die ACE (Access Control Entry)-typspezifische Steuerungsflags zu definieren. Eine komplette Liste möglicher Flags finden Sie in der [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) Definition.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CaCl:: cacetypeer Array

Ein Bytearray.

```cpp
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Bemerkungen

Diese Typdefinition gibt den Arraytyp an, der zum Definieren der Art der ACE-Objekte (Access Control Entry) verwendet wird, z. b. ACCESS_ALLOWED_ACE_TYPE oder ACCESS_DENIED_ACE_TYPE. Eine umfassende Liste möglicher Typen finden Sie in der [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) -Definition.

## <a name="caclcacl"></a><a name="cacl"></a>CaCl:: CAcl

Der Konstruktor.

```cpp
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Ein vorhandenes `CAcl`-Objekt.

### <a name="remarks"></a>Bemerkungen

Das `CAcl` -Objekt kann optional mit einem vorhandenen `CAcl` -Objekt erstellt werden.

## <a name="caclcacl"></a><a name="dtor"></a>CaCl:: ~ CAcl

Der Destruktor.

```cpp
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor gibt alle Ressourcen frei, die vom-Objekt abgerufen wurden.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CaCl:: getacecount

Gibt die Anzahl der ACE (Access Control Entry)-Objekte zurück.

```cpp
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der ACE-Einträge im `CAcl` -Objekt zurück.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CaCl:: getaclentries

Ruft die Einträge in der Zugriffs Steuerungs Liste (Access Control List, ACL) aus dem `CAcl` -Objekt ab.

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*psids*<br/>
Ein Zeiger auf ein Array von [CSID](../../atl/reference/csid-class.md) -Objekten.

*paccessmasken*<br/>
Die Zugriffs Masken.

*pacetypes*<br/>
Die ACE-Typen (Access Control Entry, Zugriffs Steuerungs Eintrag).

*paceflags*<br/>
Die ACE-Flags.

### <a name="remarks"></a>Bemerkungen

Diese Methode füllt die Array Parameter mit den Details jedes ACE-Objekts, das im `CAcl` -Objekt enthalten ist. Verwenden Sie NULL, wenn die Details für dieses bestimmte Array nicht erforderlich sind.

Der Inhalt jedes Arrays entspricht einander, d. h., das erste Element des `CAccessMaskArray` Arrays entspricht dem ersten Element im `CSidArray` Array usw.

Weitere Informationen zu ACE-Typen und-Flags finden Sie unter [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CaCl:: getaclentry

Ruft alle Informationen zu einem Eintrag in einer Zugriffs Steuerungs Liste (Access Control List, ACL) ab.

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
Index des abzurufenden ACL-Eintrags.

*pSid*<br/>
Das [CSID](../../atl/reference/csid-class.md) -Objekt, für das der ACL-Eintrag gilt.

*pmask*<br/>
Die Maske, die Berechtigungen angibt, um Zugriff zu gewähren oder zu verweigern.

*pType*<br/>
Der ACE-Typ.

*pflags*<br/>
Die ACE-Flags.

*pobjecttype*<br/>
Der Objekttyp. Diese wird auf GUID_NULL festgelegt, wenn der Objekttyp nicht im ACE angegeben ist, oder, wenn der ACE kein Objekt-ACE ist.

*pinheritedobjecttype*<br/>
Der geerbte Objekttyp. Diese wird auf GUID_NULL festgelegt, wenn der geerbte Objekttyp nicht im ACE angegeben ist, oder, wenn der ACE kein Objekt-ACE ist.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode werden alle Informationen zu einem einzelnen ACE abgerufen, und es werden mehr Informationen bereitgestellt, als " [CaCl:: getaclentries](#getaclentries) Alone" verfügbar macht.

Weitere Informationen zu ACE-Typen und-Flags finden Sie unter [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetlength"></a><a name="getlength"></a>CaCl:: GetLength

Gibt die Länge der Zugriffs Steuerungs Liste (Access Control List, ACL) zurück.

```cpp
UINT GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die erforderliche Länge in Bytes zurück, die zum `ACL` Speichern der Struktur erforderlich ist.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CaCl:: getpacl

Gibt einen Zeiger auf eine Zugriffs Steuerungs Liste (Access Control List, ACL) zurück.

```cpp
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die `ACL` -Struktur zurück.

## <a name="caclisempty"></a><a name="isempty"></a>CaCl:: IsEmpty

Testet das `CAcl` -Objekt auf Einträge.

```cpp
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt "true" `CAcl` zurück, wenn das Objekt nicht NULL ist und keine Einträge enthält. Gibt false zurück, `CAcl` wenn das Objekt entweder NULL ist oder mindestens einen Eintrag enthält.

## <a name="caclisnull"></a><a name="isnull"></a>CaCl:: IsNull

Gibt den Status des- `CAcl` Objekts zurück.

```cpp
bool IsNull() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, `CAcl` wenn das Objekt NULL ist, andernfalls false.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CaCl:: Operator Konstanten ACL *

Wandelt ein `CAcl` -Objekt in `ACL` eine-Struktur (Zugriffs Steuerungs Liste) um.

```cpp
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt die Adresse der- `ACL` Struktur zurück.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CaCl:: Operator =

Zuweisungsoperator.

```cpp
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Der `CAcl` , der dem vorhandenen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktualisierte `CAcl` Objekt zurück.

## <a name="caclremoveace"></a><a name="removeace"></a>CaCl:: RemoveAce

Entfernt einen bestimmten ACE (Zugriffs Steuerungs Eintrag) aus dem `CAcl` -Objekt.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index für den zu entfern-ACE-Eintrag.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von "" mit "" "" "" "" " [".](../../atl/reference/catlarray-class.md#removeat)

## <a name="caclremoveaces"></a><a name="removeaces"></a>CaCl:: removeaces

Entfernt alle-ACEs (Zugriffs Steuerungs Einträge) aus der `CAcl` , die auf den angegebenen `CSid`angewendet werden.

```cpp
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parameter

*RSID*<br/>
Ein Verweis auf ein `CSid`-Objekt.

## <a name="caclsetempty"></a><a name="setempty"></a>CaCl:: * tempty

Markiert das `CAcl` -Objekt als leer.

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>Bemerkungen

`CAcl` Kann auf leer oder auf NULL festgelegt werden: die beiden Zustände sind unterschiedlich.

## <a name="caclsetnull"></a><a name="setnull"></a>CaCl:: SetNull

Markiert das `CAcl` Objekt als NULL.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Bemerkungen

`CAcl` Kann auf leer oder auf NULL festgelegt werden: die beiden Zustände sind unterschiedlich.

## <a name="see-also"></a>Weitere Informationen:

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
