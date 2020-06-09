---
title: 'CWinApp: Die Anwendungsklasse'
ms.date: 11/04/2016
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: e8327cf55606131d43201aa1f4f51526bcba147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617066"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: Die Anwendungsklasse

Die Haupt Anwendungsklasse in MFC kapselt die Initialisierung, Ausführung und Beendigung einer Anwendung für das Windows-Betriebssystem. Eine auf dem Framework basierende Anwendung muss nur ein einzelnes Objekt einer Klasse aufweisen, die von [CWinApp](reference/cwinapp-class.md)abgeleitet ist. Dieses Objekt wird erstellt, bevor Fenster erstellt werden.

`CWinApp`wird von abgeleitet `CWinThread` , der den hauptausführungs Thread für die Anwendung darstellt, der möglicherweise über einen oder mehrere Threads verfügt. In den aktuellen Versionen von MFC `InitInstance` sind die-, **Run** `ExitInstance` -,-und-Member- `OnIdle` Funktionen tatsächlich in der-Klasse `CWinThread` . Diese Funktionen werden hier behandelt, als würden Sie stattdessen als Member behandelt werden `CWinApp` , da die Diskussion die Rolle des Objekts als Anwendungs Objekt und nicht als primären Thread behandelt.

> [!NOTE]
> Ihre Anwendungsklasse stellt den primären Ausführungs Thread Ihrer Anwendung dar. Mithilfe der Win32-API-Funktionen können Sie auch sekundäre Ausführungs Threads erstellen. Diese Threads können die MFC-Bibliothek verwenden. Weitere Informationen finden Sie unter [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Wie jedes Programm für das Windows-Betriebssystem verfügt Ihre Framework-Anwendung über eine- `WinMain` Funktion. In einer Framework-Anwendung schreiben Sie jedoch nicht `WinMain` . Sie wird von der Klassenbibliothek bereitgestellt und beim Starten der Anwendung aufgerufen. `WinMain`führt Standarddienste wie das Registrieren von Fenster Klassen aus. Anschließend werden die Element Funktionen des Anwendungs Objekts aufgerufen, um die Anwendung zu initialisieren und auszuführen. (Sie können anpassen `WinMain` , indem Sie die Member-Funktionen überschreiben `CWinApp` , die `WinMain` aufruft.)

Zum Initialisieren der Anwendung `WinMain` Ruft die-und-Member-Funktionen Ihres Anwendungs Objekts auf `InitApplication` `InitInstance` . Um die Nachrichten Schleife der Anwendung auszuführen, `WinMain` Ruft die Funktion **Run** Member auf. Bei Beendigung `WinMain` Ruft die Member-Funktion des Anwendungs Objekts auf `ExitInstance` .

> [!NOTE]
> Die in dieser Dokumentation **Fett** gezeigten Namen geben Elemente an, die vom Microsoft Foundation Class-Bibliothek und Visual C++ bereitgestellt werden. In Typ angezeigte Namen `monospaced` geben Elemente an, die Sie erstellen oder überschreiben.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](general-mfc-topics.md)<br/>
[CWinApp und der MFC-Anwendungs-Assistent](cwinapp-and-the-mfc-application-wizard.md)<br/>
[Überschreibbare CWinApp-Memberfunktionen](overridable-cwinapp-member-functions.md)<br/>
[Spezielle CWinApp-Dienste](special-cwinapp-services.md)
