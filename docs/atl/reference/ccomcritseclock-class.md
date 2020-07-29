---
title: Ccomcritcclock-Klasse
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
ms.openlocfilehash: fd2904f67d84db42d6b35aa4e505b063d6ea9a9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224291"
---
# <a name="ccomcritseclock-class"></a>Ccomcritcclock-Klasse

Diese Klasse stellt Methoden zum Sperren und Entsperren eines kritischen Abschnitts Objekts bereit.

## <a name="syntax"></a>Syntax

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Parameter

*Tlock*<br/>
Das Objekt, das gesperrt und entsperrt werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Ccomcritcclock:: ccomcritcclock](#ctor)|Der Konstruktor.|
|[Ccomcritcclock:: ~ ccomcritcclock](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccomcritcclock:: Lock](#lock)|Mit dieser Methode wird das Objekt des kritischen Abschnitts gesperrt.|
|[Ccomcritcclock:: Unlock](#unlock)|Mit dieser Methode wird das Objekt des kritischen Abschnitts entsperrt.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Klasse zum Sperren und Entsperren von Objekten auf sicherere Weise als bei der [ccomcriticalsection-Klasse](../../atl/reference/ccomcriticalsection-class.md) oder der [ccomautocriticalsection-Klasse](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>Ccomcritcclock:: ccomcritcclock

Der Konstruktor.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Parameter

*CS*<br/>
Das kritische Abschnitts Objekt.

*binitizuweisung*<br/>
Der anfängliche Sperr Zustand: **`true`** bedeutet gesperrt.

### <a name="remarks"></a>Bemerkungen

Initialisiert das Objekt des kritischen Abschnitts.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>Ccomcritcclock:: ~ ccomcritcclock

Der Destruktor.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Bemerkungen

Entsperrt das Objekt des kritischen Abschnitts.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>Ccomcritcclock:: Lock

Mit dieser Methode wird das Objekt des kritischen Abschnitts gesperrt.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn das Objekt erfolgreich gesperrt wurde, oder einen Fehler HRESULT bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt bereits gesperrt ist, tritt ein Assert-Fehler in Debugbuilds auf.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>Ccomcritcclock:: Unlock

Mit dieser Methode wird das Objekt des kritischen Abschnitts entsperrt.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt bereits entsperrt ist, tritt ein Assert-Fehler in Debugbuilds auf.

## <a name="see-also"></a>Siehe auch

[Ccomcriticalsection-Klasse](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Ccomautocriticalsection-Klasse](../../atl/reference/ccomautocriticalsection-class.md)
