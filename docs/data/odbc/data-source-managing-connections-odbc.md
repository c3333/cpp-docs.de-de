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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374531"
---
# <a name="data-source-managing-connections-odbc"></a>Datenquelle: Verwalten von Verbindungen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Konfigurieren einer Datenquelle](#_core_configuring_a_data_source).

- [Wie sich eine Mehrbenutzerumgebung auf eine Datenquelle und ihre Recordsets auswirkt.](#_core_working_in_a_multiuser_environment)

- [Warum Sie eine Verbindungszeichenfolge zu einer Datenquelle verallgemeinern](#_core_generalizing_the_connection_string).

- [So stellen Sie eine Verbindung mit einer Datenquelle](#_core_connecting_to_a_specific_data_source)her.

- [So trennen Sie die Verbindung zu einer Datenquelle](#_core_disconnecting_from_a_data_source).

- [So verwenden Sie ein CDatabase-Objekt](#_core_reusing_a_cdatabase_object).

Der Verbindungsaufbau mit einer Datenquelle umfasst das Herstellen der Kommunikation mit einem DBMS, um auf die Daten zugreifen zu können. Wenn Sie von der Anwendung aus über einen ODBC-Treiber die Verbindung zu einer Datenquelle aufbauen, stellt der Treiber die Verbindung entweder lokal oder über ein Netzwerk her.

Sie können die Verbindung mit jeder beliebigen Datenquelle herstellen, für die Sie einen ODBC-Treiber besitzen. Die Benutzer der Anwendung müssen für ihre Datenquelle denselben ODBC-Treiber verwenden. Weitere Informationen zum Umverteilen von ODBC-Treibern finden Sie unter [Umverteilen von ODBC-Komponenten an Ihre Kunden](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurieren einer Datenquelle

Datenquellen werden mit dem ODBC-Administrator konfiguriert. Sie können mit dem ODBC-Administrator nach der Installation Datenquellen hinzufügen oder entfernen. Beim Erstellen von Anwendungen können Sie entweder Benutzer anleiten, wie Sie mit dem ODBC-Administrator Datenquellen hinzufügen, oder Sie können diese Funktionalität in die Anwendung integrieren, indem Sie direkte ODBC-Installationsaufrufe durchführen. Weitere Informationen finden Sie unter [ODBC Administrator](../../data/odbc/odbc-administrator.md).

Sie können eine Excel-Datei als Datenquelle verwenden, und Sie müssen die Datei so konfigurieren, dass sie registriert ist und im Dialogfeld **Datenquelle auswählen** angezeigt wird.

#### <a name="to-use-an-excel-file-as-a-data-source"></a>So verwenden Sie eine Excel-Datei als Datenquelle

1. Konfigurieren Sie die Datei mit dem ODBC-Datenquellen-Administrator.

1. Klicken Sie auf der Registerkarte **Datei-DSN** auf **Hinzufügen**.

1. Wählen Sie im Dialogfeld **Neue Datenquelle erstellen** einen Excel-Treiber aus, und klicken Sie dann auf **Weiter**.

1. Klicken Sie auf **Durchsuchen**, und wählen Sie den Namen der Datei aus, die als Datumsquelle verwendet werden soll.

> [!NOTE]
> Möglicherweise müssen Sie im Dropdownmenü **alle Dateien** auswählen, um die .xls-Dateien anzuzeigen.

1. Klicken Sie auf **Weiter** und dann auf **Fertig stellen**.

1. Wählen Sie im Dialogfeld **ODBC Microsoft Excel Setup** die Datenbankversion und die Arbeitsmappe aus.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Arbeiten in einer Mehrbenutzerumgebung

Falls mehrere Benutzer mit derselben Datenquelle verbunden sind, können sie Daten verändern, während Sie dieselben Daten in Ihren Recordsets bearbeiten. Ebenso könnten die von Ihnen durchgeführten Änderungen die Recordsets anderer Benutzer betreffen. Weitere Informationen finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) and [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Verallgemeinern der Verbindungszeichenfolge

Die Assistenten verwenden für den Verbindungsaufbau mit einer Datenquelle eine Standard-Verbindungszeichenfolge. Mit dieser Verbindung werden während der Entwicklung einer Anwendung Tabellen und Spalten angezeigt. Diese Standard-Verbindungszeichenfolge eignet sich jedoch möglicherweise nicht für die Verbindungen, die Benutzer über die Anwendung mit der Datenquelle aufbauen. Beispielsweise könnten sich die Datenquelle und der Pfad zum Speicherort dieser Datenquelle von denen unterscheiden, die Sie beim Entwickeln der Anwendung verwendet hatten. In diesem Fall sollten Sie die [CRecordset::GetDefaultConnect-Memberfunktion](../../mfc/reference/crecordset-class.md#getdefaultconnect) allgemeiner umsetzen und die Assistentenimplementierung verwerfen. Sie können z. B. eine der folgenden Lösungsmöglichkeiten verwenden:

- Registrieren und verwalten Sie die Verbindungszeichenfolgen mithilfe des ODBC-Administrators.

- Bearbeiten Sie die Verbindungszeichenfolge, und entfernen Sie den Namen der Datenquelle. Das Framework verwendet ODBC als Datenquelle. In ODBC wird zur Laufzeit ein Dialogfeld angezeigt, in dem der Name der Datenquelle und alle anderen erforderlichen Verbindungsinformationen angefordert werden.

- Geben Sie ausschließlich den Namen der Datenquelle an. ODBC fordert ggf. zur Eingabe der Benutzer-ID und des Kennworts auf. Vor der Verallgemeinerung könnte die Verbindungszeichenfolge z. B. folgendermaßen aussehen:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   In dieser Verbindungszeichenfolge ist angegeben, dass eine vertrauenswürdige Verbindung mit integrierten Sicherheitsfeatures von Windows NT verwendet wird. Die Angabe eines fest codierten bzw. keines Kennworts sollte vermieden werden, da dies zu erheblichen Sicherheitsmängeln führen kann. Sie können stattdessen eine neue Verbindungszeichenfolge für `GetDefaultConnect` festlegen, sodass Benutzer-ID und Kennwort abgefragt werden.

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Herstellen einer Verbindung mit einer bestimmten Datenquelle

Um eine Verbindung mit einer bestimmten Datenquelle herzustellen, muss ihre Datenquelle bereits mit [ODBC Administrator](../../data/odbc/odbc-administrator.md)konfiguriert sein.

#### <a name="to-connect-to-a-specific-data-source"></a>So bauen Sie die Verbindung zu einer bestimmten Datenquelle auf

1. Konstruieren Sie ein `CDatabase`-Objekt.

1. Rufen `OpenEx` Sie `Open` die Funktion oder die Memberfunktion auf.

Weitere Informationen zum Angeben der Datenquelle, wenn es sich um etwas anderes als die mit einem Assistenten angegebene ist, finden Sie unter [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) oder [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) in der *MFC-Referenz*.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Trennen der Verbindung zu einer Datenquelle

Sie müssen alle geöffneten Recordsets schließen, bevor Sie die `Close` Memberfunktion von `CDatabase`aufrufen. In Recordsets, `CDatabase` die dem Objekt zugeordnet `AddNew` sind, das Sie schließen möchten, werden alle ausstehenden oder `Edit` Anweisungen abgebrochen, und alle ausstehenden Transaktionen werden zurückgesetzt.

#### <a name="to-disconnect-from-a-data-source"></a>So trennen Sie die Verbindung mit einer Datenquelle

1. Rufen `CDatabase` Sie die [Close-Memberfunktion](../../mfc/reference/cdatabase-class.md#close) des Objekts auf.

1. Zerstören Sie das Objekt, sofern Sie es nicht wiederverwenden möchten.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Wiederverwenden eines CDatabase-Objekts

Nachdem Sie die Verbindung zu einem `CDatabase`-Objekt getrennt haben, können Sie dieses wiederverwenden. Hierbei kann entweder eine neue Verbindung zu derselben oder zu einer anderen Datenquelle aufgebaut werden.

#### <a name="to-reuse-a-cdatabase-object"></a>So verwenden Sie ein CDatabase-Objekt wieder

1. Trennen Sie die ursprüngliche Verbindung des Objekts.

1. Anstatt das Objekt zu `OpenEx` zerstören, rufen Sie seine oder `Open` Memberfunktion erneut auf.

## <a name="see-also"></a>Siehe auch

[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Datenquelle: Bestimmen des Schemas der Datenquelle (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
