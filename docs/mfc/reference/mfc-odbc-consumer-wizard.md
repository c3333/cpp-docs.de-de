---
title: MFC-ODBC-Consumer-Assistent
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: fd7e8df6692889914af2dd060ac42ed4ca3ebb8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446423"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC-ODBC-Consumer-Assistent

::: moniker range="vs-2019"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=vs-2017"

Dieser Assistent richtet eine ODBC-Recordsetklasse und die Daten Bindungen ein, die für den Zugriff auf die angegebene Datenquelle erforderlich sind.

## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente

- **Data Source**

  Mithilfe der Schaltfläche **Datenquelle** können Sie die angegebene Datenquelle mithilfe des angegebenen ODBC-Treibers einrichten. Weitere Informationen zu Datenquellen Dateien (DSN) finden Sie unter [Datei Datenquellen](/sql/odbc/reference/file-data-sources) im ODBC SDK.

  Das Dialogfeld **Datenquelle auswählen** verfügt über zwei Registerkarten:

  - Registerkarte " **Datei Datenquelle** ":

     Das Feld **Suchen in** gibt das Verzeichnis an, in dem die Dateien ausgewählt werden sollen, die als Datenquellen verwendet werden sollen. Der Standardwert ist "\Programme\Gemeinsame Dateien\ODBC\Data Sources". Die vorhandenen Datei Datenquellen (DSN-Dateien) werden im Haupt Listenfeld angezeigt. Sie können die Datenquellen entweder im Vorfeld mithilfe der Registerkarte **Datei-DSN** des [ODBC-Datenquellen-Administrators](/sql/odbc/admin/odbc-data-source-administrator)oder mithilfe dieses Dialog Felds erstellen.

     Um in diesem Dialogfeld eine neue Datei Datenquelle zu erstellen, klicken Sie auf `New`, um einen DSN-Namen anzugeben. Das Dialogfeld **neue Datenquelle erstellen** wird angezeigt. Wählen Sie im Dialogfeld **neue Datenquelle erstellen** einen geeigneten Treiber aus, und klicken Sie auf `Next`. Klicken Sie auf **Durchsuchen**, und wählen Sie den Namen der Datei aus, die als Datenquelle verwendet werden soll (Sie müssen "alle Dateien" auswählen, um nicht-DSN-Dateien, z. b. xls-Dateien), anzuzeigen. Klicken Sie auf `Next`und dann auf **Fertig**stellen. (Wenn Sie eine nicht-DSN-Datei ausgewählt haben, erhalten Sie ein Treiber spezifisches Dialogfeld, z. b. "ODBC Microsoft Excel Setup", mit dem die Datei in einen DSN konvertiert wird.)

     > [!NOTE]
     > Mit dem ODBC-Datenquellen-Administrator können Sie eine neue Datei Datenquelle auch im Vorfeld erstellen. Klicken Sie im **Startmenü** auf **Einstellungen**, **Systemsteuerung**, **Verwaltung**, **Datenquellen (ODBC)** und dann auf **ODBC-Daten**Quellen-Administrator.

     Im Feld **DSN-Name** können Sie einen Namen für die Datei Datenquelle angeben. Sie müssen sicherstellen, dass der DSN-Name mit der entsprechenden Dateierweiterung endet, z. b. xls für Excel-Dateien oder MDB für Zugriffs Dateien.

     Weitere Informationen zu DSNs finden Sie unter [Datei Datenquellen](/sql/odbc/reference/file-data-sources) im ODBC SDK.

  - Registerkarte " **Computer Datenquelle** ":

     Auf dieser Registerkarte werden die System-und Benutzerdaten Quellen aufgelistet. Benutzerdaten Quellen sind spezifisch für einen Benutzer auf diesem Computer. System Datenquellen können von allen Benutzern auf diesem Computer oder einem systemweiten Dienst verwendet werden. Siehe [Computer Datenquellen](/sql/odbc/reference/machine-data-sources) im ODBC-SDK

     Weitere Informationen zu ODBC-Datenquellen finden Sie unter [Datenquellen](/sql/odbc/reference/data-sources) im ODBC-SDK.

  Klicken Sie auf **OK**, um den Vorgang abzuschließen. Das Dialogfeld **Datenbankobjekt auswählen** wird angezeigt. Wählen Sie in diesem Dialogfeld die Tabelle oder Sicht aus, die der Consumer verwenden soll. Beachten Sie, dass Sie mehrere Sichten und Tabellen auswählen können, indem Sie die Steuerelement Taste gedrückt halten, während Sie auf die Elemente klicken. Klicken Sie auf **OK**, um den Vorgang abzuschließen.

- **Klasse**

   Der Name der Consumerklasse, der standardmäßig auf dem Namen der von Ihnen ausgewählten Datei-oder Computer Datenquelle basiert.

- **H-Datei**

   Der Name der Header Datei der Consumerklasse, der standardmäßig auf dem Namen der von Ihnen ausgewählten Datei-oder Computer Datenquelle basiert.

- **CPP-Datei**

   Der Name der Implementierungs Datei für die Consumerklasse, der standardmäßig auf dem Namen der von Ihnen ausgewählten Datei-oder Computer Datenquelle basiert.

- **Typ**

   Gibt an, ob das Recordset ein Dynaset (Standard) oder eine Momentaufnahme ist.

   - **Dynaset**: gibt an, dass das Recordset ein Dynaset ist. Ein Dynaset ist das Ergebnis einer Abfrage, die eine indizierte Sicht in den Daten der abgefragten Datenbank bereitstellt. Ein Dynaset speichert nur einen integralen Index in den ursprünglichen Daten und bietet somit eine Leistungssteigerung über eine Momentaufnahme. Der Index verweist direkt auf jeden Datensatz, der als Ergebnis einer Abfrage gefunden wurde, und gibt an, ob ein Datensatz entfernt wurde. Sie haben auch Zugriff auf aktualisierte Informationen in den abgefragten Datensätzen. Dies ist die Standardoption.

   - **Snapshot**: gibt an, dass das Recordset eine Momentaufnahme ist. Eine Momentaufnahme ist das Ergebnis einer Abfrage und eine Sicht in einer Datenbank zu einem bestimmten Zeitpunkt. Alle Datensätze, die als Ergebnis der Abfrage gefunden werden, werden zwischengespeichert, sodass keine Änderungen an den ursprünglichen Datensätzen angezeigt werden.

- **Alle Spalten binden**

   Gibt an, ob alle Spalten in der ausgewählten Tabelle gebunden sind. Wenn Sie dieses Feld (Standard) auswählen, sind alle Spalten gebunden. Wenn Sie dieses Feld nicht aktivieren, werden keine Spalten gebunden, und Sie müssen Sie manuell in der Recordset-Klasse binden.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Hinzufügen neuer Funktionen mit Code-Assistenten](../../ide/adding-functionality-with-code-wizards-cpp.md)
