---
title: Allgemeine Eigenschaften (Linux C++-Projekt)
description: In diesem Artikel sind die Linux-Projekteigenschaften beschrieben, die Sie in Visual Studio auf der Seite „Allgemeine Eigenschaften“ festlegen können.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: d6a69d9fd3091c885ebd708cbc4598533d2922b4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883979"
---
# <a name="general-properties-linux-c"></a>Allgemeine Eigenschaften (Linux C++)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

Eigenschaft | Beschreibung | Auswahlmöglichkeiten
--- | ---| ---
Ausgabeverzeichnis | Diese Eigenschaft gibt einen relativen Pfad zum Verzeichnis der Ausgabedatei an. Er kann Umgebungsvariablen enthalten.
Zwischenverzeichnis | Diese Eigenschaft gibt einen relativen Pfad zum Verzeichnis der Zwischendatei an. Er kann Umgebungsvariablen enthalten.
Target Name | Diese Eigenschaft legt den vom Projekt generierten Dateinamen fest.
Zielerweiterung | Diese Eigenschaft gibt die Dateierweiterung an, die von diesem Projekt generiert wird, z. B. `.a`.
Bei der Bereinigung zu löschende Erweiterungen | Bei dieser Eigenschaft wird eine durch Semikolons getrennte Platzhalterspezifikation verwendet, um anzugeben, welche Dateien im Zwischenverzeichnis beim Bereinigen oder erneuten Erstellen gelöscht werden sollen.
Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist.
Plattformtoolset | Diese Eigenschaft gibt das Toolset an, das beim Erstellen der aktuellen Konfiguration verwendet wird. Wenn hier nichts angegeben ist, wird das Standardtoolset verwendet.
Remotebuildcomputer | Diese Eigenschaft zeigt den Zielcomputer oder das -gerät an, das für den Remotebuild, die -bereitstellung und das -debuggen verwendet werden soll. Sie können eine Zielcomputerverbindung hinzufügen oder bearbeiten, indem Sie **Tools** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** auswählen. **Visual Studio 2019 Version 16.1**: Auf der Seite [Debuggen](debugging-linux.md) können Sie für das Debuggen einen anderen Computer angeben.
Remotebuild-Stammverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät an.
Remotebuild-Projektverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät für das Projekt an.
Remote Deploy Directory (Verzeichnis für Remotebereitstellung) | **Visual Studio 2019 Version 16.1**: Diese Eigenschaft gibt den Verzeichnispfad auf dem Remotecomputer oder-gerät an, wo das Projekt bereitgestellt werden soll.
Einzuschließende Verzeichnisse für Remotekopieren | **Visual Studio 2019 Version 16.5**: Diese Eigenschaft gibt eine Liste von Verzeichnissen an, die rekursiv aus dem Linux-Ziel kopiert werden sollen. Sie wirkt sich auf die Remoteheaderkopie für IntelliSense aus, nicht jedoch auf den Build. Sie kann verwendet werden, wenn für **IntelliSense verwendet Compilerstandardwerte** die Einstellung FALSE festgelegt ist. Verwenden Sie die Option **Zusätzliche Includeverzeichnisse** auf dem Tab „C/C++ General“ (C/C++ allgemein), um zusätzliche Includeverzeichnisse anzugeben, die sowohl für IntelliSense als auch beim Erstellen verwendet werden sollen.
Auszuschließende Verzeichnisse für Remotekopieren | **Visual Studio 2019 Version 16.5**: Diese Eigenschaft gibt eine Liste von Verzeichnissen an, die *nicht* aus dem Linux-Ziel kopiert werden sollen. Sie wird normalerweise verwendet, um Unterverzeichnisse der Includeverzeichnisse zu entfernen.
IntelliSense verwendet Compilerstandardwerte | **Visual Studio 2019 Version 16.5**: Diese Eigenschaft gibt an, ob beim Compiler, auf den von diesem Projekt verwiesen wird, dessen Standardliste von Includespeicherorten abgefragt werden soll. Diese Speicherorte werden automatisch der Liste der zu kopierenden Remoteverzeichnisse hinzugefügt. Legen Sie diese Eigenschaft nur auf FALSE fest, wenn der Compiler keine GCC-ähnlichen Parameter unterstützt. Sowohl der GCC-als auch der Clang-Compiler unterstützen das Abfragen der Includeverzeichnisse, z. B. `g++ -x c++ -E -v -std=c++11`.
Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)**<br/>**Statische Bibliothek (.a)**<br/>**Anwendung (.out)**<br/>**Makefile**
Verwendung von STL | Gibt an, welche C++-Standardbibliothek für diese Konfiguration verwendet werden soll. | **Freigegebene GNU C++-Standardbibliothek**<br/>**Statische GNU C++-Standardbibliothek (-static)**

::: moniker-end
