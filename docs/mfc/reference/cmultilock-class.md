---
title: CMultiLock-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319713"
---
# <a name="cmultilock-class"></a>CMultiLock-Klasse

Stellt den Mechanismus zur Zugriffssteuerung dar, mit dessen Hilfe der Zugriff auf Ressourcen in einem Multithreadprogramm gesteuert wird.

## <a name="syntax"></a>Syntax

```
class CMultiLock
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Erstellt ein `CMultiLock`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|Bestimmt, ob ein bestimmtes Synchronisierungsobjekt im Array gesperrt ist.|
|[CMultiLock::Lock](#lock)|Wartet auf das Array von Synchronisierungsobjekten.|
|[CMultiLock::Entsperren](#unlock)|Gibt alle eigenen Synchronisierungsobjekte frei.|

## <a name="remarks"></a>Bemerkungen

`CMultiLock`hat keine Basisklasse.

Um die Synchronisationsklassen [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)und [CEvent](../../mfc/reference/cevent-class.md)zu verwenden, können Sie entweder ein `CMultiLock` oder ein [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) erstellen, auf das gewartet und das Synchronisierungsobjekt freigegeben werden soll. Verwenden `CMultiLock` Sie diese Datei, wenn mehrere Objekte vorhanden sind, die Sie zu einem bestimmten Zeitpunkt verwenden können. Verwenden `CSingleLock` Sie diese Aufgabe, wenn Sie jeweils nur auf ein Objekt warten müssen.

Um ein `CMultiLock` Objekt zu verwenden, erstellen Sie zunächst ein Array der Synchronisierungsobjekte, auf die Sie warten möchten. Rufen Sie `CMultiLock` als Nächstes den Konstruktor des Objekts innerhalb einer Memberfunktion in der Klasse der gesteuerten Ressource auf. Rufen Sie dann die [Memberfunktion Sperren](#lock) auf, um zu ermitteln, ob eine Ressource verfügbar ist (signalisiert). Wenn dies der Vorgang der Letzter ist, fahren Sie mit der restlichen Memberfunktion fort. Wenn keine Ressource verfügbar ist, warten Sie entweder auf einen bestimmten Zeitraum, bis eine Ressource freigegeben wird, oder geben Sie einen Fehler zurück. Rufen Sie nach Abschluss der Verwendung einer Ressource entweder die [Funktion Entsperren auf,](#unlock) wenn das `CMultiLock` Objekt erneut verwendet werden soll, oder lassen Sie das `CMultiLock` Objekt zerstören.

`CMultiLock`Objekte sind am nützlichsten, wenn `CEvent` ein Thread über eine große Anzahl von Objekten verfügt, auf die er reagieren kann. Erstellen Sie ein `CEvent` Array, das alle `Lock`Zeiger enthält, und rufen Sie auf. Dadurch wartet der Thread, bis eines der Ereignisse signalisiert wird.

Weitere Informationen zur Verwendung `CMultiLock` von Objekten finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CMultiLock`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock

Erstellt ein `CMultiLock`-Objekt.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parameter

*ppObjects*<br/>
Array von Zeigern auf die zu wartenden Synchronisierungsobjekte. Lässt keine NULL-Werte zu.

*dwCount*<br/>
Anzahl der Objekte in *ppObjects*. Muss größer als 0 sein.

*bInitialLock*<br/>
Gibt an, ob zunächst versucht werden soll, auf eines der angegebenen Objekte zuzugreifen.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, nachdem das Array von Synchronisierungsobjekten erstellt wurde, auf die gewartet werden soll. Es wird normalerweise innerhalb des Threads aufgerufen, der warten muss, bis eines der Synchronisierungsobjekte verfügbar ist.

## <a name="cmultilockislocked"></a><a name="islocked"></a>CMultiLock::IsLocked

Bestimmt, ob das angegebene Objekt nicht signalisiert (nicht verfügbar) ist.

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parameter

*dwItem*<br/>
Der Index im Array von Objekten, die dem Objekt entsprechen, dessen Zustand abgefragt wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das angegebene Objekt gesperrt ist; andernfalls 0.

## <a name="cmultilocklock"></a><a name="lock"></a>CMultiLock::Lock

Rufen Sie diese Funktion auf, um Zugriff auf eine oder `CMultiLock` mehrere Ressourcen zu erhalten, die von den dem Konstruktor bereitgestellten Synchronisierungsobjekten gesteuert werden.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parameter

