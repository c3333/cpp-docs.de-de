---
title: Ccomsafedeletecriticalsection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: 115cbd466f51db271f4be65ce708fe54c7f2b2ce
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833633"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Ccomsafedeletecriticalsection-Klasse

Diese Klasse stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereit.

## <a name="syntax"></a>Syntax

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Ccomsafedeletecriticalsection:: ccomsafedeletecriticalsection](#ccomsafedeletecriticalsection)|Der Konstruktor.|
|[Ccomsafedeletecriticalsection:: ~ ccomsafedeletecriticalsection](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccomsafedeletecriticalsection:: init](#init)|Erstellt und initialisiert ein kritisches Abschnitts Objekt.|
|[Ccomsafedeletecriticalsection:: Lock](#lock)|Ruft den Besitz des kritischen Abschnitts Objekts ab.|
|[Ccomsafedeletecriticalsection:: Term](#term)|Gibt Systemressourcen frei, die vom Objekt des kritischen Abschnitts verwendet werden.|

### <a name="data-members"></a>Datenelemente

|Datenelement|Beschreibung|
|-|-|
|[m_bInitialized](#m_binitialized)|Gibt an, ob das interne `CRITICAL_SECTION` Objekt initialisiert wurde.|

## <a name="remarks"></a>Bemerkungen

`CComSafeDeleteCriticalSection` wird von der [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)-Klasse abgeleitet. Bietet jedoch `CComSafeDeleteCriticalSection` zusätzliche Sicherheitsmechanismen über [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md).

Wenn eine Instanz von `CComSafeDeleteCriticalSection` den Gültigkeitsbereich verlässt oder explizit aus dem Arbeitsspeicher gelöscht wird, wird das zugrunde liegende kritische Abschnitts Objekt automatisch bereinigt, wenn es noch gültig ist. Außerdem wird die [ccomsafedeletecriticalsection:: Term](#term) -Methode ordnungsgemäß beendet, wenn das zugrunde liegende kritische Abschnitts Objekt noch nicht zugeordnet wurde oder bereits aus dem Arbeitsspeicher freigegeben wurde.

Weitere Informationen zu kritischen Abschnitts Hilfsklassen finden Sie unter [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a> Ccomsafedeletecriticalsection:: ccomsafedeletecriticalsection

Der Konstruktor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_bInitialized](#m_binitialized) Datenmember auf false fest.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a> Ccomsafedeletecriticalsection:: ~ ccomsafedeletecriticalsection

Der Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt das interne `CRITICAL_SECTION` Objekt aus dem Arbeitsspeicher frei, wenn das [m_bInitialized](#m_binitialized) Datenmember auf true festgelegt ist.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a> Ccomsafedeletecriticalsection:: init

Ruft die Basisklassen Implementierung von [Init](/visualstudio/debugger/init) auf und legt [m_bInitialized](#m_binitialized) auf true fest, wenn erfolgreich.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [ccomcriticalsection:: init](../../atl/reference/ccomcriticalsection-class.md#init)zurück.

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a> Ccomsafedeletecriticalsection:: Lock

Ruft die Basisklassen Implementierung von [Lock](ccomcriticalsection-class.md#lock)auf.

```
HRESULT Lock();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [ccomcriticalsection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock)zurück.

### <a name="remarks"></a>Bemerkungen

Bei dieser Methode wird davon ausgegangen, dass der [m_bInitialized](#m_binitialized) Datenmember beim Eintrag auf true festgelegt ist. Eine-Assertion wird in Debugbuilds generiert, wenn diese Bedingung nicht erfüllt wird.

Weitere Informationen zum Verhalten der Funktion finden Sie unter [ccomcriticalsection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a> Ccomsafedeletecriticalsection:: m_bInitialized

Gibt an, ob das interne `CRITICAL_SECTION` Objekt initialisiert wurde.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Bemerkungen

Der `m_bInitialized` Datenmember wird verwendet, um die Gültigkeit des zugrunde liegenden Objekts nachverfolgen, `CRITICAL_SECTION` das der [ccomsafedeletecriticalsection](../../atl/reference/ccomsafedeletecriticalsection-class.md) -Klasse zugeordnet ist. `CRITICAL_SECTION`Wenn dieses Flag nicht auf true festgelegt ist, wird nicht versucht, das zugrunde liegende Objekt aus dem Arbeitsspeicher freizugeben.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a> Ccomsafedeletecriticalsection:: Term

Ruft die Basisklassen Implementierung von [ccomcriticalsection:: Term](../../atl/reference/ccomcriticalsection-class.md#term) auf, wenn das interne `CRITICAL_SECTION` Objekt gültig ist.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [ccomcriticalsection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)oder S_OK zurück, wenn [m_bInitialized](#m_binitialized) beim Eintrag auf false festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Es ist sicher, diese Methode auch dann aufzurufen, wenn das interne `CRITICAL_SECTION` Objekt ungültig ist. Der destrukturtor dieser Klasse ruft diese Methode auf, wenn das [m_bInitialized](#m_binitialized) Datenmember auf true festgelegt ist.

## <a name="see-also"></a>Weitere Informationen

[Ccomcriticalsection-Klasse](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
