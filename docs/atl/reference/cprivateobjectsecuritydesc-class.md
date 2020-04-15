---
title: CPrivateObjectSecurityDesc-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331411"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc-Klasse

Diese Klasse stellt ein privates Objekt zur Sicherheitsbeschreibung dar.

## <a name="syntax"></a>Syntax

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Der Konstruktor.|
|[CPrivateObjectSecurityDesc::'cPrivateObjectSecurityDesc](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Rufen Sie diese Methode auf, um einen Sicherheitsdeskriptor und seine Zugriffssteuerungslisten (Access Control Lists, ACLs) in ein Format zu konvertieren, das die automatische Weitergabe vereribilbarer Zugriffssteuerungseinträge (Access-Control Entries, ACEs) unterstützt.|
|[CPrivateObjectSecurityDesc::Erstellen](#create)|Rufen Sie diese Methode auf, um eine selbstrelative Sicherheitsbeschreibung für das private Objekt zuzuweisen und zu initialisieren, das vom aufrufenden Ressourcen-Manager erstellt wurde.|
|[CPrivateObjectSecurityDesc::Get](#get)|Rufen Sie diese Methode auf, um Informationen aus der Sicherheitsbeschreibung eines privaten Objekts abzurufen.|
|[CPrivateObjectSecurityDesc::Set](#set)|Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung eines privaten Objekts zu ändern.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Diese klasse, abgeleitet von [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), stellt Methoden zum Erstellen und Verwalten der Sicherheitsbeschreibung eines privaten Objekts bereit.

Eine Einführung in das Zugriffssteuerungsmodell in Windows finden Sie unter [Zugriffssteuerung](/windows/win32/SecAuthZ/access-control) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit

Rufen Sie diese Methode auf, um einen Sicherheitsdeskriptor und seine Zugriffssteuerungslisten (Access Control Lists, ACLs) in ein Format zu konvertieren, das die automatische Weitergabe vereribilbarer Zugriffssteuerungseinträge (Access-Control Entries, ACEs) unterstützt.

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
Zeiger auf ein [CSecurityDesc-Objekt,](../../atl/reference/csecuritydesc-class.md) das auf den übergeordneten Container des Objekts verweist. Wenn kein übergeordneter Container vorhanden ist, lautet dieser Parameter NULL.

*Objecttype*<br/>
Zeiger auf `GUID` eine Struktur, die den Objekttyp identifiziert, der dem aktuellen Objekt zugeordnet ist. Legen Sie *ObjectType* auf NULL fest, wenn das Objekt nicht über eine GUID verfügt.

*bIsDirectoryObject*<br/>
Gibt an, ob das neue Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass es sich bei dem neuen Objekt um einen Container handelt. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*GenericMapping*<br/>
Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) Struktur, die die Zuordnung von jedem generischen Recht auf bestimmte Rechte für das Objekt angibt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird versucht zu ermitteln, ob die ACEs in der DACL (Discretionary Access Control List) und der SystemZugriffssteuerungsliste (SACL) des aktuellen Sicherheitsdeskriptors vom übergeordneten Sicherheitsdeskriptor geerbt wurden. Es ruft die [ConvertToAutoInheritPrivateObjectSecurity-Funktion](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) auf.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Der Konstruktor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das `CPrivateObjectSecurityDesc`-Objekt.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc::'cPrivateObjectSecurityDesc

Der Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor gibt alle zugewiesenen Ressourcen frei und löscht die Sicherheitsbeschreibung des privaten Objekts.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Erstellen

Rufen Sie diese Methode auf, um eine selbstrelative Sicherheitsbeschreibung für das private Objekt zuzuweisen und zu initialisieren, das vom aufrufenden Ressourcen-Manager erstellt wurde.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parameter

*pParent*<br/>
Zeiger auf ein [CSecurityDesc-Objekt,](../../atl/reference/csecuritydesc-class.md) das auf das übergeordnete Verzeichnis verweist, in dem ein neues Objekt erstellt wird. Legen Sie null fest, wenn kein übergeordnetes Verzeichnis vorhanden ist.

*pCreator*<br/>
Zeiger auf eine Sicherheitsbeschreibung, die vom Ersteller des Objekts bereitgestellt wird. Wenn der Ersteller des Objekts keine Sicherheitsinformationen für das neue Objekt explizit übergibt, legen Sie diesen Parameter auf NULL fest.

*bIsDirectoryObject*<br/>
Gibt an, ob das neue Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass es sich bei dem neuen Objekt um einen Container handelt. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*Token*<br/>
Verweis auf das [CAccessToken-Objekt](../../atl/reference/caccesstoken-class.md) für den Clientprozess, in dessen Namen das Objekt erstellt wird.

*GenericMapping*<br/>
Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) Struktur, die die Zuordnung von jedem generischen Recht auf bestimmte Rechte für das Objekt angibt.

*Objecttype*<br/>
Zeiger auf `GUID` eine Struktur, die den Objekttyp identifiziert, der dem aktuellen Objekt zugeordnet ist. Legen Sie *ObjectType* auf NULL fest, wenn das Objekt nicht über eine GUID verfügt.

*bIsContainerObject*<br/>
Gibt an, ob das neue Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass es sich bei dem neuen Objekt um einen Container handelt. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*AutoInheritFlags*<br/>
Ein Satz von Bitflags, die steuern, wie Zugriffssteuerungseinträge (Access-Control Entries, ACEs) von *pParent*geerbt werden. Weitere Informationen finden Sie unter [CreatePrivateObjectSecurityEx.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) oder [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)auf.

Die zweite Methode ermöglicht die Angabe der Objekttyp-GUID des neuen Objekts oder die Steuerung der Vererbung von ACEs.

> [!NOTE]
> Eine selbstrelative Sicherheitsbeschreibung ist eine Sicherheitsbeschreibung, die alle sicherheitspflichtigen Informationen in einem zusammenhängenden Speicherblock speichert.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get

Rufen Sie diese Methode auf, um Informationen aus der Sicherheitsbeschreibung eines privaten Objekts abzurufen.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parameter

*Si*<br/>
Eine Gruppe von Bitflags, die die abzurufenden Teile der Sicherheitsbeschreibung angeben. Dieser Wert kann eine Kombination der [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags sein.

*pResult*<br/>
Zeiger auf ein [CSecurityDesc-Objekt,](../../atl/reference/csecuritydesc-class.md) das eine Kopie der angeforderten Informationen von der angegebenen Sicherheitsbeschreibung empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Die Sicherheitsbeschreibung ist eine Struktur und zugeordnete Daten, die die Sicherheitsinformationen für ein sicherungsfähiges Objekt enthalten.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =

Zuweisungsoperator.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CPrivateObjectSecurityDesc`-Objekt, das dem aktuellen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das `CPrivateObjectSecurityDesc` aktualisierte Objekt zurück.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set

Rufen Sie diese Methode auf, um die Sicherheitsbeschreibung eines privaten Objekts zu ändern.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Parameter

*Si*<br/>
Eine Gruppe von Bitflags, die die zu setzenden Teile des Sicherheitsdeskriptors angeben. Dieser Wert kann eine Kombination der [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags sein.

*Modifikation (Modification)*<br/>
Zeiger auf ein [CSecurityDesc-Objekt.](../../atl/reference/csecuritydesc-class.md) Die durch den *si-Parameter* angegebenen Teile dieser Sicherheitsbeschreibung werden auf den Sicherheitsdeskriptor des Objekts angewendet.

*GenericMapping*<br/>
Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) Struktur, die die Zuordnung von jedem generischen Recht auf bestimmte Rechte für das Objekt angibt.

*Token*<br/>
Verweis auf das [CAccessToken-Objekt](../../atl/reference/caccesstoken-class.md) für den Clientprozess, in dessen Namen das Objekt erstellt wird.

*AutoInheritFlags*<br/>
Ein Satz von Bitflags, die steuern, wie Zugriffssteuerungseinträge (Access-Control Entries, ACEs) von *pParent*geerbt werden. Weitere Informationen finden Sie unter [CreatePrivateObjectSecurityEx.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Die zweite Methode ermöglicht die Angabe der Objekttyp-GUID des Objekts oder das Steuern, wie ACEs vererbt werden.

## <a name="see-also"></a>Siehe auch

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc-Klasse](../../atl/reference/csecuritydesc-class.md)
