---
title: Spezielle CWinApp-Dienste
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
ms.openlocfilehash: 1f5abcdab3eda1304879b122acc8072951a0e6c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363905"
---
# <a name="special-cwinapp-services"></a>Spezielle CWinApp-Dienste

Neben dem Ausführen der Nachrichten Schleife und der Möglichkeit, die Anwendung zu initialisieren und anschließend zu bereinigen, bietet [CWinApp](../mfc/reference/cwinapp-class.md) verschiedene weitere Dienste.

## <a name="shell-registration"></a><a name="_core_shell_registration"></a>Shellregistrierung

Der MFC-Anwendungs-Assistent ermöglicht dem Benutzer standardmäßig das Öffnen von Datendateien, die von der Anwendung erstellt wurden, indem Sie im Datei-Explorer oder Datei-Manager darauf doppelklicken. Wenn es sich bei Ihrer Anwendung um eine MDI-Anwendung handelt und Sie eine Erweiterung für die Dateien angeben, die von der Anwendung erstellt werden, fügt der MFC-Anwendungs-Assistent Aufrufe der [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) -und [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) -Element Funktionen von [CWinApp](../mfc/reference/cwinapp-class.md) an die `InitInstance` Überschreibung an, die Sie für Sie schreibt.

`RegisterShellFileTypes`registriert die Dokumenttypen Ihrer Anwendung im Datei-Explorer oder Datei-Manager. Die-Funktion fügt der Registrierungsdatenbank Einträge hinzu, die von Windows verwaltet werden. Die Einträge registrieren jeden Dokumenttyp, ordnen eine Dateierweiterung dem Dateityp zu, geben eine Befehlszeile zum Öffnen der Anwendung an und geben einen DDE-Befehl (Dynamic Data Exchange) zum Öffnen eines Dokuments dieses Typs an.

`EnableShellOpen`schließt den Prozess ab, indem es Ihrer Anwendung ermöglicht, DDE-Befehle aus dem Datei-Explorer oder Datei-Manager zu empfangen, um die vom Benutzer ausgewählte Datei zu öffnen.

Durch diese automatische Registrierungs Unterstützung `CWinApp` in entfällt die Notwendigkeit, eine REG-Datei mit Ihrer Anwendung zu versenden oder eine besondere Installation durchzuführen.

Wenn Sie GDI+ für Ihre Anwendung initialisieren möchten (durch Aufrufen von [gdipl-Start](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) in der [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) -Funktion), müssen Sie den GDI+-Hintergrund Thread unterdrücken.

Legen Sie hierzu den `SuppressBackgroundThread` Member der [gdipl\startupinput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) -Struktur auf **true**fest. Beim unterdrücken des GDI+-Hintergrundthreads sollten die `NotificationHook` Aufrufe und `NotificationUnhook` unmittelbar vor dem eingeben und Beenden der Nachrichten Schleife der Anwendung vorgenommen werden. Weitere Informationen zu diesen Aufrufen finden Sie unter [gdiplingstartupoutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Ein guter Ausgangspunkt, `GdiplusStartup` und die Hook-Benachrichtigungsfunktionen würden eine Überschreibung der virtuellen Funktion [CWinApp:: Run aufweisen](../mfc/reference/cwinapp-class.md#run), wie unten dargestellt:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Wenn Sie den GDI+-Hintergrund Thread nicht unterdrücken, können DDE-Befehle vorzeitig an die Anwendung ausgegeben werden, bevor das Hauptfenster erstellt wurde. Die von der Shell ausgestellten DDE-Befehle können vorzeitig abgebrochen werden. Dies führt zu Fehlermeldungen.

## <a name="file-manager-drag-and-drop"></a><a name="_core_file_manager_drag_and_drop"></a>Datei-Manager Drag & amp; Drop

Dateien können aus dem Datei Ansichts Fenster im Datei-Manager oder Datei-Explorer in ein Fenster in der Anwendung gezogen werden. Beispielsweise können Sie eine oder mehrere Dateien in das Hauptfenster einer MDI-Anwendung ziehen, in dem die Anwendung die Dateinamen abrufen und untergeordnete MDI-Fenster für diese Dateien öffnen könnte.

Um das ziehen und Ablegen von Dateien in der Anwendung zu aktivieren, schreibt der MFC-Anwendungs-Assistent einen-Befehl in die [CWnd](../mfc/reference/cwnd-class.md) -Member-Funktion [dragakzeptfiles](../mfc/reference/cwnd-class.md#dragacceptfiles) für das Hauptrahmen Fenster in Ihrem `InitInstance`. Sie können diesen Befehl entfernen, wenn Sie die Drag & Drop-Funktion nicht implementieren möchten.

> [!NOTE]
> Außerdem können Sie allgemeinere Drag & Drop-Funktionen implementieren – das Ziehen von Daten zwischen oder innerhalb von Dokumenten – mit OLE. Weitere Informationen finden Sie im Artikel [OLE Drag](../mfc/drag-and-drop-ole.md)& amp; Drop.

## <a name="keeping-track-of-the-most-recently-used-documents"></a><a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Die zuletzt verwendeten Dokumente werden nachverfolgt.

Beim Öffnen und Schließen von Dateien durch den Benutzer werden die vier zuletzt verwendeten Dateien vom Anwendungs Objekt nachverfolgt. Die Namen dieser Dateien werden dem Menü Datei hinzugefügt und aktualisiert, wenn Sie sich ändern. Das Framework speichert diese Dateinamen entweder in der Registrierung oder in der INI-Datei mit dem gleichen Namen wie das Projekt und liest Sie aus der Datei, wenn Ihre Anwendung gestartet wird. Die `InitInstance` außer Kraft setzung, die der MFC-Anwendungs-Assistent für Sie erstellt, beinhaltet einen aufzurufenden [CWinApp](../mfc/reference/cwinapp-class.md) -Member [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), der Informationen aus der Registrierung oder der INI-Datei lädt, einschließlich der zuletzt verwendeten Dateinamen.

Diese Einträge werden wie folgt gespeichert:

- In Windows NT, Windows 2000 und höher, wird der Wert in einem Registrierungsschlüssel gespeichert.

- In Windows 3. x wird der Wert im Win gespeichert. INI-Datei.

- In Windows 95 und höher wird der Wert in einer zwischengespeicherten Version von Win gespeichert. Geleitet.

## <a name="see-also"></a>Weitere Informationen

[CWinApp: Die Anwendungsklasse](../mfc/cwinapp-the-application-class.md)
