---
title: CSyncObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365971"
---
# <a name="csyncobject-class"></a>CSyncObject-Klasse

Eine rein virtuelle Klasse, welche die Funktionalität bereitstellt, die alle Synchronisierungsobjekte in Win32 gemeinsam haben.

## <a name="syntax"></a>Syntax

```
class CSyncObject : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Erstellt ein `CSyncObject`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSyncObject::Sperren](#lock)|Erhält Zugriff auf das Synchronisierungsobjekt.|
|[CSyncObject::Entsperren](#unlock)|Erhält Zugriff auf das Synchronisierungsobjekt.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSyncObject::operator HANDLE](#operator_handle)|Bietet Zugriff auf das Synchronisierungsobjekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Das Handle für das zugrunde liegende Synchronisierungsobjekt.|

## <a name="remarks"></a>Bemerkungen

Die Microsoft Foundation-Klassenbibliothek stellt `CSyncObject`mehrere Klassen bereit, die von abgeleitet sind. Dies sind [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)und [CSemaphore](../../mfc/reference/csemaphore-class.md).

Informationen zur Verwendung der Synchronisierungsobjekte finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject

Erstellt ein Synchronisierungsobjekt mit dem angegebenen Namen.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parameter

*pstrName*<br/>
Der Name des Objekts. Wenn NULL, ist *pstrName* null.

## <a name="csyncobjectlock"></a><a name="lock"></a>CSyncObject::Sperren

Rufen Sie diese Funktion auf, um Zugriff auf die vom Synchronisierungsobjekt gesteuerte Ressource zu erhalten.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parameter

*dwTimeout*<br/>
Gibt die Zeit in Millisekunden an, um zu warten, bis das Synchronisierungsobjekt verfügbar ist (signalisiert). Wenn INFINITE, wartet, `Lock` bis das Objekt signalisiert wird, bevor es zurückkehrt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Synchronisierungsobjekt `Lock` signalisiert wird, wird erfolgreich zurückgegeben, und der Thread besitzt nun das Objekt. Wenn das Synchronisierungsobjekt nicht signalisiert `Lock` (nicht verfügbar) ist, wartet es, bis das Synchronisierungsobjekt bis zur im Parameter *dwTimeOut* angegebenen Anzahl von Millisekunden signalisiert wird. Wenn das Synchronisierungsobjekt nicht in der angegebenen `Lock` Zeit signalisiert wurde, wird ein Fehler zurückgegeben.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject

Das Handle für das zugrunde liegende Synchronisierungsobjekt.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::operator HANDLE

Verwenden Sie diesen Operator, `CSyncObject` um das Handle des Objekts abzubekommen.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle des Synchronisierungsobjekts; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Sie können das Handle verwenden, um Windows-APIs direkt aufzurufen.

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Entsperren

Die Deklaration von `Unlock` ohne Parameter ist eine reine virtuelle Funktion und `CSyncObject`muss von allen Klassen überschrieben werden, die von ableiten.

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Standardmäßig nicht verwendet.

*lpPrevCount*<br/>
Standardmäßig nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung der Deklaration mit zwei Parametern gibt immer TRUE zurück. Diese Funktion wird aufgerufen, um den Zugriff auf das Synchronisierungsobjekt freizugeben, das dem aufrufenden Thread gehört. Die zweite Deklaration wird für Synchronisierungsobjekte wie Semaphore bereitgestellt, die mehr als einen Zugriff auf eine gesteuerte Ressource zulassen.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
