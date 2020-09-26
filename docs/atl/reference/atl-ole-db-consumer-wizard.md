---
title: ATL-OLE DB-Consumer-Assistent
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: f7bdc371e5575375f5e72a1a6c0c51890921b1f4
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353128"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL-OLE DB-Consumer-Assistent

::: moniker range="vs-2019"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=vs-2017"

Dieser Assistent richtet eine OLE DB-Consumerklasse mit den Datenbindungen ein, die zum Zugriff auf die angegebene Datenquelle über den angegebenen OLE DB-Anbieter erforderlich sind.

> [!NOTE]
> Dieser Assistent erfordert, dass Sie auf die Schaltfläche **Datenquelle** klicken, um eine Datenquelle auszuwählen, bevor Sie Namen in die Felder `Class` und **H-Datei** eingeben.

## <a name="uielement-list"></a>UIElement-Liste

- **Data Source**

   Mithilfe der Schaltfläche **Datenquelle** können Sie die angegebene Datenquelle unter Verwendung des angegebenen OLE DB-Anbieters einrichten. Wenn Sie auf diese Schaltfläche klicken, wird das Dialogfeld **Datenverknüpfungseigenschaften** geöffnet. Weitere Informationen zum Erstellen von Verbindungszeichenfolgen und dem Dialogfeld **Datenverknüpfungseigenschaften** finden Sie im Abschnitt [Übersicht über die Data Link-API](/previous-versions/windows/desktop/ms718102(v=vs.85)) in der Windows SDK-Dokumentation.

   Die folgenden zusätzlichen Informationen beschreiben die Registerkarten im Dialogfeld **Datenverknüpfungseigenschaften**.

  - Registerkarte **Anbieter**

      Wählen Sie einen geeigneten Anbieter zum Verwalten der Verbindung mit der Datenquelle aus. Der Anbietertyp wird üblicherweise durch den Typ der Datenbank bestimmt, mit der Sie eine Verbindung herstellen. Klicken Sie auf die Schaltfläche **Weiter** oder auf die Registerkarte **Verbindung**.

  - Registerkarte **Verbindung**

      Die Inhalte dieser Registerkarte hängen vom ausgewählten Anbieter ab. Obwohl es viele Typen von Anbietern gibt, werden in diesem Abschnitt die Verbindungen für die beiden gängigsten: SQL-und ODBC-Daten behandelt. Die weiteren Verbindungen sind ähnliche Variationen der hier beschriebenen Felder.

      Für SQL-Daten:

      1. **Servernamen auswählen oder eingeben:** Klicken Sie auf das Dropdown Listen Menü, um alle registrierten Datenserver im Netzwerk anzuzeigen, und wählen Sie eine aus.

      1. **Geben Sie Informationen zum Anmelden am Server ein:** Geben Sie einen Benutzernamen und ein Kennwort ein, um sich beim Datenserver anzumelden.

         > [!NOTE]
         > Es besteht ein Sicherheitsproblem mit dem Feature „Kennwortspeicherung zulassen“ im Dialogfeld „Datenverknüpfungseigenschaften“. Der Abschnitt „Geben Sie Informationen zur Anmeldung beim Server ein“ enthält zwei Optionsschaltflächen:
         >
         > - **Integrierte Sicherheit von Windows NT verwenden**
         > - **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**
         >
         > Wenn Sie **Bestimmten Benutzernamen und ein Kennwort verwenden** aktivieren, erhalten Sie die Möglichkeit zur Speicherung des Kennworts (über das Kontrollkästchen „Kennwortspeicherung zulassen“). Diese Option ist jedoch nicht sicher. Es wird empfohlen, die Option **Integrierte Sicherheit von Windows NT verwenden** auszuwählen. Diese Option ist sicher, weil das Kennwort verschlüsselt wird.
         > Es kann Situationen geben, in denen die Option „Kennwortspeicherung zulassen“ benötigt wird. Wenn Sie beispielsweise eine Bibliothek mit einer privaten Datenbanklösung veröffentlichen, sollten Sie nicht direkt auf die Datenbank zugreifen, sondern stattdessen eine Middle-Tier-Anwendung verwenden, um den Benutzer (über ein Authentifizierungsschema Ihrer Wahl) zu überprüfen und die Art der Daten einzuschränken, die für den Benutzer verfügbar sind.

      1. **Wählen Sie die Datenbank auf dem Server aus:** Klicken Sie auf das Dropdown Listen Menü, um alle registrierten Datenbanken auf dem Datenserver anzuzeigen, und wählen Sie einen aus.

         \- oder -

         **Fügen Sie eine Datenbankdatei als Datenbanknamen an:** Geben Sie eine Datei an, die als Datenbank verwendet werden soll. Geben Sie den expliziten Pfadnamen ein.

      Für ODBC-Daten:

      1. **Geben Sie die Datenquelle an:** Sie können einen Datenquellen Namen oder eine Verbindungs Zeichenfolge verwenden.

         **Datenquellen Namen verwenden:** Diese Dropdown Liste zeigt Datenquellen an, die auf Ihrem Computer registriert sind. Sie können Datenquellen vorab über den ODBC-Datenquellenadministrator einrichten.

         \- oder -

         **Verbindungs Zeichenfolge verwenden:** Geben Sie entweder eine bereits erhaltene Verbindungs Zeichenfolge ein, oder klicken Sie auf die Schaltfläche **Erstellen** . Das Dialogfeld **Datenquelle auswählen** wird angezeigt. Wählen Sie eine Datei oder eine Computerdatenquelle aus, und klicken Sie auf **OK**.

         > [!NOTE]
         > Sie können eine Verbindungszeichenfolge abrufen, indem Sie die Eigenschaften einer vorhandenen Verbindung im **Server-Explorer** anzeigen, oder Sie können eine Verbindung erstellen, indem Sie im **Server-Explorer** auf **Verbindung hinzufügen** doppelklicken.

      1. **Geben Sie Informationen zum Anmelden am Server ein:** Geben Sie einen Benutzernamen und ein Kennwort ein, um sich beim Datenserver anzumelden.

      1. Geben Sie den Anfangskatalog ein, der verwendet werden soll.

      1. Klicken Sie auf **Verbindung testen**. Wenn der Test erfolgreich war, klicken Sie auf **OK**. Falls der Test nicht erfolgreich war, überprüfen Sie Ihre Anmeldeinformationen, oder versuchen Sie es mit einer anderen Datenbank oder einem anderen Datenserver.

  - Registerkarte **erweitert**

      **Netzwerkeinstellungen:** Geben Sie die Identitätswechsel **Ebene** an (die Ebene des Identitäts Wechsels, die der Server beim Annehmen der Identität des Clients verwenden darf; entspricht direkt den RPC-Identitätswechsel Ebenen) und der **Schutz Ebene** (die Ebene des Schutzes von Daten, die zwischen Client und Server gesendet werden, entspricht direkt den RPC-Schutz Ebenen).

      **Sonstige:** Geben Sie unter **Verbindungs Timeout**die Anzahl der Sekunden an, die im Leerlauf vor einem Timeout zulässig sind. Geben Sie in **Zugriffsberechtigungen** die Zugriffsberechtigungen für die Datenverbindung an.

      Weitere Informationen zu erweiterten Initialisierungseigenschaften finden Sie in der Dokumentation zum jeweiligen OLE DB-Anbieter.

  - Registerkarte **Alle**

      Auf dieser Registerkarte wird eine Zusammenfassung der Initialisierungseigenschaften für die angegebene Datenquelle und Verbindung angezeigt. Sie können diese Werte bearbeiten.

      Klicken Sie auf **OK**, um den Vorgang abzuschließen. Das Dialogfeld **Datenbankobjekt auswählen** wird angezeigt. Wählen Sie in diesem Dialogfeld die Tabelle, Ansicht oder gespeicherte Prozedur aus, die der Consumer verwenden wird.

