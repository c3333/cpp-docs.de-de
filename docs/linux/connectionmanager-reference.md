---
title: Referenz zu ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258032"
---
# <a name="connectionmanager-reference"></a>Referenz zu ConnectionManager

::: moniker range="<=vs-2017"

„ConnectionManager.exe“ ist ab Visual Studio 2019 Version 16.5 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

„ConnectionManager.exe“ ist ein Befehlszeilenhilfsprogramm zum Verwalten von Remoteentwicklungsverbindungen außerhalb von Visual Studio. Es ist gut für Aufgaben wie die Bereitstellung eines neuen Entwicklungscomputers geeignet. Sie können es auch zum Einrichten von Visual Studio für Continuous Integration verwenden. Sie können das Hilfsprogramm in einem Developer-Eingabeaufforderungsfenster verwenden. Weitere Informationen zur Developer-Eingabeaufforderung finden Sie unter [Verwenden des Microsoft C++-Toolsets in der Befehlszeile](../build/building-on-the-command-line.md).

„ConnectionManager.exe“ ist ab Visual Studio 2019 Version 16.5 verfügbar. Das Hilfsprogramm ist Teil der Workload **Linux-Entwicklung mit C++** . Es wird auch automatisch installiert, wenn Sie die Komponente **Verbindungs-Manager** im Installationsprogramm auswählen. Es wird in *%VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe* installiert.

Die Funktionalität von „ConnectionManager.exe“ ist auch in Visual Studio verfügbar. Wählen Sie zum Verwalten von Remoteentwicklungsverbindungen in der IDE wählen Sie in der Menüleiste **Extras** > **Optionen** aus, um das Dialogfeld „Optionen“ zu öffnen. Wählen Sie im Dialogfeld „Optionen“ **Plattformübergreifend** > **Verbindungs-Manager** aus.

## <a name="syntax"></a>Syntax

> **ConnectionManager.exe** *Befehl* \[*Argumente*] \[*Optionen*]

### <a name="commands-and-arguments"></a>Befehle und Argumente

- **add** *user\@host* \[ **--port** *port*] \[ **--password** *password*] \[ **--privatekey** *privatekey_file*]

  Führt die Authentifizierung aus und fügt eine neue Verbindung hinzu. Standardmäßig werden Port 22 und Kennwortauthentifizierung verwendet. (Sie werden aufgefordert, ein Kennwort einzugeben.) Verwenden Sie **--password** und **--privatekey**, um ein Kennwort für einen privaten Schlüssel anzugeben.

- **remove** \[*connection_id* \| *user\@host* \[ **--port** *port*]]

  Entfernt eine Verbindung. Wenn keine Argumente angegeben werden, werden Sie zur Angabe aufgefordert, welche Verbindung entfernt werden soll.

- **remove-all**

  Entfernt alle gespeicherten Verbindungen.

- **list**

  Zeigt Informationen und IDs aller gespeicherten Verbindungen an.

- **help**

  Zeigt einen Hilfebildschirm an.

- **version**

  Zeigt Versionsinformationen an.

### <a name="options"></a>Optionen

- **-q**, **--quiet**

  Verhindert die Ausgabe an `stdout` oder `stderr`.

- **--no-prompt**

  Fehler anstatt Eingabeaufforderung, wenn zutreffend.

- **--no-verify**

  Fügt eine Verbindung ohne Authentifizierung hinzu oder ändert sie.

- **--file** *dateiname*

  Liest Verbindungsinformationen aus dem bereitgestellten *dateinamen*.

- **--no-telemetry**

  Deaktiviert das Senden von Nutzungsdaten an Microsoft. Nutzungsdaten werden erfasst und an Microsoft gesendet, es sei denn, das Flag **--no-telemetry** wird übergeben.  

- **-n**, **--dry-run**

  Führt einen Probelauf des Befehls aus.

- **-p**

  Identisch mit **--password**.

- **-i**

  Identisch mit **--privatekey**.

## <a name="examples"></a>Beispiele

Mit diesem Befehl wird eine Verbindung für einen Benutzer namens „User“ auf „localhost“ hinzugefügt. Die Verbindung verwendet eine Schlüsseldatei für die Authentifizierung, die in *%USERPROFILE%\.ssh\id_rsa* enthalten ist.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Mit diesem Befehl wird die Verbindung mit der ID 1975957870 aus der Liste der Verbindungen entfernt.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit dem Linux-Zielsystem in Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
