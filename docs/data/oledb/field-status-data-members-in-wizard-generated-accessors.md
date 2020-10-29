---
title: Feldstatus-Datenmember in vom Assistenten generierten Accessoren
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 476c91f55071f6d1c7f243257273a32798813cae
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924639"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Feldstatus-Datenmember in vom Assistenten generierten Accessoren

::: moniker range="msvc-160"

Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=msvc-150"

Bei Verwendung des **ATL-OLE DB-Consumer-Assistenten** zum Erstellen eines Consumers generiert der Assistent einen Datenmember in der Benutzerdatensatzklasse für jedes Feld, das Sie in der Spaltenzuordnung angeben. Jeder Datenmember ist vom Typ `DWORD` und enthält einen Statuswert, der dem jeweiligen Feld entspricht.

Für einen Datenmember *m_OwnerID* generiert der Assistent z.B. einen zusätzlichen Datenmember für den Feldstatus ( *dwOwnerIDStatus* ) und einen weiteren für die Feldlänge ( *dwOwnerIDLength* ). Er generiert außerdem eine Spaltenzuordnung mit COLUMN_ENTRY_LENGTH_STATUS-Einträgen.

Dies wird im folgenden Code veranschaulicht:

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

   DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
   SELECT \
      AuID, \
      Author, \
      YearBorn \
      FROM dbo.Authors")

   BEGIN_COLUMN_MAP(CAuthorsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
   END_COLUMN_MAP()
...
```

> [!NOTE]
> Wenn Sie die Benutzerdatensatz-klasse ändern oder einen eigenen Consumer erstellen, müssen die Datenvariablen in der Reihenfolge vor den Status- und Längenvariablen liegen.

Sie können die Statuswerte zu Debugzwecken verwenden. Wenn vom **ATL-OLE DB-Consumer-Assistenten** generierter Code Kompilierungsfehler wie z.B. DB_S_ERRORSOCCURRED oder DB_E_ERRORSOCCURRED generiert, sollten Sie zuerst einen Blick auf die aktuellen Werte der Feldstatus-Datenmember werfen. Diejenigen mit Werten ungleich 0 (null) entsprechen den Spalten, in denen die Fehler auftreten.

Sie können mit den Statuswerten auch einen NULL-Wert für ein bestimmtes Feld festlegen. Dies ist hilfreich in Fällen, in denen Sie einen Feldwert von NULL von einem Feldwert von 0 (null) unterscheiden möchten. Es liegt an Ihnen, zu entscheiden, ob NULL ein gültiger Wert oder ein spezieller Wert ist, und wie Ihre Anwendung damit umgehen soll. OLE DB definiert DBSTATUS_S_ISNULL als richtiges Mittel zur Angabe eines generischen NULL-Werts. Wenn der Consumer Daten liest, und der Wert NULL ist, wird das Statusfeld auf DBSTATUS_S_ISNULL festgelegt. Wenn der Consumer einen NULL-Wert festlegen möchte, setzt er den Statuswert auf DBSTATUS_S_ISNULL, bevor der Anbieter aufgerufen wird.

Öffnen Sie als Nächstes „Oledb.h“, und suchen Sie nach DBSTATUSENUM. Sie können dann den numerischen Wert des Ungleich-null-Status mit den DBSTATUSENUM-Enumerationswerten vergleichen. Wenn der Enumerationsname nicht ausreicht, um Ihnen mitzuteilen, was falsch ist, ziehen Sie das Thema **Status** des Abschnitts **Binden von Datenwerten** im [OLE DB-Programmierhandbuch](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) zu Rate. Dieses Thema enthält Tabellen mit den Statuswerten, die beim Abrufen oder Festlegen der Daten verwendet werden. Informationen zu Längenwerten finden Sie im Thema **Länge** des gleichen Abschnitts.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Abrufen von Länge oder Status einer Spalte

Sie können die Länge einer Spalte mit variabler Länge oder den Status einer Spalte abrufen (um z.B. DBSTATUS_S_ISNULL zu überprüfen):

- Verwenden Sie zum Abrufen der Länge das COLUMN_ENTRY_LENGTH-Makro.

- Verwenden Sie zum Abrufen des Status das COLUMN_ENTRY_STATUS-Makro.

- Um beides abzurufen, verwenden Sie COLUMN_ENTRY_LENGTH_STATUS wie folgt:

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- Greifen Sie dann wie folgt auf Länge und/oder Status zu:

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

Bei Verwendung von `CDynamicAccessor` werden Länge und Status automatisch für Sie gebunden. Verwenden Sie zum Abrufen der Werte für Länge und Status die Memberfunktionen `GetLength` und `GetStatus`.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Arbeiten mit OLE DB Consumervorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)
