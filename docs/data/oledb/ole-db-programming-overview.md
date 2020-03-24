---
title: Übersicht über die OLE DB-Programmierung
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210068"
---
# <a name="ole-db-programming-overview"></a>Übersicht über die OLE DB-Programmierung

OLE DB ist eine leistungsstarke, com-basierte Datenbanktechnologie. Sie bietet eine gängige Methode für den Zugriff auf Daten, unabhängig von der Form, in der Sie gespeichert ist. In einer typischen geschäftlichen Situation wird eine große Menge an Informationen nicht in Unternehmensdatenbanken gespeichert. Diese Informationen befinden sich in Dateisystemen (z. B. FAT oder NTFS), indizierten sequenziellen Dateien, persönlichen Datenbanken (z. B. in Access), Arbeitsblättern (z. B. in Excel), Anwendungen zur Projektplanung (z. B. Project) sowie in E-Mail-Nachrichten (z. B. in Outlook). Mit OLE DB können Sie auf die gleiche Weise auf alle Arten von Daten speichern zugreifen, solange der Datenspeicher über einen OLE DB-Anbieter verfügt.

Mit OLE DB können Sie Anwendungen entwickeln, die auf unterschiedliche Datenquellen zugreifen, unabhängig davon, ob Sie DBMS sind oder nicht. OLE DB ermöglicht den universellen Zugriff durch die Verwendung von COM-Schnittstellen, die die entsprechenden DBMS-Funktionen für die jeweilige Datenquelle unterstützen. COM reduziert unnötige Verdoppelungen von Diensten und erhöht die Interoperabilität nicht nur zwischen Datenquellen, sondern auch zwischen anderen Anwendungen.

## <a name="benefits-of-com"></a>Vorteile von COM

Hier setzt COM an. OLE DB stellt eine Gruppe von COM-Schnittstellen dar. Der Datenzugriff mithilfe einer einheitlichen Gruppe von Schnittstellen ermöglicht es Ihnen, eine Datenbank als Matrix kooperierender Komponenten zu organisieren.

OLE DB definiert auf der Grundlage der COM-Spezifikation eine erweiterbare und verwaltbare Reihe von Schnittstellen, die konsistente und wiederverwendbare Teile der DBMS-Funktionalität berücksichtigen und einschließen. Diese Schnittstellen definieren die Grenzen der DBMS-Komponenten, z. B. Zeilencontainer, Abfrageprozessoren und Transaktionskoordinatoren, die einen einheitlichen Transaktionszugriff auf verschiedene Informationsquellen ermöglichen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB-Vorlagen](../../data/oledb/ole-db-templates.md)
