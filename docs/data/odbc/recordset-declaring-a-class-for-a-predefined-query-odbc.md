---
title: 'Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: 6338de99bf9c3e19e6e15ffbe0bcf5caab066ed8
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079838"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie eine Recordset-Klasse für eine vordefinierte Abfrage (manchmal als gespeicherte Prozedur bezeichnet, wie in Microsoft SQL Server) erstellt wird.

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wird gesammeltes Abrufen (Massenabrufen) von Zeilen implementiert, ist die Vorgehensweise sehr ähnlich. Informationen zu den Unterschieden zwischen Recordsets, die das Abrufen von Massen Zeilen implementieren, und denen, die dies nicht tun, finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Einige Datenbankmanagementsysteme (DBMSs) ermöglichen es Ihnen, eine vordefinierte Abfrage zu erstellen und diese wie eine Funktion aus Ihren Programmen aufzurufen. Die Abfrage hat einen Namen, kann Parameter übernehmen und kann Datensätze zurückgeben. In der Vorgehensweise in diesem Thema ist beschrieben, wie eine vordefinierte Abfrage aufgerufen wird, die Datensätze zurückgibt (und eventuell Parameter übernimmt).

Die Datenbankklassen unterstützen kein Aktualisieren vordefinierte Abfragen. Der Unterschied zwischen einer vordefinierten Momentaufnahmeabfrage und einer vordefinierten Dynasetabfrage besteht nicht in der Aktualisierbarkeit, sondern darin, ob Änderungen, die von anderen Benutzern (oder anderen Recordsets in Ihrem Programm) vorgenommen wurden, in Ihrem Recordset sichtbar sind.

> [!TIP]
>  Sie benötigen kein Recordset, um eine vordefinierte Abfrage aufzurufen, die keine Datensätze zurückgibt. Bereiten Sie die SQL-Anweisung wie nachstehend beschrieben vor, führen Sie diese aber aus, indem Sie die `CDatabase`-Memberfunktion [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) aufrufen.

Sie können eine einzelne Recordset-Klasse erstellen, um den Aufruf einer vordefinierten Abfrage zu verwalten, jedoch müssen Sie einen Teil der Arbeit selbst erledigen. Die Assistenten können keine Klasse erstellen, die speziell für diesen Zweck vorgesehen ist.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>So erstellen Sie eine Klasse zum Aufrufen einer vordefinierten Abfrage (gespeicherten Prozedur)

1. Verwenden Sie den [MFC-ODBC-Consumer-Assistenten](../../mfc/reference/adding-an-mfc-odbc-consumer.md) aus **Klasse hinzufügen**, um eine Recordset-Klasse für die Tabelle zu erstellen, zu der die meisten der Spalten gehören, die von der Abfrage zurückgegeben werden. Dies führt Sie schneller zum Ziel.

1. Fügen Sie manuell Felddatenmember für alle Spalten aus allen Tabellen hinzu, die die Abfrage zurückgibt, die der Assistent aber nicht für Sie erstellt hat.

   Wenn die Abfrage beispielsweise jeweils drei Spalten aus zwei zusätzlichen Tabellen zurückgibt, fügen Sie der Klasse sechs Felddatenmember (mit den entsprechenden Datentypen) hinzu.

1. Fügen Sie manuell [RFX](../../data/odbc/record-field-exchange-rfx.md)-Funktionsaufrufe in der [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)-Memberfunktion der Klasse hinzu, wobei einer dem Datentyp jedes hinzugefügten Felddatenmembers entspricht.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Sie müssen die Datentypen und die Reihenfolge der Spalten wissen, die im Resultset zurückgegeben werden. Die Reihenfolge der RFX-Funktionsaufrufe in `DoFieldExchange` muss mit der Reihenfolge der Spalten im Resultset übereinstimmen.

1. Fügen Sie manuell Initialisierungen für die neuen Felddatenmember im Konstruktor der Recordset-Klasse hinzu.

   Außerdem müssen Sie den Initialisierungswert für den [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)-Datenmember inkrementieren. Der Assistent schreibt die Initialisierung, berücksichtigt aber nur die Felddatenmember, die er für Sie hinzufügt. Beispiel:

    ```cpp
    m_nFields += 6;
    ```

   Einige Datentypen dürfen hier nicht initialisiert werden, z. B. `CLongBinary` oder Bytearrays.

