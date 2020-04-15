---
title: CSecurityAttributes-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 113bcebb7461415590156206ee7aa4c91e0e93d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330982"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes-Klasse

Diese Klasse ist ein dünner Wrapper für die Struktur der Sicherheitsattribute.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Rufen Sie diese Methode auf, `CSecurityAttributes` um die Attribute des Objekts festzulegen.|

## <a name="remarks"></a>Bemerkungen

Die `SECURITY_ATTRIBUTES` Struktur enthält eine [Sicherheitsbeschreibung,](/windows/win32/api/winnt/ns-winnt-security_descriptor) die für die Erstellung eines Objekts verwendet wird, und gibt an, ob das Handle, das durch Angeben dieser Struktur abgerufen wird, vererbbar ist.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

Der Konstruktor.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parameter

*rSecurityDescriptor*<br/>
Verweis auf den Sicherheitsdeskriptor.

*bInheritsHandle*<br/>
Gibt an, ob das zurückgegebene Handle geerbt wird, wenn ein neuer Prozess erstellt wird. Wenn dieses Element auf true festgelegt ist, erbt der neue Prozess das Handle.

## <a name="csecurityattributesset"></a><a name="set"></a>CSecurityAttributes::Set

Rufen Sie diese Methode auf, `CSecurityAttributes` um die Attribute des Objekts festzulegen.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parameter

*rSecurityDescriptor*<br/>
Verweis auf den Sicherheitsdeskriptor.

*bInheritHandle*<br/>
Gibt an, ob das zurückgegebene Handle geerbt wird, wenn ein neuer Prozess erstellt wird. Wenn dieses Element auf true festgelegt ist, erbt der neue Prozess das Handle.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Konstruktor verwendet, um das `CSecurityAttributes` Objekt zu initialisieren.

## <a name="see-also"></a>Siehe auch

[Sicherheitsbeispiel](../../overview/visual-cpp-samples.md)<br/>
[Security_attributes](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[Sicherheitsbeschreibung](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)
