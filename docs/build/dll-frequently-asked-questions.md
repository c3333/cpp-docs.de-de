---
title: Häufig gestellte Fragen zu MFC-DLL
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856949"
---
# <a name="dll-frequently-asked-questions"></a>Häufig gestellte Fragen (FAQs)zu DLLs

Im folgenden finden Sie einige häufig gestellte Fragen (FAQ) zu DLLs.

- [Kann eine MFC-DLL mehrere Threads erstellen?](#mfc_multithreaded_1)

- [Kann eine Multithreadanwendung auf eine MFC-DLL in verschiedenen Threads zugreifen?](#mfc_multithreaded_2)

- [Gibt es MFC-Klassen oder-Funktionen, die nicht in einer MFC-DLL verwendet werden können?](#mfc_prohibited_classes)

- [Welche Optimierungstechniken sollte ich verwenden, um die Leistung der Client Anwendung beim Laden zu verbessern?](#mfc_optimization)

- [In meiner regulären MFC-DLL gibt es einen Speicherplatz, aber mein Code sieht in Ordnung aus. Wie finde ich den Arbeits Speicherplatz?](#memory_leak)

## <a name="mfc_multithreaded_1"></a>Kann eine MFC-DLL mehrere Threads erstellen?

Außer während der Initialisierung kann eine MFC-DLL sicher mehrere Threads erstellen, solange die Win32-Funktionen (Thread Local Storage) wie z. b. **TlsAlloc** zum Zuordnen von lokalem Thread Speicher verwendet werden. Wenn eine MFC-DLL jedoch **__declspec (Thread)** zum Zuordnen von lokalem Thread Speicher verwendet, muss die Client Anwendung implizit mit der DLL verknüpft werden. Wenn die Client Anwendung explizit mit der DLL verknüpft ist, lädt der **LoadLibrary** -Befehl die dll nicht erfolgreich. Weitere Informationen zu lokalen Thread Variablen in DLLs finden Sie unter [Thread](../cpp/thread.md).

Eine MFC-DLL, die während des Starts einen neuen MFC-Thread erstellt, reagiert nicht mehr, wenn Sie von einer Anwendung geladen wird. Dies schließt immer dann ein, wenn ein Thread durch Aufrufen von `AfxBeginThread` oder `CWinThread::CreateThread` in erstellt wird:

- Die `InitInstance` eines von `CWinApp`abgeleiteten Objekts in einer regulären MFC-DLL.

- Ein bereitgestellter `DllMain` oder eine **RawDllMain** -Funktion in einer regulären MFC-DLL.

- Ein bereitgestellter `DllMain` oder eine **RawDllMain** -Funktion in einer MFC-Erweiterungs-DLL.

## <a name="mfc_multithreaded_2"></a>Kann eine Multithreadanwendung auf eine MFC-DLL in verschiedenen Threads zugreifen?

Multithreadanwendungen können auf reguläre MFC-DLLs zugreifen, die dynamisch mit MFC-und MFC-Erweiterungs-DLLs aus unterschiedlichen Threads verknüpft sind. Eine Anwendung kann auf reguläre MFC-DLLs zugreifen, die statisch mit MFC aus mehreren in der Anwendung erstellten Threads verknüpft sind.

## <a name="mfc_prohibited_classes"></a>Gibt es MFC-Klassen oder-Funktionen, die nicht in einer MFC-DLL verwendet werden können?

Erweiterungs-DLLs verwenden die von `CWinApp`abgeleitete Klasse der Client Anwendung. Sie dürfen nicht über eine eigene `CWinApp`abgeleitete Klasse verfügen.

Reguläre MFC-DLLs müssen über eine `CWinApp`abgeleitete Klasse und ein einzelnes Objekt dieser Anwendungsklasse verfügen, ebenso wie eine MFC-Anwendung. Im Gegensatz zum `CWinApp` Objekt einer Anwendung weist das `CWinApp`-Objekt der dll keine hauptnachrichtenpump auf.

Beachten Sie, dass die Anwendung das hauptnachrichtenpump besitzt, da der `CWinApp::Run` Mechanismus nicht für eine DLL gilt. Wenn die dll nicht modlose Dialogfelder öffnet oder über ein eigenes Hauptrahmen Fenster verfügt, muss die hauptnachrichtenpump der Anwendung eine von der dll exportierte Routine aufrufen, die wiederum die `CWinApp::PreTranslateMessage` Member-Funktion des Anwendungs Objekts der DLL aufruft.

## <a name="mfc_optimization"></a>Welche Optimierungstechniken sollte ich verwenden, um die Leistung der&#39;Client Anwendung beim Laden zu verbessern?

Wenn die DLL eine reguläre MFC-DLL ist, die statisch mit MFC verknüpft ist, wird durch das Ändern in eine reguläre MFC-DLL, die dynamisch mit MFC verknüpft ist, die Dateigröße reduziert.

Wenn die dll über eine große Anzahl von exportierten Funktionen verfügt, verwenden Sie eine DEF-Datei, um die Funktionen (statt **__declspec (dllexport)** ) zu exportieren, und verwenden Sie für jede exportierte Funktion das [Noname-Attribut](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) der Datei. def. Das NONAME-Attribut bewirkt, dass nur der Ordinalwert und nicht der Funktionsname in der Export Tabelle der dll gespeichert wird, wodurch die Dateigröße verringert wird.

DLLs, die implizit mit einer Anwendung verknüpft sind, werden geladen, wenn die Anwendung geladen wird. Um die Leistung beim Laden zu verbessern, versuchen Sie, die dll in verschiedene DLLs aufzuteilen. Fügen Sie alle Funktionen, die die aufrufende Anwendung benötigt, unmittelbar nach dem Laden in eine DLL ein, und lassen Sie die aufrufende Anwendung implizit mit dieser DLL verknüpfen. Fügen Sie die anderen Funktionen, die die aufrufenden Anwendung nicht benötigt, direkt in eine andere dll ein, und lassen Sie die Anwendung explizit mit dieser DLL verknüpfen. Weitere Informationen finden Sie unter [Verknüpfen einer ausführbaren Datei mit einer DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a>In&#39;meiner regulären MFC-DLL gibt es einen Speicherplatz, aber mein Code sieht in Ordnung aus. Wie finde ich den Arbeits Speicherplatz?

Eine mögliche Ursache des Speicherlecks ist, dass MFC temporäre Objekte erstellt, die in nachrichtenhandlerfunktionen verwendet werden. In MFC-Anwendungen werden diese temporären Objekte automatisch in der `CWinApp::OnIdle()`-Funktion bereinigt, die zwischen Nachrichtenverarbeitung aufgerufen wird. In MFC-DLLs (Dynamic-Link Libraries) wird die `OnIdle()`-Funktion jedoch nicht automatisch aufgerufen. Folglich werden temporäre Objekte nicht automatisch bereinigt. Um temporäre Objekte zu bereinigen, muss die dll `OnIdle(1)` in regelmäßigen Abständen explizit aufgerufen werden.

## <a name="see-also"></a>Weitere Informationen

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
