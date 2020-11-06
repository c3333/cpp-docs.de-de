---
title: Linkertoolfehler LNK1104
description: Beschreibt den Linkerfehler von Microsoft C und C++ (MSVC) LNK1104, seine Ursachen und mögliche Lösungen.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 2eea6885537037db496a2f42e0fff0ffa69127e3
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334207"
---
# <a name="linker-tools-error-lnk1104"></a>Linkertoolfehler LNK1104

> Datei " *Dateiname* " kann nicht geöffnet werden

Dieser Fehler wird gemeldet, wenn der Linker eine Datei zum Lesen oder schreiben nicht öffnen kann. Die beiden häufigsten Gründe für dieses Problem sind:

- Ihr Programm wird bereits ausgeführt oder im Debugger geladen, und

- die Bibliothekspfade sind falsch oder nicht in doppelte Anführungszeichen eingeschlossen.

Es gibt viele weitere mögliche Ursachen für diesen Fehler. Um diese einzugrenzen, überprüfen Sie zunächst, welche Art von Datei *Dateiname* lautet. Verwenden Sie dann die folgenden Abschnitte, um das jeweilige Problem zu identifizieren und zu beheben.

## <a name="cant-open-your-app-or-its-pdb-file"></a>Ihre APP oder die zugehörige PDB-Datei kann nicht geöffnet werden.

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>Ihre APP wird ausgeführt oder im Debugger geladen.

Wenn *filename* der Name der ausführbaren Datei oder eine zugehörige PDB-Datei ist, überprüfen Sie, ob Ihre Anwendung bereits ausgeführt wird. Überprüfen Sie dann, ob es in einem Debugger geladen wurde. Um dieses Problem zu beheben, müssen Sie das Programm vor dem erneuten Aufbau aus dem Debugger entfernen. Wenn die app in einem anderen Programm, z. b. einem Ressourcen-Editor, geöffnet ist, schließen Sie Sie. Wenn das Programm nicht reagiert, müssen Sie möglicherweise den Task-Manager verwenden, um den Prozess zu beenden. Sie müssen möglicherweise auch Visual Studio schließen und neu starten.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>Ihre APP wird durch einen Antivirenscan gesperrt.

Antivirenprogramme blockieren häufig vorübergehend den Zugriff auf neu erstellte Dateien, insbesondere auf ausführbare EXE-und dll-Dateien. Um dieses Problem zu beheben, versuchen Sie, die projektbuildverzeichnisse aus dem Antivirenscanner auszuschließen.

## <a name="cant-open-a-microsoft-library-file"></a>Eine Microsoft-Bibliotheksdatei kann nicht geöffnet werden.

### <a name="windows-libraries-such-as-kernel32lib"></a>Windows-Bibliotheken, z. b. Kernel32. lib

Wenn die Datei, die nicht geöffnet werden kann, eine der Standard Bibliotheksdateien ist, die von Microsoft bereitgestellt werden, z. b *. Kernel32. lib* , liegt möglicherweise ein Projekt Konfigurationsfehler oder ein Installationsfehler vor. Vergewissern Sie sich, dass der Windows SDK installiert wurde. Wenn Ihr Projekt andere Microsoft-Bibliotheken erfordert, wie z. b. MFC, stellen Sie sicher, dass die MFC-Komponenten auch vom Visual Studio-Installer installiert wurden. Sie können das Installationsprogramm erneut ausführen, um jederzeit optionale Komponenten hinzuzufügen. Weitere Informationen finden Sie unter [Ändern von Visual Studio](/visualstudio/install/modify-visual-studio). Verwenden Sie die Registerkarte **einzelne Komponenten** im Installationsprogramm, um bestimmte Bibliotheken und sdert auszuwählen.

### <a name="versioned-vcruntime-libraries"></a>Versionierte vcruntime-Bibliotheken

Wenn die Fehlermeldung eine Microsoft-Bibliothek mit Versions Angabe (z *. b. msvcr120. lib* ) aufweist, ist das Platt Form Toolset für diese Compilerversion möglicherweise nicht installiert. Um dieses Problem zu beheben, haben Sie zwei Möglichkeiten: Aktualisieren Sie das Projekt, um das aktuelle Platt Form Toolset zu verwenden, oder installieren Sie das ältere Toolset, und erstellen Sie das Projekt unverändert. Weitere Informationen finden Sie unter [Aktualisieren von Projekten aus früheren Versionen von Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) und Verwenden von systemeigenen [Ziel Versionen in Visual Studio, um alte Projekte zu erstellen](../../porting/use-native-multi-targeting.md).