- **Klasse**

   Nachdem Sie eine Datenquelle ausgewählt haben, wird dieses Feld mit einem Standardklassennamen aufgefüllt, der auf der ausgewählten Tabelle oder gespeicherten Prozedur basiert (siehe **Datenquelle auswählen** unten). Sie können den Klassennamen bearbeiten.

- **H-Datei**

   Nachdem Sie eine Datenquelle ausgewählt haben, wird dieses Feld mit einem standardmäßigen Headerklassennamen aufgefüllt, der auf der ausgewählten Tabelle oder gespeicherten Prozedur basiert (siehe **Datenquelle auswählen** unten). Sie können den Namen der Headerdatei bearbeiten oder eine vorhanden Headerdatei auswählen.

- **Attributiert**

   Diese Option gibt an, ob der Assistent Consumerklassen mithilfe von Attributen oder Vorlagendeklarationen erstellt. Bei Auswahl dieser Option verwendet der Assistent Attribute anstelle von Vorlagendeklarationen (dies ist die Standardoption). Wenn Sie diese Option deaktivieren, verwendet der Assistent Vorlagendeklarationen anstelle von Attributen.

  - Wenn Sie als **Typ** für den Consumer **Tabelle** auswählen, verwendet der Assistent die Attribute `db_source` und `db_table`, um die Klassendeklarationen für die Tabelle und den Tabellenaccessor zu erstellen, und verwendet `db_column` zum Erstellen der Spaltenzuordnung. Beispielsweise wird diese Zuordnung erstellt:

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     Stattdessen können auch die `CTable`-Vorlagenklasse zum Deklarieren der Tabellen- und Tabellenaccessorklasse sowie die Makros BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet werden, um die Spaltenzuordnung zu erstellen, wie in diesem Beispiel:

    ```cpp
    // Table accessor class
        class COrdersAccessor; // Table class
        class COrders : public CTable<CAccessor<COrdersAccessor>>;
    // ...
    // Column map
        BEGIN_COLUMN_MAP(COrderDetailsAccessor)
            COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
            COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
            // ...
        END_COLUMN_MAP()
    ```

  - Wenn Sie als **Typ** für den Consumer **Befehl** auswählen, verwendet der Assistent die Attribute `db_source` und `db_command` und verwendet `db_column` zum Erstellen der Spaltenzuordnung. Beispielsweise wird diese Zuordnung erstellt:

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     Stattdessen können auch die Befehls- und Befehlsaccessor-Klassendeklarationen in der H-Datei der Befehlsklasse verwendet werden, wie in diesem Beispiel:

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     Weitere Informationen finden Sie [Untergrund Legende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

- **Typ**

   Aktivieren Sie eine dieser Optionsschaltflächen, um anzugeben, ob die Consumerklasse von `CTable` oder `CCommand` (Standard) abgeleitet wird.

  - **Table**

      Aktivieren Sie diese Option, wenn Sie `CTable` oder `db_table` zum Erstellen der Tabellen- und Tabellenaccessor-Klassendeklarationen verwenden möchten.

  - **Befehl**

      Wählen Sie diese Option aus, wenn Sie `CCommand` oder `db_command` zum Erstellen der Tabellen- und Tabellenaccessor-Klassendeklarationen verwenden möchten. Dies ist die Standardauswahl.

- **Unterstützung**

   Aktivieren Sie die Kontrollkästchen, um die Art der Aktualisierung anzugeben, die im Consumer unterstützt wird (standardmäßig sind dies keine). Mit jeder der folgenden Optionen werden [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) und die geeigneten Einträge für [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) in der Eigenschaftenzuordnung festgelegt.

  - **Änderung**

      Gibt an, dass der Consumer das Aktualisieren von Zeilendaten im Rowset unterstützt.

  - **Einfügen**

      Gibt an, dass der Consumer das Einfügen von Zeilen in das Rowset unterstützt.

  - **Löschen**

      Gibt an, dass der Consumer das Löschen von Zeilen aus dem Rowset unterstützt.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[ATL-OLE DB-Consumer](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Verbindungszeichenfolgen und Datenverknüpfungen (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
