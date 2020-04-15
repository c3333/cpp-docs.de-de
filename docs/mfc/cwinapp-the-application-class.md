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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373521"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: Die Anwendungsklasse

Die Hauptanwendungsklasse in MFC kapselt die Initialisierung, Ausführung und Beendigung einer Anwendung für das Windows-Betriebssystem. Eine auf dem Framework basierende Anwendung muss über ein und nur ein Objekt einer von [CWinApp](../mfc/reference/cwinapp-class.md)abgeleiteten Klasse verfügen. Dieses Objekt wird erstellt, bevor Fenster erstellt werden.

`CWinApp`wird von `CWinThread`abgeleitet, der den Hauptthread der Ausführung für Ihre Anwendung darstellt, die möglicherweise über einen oder mehrere Threads verfügen. In neueren Versionen von `InitInstance`MFC `ExitInstance`sind `OnIdle` die Funktionen , `CWinThread` **Ausführen**, und Member funktionen tatsächlich in der Klasse . Diese Funktionen werden hier so `CWinApp` diskutiert, als wären sie stattdessen Mitglieder, da die Diskussion die Rolle des Objekts als Anwendungsobjekt und nicht als Primärthread betrifft.

> [!NOTE]
> Ihre Anwendungsklasse stellt den primären Ausführungsthread Ihrer Anwendung dar. Mit Win32-API-Funktionen können Sie auch sekundäre Ausführungsthreads erstellen. Diese Threads können die MFC-Bibliothek verwenden. Weitere Informationen finden Sie unter [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Wie jedes Programm für das Windows-Betriebssystem `WinMain` hat Auch Ihre Frameworkanwendung eine Funktion. In einer Frameworkanwendung schreiben `WinMain`Sie jedoch nicht . Sie wird von der Klassenbibliothek bereitgestellt und beim Starten der Anwendung aufgerufen. `WinMain`Standarddienste wie das Registrieren von Fensterklassen. Anschließend werden Memberfunktionen des Anwendungsobjekts aufausgeführt, um die Anwendung zu initialisieren und auszuführen. (Sie können `WinMain` dies `CWinApp` anpassen, `WinMain` indem Sie die Memberfunktionen überschreiben, die aufrufen.)

Um die Anwendung `WinMain` zu initialisieren, `InitApplication` werden `InitInstance` die Anwendungsobjekt- und Memberfunktionen des Anwendungsobjekts aufaufrufet. Um die Nachrichtenschleife der `WinMain` Anwendung auszuführen, ruft die **Funktion Member ausführen** auf. `WinMain` Ruft bei Beendigung die Memberfunktion des Anwendungsobjekts `ExitInstance` auf.

> [!NOTE]
> Die in dieser Dokumentation **fett dargestellten** Namen geben Elemente an, die von der Microsoft Foundation-Klassenbibliothek und Visual C++ bereitgestellt werden. Im `monospaced` Typ angezeigte Namen geben Elemente an, die Sie erstellen oder überschreiben.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)<br/>
[CWinApp und der MFC-Anwendungs-Assistent](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Überschreibbare CWinApp-Memberfunktionen](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Spezielle CWinApp-Dienste](../mfc/special-cwinapp-services.md)
