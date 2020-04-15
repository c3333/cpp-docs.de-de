---
title: Globale Sicherheitsfunktionen
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326036"
---
# <a name="security-global-functions"></a>Globale Sicherheitsfunktionen

Diese Funktionen unterstützen das Ändern von SID- und ACL-Objekten.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts abgerufen.|
|[AtlSetDacl](#atlsetdacl)|Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts festgelegt.|
|[AtlGetGroupSid](#atlgetgroupsid)|Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts abgerufen.|
|[AtlSetGroupSid](#atlsetgroupsid)|Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts festgelegt.|
|[AtlGetOwnerSid](#atlgetownersid)|Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts abgerufen.|
|[AtlSetOwnerSid](#atlsetownersid)|Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts festgelegt.|
|[AtlGetSacl](#atlgetsacl)|Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts abgerufen.|
|[AtlSetSacl](#atlsetsacl)|Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts festgelegt.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Mit dieser Funktion wird die Sicherheitsbeschreibung eines angegebenen Objekts abgerufen.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl

Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts abgerufen.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Handle für das Objekt, für das die Sicherheitsinformationen abgerufen werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*pDacl*<br/>
Zeiger auf ein DACL-Objekt, das die abgerufenen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *entweder hObject* oder *pDacl* ungültig ist.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>AtlSetDacl

Mit dieser Funktion werden die Informationen zur freigegebenen Zugriffssteuerungsliste (DACL, Discretionary Access Control List) eines bestimmten Objekts festgelegt.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*rDacl*<br/>
Die DACL, die die neuen Sicherheitsinformationen enthält.

*dwInheritanceFlowControl*<br/>
Die Vererbungsflusssteuerung. Dieser Wert kann 0 (Standard), PROTECTED_DACL_SECURITY_INFORMATION oder UNPROTECTED_DACL_SECURITY_INFORMATION sein.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *hObject* ungültig ist oder *wenn dwInheritanceFlowControl* nicht einer der drei zulässigen Werte ist.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid

Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts abgerufen.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, von dem Sicherheitsinformationen abgerufen werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*pSid*<br/>
Zeigen Sie `CSid` auf ein Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid

Mit dieser Funktion wird die Gruppensicherheits-ID (SID) eines Objekts festgelegt.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*rSid*<br/>
Das `CSid` Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts abgerufen.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, von dem Sicherheitsinformationen abgerufen werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*pSid*<br/>
Zeigen Sie `CSid` auf ein Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

Mit dieser Funktion wird die Sicherheits-ID (SID) des Besitzers eines Objekts festgelegt.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*rSid*<br/>
Das `CSid` Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>AtlGetSacl

Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts abgerufen.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, von dem die Sicherheitsinformationen abgerufen werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*pSacl*<br/>
Zeiger auf ein SACL-Objekt, das die abgerufenen Sicherheitsinformationen enthält.

*bRequestNeededPrivileges*<br/>
Wenn true, versucht die Funktion, die SE_SECURITY_NAME Berechtigung zu aktivieren und sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Wenn `AtlGetSacl` viele Male für viele verschiedene Objekte aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufruf der Funktion zu aktivieren, wobei *bRequestNeededPrivileges* auf false festgelegt ist.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>AtlSetSacl

Mit dieser Funktion werden die Informationen zur Systemzugriffssteuerungsliste (SACL, System Access Control List) eines bestimmten Objekts festgelegt.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Behandeln Sie das Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Typ des Objekts angibt, der durch den *hObject-Parameter* identifiziert wird.

*rSacl*<br/>
Die SACL, die die neuen Sicherheitsinformationen enthält.

*dwInheritanceFlowControl*<br/>
Die Vererbungsflusssteuerung. Dieser Wert kann 0 (Standard), PROTECTED_SACL_SECURITY_INFORMATION oder UNPROTECTED_SACL_SECURITY_INFORMATION sein.

*bRequestNeededPrivileges*<br/>
Wenn true, versucht die Funktion, die SE_SECURITY_NAME Berechtigung zu aktivieren und sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *hObject* ungültig ist oder *wenn dwInheritanceFlowControl* nicht einer der drei zulässigen Werte ist.

Wenn `AtlSetSacl` viele Male für viele verschiedene Objekte aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufruf der Funktion zu aktivieren, wobei *bRequestNeededPrivileges* auf false festgelegt ist.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor

Mit dieser Funktion wird die Sicherheitsbeschreibung eines angegebenen Objekts abgerufen.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parameter

*pszObjectName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Objekts angibt, von dem Sicherheitsinformationen abgerufen werden sollen.

*Objecttype*<br/>
Gibt einen Wert [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) aus der SE_OBJECT_TYPE-Enumeration an, der den Objekttyp angibt, der durch den Parameter *pszObjectName* identifiziert wird.

*pSecurityDescriptor*<br/>
Das Objekt, das den angeforderten Sicherheitsdeskriptor empfängt.

*requestedInfo*<br/>
Eine Reihe von [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags, die den Typ der abzurufenden Sicherheitsinformationen angeben. Dieser Parameter kann eine Kombination der folgenden Werte sein.

*bRequestNeededPrivileges*<br/>
Wenn true, versucht die Funktion, die SE_SECURITY_NAME Berechtigung zu aktivieren und sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Wenn `AtlGetSecurityDescriptor` viele Male für viele verschiedene Objekte aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufruf der Funktion zu aktivieren, wobei *bRequestNeededPrivileges* auf false festgelegt ist.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
