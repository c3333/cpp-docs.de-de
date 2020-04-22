---
title: CTokenGroups-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: ccfa628f4a099f7e13eb09d272c72c2bdd846f37
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746379"
---
# <a name="ctokengroups-class"></a>CTokenGroups-Klasse

Diese Klasse ist ein `TOKEN_GROUPS` Wrapper für die Struktur.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CTokenGroups
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Der Konstruktor.|
|[CTokenGroups::'cTokenGroups](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenGroups::Hinzufügen](#add)|Fügt `CSid` dem `CTokenGroups` `TOKEN_GROUPS` Objekt eine oder eine vorhandene Struktur hinzu.|
|[CTokenGroups::Delete](#delete)|Löscht a `CSid` und die zugehörigen `CTokenGroups` Attribute aus dem Objekt.|
|[CTokenGroups::DeleteAll](#deleteall)|Löscht alle `CSid` Objekte und die zugehörigen Attribute aus dem `CTokenGroups` Objekt.|
|[CTokenGroups::GetCount](#getcount)|Gibt die `CSid` Anzahl der im `CTokenGroups` Objekt enthaltenen Objekte und zugeordneten Attribute zurück.|
|[CTokenGroups::GetLength](#getlength)|Gibt die Größe `CTokenGroups` des Objekts zurück.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Ruft einen Zeiger auf `TOKEN_GROUPS` die Struktur ab.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Ruft die `CSid` Objekte und Attribute `CTokenGroups` ab, die zum Objekt gehören.|
|[CTokenGroups::LookupSid](#lookupsid)|Ruft die Attribute ab, `CSid` die einem Objekt zugeordnet sind.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Gibt das `CTokenGroups` Objekt in einen `TOKEN_GROUPS` Zeiger auf die Struktur.|
|[CTokenGroups::operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Ein [Zugriffstoken](/windows/win32/SecAuthZ/access-tokens) ist ein Objekt, das den Sicherheitskontext eines Prozesses oder Threads beschreibt und jedem Benutzer zugewiesen wird, der bei einem Windows-System angemeldet ist.

Die `CTokenGroups` Klasse ist ein Wrapper für die [TOKEN_GROUPS-Struktur,](/windows/win32/api/winnt/ns-winnt-token_groups) der Informationen über die Gruppensicherheitskennungen (SIDs) in einem Zugriffstoken enthält.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Hinzufügen

Fügt `CSid` dem `CTokenGroups` `TOKEN_GROUPS` Objekt eine oder eine vorhandene Struktur hinzu.

```cpp
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Ein [CSid-Objekt.](../../atl/reference/csid-class.md)

*dwAttributes*<br/>
Die Attribute, die `CSid` dem Objekt zugeordnet werden sollen.

*rTokenGroups*<br/>
Eine [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) Struktur.

### <a name="remarks"></a>Bemerkungen

Diese Methoden fügen `CSid` dem `CTokenGroups` Objekt ein oder mehrere Objekte und die zugehörigen Attribute hinzu.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Der Konstruktor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CTokenGroups` Objekt oder [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) Struktur, `CTokenGroups` mit der das Objekt erstellt werden soll.

### <a name="remarks"></a>Bemerkungen

Das `CTokenGroups` Objekt kann optional mit `TOKEN_GROUPS` einer Struktur `CTokenGroups` oder einem zuvor definierten Objekt erstellt werden.

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups::'cTokenGroups

Der Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle zugewiesenen Ressourcen frei.

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete

Löscht a `CSid` und die zugehörigen `CTokenGroups` Attribute aus dem Objekt.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Das [CSid-Objekt,](../../atl/reference/csid-class.md) für das die Sicherheitskennung (Security Identifier, SID) und Attribute entfernt werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt true `CSid` zurück, wenn der entfernt wird, andernfalls false.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll

Löscht alle `CSid` Objekte und die zugehörigen Attribute aus dem `CTokenGroups` Objekt.

```cpp
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount

Gibt die `CSid` Anzahl der `CTokenGroups`in enthaltenen Objekte zurück.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der [CSid-Objekte](../../atl/reference/csid-class.md) und `CTokenGroups` die zugehörigen Attribute zurück, die im Objekt enthalten sind.

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength

Gibt die Größe `CTokenGroup` des Objekts zurück.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt die Gesamtgröße `CTokenGroup` des Objekts in Bytes zurück.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Ruft einen Zeiger auf `TOKEN_GROUPS` die Struktur ab.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Ruft einen Zeiger auf die [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) `CTokenGroups` Struktur ab, die zum Zugriffstokenobjekt gehört.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Ruft die `CSid` Objekte und (optional) die Attribute `CTokenGroups` ab, die zum Objekt gehören.

```cpp
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSids*<br/>
Zeiger auf ein Array von [CSid-Objekten.](../../atl/reference/csid-class.md)

*pAttributes*<br/>
Zeiger auf ein Array von DWORDs. Wenn dieser Parameter weggelassen wird oder NULL, werden die Attribute nicht abgerufen.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt alle im `CSid` `CTokenGroups` Objekt enthaltenen Objekte auf und platziert sie und (optional) die Attributflags in Arrayobjekten.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::LookupSid

Ruft die Attribute ab, `CSid` die einem Objekt zugeordnet sind.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parameter

*rSid*<br/>
Das [CSid-Objekt.](../../atl/reference/csid-class.md)

*pdwAttributes*<br/>
Zeiger auf ein DWORD, `CSid` das das Attribut des Objekts akzeptiert. Wenn nicht mehr oder NULL, wird das Attribut nicht abgerufen.

### <a name="return-value"></a>Rückgabewert

Gibt true `CSid` zurück, wenn der gefunden wird, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Das Festlegen von *pdwAttributes* auf NULL bietet `CSid` eine Möglichkeit, die Existenz des attributs zu bestätigen. Beachten Sie, dass diese Methode nicht zum Überprüfen von Zugriffsrechten verwendet werden sollte. Anwendungen sollten stattdessen die [CAccessToken::CheckTokenMembership-Methode](../../atl/reference/caccesstoken-class.md#checktokenmembership) verwenden.

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::operator =

Zuweisungsoperator.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CTokenGroups` Objekt oder [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) Struktur, die dem `CTokenGroups` Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das `CTokenGroups` aktualisierte Objekt zurück.

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *

Gibt einen Wert auf einen `TOKEN_GROUPS` Zeiger auf die Struktur um.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Wert auf einen [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) Zeiger auf die TOKEN_GROUPS-Struktur.

## <a name="see-also"></a>Weitere Informationen

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[CSid-Klasse](../../atl/reference/csid-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
