---
title: 'Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 38a458eb6634d5075315c9c0bbd2cb215bc76eda
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075902"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie Aggregatergebnisse mit den folgenden [SQL](../../data/odbc/sql.md)-Schlüsselwörtern abgerufen werden:

- **SUM**: Berechnet die Summe der Werte in einer Spalte mit einem numerischen Datentyp.

- **MIN**: Extrahiert den kleinsten Wert aus einer Spalte mit einem numerischen Datentyp.

- **MAX**: Extrahiert den größten Wert aus einer Spalte mit einem numerischen Datentyp.

- **AVG**: Berechnet den Durchschnittswert aller Werte in einer Spalte mit einem numerischen Datentyp.

- **COUNT**: Zählt die Anzahl der Datensätze in einer Spalte mit einem beliebigen Datentyp.

Sie können diese SQL-Funktionen verwenden, um statistische Informationen zu den Datensätzen in einer Datenquelle abzurufen, statt Datensätze aus der Datenquelle zu extrahieren. Das Recordset, das erstellt wird, besteht in der Regel aus einem einzigen Datensatz (wenn alle Spalten Aggregate sind), der einen Wert enthält. (Es können mehrere Datensätze vorhanden sein, wenn Sie eine **Group by** -Klausel verwendet haben.) Dieser Wert ist das Ergebnis der Berechnung oder Extraktion, die von der SQL-Funktion ausgeführt wird.

> [!TIP]
>  Wenn Sie eine **GROUP BY**-SQL-Klausel (und möglicherweise eine **HAVING**-Klausel) zu Ihrer SQL-Anweisung hinzufügen möchten, fügen Sie diese am Ende von `m_strFilter` an. Beispiel:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Sie können die Anzahl von Datensätzen, aus denen Sie Aggregatergebnisse abrufen, einschränken, indem Sie die Spalten filtern und sortieren.

> [!CAUTION]
>  Einige Aggregationsoperatoren geben einen Wert mit einem Datentyp zurück, der sich vom Datentyp der Spalten unterscheidet, über die die Operatoren aggregieren.

- **SUM** und **AVG** geben möglicherweise den nächstgrößeren Datentyp zurück (z. B. führt ein Aufrufen mit `int` zur Rückgabe von **LONG** oder **double**).

- **COUNT** gibt üblicherweise **LONG** zurück, unabhängig vom Typ der Zielspalte.

- **MAX** und **MIN** geben den Datentyp zurück, den die Spalte hat, die sie berechnen.

     Beispielsweise erstellt der Assistent zum **Hinzufügen von Klassen** `long` `m_lSales`, um eine Verkaufs Spalte aufzunehmen, aber Sie müssen dies durch ein `double m_dblSumSales` Datenmember ersetzen, um das Aggregat Ergebnis aufzunehmen. Siehe folgendes Beispiel.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>So rufen Sie ein aggregiertes Ergebnis für ein Recordset ab

1. Erstellen Sie gemäß der Beschreibung unter [Hinzufügen eines MFC-ODBC-Consumers](../../mfc/reference/adding-an-mfc-odbc-consumer.md) ein Recordset, das die Spalten enthält, aus denen Sie aggregierte Ergebnisse abrufen möchten.

1. Ändern Sie die [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)-Funktion für das Recordset. Ersetzen Sie die Zeichenfolge, die den Namen der Spalte darstellt (das zweite Argument des [RFX](../../data/odbc/record-field-exchange-using-rfx.md)-Funktionsaufrufs) durch eine Zeichenfolge, die die Aggregationsfunktion für die Spalte darstellt. Ersetzen Sie beispielsweise:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     durch:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Öffnen Sie das Recordset. Das Ergebnis des Aggregationsvorgangs wird in `m_dblSumSales` gespeichert.

> [!NOTE]
>  Der Assistent weist tatsächlich Datenmembernamen ohne ungarische Präfixe zu. Beispielsweise würde der Assistent den Namen `m_Sales` für eine „Sales“-Spalte anstelle des Namens `m_lSales` erstellen, der zuvor zur Veranschaulichung verwendet wurde.

Wenn Sie eine [CRecordView](../../mfc/reference/crecordview-class.md)-Klasse verwenden, um die Daten anzuzeigen, müssen Sie den DDX-Funktionsaufruf so ändern, dass der neue Wert des Datenmembers angezeigt wird. In diesem Fall bedeutet dies eine Änderung von:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

in:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Wie Recordsets Datensätze auswählen (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)