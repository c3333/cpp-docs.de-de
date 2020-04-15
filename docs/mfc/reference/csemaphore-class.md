---
title: CSemaphore-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318501"
---
# <a name="csemaphore-class"></a>CSemaphore-Klasse

Ein Objekt `CSemaphore` der Klasse stellt ein "Semaphore" dar – ein Synchronisierungsobjekt, das einer begrenzten Anzahl von Threads in einem oder mehreren Prozessen den Zugriff auf eine Verwaltet eine Anzahl von Threads ermöglicht, die derzeit auf eine angegebene Ressource zugreifen.

## <a name="syntax"></a>Syntax

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Erstellt ein `CSemaphore`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Semaphore sind nützlich, um den Zugriff auf eine freigegebene Ressource zu steuern, die nur eine begrenzte Anzahl von Benutzern unterstützen kann. Die aktuelle Anzahl `CSemaphore` des Objekts ist die Anzahl der zulässigen zusätzlichen Benutzer. Wenn die Anzahl Null erreicht, werden alle `CSemaphore` Versuche, die vom Objekt gesteuerte Ressource zu verwenden, in eine Systemwarteschlange eingefügt und warten, bis entweder eine Zeitbeimsamungszeit oder die Anzahl über 0 steigt. Die maximale Anzahl von Benutzern, die gleichzeitig auf die gesteuerte Ressource zugreifen können, wird während der Konstruktion des `CSemaphore` Objekts angegeben.

Um ein `CSemaphore` Objekt zu `CSemaphore` verwenden, erstellen Sie das Objekt, wenn es benötigt wird. Geben Sie den Namen des Semaphors an, auf das Sie warten möchten, und geben Sie an, dass die Anwendung zunächst Eigentümer des Semaphors sein soll. Sie können dann auf das Semaphor zugreifen, wenn der Konstruktor zurückkehrt. Rufen Sie [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) auf, wenn Sie mit dem Zugriff auf die gesteuerte Ressource fertig sind.

Eine alternative Methode `CSemaphore` zum Verwenden von Objekten `CSemaphore` besteht darin, der Klasse, die Sie steuern möchten, eine Variable des Typs als Datenmember hinzuzufügen. Rufen Sie während der Konstruktion des gesteuerten Objekts den Konstruktor des `CSemaphore` Datenmembers auf, der die anfängliche Zugriffsanzahl, die maximale Zugriffsanzahl, den Namen des Semaphors (wenn es über Prozessgrenzen hinweg verwendet wird) und die gewünschten Sicherheitsattribute angibt.

Um auf diese `CSemaphore` Weise auf Ressourcen zuzugreifen, die von Objekten gesteuert werden, erstellen Sie zunächst eine Variable vom Typ [CSingleLock](../../mfc/reference/csinglelock-class.md) oder in der Zugriffsmemberfunktion Ihrer Ressource [CMultiLock.](../../mfc/reference/cmultilock-class.md) Rufen Sie dann die `Lock` Memberfunktion des Sperrobjekts auf (z. B. [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). An diesem Punkt erhält der Thread entweder Zugriff auf die Ressource, wartet auf die Freigabe der Ressource und erhält Zugriff, oder er wartet, bis die Ressource freigegeben und eine Zeitauszeit ausgeführt wird, ohne Zugriff auf die Ressource zu erhalten. In jedem Fall wurde auf Ihre Ressource threadsicher zugegriffen. Um die Ressource freizugeben, verwenden `Unlock` Sie die Memberfunktion des Sperrobjekts (z. B. [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), oder lassen Sie zu, dass das Sperrobjekt aus dem Gültigkeitsbereich fällt.

Alternativ können Sie ein `CSemaphore` Objekt eigenständig erstellen und explizit darauf zugreifen, bevor Sie versuchen, auf die gesteuerte Ressource zuzugreifen. Diese Methode ist zwar für jemanden, der Ihren Quellcode liest, klarer, aber fehleranfälliger.

Weitere Informationen zur Verwendung `CSemaphore` von Objekten finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore

Erstellt ein benanntes `CSemaphore` oder unbenanntes Objekt.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parameter

*lInitialCount*<br/>
Die anfängliche Verwendungsanzahl für das Semaphor. Muss größer oder gleich 0 und kleiner oder gleich *lMaxCount*sein.

*lMaxCount*<br/>
Die maximale Nutzungsanzahl für das Semaphor. Muss größer als 0 sein.

*pstrName*<br/>
Der Name des Semaphors. Muss angegeben werden, wenn auf das Semaphor über Prozessgrenzen hinweg zugegriffen wird. Wenn `NULL`, wird das Objekt unbenannt. Wenn der Name mit einem vorhandenen Semaphor übereinstimmt, erstellt der Konstruktor ein neues `CSemaphore` Objekt, das auf das Semaphor dieses Namens verweist. Wenn der Name mit einem vorhandenen Synchronisierungsobjekt übereinstimmt, das kein Semaphor ist, schlägt die Konstruktion fehl.

*lpsaAttributes*<br/>
Sicherheitsattribute für das Semaphor-Objekt. Eine vollständige Beschreibung dieser Struktur finden Sie unter [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Um auf ein `CSemaphore` Objekt zuzugreifen oder es freizugeben, erstellen Sie ein [CMultiLock-](../../mfc/reference/cmultilock-class.md) oder [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) und rufen die [Mitgliedsfunktionen Sperren](../../mfc/reference/csinglelock-class.md#lock) und [Entsperren](../../mfc/reference/csinglelock-class.md#unlock) auf.

> [!IMPORTANT]
> Verwenden Sie `CSemaphore` nach dem Erstellen des Objekts [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) um sicherzustellen, dass der Mutex noch nicht vorhanden ist. Wenn der Mutex unerwartet existierte, kann dies darauf hindeuten, dass ein Nichtautorisiertes Prozess hockt und möglicherweise beabsichtigt, den Mutex böswillig zu verwenden. In diesem Fall wird das empfohlene sicherheitsbewusste Verfahren darin durchgeführt, das Handle zu schließen und so fortzufahren, als ob beim Erstellen des Objekts ein Fehler aufgetreten wäre.

## <a name="see-also"></a>Siehe auch

[CSyncObject-Klasse](../../mfc/reference/csyncobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
