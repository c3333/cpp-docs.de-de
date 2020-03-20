---
title: Erstellen eines Consumers ohne Assistent
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 85e95afa92c8a968865d9a3031e1a309e68ae7d3
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544699"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Erstellen eines Consumers ohne Assistent

Im folgenden Beispiel wird vorausgesetzt, dass Sie OLE DB-Consumerunterstützung einem vorhandenen ATL-Projekt hinzufügen. Wenn Sie einer MFC-Anwendung OLE DB-Consumerunterstützung hinzufügen möchten, sollten Sie den **MFS-Anwendungsassistenten** ausführen, der für alle erforderliche Unterstützung sorgt und MFC-Routinen aufruft, die zum Ausführen der Anwendung erforderlich sind.

So fügen Sie OLE DB-Consumerunterstützung ohne Verwendung des **ATL-OLE DB-Consumer-Assistenten** hinzu:

- Fügen Sie in der Datei " *PCH. h* " die folgenden `#include`-Anweisungen an:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Programmgesteuert führt ein Consumer in der Regel die folgende Sequenz von Vorgängen aus:

1. Erstellen Sie eine Benutzerdatensatzklasse, die Spalten an lokale Variablen bindet. In diesem Beispiel ist `CMyTableNameAccessor` die Benutzerdatensatzklasse (siehe [Benutzerdatensätze](../../data/oledb/user-records.md)). Diese Klasse enthält die Spalten- und Parameterzuordnung. Deklarieren Sie in der Benutzerdatensatzklasse für jedes Feld, das Sie in der Spaltenzuordnung angeben, einen Datenmember; deklarieren Sie auch für jeden dieser Datenmember einen Statusdatenmember und einen Längendatenmember. Weitere Informationen finden Sie unter [Feldstatus-Datenmember in vom Assistenten generierten Accessoren](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Wenn Sie einen eigenen Consumer erstellen, müssen die Datenvariablen in der Reihenfolge vor den Status- und Längenvariablen liegen.

- Instanziieren Sie eine Datenquelle und eine Sitzung. Entscheiden Sie, welcher Accessor- und Rowsettyp verwendet werden soll, und instanziieren Sie dann ein Rowset mit [CCommand](../../data/oledb/ccommand-class.md) oder [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Rufen Sie `CoInitialize` zur COM-Initialisierung auf. Dies wird im Hauptcode aufgerufen. Beispiel:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Rufen Sie [CDataSource::Open](../../data/oledb/cdatasource-open.md) oder eine seine Varianten auf.

- Öffnen Sie eine Verbindung mit der Datenquelle, öffnen Sie die Sitzung, und öffnen und initialisieren Sie das Rowset (und führen Sie auch ggf. einen Befehl aus):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Legen Sie optional Rowseteigenschaften mit `CDBPropSet::AddProperty` fest, und übergeben Sie sie als Parameter an `rs.Open`. Ein Beispiel hierfür finden Sie unter `GetRowsetProperties` in [Vom Consumer-Assistenten generierte Methoden](../../data/oledb/consumer-wizard-generated-methods.md).

- Sie können das Rowset jetzt zum Abrufen/Bearbeiten der Daten verwenden.

- Wenn Ihre Anwendung abgeschlossen ist, schließen Sie Verbindung, Sitzung und Rowset:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Wenn Sie einen Befehl verwenden, sollten Sie `ReleaseCommand` nach `Close` aufrufen. Das Codebeispiel in [CCommand::Close](../../data/oledb/ccommand-close.md) zeigt Ihnen, wie Sie `Close` und `ReleaseCommand` aufrufen.

- Rufen Sie `CoUnInitialize` auf, um die COM-Initialisierung aufzuheben. Dies wird im Hauptcode aufgerufen.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB-Consumers](../../data/oledb/creating-an-ole-db-consumer.md)