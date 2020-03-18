---
title: 'vcpkg: ein C++-Paket-Manager für Windows, Linux und macOS'
description: vcpkg ist ein Befehlszeilen-Paket-Manager, der den Erwerb und die Installation von Open Source-C++-Bibliotheken für Windows, MacOS und Linux erheblich vereinfacht.
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 7c3dddd62a66c746d92d2f931b97e354ee27d75f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422757"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: ein C++-Paket-Manager für Windows, Linux und macOS

vcpkg ist ein Befehlszeilen-Paket-Manager für C++. Er vereinfacht den Erwerb und die Installation von Drittanbieterbibliotheken für Windows, Linux und macOS erheblich. Wenn Ihr Projekt Drittanbieterbibliotheken verwendet, wird empfohlen, dass Sie vcpkg verwenden, um diese zu installieren. Vcpkg unterstützt sowohl Open Source- als auch proprietäre Bibliotheken. Alle Bibliotheken im vcpkg-Windows-Katalog wurden auf ihre Kompatibilität mit Visual Studio 2015, Visual Studio 2017 und Visual Studio 2019 getestet. Mit den Windows-und Linux/MacOS-Katalogen unterstützt vcpkg jetzt mehr als 1.900 Bibliotheken. Die C++-Community fügt beiden Katalogen weiterhin neue Bibliotheken hinzu.

## <a name="simple-yet-flexible"></a>Einfach aber flexibel

Mit einem einzigen Befehl können Sie Quellen herunterladen und eine Bibliothek erstellen. vcpkg ist selbst ein Open-Source-Projekt, das auf GitHub verfügbar ist. Sie können Ihre privaten vcpkg-Klone beliebig anpassen. Sie können z. B. andere Bibliotheken oder andere Versionen von Bibliotheken als diejenigen angeben, die im öffentlichen Katalog zu finden sind. Sie können auf einem einzelnen Computer über mehrere vcpkg-Klone verfügen. Jeder kann so festgelegt werden, dass eine benutzerdefinierte Sammlung von Bibliotheken mit Ihren bevorzugten Kompilierungsschaltern erzeugt wird. Jeder Klon ist eine eigenständige Umgebung mit ihrer eigenen Kopie von „vcpkg.exe“, die nur für die eigene Hierarchie verwendet wird. vcpkg wird keinen Umgebungsvariablen hinzugefügt und verfügt über keine Abhängigkeit von der Windows-Registrierung oder Visual Studio.

## <a name="sources-not-binaries"></a>Quellen statt Binärdateien

Im Fall von Bibliotheken im Windows-Katalog lädt vcpkg Quellen anstelle von Binärdateien herunter<sup>1</sup>. Es kompiliert diese Quellen mithilfe der aktuellsten Version von Visual Studio, die es findet. In C++ ist es wichtig, dass Ihr Anwendungscode und alle Bibliotheken, die Sie verwenden, mit dem gleichen Compiler und der gleichen Compilerversion kompiliert werden. Durch die Verwendung von vcpkg eliminieren Sie das Risiko nicht übereinstimmender Binärdateien und die Probleme, die dadurch entstehen können, oder reduzieren dieses zumindest entscheidend. In Teams, in denen eine bestimmte Version eines Compilers verwendet wird, kann ein Teammitglied mit vcpkg Quellen herunterladen und Binärdateien kompilieren. Anschließend kann es mit dem Exportbefehl die Binärdateien und Header für andere Teammitglieder zippen. Weitere Informationen finden Sie nachstehend unter [Exportieren von kompilierten Binärdateien und Headern](#export_binaries_per_project).

Sie können auch einen vcpkg-Klon erstellen, in dessen Auflistung der Ports private Bibliotheken enthalten sind. Fügen Sie einen Port hinzu, der Ihre vorab erstellten Binärdateien und Header herunterlädt. Schreiben Sie dann eine Datei vom Typ „portfile.cmake“, mit der diese Dateien einfach an den bevorzugten Speicherort kopiert werden.

<sup>1</sup> *Hinweis: Für einige proprietäre Bibliotheken stehen keine Quellen zur Verfügung. vcpkg lädt in diesem Fall kompatible, vorab erstellte Binärdateien herunter.*

## <a name="installation"></a>Installation

Klonen Sie das vcpkg-Repository von GitHub: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg). Sie können es in jeden beliebigen Ordner herunterladen.

Führen Sie den Bootstrapper im Stammverzeichnis aus:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, macOS)

## <a name="search-the-list-of-available-libraries"></a>Suchen nach der Liste verfügbarer Bibliotheken

