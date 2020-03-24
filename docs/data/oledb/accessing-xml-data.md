---
title: Zugreifen auf XML-Daten
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: be4225003211449a98d3fbe5fd686b9b8058a651
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212276"
---
# <a name="accessing-xml-data"></a>Zugreifen auf XML-Daten

Es gibt zwei separate Methoden zum Abrufen von XML-Daten aus einer Datenquelle: eine verwendet [CStreamRowset](../../data/oledb/cstreamrowset-class.md) , und die andere verwendet [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).

|Funktionalität|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Übertragene Datenmenge|Ruft Daten gleichzeitig aus allen Spalten und Zeilen ab.|Ruft Daten aus allen Spalten ab, aber jeweils nur eine Zeile. Sie müssen mit Methoden wie `MoveNext`in den Zeilen navigieren.|
|Formatieren der Zeichenfolge|SQL Server formatiert die XML-Zeichenfolge und sendet Sie an den Consumer.|Ruft Rowsetdaten im systemeigenen Format (Anforderungen, die der Anbieter als Unicode-Zeichen folgen sendet) ab und erstellt dann die Zeichenfolge, die die Daten im XML-Format enthält.|
|Steuern der Formatierung|Sie haben ein gewisses Maß an Kontrolle darüber, wie die XML-Zeichenfolge formatiert wird, indem Sie einige SQL Server 2000-spezifische Eigenschaften festlegen.|Sie haben keine Kontrolle über das Format der generierten XML-Zeichenfolge.|

Obwohl `CStreamRowset` eine allgemeinere Methode zum Abrufen von Daten im XML-Format bereitstellt, wird Sie nur von SQL Server 2000 unterstützt.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Abrufen von XML-Daten mithilfe von CStreamRowset

Sie geben [CStreamRowset](../../data/oledb/cstreamrowset-class.md) als Rowsettyp in der `CCommand` oder `CTable` Deklaration an. Sie können Sie mit Ihrem eigenen-Accessor oder ohne-Accessor verwenden, z. b.:

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

Oder

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Wenn Sie `CCommand::Open` abrufen (z. b. `CRowset` als `TRowset` Klasse), wird normalerweise ein `IRowset` Zeiger abgerufen. `ICommand::Execute` gibt einen `IRowset`-Zeiger zurück, der im `m_spRowset`-Member des `CRowset` Objekts gespeichert wird. Methoden wie `MoveFirst`, `MoveNext`und `GetData` verwenden diesen Zeiger, um die Daten abzurufen.

Wenn Sie dagegen `CCommand::Open` aufrufen (aber `CStreamRowset` als `TRowset` Klasse angeben), gibt `ICommand::Execute` einen `ISequentialStream`-Zeiger zurück, der im `m_spStream` Datenmember von [CStreamRowset](../../data/oledb/cstreamrowset-class.md)gespeichert wird. Anschließend verwenden Sie die `Read`-Methode, um die (Unicode-Zeichen folgen) im XML-Format abzurufen. Beispiel:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 führt die XML-Formatierung aus und gibt alle Spalten und alle Zeilen des Rowsets als eine XML-Zeichenfolge zurück.

Ein Beispiel für die Verwendung der `Read`-Methode finden Sie unter **Hinzufügen von XML-Unterstützung für den Consumer** beim [Implementieren eines einfachen](../../data/oledb/implementing-a-simple-consumer.md)Consumers.

> [!NOTE]
> Die XML-Unterstützung mithilfe von `CStreamRowset` funktioniert nur mit SQL Server 2000 und erfordert, dass Sie über den OLE DB Anbieter für SQL Server 2000 (installiert mit MDAC) verfügen.

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Abrufen von XML-Daten mithilfe von CXMLAccessor

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) ermöglicht den Zugriff auf Daten aus einer Datenquelle als Zeichen folgen Daten, wenn Sie nicht über das Schema des Daten Stores verfügen. `CXMLAccessor` funktioniert wie `CDynamicStringAccessorW`, mit dem Unterschied, dass der frühere Daten alle Daten, auf die aus dem Datenspeicher zugegriffen wird, als im XML-Format (markierte) Die Namen der XML-Tags entsprechen den Spaltennamen des Daten Stores so genau wie möglich.

Verwenden Sie `CXMLAccessor` wie jede andere Accessor-Klasse, und übergeben Sie Sie als Vorlagen Parameter an `CCommand` oder `CTable`:

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Verwenden Sie [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) , um Daten zeilenweise aus der Tabelle abzurufen, und navigieren Sie mithilfe von Methoden wie z. b. `MoveNext`wie folgt:

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

Sie können [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) verwenden, um die Spalten Informationen (Datentyp) als XML-formatierte Zeichen folgen Daten abzurufen.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
