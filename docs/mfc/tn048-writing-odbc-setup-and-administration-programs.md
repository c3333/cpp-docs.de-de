---
title: 'TN048: Schreiben von ODBC-Einrichtungs- und Verwaltungsprogrammen für MFC-Datenbankanwendungen'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365485"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Schreiben von ODBC-Einrichtungs- und Verwaltungsprogrammen für MFC-Datenbankanwendungen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Anwendungen, die MFC-Datenbankklassen verwenden, benötigen ein Setupprogramm, das ODBC-Komponenten installiert. Möglicherweise benötigen sie auch ein ODBC-Verwaltungsprogramm, das Informationen zu den verfügbaren Treibern abruft, Standardtreiber angibt und Datenquellen konfiguriert. Dieser Hinweis beschreibt die Verwendung der ODBC Installer-API zum Schreiben dieser Programme.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>Schreiben eines ODBC-Setupprogramms

Für eine MFC-Datenbankanwendung ist der ODBC Driver Manager (ODBC. DLL) und ODBC-Treiber, um zu Datenquellen gelangen zu können. Viele ODBC-Treiber benötigen außerdem zusätzliche Netzwerk- und Kommunikations-DLLs. Die meisten ODBC-Treiber werden mit einem Setup-Programm ausgeliefert, das die erforderlichen ODBC-Komponenten installiert. Anwendungsentwickler, die MFC-Datenbankklassen verwenden, können:

- Verlassen Sie sich bei der Installation von ODBC-Komponenten auf die treiberspezifischen Setup-Programme. Dies erfordert keine weitere Arbeit seitens des Entwicklers – Sie können einfach das Setup-Programm des Treibers neu verteilen.

- Alternativ können Sie Ihr eigenes Setup-Programm schreiben, das den Treiber-Manager und den Treiber installiert.

Die ODBC-Installations-API kann zum Schreiben anwendungsspezifischer Setupprogramme verwendet werden. Die Funktionen in der Installer-API werden vom ODBC-Installationsprogramm DLL – ODBCINST implementiert. DLL auf 16-Bit-Windows und ODBCCP32. DLL auf Win32. Eine Anwendung `SQLInstallODBC` kann die Installations-DLL aufrufen, in der der ODBC-Treiber-Manager, ODBC-Treiber und alle erforderlichen Übersetzer installiert werden. Anschließend werden die installierten Treiber und Übersetzer im ODBCINST aufzeichnet. INI-Datei (oder die Registrierung, auf NT). `SQLInstallODBC`erfordert den vollständigen Pfad zum ODBC. INF-Datei, die die Liste der zu installierenden Treiber enthält und die Dateien beschreibt, aus denen die einzelnen Treiber bestehen. Es enthält auch ähnliche Informationen über den Treiber-Manager und Übersetzer. Odbc. INF-Dateien werden in der Regel von Treiberentwicklern bereitgestellt.

Ein Programm kann auch einzelne ODBC-Komponenten installieren. Um den Treiber-Manager zu `SQLInstallDriverManager` installieren, ruft ein Programm zuerst in der Installations-DLL auf, um das Zielverzeichnis für den Treiber-Manager abzuverweisen. Dies ist in der Regel das Verzeichnis, in dem sich Windows-DLLs befinden. Das Programm verwendet dann die Informationen im Abschnitt [ODBC Driver Manager] des ODBC. INF-Datei, um den Treiber-Manager und die zugehörigen Dateien vom Installationsdatenträger in dieses Verzeichnis zu kopieren. Um einen einzelnen Treiber zu `SQLInstallDriver` installieren, ruft ein Programm zuerst in der Installations-DLL auf, um die Treiberspezifikation zum ODBCINST hinzuzufügen. INI-Datei (oder die Registrierung, auf NT). `SQLInstallDriver`gibt das Zielverzeichnis des Treibers zurück – in der Regel das Verzeichnis, in dem sich Windows-DLLs befinden. Das Programm verwendet dann die Informationen im Treiberbereich des ODBC. INF-Datei, um die Treiber-DLL und verwandte Dateien vom Installationsdatenträger in dieses Verzeichnis zu kopieren.

Weitere Informationen zu ODBC. INF, ODBCINST. INI und unter Verwendung der Installer-API finden Sie unter ODBC SDK *Programmer es Reference,* Kapitel 19, Installieren von ODBC-Software.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>Schreiben eines ODBC-Administrators

Eine MFC-Datenbankanwendung kann ODBC-Datenquellen auf zwei Arten wie folgt einrichten und konfigurieren:

- Verwenden Sie den ODBC-Administrator (verfügbar als Programm oder als Systemsteuerungselement).

- Erstellen Sie Ein eigenes Programm, um Datenquellen zu konfigurieren.

Ein Programm, das Datenquellen konfiguriert, führt Funktionsaufrufe an die Installations-DLL durch. Die Installations-DLL ruft eine Setup-DLL auf, um eine Datenquelle zu konfigurieren. Für jeden Treiber gibt es eine Setup-DLL. Es kann sich um die Treiber-DLL selbst oder um eine separate DLL handelt. Die Setup-DLL fordert den Benutzer auf, Informationen zu erhalten, die der Treiber für die Verbindung mit der Datenquelle und dem Standardübersetzer benötigt, sofern diese unterstützt werden. Anschließend werden die Installations-DLL- und Windows-APIs aufruft, um diese Informationen im ODBC aufzuzeichnen. INI-Datei (oder Registrierung).

Um ein Dialogfeld anzuzeigen, mit dem ein Benutzer Datenquellen hinzufügen, ändern und löschen kann, ruft ein Programm in der Installations-DLL auf. `SQLManageDataSources` Diese Funktion wird aufgerufen, wenn die Installations-DLL von der Systemsteuerung aufgerufen wird. Zum Hinzufügen, Ändern oder Löschen `SQLManageDataSources` einer `ConfigDSN` Datenquelle werden Aufrufe in der Setup-DLL für den Treiber, der dieser Datenquelle zugeordnet ist, hinzugefügt, geändert oder gelöscht. Zum direkten Hinzufügen, Ändern oder Löschen von `SQLConfigDataSource` Datenquellen ruft ein Programm in der Installations-DLL auf. Das Programm übergibt den Namen der Datenquelle und eine Option, die die zu ergreifende Aktion angibt. `SQLConfigDataSource`ruft `ConfigDSN` in der Setup-DLL auf `SQLConfigDataSource`und übergibt ihm die Argumente von .

Weitere Informationen finden Sie unter ODBC SDK *Programmer es Reference,* Chapter 23, Setup DLL Function Reference, und Chapter 24, Installer DLL Function Reference.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