*dwTimeOut*<br/>
Gibt an, wie lange gewartet werden muss, bis das Synchronisierungsobjekt verfügbar ist (signalisiert). Wenn INFINITE, wartet, `Lock` bis das Objekt signalisiert wird, bevor es zurückkehrt.

*bWaitForAll*<br/>
Gibt an, ob alle objekte, auf die gewartet wurde, gleichzeitig signalisiert werden müssen, bevor sie zurückgegeben werden. Wenn FALSE, wird zurückgegeben, `Lock` wenn eines der objekte, auf die gewartet wurde, signalisiert wird.

*dwWakeMask*<br/>
Gibt andere Bedingungen an, die die Wartezeit abbrechen dürfen. Eine vollständige Liste der verfügbaren Optionen für diesen Parameter finden Sie unter [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Wenn `Lock` dies fehlschlägt, kehrt er zurück - 1. Bei Erfolg wird einer der folgenden Werte zurückgegeben:

- Zwischen WAIT_OBJECT_0 und WAIT_OBJECT_0 + (Anzahl der Objekte - 1)

   Wenn *bWaitForAll* TRUE ist, werden alle Objekte signalisiert (verfügbar). Wenn *bWaitForAll* FALSE ist, ist der Rückgabewert - WAIT_OBJECT_0 der Index im Array der Objekte des Objekts, das signalisiert wird (verfügbar).

- WAIT_OBJECT_0 + (Anzahl der Objekte)

   Ein in *dwWakeMask* angegebenes Ereignis ist in der Eingabewarteschlange des Threads verfügbar.

- Zwischen WAIT_ABANDONED_0 und WAIT_ABANDONED_0 + (Anzahl der Objekte - 1)

   Wenn *bWaitForAll* TRUE ist, werden alle Objekte signalisiert, und mindestens eines der Objekte ist ein verlassenes mutex-Objekt. Wenn *bWaitForAll* FALSE ist, ist der Rückgabewert - WAIT_ABANDONED_0 der Index im Array von Objekten des verlassenen mutex-Objekts, der die Wartezeit befriedigt hat.

- Wait_timeout

   Das in *dwTimeOut* angegebene Timeoutintervall ist abgelaufen, ohne dass die Wartezeit erfolgreich war.

### <a name="remarks"></a>Bemerkungen

Wenn *bWaitForAll* TRUE `Lock` ist, wird erfolgreich zurückgegeben, sobald alle Synchronisationsobjekte gleichzeitig signalisiert werden. Wenn *bWaitForAll* FALSE `Lock` ist, wird zurückgegeben, sobald eines oder mehrere der Synchronisierungsobjekte signalisiert werden.

Wenn `Lock` die Rückgabe nicht sofort möglich ist, wartet sie nicht mehr als die im Parameter *dwTimeOut* angegebene Anzahl von Millisekunden, bevor sie zurückgegeben wird. Wenn *dwTimeOut* INFINITE `Lock` ist, wird erst zurückgegeben, wenn der Zugriff auf ein Objekt gewonnen wurde oder eine in *dwWakeMask* angegebene Bedingung erfüllt wurde. Andernfalls wird `Lock` ein Synchronisierungsobjekt erfolgreich zurückgegeben, wenn es ein Synchronisierungsobjekt abrufen konnte. wenn nicht, wird es Fehler zurückgeben.

## <a name="cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Entsperren

Gibt das Synchronisierungsobjekt frei, das im Besitz von `CMultiLock`ist.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Die Anzahl der Verweisanzahlfür die Freigabe. Muss größer als 0 sein. Wenn der angegebene Betrag dazu führen würde, dass die Anzahl des Objekts das Maximum überschreitet, wird die Anzahl nicht geändert, und die Funktion gibt FALSE zurück.

*lPrevCount*<br/>
Zeigt auf eine Variable, um die vorherige Anzahl für das Synchronisierungsobjekt zu erhalten. Wenn NULL, wird die vorherige Anzahl nicht zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird `CMultiLock`vom Destruktor von aufgerufen.

Die erste `Unlock` Form des Versuchs, `CMultiLock`das von verwaltete Synchronisierungsobjekt zu entsperren. Die zweite `Unlock` Form des `CSemaphore` Versuchs, `CMultiLock`die Objekte freizuschalten, die im Besitz von sind. Wenn `CMultiLock` kein gesperrtes `CSemaphore` Objekt vorhanden ist, gibt die Funktion FALSE zurück. Andernfalls gibt es TRUE zurück. *lCount* und *lpPrevCount* sind genau die gleichen wie die Parameter von [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Die zweite `Unlock` Form von ist selten auf Multilock-Situationen anwendbar.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
