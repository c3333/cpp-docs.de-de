---
title: Vom Anbieter-Assistenten generierte Dateien
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 3bc680e5999c077dda384823ec4f67d2456af284
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924327"
---
# <a name="provider-wizard-generated-files"></a>Vom Anbieter-Assistenten generierte Dateien

::: moniker range="msvc-160"

Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Der **ATL-OLE DB-Anbieter-Assistent** generiert die folgenden Dateien. Die folgenden Themen verwenden den Custom *Benutzerdefiniert* , aber die genauen Dateinamen hängen von der Wahl ab, die Sie beim Anlegen des Anbieters getroffen haben.

|Dateiname|BESCHREIBUNG|
|---------------|-----------------|
|*Custom* RS.cpp|Enthält die `Execute`-Hilfsmethode für den Befehl und die Spaltenzuordnung für den Anbieter.|
|*Custom* DS.h|Implementiert das Datenquellenobjekt. Diese Headerdatei enthält die Eigenschaftenzuordnung für die Eigenschaften der Datenquelle.|
|*Custom* RS.h|Implementiert die Befehls- und Rowsetobjekte. Diese Headerdatei enthält die Eigenschaftenzuordnung für Rowset- und Befehlseigenschaften.|
|*Custom* Sess.h|Implementiert das Sitzungsobjekt. Diese Headerdatei enthält die Eigenschaftenzuordnung für die Sitzungseigenschaften.|
|*Custom* .rgs|Enthält die vom **ATL-OLE DB-Anbieter-Assistenten** generierten registrierten Objekte.|

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB Anbieters](../../data/oledb/creating-an-ole-db-provider.md)<br/>
