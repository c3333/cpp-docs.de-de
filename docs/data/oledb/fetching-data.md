---
title: Abrufen von Daten
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 919eb059f5d3f29d491bf7a6598b0c77163bd783
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184643"
---
# <a name="fetching-data"></a>Abrufen von Daten

Nachdem Sie die Datenquellen-, Sitzungs-und Rowsetobjekte geöffnet haben, können Sie Daten abrufen. Abhängig vom Typ der verwendeten Zugriffsmethode müssen Sie möglicherweise Spalten binden.

## <a name="to-fetch-data"></a>So rufen Sie Daten ab

1. Öffnen Sie das Rowset mit dem entsprechenden **Open** -Befehl.

1. Wenn Sie verwenden `CManualAccessor` , binden Sie die Ausgabespalten, wenn Sie dies nicht bereits getan haben. Das folgende Beispiel stammt aus dem [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) -Beispiel. Um die Spalten zu binden, rufen Sie auf, `GetColumnInfo` und erstellen Sie dann einen Accessor mit den Bindungen, wie im folgenden Beispiel gezeigt:

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. Schreiben Sie eine- **`while`** Schleife, um die Daten abzurufen. In der-Schleife wird aufgerufen, `MoveNext` um den Cursor vorwärts zu setzen und den Rückgabewert für S_OK zu testen, wie im folgenden Beispiel gezeigt:

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. Innerhalb der **`while`** Schleife können Sie die Daten gemäß Ihrem Accessortyp abrufen.

   - Wenn Sie die [CAccessor](../../data/oledb/caccessor-class.md) -Klasse verwenden, sollten Sie über einen Benutzerdaten Satz verfügen, der Datenelemente enthält. Sie können mit diesen Datenmembern auf Ihre Daten zugreifen, wie im folgenden Beispiel gezeigt:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Wenn Sie die `CDynamicAccessor` `CDynamicParameterAccessor` -Klasse oder die-Klasse verwenden, können Sie Daten mithilfe der Zugriffs Funktionen `GetValue` und Abrufen `GetColumn` , wie im folgenden Beispiel gezeigt. Wenn Sie den Typ der verwendeten Daten ermitteln möchten, verwenden Sie `GetType` .

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - Wenn Sie verwenden `CManualAccessor` , müssen Sie Ihre eigenen Datenmember angeben, Sie selbst binden und direkt darauf zugreifen, wie im folgenden Beispiel gezeigt:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB Consumervorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)
