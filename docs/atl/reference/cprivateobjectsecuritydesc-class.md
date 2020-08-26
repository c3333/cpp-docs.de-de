---
title: Cprivateobjectsecuritydesc-Klasse
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
ms.openlocfilehash: f62d289418280a05f390bf9cdec23ea30632aed2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833503"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Cprivateobjectsecuritydesc-Klasse

Diese Klasse stellt ein Sicherheits beschreibungerobjekt für private Objekte dar.

## <a name="syntax"></a>Syntax

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Cprivateobjectsecuritydesc:: cprivateobjectsecuritydesc](#cprivateobjectsecuritydesc)|Der Konstruktor.|
|[Cprivateobjectsecuritydesc:: ~ cprivateobjectsecuritydesc](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cprivateobjectsecuritydesc:: convertdeautoerben](#converttoautoinherit)|Mit dieser Methode können Sie eine Sicherheits Beschreibung und ihre Zugriffs Steuerungs Listen (Access Control Lists, ACLs) in ein Format konvertieren, das die Automatische Propagierung von vererbbaren Zugriffs Steuerungs Einträgen (ACEs) unterstützt.|
|[Cprivateobjectsecuritydesc:: Create](#create)|Rufen Sie diese Methode auf, um eine selbst relative Sicherheits Beschreibung für das vom aufrufenden Ressourcen-Manager erstellte private Objekt zuzuordnen und zu initialisieren.|
|[Cprivateobjectsecuritydesc:: Get](#get)|Rufen Sie diese Methode auf, um Informationen aus der Sicherheits Beschreibung eines privaten Objekts abzurufen.|
|[Cprivateobjectsecuritydesc:: Set](#set)|Mit dieser Methode können Sie die Sicherheits Beschreibung eines privaten Objekts ändern.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[Operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

Diese von [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)abgeleitete Klasse stellt Methoden zum Erstellen und Verwalten der Sicherheits Beschreibung eines privaten Objekts bereit.

Eine Einführung zum Zugriffs Steuerungsmodell in Windows finden Sie unter [Access Control](/windows/win32/SecAuthZ/access-control) in der Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLSecurity. h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a> Cprivateobjectsecuritydesc:: convertdeautoerben

Mit dieser Methode können Sie eine Sicherheits Beschreibung und ihre Zugriffs Steuerungs Listen (Access Control Lists, ACLs) in ein Format konvertieren, das die Automatische Propagierung von vererbbaren Zugriffs Steuerungs Einträgen (ACEs) unterstützt.

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parameter

*pparent*<br/>
Zeiger auf ein [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) -Objekt, das auf den übergeordneten Container des-Objekts verweist. Wenn kein übergeordneter Container vorhanden ist, ist dieser Parameter NULL.

*ObjectType*<br/>
Ein Zeiger auf eine- `GUID` Struktur, die den Typ des Objekts identifiziert, das dem aktuellen-Objekt zugeordnet ist. Legen Sie *ObjectType* auf NULL fest, wenn das Objekt nicht über eine GUID verfügt.

*bisdirectoryobject*<br/>
Gibt an, ob das neue-Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass das neue Objekt ein Container ist. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*GenericMapping*<br/>
Ein Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) -Struktur, die die Zuordnung von jedem generischen Recht zu bestimmten Rechten für das-Objekt angibt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Diese Methode versucht zu bestimmen, ob die ACEs in der freigegebenen Zugriffs Steuerungs Liste (DACL) und der System Zugriffs Steuerungs Liste (SACL) der aktuellen Sicherheits Beschreibung von der übergeordneten Sicherheits Beschreibung geerbt wurden. Sie ruft die [ConvertTo autovererprivateobjectsecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) -Funktion auf.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a> Cprivateobjectsecuritydesc:: cprivateobjectsecuritydesc

Der Konstruktor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das `CPrivateObjectSecurityDesc`-Objekt.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a> Cprivateobjectsecuritydesc:: ~ cprivateobjectsecuritydesc

Der Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor gibt alle zugeordneten Ressourcen frei und löscht die Sicherheits Beschreibung des privaten Objekts.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a> Cprivateobjectsecuritydesc:: Create

Rufen Sie diese Methode auf, um eine selbst relative Sicherheits Beschreibung für das vom aufrufenden Ressourcen-Manager erstellte private Objekt zuzuordnen und zu initialisieren.

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

*pparent*<br/>
Zeiger auf ein [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) -Objekt, das auf das übergeordnete Verzeichnis verweist, in dem ein neues Objekt erstellt wird. Auf NULL festgelegt, wenn kein übergeordnetes Verzeichnis vorhanden ist.

*pcreator*<br/>
Zeiger auf eine Sicherheits Beschreibung, die vom Ersteller des-Objekts bereitgestellt wird. Wenn der Ersteller des Objekts die Sicherheitsinformationen für das neue Objekt nicht explizit übergibt, legen Sie diesen Parameter auf NULL fest.

*bisdirectoryobject*<br/>
Gibt an, ob das neue-Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass das neue Objekt ein Container ist. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*Token*<br/>
Verweis auf das [CAccessToken](../../atl/reference/caccesstoken-class.md) -Objekt für den Client Prozess, in dessen Auftrag das Objekt erstellt wird.

*GenericMapping*<br/>
Ein Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) -Struktur, die die Zuordnung von jedem generischen Recht zu bestimmten Rechten für das-Objekt angibt.

*ObjectType*<br/>
Ein Zeiger auf eine- `GUID` Struktur, die den Typ des Objekts identifiziert, das dem aktuellen-Objekt zugeordnet ist. Legen Sie *ObjectType* auf NULL fest, wenn das Objekt nicht über eine GUID verfügt.

*biscontainerobject*<br/>
Gibt an, ob das neue-Objekt andere Objekte enthalten kann. Der Wert true gibt an, dass das neue Objekt ein Container ist. Der Wert false gibt an, dass das neue Objekt kein Container ist.

*Autogeerbt-Flags*<br/>
Ein Satz von Bitflags, mit denen gesteuert wird, wie Zugriffs Steuerungs Einträge (ACEs) von *pparent*geerbt werden. Weitere Informationen finden Sie unter " [kreateprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) ".

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft " [kreateprivateobjectser.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) " oder " [kreateprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)" auf.

Die zweite Methode ermöglicht das Angeben der Objekttyp-GUID des neuen Objekts oder das Steuern der Vererbung von ACEs.

> [!NOTE]
> Eine selbst relative Sicherheits Beschreibung ist eine Sicherheits Beschreibung, in der alle Sicherheitsinformationen in einem zusammenhängenden Speicherblock gespeichert werden.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a> Cprivateobjectsecuritydesc:: Get

Rufen Sie diese Methode auf, um Informationen aus der Sicherheits Beschreibung eines privaten Objekts abzurufen.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parameter

*Si*<br/>
Ein Satz von Bitflags, die die Teile der abzurufenden Sicherheits Beschreibung angeben. Bei diesem Wert kann es sich um eine Kombination aus den [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags handeln.

*pResult*<br/>
Ein Zeiger auf ein [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) -Objekt, das eine Kopie der angeforderten Informationen aus der angegebenen Sicherheits Beschreibung empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Die Sicherheits Beschreibung ist eine Struktur und zugehörige Daten, die die Sicherheitsinformationen für ein Sicherungs fähiges Objekt enthalten.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a> Cprivateobjectsecuritydesc:: Operator =

Zuweisungsoperator.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parameter

*rhs*<br/>
Das `CPrivateObjectSecurityDesc`-Objekt, das dem aktuellen Objekt zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das aktualisierte `CPrivateObjectSecurityDesc` Objekt zurück.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a> Cprivateobjectsecuritydesc:: Set

Mit dieser Methode können Sie die Sicherheits Beschreibung eines privaten Objekts ändern.

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
Ein Satz von Bitflags, die die Teile der Sicherheits Beschreibung angeben, die festgelegt werden sollen. Bei diesem Wert kann es sich um eine Kombination aus den [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) Bitflags handeln.

*Modifikation (Modification)*<br/>
Zeiger auf ein [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) -Objekt. Die Teile dieser Sicherheits Beschreibung, die durch den *Si* -Parameter angegeben werden, werden auf die Sicherheits Beschreibung des Objekts angewendet.

*GenericMapping*<br/>
Ein Zeiger auf eine [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) -Struktur, die die Zuordnung von jedem generischen Recht zu bestimmten Rechten für das-Objekt angibt.

*Token*<br/>
Verweis auf das [CAccessToken](../../atl/reference/caccesstoken-class.md) -Objekt für den Client Prozess, in dessen Auftrag das Objekt erstellt wird.

*Autogeerbt-Flags*<br/>
Ein Satz von Bitflags, mit denen gesteuert wird, wie Zugriffs Steuerungs Einträge (ACEs) von *pparent*geerbt werden. Weitere Informationen finden Sie unter " [kreateprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) ".

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg true zurück, bei einem Fehler false.

### <a name="remarks"></a>Bemerkungen

Die zweite Methode ermöglicht das Angeben der Objekttyp-GUID des Objekts oder das Steuern der Vererbung von ACEs.

## <a name="see-also"></a>Weitere Informationen

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Globale Sicherheitsfunktionen](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc-Klasse](../../atl/reference/csecuritydesc-class.md)
