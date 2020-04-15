---
title: Datenbankunterstützung, MFC-Anwendungs-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: c13d56d2fee45e130aba81168188bec6d8828d51
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365880"
---
# <a name="database-support-mfc-application-wizard"></a>Datenbankunterstützung, MFC-Anwendungs-Assistent

Diese Seite bietet Optionen, mit denen Sie die Ebene der Datenbankunterstützung (bei Bedarf plus Datenquelle) für Ihr Projekt angeben können.

- **Datenbankunterstützung**

   Legt die Ebene der Datenbankunterstützung für Ihr Projekt fest.

   |Option|BESCHREIBUNG|
   |------------|-----------------|
   |**None**|Bietet keine Datenbankunterstützung. Dies ist die Standardoption.|
   |**Nur Headerdateien**|Bietet die grundlegende Ebene der Datenbankunterstützung für Ihre Anwendung. Wenn Sie ODBC-Unterstützung unter **Clienttyp**auswählen, enthält der MFC-Anwendungs-Assistent in Ihrem Projekt die Headerdatei AFXDB. H. Es fügt Verknüpfungsbibliotheken hinzu, erstellt jedoch keine datenbankspezifischen Klassen. Sie können später Recordsets erstellen und diese zum Überprüfen und Aktualisieren von Datensätzen verwenden. Wenn Sie OLE DB-Unterstützung unter **Clienttyp**auswählen, sind die folgenden Headerdateien enthalten: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Datenbankansicht ohne Dateiunterstützung**|Enthält Datenbankheaderdateien, Linkbibliotheken, eine Datensatzansicht und ein Recordset. (Verfügbar nur für Anwendungen mit der **Unterstützungsoption Dokument-/Ansichtsarchitektur,** die auf der Seite [Anwendungstyp](../../mfc/reference/application-type-mfc-application-wizard.md) ausgewählt ist.) Diese Option umfasst Die Unterstützung für Dokumente, aber keine Serialisierungsunterstützung. Wenn Sie eine Datenbankansicht einschließen möchten, müssen Sie die Quelle der Daten angeben.|
   |**Datenbankansicht mit Dateiunterstützung**|Enthält Datenbankheaderdateien, Linkbibliotheken, eine Datensatzansicht und ein Recordset. (Verfügbar nur für Anwendungen mit der **Unterstützungsoption Dokument-/Ansichtsarchitektur,** die auf der Seite **Anwendungstyp** ausgewählt ist.) Diese Option unterstützt die Dokumentserialisierung, mit der Sie z. B. eine Benutzerprofildatei aktualisieren können. Datenbankanwendungen arbeiten in der Regel pro Datensatz und nicht pro Datei und müssen daher nicht serialisiert werden. Möglicherweise haben Sie jedoch eine spezielle Verwendung für die Serialisierung. Wenn Sie eine Datenbankansicht einschließen möchten, müssen Sie die Quelle der Daten angeben.|

   > [!NOTE]
   > Wenn Sie unter **Datenbankunterstützung**entweder **die Datenbankansicht ohne Dateiunterstützung** oder die **Datenbankansicht mit Dateiunterstützung**auswählen, unterscheidet sich die Ansichtsklassenableitung je nach **Clienttypauswahl** wie folgt:

  - Wenn Sie **ODBC** unter **Clienttyp**auswählen, leitet sich die Ansichtsklasse der Anwendung von [CRecordView](../../mfc/reference/crecordview-class.md)ab. Diese Klasse ist einer [CRecordset-derived-Klasse](../../mfc/reference/crecordset-class.md)zugeordnet, die der MFC-Anwendungs-Assistent ebenfalls für Sie erstellt. Mit dieser Option erhalten Sie eine formularbasierte Anwendung, in der die Datensatzansicht zum Anzeigen und Aktualisieren von Datensätzen über das Recordset verwendet wird.

  - Wenn Sie **OLE DB** unter **Clienttyp**auswählen, leitet sich die Ansichtsklasse von [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)ab und ist einer [CTable-](../../data/oledb/ctable-class.md) oder [CCommand-abgeleiteten](../../data/oledb/ccommand-class.md)Klasse zugeordnet.

