---
title: 'Leitfaden zum Portieren: MFC Scribble'
ms.date: 10/23/2019
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: 789d29effeea76045a4a10fbca19f20d06778f7c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076965"
---
# <a name="porting-guide-mfc-scribble"></a>Leitfaden zum Portieren: MFC Scribble

Dieses Thema ist das erste von mehreren Themen, in denen der Upgradevorgang für C++-Projekte in Visual Studio auf Visual Studio 2017 vorgestellt wird, die in älteren Versionen von Visual Studio erstellt wurden. Diese Themen stellen den Aktualisierungsvorgang durch Beispiele vor, beginnend mit einem sehr einfachen Projekt, um danach mit etwas komplexeren fortzufahren. In diesem Abschnitt arbeiten wir uns durch den Aktualisierungsvorgang für ein bestimmtes Projekt, MFC Scribble. Es eignet sich als grundlegende Einführung in den Aktualisierungsvorgang für C++-Projekte.

In jeder Version von Visual Studio gibt es mögliche Inkompatibilitäten, die das Verschieben von Code aus einer älteren Version von Visual Studio in eine neuere erschweren können. Manchmal sind die erforderlichen Änderungen im Code, sodass Sie den Code erneut kompilieren und aktualisieren müssen, und manchmal betreffen die erforderlichen Änderungen die Projektdateien. Wenn Sie ein Projekt öffnen, das mit einer früheren Version von Visual Studio erstellt wurde, fragt Sie Visual Studio automatisch, ob ein Projekt oder eine Projektmappe auf die neueste Version aktualisiert werden soll. Diese Tools aktualisieren in der Regel nur die Projektdateien. Sie ändern nicht den Quellcode.

## <a name="mfc-scribble"></a>MFC Scribble

MFC Scribble ist ein bekanntes Beispiel, das in vielen verschiedenen Versionen von Visual C++ eingeschlossen wurde. Es handelt sich dabei um eine einfache Zeichenanwendung, die einige der grundlegenden Funktionen von MFC veranschaulicht. Es gibt davon verschiedene Versionen, u. a. in verwaltetem und nativem Code. In diesem Beispiel haben wir eine alte Version von Scribble in nativem Code aus Visual Studio 2005 gefunden und in Visual Studio 2017 geöffnet.

Vergewissern Sie sich vor der Aktualisierung, dass die Arbeitsauslastung „Windows Desktop“ installiert ist. Öffnen Sie den Visual Studio-Installer (vs_installer.exe). Sie können den Installer beispielsweise öffnen, indem Sie auf **Datei** > **Neues Projekt** klicken und zum Ende der Liste installierter Vorlagen scrollen, bis **Visual Studio-Installer öffnen** angezeigt wird. Nach Öffnen des Installers sehen Sie alle verfügbaren Arbeitsauslastungen. Wenn das Kontrollkästchen für die Workload **Windows-Desktop** nicht ausgewählt ist, wählen Sie es aus, und klicken Sie unten im Fenster auf **Ändern**.

Sichern Sie als Nächstes die Projektmappe samt Inhalt.

Öffnen Sie abschließend die Projekt Mappe in der aktuellen Version von Visual Studio, und lassen Sie den Assistenten das Konvertieren des Projekts zu.

