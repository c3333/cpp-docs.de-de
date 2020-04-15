---
title: CComSafeDeleteCriticalSection-Klasse
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
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327370"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection-Klasse

Diese Klasse stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnittsobjekts bereit.

## <a name="syntax"></a>Syntax

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Der Konstruktor.|
|[CComSafeDeleteCriticalSection::-cComSafeDeleteCriticalSection](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Erstellt und initialisiert ein kritisches Schnittobjekt.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Ruft den Besitz des kritischen Abschnittsobjekts ab.|
|[CComSafeDeleteCriticalSection::Term](#term)|Gibt Systemressourcen frei, die vom kritischen Abschnittsobjekt verwendet werden.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Flags, ob `CRITICAL_SECTION` das interne Objekt initialisiert wurde.|

## <a name="remarks"></a>Bemerkungen

`CComSafeDeleteCriticalSection`leitet sich von der Klasse [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)ab. `CComSafeDeleteCriticalSection` Bietet jedoch zusätzliche Sicherheitsmechanismen über [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Wenn eine `CComSafeDeleteCriticalSection` Instanz von aus dem Gültigkeitsbereich geht oder explizit aus dem Speicher gelöscht wird, wird das zugrunde liegende objekt des kritischen Abschnitts automatisch bereinigt, wenn es noch gültig ist. Darüber hinaus wird die [CComSafeDeleteCriticalSection::Term-Methode](#term) ordnungsgemäß beendet, wenn das zugrunde liegende kritische Abschnittsobjekt noch nicht zugewiesen wurde oder bereits aus dem Speicher freigegeben wurde.

Weitere Informationen zu kritischen Abschnittshilfsklassen finden Sie unter [CComCriticalSection.](../../atl/reference/ccomcriticalsection-class.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Der Konstruktor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Bemerkungen

Legt den [m_bInitialized](#m_binitialized) Datenmember auf FALSE fest.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafeDeleteCriticalSection::-cComSafeDeleteCriticalSection

Der Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt das `CRITICAL_SECTION` interne Objekt aus dem Speicher frei, wenn das [m_bInitialized](#m_binitialized) Datenmember auf TRUE festgelegt ist.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteCriticalSection::Init

Ruft die Basisklassenimplementierung von [Init](/visualstudio/debugger/init) auf und legt [m_bInitialized](#m_binitialized) auf TRUE fest, falls erfolgreich.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init)zurück.

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteCriticalSection::Lock

Ruft die Basisklassenimplementierung von [Lock](ccomcriticalsection-class.md#lock)auf.

```
HRESULT Lock();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock)zurück.

### <a name="remarks"></a>Bemerkungen

Bei dieser Methode wird davon [ausgegangen,](#m_binitialized) dass der m_bInitialized Datenmember bei der Eingabe auf TRUE festgelegt ist. In Debugbuilds wird eine Assertion generiert, wenn diese Bedingung nicht erfüllt ist.

Weitere Informationen zum Verhalten der Funktion finden Sie unter [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized

Flags, ob `CRITICAL_SECTION` das interne Objekt initialisiert wurde.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Bemerkungen

Der `m_bInitialized` Datenmember wird verwendet, um `CRITICAL_SECTION` die Gültigkeit des zugrunde liegenden Objekts nachzuverfolgen, das der [CComSafeDeleteCriticalSection-Klasse](../../atl/reference/ccomsafedeletecriticalsection-class.md) zugeordnet ist. Das `CRITICAL_SECTION` zugrunde liegende Objekt wird nicht versucht, aus dem Speicher freigegeben zu werden, wenn dieses Flag nicht auf TRUE festgelegt ist.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteCriticalSection::Term

Ruft die Basisklassenimplementierung von [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) auf, wenn das interne `CRITICAL_SECTION` Objekt gültig ist.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis von [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)oder S_OK zurück, wenn [m_bInitialized](#m_binitialized) beim Eintrag auf FALSE festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Es ist sicher, diese Methode `CRITICAL_SECTION` aufzurufen, auch wenn das interne Objekt ungültig ist. Der Destruktor dieser Klasse ruft diese Methode auf, wenn der [m_bInitialized](#m_binitialized) Datenmember auf TRUE festgelegt ist.

## <a name="see-also"></a>Siehe auch

[CComCriticalSection-Klasse](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