- **Clienttyp**

   Gibt an, ob das Projekt OLE DB- oder ODBC-Klassen verwendet.

   |Option|BESCHREIBUNG|
   |------------|-----------------|
   |**OLE DB**|Wenn diese Option ausgewählt ist, ruft das Klicken auf die Schaltfläche **Datenquelle** den Assistenten für **Datenverknüpfungseigenschaften** auf, um Eine Verbindung zu einer OLE DB-Datenquelle herzustellen.|
   |**ODBC**|Wenn diese Option ausgewählt ist, ruft das Klicken auf die Schaltfläche **Datenquelle** den Assistenten Datenquelle **auswählen** auf, um Ihnen beim Erstellen einer Verbindung mit einer ODBC-Datenquelle zu helfen.|

- **Data source**

   > [!NOTE]
   > Der ATL OLE DB Consumer-Assistent und der MFC ODBC Consumer-Assistent sind in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Klicken Sie auf die Schaltfläche **Datenquelle,** um eine Datenquelle mit dem angegebenen Treiber oder Anbieter und der angegebenen Datenbank einzurichten. Wenn Sie OLE DB in der Option **Clienttyp** ausgewählt haben, wird mit dieser Schaltfläche das Dialogfeld **Datenverknüpfungseigenschaften** angezeigt. Wenn Sie ODBC in der Option **Clienttyp** ausgewählt haben, wird diese Schaltfläche im Dialogfeld **Datenquelle auswählen** angezeigt. Diese Option ist nur verfügbar, wenn Sie eine Datenbankansicht in Ihre Anwendung aufnehmen möchten.

   |Option|BESCHREIBUNG|
   |------------|-----------------|
   |**Datenverknüpfungseigenschaften** (OLE DB)|Erstellt die angegebene Datenquelle mithilfe des angegebenen OLE DB-Anbieters. Sie müssen den OLE DB-Anbieter, den Speicherort der Daten, die Datenquelle, die Anmelde-ID und (optional) ein Kennwort angeben. Weitere Informationen zu diesem Dialogfeld finden Sie unter **Datenquelle** im [ATL OLE DB Consumer Wizard](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Datenquelle auswählen** (ODBC)|Legt die angegebene Datenquelle mithilfe des angegebenen ODBC-Treibers fest. Sie müssen einen Datenquellennamen auswählen, um eine Tabelle für die Datenquelle auszuwählen. Der Assistent bindet alle Spalten der Tabelle an `CRecordset`die Membervariablen einer -derived-Klasse. Weitere Informationen zu diesem Dialogfeld finden Sie unter **Datenquelle** im [MFC ODBC Consumer Wizard](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

- **Zugeschriebene Datenbankklasse generieren**

   Nur für OLE DB-Clients verfügbar. Gibt an, ob die Datenbankklassen im generierten Projekt Attribute verwenden.

- **Binden aller Spalten**

   Nur für ODBC-Clients verfügbar. Gibt an, ob alle Spalten in der ausgewählten Tabelle gebunden sind. Wenn Sie dieses Feld aktivieren, sind alle Spalten gebunden. Wenn Sie dieses Feld nicht auswählen, sind keine Spalten gebunden, und Sie müssen sie manuell in der Recordset-Klasse binden.

- **Typ**

   Nur für ODBC-Clients verfügbar. Gibt an, ob es sich bei dem Recordset um ein Dynaset oder einen Snapshot handelt, wie in der folgenden Tabelle beschrieben.

   |Option|BESCHREIBUNG|
   |------------|-----------------|
   |**Dynaset**|Gibt an, dass es sich bei dem Recordset um ein Dynaset handelt. Ein Dynaset ist das Ergebnis einer Abfrage, die eine indizierte Ansicht in die Daten der abgefragten Datenbank bereitstellt. Ein Dynaset speichert nur einen integralen Index zu den ursprünglichen Daten und bietet somit eine Leistungssteigerung gegenüber einem Snapshot. Der Index zeigt direkt auf jeden Datensatz, der als Ergebnis einer Abfrage gefunden wurde, und gibt an, ob ein Datensatz entfernt wird. Sie haben auch Zugriff auf aktualisierte Informationen in den abgefragten Datensätzen.|
   |**Momentaufnahme**|Gibt an, dass es sich bei dem Recordset um einen Snapshot handelt. Ein Snapshot ist das Ergebnis einer Abfrage und eine Ansicht in einer Datenbank zu einem Zeitpunkt. Alle Datensätze, die als Ergebnis der Abfrage gefunden wurden, werden zwischengespeichert, sodass keine Änderungen an den ursprünglichen Datensätzen angezeigt werden.|

## <a name="see-also"></a>Siehe auch

[MFC-Anwendungs-Assistent](../../mfc/reference/mfc-application-wizard.md)
