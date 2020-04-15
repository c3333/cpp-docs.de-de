---
title: Kopieren von Quellprojekteigenschaften (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: 732a13520a223f1aa73733cd4098c247052f8d3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441385"
---
# <a name="copy-sources-project-properties-linux-c"></a>Kopieren von Quellprojekteigenschaften (Linux C++)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

Die auf dieser Eigenschaftenseite festgelegten Eigenschaften gelten für alle Dateien im Projekt, mit Ausnahme derjenigen, deren Eigenschaften auf Dateiebene festgelegt sind.

| Eigenschaft | Beschreibung |
|--|--|
| Zu kopierende Quellen | Gibt die Quellen an, die auf das Remotesystem kopiert werden sollen. Das Ändern dieser Liste kann die Verzeichnisstruktur, in die Dateien auf dem Remotesystem kopiert werden, verschieben oder anderweitig beeinflussen. |
| Kopieren der Quellen | Gibt an, ob die Quellen auf das Remotesystem kopiert werden sollen. |
| Zusätzliche zu kopierende Quellen | Gibt zusätzliche Quellen an, die auf das Remotesystem kopiert werden sollen. Geben Sie optional Zuordnungspaare zwischen lokal und remote mit der folgenden Syntax an: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2. Dabei kann eine lokale Datei auf den angegebenen Remotespeicherort auf dem Remotesystem kopiert werden. |

@SourcesToCopyRemotely und @DataFilesToCopyRemotely verweisen in der Projektdatei auf Elementgruppen. Bearbeiten Sie die *vcxproj*-Datei wie im folgenden Beispiel, um zu ändern, welche Quellen oder Datendateien remote kopiert werden.

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