### <a name="retail-debug-or-platform-specific-libraries"></a>Einzelhandels-, Debug-oder plattformspezifische Bibliotheken

Der Fehler kann auftreten, wenn Sie erstmalig eine neue Zielplattform oder-Konfiguration erstellen, z. b. "Retail" oder "ARM64". Überprüfen Sie in der IDE, ob das **Platt Form Toolset** und **Windows SDK Version** , die auf der [Eigenschaften Seite Allgemein](../../build/reference/general-property-page-project.md) angegeben sind, installiert sind. Vergewissern Sie sich außerdem, dass die erforderlichen Bibliotheken in den **Bibliotheks Verzeichnissen** verfügbar sind, die auf der [Eigenschaften Seite VC + +-Verzeichnisse](../../build/reference/vcpp-directories-property-page.md)angegeben sind. Überprüfen Sie die Eigenschaften für jede Konfiguration, z. b. Debug, Retail, x86 oder ARM64. Wenn ein Build funktioniert, aber noch nicht, vergleichen Sie die Einstellungen für beide. Installieren Sie fehlende erforderliche Tools und Bibliotheken.

### <a name="the-vccorliblib-library"></a>Die Bibliothek "vccorlib. lib"

Für universelle Windows-Apps (UWP)-Apps oder-Komponenten gibt es keine von Spectre abgeminderten Bibliotheken. Wenn die Fehlermeldung " *vccorlib. lib* " enthält, haben Sie möglicherweise " [/Qspectre](../../build/reference/qspectre.md) " in einem UWP-Projekt aktiviert. Deaktivieren Sie die **/Qspectre** -Compileroption, um dieses Problem zu beheben. Ändern Sie in Visual Studio die Eigenschaft **Spectre-Entschärfung** . Sie befindet sich auf der Seite **C/C++** -  >  **Code Generierung** des Dialog Felds **Eigenschaften Seiten** des Projekts.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>Bibliotheken in Projekten aus Online oder anderen Quellen

Wenn Sie ein Projekt erstellen, das von einem anderen Computer kopiert wurde, können sich die Bibliotheks Installations Pfade unterscheiden. Vergewissern Sie sich bei Befehlszeilenbuilds, dass die lib-Umgebungsvariable und die Bibliothekspfade für den Build ordnungsgemäß festgelegt sind. In Visual Studio können Sie die aktuellen Bibliothekspfade sehen und bearbeiten, die auf den Eigenschaften Seiten für das Projekt festgelegt sind. Wählen Sie auf der Seite **VC + +-Verzeichnisse** das Dropdown-Steuerelement für die Eigenschaft **Bibliotheks Verzeichnisse** aus, und klicken Sie dann auf **Bearbeiten**. Im Abschnitt **ausgewerteter Wert** des Dialog Felds **Bibliotheks Verzeichnisse** werden die aktuellen Pfade aufgelistet, die nach Bibliotheksdateien durchsucht werden. Aktualisieren Sie diese Pfade so, dass Sie auf Ihre lokalen Bibliotheken verweisen.

### <a name="updated-windows-sdk-libraries"></a>Aktualisierte Windows SDK Bibliotheken

Dieser Fehler kann auftreten, wenn der Visual Studio-Pfad zum Windows SDK veraltet ist. Dies kann vorkommen, wenn Sie eine neuere Windows SDK unabhängig vom Visual Studio-Installer installieren. Aktualisieren Sie die Pfade, die auf der [Eigenschaften Seite für VC + +-Verzeichnisse](../../build/reference/vcpp-directories-property-page.md)angegeben sind, um Sie in der IDE zu beheben. Legen Sie die Version im Pfad so fest, dass Sie dem neuen SDK entspricht. Wenn Sie die Developer-Eingabeaufforderung verwenden, aktualisieren Sie die Batchdatei, die die Umgebungsvariablen initialisiert, mit den neuen SDK-Pfaden. Dieses Problem kann vermieden werden, indem Sie mithilfe des Visual Studio-Installers aktualisierte sdche installieren.

