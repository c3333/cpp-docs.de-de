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
ms.openlocfilehash: 0b42fe10ef1de517677b35a9fe54d0c6a04ff748
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834491"
---
# <a name="security-global-functions"></a>Globale Sicherheitsfunktionen

Diese Funktionen bieten Unterstützung für das Ändern von sid-und ACL-Objekten.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Name|Beschreibung|
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

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a> Atlgetdacl

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

*hobject*<br/>
Handle für das-Objekt, für das die Sicherheitsinformationen abgerufen werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*pdacl*<br/>
Zeiger auf ein DACL-Objekt, das die abgerufenen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn entweder " *hobject* " oder " *pdacl* " ungültig ist.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a> Atlsetdacl

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

*hobject*<br/>
Handle für das-Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*rdacl*<br/>
Die DACL, die die neuen Sicherheitsinformationen enthält.

*dwinerbanceflowcontrol*<br/>
Die Vererbungs Fluss Steuerung. Dieser Wert kann 0 (Standard), PROTECTED_DACL_SECURITY_INFORMATION oder UNPROTECTED_DACL_SECURITY_INFORMATION sein.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn das *hobject* ungültig ist oder *dwinerbanceflowcontrol* keinem der drei zulässigen Werte entspricht.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a> Atlgetgroupsid

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

*hobject*<br/>
Handle für das-Objekt, aus dem Sicherheitsinformationen abgerufen werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*pSid*<br/>
Zeiger auf ein- `CSid` Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a> Atlsetgroupsid

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

*hobject*<br/>
Handle für das-Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*RSID*<br/>
Das-Objekt, das `CSid` die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a> Atlgetownersid

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

*hobject*<br/>
Handle für das-Objekt, aus dem Sicherheitsinformationen abgerufen werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*pSid*<br/>
Zeiger auf ein- `CSid` Objekt, das die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a> Atlseetownersid

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

*hobject*<br/>
Handle für das-Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*RSID*<br/>
Das-Objekt, das `CSid` die neuen Sicherheitsinformationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a> Atlgeout-ACL

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

*hobject*<br/>
Handle für das-Objekt, aus dem die Sicherheitsinformationen abgerufen werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*psacl*<br/>
Zeiger auf ein SACL-Objekt, das die abgerufenen Sicherheitsinformationen enthält.

*brequestneedecodprivileges*<br/>
True gibt an, dass die Funktion versucht, die SE_SECURITY_NAME Berechtigung zu aktivieren und Sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Wenn für `AtlGetSacl` viele verschiedene Objekte mehrmals aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufrufen der Funktion zu aktivieren, wobei *brequestneededprivileges* auf false festgelegt ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a> Atlanacl

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

*hobject*<br/>
Handle für das-Objekt, für das Sicherheitsinformationen festgelegt werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *hobject* -Parameter identifiziert wird.

*rsacl*<br/>
Die SACL, die die neuen Sicherheitsinformationen enthält.

*dwinerbanceflowcontrol*<br/>
Die Vererbungs Fluss Steuerung. Dieser Wert kann 0 (Standard), PROTECTED_SACL_SECURITY_INFORMATION oder UNPROTECTED_SACL_SECURITY_INFORMATION sein.

*brequestneedecodprivileges*<br/>
True gibt an, dass die Funktion versucht, die SE_SECURITY_NAME Berechtigung zu aktivieren und Sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn das *hobject* ungültig ist oder *dwinerbanceflowcontrol* keinem der drei zulässigen Werte entspricht.

Wenn für `AtlSetSacl` viele verschiedene Objekte mehrmals aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufrufen der Funktion zu aktivieren, wobei *brequestneededprivileges* auf false festgelegt ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a> Atlgetsecuritydescriptor

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

*pszobjectname*<br/>
Ein Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen des Objekts angibt, aus dem Sicherheitsinformationen abgerufen werden sollen.

*ObjectType*<br/>
Gibt einen Wert aus der [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) Enumeration an, der den Objekttyp angibt, der durch den *pszobjectname* -Parameter identifiziert wird.

*psecuritydescriptor*<br/>
Das-Objekt, das die angeforderte Sicherheits Beschreibung empfängt.

*requestedinfo*<br/>
Ein Satz von [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags, die den Typ der abzurufenden Sicherheitsinformationen angeben. Dieser Parameter kann eine Kombination der folgenden Werte sein.

*brequestneedecodprivileges*<br/>
True gibt an, dass die Funktion versucht, die SE_SECURITY_NAME Berechtigung zu aktivieren und Sie nach Abschluss wiederherzustellen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Wenn für `AtlGetSecurityDescriptor` viele verschiedene Objekte mehrmals aufgerufen werden soll, ist es effizienter, die SE_SECURITY_NAME Berechtigung einmal vor dem Aufrufen der Funktion zu aktivieren, wobei *brequestneededprivileges* auf false festgelegt ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
