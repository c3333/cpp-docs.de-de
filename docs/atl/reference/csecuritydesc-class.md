---
title: CSecurityDesc-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330969"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc-Klasse

Diese Klasse ist ein `SECURITY_DESCRIPTOR` Wrapper für die Struktur.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CSecurityDesc
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Der Konstruktor.|
|[CSecurityDesc::'CSecurityDesc](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Konvertiert einen Sicherheitsdeskriptor im Zeichenfolgenformat in einen gültigen, funktionalen Sicherheitsdeskriptor.|
|[CSecurityDesc::GetControl](#getcontrol)|Ruft Steuerelementinformationen aus der Sicherheitsbeschreibung ab.|
|[CSecurityDesc::GetDacl](#getdacl)|Ruft DACL-Informationen (Discretionary Access Control List) aus der Sicherheitsbeschreibung ab.|
|[CSecurityDesc::GetGroup](#getgroup)|Ruft die primären Gruppeninformationen aus der Sicherheitsbeschreibung ab.|
|[CSecurityDesc::Besitzer abrufen](#getowner)|Ruft Besitzer-Informaton aus der Sicherheitsbeschreibung ab.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Gibt einen Zeiger `SECURITY_DESCRIPTOR` auf die Struktur zurück.|
|[CSecurityDesc::GetSacl](#getsacl)|Ruft SACL-Informationen (System Access-Control List) aus der Sicherheitsbeschreibung ab.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Bestimmt, ob die DACL für die Unterstützung der automatischen Weitergabe konfiguriert ist.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Bestimmt, ob der Sicherheitsdeskriptor mit einer Standard-DACL konfiguriert ist.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Bestimmt, ob der Sicherheitsdeskriptor eine DACL enthält.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Bestimmt, ob die DACL konfiguriert ist, um Änderungen zu verhindern.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Bestimmt, ob die Sicherheitskennung (Security Identifier, SID) des Sicherheitsdeskriptors standardmäßig festgelegt wurde.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Bestimmt, ob die Besitzer-SID des Sicherheitsdeskriptors standardmäßig festgelegt wurde.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Bestimmt, ob die SACL für die Unterstützung der automatischen Weitergabe konfiguriert ist.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Bestimmt, ob der Sicherheitsdeskriptor mit einer Standard-SACL konfiguriert ist.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Bestimmt, ob der Sicherheitsdeskriptor eine SACL enthält.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Bestimmt, ob die SACL so konfiguriert ist, dass Änderungen verhindert werden.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Bestimmt, ob der Sicherheitsdeskriptor im selbstrelativen Format ist.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung in das absolute Format zu konvertieren.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung in ein selbstrelatives Format zu konvertieren.|
|[CSecurityDesc::SetControl](#setcontrol)|Legt die Steuerungsbits einer Sicherheitsbeschreibung fest.|
|[CSecurityDesc::SetDacl](#setdacl)|Legt Informationen in einer DACL fest. Wenn eine DACL bereits in der Sicherheitsbeschreibung vorhanden ist, wird sie ersetzt.|
|[CSecurityDesc::SetGroup](#setgroup)|Legt die primären Gruppeninformationen eines absoluten Formatsicherheitsdeskriptors fest und ersetzt alle bereits vorhandenen primären Gruppeninformationen.|
|[CSecurityDesc::SetOwner](#setowner)|Legt die Besitzerinformationen einer absoluten Sicherheitsbeschreibung für das Format fest und ersetzt alle bereits vorhandenen Besitzerinformationen.|
|[CSecurityDesc::SetSacl](#setsacl)|Legt Informationen in einer SACL fest. Wenn eine SACL bereits in der Sicherheitsbeschreibung vorhanden ist, wird sie ersetzt.|
|[CSecurityDesc::ToString](#tostring)|Konvertiert einen Sicherheitsdeskriptor in ein Zeichenfolgenformat.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Gibt einen Zeiger `SECURITY_DESCRIPTOR` auf die Struktur zurück.|
|[CSecurityDesc::operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Die `SECURITY_DESCRIPTOR` Struktur enthält die Sicherheitsinformationen, die einem Objekt zugeordnet sind. Anwendungen verwenden diese Struktur, um den Sicherheitsstatus eines Objekts festzulegen und abzufragen. Siehe auch [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Anwendungen sollten die `SECURITY_DESCRIPTOR` Struktur nicht direkt ändern und stattdessen die bereitgestellten Klassenmethoden verwenden.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Der Konstruktor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CSecurityDesc` Objekt `SECURITY_DESCRIPTOR` oder die Struktur, das dem neuen `CSecurityDesc` Objekt zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Das `CSecurityDesc` Objekt kann optional mit `SECURITY_DESCRIPTOR` einer Struktur `CSecurityDesc` oder einem zuvor definierten Objekt erstellt werden.

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc::'CSecurityDesc

Der Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle zugewiesenen Ressourcen frei.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::FromString

Konvertiert einen Sicherheitsdeskriptor im Zeichenfolgenformat in einen gültigen, funktionalen Sicherheitsdeskriptor.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parameter

*Pstr*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den zu konvertierenden [Sicherheitsdeskriptor im Zeichenfolgenformat](/windows/win32/SecAuthZ/security-descriptor-string-format) enthält.

### <a name="return-value"></a>Rückgabewert

Kehrt auf Erfolg zurück. Löst eine Ausnahme bei einem Fehler aus.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge kann mit [CSecurityDesc::ToString](#tostring)erstellt werden. Das Konvertieren der Sicherheitsbeschreibung in eine Zeichenfolge erleichtert das Speichern und Übertragen.

Diese Methode ruft [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)auf.

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::GetControl

Ruft Steuerelementinformationen aus der Sicherheitsbeschreibung ab.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parameter

*psdc*<br/>
Zeiger auf `SECURITY_DESCRIPTOR_CONTROL` eine Struktur, die die Steuerelementinformationen des Sicherheitsdeskriptors empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, false, wenn sie fehlschlägt.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)auf.

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl

Ruft DACL-Informationen (Discretionary Access Control List) aus der Sicherheitsbeschreibung ab.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pDacl*<br/>
Zeigen Sie `CDacl` auf eine Struktur, in der eine Kopie der DACL des Sicherheitsdeskriptors gespeichert werden soll. Wenn eine diskretionäre ACL vorhanden ist, legt die Methode *pDacl* auf die Adresse der diskretionären ACL des Sicherheitsdeskriptors fest. Wenn keine diskretionäre ACL vorhanden ist, wird kein Wert gespeichert.

*pbPresent*<br/>
Zeiger auf einen Wert, der das Vorhandensein einer diskretionären ACL in der angegebenen Sicherheitsbeschreibung angibt. Wenn der Sicherheitsdeskriptor eine diskretionäre ACL enthält, wird dieser Parameter auf true festgelegt. Wenn die Sicherheitsbeschreibung keine diskretionäre ACL enthält, wird dieser Parameter auf false festgelegt.

*pbDefaulted*<br/>
Zeiger auf ein Flag, das auf den `SECURITY_DESCRIPTOR_CONTROL` Wert des SE_DACL_DEFAULTED-Flags in der Struktur festgelegt ist, wenn eine diskretionäre ACL für die Sicherheitsbeschreibung vorhanden ist. Wenn dieses Flag wahr ist, wurde die diskretionäre ACL von einem Standardmechanismus abgerufen. wenn false, wurde die diskretionäre ACL explizit von einem Benutzer angegeben.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, false, wenn sie fehlschlägt.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::GetGroup

Ruft die primären Gruppeninformationen aus der Sicherheitsbeschreibung ab.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf einen [CSid](../../atl/reference/csid-class.md) (Sicherheitsbezeichner), der eine Kopie der im CDacl gespeicherten Gruppe empfängt.

*pbDefaulted*<br/>
Zeiger auf ein Flag, das auf den `SECURITY_DESCRIPTOR_CONTROL` Wert des SE_GROUP_DEFAULTED-Flags in der Struktur festgelegt ist, wenn die Methode zurückkehrt.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, false, wenn sie fehlschlägt.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::Besitzer abrufen

Ruft Besitzer-Informaton aus der Sicherheitsbeschreibung ab.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSid*<br/>
Zeiger auf einen [CSid](../../atl/reference/csid-class.md) (Sicherheitsbezeichner), der eine Kopie der im CDacl gespeicherten Gruppe empfängt.

*pbDefaulted*<br/>
Zeiger auf ein Flag, das auf den `SECURITY_DESCRIPTOR_CONTROL` Wert des SE_OWNER_DEFAULTED-Flags in der Struktur festgelegt ist, wenn die Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, false, wenn sie fehlschlägt.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Gibt einen Zeiger `SECURITY_DESCRIPTOR` auf die Struktur zurück.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die [SECURITY_DESCRIPTOR-Struktur](/windows/win32/api/winnt/ns-winnt-security_descriptor) zurück.

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl

Ruft SACL-Informationen (System Access-Control List) aus der Sicherheitsbeschreibung ab.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parameter

*pSacl*<br/>
Zeigen Sie `CSacl` auf eine Struktur, in der eine Kopie der Sicherheitsbeschreibungs-SACL gespeichert werden soll. Wenn eine System-ACL vorhanden ist, legt die Methode *pSacl* auf die Adresse der System-ACL des Sicherheitsdeskriptors fest. Wenn keine System-ACL vorhanden ist, wird kein Wert gespeichert.

*pbPresent*<br/>
Zeiger auf ein Flag, das die Methode festlegt, um das Vorhandensein einer System-ACL in der angegebenen Sicherheitsbeschreibung anzuzeigen. Wenn der Sicherheitsdeskriptor eine System-ACL enthält, wird dieser Parameter auf true festgelegt. Wenn die Sicherheitsbeschreibung keine System-ACL enthält, wird dieser Parameter auf false festgelegt.

*pbDefaulted*<br/>
Zeiger auf ein Flag, das auf den `SECURITY_DESCRIPTOR_CONTROL` Wert des SE_SACL_DEFAULTED-Flags in der Struktur festgelegt ist, wenn eine System-ACL für die Sicherheitsbeschreibung vorhanden ist.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, false, wenn sie fehlschlägt.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Bestimmt, ob die DACL (Discretionary Access Control List) für die Unterstützung der automatischen Weitergabe konfiguriert ist.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine DACL enthält, die eingerichtet wurde, um die automatische Weitergabe vererbbarer Zugriffssteuerungseinträge (Access-Control Entries, ACEs) auf vorhandene untergeordnete Objekte zu unterstützen. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Das System legt dieses Bit fest, wenn es den automatischen Vererbungsalgorithmus für das Objekt und seine vorhandenen untergeordneten Objekte ausführt.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Bestimmt, ob der Sicherheitsdeskriptor mit einer standardmäßigen DACL (Discretionary Access Control List) konfiguriert ist.

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine Standard-DACL enthält, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Dieses Flag kann sich auf die Behandlung der DACL durch das System in Bezug auf die ACE-Vererbung (Access-Control Entry) auswirken. Wenn z. B. der Ersteller eines Objekts keine DACL angibt, empfängt das Objekt die Standard-DACL vom Zugriffstoken des Erstellers. Das System ignoriert dieses Flag, wenn das SE_DACL_PRESENT-Flag nicht festgelegt ist.

Dieses Flag wird verwendet, um zu bestimmen, wie die endgültige DACL für das Objekt berechnet werden soll, und nicht physisch in der Sicherheitsbeschreibungssteuerung des sicherungsfähigen Objekts gespeichert wird.

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetDacl-Methode.](#setdacl)

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Bestimmt, ob der Sicherheitsdeskriptor eine DACL (Discretionary Access Control List, DACL) enthält.

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine DACL enthält, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn dieses Flag nicht festgelegt ist oder wenn dieses Flag gesetzt ist und die DACL NULL ist, ermöglicht die Sicherheitsbeschreibung allen Den vollen Zugriff.

Dieses Flag wird verwendet, um die von einem Aufrufer angegebenen Sicherheitsinformationen zu enthalten, bis der Sicherheitsdeskriptor einem sicherungsfähigen Objekt zugeordnet ist. Sobald die Sicherheitsbeschreibung einem sicherungsfähigen Objekt zugeordnet ist, wird das SE_DACL_PRESENT-Flag immer im Steuerelement der Sicherheitsbeschreibung festgelegt.

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetDacl-Methode.](#setdacl)

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected

Bestimmt, ob die DACL (Discretionary Access Control List) konfiguriert ist, um Änderungen zu verhindern.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die DACL so konfiguriert ist, dass verhindert wird, dass die Sicherheitsbeschreibung durch vererbbare Zugriffssteuerungseinträge (Access-Control Entries, ACEs) geändert wird. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetDacl-Methode.](#setdacl)

Diese Methode unterstützt die automatische Verbreitung vererbbarer ACEs.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Bestimmt, ob die Sicherheitskennung (Security Identifier, SID) des Sicherheitsdeskriptors standardmäßig festgelegt wurde.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn ein Standardmechanismus anstelle des ursprünglichen Anbieters der Sicherheitsbeschreibung die Gruppen-SID des Sicherheitsdeskriptors bereitgestellt hat. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetGroup-Methode.](#setgroup)

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Bestimmt, ob die Sicherheitskennung (SID) des Sicherheitsdeskriptors standardmäßig festgelegt wurde.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn ein Standardmechanismus anstelle des ursprünglichen Anbieters der Sicherheitsbeschreibung die Besitzer-SID des Sicherheitsdeskriptors bereitgestellt hat. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetOwner-Methode.](#setowner)

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Bestimmt, ob die Systemzugriffssteuerungsliste (SACL) für die Unterstützung der automatischen Weitergabe konfiguriert ist.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine SACL enthält, die eingerichtet wurde, um die automatische Weitergabe vererbbarer Zugriffssteuerungseinträge (Access-Control Entries, ACEs) auf vorhandene untergeordnete Objekte zu unterstützen. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Das System legt dieses Bit fest, wenn es den automatischen Vererbungsalgorithmus für das Objekt und seine vorhandenen untergeordneten Objekte ausführt.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Bestimmt, ob der Sicherheitsdeskriptor mit einer Standardsystemzugriffssteuerungsliste (SACL) konfiguriert ist.

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine Standard-SACL enthält, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Dieses Flag kann sich auf die Behandlung der SACL durch das System in Bezug auf die ACE-Vererbung (Access-Control Entry) auswirken. Das System ignoriert dieses Flag, wenn das SE_SACL_PRESENT-Flag nicht festgelegt ist.

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetSacl-Methode.](#setsacl)

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Bestimmt, ob der Sicherheitsdeskriptor eine Systemzugriffssteuerungsliste (SACL) enthält.

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor eine SACL enthält, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetSacl-Methode.](#setsacl)

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected

Bestimmt, ob die Systemzugriffssteuerungsliste (SACL) konfiguriert ist, um Änderungen zu verhindern.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die SACL so konfiguriert ist, dass verhindert wird, dass die Sicherheitsbeschreibung durch vererbbare Zugriffssteuerungseinträge (Access-Control Entries, ACEs) geändert wird. Andernfalls wird False zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Um dieses Flag festzulegen, verwenden Sie die [CSecurityDesc::SetSacl-Methode.](#setsacl)

Diese Methode unterstützt die automatische Verbreitung vererbbarer ACEs.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Bestimmt, ob der Sicherheitsdeskriptor im selbstrelativen Format ist.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Sicherheitsdeskriptor im selbstrelativen Format mit allen Sicherheitsinformationen in einem zusammenhängenden Speicherblock ist. Gibt false zurück, wenn der Sicherheitsdeskriptor im absoluten Format ist. Weitere Informationen finden Sie unter [Absolute und Selbstrelative Sicherheitsbeschreibungen](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung in das absolute Format zu konvertieren.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein Sicherheitsdeskriptor im absoluten Format enthält Zeiger auf die darin enthaltenen Informationen und nicht auf die Informationen selbst. Ein Sicherheitsdeskriptor im selbstrelativen Format enthält die Informationen in einem zusammenhängenden Speicherblock. In einer selbstrelativen Sicherheitsbeschreibung `SECURITY_DESCRIPTOR` startet eine Struktur immer die Informationen, aber die anderen Komponenten des Sicherheitsdeskriptors können der Struktur in beliebiger Reihenfolge folgen. Anstatt Speicheradressen zu verwenden, werden die Komponenten der selbstrelativen Sicherheitsbeschreibung durch Offsets vom Anfang der Sicherheitsbeschreibung identifiziert. Dieses Format ist nützlich, wenn ein Sicherheitsdeskriptor auf einem Datenträger gespeichert oder über ein Kommunikationsprotokoll übertragen werden muss. Weitere Informationen finden Sie unter [Absolute und Selbstrelative Sicherheitsbeschreibungen](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung in ein selbstrelatives Format zu konvertieren.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Methode erfolgreich ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein Sicherheitsdeskriptor im absoluten Format enthält Zeiger auf die darin enthaltenen Informationen, anstatt die Informationen selbst zu enthalten. Ein Sicherheitsdeskriptor im selbstrelativen Format enthält die Informationen in einem zusammenhängenden Speicherblock. In einer selbstrelativen Sicherheitsbeschreibung `SECURITY_DESCRIPTOR` startet eine Struktur immer die Informationen, aber die anderen Komponenten des Sicherheitsdeskriptors können der Struktur in beliebiger Reihenfolge folgen. Anstatt Speicheradressen zu verwenden, werden die Komponenten der Sicherheitsbeschreibung durch Offsets vom Anfang der Sicherheitsbeschreibung identifiziert. Dieses Format ist nützlich, wenn ein Sicherheitsdeskriptor auf einem Datenträger gespeichert oder über ein Kommunikationsprotokoll übertragen werden muss. Weitere Informationen finden Sie unter [Absolute und Selbstrelative Sicherheitsbeschreibungen](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::operator =

Zuweisungsoperator.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Die `SECURITY_DESCRIPTOR` Struktur `CSecurityDesc` oder das `CSecurityDesc` Objekt, die dem Objekt zugewiesen werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt das `CSecurityDesc` aktualisierte Objekt zurück.

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *

Gibt einen Wert auf einen `SECURITY_DESCRIPTOR` Zeiger auf die Struktur um.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::SetControl

Legt die Steuerungsbits einer Sicherheitsbeschreibung fest.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parameter

*ControlBitsOfInterest*<br/>
Eine SECURITY_DESCRIPTOR_CONTROL-Maske, die die festzulegenden Steuerungsbits angibt. Eine Liste der Flags, die festgelegt werden können, finden Sie unter [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Eine SECURITY_DESCRIPTOR_CONTROL Maske, die die neuen Werte für die von der *ControlBitsOfInterest-Maske* angegebenen Steuerelementbits angibt. Dieser Parameter kann eine Kombination der Flags sein, die für den *Parameter ControlBitsOfInterest* aufgeführt sind.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)auf.

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl

Legt Informationen in einer DACL (Discretionary Access Control List) fest. Wenn eine DACL bereits in der Sicherheitsbeschreibung vorhanden ist, wird sie ersetzt.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parameter

*Dacl*<br/>
Verweis auf `CDacl` ein Objekt, das die DACL für die Sicherheitsbeschreibung angibt. Dieser Parameter darf nicht NULL sein. Um eine NULL-DACL in der Sicherheitsbeschreibung festzulegen, sollte die erste Form der Methode verwendet werden, wobei *bPresent* auf false gesetzt ist.

*bVorhanden*<br/>
Gibt ein Flag an, das das Vorhandensein einer DACL im Sicherheitsdeskriptor angibt. Wenn dieser Parameter true ist, legt die `SECURITY_DESCRIPTOR_CONTROL` Methode das SE_DACL_PRESENT-Flag in der Struktur fest und verwendet die Werte in den Parametern *Dacl* und *bDefaulted.* Wenn sie false ist, löscht die Methode das SE_DACL_PRESENT-Flag, und *bDefaulted* wird ignoriert.

*bDefaulted*<br/>
Gibt ein Flag an, das die Quelle der DACL angibt. Wenn dieses Flag wahr ist, wurde die DACL von einem Standardmechanismus abgerufen. Wenn false, wurde die DACL explizit von einem Benutzer angegeben. Die Methode speichert diesen Wert im `SECURITY_DESCRIPTOR_CONTROL` SE_DACL_DEFAULTED-Flag der Struktur. Wenn dieser Parameter nicht angegeben ist, wird das SE_DACL_DEFAULTED-Flag gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Es gibt einen wichtigen Unterschied zwischen einer leeren und einer nicht vorhandenen DACL. Wenn eine DACL leer ist, enthält sie keine Zugriffssteuerungseinträge, und es wurden keine Zugriffsrechte explizit gewährt. Daher wird der Zugriff auf das Objekt implizit verweigert. Wenn ein Objekt hingegen keine DACL hat, wird dem Objekt kein Schutz zugewiesen, und jede Zugriffsanforderung wird gewährt.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup

Legt die primären Gruppeninformationen eines absoluten Formatsicherheitsdeskriptors fest und ersetzt alle bereits vorhandenen primären Gruppeninformationen.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parameter

*Sid*<br/>
Verweis auf ein [CSid-Objekt](../../atl/reference/csid-class.md) für die neue primäre Gruppe des Sicherheitsdeskriptors. Dieser Parameter darf nicht NULL sein. Ein Sicherheitsdeskriptor kann als nicht über eine DACL oder Eine SACL gekennzeichnet werden, aber er muss eine Gruppe und einen Besitzer haben, auch wenn es sich um die NULL-SID handelt (eine integrierte SID mit einer besonderen Bedeutung).

*bDefaulted*<br/>
Gibt an, ob die primären Gruppeninformationen von einem Standardmechanismus abgeleitet wurden. Wenn dieser Wert true ist, handelt es sich um Standardinformationen, `SECURITY_DESCRIPTOR_CONTROL` und die Methode speichert diesen Wert als SE_GROUP_DEFAULTED-Flag in der Struktur. Wenn dieser Parameter Null ist, wird das SE_GROUP_DEFAULTED-Flag gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

Legt die Besitzerinformationen eines absoluten Sicherheitsdeskriptors für das Format fest. Es ersetzt alle bereits vorhandenen Besitzerinformationen.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parameter

*Sid*<br/>
Das [CSid-Objekt](../../atl/reference/csid-class.md) für den neuen primären Besitzer des Sicherheitsdeskriptors. Dieser Parameter darf nicht NULL sein.

*bDefaulted*<br/>
Gibt an, ob die Besitzerinformationen von einem Standardmechanismus abgeleitet werden. Wenn dieser Wert wahr ist, handelt es sich um Standardinformationen. Die Methode speichert diesen Wert als `SECURITY_DESCRIPTOR_CONTROL` SE_OWNER_DEFAULTED-Flag in der Struktur. Wenn dieser Parameter Null ist, wird das SE_OWNER_DEFAULTED-Flag gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl

Legt Informationen in einer Systemzugriffssteuerungsliste (SACL) fest. Wenn eine SACL bereits in der Sicherheitsbeschreibung vorhanden ist, wird sie ersetzt.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parameter

*Sacl*<br/>
Zeiger auf `CSacl` ein Objekt, das die SACL für die Sicherheitsbeschreibung angibt. Dieser Parameter darf nicht NULL sein und muss ein CSacl-Objekt sein. Im Gegensatz zu DACLs gibt es keinen Unterschied zwischen NULL und einer leeren SACL, da SACL-Objekte keine Zugriffsrechte angeben, sondern nur Überwachungsinformationen.

*bDefaulted*<br/>
Gibt ein Flag an, das die Quelle der SACL angibt. Wenn dieses Flag wahr ist, wurde die SACL von einem Standardmechanismus abgerufen. Wenn false, wurde die SACL explizit von einem Benutzer angegeben. Die Methode speichert diesen Wert im `SECURITY_DESCRIPTOR_CONTROL` SE_SACL_DEFAULTED-Flag der Struktur. Wenn dieser Parameter nicht angegeben ist, wird das SE_SACL_DEFAULTED-Flag gelöscht.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

## <a name="csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString

Konvertiert einen Sicherheitsdeskriptor in ein Zeichenfolgenformat.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parameter

*Pstr*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den [Sicherheitsdeskriptor im Zeichenfolgenformat](/windows/win32/SecAuthZ/security-descriptor-string-format)empfängt.

*Si*<br/>
Gibt eine Kombination aus SECURITY_INFORMATION Bitflags an, um die Komponenten des Sicherheitsdeskriptors anzugeben, die in die Ausgabezeichenfolge eingeschlossen werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Sobald der Sicherheitsdeskriptor im Zeichenfolgenformat ist, kann er leichter gespeichert oder übertragen werden. Verwenden `CSecurityDesc::FromString` Sie die Methode, um die Zeichenfolge wieder in eine Sicherheitsbeschreibung zu konvertieren.

Der *si-Parameter* kann die folgenden SECURITY_INFORMATION Flags enthalten:

|Wert|Bedeutung|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Schließen Sie den Besitzer ein.|
|GROUP_SECURITY_INFORMATION|Schließen Sie die primäre Gruppe ein.|
|DACL_SECURITY_INFORMATION|Schließen Sie die DACL ein.|
|SACL_SECURITY_INFORMATION|Schließen Sie die SACL ein.|

Wenn die DACL NULL ist und das SE_DACL_PRESENT-Steuerelementbit im Eingabesicherheitsdeskriptor festgelegt ist, schlägt die Methode fehl.

Wenn die DACL NULL ist und das SE_DACL_PRESENT-Steuerelementbit nicht im Eingabesicherheitsdeskriptor festgelegt ist, verfügt die resultierende Sicherheitsbeschreibungszeichenfolge nicht über eine D:-Komponente. Weitere Informationen finden Sie unter [Security Descriptor String Format.](/windows/win32/SecAuthZ/security-descriptor-string-format)

Diese Methode ruft [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)auf.

## <a name="see-also"></a>Siehe auch

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
