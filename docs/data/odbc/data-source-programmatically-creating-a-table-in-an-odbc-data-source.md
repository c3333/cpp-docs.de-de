---
title: Programmgesteuertes Erstellen einer Tabelle in einer ODBC-Datenquelle
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358840"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Datenquelle: Programmgesteuertes Erstellen einer Tabelle in einer ODBC-Datenquelle

In diesem Thema wird erläutert, wie Sie `ExecuteSQL` mithilfe der `CDatabase`Memberfunktion der Klasse eine Tabelle für Ihre Datenquelle erstellen und der Funktion eine Zeichenfolge übergeben, die eine **CREATE TABLE** SQL-Anweisung enthält.

Allgemeine Informationen zu ODBC-Datenquellen in MFC finden Sie unter [Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md). Das Thema [Datenquelle: Programmgesteuertes Konfigurieren einer ODBC-Datenquelle](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) beschreibt das Erstellen von Datenquellen.

Wenn Sie die Datenquelle eingerichtet haben, können `ExecuteSQL` Sie ganz einfach Tabellen mit der Memberfunktion und der **CREATE TABLE** SQL-Anweisung erstellen. Wenn Sie z. `CDatabase` B. `myDB`ein Objekt mit dem Namen haben, können Sie den folgenden MFC-Code verwenden, um eine Tabelle zu erstellen:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

In diesem Codebeispiel wird eine Tabelle mit dem Namen `myDB`"OFFICES" in der Microsoft Access-Datenquellenverbindung erstellt, die von verwaltet wird. Die Tabelle enthält zwei Felder "OfficeID" und "OfficeName".

> [!NOTE]
> Die in der **CREATE TABLE** SQL-Anweisung angegebenen Feldtypen können je nach verwendetem ODBC-Treiber variieren. Das Microsoft Query-Programm (verteilt mit Visual C++ 1.5) ist eine Möglichkeit, um herauszufinden, welche Feldtypen für eine Datenquelle verfügbar sind. Klicken Sie in Microsoft Query auf **Datei**, klicken Sie auf **Table_Definition**, wählen Sie eine Tabelle aus einer Datenquelle aus, und sehen Sie sich den Typ an, **der** im Feld Typkombination angezeigt wird. SQL-Syntax ist auch vorhanden, um Indizes zu erstellen.

## <a name="see-also"></a>Siehe auch

[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)