Um festzustellen, welche Pakete verfügbar sind, führen Sie an der Eingabeaufforderung Folgendes aus: **vcpkg search**

Dieser Befehl zählt die Steuerelementdateien in den vcpkg-/Ports-Unterordnern auf. Es wird eine Liste wie die folgende angezeigt:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Sie können nach einem Muster filtern, z. B. **vcpkg search ta**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Installieren einer Bibliothek auf Ihrem lokalen Computer

Nachdem Sie den Namen einer Bibliothek mithilfe von **vcpkg search** erhalten, verwenden Sie **vcpkg install** zum Herunterladen der Bibliothek, und kompilieren Sie diese. Vcpkg verwendet die Portdatei der Bibliothek im Ports-Verzeichnis. Wenn kein Tripel angegeben wird, installiert und kompiliert vcpkg für das Standard-Tripel der Zielplattform: Windows (x86), linux.cmake (x64) oder osx.cmake (x64).

Bei Linux-Bibliotheken muss gcc für vcpkg auf dem lokalen Computer installiert sein. Unter macOS verwendet vcpkg Clang.

Wenn die Portdatei Abhängigkeiten angibt, lädt vcpkg diese ebenso herunter und installiert sie. Nach dem Herunterladen erstellt vcpkg die Bibliothek und verwendet dabei das gleiche Buildsystem wie die Bibliothek. Bevorzugt werden CMake-Projekte und MSBuild-Projekte (unter Windows). MAKE wird jedoch zusammen mit jedem anderen Buildsystem unterstützt. Wenn vcpkg das angegebene Buildsystem auf dem lokalen Computer nicht finden kann, lädt es dieses herunter und installiert es.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Verwenden Sie bei CMAKE-Projekten CMAKE_TOOLCHAIN_FILE, um Bibliotheken mit `find_package()` zur Verfügung zu stellen. Zum Beispiel:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Auflisten der bereits installierten Bibliotheken

Nachdem Sie einige Bibliotheken installiert haben, können Sie **vcpkg list** verwenden, um anzuzeigen, welche Sie bereits haben:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Integration mit Visual Studio (Windows)

### <a name="per-user"></a>Pro Benutzer

Führen Sie **vcpkg integrate install** aus, um Visual Studio so zu konfigurieren, dass alle vcpkg-Headerdateien und -Binärdateien für jeden einzelnen Benutzer gesucht werden. Die Pfade von VC++-Verzeichnissen müssen dabei nicht manuell geändert werden. Wenn Sie über mehrere Klone verfügen, wird der Klon, von dem aus Sie diesen Befehl ausführen, zum neuen Standardspeicherort.

Nun können Sie für Header einfach die #include-Anweisung ausführen, indem Sie den Ordner/Header eingeben und automatisch vervollständigen lassen. Es sind keine weiteren Schritte erforderlich, um Verknüpfungen mit Bibliotheken zu erstellen oder Projektverweise hinzuzufügen. Die folgende Abbildung zeigt, wie Visual Studio die azure-storage-cpp-Header sucht. Vcpkg platziert seine Header im Unterordner **/installed**, partitioniert nach Zielplattform. Das folgende Diagramm zeigt die Liste der Includedateien im Unterordner **/was** für die Bibliothek:

![vcpkg und IntelliSense](media/vcpkg-intellisense.png "vcpkg und IntelliSense")

### <a name="per-project"></a>Pro Projekt

Wenn Sie eine spezifische Version einer Bibliothek verwenden müssen, die sich von der Version in Ihrer aktiven vcpkg-Instanz unterscheidet, führen Sie die folgenden Schritte aus:

1. Erstellen Sie einen neuen Klon von vcpkg.
1. Modifizieren Sie die Portdatei für die Bibliothek, um die Version zu erhalten, die Sie benötigen.
1. Führen Sie **vcpkg install \<library>** aus.
1. Verwenden Sie **vcpkg integrate project**, um ein NuGet-Paket zu erstellen, das pro Projekt auf diese Bibliothek verweist.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integration mit Visual Studio Code (Linux/macOS)

Führen Sie **vcpkg integrate install** aus, um Visual Studio Code unter Linux/MacOS zu konfigurieren. Dieser Befehl legt den Speicherort der vcpkg-Eintragung fest und aktiviert IntelliSense für Quelldateien.

## <a name="target-linux-from-windows-via-wsl"></a>Erstellen von Dateien für Linux unter Windows mit WSL

