---
title: Abrufen von Metadaten mit Schemarowsets
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 37418cc91913ed840d1601aab9005b476bf29ee0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508992"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Abrufen von Metadaten mit Schemarowsets

Möglicherweise müssen Sie Informationen über Anbieter, Rowsets, Tabellen, Spalten oder andere Datenbankinformationen beziehen, ohne dafür das Rowset zu öffnen. Daten mit Angaben über die Datenbankstruktur werden als Metadaten bezeichnet und können mithilfe einer Anzahl verschiedener Methoden abgerufen werden. Die Verwendung von Schemarowsets ist eine dieser Methoden.

OLE DB Vorlagen stellen eine Reihe von Klassen zum Abrufen von Schema Informationen bereit. Diese Klassen erstellen vordefinierte Schemarowsets und sind in [Schemarowset-Klassen und typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)aufgeführt.

> [!NOTE]
> Wenn Sie OLAP verwenden und einige der Rowsets nicht von den Schemarowset-Klassen unterstützt werden (wenn Sie z. B. eine variable Spaltenanzahl haben), sollten Sie versuchen, `CManualAccessor` oder `CDynamicAccessor` zu verwenden. Sie können durch die Spalten scrollen und case-Anweisungen verwenden, um die möglichen Datentypen für jede einzelne Spalte zu behandeln.

## <a name="catalogschema-model"></a>Das Katalog-/Schemamodell

ANSI SQL definiert ein Katalog-/Schemamodell für Datenspeicher. OLE DB verwendet dieses Modell. In diesem Modell verfügen Kataloge (Datenbanken) über-Schemas und-Schemas über Tabellen.

- **Katalog** Ein Katalog ist ein anderer Name für eine Datenbank. Dabei handelt es sich um eine Sammlung verwandter Schemas. Verwenden Sie [CCatalog](./schema-rowset-classes-and-typedef-classes.md#catalog), um die Kataloge (Datenbanken) aufzulisten, die zu einer bestimmten Datenquelle gehören. Da viele Datenbanken nur einen Katalog aufweisen, werden Metadaten manchmal als Schema Informationen bezeichnet.

- **Schema** Ein Schema ist eine Auflistung von Datenbankobjekten, die im Besitz eines bestimmten Benutzers sind oder von einem bestimmten Benutzer erstellt wurden. Um die Schemas im Besitz eines bestimmten Benutzers aufzulisten, verwenden Sie [CSchemata](./schema-rowset-classes-and-typedef-classes.md#schemata).

   In Microsoft SQL Server und ODBC 2.x stellt ein Schema einen Besitzer dar (dbo ist beispielsweise ein typischer Schemaname). Darüber hinaus speichert SQL Server Metadaten in einer Tabellengruppe: Eine Tabelle enthält eine Liste aller Tabellen, und eine weitere Tabelle enthält eine Liste aller Spalten. Es gibt keine Entsprechung zu einem Schema in einer Microsoft Access-Datenbank.

- **Tabelle** Tabellen sind Auflistungen von Spalten, die in bestimmten Aufträgen angeordnet sind. Verwenden Sie [CTables](./schema-rowset-classes-and-typedef-classes.md#table), um die in einem bestimmten Katalog (Datenbank) definierten Tabellen und Informationen zu diesen Tabellen aufzulisten.

## <a name="restrictions"></a>Beschränkungen

Wenn Sie Schema Informationen Abfragen, können Sie Einschränkungen verwenden, um den Typ der Informationen anzugeben, die Sie interessieren. Sie können sich diese Einschränkungen wie einen Filter oder Qualifizierer in einer Abfrage vorstellen. Beispielsweise ist in der Abfrage:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` eine Einschränkung. Dies ist ein einfaches Beispiel mit nur einer Einschränkung. die Schemarowset-Klassen unterstützen mehrere Einschränkungen.

Die [Schemarowset-typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Kapseln alle OLE DB Schemarowsets, damit Sie wie jedes andere Rowset auf ein Schemarowset zugreifen können, indem Sie es instanziieren und öffnen. Beispielsweise ist die typedef-Klasse [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns) wie folgt definiert:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

Die Klasse " [krestrictions](../../data/oledb/crestrictions-class.md) " bietet die Einschränkungs Unterstützung. Nachdem Sie eine Instanz des Schemarowsets erstellt haben, rufen Sie die Funktion "Erstellungs Methode [:: Open](./crestrictions-class.md#open)" auf. Diese Methode gibt auf der Grundlage der von Ihnen angegebenen Einschränkungen ein Resultset zurück.

Informationen zum Angeben von Einschränkungen finden Sie im [Anhang B: Schemarowsets](/previous-versions/windows/desktop/ms712921(v=vs.85)) , und suchen Sie nach dem Rowset, das Sie verwenden. `CColumns`Entspricht z. b. dem [COLUMNS-Rowset](/previous-versions/windows/desktop/ms723052(v=vs.85)). in diesem Thema sind die Einschränkungs Spalten im COLUMNS-Rowset aufgeführt: TABLE_CATALOG, TABLE_SCHEMA table_name, column_name. Sie müssen diese Reihenfolge beim Angeben der Einschränkungen einhalten.

Wenn Sie z. b. den Tabellennamen einschränken möchten, ist table_name die dritte Einschränkungs Spalte und dann aufrufen, indem Sie `Open` den gewünschten Tabellennamen als dritten Einschränkungs Parameter angeben, wie im folgenden Beispiel gezeigt.

### <a name="to-use-schema-rowsets"></a>So verwenden Sie Schemarowsets

1. Schließen Sie die Header Datei ein `Atldbsch.h` (Sie benötigen `Atldbcli.h` auch Consumerunterstützung).

1. Instanziieren Sie ein Schemarowsetobjekt in der Consumer- oder Dokumentheaderdatei. Wenn Sie Tabellen Informationen wünschen, deklarieren Sie ein- `CTables` Objekt. Wenn Sie Spalten Informationen wünschen, deklarieren Sie ein- `CColumns` Objekt. In diesem Beispiel wird veranschaulicht, wie die Spalten der Tabelle „Authors“ abgerufen werden können:

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. Greifen Sie zum Abrufen der Informationen auf den entsprechenden Datenmember des Schemarowsetobjekts zu (z. B. `ColumnSchemaRowset.m_szColumnName`). Dieser Datenmember entspricht column_name. Weitere Informationen zu den OLE DB Spalten, denen die einzelnen Datenmember entsprechen, finden Sie unter [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns).

Für den Verweis auf das Schemarowset werden die typedef-Klassen in den OLE DB Vorlagen bereitgestellt (siehe [Schemarowset-Klassen und typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Weitere Informationen zu OLE DB Schemarowsets, einschließlich Einschränkungs Spalten, finden Sie im [Anhang B: Schemarowsets](/previous-versions/windows/desktop/ms712921(v=vs.85)) in der **OLE DB Programmierer-Referenz**.

Komplexere Beispiele zur Verwendung von Schemarowsetklassen finden Sie [in den Beispielen](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) für [die Beispiele für](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) die Verwendung von c#.

Weitere Informationen zur Anbieter Unterstützung für Schemarowsets finden Sie [unter unterstützen von Schemarowsets](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Accessoren](../../data/oledb/using-accessors.md)
