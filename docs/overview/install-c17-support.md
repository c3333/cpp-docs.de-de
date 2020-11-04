---
title: Installieren der Unterstützung für C11 und C17 in Visual Studio
description: Installieren von Windows SDK- und CRT-Unterstützung für C11 und C17 in Visual Studio
ms.date: 09/11/2020
helpviewer_keywords:
- Install preview Windows SDK
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 9310b0dbb4e436245de820622ec9dd0f52292871
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924409"
---
# <a name="install-c11-and-c17-support-in-visual-studio"></a>Installieren der Unterstützung für C11 und C17 in Visual Studio

::: moniker range="<=msvc-150"

Die Unterstützung für die Standards C11 und C17 erfordert Visual Studio 2019 Version 16.8 oder höher. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range="msvc-160"

Die Unterstützung für die Standards C11 und C17 beginnt in Visual Studio 2019 Version 16.8. Die Unterstützung erfordert eine aktualisierte Universal C-Runtime (UCRT) und die neuesten Windows SDK-Updates, um ordnungsgemäß mit dem entsprechenden Präprozessor ([`/Zc:preprocessor`](../build/reference/zc-preprocessor.md)) zu arbeiten.

Windows SDK-Releases entsprechen Windows-Betriebssystem-Releases. Da es noch kein Windows-Release mit diesen Änderungen gab, benötigen Sie ein *Insidervorschau-Windows SDK*. Dabei handelt es sich um eine Vorschauversion des Windows SDK, die sich auf Windows-Builds bezieht, die derzeit von Windows-Insidern als *Flights* getestet werden. Nachdem Sie das Insider Preview Windows 10 SDK installiert haben, verwenden Visual Studio-Projekte, die für die Verwendung des neuesten Windows SDK konfiguriert sind, die Insider-Vorschau.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2019 Version 16.8 Preview 3 oder höher wird auf Ihrem Computer installiert und ausgeführt. Schließen Sie in die Installation die Workload „Desktopentwicklung mit C++“ ein. Sie können die neueste Vorschauversion von der [Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/)-Seite herunterladen. Wenn Visual Studio noch nicht installiert ist, nutzen Sie die Installationsanleitung in [Installieren der Unterstützung für C und C++ in Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="step-1-sign-in-by-using-an-insider-microsoft-account"></a>Schritt 1: Melden Sie sich mit einem Microsoft-Konto an.

Jeder Benutzer kann ein kostenloses [Microsoft-Konto](https://signup.live.com/) erstellen und dann das Insider-Programm wählen. Wechseln Sie zur Seite [The Windows Insider Program for Developers](https://insider.windows.com/for-developers) (Windows-Insider-Programm für Entwickler), wählen Sie **Register** (Registrieren) aus, und melden Sie sich an.

Nachdem Sie sich registriert haben, können Sie damit beginnen, Insider-Versionen von Windows als Flights zu testen. Dieser Schritt ist nicht erforderlich, um das Insider Windows 10 SDK herunterzuladen und zu verwenden. Wenn Sie sich für Windows Insider registrieren, können Ihre Computer nicht automatisch neue Windows-Flights herunterladen.

Auf der Seite **Welcome to the Windows Insider Program** (Willkommen beim Windows Insider-Programm) müssen Sie **Flight now** (Jetzt Flight herunterladen) auswählen. Fahren Sie mit dem nächsten Schritt fort, um das Insider Preview Windows 10 SDK herunterzuladen.

## <a name="step-2-download-the-insider-preview-windows-10-sdk"></a>Schritt 2: Herunterladen des Insider Preview Windows 10 SDK

Sie können das Insider Preview Windows SDK auf der Seite [Windows Insider Preview Downloads](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) herunterladen. Wenn eine Meldung angezeigt wird, die besagt, dass Sie Mitglied des Windows Insider-Programms sein müssen, stellen Sie sicher, dass Sie angemeldet sind. Verwenden Sie dasselbe Microsoft-Konto wie für das Insider-Programm. Wenn eine Meldung mit dem Hinweis angezeigt wird, dass die angeforderte Seite nicht gefunden werden kann, versuchen Sie, das Gebietsschema in der URL in *en-us* zu ändern.

Auf der Insider-Seite steht, die Verwendung eines Windows 10 Insider Preview-Betriebssystems sei erforderlich. Dies gilt nur für einige Inhalte des Windows SDK. Dieser Inhalt kann von neuen APIs abhängen, die in älteren Versionen von Windows nicht vorhanden sind. Die Windows- und Universal C-Runtime-Header können jedoch ohne Insider-Betriebssystem installiert und verwendet werden.

Wählen Sie **Get SDK Insider Preview – Build 20211** (SDK Insider Preview – Build 20211 abrufen) aus (oder höher), um mit dem Herunterladen zu beginnen. Spätere Versionen des Windows SDK werden ebenfalls funktionieren.

## <a name="step-3-install-the-insider-preview-windows-10-sdk"></a>Schritt 3: Installieren des Insider Preview Windows 10 SDK

Das Insider Preview Windows SDK wird als *`.iso`* -Datei heruntergeladen. Öffnen Sie den Ordner, der die heruntergeladene Datei enthält, im Datei-Explorer. Binden Sie die *`.iso`* -Datei ein, und führen Sie dann *`WinSDKSetup.exe`* aus, um die Installation zu starten.

Wählen Sie auf der Seite **Specify Location** (Speicherort angeben) die Option **Install the Windows Software Development Kit – \<version> to this computer** (Windows Software Development Kit <Version> auf diesem Computer installieren) und dann **Next** (Weiter) aus. Wählen Sie auf der Seite **Windows Kits Privacy** (Windows-Kits-Datenschutz) aus, ob Microsoft Erkenntnisse für die Windows 10-Kits erfassen darf, und wählen Sie dann **Next** (Weiter) aus. Wählen Sie **Accept** aus, um die Lizenzbedingungen zu akzeptieren. Wählen Sie auf der Seite **Select the features you want to install** (Auswählen der zu installierenden Funktionen) nur diese Funktionen aus:  

- Windows SDK-Signierungstools für Desktop-Apps

- Windows SDK für verwaltete UWP-Apps

- Windows SDK für UWP-C++-Apps

- Windows SDK für Desktop C++-x86-Apps (wenn Sie planen, für x86 zu erstellen)

- Windows SDK für Desktop C++-amd64-Apps (wenn Sie planen, für amd64 zu erstellen)

- Windows SDK für Desktop C++-arm-Apps (wenn Sie planen, für arm zu erstellen)

- Windows SDK für Desktop C++-arm64-Apps (wenn Sie planen, für arm64 zu erstellen)

![Ein Screenshot des Windows SDK-Installationsprogramms mit den für die Installation ausgewählten Komponenten](media/c11-7-windows-sdk-installer-select-features.png)

Wählen Sie **Install** (Installieren), um die ausgewählten SDK-Komponenten zu installieren. Die SDK-Installation nimmt einige Minuten in Anspruch. Wenn der Vorgang abgeschlossen ist, öffnen Sie Visual Studio.

## <a name="step-4-configuring-c11-or-c17-mode-in-visual-studio"></a>Schritt 4: Konfigurieren des C11- oder C17-Modus in Visual Studio

Öffnen Sie in Visual Studio ein neues oder vorhandenes C-Projekt, und öffnen Sie dann das Dialogfeld **Eigenschaftenseiten** des Projekts.

Legen Sie für das Projekt die Verwendung des Insider Preview Windows 10 SDK fest. Legen Sie auf der Seite **Konfigurationseigenschaften** > **Allgemein** die Eigenschaft **Windows SDK-Version** entweder auf **10.0 (neueste installierte Version)** oder auf die angegebene Vorschauversion fest, die Sie installiert haben.

Außerdem wird eine neue Option angezeigt: **C-Sprachstandard**. Legen Sie diese Eigenschaft auf **ISO C11 Standard (`/std:c11`)** oder **ISO C17 (2018) Standard (`/std:c17`)** fest.  

![Ein Screenshot des Dialogfelds „Eigenschaftenseiten“ auf der Seite „Allgemeine Konfigurationseigenschaften“ mit der Dropdownauswahl „ISO C 17“ für die Eigenschaft „C-Sprachstandard“.](media/c11-9-project-property-page-c-language-standard.png)

Der C++-Sprachstandard wird für die Sprache C++ verwendet. Dies ist die Standardeinstellung für die Dateierweiterung *`.cpp`* . Die C-Sprachstandard-Version wird für die Sprache C verwendet. Dies ist die Standardeinstellung für die Dateierweiterung *`.c`* . Wenn Sie mit C11 oder C17 erstellen möchten, platzieren Sie den Quellcode in eine *`.c`* -Datei, oder legen Sie den Code für die C-Kompilierung fest. Sie können diese Eigenschaft für Ihr Projekt auf der Seite **Konfigurationseigenschaften** > **C/C++**  > **Erweitert** festlegen. Legen Sie die Eigenschaft **Kompilierungsart** auf **Als C-Code kompilieren (/TC)** fest.

Herzlichen Glückwunsch, Sie haben alles eingerichtet, was Sie zum Erstellen von C11- und C17-Code in Visual Studio 2019 Version 16.8 Preview 3 benötigen!

## <a name="see-also"></a>Weitere Informationen

[`/std` (Standardversion für die Sprache festlegen)](../build/reference/std-specify-language-standard-version.md)

::: moniker-end
