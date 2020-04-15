---
title: CSid-Klasse
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330917"
---
# <a name="csid-class"></a>CSid-Klasse

Diese Klasse ist ein `SID` Wrapper für eine (Sicherheitskennungs-)Struktur.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CSid
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Ein Array von `CSid`-Objekten.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSid::CSid](#csid)|Der Konstruktor.|
|[CSid::-CSid](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSid::Kontoname](#accountname)|Gibt den Namen des Kontos zurück, das dem `CSid` Objekt zugeordnet ist.|
|[CSid::Domain](#domain)|Gibt den Namen der Domäne `CSid` zurück, die dem Objekt zugeordnet ist.|
|[CSid::EqualPrefix](#equalprefix)|Tests `SID` (Sicherheitskennung) präfixieren die Gleichheit.|
|[CSid::GetLength](#getlength)|Gibt die Länge `CSid` des Objekts zurück.|
|[CSid::GetPSID](#getpsid)|Gibt einen Zeiger `SID` auf eine Struktur zurück.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Gibt einen Zeiger `SID_IDENTIFIER_AUTHORITY` auf die Struktur zurück.|
|[CSid::GetSubAuthority](#getsubauthority)|Gibt eine angegebene Unterautorität in einer `SID` Struktur zurück.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Gibt die Anzahl der Unterautoritäten zurück.|
|[CSid::IsValid](#isvalid)|Testet `CSid` das Objekt auf Gültigkeit.|
|[CSid::LoadAccount](#loadaccount)|Aktualisiert `CSid` das Objekt mit dem Kontonamen `SID` und der Domäne oder einer vorhandenen Struktur.|
|[CSid::Sid](#sid)|Gibt die ID-Zeichenfolge zurück.|
|[CSid::SidNameUse](#sidnameuse)|Gibt eine Beschreibung des `CSid` Zustands des Objekts zurück.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator_eq)|Zuweisungsoperator.|
|[Operator const SID *](#operator_const_sid__star)|Gibt ein `CSid` Objekt auf einen `SID` Zeiger auf eine Struktur um.|

### <a name="global-operators"></a>Globale Operatoren

|||
|-|-|
|[Operator ==](#operator_eq_eq)|Testet zwei Sicherheitsdeskriptorobjekte auf Gleichheit|
|[Operator !=](#operator_neq)|Testet zwei Sicherheitsdeskriptorobjekte auf Ungleichheit|
|[Operator\<](#operator_lt)|Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.|
|[Betreiber >](#operator_gt)|Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.|
|[Operator\<=](#operator_lt__eq)|Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.|
|[Operator >=](#operator_gt__eq)|Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.|

## <a name="remarks"></a>Bemerkungen

Die `SID` Struktur ist eine Struktur variabler Länge, die verwendet wird, um Benutzer oder Gruppen eindeutig zu identifizieren.

Anwendungen sollten die `SID` Struktur nicht direkt ändern, sondern stattdessen die in dieser Wrapperklasse bereitgestellten Methoden verwenden. Siehe auch [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)und [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::Kontoname

Gibt den Namen des Kontos zurück, das dem `CSid` Objekt zugeordnet ist.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt den LPCTSTR zurück, der auf den Namen des Kontos verweist.

### <a name="remarks"></a>Bemerkungen

Diese Methode versucht, einen Namen `SID` für den angegebenen Namen (Sicherheitsbezeichner) zu finden. Ausführliche Informationen finden Sie unter [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Wenn kein Kontoname `SID` für die `AccountName` gefunden werden kann, wird eine leere Zeichenfolge zurückgegeben. Dies kann auftreten, wenn ein Netzwerktimeout verhindert, dass diese Methode den Namen findet. Sie tritt auch für Sicherheitskennungen ohne entsprechenden `SID` Kontonamen auf, z. B. für eine, die eine Anmeldesitzung identifiziert.

## <a name="csidcsid"></a><a name="csid"></a>CSid::CSid

Der Konstruktor.

```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Ein `CSid` vorhandenes `SID` Objekt oder eine (Sicherheitskennungs-)Struktur.

*IdentifierAuthority*<br/>
Die Behörde.

*nSubAuthorityCount*<br/>
Die Anzahl der Unterautoritäten.

*pszAccountName*<br/>
Der Kontoname.

*pszSystem*<br/>
Der Systemname. Diese Zeichenfolge kann der Name eines Remotecomputers sein. Wenn diese Zeichenfolge NULL ist, wird stattdessen das lokale System verwendet.

*pSid*<br/>
Ein Zeiger auf `SID` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor initialisiert `CSid` das Objekt, indem er einen internen Datenmember auf *SidTypeInvalid*festlegt oder die Einstellungen aus einem vorhandenen `CSid`, `SID`oder vorhandenen Konto kopiert.

Wenn die Initialisierung fehlschlägt, löst der Konstruktor eine [CAtlException-Klasse](../../atl/reference/catlexception-class.md)aus.

## <a name="csidcsid"></a><a name="dtor"></a>CSid::-CSid

Der Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle Ressourcen frei, die vom Objekt erworben wurden.

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray

Ein Array von [CSid-Objekten.](../../atl/reference/csid-class.md)

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Bemerkungen

Dieser typedef gibt den Arraytyp an, der zum Abrufen von Sicherheitskennungen aus einer ACL (Zugriffssteuerungsliste) verwendet werden kann. Siehe [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a>CSid::Domain

Gibt den Namen der Domäne `CSid` zurück, die dem Objekt zugeordnet ist.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt `LPCTSTR` den Hinweis auf die Domäne zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode versucht, einen Namen `SID` für den angegebenen Namen (Sicherheitsbezeichner) zu finden. Ausführliche Informationen finden Sie unter [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Wenn kein Kontoname `SID` für die `Domain` gefunden werden kann, gibt die Domäne als leere Zeichenfolge zurück. Dies kann auftreten, wenn ein Netzwerktimeout verhindert, dass diese Methode den Namen findet. Sie tritt auch für Sicherheitskennungen ohne entsprechenden `SID` Kontonamen auf, z. B. für eine, die eine Anmeldesitzung identifiziert.

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix

Tests `SID` (Sicherheitskennung) präfixieren die Gleichheit.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Die `SID` (Sicherheitskennungs-)Struktur oder `CSid` das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) im Windows SDK.

## <a name="csidgetlength"></a><a name="getlength"></a>CSid::GetLength

Gibt die Länge `CSid` des Objekts zurück.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Länge in `CSid` Bytes des Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Wenn `CSid` die Struktur ungültig ist, ist der Rückgabewert nicht definiert. Verwenden `GetLength`Sie vor dem Aufruf die [CSid::IsValid-Memberfunktion,](#isvalid) um zu überprüfen, ob dies `CSid` gültig ist.

> [!NOTE]
> Unter Debugbuilds verursacht die Funktion `CSid` einen ASSERT, wenn das Objekt ungültig ist.

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID

Gibt einen Zeiger `SID` auf eine (Sicherheitskennungs-)Struktur zurück.

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse `CSid` der zugrunde `SID` liegenden Struktur des Objekts zurück.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

Gibt einen Zeiger `SID_IDENTIFIER_AUTHORITY` auf die Struktur zurück.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, gibt `SID_IDENTIFIER_AUTHORITY` sie die Adresse der Struktur zurück. Wenn dies fehlschlägt, ist der Rückgabewert nicht definiert. Fehler kann auftreten, wenn das `CSid` Objekt ungültig ist, in diesem Fall gibt die [CSid::IsValid-Methode](#isvalid) FALSE zurück. Die `GetLastError` Funktion kann für erweiterte Fehlerinformationen aufgerufen werden.

> [!NOTE]
> Unter Debugbuilds verursacht die Funktion `CSid` einen ASSERT, wenn das Objekt ungültig ist.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority

Gibt eine angegebene Unterautorität in einer `SID` (Sicherheitskennungs-)Struktur zurück.

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parameter

*nSubAuthority*<br/>
Die Unterbehörde.

### <a name="return-value"></a>Rückgabewert

Gibt die Unterautorität zurück, auf die von *nSubAuthority* verwiesen wird. Der Subauthority-Wert ist ein relativer Bezeichner (RID).

### <a name="remarks"></a>Bemerkungen

Der Parameter *nSubAuthority* gibt einen Indexwert an, der das Arrayelement der Unterautorität identifiziert, das die Methode zurückgibt. Die Methode führt keine Validierungstests für diesen Wert durch. Eine Anwendung kann [CSid::GetSubAuthorityCount](#getsubauthoritycount) aufrufen, um den Bereich der zulässigen Werte zu ermitteln.

> [!NOTE]
> Unter Debugbuilds verursacht die Funktion `CSid` einen ASSERT, wenn das Objekt ungültig ist.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount

Gibt die Anzahl der Unterautoritäten zurück.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, ist der Rückgabewert die Unterautoritätsanzahl.

Wenn die Methode fehlschlägt, ist der Rückgabewert nicht definiert. Die Methode schlägt `CSid` fehl, wenn das Objekt ungültig ist. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

> [!NOTE]
> Unter Debugbuilds verursacht die Funktion `CSid` einen ASSERT, wenn das Objekt ungültig ist.

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid::IsValid

Testet `CSid` das Objekt auf Gültigkeit.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE `CSid` zurück, wenn das Objekt gültig ist, FALSE, wenn nicht. Es gibt keine erweiterten Fehlerinformationen für diese Methode. rufen Sie `GetLastError`nicht an.

### <a name="remarks"></a>Bemerkungen

Die `IsValid` Methode überprüft `CSid` das Objekt, indem überprüft wird, ob sich die Revisionsnummer innerhalb eines bekannten Bereichs befindet und dass die Anzahl der Unterautoritäten kleiner als das Maximum ist.

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::LoadAccount

Aktualisiert das `CSid`-Objekt, das den Kontonamen und die Domäne oder eine vorhandene SID-Struktur (Sicherheits-ID) erhalten hat.

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parameter

*pszAccountName*<br/>
Der Kontoname.

*pszSystem*<br/>
Der Systemname. Diese Zeichenfolge kann der Name eines Remotecomputers sein. Wenn diese Zeichenfolge NULL ist, wird stattdessen das lokale System verwendet.

*pSid*<br/>
Ein Zeiger auf eine [SID-Struktur.](/windows/win32/api/winnt/ns-winnt-sid)

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

### <a name="remarks"></a>Bemerkungen

`LoadAccount` versucht, eine Sicherheits-ID für den angegebenen Namen zu suchen. Weitere Informationen finden Sie unter [LookupAccountSid.](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::operator =

Zuweisungsoperator.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Der `SID` (Sicherheitsbezeichner) `CSid` oder `CSid` dem Objekt zuzuweisen.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CSid` auf das aktualisierte Objekt zurück.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::operator ==

Testet zwei Sicherheitsdeskriptorobjekte auf Gleichheit.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Die `SID` (Sicherheitskennung) oder `CSid` die auf der linken Seite des Operators ==angezeigt wird.

*rhs*<br/>
Die `SID` (Sicherheitskennung) oder `CSid` die auf der rechten Seite des Operators == angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Sicherheitsdeskriptoren gleich sind, andernfalls FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::operator !=

Testet zwei Sicherheitsdeskriptorobjekte auf Ungleichheit.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der `SID` (Sicherheitsbezeichner) oder `CSid` der auf der linken Seite des !=-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheitskennungs- oder `CSid` -bezeichner) wird auf der rechten Seite des !=-Operators angezeigt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Sicherheitsdeskriptoren nicht gleich sind, andernfalls FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::Operator&lt;

Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der `SID` (Sicherheitsbezeichner) oder `CSid` der auf der linken Seite des !=-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheitskennungs- oder `CSid` -bezeichner) wird auf der rechten Seite des !=-Operators angezeigt.

### <a name="return-value"></a>Rückgabewert

TRUE wenn *lhs* kleiner als *rhs*ist, andernfalls FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::Operator&lt;=

Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der `SID` (Sicherheitsbezeichner) oder `CSid` der auf der linken Seite des !=-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheitskennungs- oder `CSid` -bezeichner) wird auf der rechten Seite des !=-Operators angezeigt.

### <a name="return-value"></a>Rückgabewert

TRUE wenn *lhs* kleiner oder gleich *rhs*ist, andernfalls FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::Operator&gt;

Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der `SID` (Sicherheitsbezeichner) oder `CSid` der auf der linken Seite des !=-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheitskennungs- oder `CSid` -bezeichner) wird auf der rechten Seite des !=-Operators angezeigt.

### <a name="return-value"></a>Rückgabewert

TRUE wenn *lhs* größer als *rhs*ist, andernfalls FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::Operator&gt;=

Vergleicht den relativen Wert von zwei Sicherheitsdeskriptorobjekten.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Der `SID` (Sicherheitsbezeichner) oder `CSid` der auf der linken Seite des !=-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheitskennungs- oder `CSid` -bezeichner) wird auf der rechten Seite des !=-Operators angezeigt.

### <a name="return-value"></a>Rückgabewert

TRUE wenn *lhs* größer oder gleich *rhs*ist, andernfalls FALSE.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::operator const SID\*

Gibt ein `CSid` Objekt in einen `SID` Zeiger auf eine Struktur (Sicherheitskennung) um.

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt die Adresse `SID` der Struktur zurück.

## <a name="csidsid"></a><a name="sid"></a>CSid::Sid

Gibt `SID` die Struktur (Sicherheitsbezeichner) als Zeichenfolge zurück.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt `SID` die Struktur als Zeichenfolge in einem Format zurück, das für die Anzeige, Speicherung oder Übertragung geeignet ist. Entspricht [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse

Gibt eine Beschreibung des `CSid` Zustands des Objekts zurück.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert des Datenmembers zurück, der `CSid` einen Wert speichert, der den Status des Objekts beschreibt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SidTypeUser|Gibt einen `SID` Benutzer an (Sicherheitskennung).|
|SidTypeGroup|Gibt eine `SID`Gruppe an.|
|SidTypeDomain|Gibt eine `SID`Domäne an.|
|SidTypeAlias|Gibt einen `SID`Alias an.|
|SidTypeWellKnownGroup|Gibt `SID` eine für eine bekannte Gruppe an.|
|SidTypeDeletedAccount|Gibt `SID` eine für ein gelöschtes Konto an.|
|SidTypeInvalid|Gibt eine `SID`ungültige an.|
|SidTypeUnbekannt|Gibt einen `SID` unbekannten Typ an.|
|SidTypeComputer|Gibt `SID` eine für einen Computer an.|

### <a name="remarks"></a>Bemerkungen

Rufen Sie [CSid::LoadAccount](#loadaccount) auf, um das `CSid` Objekt vor dem Aufruf `SidNameUse` zu aktualisieren, um den Status zurückzugeben. `SidNameUse`ändert nicht den Status des Objekts `LookupAccountName` `LookupAccountSid`(durch Aufrufen von oder ), sondern gibt nur den aktuellen Status zurück.

## <a name="see-also"></a>Siehe auch

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)<br/>
[Operatoren](../../atl/reference/atl-operators.md)
