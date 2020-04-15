---
title: Einrichten einer FIPS-konformen sicheren Linux-Remoteentwicklung
description: Einrichten einer mit FIPS kompatiblen kryptografischen Verbindung zwischen Visual Studio und einem Linux-Computer für Remoteentwicklung.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520462"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Einrichten einer FIPS-konformen sicheren Linux-Remoteentwicklung

::: moniker range="<=vs-2017"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar. Mit FIPS kompatible sichere Linux-Remoteentwicklung ist in Visual Studio 2019 (Version 16.5 oder höher) verfügbar.

::: moniker-end

::: moniker range="vs-2019"

Die FIPS-Veröffentlichung (Federal Information Processing Standard) 140-2 ist ein Standard der US-Regierung für kryptografische Module. Implementierungen des Standards werden von NIST überprüft. Windows verfügt über [überprüfte Unterstützung für mit FIPS kompatible kryptografische Module](/windows/security/threat-protection/fips-140-validation). In Visual Studio 2019 (Version 16.5 oder höher) können Sie eine sichere, mit FIPS kompatible kryptografische Verbindung mit Ihrem Linux-System für Remoteentwicklung verwenden.

Im Folgenden wird erläutert, wie Sie eine sichere, mit FIPS kompatible Verbindung zwischen Visual Studio und Ihrem Linux-Remotesystem einrichten. Dieser Leitfaden ist anwendbar, wenn Sie CMake- oder MSBuild-Linux-Projekte in Visual Studio erstellen. Dieser Artikel handelt es sich um die mit FIPS kompatible Version der Verbindungsanweisungen unter [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Vorbereiten einer mit FIPS kompatiblen Verbindung

Einige Vorbereitungsschritte sind erforderlich, um eine mit FIPS kompatible, kryptografisch sichere SSH-Verbindung zwischen Visual Studio und Ihrem Linux-Remotesystem herzustellen. Für Kompatibilität mit FIPS-140-2 unterstützt Visual Studio nur RSA-Schlüssel.

In den Beispielen in diesem Artikel wird Ubuntu 18.04 LTS mit OpenSSH Server Version 7.6 verwendet. Allerdings sollten die Anweisungen für jede Distribution identisch sein, die eine moderate aktuelle Version von OpenSSH verwendet.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>So richten Sie den SSH-Server auf dem Remotesystem ein

1. Installieren und starten Sie auf dem Linux-System den OpenSSH-Server:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Wenn Sie möchten, dass der SSH-Server beim Start des Systems automatisch gestartet wird, aktivieren Sie ihn mithilfe von systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Öffnen Sie */etc/ssh/sshd_config* als root. Bearbeiten Sie die folgenden Zeilen, oder fügen Sie sie hinzu, wenn sie nicht vorhanden sind:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa ist der einzige mit FIPS kompatible Hostschlüsselalgorithmus, der von VS unterstützt wird. Die aes\*-ctr-Algorithmen sind ebenfalls mit FIPS kompatibel, aber die Implementierung in Visual Studio ist nicht genehmigt. Die ecdh-\*-Schlüsselaustauschalgorithmen sind mit FIPS kompatibel, werden aber in Visual Studio nicht unterstützt.

   Sie sind nicht auf diese Optionen beschränkt. Sie können SSH so konfigurieren, dass zusätzliche Verschlüsselungsverfahren, Hostschlüsselalgorithmen usw. verwendet werden. Einige andere relevante Sicherheitsoptionen, die Sie möglicherweise in Erwägung ziehen können, sind `PermitRootLogin`, `PasswordAuthentication` und `PermitEmptyPasswords`. Weitere Informationen finden Sie auf der Manpage zu sshd_config oder im Artikel [Konfiguration des SSH-Servers](https://www.ssh.com/ssh/sshd_config).

1. Starten Sie nach dem Speichern und Schließen von sshd_config den SSH-Server neu, um die neue Konfiguration anzuwenden:

   ```bash
   sudo service ssh restart
   ```

Im nächsten Schritt erstellen Sie ein RSA-Schlüsselpaar auf Ihrem Windows-Computer. Anschließend kopieren Sie den öffentlichen Schlüssel zur Verwendung durch SSH auf das Linux-Remotesystem.

### <a name="to-create-and-use-an-rsa-key-file"></a>So erstellen und verwenden Sie eine RSA-Schlüsseldatei

1. Generieren Sie auf dem Windows-Computer mit dem folgenden Befehl ein öffentliches/privates RSA-Schlüsselpaar:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Mit diesem Befehl wird ein öffentlicher und einer privater Schlüssel erstellt. Standardmäßig werden die Schlüssel in *%USERPROFILE%\\.ssh\\id_rsa* und *%USERPROFILE%\\.ssh\\id_rsa.pub* gespeichert. (Verwenden Sie in PowerShell `$env:USERPROFILE` anstelle des cmd-Makros `%USERPROFILE%`.) Wenn Sie den Schlüsselnamen ändern, verwenden Sie den geänderten Namen in den folgenden Schritten.  Es wird empfohlen, eine Passphrase zu verwenden, um die Sicherheit zu erhöhen.

1. Kopieren Sie den öffentlichen Schlüssel aus Windows auf den Linux-Computer:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. Fügen Sie den Schlüssel auf dem Linux-System zur Liste der autorisierten Schlüssel hinzu, und stellen Sie sicher, dass die Datei die richtigen Berechtigungen besitzt:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Nun können Sie testen, ob der neue Schlüssel in SSH funktioniert. Verwenden Sie ihn, um sich von Windows aus anzumelden:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Sie haben SSH erfolgreich eingerichtet, Verschlüsselungsschlüssel erstellt und bereitgestellt und die Verbindung getestet. Jetzt sind Sie bereit, die Visual Studio-Verbindung einzurichten.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Herstellen einer Verbindung mit dem Remotesystem in Visual Studio

1. Klicken Sie in Visual Studio in der Menüleiste auf **Extras > Optionen**, um das Dialogfeld **Optionen** zu öffnen. Wählen Sie dann **Plattformübergreifend > Verbindungs-Manager** aus, um das Dialogfeld „Verbindungs-Manager“ zu öffnen.

   Wenn Sie zuvor noch keine Verbindung in Visual Studio eingerichtet haben, öffnet Visual Studio das Dialogfeld „Verbindungs-Manager“, wenn Sie das Projekt erstmals erstellen.

1. Wählen Sie im Dialogfeld „Verbindungs-Manager“ die Schaltfläche **Hinzufügen** aus, um eine neue Verbindung hinzuzufügen.

   ![Verbindungs-Manager](media/settings_connectionmanager.png)

   Das Fenster **Mit Remotesystem verbinden** wird angezeigt.

   ![Connect to Remote System (Mit Remotesystem verbinden)](media/connect.png)

1. Geben Sie im Dialogfeld **Mit Remotesystem verbinden** die Verbindungsdetails Ihres Remotecomputers ein.

   | Eingabe | Beschreibung
   | ----- | ---
   | **Hostname**           | Name oder IP-Adresse des Zielgeräts
   | **Port**                | Port, auf dem der SSH-Dienst ausgeführt wird, in der Regel Port 22
   | **Benutzername**           | Zu authentifizierender Benutzer
   | **Authentifizierungstyp** | Auswählen eines privaten Schlüssel für eine mit FIPS kompatible Verbindung
   | **Datei für den privaten Schlüssel**    | Für die SSH-Verbindung erstellte private Schlüsseldatei
   | **Passphrase**          | Passphrase mit dem zuvor ausgewählten privaten Schlüssel

   Ändern Sie den Authentifizierungstyp in **Privater Schlüssel**. Geben Sie den Pfad zu Ihrem privaten Schlüssel in das Feld **Datei des privaten Schlüssels** ein. Sie können die Schaltfläche **Durchsuchen** verwenden, um stattdessen zu Ihrer Datei mit dem privaten Schlüssel zu navigieren. Geben Sie dann die Passphrase in das Feld **Passphrase** ein, die verwendet wird, um die Datei mit dem privaten Schlüssel zu verschlüsseln.

1. Klicken Sie auf die Schaltfläche **Verbinden**, um eine Verbindung mit dem Remotecomputer herzustellen.

   Wenn die Verbindung erfolgreich hergestellt wird, konfiguriert Visual Studio IntelliSense für die Verwendung der Remoteheader. Weitere Informationen finden Sie unter [IntelliSense für Header auf Remotesystemen](configure-a-linux-project.md#remote_intellisense).

   Wenn die Verbindung nicht erfolgreich hergestellt wird, werden die Eintragsfelder, die geändert werden müssen, rot umrandet.

   ![Fehler des Verbindungs-Manager](media/settings_connectionmanagererror.png)

   Weitere Informationen zur Problembehandlung der Verbindung finden Sie unter [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Befehlszeilenhilfsprogramm für den Verbindungs-Manager  

**Visual Studio 2019 Version 16.5 oder höher**: „ConnectionManager.exe“ ist ein Befehlszeilenhilfsprogramm zum Verwalten von Remoteentwicklungsverbindungen außerhalb von Visual Studio. Es ist gut für Aufgaben wie die Bereitstellung eines neuen Entwicklungscomputers geeignet. Sie können es auch zum Einrichten von Visual Studio für Continuous Integration verwenden. Beispiele für den und eine umfassende Referenz zum ConnectionManager-Befehl finden Sie unter [ConnectionManager-Referenz](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Optional: Aktivieren oder Deaktivieren des FIPS-Modus

Es ist möglich, den FIPS-Modus in Windows global zu aktivieren.

1. Um den FIPS-Modus zu aktivieren, drücken Sie **WINDOWS+R**, um das Dialogfeld „Ausführen“ zu öffnen, und führen Sie dann „gpedit.msc“ aus.

1. Erweitern Sie **Lokale Computerrichtlinie > Computerkonfiguration > Windows-Einstellungen > Sicherheitseinstellungen > Lokale Richtlinien**, und wählen Sie dann **Sicherheitsoptionen** aus.

1. Wählen Sie unter **Richtlinie** die Option **Systemkryptografie: Mit FIPS kompatiblen Algorithmus für Verschlüsselung, Hashing und Signieren verwenden** aus, und drücken Sie dann die **EINGABETASTE**, um das entsprechende Dialogfeld zu öffnen.

1. Wählen Sie auf der Registerkarte **Lokale Sicherheitseinstellung** die Option **Aktiviert** oder **Deaktiviert** aus, und wählen Sie dann **OK** aus, um die Änderungen zu speichern.

> [!WARNING]
> Das Aktivieren des FIPS-Modus kann dazu führen, dass einige Anwendungen nicht mehr funktionieren oder sich unerwartet verhalten. Weitere Informationen finden Sie im Blogbeitrag [Why We’re Not Recommending „FIPS mode“ Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037) (Warum wir den „FIPS-Modus“ nicht mehr empfehlen).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

[Microsoft-Dokumentation zur FIPS 140-Überprüfung](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: Sicherheitsanforderungen für kryptografische Module](https://csrc.nist.gov/publications/detail/fips/140/2/final) (von NIST)

[Validierungsprogramm für kryptografischen Algorithmus: Validierungsanmerkungen](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (von NIST)

Microsoft-Blogbeitrag zu [Why We’re Not Recommending „FIPS mode“ Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037) (Warum wir den „FIPS-Modus“ nicht mehr empfehlen)

[Konfiguration des SSH-Servers](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Siehe auch

[Konfigurieren eines Linux-Projekts](configure-a-linux-project.md)\
[Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md)\
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](deploy-run-and-debug-your-linux-project.md)\
[Konfigurieren von CMake-Debugsitzungen](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