Mithilfe des Windows-Subsystems für Linux (WSL) können Sie Linux-Binärdateien auf einem Windows-Computer erstellen. Folgen Sie einfach der Anleitung zum [Einrichten von WSL unter Windows 10](/windows/wsl/install-win10), und konfigurieren Sie es mit der [Visual Studio-Erweiterung für Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Es ist in Ordnung, wenn Sie alle erstellten Bibliotheken für Windows und Linux in demselben Ordner platzieren. Sie sind sowohl über Windows als auch über WSL zugänglich.

## <a name="export_binaries_per_project"></a> Exportieren von kompilierten Binärdateien und Headern

Es ist ineffizient, wenn alle Benutzer in einem Team gemeinsame Bibliotheken herunterladen und erstellen können. Ein einzelnes Teammitglied kann den Befehl **vcpkg export** verwenden, um eine gemeinsame ZIP-Datei der Binärdateien und Header oder ein NuGet-Paket zu erstellen. Die Freigabe für andere Teammitglieder ist anschließend ganz einfach möglich.

## <a name="updateupgrade-installed-libraries"></a>Update/Upgrade für installierte Bibliotheken

Der öffentliche Katalog wird mit den aktuellen Versionen der Bibliotheken auf dem neuesten Stand gehalten. Um zu bestimmen, welche Ihrer lokalen Bibliotheken veraltet sind, verwenden Sie **vcpkg update**. Wenn Sie bereit sind, Ihre Auflistung der Ports auf die neueste Version des öffentlichen Katalogs zu aktualisieren, führen Sie den Befehl **vcpkg upgrade** aus. Alle installierten Bibliotheken, die nicht mehr aktuell sind, werden automatisch heruntergeladen und neu erstellt.

Standardmäßig listet der **upgrade**-Befehl nur die Bibliotheken auf, die veraltet sind. Er führt kein Upgrade der Bibliotheken durch. Wenn Sie jedoch ein Upgrade der Bibliotheken durchführen möchten, verwenden Sie die Option **--no-dry-run**.

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Upgradeoptionen

- **--no-dry-run**: Durchführen des Upgrades. Ist diese Option nicht angegeben, listet der Befehl nur die veralteten Pakete auf.
- **--keep-going**: Die Installation der Pakete wird fortgeführt, auch wenn die Installation eines Pakets fehlschlägt.
- **--triplet \<t>** : Festlegen der Standarddreiergruppe für nicht qualifizierte Pakete
- **--vcpkg-root \<pfad>** : Gibt den zu verwendenden vcpkg-Verzeichnisses anstelle des aktuellen Verzeichnisses oder Toolverzeichnisses an.

### <a name="upgrade-example"></a>Beispiel für ein Upgrade

In folgendem Beispiel wird gezeigt, wie ein Upgrade nur für angegebene Bibliotheken durchgeführt wird. vcpkg pullt Abhängigkeiten automatisch, wenn dies erforderlich ist.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Beisteuern neuer Bibliotheken

Sie können jede beliebige Bibliothek in Ihre private Ports-Sammlung aufnehmen. Um eine neue Bibliothek für den öffentlichen Katalog vorzuschlagen, öffnen Sie ein Issue auf der [GitHub-Seite zu vcpkg-Issues](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Entfernen einer Bibliothek

Geben Sie **vcpkg remove** ein, um eine installierte Bibliothek zu entfernen. Wenn andere Bibliotheken davon abhängig sind, werden Sie dazu aufgefordert, den Befehl mit **--recurse** erneut auszuführen, wodurch alle nachgeschalteten Bibliotheken entfernt werden.

## <a name="customize-vcpkg"></a>Anpassen von vcpkg

Sie können Ihren Klon von vcpkg beliebig bearbeiten. Sie können auch mehrere vcpkg-Klone erstellen und anschließend die Portdateien in den einzelnen Klonen ändern. Dies ist eine einfache Möglichkeit, um bestimmte Bibliotheksversionen zu erhalten oder bestimmte Befehlszeilenparameter anzugeben. In einem Unternehmen können beispielsweise einzelne Gruppen von Entwicklern an einer Software arbeiten, die über einen für ihre Gruppe spezifischen Satz von Abhängigkeiten verfügt. Die Lösung besteht darin, für jedes Team einen Klon von vcpkg einzurichten. Verändern Sie die Klone anschließend so, dass die Bibliotheksversionen heruntergeladen werden, und legen Sie die Kompilierungsschalter fest, die die einzelnen Teams benötigen.

## <a name="uninstall-vcpkg"></a>Deinstallieren von vcpkg

Löschen Sie einfach das vcpkg-Verzeichnis. Dadurch wird die vcpkg-Verteilung deinstalliert, sowie alle für vcpkg installierten Bibliotheken.

## <a name="send-feedback-about-vcpkg"></a>Senden von Feedback zu vcpkg

Verwenden Sie den Befehl **vcpkg contact --survey**, um Microsoft Feedback zu vcpkg zu senden, einschließlich Fehlerberichten und Featurevorschlägen.

## <a name="the-vcpkg-folder-hierarchy"></a>Die vcpkg-Ordnerhierarchie

Alle vcpkg-Funktionen und -Daten sind eigenständig in einer einzigen Verzeichnishierarchie, als „Instanz“ bezeichnet. Es gibt keine Registrierungseinstellungen oder Umgebungsvariablen. Sie können über eine beliebige Anzahl von Instanzen von vcpkg auf einem Computer verfügen, ohne dass diese sich gegenseitig beeinträchtigen.

Der Inhalt einer vcpkg-Instanz sieht folgendermaßen aus:

- buildtrees: Enthält Unterordner von Quellen, aus denen jede Bibliothek erstellt wird.
- docs: Dokumentation und Beispiele.
- downloads: Zwischengespeicherte Kopien von heruntergeladenen Tools oder Quellen. vcpkg sucht hier zuerst, wenn Sie den Installationsbefehl ausführen.
- installed: Enthält die Header und Binärdateien für jede installierte Bibliothek. Wenn Sie eine Integration in Visual Studio durchführen, veranlassen Sie im Wesentlichen, dass dieser Ordner zu den Suchpfaden hinzugefügt wird.
- packages: Interner Ordner für das Staging zwischen Installationsvorgängen.
- ports: Dateien, die jede Bibliothek im Katalog, deren Version und den Ort beschreiben, von dem aus sie heruntergeladen werden kann. Sie können, falls nötig, Ihre eigenen Ports hinzufügen.
- scripts: Skripts (cmake, powershell), die von vcpkg verwendet werden.
- toolsrc: C++-Quellcode für vcpkg und zugehörige Komponenten.
- triplets: Enthält die Einstellung für jede unterstützte Zielplattform (z. B. x86-windows oder x64-uwp).

## <a name="command-line-reference"></a>Befehlszeilenreferenz

|Befehl|Beschreibung|
|---------|---------|
|**vcpkg search \[pat]**|Suchen nach installationsbereiten Paketen|
|**vcpkg install \<pkg>...**|Installieren eines Pakets|
|**vcpkg remove \<pkg>...**|Deinstallieren eines Pakets|
|**vcpkg remove --outdated**|Deinstallieren aller veralteten Pakete|
|**vcpkg list**|Auflisten installierter Pakete|
|**vcpkg update**|Anzeigen einer Liste von Paketen zum Aktualisieren|
|**vcpkg upgrade**|Neu Erstellen aller veralteten Pakete|
|**vcpkg hash \<file> \[alg]**|Berechnen des Hashwerts für eine Datei über einen bestimmten Algorithmus (Standard SHA512)|
|**vcpkg integrate install**|Verfügbarmachen von installierten Paketen für alle Benutzer. Erfordert Administratorrechte bei der ersten Verwendung|
|**vcpkg integrate remove**|Entfernen der benutzerweiten Integration|
|**vcpkg integrate project**|Erstellen eines Referenz-NuGet-Pakets für die individuelle VS-Projektverwendung|
|**vcpkg export \<pkg>... \[opt]...**|Exportieren eines Pakets|
|**vcpkg edit \<pkg>**|Öffnen eines Ports zum Bearbeiten (verwendet %EDITOR%, Standard „code“)|
|**vcpkg create \<pkg> \<url> \[archivename]**|Erstellen eines neuen Pakets|
|**vcpkg cache**|Auflisten zwischengespeicherter kompilierter Pakete|
|**vcpkg version**|Anzeigen von Versionsinformationen|
|**vcpkg contact --survey**|Kontaktdaten zum Senden von Feedback anzeigen|

### <a name="options"></a>Optionen

|Option|Beschreibung|
|---------|---------|
|**--triplet \<t>**|Angeben der Dreiergruppe der Zielarchitektur (Standard: `%VCPKG_DEFAULT_TRIPLET%`, siehe auch **vcpkg help triplet**)|
|**--vcpkg-root \<path>**|Angeben des vcpkg-Stammverzeichnisses (Standard: `%VCPKG_ROOT%`)|
