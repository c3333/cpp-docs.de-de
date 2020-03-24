---
title: Programm gesteuertes Erstellen einer Tabelle in einer ODBC-Datenquelle
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213277"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Datenquelle: Programmgesteuertes Erstellen einer Tabelle in einer ODBC-Datenquelle

In diesem Thema wird erläutert, wie Sie eine Tabelle für Ihre Datenquelle erstellen, indem Sie die `ExecuteSQL` Member-Funktion der-Klasse `CDatabase`verwenden und der Funktion eine Zeichenfolge übergeben, die eine **CREATE TABLE** SQL-Anweisung enthält.

Allgemeine Informationen zu ODBC-Datenquellen in MFC finden Sie unter [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md). Im Thema [Datenquelle: Programm gesteuertes Konfigurieren einer ODBC-Datenquelle](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) wird das Erstellen von Datenquellen beschrieben.

Wenn Sie die Datenquelle eingerichtet haben, können Sie mit der `ExecuteSQL` Member-Funktion und der **CREATE TABLE** SQL-Anweisung problemlos Tabellen erstellen. Wenn Sie z. b. ein `CDatabase` Objekt mit dem Namen `myDB`haben, können Sie den folgenden MFC-Code verwenden, um eine Tabelle zu erstellen:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

In diesem Codebeispiel wird eine Tabelle mit dem Namen "Niederlassungen" in der von `myDB`verwalteten Verbindung mit der Microsoft Access-Datenquelle erstellt. die Tabelle enthält die beiden Felder "OfficeId" und "OfficeName".

> [!NOTE]
>  Die Feldtypen, die in der **CREATE TABLE** SQL-Anweisung angegeben sind, können je nach dem von Ihnen verwendeten ODBC-Treiber variieren. Das Microsoft-Abfrageprogramm (mit Visual C++ 1,5 verteilt) ist eine Möglichkeit, herauszufinden, welche Feldtypen für eine Datenquelle verfügbar sind. Klicken Sie in Microsoft Query auf **File**, klicken Sie auf **Table_Definition**, wählen Sie eine Tabelle aus einer Datenquelle aus, und überprüfen Sie den Typ, der im Kombinations Feld **Typ** angezeigt wird. Die SQL-Syntax ist auch zum Erstellen von Indizes vorhanden.

## <a name="see-also"></a>Weitere Informationen

[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)
