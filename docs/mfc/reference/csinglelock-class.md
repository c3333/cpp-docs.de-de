---
title: CSingleLock-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318270"
---
# <a name="csinglelock-class"></a>CSingleLock-Klasse

Stellt den Mechanismus zur Zugriffssteuerung dar, mit dessen Hilfe der Zugriff auf Ressourcen in einem Multithreadprogramm gesteuert wird.

## <a name="syntax"></a>Syntax

```
class CSingleLock
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Erstellt ein `CSingleLock`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Bestimmt, ob das Objekt gesperrt ist.|
|[CSingleLock::Sperren](#lock)|Wartet auf ein Synchronisierungsobjekt.|
|[CSingleLock::Entsperren](#unlock)|Gibt ein Synchronisierungsobjekt frei.|

## <a name="remarks"></a>Bemerkungen

`CSingleLock`hat keine Basisklasse.

Um die Synchronisationsklassen [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)und [CEvent](../../mfc/reference/cevent-class.md)zu verwenden, müssen Sie entweder ein `CSingleLock` oder ein [CMultiLock-Objekt](../../mfc/reference/cmultilock-class.md) erstellen, um zu warten und das Synchronisierungsobjekt freizugeben. Verwenden `CSingleLock` Sie diese Aufgabe, wenn Sie jeweils nur auf ein Objekt warten müssen. Verwenden `CMultiLock` Sie diese Datei, wenn mehrere Objekte vorhanden sind, die Sie zu einem bestimmten Zeitpunkt verwenden können.

Um ein `CSingleLock` Objekt zu verwenden, rufen Sie seinen Konstruktor innerhalb einer Memberfunktion in der Klasse der gesteuerten Ressource auf. Rufen Sie dann die [IsLocked-Memberfunktion](#islocked) auf, um zu ermitteln, ob die Ressource verfügbar ist. Wenn dies der Vorgang der Vorgang ist, fahren Sie mit dem Rest der Memberfunktion fort. Wenn die Ressource nicht verfügbar ist, warten Sie entweder auf einen bestimmten Zeitraum, bis die Ressource freigegeben wird, oder geben Sie einen Fehler zurück. Rufen Sie nach Abschluss der Verwendung der Ressource entweder die [Funktion Entsperren auf,](#unlock) wenn das `CSingleLock` Objekt erneut verwendet werden soll, oder lassen Sie das `CSingleLock` Objekt zerstören.

`CSingleLock`Objekte erfordern das Vorhandensein eines von [CSyncObject](../../mfc/reference/csyncobject-class.md)abgeleiteten Objekts . Dies ist in der Regel ein Datenmember der Klasse der gesteuerten Ressource. Weitere Informationen zur Verwendung `CSingleLock` von Objekten finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CSingleLock`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>CSingleLock::CSingleLock

Erstellt ein `CSingleLock`-Objekt.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Zeigt auf das Synchronisierungsobjekt, auf das zugegriffen werden soll. Lässt keine NULL-Werte zu.

*bInitialLock*<br/>
Gibt an, ob zunächst versucht werden soll, auf das angegebene Objekt zuzugreifen.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird im Allgemeinen innerhalb einer Zugriffsmemberfunktion der gesteuerten Ressource aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>CSingleLock::IsLocked

Bestimmt, ob das `CSingleLock` dem Objekt zugeordnete Objekt nicht signalisiert (nicht verfügbar) ist.

```
BOOL IsLocked();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt gesperrt ist; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>CSingleLock::Sperren

Rufen Sie diese Funktion auf, um Zugriff auf `CSingleLock` die Ressource zu erhalten, die vom Synchronisierungsobjekt gesteuert wird, das dem Konstruktor bereitgestellt wird.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parameter

*dwTimeOut*<br/>
Gibt an, wie lange gewartet werden muss, bis das Synchronisierungsobjekt verfügbar ist (signalisiert). Wenn INFINITE, wartet, `Lock` bis das Objekt signalisiert wird, bevor es zurückkehrt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Synchronisierungsobjekt `Lock` signalisiert wird, wird erfolgreich zurückgegeben, und der Thread besitzt nun das Objekt. Wenn das Synchronisierungsobjekt nicht signalisiert `Lock` (nicht verfügbar) ist, wartet es, bis das Synchronisierungsobjekt bis zur im Parameter *dwTimeOut* angegebenen Anzahl von Millisekunden signalisiert wird. Wenn das Synchronisierungsobjekt nicht in der angegebenen `Lock` Zeit signalisiert wurde, wird ein Fehler zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>CSingleLock::Entsperren

Gibt das Synchronisierungsobjekt frei, das im Besitz von `CSingleLock`ist.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Anzahl der freizugebenden Zugriffe. Muss größer als 0 sein. Wenn der angegebene Betrag dazu führen würde, dass die Anzahl des Objekts das Maximum überschreitet, wird die Anzahl nicht geändert, und die Funktion gibt FALSE zurück.

*lPrevCount*<br/>
Zeigt auf eine Variable, um die vorherige Anzahl des Synchronisierungsobjekts zu erhalten. Wenn NULL, wird die vorherige Anzahl nicht zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird `CSingleLock`vom Destruktor von aufgerufen.

Wenn Sie mehr als eine Zugriffsanzahl eines Semaphors freigeben `Unlock` müssen, verwenden Sie die zweite Form von und geben Sie die Anzahl der freizugebenden Zugriffe an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock-Klasse](../../mfc/reference/cmultilock-class.md)