## <a name="cant-open-a-third-party-library-file"></a>Eine Drittanbieter-Bibliotheksdatei kann nicht geöffnet werden.

Es gibt verschiedene Häufige Gründe für dieses Problem:

- Der Pfad zu ihrer Bibliotheksdatei ist möglicherweise falsch oder nicht in doppelte Anführungszeichen eingeschlossen. Oder Sie haben Sie möglicherweise nicht für den Linker angegeben.

- Sie haben möglicherweise eine 32-Bit-Version der Bibliothek installiert, aber Sie entwickeln für 64 Bits oder umgekehrt.

- Die Bibliothek kann Abhängigkeiten von anderen Bibliotheken aufweisen, die nicht installiert sind.

Vergewissern Sie sich, dass die lib-Umgebungsvariable festgelegt ist, um ein Pfad Problem für Befehlszeilenbuilds zu beheben. Stellen Sie sicher, dass Sie Pfade für alle Bibliotheken enthält, die Sie verwenden, und für jede Konfiguration, die Sie erstellen. In der IDE werden die Bibliothekspfade von der Eigenschaft " **VC + +-Verzeichnisse** -  >  **Bibliotheks Verzeichnisse** " festgelegt. Stellen Sie sicher, dass alle Verzeichnisse, die die benötigten Bibliotheken enthalten, für jede Konfiguration, die Sie erstellen, hier aufgeführt sind.

