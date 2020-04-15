---
title: MFC-ODBC-Consumer-Assistent
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373021"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC-ODBC-Consumer-Assistent

::: moniker range="vs-2019"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=vs-2017"

Dieser Assistent richtet eine ODBC-Recordset-Klasse und die Datenbindungen ein, die für den Zugriff auf die angegebene Datenquelle erforderlich sind.

## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente

- **Data source**

  Mit der Schaltfläche **Datenquelle** können Sie die angegebene Datenquelle mit dem angegebenen ODBC-Treiber einrichten. Weitere Informationen zu Datenquellendateien (Data Source Files, DSN) finden Sie unter [Dateidatenquellen](/sql/odbc/reference/file-data-sources) im ODBC SDK.

  Das Dialogfeld **Datenquelle auswählen** verfügt über zwei Registerkarten:

  - **Registerkarte Dateidatenquelle:**

     Das Feld **Suchen in** gibt das Verzeichnis an, in dem Dateien ausgewählt werden sollen, die als Datenquellen verwendet werden sollen. Der Standardwert ist die Option "Programmdateien", "Gemeinsame Dateien", "ODBC" und "Datenquellen". Die vorhandenen Dateidatenquellen (.dsn-Dateien) werden im Hauptlistenfeld angezeigt. Sie können die Datenquellen entweder im Voraus über die Registerkarte **Datei-DSN** im [ODBC-Datenquellenadministrator](/sql/odbc/admin/odbc-data-source-administrator)einrichten oder mithilfe dieses Dialogfelds neue erstellen.

     Um eine neue Dateidatenquelle aus diesem `New` Dialogfeld zu erstellen, klicken Sie auf , um einen DSN-Namen anzugeben. das Dialogfeld **Neue Datenquelle erstellen** wird angezeigt. Wählen Sie im Dialogfeld **Neue Datenquelle** erstellen `Next`einen entsprechenden Treiber aus, und klicken Sie auf ; Klicken Sie auf **Durchsuchen**, und wählen Sie den Namen der Datei aus, die als Datenquelle verwendet werden soll (Sie müssen "Alle Dateien" auswählen, um Nicht-DSN-Dateien anzuzeigen, z. B. .xls-Dateien); Klicken `Next`Sie auf , und klicken Sie dann auf **Fertig stellen**. (Wenn Sie eine Nicht-DSN-Datei ausgewählt haben, erhalten Sie ein treiberspezifisches Dialogfeld, z. B. "ODBC Microsoft Excel Setup", das die Datei in eine DSN konvertiert.)

     > [!NOTE]
     > Sie können zuvor auch eine neue Dateidatenquelle mit dem ODBC-Datenquellenadministrator erstellen. Wählen Sie im **Startmenü** **Einstellungen**, **Systemsteuerung**, **Verwaltungstools** **, Datenquellen (ODBC) und**dann **ODBC Data Source Administrator**aus.

     Im Feld **DSN Name** können Sie einen Namen für die Dateidatenquelle angeben. Sie müssen sicherstellen, dass der DSN-Name mit der entsprechenden Dateierweiterung endet, z. B. .xls für Excel-Dateien oder .mdb für Access-Dateien.

     Weitere Informationen zu DSNs finden Sie unter [Dateidatenquellen](/sql/odbc/reference/file-data-sources) im ODBC SDK.

  - **Registerkarte Computerdatenquelle:**

     Auf dieser Registerkarte werden System- und BenutzerDATENquellen aufgelistet. Benutzerdatenquellen sind spezifisch für einen Benutzer auf diesem Computer. Systemdatenquellen können von allen Benutzern auf diesem Computer oder auf einem systemweiten Dienst verwendet werden. Siehe [Computerdatenquellen](/sql/odbc/reference/machine-data-sources) im ODBC SDK

     Weitere Informationen zu ODBC-Datenquellen finden Sie unter [Datenquellen](/sql/odbc/reference/data-sources) im ODBC SDK.

  Klicken Sie auf **OK**, um den Vorgang abzuschließen. Das Dialogfeld **Datenbankobjekt auswählen** wird angezeigt. Wählen Sie in diesem Dialogfeld die Tabelle oder Ansicht aus, die der Consumer verwenden soll. Beachten Sie, dass Sie mehrere Ansichten und Tabellen auswählen können, indem Sie die Steuertaste halten, während Sie auf die Elemente klicken. Klicken Sie auf **OK**, um den Vorgang abzuschließen.

- **Class**

   Der Name der Consumerklasse, der standardmäßig auf dem Namen der ausgewählten Datei oder Computerdatenquelle basiert.

- **H-Datei**

   Der Name der Consumer-Klassenheaderdatei, basierend auf dem Namen der ausgewählten Datei oder Computerdatenquelle.

- **CPP-Datei**

   Der Name der Implementierungsdatei der Consumerklasse, die standardmäßig auf dem Namen der ausgewählten Datei oder Computerdatenquelle basiert.

- **Typ**

   Gibt an, ob es sich bei dem Recordset um ein Dynaset (Standard) oder einen Snapshot handelt.

  - **Dynaset**: Gibt an, dass es sich bei dem Recordset um ein Dynaset handelt. Ein Dynaset ist das Ergebnis einer Abfrage, die eine indizierte Ansicht in die Daten der abgefragten Datenbank bereitstellt. Ein Dynaset speichert nur einen integralen Index zu den ursprünglichen Daten und bietet somit eine Leistungssteigerung gegenüber einem Snapshot. Der Index zeigt direkt auf jeden Datensatz, der als Ergebnis einer Abfrage gefunden wurde, und gibt an, ob ein Datensatz entfernt wird. Sie haben auch Zugriff auf aktualisierte Informationen in den abgefragten Datensätzen. Dies ist die Standardoption.

  - **Snapshot**: Gibt an, dass es sich bei dem Recordset um einen Snapshot handelt. Ein Snapshot ist das Ergebnis einer Abfrage und eine Ansicht in einer Datenbank zu einem Zeitpunkt. Alle Datensätze, die als Ergebnis der Abfrage gefunden wurden, werden zwischengespeichert, sodass keine Änderungen an den ursprünglichen Datensätzen angezeigt werden.

- **Binden aller Spalten**

   Gibt an, ob alle Spalten in der ausgewählten Tabelle gebunden sind. Wenn Sie dieses Feld (Standard) aktivieren, sind alle Spalten gebunden. Wenn Sie dieses Feld nicht auswählen, sind keine Spalten gebunden, und Sie müssen sie manuell in der Recordset-Klasse binden.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)
