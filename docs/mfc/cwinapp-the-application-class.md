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
ms.openlocfilehash: 8518e21a9fa6bcf5ac640cff25b17c5028046b06
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447023"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: Die Anwendungsklasse

Die Haupt Anwendungsklasse in MFC kapselt die Initialisierung, Ausführung und Beendigung einer Anwendung für das Windows-Betriebssystem. Eine auf dem Framework basierende Anwendung muss nur ein einzelnes Objekt einer Klasse aufweisen, die von [CWinApp](../mfc/reference/cwinapp-class.md)abgeleitet ist. Dieses Objekt wird erstellt, bevor Fenster erstellt werden.

`CWinApp` wird von `CWinThread`abgeleitet, die den hauptausführungs Thread für die Anwendung darstellt, der möglicherweise über einen oder mehrere Threads verfügt. In den aktuellen Versionen von MFC sind die `InitInstance`-, **Run**-, `ExitInstance`-und `OnIdle` Member-Funktionen tatsächlich in der Klasse `CWinThread`. Diese Funktionen werden hier behandelt, als würden Sie stattdessen `CWinApp` Member, denn die Diskussion bezieht sich auf die Rolle des Objekts als Anwendungs Objekt und nicht als primären Thread.

> [!NOTE]
>  Ihre Anwendungsklasse stellt den primären Ausführungs Thread Ihrer Anwendung dar. Mithilfe der Win32-API-Funktionen können Sie auch sekundäre Ausführungs Threads erstellen. Diese Threads können die MFC-Bibliothek verwenden. Weitere Informationen finden Sie unter [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Wie jedes Programm für das Windows-Betriebssystem verfügt Ihre Framework-Anwendung über eine `WinMain` Funktion. In einer Framework-Anwendung schreiben Sie jedoch keine `WinMain`. Sie wird von der Klassenbibliothek bereitgestellt und beim Starten der Anwendung aufgerufen. `WinMain` führt Standarddienste wie das Registrieren von Fenster Klassen aus. Anschließend werden die Element Funktionen des Anwendungs Objekts aufgerufen, um die Anwendung zu initialisieren und auszuführen. (Sie können `WinMain` anpassen, indem Sie die `CWinApp` Member-Funktionen überschreiben, die von `WinMain` aufgerufen werden.)

Zum Initialisieren der Anwendung ruft `WinMain` die `InitApplication`-und `InitInstance` Member-Funktionen Ihres Anwendungs Objekts auf. Um die Nachrichten Schleife der Anwendung auszuführen, ruft `WinMain` die Funktion **Run** Member auf. Bei Beendigung ruft `WinMain` die `ExitInstance` Member-Funktion des Anwendungs Objekts auf.

> [!NOTE]
>  Die in dieser Dokumentation **Fett** gezeigten Namen geben Elemente an, die von der Microsoft Foundation Class-Bibliothek C++und der Visualisierung bereitgestellt werden. In `monospaced` Typ angezeigte Namen geben Elemente an, die Sie erstellen oder überschreiben.

## <a name="see-also"></a>Weitere Informationen

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)<br/>
[CWinApp und der MFC-Anwendungs-Assistent](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Überschreibbare CWinApp-Memberfunktionen](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Spezielle CWinApp-Dienste](../mfc/special-cwinapp-services.md)