Beachten Sie, dass Sie devenv auch in der Befehlszeile mithilfe der `/Upgrade`-Option ausführen können, anstatt den Assistenten zum Aktualisieren von Projekten zu verwenden. Siehe [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Das kann hilfreich bei der Automatisierung des Aktualisierungsvorgangs für eine große Anzahl von Projekten sein.

### <a name="step-1-converting-the-project-file"></a>Schritt 1: Konvertieren der Projektdatei

Wenn Sie eine alte Projektdatei in Visual Studio öffnen, bietet Visual Studio das Konvertieren der Projektdatei in die aktuellste Version an, die wir akzeptiert haben. Das folgende Dialogfeld wurde angezeigt:

![Überprüfen von Projekt-und Lösungs Änderungen](../porting/media/scribbleprojectupgrade.PNG "Projekt- und Projektmappenänderungen überprüfen")

Es ist ein Fehler aufgetreten, der uns darüber informiert, dass das Itanium-Ziel nicht verfügbar ist und nicht konvertiert wird.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

Zu dem Zeitpunkt, als das vorherige Scribble-Projekt erstellt wurde, war Itanium eine wichtige Zielplattform. Die Windows-Plattform unterstützt Itanium nicht mehr, daher wählen wir aus, ohne Unterstützung der Itanium-Plattform fortzufahren.

Visual Studio hat dann einen Migrationsbericht mit einer Liste aller Probleme der alten Projektdatei angezeigt.

![Upgradebericht](../porting/media/scribblemigrationreport.PNG "Upgradebericht")

In diesem Fall waren alle Probleme Warnungen, und Visual Studio hat die entsprechenden Änderungen in der Projektdatei vorgenommen. Der große Unterschied hinsichtlich des Projekts liegt darin, dass das Buildtool von vcbuild in msbuild geändert wurde. Diese Änderung wurde in Visual Studio 2010 eingeführt. Weitere Änderungen umfassen u. a. eine Neuanordnung der Elementreihenfolge in der Projektdatei selbst. Keines der Probleme bedurfte für dieses einfache Projekt weiterer Aufmerksamkeit.

### <a name="step-2-getting-it-to-build"></a>Schritt 2: Erstellen des Projekts

Vor der Erstellung überprüfen wir das Plattformtoolset, damit wir wissen, welche Compilerversion das Projektsystem verwendet. Sehen Sie sich im Dialogfeld „Projekteigenschaften“ unter **Konfigurationseigenschaften** in der Kategorie **Allgemein** die Eigenschaft **Plattformtoolset** an. Sie enthält die Version von Visual Studio und die Versionsnummer des Plattformtools, in diesem Fall v141 für die Visual Studio 2017-Version der Tools. Wenn Sie ein Projekt konvertieren, das ursprünglich mit Visual Studio 2010, 2012, 2013 oder 2015 kompiliert wurde, wird das Toolset nicht automatisch auf das neueste Toolset aktualisiert.

Für den Wechsel zu Unicode öffnen Sie die Projekteigenschaften unter **Konfigurationseigenschaften**, wählen den Abschnitt **Allgemein** aus und suchen die Eigenschaft **Zeichensatz**. Ändern Sie sie von **Multibyte-Zeichensatz verwenden** in **Unicode-Zeichensatz** verwenden. Als Auswirkung dieser Änderung sind jetzt die Makros _UNICODE und UNICODE definiert, _MBCS aber nicht, was Sie im Eigenschaftendialogfeld unter der Kategorie **C/C++** der Eigenschaft **Befehlszeile** überprüfen können.

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

Obwohl das Scribble-Projekt nicht für die Kompilierung mit Unicode-Zeichen eingerichtet wurde, wurde es bereits mit TCHAR anstelle von char geschrieben, sodass nichts tatsächlich geändert werden muss. Das Projekt wird erfolgreich mit dem Unicode-Zeichensatz erstellt.

Erstellen Sie nun die Projektmappe. Im Ausgabefenster gibt der Compiler in etwa folgendermaßen an, dass _WINNT32_WINNT nicht definiert ist:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Dies ist eine Warnung, kein Fehler, und kommt sehr häufig vor, wenn ein C++-Projekt in Visual Studio aktualisiert wird. Dies ist das Makro, das die niedrigste Version von Windows definiert, auf der Ihre Anwendung ausgeführt werden kann. Wenn wir die Warnung ignorieren, akzeptieren wir den Standardwert _WIN32_WINNT_MAXVER, d. h. die aktuelle Version von Windows. Eine Tabelle der möglichen Werte finden Sie unter [Verwenden der Windows-Header](/windows/win32/WinProg/using-the-windows-headers). Beispielsweise können wir ihre Ausführung auf eine beliebige Version ab Vista festlegen.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Wenn der Code Teile der Windows-API verwendet, die nicht in der Version von Windows verfügbar sind, die Sie mit diesem Makro angeben, sollte das als Compilerfehler angezeigt werden. Im Fall des Scribble-Codes gibt es keinen Fehler.

### <a name="step-3-testing-and-debugging"></a>Schritt 3: Testen und Debuggen

Es gibt keine Testsammlung, daher haben wir die App einfach gestartet und ihre Funktionen manuell über die Benutzeroberfläche getestet. Es wurden keine Probleme festgestellt.

### <a name="step-4-improve-the-code"></a>Schritt 4. Verbessern des Codes

Nach der Migration zu Visual Studio 2017 möchten Sie u.U. einige Änderungen vornehmen, um neue C++-Features zu nutzen. Die aktuelle Version des C++-Compilers entspricht viel mehr dem C++-Standard als ältere Versionen. Wenn Sie also Codeänderungen vornehmen möchten, um den Code sicherer und besser portierbar für andere Compiler und Betriebssysteme zu machen, sollten Sie einige Verbesserungen vornehmen.

## <a name="next-steps"></a>Nächste Schritte

Scribble war eine kleine und einfache Windows-Desktopanwendung, bei der Konvertierungen einfach waren. Viele kleine, einfache Anwendungen können genauso einfach in die neue Version konvertiert werden.  Für komplexere Anwendungen mit viel mehr Codezeilen, für älteren Legacycode, der möglicherweise nicht den modernen technischen Standards entspricht, für mehrere Projekte und Bibliotheken, benutzerdefinierte Buildschritte oder für komplexe geskriptete automatische Builds ist die Aktualisierung zeitaufwendiger. Fahren Sie mit dem [nächsten Beispiel](../porting/porting-guide-com-spy.md) fort, einer ATL/COM-Anwendung namens COM Spy.

## <a name="see-also"></a>Weitere Informationen

[Portieren und Aktualisieren: Beispiele und Fallstudien](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Nächstes Beispiel: COM Spy](../porting/porting-guide-com-spy.md)
