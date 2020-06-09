---
title: Klassen zur Anwendungs- und Threadunterstützung
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 7e64cc50a121f457b7e32e0ed549db2fa9950843
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619441"
---
# <a name="application-and-thread-support-classes"></a>Klassen zur Anwendungs- und Threadunterstützung

Jede Anwendung verfügt über genau ein Anwendungs Objekt. Dieses Objekt koordiniert andere Objekte im laufenden Programm und wird von abgeleitet `CWinApp` .

Die MFC-Bibliothek (Microsoft Foundation Class) unterstützt mehrere Ausführungs Threads innerhalb einer Anwendung. Alle Anwendungen müssen über mindestens einen Thread verfügen. der Thread, der vom- `CWinApp` Objekt verwendet wird, ist dieser primäre Thread.

`CWinThread`kapselt einen Teil der Threading Funktionen des Betriebssystems. Um die Verwendung mehrerer Threads zu vereinfachen, stellt MFC auch Synchronisierungs Objektklassen bereit, um eine C++-Schnittstelle für Win32-Synchronisierungs Objekte bereitzustellen.

## <a name="application-and-thread-classes"></a>Anwendungs-und Thread Klassen

[CWinApp](reference/cwinapp-class.md)<br/>
Kapselt den Code zum Initialisieren, ausführen und Beenden der Anwendung. Sie leiten das Anwendungs Objekt von dieser Klasse ab.

[CWinThread](reference/cwinthread-class.md)<br/>
Die Basisklasse für alle Threads. Verwenden Sie direkt, oder leiten Sie eine Klasse von ab, `CWinThread` Wenn Ihr Thread Benutzeroberflächen Funktionen ausführt. `CWinApp` wird von `CWinThread` abgeleitet.

## <a name="synchronization-object-classes"></a>Synchronisierungs Objektklassen

[CSyncObject](reference/csyncobject-class.md)<br/>
Basisklasse der Synchronisierungs Objektklassen.

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
Eine Synchronisierungs Klasse, die nur einem Thread innerhalb eines einzelnen Prozesses ermöglicht, auf ein Objekt zuzugreifen.

[CSemaphore](reference/csemaphore-class.md)<br/>
Eine Synchronisierungs Klasse, die zwischen einer und einer angegebenen maximalen Anzahl gleichzeitiger Zugriffe auf ein Objekt zulässt.

[CMutex](reference/cmutex-class.md)<br/>
Eine Synchronisierungs Klasse, die nur einen Thread innerhalb einer beliebigen Anzahl von Prozessen für den Zugriff auf ein Objekt zulässt.

[CEvent](reference/cevent-class.md)<br/>
Eine Synchronisierungs Klasse, die eine Anwendung benachrichtigt, wenn ein Ereignis aufgetreten ist.

[CSingleLock](reference/csinglelock-class.md)<br/>
Wird in Member-Funktionen von Thread sicheren Klassen verwendet, um ein Synchronisierungs Objekt zu sperren.

[CMultiLock](reference/cmultilock-class.md)<br/>
Wird in Member-Funktionen von Thread sicheren Klassen verwendet, um ein oder mehrere Synchronisierungs Objekte aus einem Array von Synchronisierungs Objekten zu sperren.

## <a name="related-classes"></a>Verwandte Klassen

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
Analysiert die Befehlszeile, mit der das Programm gestartet wurde.

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
Versetzt einen Warte Cursor auf den Bildschirm. Wird bei langwierigen Vorgängen verwendet.

[CDockState](reference/cdockstate-class.md)<br/>
Behandelt persistente Speicherung von Andock Zustandsdaten für Steuer leisten.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Verwaltet die zuletzt verwendete Datei Liste (MRU).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
