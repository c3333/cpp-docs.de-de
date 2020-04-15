---
title: CHandle-Klasse
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 7c72ded75298ed69efe73c1a81abf404545ea9b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326925"
---
# <a name="chandle-class"></a>CHandle-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwenden eines Handleobjekts bereit.

## <a name="syntax"></a>Syntax

```
class CHandle
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Der Konstruktor.|
|[CHandle::-CHandle](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHandle::Attach](#attach)|Rufen Sie diese `CHandle` Methode auf, um das Objekt an ein vorhandenes Handle anzufügen.|
|[CHandle::Schließen](#close)|Rufen Sie diese `CHandle` Methode auf, um ein Objekt zu schließen.|
|[CHandle::Detach](#detach)|Rufen Sie diese Methode auf, `CHandle` um ein Handle von einem Objekt zu trennen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHandle::operator HANDLE](#operator_handle)|Gibt den Wert des gespeicherten Handles zurück.|
|[CHandle::operator =](#operator_eq)|Zuweisungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHandle::m_h](#m_h)|Die Membervariable, die das Handle speichert.|

## <a name="remarks"></a>Bemerkungen

Ein `CHandle` Objekt kann immer dann verwendet werden, wenn `CHandle` ein Handle erforderlich ist: Der Hauptunterschied besteht darin, dass das Objekt automatisch gelöscht wird.

> [!NOTE]
> Einige API-Funktionen verwenden NULL als leeres oder ungültiges Handle, während andere INVALID_HANDLE_VALUE verwenden. `CHandle`verwendet nur NULL und behandelt INVALID_HANDLE_VALUE als echtes Handle. Wenn Sie eine API aufrufen, die INVALID_HANDLE_VALUE zurückgeben kann, sollten Sie nach diesem `CHandle` Wert suchen, bevor Sie [CHandle::Attach](#attach) aufrufen oder an den Konstruktor übergeben, und stattdessen NULL übergeben.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>CHandle::Attach

Rufen Sie diese `CHandle` Methode auf, um das Objekt an ein vorhandenes Handle anzufügen.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parameter

*H*<br/>
`CHandle`übernimmt das Handle *h*.

### <a name="remarks"></a>Bemerkungen

Weist das `CHandle` Objekt dem *h-Handle* zu und ruft dann **h.Detach()** auf. In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *h* NULL ist. Es wird keine andere Prüfung der Gültigkeit des Griffs vorgenommen.

## <a name="chandlechandle"></a><a name="chandle"></a>CHandle::CHandle

Der Konstruktor.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein vorhandenes `CHandle`Handle oder .

### <a name="remarks"></a>Bemerkungen

Erstellt ein `CHandle` neues Objekt, optional mit `CHandle` einem vorhandenen Handle oder Objekt.

## <a name="chandlechandle"></a><a name="dtor"></a>CHandle::-CHandle

Der Destruktor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt das `CHandle` Objekt frei, indem [CHandle::Close](#close)aufgerufen wird.

## <a name="chandleclose"></a><a name="close"></a>CHandle::Schließen

Rufen Sie diese `CHandle` Methode auf, um ein Objekt zu schließen.

```
void Close() throw();
```

### <a name="remarks"></a>Bemerkungen

Schließt ein geöffnetes Objekthandle. Wenn das Handle NULL ist, was `Close` der Fall sein wird, wenn es bereits aufgerufen wurde, wird ein ATLASSERT in Debugbuilds ausgelöst.

## <a name="chandledetach"></a><a name="detach"></a>CHandle::Detach

Rufen Sie diese Methode auf, `CHandle` um ein Handle von einem Objekt zu trennen.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den abgetrennten Ziehpunkt zurück.

### <a name="remarks"></a>Bemerkungen

Gibt den Besitz des Handles frei.

## <a name="chandlem_h"></a><a name="m_h"></a>CHandle::m_h

Die Membervariable, die das Handle speichert.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>CHandle::operator =

Der Zuweisungsoperator.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parameter

*H*<br/>
`CHandle`übernimmt das Handle *h*.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis `CHandle` auf das neue Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Wenn `CHandle` das Objekt derzeit ein Handle enthält, wird es geschlossen. Für `CHandle` das übergebene Objekt ist der Handleverweis auf NULL festgelegt. Dadurch wird `CHandle` sichergestellt, dass zwei Objekte niemals denselben aktiven Handle enthalten.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>CHandle::operator HANDLE

Gibt den Wert des gespeicherten Handles zurück.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt den in [CHandle::m_h](#m_h)gespeicherten Wert zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
