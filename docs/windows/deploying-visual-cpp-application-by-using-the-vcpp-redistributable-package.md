---
title: Bereitstellen einer App mithilfe des Redistributable Package (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: 1e09debc53e5b1b3e1eeaa6a63924b04fd2b7ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443890"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe von Visual C++ Redistributable Package

In diesem Artikel wird ausführlich beschrieben, wie Sie das Visual C++ Redistributable Package verwenden, um eine Visual C++-Anwendung bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen folgende Komponenten, um diese exemplarische Vorgehensweise abzuschließen:

- Einen Computer, auf dem Visual Studio installiert ist.

- Einen zusätzlichen Computer, auf dem keine Visual C++-Bibliotheken vorhanden sind.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Verwenden des Visual C++ Redistributable Package zum Bereitstellen einer Anwendung

1.  Erstellen Sie eine MFC-Anwendung, indem Sie die folgenden Schritte unter [Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md) befolgen.

1. Erstellen Sie eine Datei, nennen Sie diese „setup.bat“, und fügen Sie dieser folgende Befehle hinzu. Ändern Sie `MyMFCApplication` in den Namen Ihres Projekts.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Erstellen Sie eine selbstextrahierende Setupdatei:

   1. Führen Sie „iexpress.exe“ über eine Eingabeaufforderung oder über das Fenster **Ausführen** aus.

   1. Wählen Sie **Create new Self Extraction Directive file** (Neue selbstextrahierende Anweisungsdatei erstellen) aus, und klicken Sie dann auf die Schaltfläche **Weiter**.

   1. Wählen Sie **Extract files and run an installation command** (Dateien extrahieren und Installationsbefehl ausführen) aus, und klicken Sie dann auf **Weiter**.

   1. Geben Sie im Textfeld den Namen Ihrer MFC-Anwendung ein, und klicken Sie dann auf **Weiter**.

   1. Wählen Sie auf der Seite **Confirmation prompt** (Bestätigungsaufforderung) die Option **Keine Eingabeaufforderung** aus, und klicken Sie auf **Weiter**.

   1. Wählen Sie auf der Seite **Lizenzbedingungen** die Option **Do not display a license** (Keine Lizenz anzeigen) aus, und klicken Sie dann auf **Weiter**.

   1. Fügen Sie auf der Seite **Packaged files** (Gepackte Dateien) folgende Dateien hinzu, und klicken Sie auf **Weiter**.

      - Ihre MFC-Anwendungen (EXE-Datei)

      - vcredist_x86.exe In Visual Studio 2015 befindet sich diese Datei im Verzeichnis *% VCInstallDir% Redist\\1033\\* . In Visual Studio 2017 und Visual Studio 2019 befindet sich diese Datei unter *% vctoolsredistdir%* . Sie können auch [die neueste unterstützte Redist-Datei von Microsoft herunterladen](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Die Datei „setup.bat“, die Sie zuvor erstellt haben.

   1. Geben Sie auf der Seite **Install Program to Launch** (Zu startendes Programm installieren) im Textfeld **Install Program** (Programm installieren) folgende Befehlszeile ein, und klicken Sie dann auf **Weiter**.

      **cmd.exe /c "setup.bat"**

   1. Wählen Sie auf der Seite **Fenster anzeigen** die Option **Standard** aus, und klicken Sie dann auf **Weiter**.

   1. Wählen Sie auf der Seite **Finished message** (Abschlussmeldung) die Option **Keine Meldung** aus, und klicken Sie dann auf **Weiter**.

   1. Geben Sie auf der Seite **Package Name and Options** (Paketname und -optionen) einen Namen für die selbstextrahierende Setupdatei ein, wählen Sie die Option **Store files using Long File Name inside Package** (Dateien mit langem Dateinamen in Paketen speichern) aus, und klicken Sie dann auf **Weiter**. Der Dateiname muss auf „Setup.exe“ enden, z.B. *MyMFCApplicationSetup.exe*.

   1. Wählen Sie auf der Seite **Configure restart** (Neustart konfigurieren) die Option **No restart** (Kein Neustart) aus, und klicken Sie dann auf **Weiter**.

   1. Wählen Sie auf der Seite **Save Self Extraction Directive** (Selbstextrahierende Anweisung speichern) die Option **Save Self Extraction Directive (SED) file** (SED-Datei speichern) aus, und klicken Sie dann auf **Weiter**.

   1. Klicken Sie auf der Seite **Paket erstellen** auf **Weiter**. Klicken Sie auf **Fertig stellen**.

1. Testen Sie die selbstextrahierende Setupdatei auf einem anderen Computer, auf dem keine Visual C++-Bibliothek vorhanden sind:

   1. Laden Sie auf dem anderen Computer eine Kopie der Setupdatei herunter, und installieren Sie diese, indem Sie sie ausführen und die bereitgestellten Schritte befolgen. Abhängig von den ausgewählten Optionen erfordert die Installation möglicherweise den Befehl **Als Administrator ausführen**.

   1. Führen Sie die MFC-Anwendung aus.

      Die selbstextrahierende Setupdatei installiert die MFC-Anwendung, die sich in dem Ordner befindet, den Sie in Schritt 2 angegeben haben. Die Anwendung wird erfolgreich ausgeführt, da der Installer für Visual C++ Redistributable Package in der selbstextrahierenden Setupdatei enthalten ist.

      > [!IMPORTANT]
      > Um zu ermitteln, welche Version der Laufzeit installiert ist, überprüft das Installationsprogramm den Registrierungsschlüssel \\HKLM\\Software\\Microsoft\\VisualStudio\\_Version_\\VC\\Runtimes\\_Platform_\\Version. Wenn die derzeit installierte Version neuer als die Version ist, die der Installer zu installieren versucht, gibt der Installer einen Erfolg zurück, ohne die ältere Version zu installieren und erstellt einen zusätzlichen Eintrag auf der Seite des installierten Programms in der Systemsteuerung.

## <a name="see-also"></a>Weitere Informationen

[Bereitstellungsbeispiele](deployment-examples.md)<br/>
