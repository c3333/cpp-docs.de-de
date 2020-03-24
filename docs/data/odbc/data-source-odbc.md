---
title: Datenquelle (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: ed9eeb8f5ef0d53846761062cf2c6575d2eaf9e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213300"
---
# <a name="data-source-odbc"></a>Datenquelle (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In Datenbankterminologie ausgedrückt setzt sich eine Datenquelle aus einem bestimmten Satz von Daten zusammen, den Informationen, die für den Zugriff auf die Daten notwendig sind, und der Position der Datenquelle, die in Form eines Datenquellennamens beschrieben werden kann. Bei der Verwendung der [CDatabase](../../mfc/reference/cdatabase-class.md)-Klasse muss es sich bei der Datenquelle um eine Datenbank handeln, die Sie über Open Database Connectivity (ODBC)-Administrator konfiguriert haben. Beispiele für Datenquellen sind eine Remote Datenbank, die auf Microsoft SQL Server über ein Netzwerk oder eine Microsoft Access-Datei in einem lokalen Verzeichnis ausgeführt wird. Sie können von der Anwendung aus auf jede Datenquelle zugreifen, für die Sie einen ODBC-Treiber besitzen.

In der Anwendung können eine oder mehrere Datenquellen gleichzeitig aktiv sein. Dabei wird jede von einem `CDatabase`-Objekt repräsentiert. Es können auch gleichzeitig mehrere Verbindungen zu einer Datenquelle bestehen. Sie können eine Verbindung zu Remote- oder zu lokalen Datenquellen aufbauen, je nachdem, welche Treiber installiert wurden und welche Funktionen diese ODBC-Treiber unterstützen. Weitere Informationen zu Datenquellen und zum ODBC-Administrator finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und ODBC- [Administrator](../../data/odbc/odbc-administrator.md).

Die folgenden Themen enthalten weitere Informationen zu Datenquellen:

- [Datenquelle: Verwalten von Verbindungen (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Datenquelle: Bestimmen des Schemas der Datenquelle (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
