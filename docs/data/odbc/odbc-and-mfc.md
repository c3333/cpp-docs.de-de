---
title: ODBC und MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320070"
---
# <a name="odbc-and-mfc"></a>ODBC und MFC

> [!NOTE]
> Um die MFC-Datenbankklassen verwenden zu können, müssen Sie über den entsprechenden ODBC-Treiber für Ihre Datenquelle verfügen. Der letzte Microsoft ODBC-Treiber für SQL Server ist [Microsoft ODBC Driver 13 für SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Die meisten Datenbankanbieter stellen einen ODBC-Treiber für Windows bereit.

In diesem Thema werden die wichtigsten Konzepte der ODBC-basierten Datenbankklassen (MFC) der Microsoft Foundation Classes (MFC-Bibliothek) vorgestellt und ein Überblick über die Zusammenarbeit der Klassen angezeigt. Weitere Informationen zu ODBC und MFC finden Sie in den folgenden Themen:

- [Herstellen der Verbindung mit einer Datenquelle](connecting-to-a-data-source.md)

- [Auswählen und Verändern von Datensätzen](selecting-and-manipulating-records.md)

- [Anzeigen und Bearbeiten von Daten in einem Formular](displaying-and-manipulating-data-in-a-form.md)

- [Arbeiten mit Dokumenten und Ansichten](working-with-documents-and-views.md)

- [Zugreifen auf ODBC und SQL](access-to-odbc-and-sql.md)

- [Weitere Lektüre zu den MFC ODBC-Klassen](further-reading-about-the-mfc-odbc-classes.md)

Die auf ODBC basierenden MFC-Datenbankklassen sind so konzipiert, dass sie Zugriff auf jede Datenbank bieten, für die ein ODBC-Treiber verfügbar ist. Da die Klassen ODBC verwenden, kann Ihre Anwendung auf Daten in vielen verschiedenen Datenformaten und unterschiedlichen lokalen/Remotekonfigurationen zugreifen. Sie müssen keinen Sonderfallcode schreiben, um verschiedene Datenbankverwaltungssysteme (DBMS) zu verarbeiten. Solange Ihre Benutzer über einen geeigneten ODBC-Treiber für die Daten verfügen, auf die sie zugreifen möchten, können sie Ihr Programm verwenden, um Daten in dort gespeicherten Tabellen zu bearbeiten.

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)
