---
title: Datenquellen und Sitzungen
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211054"
---
# <a name="data-sources-and-sessions"></a>Datenquellen und Sitzungen

Die folgende Abbildung zeigt die Klassen, die das Herstellen einer Verbindung mit und das Zugreifen auf eine Datenquelle unterstützen. Jede Klasse basiert auf einer Standard Implementierung der OLE DB-Komponente.

![Datenquellen-und Sitzungs Klassen](../../data/oledb/media/vcdatasourcesessionclasses.gif "Datenquelle und Sitzungsklassen") <br/>
Datenquelle und Sitzungsklassen

Die Klassen lauten:

- [CDataSource](../../data/oledb/cdatasource-class.md) Diese Klasse instanziiert das Datenquellen Objekt, das über einen OLE DB Anbieter eine Verbindung mit einer Datenquelle erstellt und verwaltet. Die Datenquelle übernimmt Informationen wie die Datenquellen Adresse und Authentifizierungsinformationen in Form einer Verbindungs Zeichenfolge.

   Beachten Sie auch, dass die Hilfsklasse [cenenumerator](../../data/oledb/cenumerator-class.md) häufig verwendet wird, bevor eine Verbindung hergestellt wird, um eine Liste der verfügbaren Anbieter zu erhalten, die auf einem System registriert sind. Auf diese Weise können Sie einen Anbieter als Datenquelle auswählen. Im Dialogfeld **Daten Link Eigenschaften** wird diese Klasse beispielsweise verwendet, um die Liste der Anbieter auf der Registerkarte **Anbieter** aufzufüllen. Sie entspricht der `SQLBrowseConnect`-oder `SQLDriverConnect`-Funktion.

- [CSession](../../data/oledb/csession-class.md) Diese Klasse instanziiert das Sitzungs Objekt, das eine einzelne Zugriffssitzung auf die Datenquelle darstellt. Sie können jedoch mehrere Sitzungen für eine Datenquelle erstellen. Für jede Sitzung können Sie Rowsets, Befehle und andere Objekte erstellen, um auf Daten aus der Datenquelle zuzugreifen. Die Sitzung verarbeitet Transaktionen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)
