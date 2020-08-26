---
title: CSID-Klasse
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
ms.openlocfilehash: b6787c0e3f075935f19d51aa73bbd66da9cc0fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835596"
---
# <a name="csid-class"></a>CSID-Klasse

Diese Klasse ist ein Wrapper für eine `SID` (sicherheitsbezeichnerstruktur).

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CSid
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[CSID:: csidarray](#csidarray)|Ein Array von `CSid`-Objekten.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CSID:: CSID](#csid)|Der Konstruktor.|
|[CSID:: ~ CSID](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CSID:: Accountname](#accountname)|Gibt den Namen des Kontos zurück, das dem-Objekt zugeordnet ist `CSid` .|
|[CSID::D omain](#domain)|Gibt den Namen der Domäne zurück, die dem-Objekt zugeordnet ist `CSid` .|
|[CSID:: equalprefix](#equalprefix)|Testet `SID` (Sicherheits-ID) Präfixe auf Gleichheit.|
|[CSID:: GetLength](#getlength)|Gibt die Länge des- `CSid` Objekts zurück.|
|[CSID:: getpsid](#getpsid)|Gibt einen Zeiger auf eine- `SID` Struktur zurück.|
|[CSID:: GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Gibt einen Zeiger auf die- `SID_IDENTIFIER_AUTHORITY` Struktur zurück.|
|[CSID:: getsubauthority](#getsubauthority)|Gibt eine angegebene untergeordnete Instanz in einer- `SID` Struktur zurück.|
|[CSID:: getsubautoritycount](#getsubauthoritycount)|Gibt die Anzahl der untergeordneten Behörden zurück.|
|[CSID:: IsValid](#isvalid)|Testet das `CSid` Objekt auf Gültigkeit.|
|[CSID:: loadaccount](#loadaccount)|Aktualisiert das `CSid` -Objekt anhand des Konto namens und der Domäne oder einer vorhandenen `SID` Struktur.|
|[CSID:: sid](#sid)|Gibt die ID-Zeichenfolge zurück.|
|[CSID:: sidnameuse](#sidnameuse)|Gibt eine Beschreibung des Zustands des- `CSid` Objekts zurück.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator =](#operator_eq)|Zuweisungsoperator.|
|[Operator Konstante sid *](#operator_const_sid__star)|Wandelt ein- `CSid` Objekt in einen Zeiger auf eine- `SID` Struktur um.|

### <a name="global-operators"></a>Globale Operatoren

|Name|Beschreibung|
|-|-|
|[Operator = =](#operator_eq_eq)|Testet zwei Sicherheits deskriptorobjekte auf Gleichheit.|
|[Operator! =](#operator_neq)|Testet zwei sicherheitsbeschreibungerobjekte auf Ungleichheit.|
|[KOM \<](#operator_lt)|Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.|
|[Operator >](#operator_gt)|Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.|
|[KOM \<=](#operator_lt__eq)|Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.|
|[Operator >=](#operator_gt__eq)|Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.|

## <a name="remarks"></a>Bemerkungen

Die `SID` Struktur ist eine Struktur mit variabler Länge, die zur eindeutigen Identifizierung von Benutzern oder Gruppen verwendet wird.

Anwendungen sollten die Struktur nicht `SID` direkt ändern, sondern stattdessen die Methoden verwenden, die in dieser Wrapper Klasse bereitgestellt werden. Siehe auch [atlgetownersid](security-global-functions.md#atlgetownersid), [atlsetgroupsid](security-global-functions.md#atlsetgroupsid), [atlgetgroupsid](security-global-functions.md#atlgetgroupsid)und [atlsetownersid](security-global-functions.md#atlsetownersid).

Eine Einführung zum Zugriffs Steuerungsmodell in Windows finden Sie unter [Access Control](/windows/win32/SecAuthZ/access-control) in der Windows SDK.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="csidaccountname"></a><a name="accountname"></a> CSID:: Accountname

Gibt den Namen des Kontos zurück, das dem-Objekt zugeordnet ist `CSid` .

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt den LPCTSTR zurück, der auf den Namen des Kontos zeigt.

### <a name="remarks"></a>Bemerkungen

Diese Methode versucht, einen Namen für die angegebene (Sicherheits-ID) zu finden `SID` . Ausführliche Informationen finden Sie unter [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Wenn kein Kontoname für `SID` gefunden werden kann, wird `AccountName` eine leere Zeichenfolge zurückgegeben. Dies kann vorkommen, wenn ein Netzwerk Timeout verhindert, dass diese Methode den Namen findet. Sie tritt auch für Sicherheits-IDs ohne entsprechenden Kontonamen auf, wie z. b. einen, `SID` der eine Anmelde Sitzung identifiziert.

## <a name="csidcsid"></a><a name="csid"></a> CSID:: CSID

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
Ein vorhandenes- `CSid` Objekt oder- `SID` Struktur (Sicherheits-ID).

*Identifiziererautorität*<br/>
Die Autorität.

*nsubautoritycount*<br/>
Die Anzahl der untergeordneten Behörden.

*pszaccountname*<br/>
Der Kontoname.

*pszsystem*<br/>
Der Systemname. Diese Zeichenfolge kann der Name eines Remotecomputers sein. Wenn diese Zeichenfolge NULL ist, wird stattdessen das lokale System verwendet.

*pSid*<br/>
Ein Zeiger auf eine- `SID` Struktur.

### <a name="remarks"></a>Bemerkungen

Der-Konstruktor initialisiert das- `CSid` Objekt, legt einen internen Datenmember auf *SidTypeInvalid*fest oder kopiert die Einstellungen aus einem vorhandenen `CSid` , `SID` oder vorhandenen Konto.

Wenn die Initialisierung fehlschlägt, löst der Konstruktor eine [Klasse "Klasse](../../atl/reference/catlexception-class.md)auslösen" aus.

## <a name="csidcsid"></a><a name="dtor"></a> CSID:: ~ CSID

Der Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor gibt alle Ressourcen frei, die vom-Objekt abgerufen wurden.

## <a name="csidcsidarray"></a><a name="csidarray"></a> CSID:: csidarray

Ein Array von [CSID](../../atl/reference/csid-class.md) -Objekten.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Bemerkungen

Diese Typdefinition gibt den Arraytyp an, der zum Abrufen von Sicherheits-IDs aus einer ACL (Zugriffs Steuerungs Liste) verwendet werden kann. Siehe [CaCl:: getaclentries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a> CSID::D omain

Gibt den Namen der Domäne zurück, die dem-Objekt zugeordnet ist `CSid` .

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt den zurück `LPCTSTR` , der auf die Domäne zeigt.

### <a name="remarks"></a>Bemerkungen

Diese Methode versucht, einen Namen für die angegebene (Sicherheits-ID) zu finden `SID` . Ausführliche Informationen finden Sie unter [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Wenn kein Kontoname für `SID` gefunden werden kann, wird `Domain` die Domäne als leere Zeichenfolge zurückgegeben. Dies kann vorkommen, wenn ein Netzwerk Timeout verhindert, dass diese Methode den Namen findet. Sie tritt auch für Sicherheits-IDs ohne entsprechenden Kontonamen auf, wie z. b. einen, `SID` der eine Anmelde Sitzung identifiziert.

## <a name="csidequalprefix"></a><a name="equalprefix"></a> CSID:: equalprefix

Testet `SID` (Sicherheits-ID) Präfixe auf Gleichheit.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Die `SID` (sicherheitsbezeichnerstruktur) oder das `CSid` zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [equalprefixsid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) im Windows SDK.

## <a name="csidgetlength"></a><a name="getlength"></a> CSID:: GetLength

Gibt die Länge des- `CSid` Objekts zurück.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Länge des-Objekts in Bytes zurück `CSid` .

### <a name="remarks"></a>Bemerkungen

Wenn die `CSid` Struktur ungültig ist, ist der Rückgabewert nicht definiert. `GetLength`Verwenden Sie vor dem Aufrufen von die [CSID:: IsValid](#isvalid) -Member-Funktion, um zu überprüfen, ob `CSid` gültig ist.

> [!NOTE]
> Unter Debugbuilds führt die Funktion eine Assert-Funktion aus, wenn das `CSid` Objekt nicht gültig ist.

## <a name="csidgetpsid"></a><a name="getpsid"></a> CSID:: getpsid

Gibt einen Zeiger auf eine- `SID` Struktur (sicherheitsbezeichnerstruktur) zurück.

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse der `CSid` zugrunde liegenden-Struktur des-Objekts zurück `SID` .

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a> CSID:: GetPSID_IDENTIFIER_AUTHORITY

Gibt einen Zeiger auf die- `SID_IDENTIFIER_AUTHORITY` Struktur zurück.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ausgeführt wird, wird die Adresse der-Struktur zurückgegeben `SID_IDENTIFIER_AUTHORITY` . Wenn ein Fehler auftritt, ist der Rückgabewert nicht definiert. Wenn das `CSid` Objekt ungültig ist, kann ein Fehler auftreten. in diesem Fall gibt die [CSID:: IsValid](#isvalid) -Methode "false" zurück. Die-Funktion `GetLastError` kann für erweiterte Fehlerinformationen aufgerufen werden.

> [!NOTE]
> Unter Debugbuilds führt die Funktion eine Assert-Funktion aus, wenn das `CSid` Objekt nicht gültig ist.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a> CSID:: getsubauthority

Gibt eine angegebene untergeordnete Instanz in einer- `SID` Struktur (sicherheitsbezeichnerstruktur) zurück.

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parameter

*nsubauthority*<br/>
Die untergeordnete Autorität.

### <a name="return-value"></a>Rückgabewert

Gibt die von der *nsubauthority* referenzierte untergeordnete Autorität zurück. Der Wert der untergeordneten Autorität ist ein relativer Bezeichner (RID).

### <a name="remarks"></a>Bemerkungen

Der Parameter *nsubauthority* gibt einen Indexwert an, der das untergeordnete Array Element identifiziert, das von der Methode zurückgegeben wird. Die-Methode führt keine Validierungstests für diesen Wert aus. Eine Anwendung kann [CSID:: getsubautoritycount](#getsubauthoritycount) aufrufen, um den Bereich zulässiger Werte zu ermitteln.

> [!NOTE]
> Unter Debugbuilds führt die Funktion eine Assert-Funktion aus, wenn das `CSid` Objekt nicht gültig ist.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a> CSID:: getsubautoritycount

Gibt die Anzahl der untergeordneten Behörden zurück.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ausgeführt wird, ist der Rückgabewert die Anzahl der untergeordneten Behörden.

Wenn die Methode fehlschlägt, ist der Rückgabewert nicht definiert. Die-Methode schlägt fehl, wenn das- `CSid` Objekt ungültig ist. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

> [!NOTE]
> Unter Debugbuilds führt die Funktion eine Assert-Funktion aus, wenn das `CSid` Objekt nicht gültig ist.

## <a name="csidisvalid"></a><a name="isvalid"></a> CSID:: IsValid

Testet das `CSid` Objekt auf Gültigkeit.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das `CSid` Objekt gültig ist, andernfalls false. Es sind keine erweiterten Fehlerinformationen für diese Methode vorhanden. nicht aufzurufen `GetLastError` .

### <a name="remarks"></a>Bemerkungen

Die- `IsValid` Methode überprüft das- `CSid` Objekt, indem überprüft wird, ob die Revisionsnummer innerhalb eines bekannten Bereichs liegt und die Anzahl der untergeordneten Autoritäten kleiner ist als der Maximalwert.

## <a name="csidloadaccount"></a><a name="loadaccount"></a> CSID:: loadaccount

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

*pszaccountname*<br/>
Der Kontoname.

*pszsystem*<br/>
Der Systemname. Diese Zeichenfolge kann der Name eines Remotecomputers sein. Wenn diese Zeichenfolge NULL ist, wird stattdessen das lokale System verwendet.

*pSid*<br/>
Ein Zeiger auf eine [sid](/windows/win32/api/winnt/ns-winnt-sid) -Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

### <a name="remarks"></a>Bemerkungen

`LoadAccount` versucht, eine Sicherheits-ID für den angegebenen Namen zu suchen. Weitere Informationen finden Sie unter [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) .

## <a name="csidoperator-"></a><a name="operator_eq"></a> CSID:: Operator =

Zuweisungsoperator.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der dem-Objekt zugewiesen werden soll `CSid` .

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das aktualisierte `CSid` Objekt zurück.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a> CSID:: Operator = =

Testet zwei sicherheitsbeschreibungerobjekte auf Gleichheit.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des = =-Operators angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des = =-Operators angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Sicherheits Deskriptoren gleich sind, andernfalls false.

## <a name="csidoperator-"></a><a name="operator_neq"></a> CSID:: Operator! =

Testet zwei sicherheitsbeschreibungerobjekte auf Ungleichheit.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des Operators "! =" angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des Operators "! =" angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Sicherheits Deskriptoren nicht gleich sind, andernfalls false.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a> CSID::-Operator &lt;

Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des Operators "! =" angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des Operators "! =" angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *LHS* kleiner als *RHS*ist, andernfalls false.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a> CSID::-Operator &lt;=

Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des Operators "! =" angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des Operators "! =" angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *LHS* kleiner oder gleich *RHS*ist, andernfalls false.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a> CSID::-Operator &gt;

Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des Operators "! =" angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des Operators "! =" angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *LHS* größer als *RHS*ist, andernfalls false.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a> CSID::-Operator &gt;=

Vergleicht den relativen Wert von zwei sicherheitsbeschreibungerobjekten.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der linken Seite des Operators "! =" angezeigt wird.

*rhs*<br/>
Der `SID` (Sicherheits-ID) oder `CSid` , der auf der rechten Seite des Operators "! =" angezeigt wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *LHS* größer oder gleich *RHS*ist, andernfalls false.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a> CSID:: Operator Konstanten-sid \*

Wandelt ein- `CSid` Objekt in einen Zeiger auf eine- `SID` Struktur (sicherheitsbezeichnerstruktur) um.

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Bemerkungen

Gibt die Adresse der- `SID` Struktur zurück.

## <a name="csidsid"></a><a name="sid"></a> CSID:: sid

Gibt die- `SID` Struktur (Sicherheits-ID) als Zeichenfolge zurück.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt die `SID` Struktur als Zeichenfolge in einem Format zurück, das für die Anzeige, Speicherung oder Übertragung geeignet ist. Entspricht [convertsidto stringsid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a> CSID:: sidnameuse

Gibt eine Beschreibung des Zustands des- `CSid` Objekts zurück.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert des Datenmembers zurück, der einen Wert speichert, der den Zustand des- `CSid` Objekts beschreibt.

|Wert|Beschreibung|
|-----------|-----------------|
|SidTypeUser|Gibt einen Benutzer `SID` (Sicherheits-ID) an.|
|SidTypeGroup|Gibt eine Gruppe an `SID` .|
|SidTypeDomain|Gibt eine Domäne an `SID` .|
|Sidtypealias|Gibt einen Alias an `SID` .|
|Sidtypewellknowngroup|Gibt einen `SID` für eine bekannte Gruppe an.|
|SidTypeDeletedAccount|Gibt einen `SID` für ein gelöschtes Konto an.|
|Sidtypeingabe gültig|Gibt ein ungültiges an `SID` .|
|SidTypeUnknown|Gibt einen unbekannten `SID` Typ an.|
|Sidtypecomputer|Gibt einen `SID` für einen Computer an.|

### <a name="remarks"></a>Bemerkungen

Rufen Sie [CSID:: loadaccount](#loadaccount) auf, um das Objekt zu aktualisieren, `CSid` bevor `SidNameUse` Sie aufrufen, um seinen Status zurückzugeben. `SidNameUse` ändert den Zustand des-Objekts nicht (durch Aufrufen von `LookupAccountName` oder `LookupAccountSid` ), sondern gibt nur den aktuellen Status zurück.

## <a name="see-also"></a>Weitere Informationen

[Sicherheits Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)<br/>
[Operatoren](../../atl/reference/atl-operators.md)