1. Hat die Abfrage Parameter, fügen Sie einen Parameterdatenmember, eine RFX-Funktion und eine Initialisierung für jeden Parameter hinzu.

1. Sie müssen `m_nParams` für jeden hinzugefügten Parameter inkrementieren, wie Sie dies für `m_nFields` für hinzugefügte Felder in Schritt 4 dieser Vorgehensweise getan haben. Weitere Informationen finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Schreiben Sie manuell eine SQL-Anweisungseichenfolge im folgenden Format:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   Dabei ist **CALL** ein ODBC-Schlüsselwort, **proc-name** ist der Name der Abfrage, wie er in der Datenquelle bekannt ist, und die „?“-Elemente sind Platzhalter für die Parameterwerte, die Sie (sofern vorhanden) dem Recordset zur Laufzeit bereitstellen. Im folgenden Beispiel wird ein Platzhalter für einen Parameter vorbereitet:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. Legen Sie in dem Code, in dem das Recordset geöffnet wird, die Werte der Parameterdatenmeber des Recordsets fest, und rufen Sie dann die `Open`-Memberfunktion auf, wobei Sie Ihre SQL-Zeichenfolge für den *lpszSQL*-Parameter übergeben. Oder ersetzen Sie stattdessen die Zeichenfolge, die von der `GetDefaultSQL`-Memberkunktion in Ihrer Klasse zurückgegeben wird.

In den folgenden Beispielen ist die Vorgehensweise zum Aufrufen einer vordefinierten Abfrage namens `Delinquent_Accts` gezeigt, die einen Parameter für eine Vertriebsgebietsnummer (sales district number) hat. Diese Abfrage gibt drei Spalten zurück: `Acct_No`, `L_Name`, `Phone`. Alle Spalten stammen aus der „Customers“-Tabelle.

Im folgenden Recordset sind Felddatenmember für die Spalten, die die Abfrage zurückgibt, und ein Parameter für die Vertriebsgebietsnummer angegeben, die zur Laufzeit angefordert wird.

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

Diese Klassendeklaration ist so, wie der Assistent sie schreibt, mit Ausnahme des manuell hinzugefügten `m_lDistParam`-Members. Weitere Member sind hier nicht gezeigt.

Das nächste Beispiel zeigt die Initialisierungen für die Datenmember im `CDelinquents`-Konstruktor.

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

Beachten Sie die Initialisierungen für [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) und [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Der Assistent initialisiert `m_nFields`; Sie initialisieren `m_nParams`.

Im nächsten Beispiel sind die RFX-Funktionen in `CDelinquents::DoFieldExchange` gezeigt:

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

Neben dem Ausführen der RFX Aufrufe für die drei zurückgegebenen Spalten wird in diesem Code das Binden des Parameters verwaltet, den Sie zur Laufzeit übergeben. Der Parameter wird an die Spalte `Dist_No` (district number, Gebietsnummer) gebunden.

Das nächste Beispiel zeigt, wie Sie die SQL-Zeichenfolge einrichten und diese dazu verwenden, das Recordset zu öffnen.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

In diesem Code wird eine Momentaufnahme erstellt, wird an sie ein Parameter übergeben, der zuvor vom Benutzer angegeben wurde, und wird die vordefinierte Abfrage aufgerufen. Wenn die Abfrage ausgeführt wird, gibt sie Datensätze für das angegebene Vertriebsgebiet zurück. Jeder Datensatz enthält Spalten für die Kontonummer, den Nachnamen des Kunden und die Telefonnummer des Kunden.

> [!TIP]
>  Es bietet sich an, einen Rückgabewert (Ausgabeparameter) in einer gespeicherten Prozedur zu verarbeiten. Weitere Informationen und ein Beispiel hierzu finden Sie unter [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Erneutes Abfragen eines Recordsets (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset: Ausführen eines Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)