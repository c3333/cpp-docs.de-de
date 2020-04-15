---
title: Installieren der C++-Unterstützung in Visual Studio
description: Installieren der Visual Studio-Unterstützung für Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335369"
---
# <a name="install-c-support-in-visual-studio"></a>Installieren der C++-Unterstützung in Visual Studio

Wenn Sie Visual Studio und die Visual C++-Tools noch nicht heruntergeladen und installiert haben, können Sie beginnen.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Installation von Visual Studio 2019

Willkommen bei Visual Studio 2019. In dieser Version können Sie ganz einfach die Features auswählen und installieren, die Sie benötigen. Und aufgrund des reduzierten minimalen Speicherbedarfs, werden sie schnell und mit weniger Beeinträchtigung des Systems installiert.

> [!NOTE]
> Dieses Thema gilt für die Installation von Visual Studio unter Windows. [Visual Studio Code](https://code.visualstudio.com/) ist eine einfache, plattformübergreifende Entwicklungsumgebung, die auf Windows-, Mac- und Linux-Systemen ausgeführt wird. Die Erweiterung Microsoft [C/C++ für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) unterstützt IntelliSense, Debugging, Codeformatierung und automatische Vervollständigung. Visual Studio für Mac unterstützt Nicht Microsoft C++, aber .NET-Sprachen und plattformübergreifende Entwicklung. Installationsanweisungen finden Sie unter [Installieren von Visual Studio für Mac](/visualstudio/mac/installation/).

Sie möchten mehr zu weiteren Neuerungen in dieser Version wissen? Weitere Informationen finden Sie in den Visual [Studio-Versionshinweisen](/visualstudio/releases/2019/release-notes/).

Bereit für die Installation? Schauen Sie sich diese schrittweise Vorführung an.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Schritt 1: Stellen Sie sicher, dass Ihr Computer für Visual Studio bereit ist

Vor der Installation von Visual Studio:

1. Informieren Sie sich über die [Systemanforderungen](/visualstudio/releases/2019/system-requirements). Anhand dieser Anforderungen können Sie feststellen, ob Ihr Computer Visual Studio 2019 unterstützt.

1. Laden Sie die aktuellen Windows-Updates herunter. So stellen Sie sicher, dass Ihr Computer sowohl die neuesten Sicherheitsupdates als auch die erforderlichen Systemkomponenten für Visual Studio hat.

1. Führen Sie einen Neustart aus. Dadurch wird sichergestellt, dass keine ausstehenden Installationen oder Updates die Installation von Visual Studio behindern.

1. Geben Sie Speicherplatz frei. Entfernen Sie nicht benötigte Dateien und Anwendungen z.B. mit der Datenträgerbereinigung-App von Ihrem %Systemlaufwerk%.

Informationen zur parallelen Ausführung vorheriger Versionen von Visual Studio und Visual Studio 2019 finden Sie auf der Seite [Visual Studio 2019 – Zielplattformen und Kompatibilität](/visualstudio/releases/2019/compatibility/).

### <a name="step-2---download-visual-studio"></a>Schritt 2: Herunterladen von Visual Studio

Laden Sie danach die Visual Studio-Bootstrapperdatei herunter. Klicken Sie zu diesem Zweck auf die folgende Schaltfläche, wählen Sie die gewünschte Edition von Visual Studio aus, und klicken Sie dann auf **Speichern** und **Ordner öffnen**.

 > [!div class="button"]
 > [Visual Studio herunterladen](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Schritt 3: Installieren des Visual Studio-Installers

Führen Sie die Bootstrapperdatei aus, um den Visual Studio-Installer zu installieren. Dieses neue, schlanke Installationsprogramm enthält alle Elemente, die Sie zum Installieren und Anpassen von Visual Studio benötigen.

1. Doppelklicken Sie in Ihrem Ordner **Downloads** auf die Bootstrapperdatei, die einer der folgenden Dateien entspricht oder ähnelt:

   - **vs_community.exe** für Visual Studio Community
   - **vs_professional.exe** für Visual Studio Professional
   - **vs_enterprise.exe** für Visual Studio Enterprise

   Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.

1. Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://visualstudio.microsoft.com/license-terms/) und die Microsoft-[Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement) zu akzeptieren. Klicken Sie auf **Weiter**.

### <a name="step-4---choose-workloads"></a>Schritt 4: Auswählen von Workloads

Nachdem das Installationsprogramm installiert wurde, können Sie es verwenden, um die Installation anzupassen, indem Sie die *gewünschten Workloads*oder Feature-Sets auswählen. Gehen Sie folgendermaßen vor:

1. Suchen Sie die gewünschten Arbeitsauslastungen im Bildschirm **Visual Studio wird installiert**.

   ![Visual Studio 2019: Installieren einer Arbeitsauslastung](../get-started/media/vs-installer-workloads.png)

   Wählen Sie für die C++-Zentrale die Arbeitsauslastung "Desktop-Entwicklung mit C++". Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.

   Zusätzliche Workloads unterstützen andere Arten der C++-Entwicklung. Wählen Sie beispielsweise die Arbeitsauslastung "Universelle Windows-Plattformentwicklung" aus, um Apps zu erstellen, die die Windows-Runtime für den Microsoft Store verwenden. Wählen Sie "Spielentwicklung mit C++", um Spiele zu erstellen, die DirectX, Unreal und Cocos2d verwenden. Wählen Sie "Linux-Entwicklung mit C++", um Linux-Plattformen, einschließlich IoT-Entwicklung, anzusprechen.

   Im Bereich **Installationsdetails** werden die enthaltenen und optionalen Komponenten aufgeführt, die von jeder Arbeitsauslastung installiert werden. Sie können optionale Komponenten in dieser Liste auswählen oder deaktivieren. Um beispielsweise die Entwicklung mithilfe der Visual Studio 2017- oder 2015-Compilertoolsets zu unterstützen, wählen Sie die optionalen Komponenten MSVC v141 oder MSVC v140 aus. Sie können Unterstützung für MFC, die experimentelle Modulsprachenerweiterung, IncrediBuild und mehr hinzufügen.

1. Nachdem Sie die gewünschten Workload(s) und optionalen Komponenten gewählt haben, wählen Sie **Installieren**aus.

   Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

> [!TIP]
> Nach der Installation können Sie jederzeit die Installation von Workloads oder Komponenten nachholen. Wenn Sie Visual Studio geöffnet haben, gehen Sie zu **Tools** > **Abrufen von Tools und Features...,** wodurch Visual Studio Installer geöffnet wird. Öffnen Sie den **Visual Studio-Installer** alternativ über das Startmenü. Nun können Sie die Workloads oder Komponenten auswählen, die Sie installieren möchten. Klicken Sie anschließend auf **Ändern**.

### <a name="step-5---choose-individual-components-optional"></a>Schritt 5: Auswählen einzelner Komponenten (optional)

Wenn Sie die Funktion "Workloads" nicht zum Anpassen der Visual Studio-Installation verwenden oder mehr Komponenten als eine Workload-Installation hinzufügen möchten, können Sie dies tun, indem Sie einzelne Komponenten auf der Registerkarte **Einzelne Komponenten** installieren oder hinzufügen. Wählen Sie, was Sie möchten, und folgen Sie dann den Anweisungen.

  ![Visual Studio 2019 – Installieren einzelner Komponenten](../get-started/media/vs-installer-individual-components.png "Installieren einzelner Komponenten von Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Schritt 6: Installieren von Language Packs (optional)

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Zum Installieren von Visual Studio in einer Sprache Ihrer Wahl klicken Sie im Visual Studio-Installer auf die Registerkarte **Sprachpakete**, und folgen Sie dann den Anweisungen.

  ![Visual Studio 2019 – Installieren von Sprachpaketen](../get-started/media/vs-installer-language-packs.png "Installieren von Visual Studio-Sprachpaketen")

#### <a name="change-the-installer-language-from-the-command-line"></a>Ändern der Installersprache über die Befehlszeile

Eine andere Möglichkeit zum Ändern der Standardsprache ist die Ausführung des Installers über die Befehlszeile. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Das Installationsprogramm merkt sich diese Einstellung, wenn es das nächste Mal ausgeführt wird. Der Installer unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, es-ES, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU und tr-TR.

### <a name="step-7---change-the-installation-location-optional"></a>Schritt 7: Ändern des Installationspfads (optional)

Sie können den Speicherbedarf für die Installation von Visual Studio auf Ihrem Systemlaufwerk reduzieren. Sie können den Downloadcache, freigegebene Komponenten, SDKs und Tools auf andere Datenträger verschieben, und Visual Studio dort belassen, wo es am schnellsten ausgeführt werden kann.

  ![Visual Studio 2019 - Installationsorte ändern](../get-started/media/vs-installer-installation-locations.png "Ändern des Installationspfads")

> [!IMPORTANT]
> Sie können nur bei der ersten Installation von Visual Studio ein anderes Laufwerk auswählen. Wenn Sie Visual Studio bereits installiert haben und das Laufwerk wechseln möchten, müssen Sie Visual Studio deinstallieren und anschließend neu installieren.

### <a name="step-8---start-developing"></a>Schritt 8: Mit dem Entwickeln beginnen

1. Klicken Sie nach Abschluss der Visual Studio-Installation auf **Starten**, um mit dem Programmieren in Visual Studio zu beginnen.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

1. Geben Sie den Typ von App im Suchfeld ein, den Sie erstellen möchten, um eine Liste der verfügbaren Vorlagen anzuzeigen. Die Liste der Vorlagen basiert auf den Workloads, die Sie bei der Installation ausgewählt haben. Wählen Sie andere Workloads aus, um andere Vorlagen anzuzeigen.

   Sie können die Suchergebnisse nach bestimmten Programmiersprachen filtern, indem Sie die Dropdownliste **Sprache** verwenden. Sie können außerdem die Listen **Plattform** und **Projekttyp** zum Filtern verwenden.

1. Ihr neues Projekt wird dann in Visual Studio geöffnet, und Sie können damit anfangen, Code zu schreiben.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Installieren von Visual Studio 2017

In Visual Studio 2017 ist es einfach, nur die Funktionen auszuwählen und zu installieren, die Sie benötigen. Und aufgrund des reduzierten minimalen Speicherbedarfs, werden sie schnell und mit weniger Beeinträchtigung des Systems installiert.

### <a name="prerequisites"></a>Voraussetzungen

- Eine Breitband-Internetverbindung. Das Visual Studio-Installationsprogramm kann mehrere Gigabyte an Daten herunterladen.

- Ein Computer, auf dem Microsoft Windows 7 oder eine höhere Version ausgeführt wird. Für ein optimales Entwicklungserlebnis empfehlen wir Windows 10. Stellen Sie sicher, dass die neuesten Updates auf Ihr System angewendet werden, bevor Sie Visual Studio installieren.

- Genug freier Speicherplatz. Visual Studio benötigt mindestens 7 GB Speicherplatz und kann 50 GB oder mehr benötigen, wenn viele allgemeine Optionen installiert sind. Wir empfehlen Ihnen, es auf Ihrem Laufwerk C: zu installieren.

Weitere Informationen zu den Anforderungen des Festplattenspeichers und des Betriebssystems finden Sie unter [Systemanforderungen für die Produktfamilie von Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Das Installationsprogramm gibt an, wie viel Speicherplatz für die ausgewählten Optionen benötigt wird.

### <a name="download-and-install"></a>Herunterladen und Installieren

1. Laden Sie das neueste Visual Studio 2017-Installationsprogramm für Windows herunter.

   > [!div class="nextstepaction"]
   > [Installieren von Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Die Community Edition eignet sich für einzelne Entwickler, Schulungsumgebungen, akademische Forschung und Open Source-Entwicklung. Installieren Sie für andere Verwendungen [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) oder [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Suchen Sie die Installationsdatei, die Sie heruntergeladen haben, und führen Sie sie aus. Es kann in Ihrem Browser angezeigt werden, oder Sie können es in Ihrem Downloads-Ordner finden. Das Installationsprogramm benötigt Administratorrechte, um ausgeführt zu werden. Möglicherweise wird ein Dialogfeld **"Benutzerkontensteuerung"** angezeigt, in dem Sie aufgefordert werden, die Berechtigung zu erteilen, damit der Installer Änderungen an Ihrem System vornehmen kann. Wählen Sie **Ja**. Wenn Sie Probleme haben, suchen Sie die heruntergeladene Datei im Datei-Explorer, klicken Sie mit der rechten Maustaste auf das Installationssymbol, und wählen Sie im Kontextmenü **als Administrator ausführen** aus.

   ![Herunterladen und Installieren des Visual Studio Installers](media/vscpp-concierge-run-installer.gif "Herunterladen und Installieren des Visual Studio Installers")

1. Der Installer bietet Ihnen eine Liste von Workloads, bei denen es sich um Gruppen von verwandten Optionen für bestimmte Entwicklungsbereiche handelt. Die Unterstützung für C++ ist jetzt Teil optionaler Workloads, die standardmäßig nicht installiert sind.

   ![Desktop-Entwicklung mit C++-Workload](media/desktop-development-with-cpp.png "Desktopentwicklung mit C++")

   Wählen Sie für C++ die **Desktopentwicklung mit C++-Workload** aus, und wählen Sie dann **Installieren**aus.

   ![Installieren der Desktopentwicklung mit C++-Workload](media/vscpp-concierge-choose-workload.gif "Installieren der Desktopentwicklung mit C++-Workload")

1. Wenn die Installation abgeschlossen ist, wählen Sie die **Schaltfläche Starten** aus, um Visual Studio zu starten.

   Wenn Sie Visual Studio zum ersten Mal ausführen, werden Sie aufgefordert, sich mit einem Microsoft-Konto anzumelden. Sollten Sie über keine Organisation verfügen, können Sie kostenlos eine Organisation erstellen. Sie müssen auch ein Thema auswählen. Keine Sorge, Sie können es später ändern, wenn Sie möchten.

   Es kann einige Minuten dauern, bis Visual Studio zum ersten Mal einsatzbereit ist. So sieht es in einem kurzen Zeitraffer aus:

   ![Visual Studio 2017 anmelden](media/vscpp-quickstart-first-run.gif "Visual Studio 2017 anmelden")

   Visual Studio wird viel schneller gestartet, wenn Sie es erneut ausführen.

1. Wenn Visual Studio geöffnet wird, überprüfen Sie, ob das Flagsymbol in der Titelleiste hervorgehoben ist:

   ![Visual Studio 2017-Benachrichtigungsflag](media/vscpp-first-start-page-flag.png "Visual Studio 2017-Benachrichtigungsflag")

   Wenn diese Option hervorgehoben ist, wählen Sie sie aus, um das **Benachrichtigungsfenster** zu öffnen. Wenn Updates für Visual Studio verfügbar sind, empfehlen wir Ihnen, sie jetzt zu installieren. Starten Sie Visual Studio nach Abschluss der Installation neu.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Installieren von Visual Studio 2015

Auf der Seite [Downloads älterer Versionen von Visual Studio](https://www.visualstudio.com/vs/older-downloads/) können Sie Visual Studio 2015 herunterladen. Führen Sie das Setupprogramm aus, klicken Sie auf **Benutzerdefinierte Installation**, und wählen Sie die C++-Komponente aus. Um einer vorhandenen Visual Studio 2015-Installation C++-Unterstützung hinzuzufügen, klicken Sie auf die Schaltfläche Windows-Start, und geben Sie **"Programme entfernen hinzufügen"** ein. Öffnen Sie das Programm aus der Ergebnisliste, und suchen Sie dann Ihre Visual Studio 2015-Installation in der Liste der installierten Programme. Doppelklicken Sie darauf, und wählen Sie dann **Ändern** aus, und wählen Sie die zu installierenden Visual C++-Komponenten aus.

In der Regel wird die Verwendung von Visual Studio 2017 empfohlen, auch wenn Sie dann Ihren Code mithilfe des Visual Studio 2015-Compilers kompilieren müssen. Weitere Informationen finden Sie unter [Use native multi-targeting in Visual Studio to build old projects (Verwenden der nativen Festlegung von Zielversionen in Visual Studio, um alte Projekte zu erstellen)](../porting/use-native-multi-targeting.md).

::: moniker-end

Wenn Visual Studio ausgeführt wird, können Sie mit dem nächsten Schritt fortfahren.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen eines C++-Projekts](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
