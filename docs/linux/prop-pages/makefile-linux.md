---
title: Allgemeine Eigenschaften (Linux C++ Makefile-Projekt) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446150"
---
# <a name="makefile-project-properties-linux-c"></a>MakeFile-Projekteigenschaften (Linux C++)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

Dies ist eine unvollständige Liste der Eigenschaften, dir in einem Linux Makefile-Projekt verfügbar sind. Viele Eigenschaften des MakeFile-Projekts sind identisch mit den Projekteigenschaften der Linux C++-Konsolenanwendung.

## <a name="general"></a>Allgemein

| Eigenschaft | Beschreibung | Auswahlmöglichkeiten |
|--|--|--|
| Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten. |
| Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten. |
| Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist. |
| Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)** : Dynamische Bibliothek (.so)<br>**Statische Bibliothek (.a)** : Statische Bibliothek (.a)<br>**Anwendung (.out)** : Anwendung (.out)<br>**Makefile**: Makefile<br> |
| Remotebuildcomputer | Der Zielcomputer oder das Gerät, der bzw. das für den Remotebuild, die Bereitstellung und das Debuggen verwendet werden soll. |
| Remotebuild-Stammverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät an. |
| Remotebuild-Projektverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät für das Projekt an. |

## <a name="debugging"></a>Debuggen

Siehe [Debuggereigenschaften (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopieren der Quellen

Siehe [Kopieren von Quellprojekteigenschaften (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Buildereignisse

### <a name="pre-build-event"></a>Präbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auszuführende Präbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Präbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die auf das Remotesystem kopiert werden sollen. Optional kann die Liste als Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax bereitgestellt werden: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei an den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

### <a name="post-build-event"></a>Postbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auszuführende Postbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Postbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die auf das Remotesystem kopiert werden sollen. Optional kann die Liste als Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax bereitgestellt werden: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei an den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

### <a name="remote-pre-build-event"></a>Remote-Präbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auf dem Remotesystem auszuführende Präbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Präbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die vom Remotesystem kopiert werden sollen. Optional kann die Liste als Zuordnungspaare zwischen remote und lokal mit der folgenden Syntax bereitgestellt werden: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2. Dabei kann eine Remotedatei an den angegebenen Speicherort auf dem lokalen Computer kopiert werden. |

### <a name="remote-post-build-event"></a>Remote-Postbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auf dem Remotesystem auszuführende Postbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Postbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die vom Remotesystem kopiert werden sollen. Optional kann die Liste als Zuordnungspaare zwischen remote und lokal mit der folgenden Syntax bereitgestellt werden: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2. Dabei kann eine Remotedatei an den angegebenen Speicherort auf dem lokalen Computer kopiert werden. |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Die IntelliSense-Eigenschaften können auf Projekt- oder Dateiebene festgelegt werden, um Hinweise für die IntelliSense-Engine bereitzustellen. Sie wirken sich nicht auf die Kompilierung aus.

| Eigenschaft | Beschreibung |
|--|--|
| Includesuchpfad | Gibt den Includesuchpfad zum Auflösen von eingebundenen Dateien an. |
| Erzwungene Includedateien | Gibt die Dateien an, deren Einbindung erzwungen wird |
| Präprozessordefinitionen | Gibt die von den Quelldateien verwendeten Präprozessordefinitionen an |
| Präprozessordefinitionen aufheben | Gibt mindestens eine aufgehobene Präprozessordefinition an.     (/U[Makro]) |
| Zusätzliche Optionen | Gibt zusätzliche Compilerschalter an, die von IntelliSense beim Analysieren von C++-Dateien verwendet werden sollen. |

### <a name="build"></a>Build

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile „Build“ | Gibt die Befehlszeile an, die für den Befehl „Build“ ausgeführt werden soll. |
| Befehlszeile „Rebuild All“ | Gibt die Befehlszeile die für den Befehl „Build All“ ausgeführt werden soll. |
| Befehlszeile „Clean“ | Gibt die Befehlszeile an, die für den Befehl „Clean“ ausgeführt werden soll. |

### <a name="remote-build"></a>Remotebuild

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile „Build“ | Gibt die Befehlszeile an, die für den Befehl „Build“ ausgeführt werden soll. Dies wird auf dem Remotesystem ausgeführt. |
| Befehlszeile „Rebuild All“ | Gibt die Befehlszeile die für den Befehl „Build All“ ausgeführt werden soll. Dies wird auf dem Remotesystem ausgeführt. |
| Befehlszeile „Clean“ | Gibt die Befehlszeile an, die für den Befehl „Clean“ ausgeführt werden soll Dies wird auf dem Remotesystem ausgeführt. |
| Ausgaben | Gibt die Ausgaben an, die von Remotebuild auf dem Remotsystem generiert werden. |

::: moniker-end
