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
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213171"
---
# <a name="odbc-and-mfc"></a>ODBC und MFC

> [!NOTE]
>  Um die MFC-Datenbankklassen verwenden zu können, müssen Sie über den entsprechenden ODBC-Treiber für die Datenquelle verfügen. Der letzte Microsoft ODBC Driver for SQL Server ist der [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Die meisten Datenbankanbieter stellen einen ODBC-Treiber für Windows bereit.

In diesem Thema werden die Hauptkonzepte der ODBC-basierten Datenbankklassen der Microsoft Foundation Classes (MFC) vorgestellt und eine Übersicht über die Zusammenarbeit der Klassen bereitstellt. Weitere Informationen zu ODBC und MFC finden Sie in den folgenden Themen:

- [Aufbauen der Verbindung zu einer Datenquelle](connecting-to-a-data-source.md)

- [Auswählen und Verändern von Datensätzen](selecting-and-manipulating-records.md)

- [Anzeigen und Verändern von Daten in einem Formular](displaying-and-manipulating-data-in-a-form.md)

- [Arbeiten mit Dokumenten und Ansichten](working-with-documents-and-views.md)

- [Zugreifen auf ODBC und SQL](access-to-odbc-and-sql.md)

- [Weiterführende Themen zu MFC-ODBC-Klassen](further-reading-about-the-mfc-odbc-classes.md)

Die MFC-Datenbankklassen, die auf ODBC basieren, sind darauf ausgelegt, Zugriff auf jede Datenbank bereitzustellen, für die ein ODBC-Treiber verfügbar ist. Da die-Klassen ODBC verwenden, kann Ihre Anwendung auf Daten in vielen verschiedenen Datenformaten und unterschiedlichen lokalen/Remote Konfigurationen zugreifen. Sie müssen keinen speziellen Code schreiben, um unterschiedliche Datenbankverwaltungssysteme (DBMSs) zu verarbeiten. Solange die Benutzer über einen geeigneten ODBC-Treiber für die Daten verfügen, auf die Sie zugreifen möchten, können Sie das Programm verwenden, um Daten in dort gespeicherten Tabellen zu bearbeiten.

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)
