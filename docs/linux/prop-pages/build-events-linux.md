---
title: Remotebuildereignisse (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441497"
---
# <a name="build-event-properties-linux-c"></a>Buildereigniseigenschaften (Linux C++)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>Präbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auszuführende Präbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Präbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die auf das Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax an: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei auf den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

## <a name="pre-link-event"></a>Prälinkereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auszuführende Prälinkereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Prälinkereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die auf das Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax an: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei auf den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

## <a name="post-build-event"></a>Postbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auszuführende Postbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Postbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die auf das Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax an: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei auf den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

## <a name="remote-pre-build-event"></a>Remote-Präbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auf dem Remotesystem auszuführende Präbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Präbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die vom Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen remote und lokal mit der folgenden Syntax an: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2. Dabei kann eine Remotedatei auf den angegebenen Speicherort auf dem lokalen Computer kopiert werden. |

## <a name="remote-pre-link-event"></a>Remote-Prälinkereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auf dem Remotesystem auszuführende Prälinkereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Prälinkereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die vom Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen remote und lokal mit der folgenden Syntax an: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2. Dabei kann eine Remotedatei auf den angegebenen Speicherort auf dem lokalen Computer kopiert werden. |

## <a name="remote-post-build-event"></a>Remote-Postbuildereignis

| Eigenschaft | Beschreibung |
|--|--|
| Befehlszeile | Gibt eine Befehlszeile für das auf dem Remotesystem auszuführende Postbuildereignis-Tool an. |
| Beschreibung | Gibt eine Beschreibung für das anzuzeigende Postbuildereignis-Tool an. |
| In Build verwenden | Gibt an, ob dieses Buildereignis aus dem Build für die aktuelle Konfiguration ausgeschlossen wird. |
| Zusätzliche zu kopierende Dateien | Gibt zusätzliche Dateien an, die vom Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen remote und lokal mit der folgenden Syntax an: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2. Dabei kann eine Remotedatei auf den angegebenen Speicherort auf dem lokalen Computer kopiert werden. |

::: moniker-end
