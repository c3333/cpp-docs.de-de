---
title: CComCritSecLock-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 4b2ef093c1142b592ad2a6605a08bd8c34a643ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748074"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock-Klasse

Diese Klasse stellt Methoden zum Sperren und Entsperren eines kritischen Abschnittsobjekts bereit.

## <a name="syntax"></a>Syntax

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parameter

*TLock*<br/>
Das zu sperrende und zu entsperrte Objekt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Der Konstruktor.|
|[CComCritSecLock::'CComCritSecLock](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Rufen Sie diese Methode auf, um das Objekt des kritischen Abschnitts zu sperren.|
|[CComCritSecLock::Entsperren](#unlock)|Rufen Sie diese Methode auf, um das Objekt des kritischen Abschnitts zu entsperren.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Klasse, um Objekte sicherer zu sperren und zu entsperren als mit der [CComCriticalSection-Klasse](../../atl/reference/ccomcriticalsection-class.md) oder [cComAutoCriticalSection-Klasse](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

Der Konstruktor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parameter

*Cs*<br/>
Das kritische Abschnittsobjekt.

*bInitialLock*<br/>
Der anfängliche Sperrzustand: **true** bedeutet gesperrt.

### <a name="remarks"></a>Bemerkungen

Initialisiert das Objekt des kritischen Abschnitts.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock::'CComCritSecLock

Der Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Bemerkungen

Entsperrt das Objekt des kritischen Abschnitts.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock::Lock

Rufen Sie diese Methode auf, um das Objekt des kritischen Abschnitts zu sperren.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn das Objekt erfolgreich gesperrt wurde, oder einen Fehler HRESULT bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt bereits gesperrt ist, tritt ein ASSERT-Fehler in Debugbuilds auf.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock::Entsperren

Rufen Sie diese Methode auf, um das Objekt des kritischen Abschnitts zu entsperren.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt bereits entsperrt ist, tritt ein ASSERT-Fehler in Debugbuilds auf.

## <a name="see-also"></a>Weitere Informationen

[CComCriticalSection-Klasse](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection-Klasse](../../atl/reference/ccomautocriticalsection-class.md)
