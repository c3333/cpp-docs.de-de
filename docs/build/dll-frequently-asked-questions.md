---
title: Häufig gestellte Fragen zu MFC-DLLs
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422823"
---
# <a name="dll-frequently-asked-questions"></a>FAQ (Häufig gestellte Fragen) zu DLLs

Im Folgenden finden Sie einige häufig gestellte Fragen zu DLLs.

- [Kann eine MFC-DLL mehrere Threads erstellen?](#mfc_multithreaded_1)

- [Kann eine Multithreadanwendung auf eine MFC-DLL in unterschiedlichen Threads zugreifen?](#mfc_multithreaded_2)

- [Gibt es MFC-Klassen oder -Funktionen, die nicht in einer MFC-DLL verwendet werden können?](#mfc_prohibited_classes)

- [Welche Optimierungstechniken sollten verwendet werden, um die Leistung der Clientanwendung beim Laden zu verbessern?](#mfc_optimization)

- [In meiner regulären MFC-DLL gibt es einen Arbeitsspeicherverlust, ich finde aber keine Fehler in meinem Code. Wie finde ich den Grund für den Arbeitsspeicherverlust?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a> Kann eine MFC-DLL mehrere Threads erstellen?

Mit Ausnahme der Initialisierung kann eine MFC-DLL sicher mehrere Threads erstellen, solange die Win32-TLS-Funktionen (threadlokaler Speicher), z. B. **TlsAlloc**, verwendet werden, um threadlokalen Speicher zuzuweisen. Wenn eine MFC-DLL jedoch **__declspec(thread)** verwendet, um threadlokalen Speicher zuzuweisen, muss die Anwendung implizit mit der DLL verknüpft werden. Wenn die Clientanwendung explizit eine Verknüpfung mit der DLL herstellt, lädt der Aufruf für **LoadLibrary** die DLL nicht erfolgreich. Weitere Informationen zu threadlokalen Variablen in DLLs finden Sie unter [thread](../cpp/thread.md).

Eine MFC-DLL, die während des Starts einen neuen MFC-Thread erstellt, antwortet nicht mehr, wenn sie von einer Anwendung geladen wird. Dies beinhaltet Szenarios, in denen ein Thread erstellt wird, indem ein Thread durch Aufruf von `AfxBeginThread` oder `CWinThread::CreateThread` innerhalb der folgenden Funktionen erstellt wird:

- Die `InitInstance`-Funktion eines von `CWinApp` abgeleiteten Objekts in einer regulären MFC-DLL

- Eine bereitgestellte `DllMain`- oder **RawDllMain**-Funktion in einer regulären MFC-DLL

- Eine bereitgestellte `DllMain`- oder **RawDllMain**-Funktion in einer MFC-Erweiterungs-DLL.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a> Kann eine Multithreadanwendung auf eine MFC-DLL in unterschiedlichen Threads zugreifen?

Multithreadanwendungen können auf reguläre MFC-DLLs zugreifen, die eine dynamische Verknüpfung zu MFC- und MFC-Erweiterungs-DLLs in unterschiedlichen Threads herstellen. Eine Anwendung kann auf reguläre MFC-DLLs zugreifen, die eine statische Verknüpfung zu MFC in mehreren Threads herstellen, die in der Anwendung erstellt wurden.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a> Gibt es MFC-Klassen oder -Funktionen, die nicht in einer MFC-DLL verwendet werden können?

Erweiterungs-DLLs verwenden die von `CWinApp` abgeleitete Klasse der Clientanwendung. Sie müssen keine eigene von `CWinApp` abgeleitete Klasse haben.

Reguläre MFC-DLLs müssen wie eine MFC-Anwendung über eine von `CWinApp` abgeleitete Klasse und ein einzelnes Objekt dieser Anwendungsklasse verfügen. Das `CWinApp`-Objekt der DLL muss jedoch nicht wie das `CWinApp`-Objekt einer Anwendung über ein Hauptnachrichtensystem verfügen.

Beachten Sie, dass der `CWinApp::Run`-Mechanismus nicht für eine DLL gilt, da die Anwendung das Hauptnachrichtensystem besitzt. Wenn die DLL Dialogfelder ohne Modus öffnet oder über ein eigenes Hauptrahmenfenster verfügt, muss das Hauptnachrichtensystem der Anwendung eine von der DLL exportierte Routine aufrufen, die wiederum die `CWinApp::PreTranslateMessage`-Memberfunktion des Anwendungsobjekts der DLL aufruft.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a> Welche Optimierungstechniken sollten verwendet werden, um die Leistung der Clientanwendung beim Laden zu verbessern?

Wenn es sich bei Ihrer DLL um eine reguläre MFC-DLL handelt, die statisch mit MFC verknüpft ist, wird die Dateigröße reduziert, wenn sie in eine reguläre MFC-DLL geändert wird, die dynamisch mit MFC verknüpft ist.

Wenn die DLL über eine große Anzahl exportierter Funktionen verfügt, verwenden Sie eine DEF-Datei, um die Funktionen zu exportieren (anstelle von **__declspec(dllexport)** ), und verwenden Sie die DEF-Datei [NONAME attribute](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) für jede exportierte Funktion. Das NONAME-Attribut führt dazu, dass nur der Ordinalwert und nicht der Funktionsname in der Exporttabelle der DLL gespeichert werden. Dies reduziert die Dateigröße.

DLLs, die implizit mit einer Anwendung verknüpft sind, werden beim Laden der Anwendung geladen. Zur Leistungsverbesserung beim Laden können Sie versuchen, die DLL in verschiedene DLLs zu teilen. Verschieben Sie alle Funktionen, die die Anwendung, die den Aufruf durchführt, benötigt, sofort nach dem Ladevorgang in eine DLL, und lassen Sie die aufrufende Anwendung eine implizite Verknüpfung zu dieser DLL herstellen. Verschieben Sie die anderen Funktionen, die die aufrufende Anwendung nicht benötigt, sofort in einer andere DLL, und lassen Sie die Anwendung eine explizite Verknüpfung zu dieser DLL herstellen. Weitere Informationen finden Sie unter [Ermitteln der zu verwendenden Verknüpfungsmethode](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a> In meiner regulären MFC-DLL gibt es einen Arbeitsspeicherverlust, ich finde aber keine Fehler in meinem Code. Wie finde ich den Grund für den Arbeitsspeicherverlust?

Ein möglicher Grund für den Arbeitsspeicherverlust ist, dass MFC temporäre Objekte erstellt, die innerhalb der Meldungshandlerfunktionen verwendet werden. In MFC-Anwendungen werden diese temporären Objekte in der `CWinApp::OnIdle()`-Funktion automatisch bereinigt, die zwischen der Verarbeitung von Nachrichten aufgerufen wird. In MFC-DLLs wird die `OnIdle()`-Funktion jedoch nicht automatisch aufgerufen. Dies hat zur Folge, dass temporäre Objekte nicht automatisch bereinigt werden. Zur Bereinigung temporärer Objekte muss die DLL `OnIdle(1)` regelmäßig explizit aufrufen.

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
