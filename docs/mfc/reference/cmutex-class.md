---
title: CMutex-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363285"
---
# <a name="cmutex-class"></a>CMutex-Klasse

Stellt einen "Mutex" dar – ein Synchronisierungsobjekt, das einem Thread den sich gegenseitig ausschließenden Zugriff auf eine Ressource ermöglicht.

## <a name="syntax"></a>Syntax

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Erstellt ein `CMutex`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Mutexe sind nützlich, wenn jeweils nur ein Thread Daten oder eine andere gesteuerte Ressource ändern darf. Das Hinzufügen von Knoten zu einer verknüpften Liste ist z. B. ein Prozess, der jeweils nur von einem Thread zugelassen werden sollte. Durch die `CMutex` Verwendung eines Objekts zum Steuern der verknüpften Liste kann jeweils nur ein Thread auf die Liste zugreifen.

Um ein `CMutex` Objekt zu `CMutex` verwenden, erstellen Sie das Objekt, wenn es benötigt wird. Geben Sie den Namen des Mutex an, auf den Sie warten möchten, und geben Sie an, dass die Anwendung zunächst Eigentümer des Mutex sein soll. Sie können dann auf den Mutex zugreifen, wenn der Konstruktor zurückkehrt. Rufen Sie [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) auf, wenn Sie mit dem Zugriff auf die gesteuerte Ressource fertig sind.

Eine alternative Methode `CMutex` zum Verwenden von Objekten `CMutex` besteht darin, der Klasse, die Sie steuern möchten, eine Variable des Typs als Datenmember hinzuzufügen. Rufen Sie während der Konstruktion des gesteuerten Objekts den Konstruktor des `CMutex` Datenelements auf, der angibt, ob der Mutex ursprünglich im Besitz des Mutex ist, den Namen des Mutex (wenn er über Prozessgrenzen hinweg verwendet wird) und die gewünschten Sicherheitsattribute.

Um auf diese `CMutex` Weise auf Ressourcen zuzugreifen, die von Objekten gesteuert werden, erstellen Sie zunächst eine Variable vom Typ [CSingleLock](../../mfc/reference/csinglelock-class.md) oder in der Zugriffsmemberfunktion Ihrer Ressource [CMultiLock.](../../mfc/reference/cmultilock-class.md) Rufen Sie dann die `Lock` Memberfunktion des Sperrobjekts auf (z. B. [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). An diesem Punkt erhält der Thread entweder Zugriff auf die Ressource, wartet auf die Freigabe der Ressource und erhält Zugriff, oder er wartet, bis die Ressource freigegeben und eine Zeitauszeit ausgeführt wird, ohne Zugriff auf die Ressource zu erhalten. In jedem Fall wurde auf Ihre Ressource threadsicher zugegriffen. Um die Ressource freizugeben, verwenden `Unlock` Sie die Memberfunktion des Sperrobjekts (z. B. [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), oder lassen Sie zu, dass das Sperrobjekt aus dem Gültigkeitsbereich fällt.

Weitere Informationen zur `CMutex` Verwendung von Objekten finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex

Erstellt ein benanntes `CMutex` oder unbenanntes Objekt.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parameter

*bInitiallyOwn*<br/>
Gibt an, ob `CMutex` der Thread, der das Objekt erstellt, zunächst Zugriff auf die Ressource hat, die vom Mutex gesteuert wird.

*lpszName*<br/>
Name des `CMutex`-Objekts. Wenn ein anderer Mutex mit demselben Namen vorhanden ist, muss *lpszName* angegeben werden, wenn das Objekt über Prozessgrenzen hinweg verwendet wird. Wenn **NULL**, wird der Mutex unbenannt. Wenn der Name mit einem vorhandenen Mutex `CMutex` übereinstimmt, erstellt der Konstruktor ein neues Objekt, das auf den Mutex dieses Namens verweist. Wenn der Name mit einem vorhandenen Synchronisierungsobjekt übereinstimmt, das kein Mutex ist, schlägt die Konstruktion fehl.

*lpsaAttribute*<br/>
Sicherheitsattribute für das mutex-Objekt. Eine vollständige Beschreibung dieser Struktur finden Sie unter [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Um auf ein `CMutex` Objekt zuzugreifen oder es freizugeben, erstellen Sie ein [CMultiLock-](../../mfc/reference/cmultilock-class.md) oder [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) und rufen die [Mitgliedsfunktionen Sperren](../../mfc/reference/csinglelock-class.md#lock) und [Entsperren](../../mfc/reference/csinglelock-class.md#unlock) auf. Wenn `CMutex` das Objekt eigenständig verwendet wird, rufen Sie seine `Unlock` Memberfunktion auf, um es freizugeben.

> [!IMPORTANT]
> Verwenden Sie `CMutex` nach dem Erstellen des Objekts [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) um sicherzustellen, dass der Mutex noch nicht vorhanden ist. Wenn der Mutex unerwartet existierte, kann dies darauf hindeuten, dass ein Nichtautorisiertes Prozess hockt und möglicherweise beabsichtigt, den Mutex böswillig zu verwenden. In diesem Fall wird das empfohlene sicherheitsbewusste Verfahren darin durchgeführt, das Handle zu schließen und so fortzufahren, als ob beim Erstellen des Objekts ein Fehler aufgetreten wäre.

## <a name="see-also"></a>Siehe auch

[CSyncObject-Klasse](../../mfc/reference/csyncobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