Möglicherweise müssen Sie ein Bibliotheksverzeichnis bereitstellen, das ein Standard Bibliotheksverzeichnis überschreibt. Verwenden Sie in der Befehlszeile die Option [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Verwenden Sie in der IDE die Eigenschaft **zusätzliche Bibliotheks Verzeichnisse** auf der **Eigenschaften Seite Konfigurations Eigenschaften > Linker > allgemein** für Ihr Projekt.

Stellen Sie sicher, dass Sie jede Version der Bibliothek installieren, die Sie für die von Ihnen Erstellungs Konfigurationen benötigen. Verwenden Sie ggf. das [vcpkg](../../build/vcpkg.md) -Paket Verwaltungs Hilfsprogramm, um die Installation und Einrichtung für viele gängige Bibliotheken zu automatisieren. Wenn dies möglich ist, sollten Sie Ihre eigenen Kopien von Bibliotheken von Drittanbietern erstellen. Dann sind Sie sicher, dass alle lokalen Abhängigkeiten der Bibliotheken für dieselben Konfigurationen wie für Ihr Projekt erstellt wurden.

## <a name="cant-open-a-file-built-by-your-project"></a>Eine vom Projekt erstellter Datei kann nicht geöffnet werden.

Dieser Fehler wird möglicherweise angezeigt, wenn der *Dateiname* noch nicht vorhanden ist, wenn der Linker versucht, darauf zuzugreifen. Dies kann vorkommen, wenn ein Projekt von einem anderen Projekt in der Projekt Mappe abhängt, die Projekte jedoch in der falschen Reihenfolge erstellt werden. Um dieses Problem zu beheben, stellen Sie sicher, dass die Projekt Verweise im Projekt, das die Datei verwendet, festgelegt werden. Anschließend wird die fehlende Datei erstellt, bevor Sie benötigt wird. Weitere Informationen finden Sie unter [Hinzufügen von Verweisen in Visual Studio C++ Projekte](../../build/adding-references-in-visual-cpp-projects.md) und [Verwalten von Verweisen in einem Projekt](/visualstudio/ide/managing-references-in-a-project).

## <a name="cant-open-file-cprogramobj"></a>Die Datei "C: \\ Program. obj" kann nicht geöffnet werden.

Wenn der Dateiname *C: \\ Program. obj* in der Fehlermeldung angezeigt wird, schließen Sie die Bibliothekspfade in doppelte Anführungszeichen ein. Dieser Fehler tritt auf, wenn ein nicht umschließelter Pfad, der mit *C: \\ Program Files* beginnt, an den Linker übermittelt wird. Nicht umschließende Pfade können auch ähnliche Fehler verursachen. In der Regel wird eine unerwartete obj-Datei im Stammverzeichnis des Laufwerks angezeigt.

Um dieses Problem bei Befehlszeilenbuilds zu beheben, überprüfen Sie die Parameter der [/LIBPATH](../../build/reference/libpath-additional-libpath.md) -Option. Überprüfen Sie außerdem die Pfade, die in der LIB-Umgebungsvariablen angegeben sind, sowie die in der Befehlszeile angegebenen Pfade. Stellen Sie sicher, dass Sie doppelte Anführungszeichen für alle Pfade verwenden, die Leerzeichen enthalten.

Um dieses Problem in der IDE zu beheben, fügen Sie den folgenden Eigenschaften für Ihr Projekt nach Bedarf doppelte Anführungszeichen ein:

- Die Eigenschaft **Bibliotheks Verzeichnisse** auf der [Eigenschaften Seite "Konfigurations Eigenschaften > VC + +-Verzeichnisse](../../build/reference/vcpp-directories-property-page.md) ",

- Die Eigenschaft **zusätzliche Bibliotheks Verzeichnisse** auf der **Eigenschaften Seite Konfigurations Eigenschaften > Linker > allgemein**

- Die Eigenschaft **Zusätzliche Abhängigkeiten** auf der **Eigenschaften Seite Konfigurations Eigenschaften > Linker > Eingabe** .

## <a name="other-common-issues"></a>Andere häufige Probleme

### <a name="path-or-filename-issues"></a>Pfad-oder Dateinamen Probleme

Dieser Fehler kann auftreten, wenn der für den Linker angegebene Dateiname oder Pfad nicht korrekt ist. Oder, wenn der Pfad eine ungültige Laufwerk Spezifikation aufweist. Suchen Sie in der Befehlszeile oder in einer beliebigen #pragma comment-Direktive [(lib, "library_name")](../../preprocessor/comment-c-cpp.md) nach Problemen. Überprüfen Sie die Rechtschreibung und die Dateierweiterung, und vergewissern Sie sich, dass die Datei am angegebenen Speicherort vorhanden ist

### <a name="parallel-build-synchronization"></a>Parallele buildsynchronisierung

Wenn Sie eine parallele Buildoption verwenden, wurde die Datei möglicherweise von Visual Studio in einem anderen Thread gesperrt. Um dieses Problem zu beheben, überprüfen Sie, ob das gleiche Code Objekt oder die gleiche Bibliothek nicht in mehreren Projekten erstellt wurde Verwenden Sie Buildabhängigkeiten oder Projekt Verweise, um die erstellten Binärdateien in Ihrem Projekt auszuwählen.

### <a name="additional-dependencies-specified-in-the-ide"></a>Zusätzliche in der IDE angegebene Abhängigkeiten

Wenn Sie einzelne Bibliotheken direkt in der Eigenschaft **Zusätzliche Abhängigkeiten** angeben, verwenden Sie Leerzeichen, um die Bibliotheksnamen voneinander zu trennen. Verwenden Sie keine Kommas oder Semikolons. Wenn Sie das Menü Element **Bearbeiten** verwenden, um das Dialogfeld **Zusätzliche Abhängigkeiten** zu öffnen, verwenden Sie Zeilenumbrüche, um die Namen, nicht Kommas, Semikolons oder Leerzeichen zu trennen. Verwenden Sie auch Zeilenumbrüche, wenn Sie Bibliothekspfade in den Dialogfeldern **Bibliotheks Verzeichnisse** und **zusätzliche Bibliotheks Verzeichnisse** angeben.

### <a name="paths-that-are-too-long"></a>Pfade, die zu lang sind

Dieser Fehler wird möglicherweise angezeigt, wenn der Pfad für *Dateiname* auf mehr als 260 Zeichen erweitert wird. Ordnen Sie bei Bedarf die Verzeichnisstruktur neu an, oder verkürzen Sie die Ordner-und Dateinamen, um die Pfade zu verkürzen.

### <a name="files-that-are-too-large"></a>Dateien, die zu groß sind

Dieser Fehler kann auftreten, wenn die Datei zu groß ist. Bibliotheken oder Objektdateien mit einer Größe von mehr als Gigabyte können für den 32-Bit-Linker Probleme verursachen. Eine mögliche Lösung für dieses Problem besteht darin, das 64-Bit-Toolset zu verwenden. Weitere Informationen zur Verwendung des 64-Bit-Toolsets in der Befehlszeile finden Sie unter Gewusst [wie: Aktivieren eines 64-Bit-Visual C++ Toolsets in der Befehlszeile](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informationen zur Verwendung des 64-Bit-Toolsets in der IDE finden [Sie unter Verwenden von MSBuild mit dem 64-Bit-Compiler und-Tools](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project). Weitere Informationen finden Sie auch in diesem Stack Overflow Beitrag: [so machen Sie Visual Studio mit der systemeigenen amd64-Toolkette](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

### <a name="incorrect-file-permissions"></a>Falsche Dateiberechtigungen

Dieser Fehler kann auftreten, wenn Sie nicht über ausreichende Dateiberechtigungen für den Zugriff auf *filename* verfügen. Dies kann vorkommen, wenn Sie ein normales Benutzerkonto verwenden, um auf Bibliotheksdateien in geschützten Systemverzeichnissen zuzugreifen. Oder, wenn Sie Dateien verwenden, die von anderen Benutzern kopiert werden, für die noch ihre ursprünglichen Berechtigungen festgelegt sind. Um dieses Problem zu beheben, verschieben Sie die Datei in ein beschreibbares Projektverzeichnis. Wenn die verschoderte Datei nicht auf die Berechtigungen zugreifen kann, führen Sie den takeown.exe Befehl in einem Administrator Befehlsfenster aus, um den Besitz der Datei zu übernehmen.

### <a name="insufficient-disk-space"></a>Nicht genügend Speicherplatz.

Der Fehler kann auftreten, wenn nicht genügend Speicherplatz vorhanden ist. Der Linker verwendet im verschiedenen Fällen temporäre Dateien. Auch wenn Sie über genügend Speicherplatz verfügen, kann ein großer Link den verfügbaren Speicherplatz erschöpft oder fragmentieren. Verwenden Sie die Option [/OPT (Optimierungen)](../../build/reference/opt-optimizations.md) . durch die transitiv Comdat-Eliminierung werden alle Objektdateien mehrmals gelesen.

### <a name="problems-in-the-tmp-environment-variable"></a>Probleme in der TMP-Umgebungsvariablen

Wenn der *Dateiname* den Namen lnk *nnn* hat, handelt es sich um einen vom Linker für eine temporäre Datei generierten Dateinamen. Das in der TMP-Umgebungsvariable angegebene Verzeichnis ist möglicherweise nicht vorhanden. Oder es können mehrere Verzeichnisse für die TMP-Umgebungsvariable angegeben werden. Es muss nur ein Verzeichnispfad für die TMP-Umgebungsvariable angegeben werden.

## <a name="help-my-issue-isnt-listed-here"></a>Hilfe, mein Problem ist hier nicht aufgeführt.

Wenn keines der hier aufgeführten Probleme zutrifft, können Sie die Feedback Tools in Visual Studio verwenden, um Hilfe zu erhalten. Wechseln Sie in der IDE zur Menüleiste, und wählen Sie **Hilfe > Feedback senden > Problem melden**. Oder senden Sie einen Vorschlag mithilfe der **Hilfe > senden Sie Feedback > senden Sie einen Vorschlag**. Sie können auch die [Microsoft-Dokumentation Q&einer](/answers/topics/c%2B%2B.html) Website für Fragen und die Visual Studio C++ [Developer Community](https://aka.ms/vsfeedback/browsecpp) -Website verwenden. Verwenden Sie diese Websites, um nach Antworten auf Fragen zu suchen und Hilfe zu Fragen. Weitere Informationen finden Sie unter [melden eines Problems mit dem Visual C++-Toolset oder der-Dokumentation](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Wenn Sie eine neue Möglichkeit gefunden haben, dieses Problem zu beheben, das wir diesem Artikel hinzufügen sollten, teilen Sie uns dies mit. Sie können uns Feedback senden, indem Sie die Schaltfläche unten für **Diese Seite** verwenden. Verwenden Sie es, um ein neues Problem in unserem [GitHub](https://github.com/MicrosoftDocs/cpp-docs/issues)-Repository in der C++-Dokumentation zu erstellen. Vielen Dank!
