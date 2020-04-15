---
title: CEvent-Klasse
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373959"
---
# <a name="cevent-class"></a>CEvent-Klasse

Stellt ein Ereignis dar, bei dem es sich um ein Synchronisierungsobjekt handelt, das es einem Thread ermöglicht, einen anderen thread zu benachrichtigen, dass ein Ereignis aufgetreten ist.

## <a name="syntax"></a>Syntax

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Erstellt ein `CEvent`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Legt das Ereignis auf verfügbar (signalisiert), gibt wartende Threads frei und legt das Ereignis auf nicht verfügbar (nicht signalisiert) fest.|
|[CEvent::ResetEvent](#resetevent)|Legt fest, dass das Ereignis nicht verfügbar ist (nicht signalisiert).|
|[CEvent::SetEvent](#setevent)|Legt das Ereignis auf verfügbar (signalisiert) fest und gibt alle wartenden Threads frei.|
|[CEvent::Entsperren](#unlock)|Gibt das Ereignisobjekt frei.|

## <a name="remarks"></a>Bemerkungen

Ereignisse sind nützlich, wenn ein Thread wissen muss, wann seine Aufgabe ausgeführt werden muss. Beispielsweise muss ein Thread, der Daten in ein Datenarchiv kopiert, benachrichtigt werden, wenn neue Daten verfügbar sind. Wenn Sie `CEvent` ein Objekt verwenden, um den Kopierthread zu benachrichtigen, wenn neue Daten verfügbar sind, kann der Thread seine Aufgabe so schnell wie möglich ausführen.

`CEvent`Objekte haben zwei Typen: manuell und automatisch.

Ein `CEvent` automatisches Objekt kehrt automatisch in einen nicht signalisierten (nicht verfügbaren) Zustand zurück, nachdem mindestens ein Thread freigegeben wurde. Standardmäßig ist `CEvent` ein Objekt automatisch, `TRUE` es sei denn, Sie übergeben den *Parameter bManualReset* während der Konstruktion.

Ein `CEvent` manuelles Objekt verbleibt in dem zustand, der von [SetEvent](#setevent) oder [ResetEvent](#resetevent) festgelegt wurde, bis die andere Funktion aufgerufen wird. Um ein `CEvent` manuelles `TRUE` Objekt `bManualReset` zu erstellen, übergeben Sie den Parameter während der Konstruktion.

Um ein `CEvent` Objekt zu `CEvent` verwenden, erstellen Sie das Objekt, wenn es erforderlich ist. Geben Sie den Namen des Ereignisses an, auf das Sie warten möchten, und geben Sie außerdem an, dass die Anwendung zunächst Eigentümer des Ereignisses sein soll. Sie können dann auf das Ereignis zugreifen, wenn der Konstruktor zurückkehrt. Rufen Sie [SetEvent](#setevent) auf, um das Ereignisobjekt zu signalisieren (verfügbar zu machen), und rufen Sie dann [Unlock](#unlock) auf, wenn Sie mit dem Zugriff auf die gesteuerte Ressource fertig sind.

Eine alternative Methode `CEvent` zum Verwenden von Objekten `CEvent` besteht darin, der Klasse, die Sie steuern möchten, eine Variable des Typs als Datenmember hinzuzufügen. Rufen Sie während der Konstruktion des gesteuerten Objekts den Konstruktor des `CEvent` Datenmembers auf, und geben Sie an, ob das Ereignis anfänglich signalisiert wird, und geben Sie auch den gewünschten Ereignistyp, den Namen des Ereignisses (falls es über Prozessgrenzen hinweg verwendet wird) und alle gewünschten Sicherheitsattribute an.

Um auf diese Weise `CEvent` auf eine von einem Objekt gesteuerte Ressource zuzugreifen, erstellen Sie zunächst eine Variable vom Typ [CSingleLock](../../mfc/reference/csinglelock-class.md) oder in der Zugriffsmethode Ihrer Ressource [cMultiLock.](../../mfc/reference/cmultilock-class.md) Rufen Sie `Lock` dann die Methode des Sperrobjekts auf (z. B. [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). An diesem Punkt erhält der Thread entweder Zugriff auf die Ressource, wartet auf die Freigabe der Ressource und erhält Zugriff, oder wartet, bis die Ressource freigegeben wird, eine Zeitauszeit und kein Zugriff auf die Ressource. In jedem Fall wurde auf Ihre Ressource threadsicher zugegriffen. Um die Ressource `SetEvent` freizugeben, rufen Sie das Ereignisobjekt auf, um das Ereignisobjekt zu signalisieren, und verwenden Sie dann die `Unlock` Methode des Sperrobjekts (z. B. [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), oder lassen Sie das Sperrobjekt aus dem Gültigkeitsbereich fallen.

Weitere Informationen zur Verwendung `CEvent` von Objekten finden Sie unter [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>CEvent::CEvent

Erstellt ein benanntes `CEvent` oder unbenanntes Objekt.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parameter

*bInitiallyOwn*<br/>
Wenn TRUE, ist `CMultilock` der `CSingleLock` Thread für das oder-Objekt aktiviert. Andernfalls müssen alle Threads, die auf die Ressource zugreifen möchten, warten.

*bManualReset*<br/>
Wenn TRUE, gibt an, dass das Ereignisobjekt ein manuelles Ereignis ist, andernfalls ist das Ereignisobjekt ein automatisches Ereignis.

*lpszName*<br/>
Name des `CEvent`-Objekts. Muss angegeben werden, wenn das Objekt über Prozessgrenzen hinweg verwendet wird. Wenn der Name mit einem vorhandenen Ereignis `CEvent` übereinstimmt, erstellt der Konstruktor ein neues Objekt, das auf das Ereignis dieses Namens verweist. Wenn der Name mit einem vorhandenen Synchronisierungsobjekt übereinstimmt, das kein Ereignis ist, schlägt die Konstruktion fehl. Wenn NULL, ist der Name NULL.

*lpsaAttribute*<br/>
Sicherheitsattribute für das Ereignisobjekt. Eine vollständige Beschreibung dieser Struktur finden Sie unter [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Um auf ein `CEvent` Objekt zuzugreifen oder es freizugeben, erstellen Sie ein [CMultiLock-](../../mfc/reference/cmultilock-class.md) oder [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) und rufen die [Mitgliedsfunktionen Sperren](../../mfc/reference/csinglelock-class.md#lock) und [Entsperren](../../mfc/reference/csinglelock-class.md#unlock) auf.

Um den Status `CEvent` eines Objekts in signalisiert zu ändern (Threads müssen nicht warten), rufen Sie [SetEvent](#setevent) oder [PulseEvent](#pulseevent)auf. Um den Status `CEvent` eines Objekts auf nicht signalisiert festzulegen (Threads müssen warten), rufen Sie [ResetEvent](#resetevent)auf.

> [!IMPORTANT]
> Verwenden Sie `CEvent` nach dem Erstellen des Objekts [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) um sicherzustellen, dass der Mutex noch nicht vorhanden ist. Wenn der Mutex unerwartet existierte, kann dies darauf hindeuten, dass ein Nichtautorisiertes Prozess hockt und möglicherweise beabsichtigt, den Mutex böswillig zu verwenden. In diesem Fall wird das empfohlene sicherheitsbewusste Verfahren darin durchgeführt, das Handle zu schließen und so fortzufahren, als ob beim Erstellen des Objekts ein Fehler aufgetreten wäre.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>CEvent::PulseEvent

Legt den Status des Ereignisses auf signalisiert (verfügbar) fest, gibt alle wartenden Threads frei und setzt es automatisch auf nicht signalisiert (nicht verfügbar) zurück.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Ereignis manuell ist, werden alle wartenden Threads freigegeben, `PulseEvent` das Ereignis wird auf nicht signalisiert festgelegt und kehrt zurück. Wenn das Ereignis automatisch ist, wird ein einzelner Thread freigegeben, `PulseEvent` das Ereignis wird auf nicht signalisiert gesetzt und kehrt zurück.

Wenn keine Threads warten oder keine Threads `PulseEvent` sofort freigegeben werden können, wird der Status des Ereignisses auf nicht signalisiert festgelegt und zurückgegeben.

`PulseEvent`verwendet die zugrunde `PulseEvent` liegende Win32-Funktion, die durch einen asynchronen Prozeduraufruf im Kernelmodus kurzzeitig aus dem Wartezustand entfernt werden kann. Daher `PulseEvent` ist unzuverlässig und sollte nicht von neuen Anwendungen verwendet werden. Weitere Informationen finden Sie in der [PulseEvent-Funktion](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a>CEvent::ResetEvent

Legt den Status des Ereignisses auf nicht signalisiert fest, bis explizit von der [SetEvent-Memberfunktion](#setevent) signalisiert festgelegt wird.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies führt dazu, dass alle Threads, die auf dieses Ereignis zugreifen möchten, warten.

Diese Memberfunktion wird von automatischen Ereignissen nicht verwendet.

## <a name="ceventsetevent"></a><a name="setevent"></a>CEvent::SetEvent

Legt den Status des Ereignisses auf signalisiert fest und gibt alle wartenden Threads frei.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn das Ereignis manuell ist, bleibt das Ereignis signalisiert, bis [ResetEvent](#resetevent) aufgerufen wird. In diesem Fall können mehr als ein Thread freigegeben werden. Wenn das Ereignis automatisch ist, bleibt das Ereignis signalisiert, bis ein einzelner Thread freigegeben wird. Das System setzt dann den Status des Ereignisses auf nicht signalisiert. Wenn keine Threads warten, bleibt der Status signalisiert, bis ein Thread freigegeben wird.

## <a name="ceventunlock"></a><a name="unlock"></a>CEvent::Entsperren

Gibt das Ereignisobjekt frei.

```
BOOL Unlock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Thread Eigentümer des Ereignisobjekts ist und das Ereignis ein automatisches Ereignis ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von Threads aufgerufen, die derzeit ein automatisches Ereignis besitzen, um sie nach deren Verwendung freizugeben, wenn ihr Sperrobjekt wiederverwendet werden soll. Wenn das Sperrobjekt nicht wiederverwendet werden soll, wird diese Funktion vom Destruktor des Sperrobjekts aufgerufen.

## <a name="see-also"></a>Siehe auch

[CSyncObject-Klasse](../../mfc/reference/csyncobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
