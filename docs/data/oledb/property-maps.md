---
title: Eigenschaftenzuordnungen
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544555"
---
# <a name="property-maps"></a>Eigenschaftenzuordnungen

Bei der Sitzung, dem Rowset und dem optionalen Befehls Objekt unterstützt jeder Anbieter eine oder mehrere Eigenschaften. Diese Eigenschaften werden in Eigenschaften Zuordnungen definiert, die in den Header Dateien gespeichert sind, die vom **Assistenten für OLE DB Anbieter**erstellt wurden. Jede Header Datei enthält eine Zuordnung für die Eigenschaften in der OLE DB-Eigenschaften Gruppe, die für das Objekt oder die in dieser Datei definierten Objekte definiert sind. Die Header Datei, die das Datenquellen Objekt enthält, enthält auch die Eigenschaften Zuordnung für die [DataSource-Eigenschaften](/previous-versions/windows/desktop/ms724188(v=vs.85)). `Session.h` enthält die Eigenschaften Zuordnung für die [Sitzungs Eigenschaften](/previous-versions/windows/desktop/ms714221(v=vs.85)). Die Rowset-und Command-Objekte befinden sich in einer einzelnen Header Datei namens *ProjectName*Rs. h. Diese Eigenschaften sind Mitglieder der Gruppe der [Rowseteigenschaften](/previous-versions/windows/desktop/ms711252(v=vs.85)) .

## <a name="see-also"></a>Siehe auch

[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
