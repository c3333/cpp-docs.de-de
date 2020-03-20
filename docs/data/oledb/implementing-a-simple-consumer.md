---
title: Implementieren eines einfachen Consumers
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 2f290f2a17c51682c75fbc09118757e5fd12c4f7
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544705"
---
# <a name="implementing-a-simple-consumer"></a>Implementieren eines einfachen Consumers

::: moniker range="vs-2019"

Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Die folgenden Themen zeigen, wie Sie die vom **MFC-Anwendungsassistenten** und **ATL-OLE DB-Consumer-Assistenten** erstellten Dateien bearbeiten können, um einen einfachen Consumer zu erstellen. Dieses Beispiel besteht aus folgenden Teilen:

- In [Abrufen von Daten mit dem Consumer](#retrieve) wird erläutert, wie Sie Code im Consumer implementieren, der alle Daten zeilenweise aus einer Datenbanktabelle liest.

- In [Hinzufügen von Lesezeichenunterstützung für den Consumer](#bookmark) wird gezeigt, wie Sie dem Consumer Lesezeichenunterstützung hinzufügen können.

> [!NOTE]
> Sie können die in diesem Abschnitt beschriebene Consumeranwendung verwenden, um die `MyProv`- und `Provider`-Beispielanbieter zu testen.

> [!NOTE]
> Um eine Consumeranwendung zum Testen von `MyProv` (derselbe Anbieter, der unter [Erweitern des einfachen schreibgeschützen Anbieters](../../data/oledb/enhancing-the-simple-read-only-provider.md) beschrieben ist) zu erstellen, müssen Sie die Lesezeichenunterstützung wie unter [Hinzufügen der Lesezeichenunterstützung für den Cosumer](#bookmark) beschrieben integrieren.

## <a name="retrieving-data-with-the-consumer"></a><a name="retrieve" ></a> Abrufen von Daten mit dem Consumer

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>So ändern Sie die Konsolenanwendung zur Verwendung des OLE DB-Consumers

1. Ändern Sie unter `MyCons.cpp` den Hauptcode, indem Sie den fettgedruckten Text wie folgt einfügen:

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="adding-bookmark-support-to-the-consumer"></a><a name="bookmark" ></a> Hinzufügen von Lesezeichenunterstützung für den Consumer

Ein Lesezeichen ist eine Spalte, die Zeilen in der Tabelle eindeutig identifiziert. Normalerweise ist das die Schlüsselspalte. Dies ist jedoch nicht immer der Fall, es ist anbieterspezifisch. In diesem Abschnitt erfahren Sie, wie Sie die Lesezeichenunterstützung hinzufügen. Dazu müssen Sie die folgenden Schritte in der Klasse der Benutzerdatensätze durchführen:

- Instanziieren Sie die Lesezeichen. Hierbei handelt es sich um Objekte des Typs [CBookmark](../../data/oledb/cbookmark-class.md).

- Fordern Sie eine Lesezeichenspalte vom Anbieter an, indem Sie die Eigenschaft `DBPROP_IRowsetLocate` festlegen.

- Fügen Sie der Spaltenübersicht mit dem Makro [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) einen Lesezeicheneintrag hinzu.

Mit den vorherigen Schritten erhalten Sie Lesezeichenunterstützung und ein Lesezeichenobjekt, mit dem Sie arbeiten können. Dieses Codebeispiel veranschaulicht ein Lesezeichen wie folgt:

- Öffnen Sie eine Datei zum Schreiben.

- Geben Sie die Rowsetdaten in die Datei zeilenweise aus.

- Verschieben Sie den Rowsetsursor auf das Lesezeichen, indem Sie [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md) aufrufen.

- Geben Sie die mit Lesezeichen versehene Zeile aus, und hängen Sie sie an das Ende der Datei an.

> [!NOTE]
> Wenn Sie diese Consumeranwendung verwenden, um die `Provider`-Beispielanbieteranwendung zu testen, lassen Sie die in diesem Abschnitt beschriebene Lesezeichenunterstützung weg.

### <a name="to-instantiate-the-bookmark"></a>So instanziieren Sie das Lesezeichen

1. Der Accessor muss ein Objekt des Typs [CBookmark](../../data/oledb/cbookmark-class.md) enthalten. Der *nSize*-Parameter gibt die Größe des Lesezeichenpuffers in Bytes an (in der Regel 4 für 32-Bit-Plattformen und 8 für 64-Bit-Plattformen). Fügen Sie die folgende Deklaration zu den Spaltendatenmembern in der Benutzerdatensatz-Klasse hinzu:

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>So fordern Sie eine Lesezeichenspalte vom Anbieter an

1. Fügen Sie den folgenden Code in der `GetRowsetProperties`-Methode der Benutzerdatensatz-Klasse hinzu:

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>So fügen Sie einen Lesezeicheneintrag zur Spaltenzuordnung hinzu

1. Fügen Sie den folgenden Eintrag zur Spaltenzuordnung in der Benutzerdatensatz-Klasse hinzu:

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>So verwenden Sie eine Lesezeichen in Ihrem Hauptcode

1. Ändern Sie in der `MyCons.cpp`-Datei aus der zuvor erstellten Konsolenanwendung den Hauptcode wie folgt. Um Lesezeichen verwenden zu können, muss der Hauptcode sein eigenes Lesezeichenobjekt (`myBookmark`) instanziieren; dies ist ein anderes Lesezeichen als das im Accessor (`m_bookmark`).

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

Weitere Informationen über Lesezeichen finden Sie unter [Verwenden von Lesezeichen](../../data/oledb/using-bookmarks.md). Beispiele für Lesezeichen finden Sie auch in [Aktualisieren von Rowsets](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB-Consumers mit einem Assistenten](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
