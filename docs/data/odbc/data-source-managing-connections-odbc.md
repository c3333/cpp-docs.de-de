---
title: 'Datenquelle: Verwalten von Verbindungen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213292"
---
# <a name="data-source-managing-connections-odbc"></a>Datenquelle: Verwalten von Verbindungen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [So konfigurieren Sie eine Datenquelle](#_core_configuring_a_data_source)

- [Die Auswirkungen einer mehr Benutzerumgebung auf eine Datenquelle und ihre Recordsets](#_core_working_in_a_multiuser_environment).

- [Warum Sie eine Verbindungs Zeichenfolge zu einer Datenquelle generalisieren](#_core_generalizing_the_connection_string).

- Vorgehens [Weise beim Herstellen einer Verbindung mit einer Datenquelle](#_core_connecting_to_a_specific_data_source)

- [So trennen Sie die Verbindung mit einer Datenquelle](#_core_disconnecting_from_a_data_source)

- [Wieder verwenden eines CDatabase-Objekts](#_core_reusing_a_cdatabase_object)

Der Verbindungsaufbau mit einer Datenquelle umfasst das Herstellen der Kommunikation mit einem DBMS, um auf die Daten zugreifen zu können. Wenn Sie von der Anwendung aus über einen ODBC-Treiber die Verbindung zu einer Datenquelle aufbauen, stellt der Treiber die Verbindung entweder lokal oder über ein Netzwerk her.

Sie können die Verbindung mit jeder beliebigen Datenquelle herstellen, für die Sie einen ODBC-Treiber besitzen. Die Benutzer der Anwendung müssen für ihre Datenquelle denselben ODBC-Treiber verwenden. Weitere Informationen zum erneuten Verteilen von ODBC-Treibern finden [Sie unter weiter Vertrieb von ODBC-Komponenten an Ihre Kunden](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurieren einer Datenquelle

Datenquellen werden mit dem ODBC-Administrator konfiguriert. Sie können mit dem ODBC-Administrator nach der Installation Datenquellen hinzufügen oder entfernen. Beim Erstellen von Anwendungen können Sie entweder Benutzer anleiten, wie Sie mit dem ODBC-Administrator Datenquellen hinzufügen, oder Sie können diese Funktionalität in die Anwendung integrieren, indem Sie direkte ODBC-Installationsaufrufe durchführen. Weitere Informationen finden Sie unter [ODBC-Administrator](../../data/odbc/odbc-administrator.md).

Sie können eine Excel-Datei als Datenquelle verwenden, und Sie müssen die Datei so konfigurieren, dass Sie registriert ist und im Dialogfeld **Datenquelle auswählen** angezeigt wird.

#### <a name="to-use-an-excel-file-as-a-data-source"></a>So verwenden Sie eine Excel-Datei als Datenquelle

1. Konfigurieren Sie die Datei mit dem ODBC-Datenquellen-Administrator.

1. Klicken Sie auf der Registerkarte **Datei-DSN** auf **Hinzufügen**.

1. Wählen Sie im Dialogfeld **neue Datenquelle erstellen** einen Excel-Treiber aus, und klicken Sie dann auf **weiter**.

1. Klicken Sie auf **Durchsuchen**, und wählen Sie den Namen der Datei aus, die als Datums Quelle verwendet werden soll.

> [!NOTE]
>  Sie müssen möglicherweise **alle Dateien** im Dropdown Menü auswählen, um die XLS-Dateien anzuzeigen.

1. Klicken Sie auf **Weiter**und anschließend auf **Fertig stellen**.

1. Wählen Sie im Dialogfeld **ODBC-Setup für Microsoft Excel** die Daten Bank Version und die Arbeitsmappe aus.

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Arbeiten in einer mehr Benutzerumgebung

Falls mehrere Benutzer mit derselben Datenquelle verbunden sind, können sie Daten verändern, während Sie dieselben Daten in Ihren Recordsets bearbeiten. Ebenso könnten die von Ihnen durchgeführten Änderungen die Recordsets anderer Benutzer betreffen. Weitere Informationen finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) und [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Generalisieren der Verbindungs Zeichenfolge

Die Assistenten verwenden für den Verbindungsaufbau mit einer Datenquelle eine Standard-Verbindungszeichenfolge. Mit dieser Verbindung werden während der Entwicklung einer Anwendung Tabellen und Spalten angezeigt. Diese Standard-Verbindungszeichenfolge eignet sich jedoch möglicherweise nicht für die Verbindungen, die Benutzer über die Anwendung mit der Datenquelle aufbauen. Beispielsweise könnten sich die Datenquelle und der Pfad zum Speicherort dieser Datenquelle von denen unterscheiden, die Sie beim Entwickeln der Anwendung verwendet hatten. In diesem Fall sollten Sie die Member-Funktion [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) in einer generischen Weise neu angleichen und die Implementierung des Assistenten verwerfen. Sie können z. B. eine der folgenden Lösungsmöglichkeiten verwenden:

- Registrieren und verwalten Sie die Verbindungszeichenfolgen mithilfe des ODBC-Administrators.

- Bearbeiten Sie die Verbindungszeichenfolge, und entfernen Sie den Namen der Datenquelle. Das Framework verwendet ODBC als Datenquelle. In ODBC wird zur Laufzeit ein Dialogfeld angezeigt, in dem der Name der Datenquelle und alle anderen erforderlichen Verbindungsinformationen angefordert werden.

- Geben Sie ausschließlich den Namen der Datenquelle an. ODBC fordert ggf. zur Eingabe der Benutzer-ID und des Kennworts auf. Vor der Verallgemeinerung könnte die Verbindungszeichenfolge z. B. folgendermaßen aussehen:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Diese Verbindungs Zeichenfolge gibt eine vertrauenswürdige Verbindung an, die die integrierte Sicherheit von Windows NT verwendet. Die Angabe eines fest codierten bzw. keines Kennworts sollte vermieden werden, da dies zu erheblichen Sicherheitsmängeln führen kann. Sie können stattdessen eine neue Verbindungszeichenfolge für `GetDefaultConnect` festlegen, sodass Benutzer-ID und Kennwort abgefragt werden.

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Herstellen einer Verbindung mit einer bestimmten Datenquelle

Zum Herstellen einer Verbindung mit einer bestimmten Datenquelle muss Ihre Datenquelle bereits mit dem [ODBC-Administrator](../../data/odbc/odbc-administrator.md)konfiguriert worden sein.

#### <a name="to-connect-to-a-specific-data-source"></a>So bauen Sie die Verbindung zu einer bestimmten Datenquelle auf

1. Konstruieren Sie ein `CDatabase`-Objekt.

1. Ruft seine `OpenEx` oder `Open` Member-Funktion auf.

Weitere Informationen darüber, wie Sie die Datenquelle angeben, wenn Sie etwas anderes als das mit einem Assistenten angegebene ist, finden Sie unter [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) oder [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) in der *MFC-Referenz*.

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Trennen der Verbindung mit einer Datenquelle

Sie müssen alle geöffneten Recordsets schließen, bevor Sie die `Close` Member-Funktion von `CDatabase`aufrufen. In Recordsets, die dem `CDatabase` Objekt zugeordnet sind, das Sie schließen möchten, werden alle ausstehenden `AddNew` oder `Edit` Anweisungen abgebrochen, und für alle ausstehenden Transaktionen wird ein Rollback ausgeführt.

#### <a name="to-disconnect-from-a-data-source"></a>So trennen Sie die Verbindung mit einer Datenquelle

1. Ruft die [Close](../../mfc/reference/cdatabase-class.md#close) -Member-Funktion des `CDatabase` Objekts auf.

1. Zerstören Sie das Objekt, sofern Sie es nicht wiederverwenden möchten.

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Wieder verwenden eines CDatabase-Objekts

Nachdem Sie die Verbindung zu einem `CDatabase`-Objekt getrennt haben, können Sie dieses wiederverwenden. Hierbei kann entweder eine neue Verbindung zu derselben oder zu einer anderen Datenquelle aufgebaut werden.

#### <a name="to-reuse-a-cdatabase-object"></a>So verwenden Sie ein CDatabase-Objekt wieder

1. Trennen Sie die ursprüngliche Verbindung des Objekts.

1. Anstatt das Objekt zu zerstören, müssen Sie dessen `OpenEx` oder `Open` Member-Funktion erneut aufzurufen.

## <a name="see-also"></a>Weitere Informationen

[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Datenquelle: Bestimmen des Schemas der Datenquelle (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
