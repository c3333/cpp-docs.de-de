---
title: Registrierung
ms.date: 11/04/2016
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
ms.openlocfilehash: 82411e53620e92eff3484f7d3f7955030fd439ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372841"
---
# <a name="registration"></a>Registrierung

Wenn ein Benutzer ein OLE-Element in eine Anwendung einfügen möchte, stellt OLE eine Liste der Objekttypen zur Auswahl. OLE ruft diese Liste aus der Systemregistrierungsdatenbank ab, die Informationen enthält, die von allen Serveranwendungen bereitgestellt werden. Wenn sich ein Server selbst registriert, beschreiben die Einträge, die er in die Systemregistrierungsdatenbank (die Registrierung) eingibt, unter anderem jeden Von-Objekt-Typ, den er bereitstellt, Dateierweiterungen und den Pfad zu sich selbst.

Das Framework und die Ole-System-Dynamic-Link-Bibliotheken (DLL) verwenden diese Registrierung, um zu bestimmen, welche Typen von OLE-Elementen auf dem System verfügbar sind. Die OLE-System-DLLs verwenden diese Registrierung auch, um zu bestimmen, wie eine Serveranwendung gestartet wird, wenn ein verknüpftes oder eingebettetes Objekt aktiviert wird.

In diesem Artikel wird beschrieben, was jede Serveranwendung tun muss, wenn sie installiert wird und bei jeder Ausführung.

Ausführliche Informationen zur Systemregistrierungsdatenbank und zum Format der zu ihrer Aktualisierung verwendeten .reg-Dateien finden Sie in der *Referenz des OLE-Programmierers*.

## <a name="server-installation"></a><a name="_core_server_installation"></a>Serverinstallation

Wenn Sie Ihre Serveranwendung zum ersten Mal installieren, sollte sie alle Typen von OLE-Elementen registrieren, die sie unterstützt. Sie können den Server auch jedes Mal aktualisieren lassen, wenn er als eigenständige Anwendung ausgeführt wird. Dadurch wird die Registrierungsdatenbank auf dem neuesten Stand, wenn die ausführbare Datei des Servers verschoben wird.

> [!NOTE]
> MFC-Anwendungen, die vom Anwendungsassistenten generiert werden, registrieren sich automatisch selbst, wenn sie als eigenständige Anwendungen ausgeführt werden.

Wenn Sie Ihre Anwendung während der Installation registrieren möchten, verwenden Sie das Programm RegEdit.exe. Wenn Sie ihrer Anwendung ein Setupprogramm beifügen, führen Sie das Setupprogramm "RegEdit /S *appname*.reg" aus. (Das /S-Flag zeigt einen stillen Vorgang an, d. h., es zeigt das Dialogfeld nicht an, in dem der erfolgreiche Abschluss des Befehls gemeldet wird.) Weisen Sie andernfalls den Benutzer an, RegEdit manuell auszuführen.

> [!NOTE]
> Die vom Anwendungsassistenten erstellte .reg-Datei enthält nicht den vollständigen Pfad für die ausführbare Datei. Das Installationsprogramm muss entweder die .reg-Datei so ändern, dass sie den vollständigen Pfad zur ausführbaren Datei enthält, oder die PATH-Umgebungsvariable so ändern, dass sie das Installationsverzeichnis enthält.

RegEdit führt den Inhalt der .reg-Textdatei in der Registrierungsdatenbank zusammen. Verwenden Sie den Registrierungseditor, um die Datenbank zu überprüfen oder zu reparieren. Achten Sie darauf, wesentliche OLE-Einträge nicht zu löschen.

## <a name="server-initialization"></a><a name="_core_server_initialization"></a>Serverinitialisierung

Wenn Sie eine Serveranwendung mit dem Anwendungsassistenten erstellen, führt der Assistent alle Initialisierungsaufgaben automatisch aus. In diesem Abschnitt wird beschrieben, was Sie tun müssen, wenn Sie eine Serveranwendung manuell schreiben.

Wenn eine Serveranwendung von einer Containeranwendung gestartet wird, fügen die OLE-System-DLLs der Befehlszeile des Servers die Option "/Embedding" hinzu. Das Verhalten einer Serveranwendung unterscheidet sich je nachdem, ob sie von einem Container gestartet wurde, daher ist das erste, was eine Anwendung tun sollte, wenn sie mit der Ausführung beginnt, die Option "/Embedding" oder "-Embedding" in der Befehlszeile. Wenn dieser Switch vorhanden ist, laden Sie einen anderen Satz von Ressourcen, die den Server entweder als aktiv oder vollständig geöffnet anzeigen. Weitere Informationen finden Sie unter [Menüs und Ressourcen: Servererweiterungen](../mfc/menus-and-resources-server-additions.md).

Ihre Serveranwendung sollte `CWinApp::RunEmbedded` auch ihre Funktion aufrufen, um die Befehlszeile zu analysieren. Wenn ein Wert ungleich Null zurückgegeben wird, sollte die Anwendung ihr Fenster nicht anzeigen, da es von einer Containeranwendung ausgeführt wurde, nicht als eigenständige Anwendung. Diese Funktion aktualisiert den Eintrag des Servers in `RegisterAll` der Systemregistrierungsdatenbank und ruft die Memberfunktion für Sie auf, indem sie die Instanzregistrierung durchführt.

Wenn Ihre Serveranwendung gestartet wird, müssen Sie sicherstellen, dass sie die Instance-Registrierung durchführen kann. Die Instanzregistrierung informiert die OLE-System-DLLs, dass der Server aktiv ist und zum Empfangen von Anforderungen von Containern bereit ist. Es wird kein Eintrag zur Registrierungsdatenbank hinzugefügt. Führen Sie die Instanzregistrierung `ConnectTemplate` des Servers `COleTemplateServer`durch, indem Sie die member-Funktion aufrufen, die durch definiert ist. Dadurch wird `CDocTemplate` das `COleTemplateServer` Objekt mit dem Objekt verbunden.

Die `ConnectTemplate` Funktion verwendet drei Parameter: die *CLSID*des `CDocTemplate` Servers , einen Zeiger auf das Objekt und ein Flag, das angibt, ob der Server mehrere Instanzen unterstützt. Ein Miniserver muss in der Lage sein, mehrere Instanzen zu unterstützen, d. h., es muss möglich sein, dass mehrere Instanzen des Servers gleichzeitig ausgeführt werden können, eine für jeden Container. Übergeben Sie **daher TRUE** für dieses Flag, wenn Sie einen Miniserver starten.

Wenn Sie einen Miniserver schreiben, wird er per Definition immer von einem Container gestartet. Sie sollten die Befehlszeile dennoch analysieren, um nach der Option "/Embedding" zu suchen. Das Fehlen dieser Option in der Befehlszeile bedeutet, dass der Benutzer versucht hat, den Miniserver als eigenständige Anwendung zu starten. Registrieren Sie in diesem Fall den Server bei der Systemregistrierungsdatenbank, und zeigen Sie dann ein Meldungsfeld an, in dem der Benutzer darüber informiert wird, den Miniserver von einer Containeranwendung aus zu starten.

## <a name="see-also"></a>Siehe auch

[OLE](../mfc/ole-in-mfc.md)<br/>
[Server](../mfc/servers.md)<br/>
[CWinApp::RunAutomatisiert](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer-Klasse](../mfc/reference/coletemplateserver-class.md)
