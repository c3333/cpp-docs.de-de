---
title: Referenz zu ConnectionManager
description: Hier erfahren Sie, wie Sie Ihre SSH-Remoteverbindungen über ein Befehlszeilentool verwalten.
ms.date: 10/7/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2f38fec21e7526fa214db811b00fc545504f0610
ms.sourcegitcommit: 611e903f222ec794ef14195796b332851ab98904
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847137"
---
# <a name="connectionmanager-reference"></a>Referenz zu ConnectionManager

::: moniker range="<=vs-2017"

„ConnectionManager.exe“ ist ab Visual Studio 2019 Version 16.5 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

„ConnectionManager.exe“ ist ein Befehlszeilenhilfsprogramm zum Verwalten von Remoteentwicklungsverbindungen außerhalb von Visual Studio. Es ist gut für Aufgaben wie die Bereitstellung eines neuen Entwicklungscomputers geeignet. Sie können es auch zum Einrichten von Visual Studio für Continuous Integration verwenden.Sie können das Hilfsprogramm in einem Developer-Eingabeaufforderungsfenster verwenden. Weitere Informationen zur Developer-Eingabeaufforderung finden Sie unter [Verwenden des Microsoft C++-Toolsets in der Befehlszeile](../build/building-on-the-command-line.md).

„ConnectionManager.exe“ ist ab Visual Studio 2019 Version 16.5 verfügbar. Das Hilfsprogramm ist Teil der Workload **Linux-Entwicklung mit C++** . Es wird auch automatisch installiert, wenn Sie die Komponente **Verbindungs-Manager** im Installationsprogramm auswählen. Es wird in *%VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe* installiert.

Die Funktionalität von „ConnectionManager.exe“ ist auch in Visual Studio verfügbar. Wählen Sie zum Verwalten von Remoteentwicklungsverbindungen in der IDE wählen Sie in der Menüleiste **Extras** > **Optionen** aus, um das Dialogfeld „Optionen“ zu öffnen. Wählen Sie im Dialogfeld „Optionen“ **Plattformübergreifend** > **Verbindungs-Manager** aus.

## <a name="syntax"></a>Syntax

> **`ConnectionManager.exe`** *Befehl* \[*Argumente* ] \[*Optionen* ]

### <a name="commands-and-arguments"></a>Befehle und Argumente

- **`add`** *Benutzer\@Host* \[ **`--port`** *Port* ] \[ **`--password`** *Kennwort* ] \[ **`--privatekey`** *privaterSchlüssel_Datei* ]

  Führt die Authentifizierung aus und fügt eine neue Verbindung hinzu. Standardmäßig werden Port 22 und Kennwortauthentifizierung verwendet. (Sie werden aufgefordert, ein Kennwort einzugeben.) Verwenden Sie sowohl **-`-password`** als auch **`--privatekey`** , um ein Kennwort für einen privaten Schlüssel anzugeben.

- **`remove`** \[*Verbindungs_ID* \| *Benutzer\@Host* \[ **`--port`** *Port* ]]

  Entfernt eine Verbindung. Wenn keine Argumente angegeben werden, werden Sie zur Angabe aufgefordert, welche Verbindung entfernt werden soll.
  
- **`modify`** \[*Standard* \| *Verbindungs_ID* \| *Benutzer\@Host* \[ **`--port`** *Port* ]] \[ **`--property`** *Schlüssel=Wert* ]

  Hiermit wird eine Eigenschaft einer Verbindung definiert oder geändert.\
  Wenn *Wert* leer ist, wird der *Schlüssel* der Eigenschaft gelöscht.\
  Wenn es bei der Authentifizierung zu einem Fehler kommt, werden keine Änderungen vorgenommen.\
  Wenn keine Verbindung angegeben ist (das ist die Bedeutung von *Standard* oben), wird die Standardremoteverbindung des Benutzers verwendet.

- **`remove-all`**

  Entfernt alle gespeicherten Verbindungen.
  
- **`clean`**

  Hiermit wird Headercache für Verbindungen entfernt, die nicht mehr vorhanden sind. 

- **`list`** \[**`--properties`** ]

  Hiermit werden Informationen, IDs und Eigenschaften aller gespeicherten Verbindungen angezeigt. 

- **`help`**

  Zeigt einen Hilfebildschirm an.

- **`version`**

  Zeigt Versionsinformationen an.

### <a name="options"></a>Optionen

- **`-q`** , **`--quiet`**

  Verhindert die Ausgabe an `stdout` oder `stderr`.

- **`--no-prompt`**

  Fehler anstatt Eingabeaufforderung, wenn zutreffend.

- **`--no-verify`**

  Fügt eine Verbindung ohne Authentifizierung hinzu oder ändert sie.

- **`--file`** *Dateiname*

  Liest Verbindungsinformationen aus dem bereitgestellten *dateinamen* .

- **`--no-telemetry`**

  Deaktiviert das Senden von Nutzungsdaten an Microsoft. Nutzungsdaten werden erfasst und an Microsoft gesendet, es sei denn, das Flag **`--no-telemetry`** wird übergeben.  

- **`-n`** , **`--dry-run`**

  Führt einen Probelauf des Befehls aus.
 
- **`--p`**

  Identisch mit **`--password`**

- **`-i`**

  Identisch mit **`--privatekey`**

## <a name="examples"></a>Beispiele

Mit diesem Befehl wird eine Verbindung für einen Benutzer namens „User“ auf „localhost“ hinzugefügt. Die Verbindung verwendet eine Schlüsseldatei für die Authentifizierung, die in *%USERPROFILE%\.ssh\id_rsa* enthalten ist.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Mit diesem Befehl wird die Verbindung mit der ID 1975957870 aus der Liste der Verbindungen entfernt.

```cmd
ConnectionManager.exe remove 1975957870
```

Dieser Befehl überschreibt die Shellauswahl für die Verbindung durch die Verbindungs-ID 21212121. Unterstützte Shells: **`sh, csh, bash, tcsh, ksh, zsh, dash`** . Wenn die im Linux-System gefundene Shell nicht unterstützt wird, wird ein Fallback dazu ausgeführt, **`sh`** explizit für alle Befehle zu verwenden.

```cmd
ConnectionManager.exe modify 21212121 --property shell=csh
```

## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit dem Linux-Zielsystem in Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end