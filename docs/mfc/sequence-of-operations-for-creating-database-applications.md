---
title: Reihenfolge der Operationen zur Erstellung Datenbankanwendungen
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372775"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Reihenfolge der Operationen zur Erstellung Datenbankanwendungen

Die folgende Tabelle zeigt Ihre Rolle und die Rolle des Frameworks beim Schreiben von Datenbankanwendungen.

> [!NOTE]
> Die Visual C++-Umgebung und die Assistenten unterstützen DAO nicht (obwohl die DAO-Klassen enthalten sind und Sie sie weiterhin verwenden können). Microsoft empfiehlt, ODBC für neue MFC-Projekte zu verwenden. Sie sollten DAO nur bei der Verwaltung vorhandener Anwendungen verwenden.

### <a name="creating-database-applications"></a>Erstellen von Datenbankanwendungen

|Aufgabe|Sie tun|Der Rahmen|
|----------|------------|------------------------|
|Entscheiden Sie, ob die MFC ODBC- oder DAO-Klassen verwendet werden sollen.|Verwenden Sie ODBC für neue MFC-Projekte. Verwenden Sie DAO nur, um vorhandene Anwendungen zu verwalten. Allgemeine Informationen finden Sie im Artikel [Data Access Programming](../data/data-access-programming-mfc-atl.md).|Das Framework stellt Klassen zur Verfügung, die den Datenbankzugriff unterstützen.|
|Erstellen Sie Ihre Skelettanwendung mit Datenbankoptionen.|Führen Sie den MFC-Anwendungs-Assistenten aus. Wählen Sie Optionen auf der Seite Datenbanksupport aus. Wenn Sie eine Option auswählen, die eine Datensatzansicht erstellt, geben Sie auch Folgendes an:<br /><br />- Datenquellen- und Tabellennamen oder -namen<br />- Abfragenamen oder -namen.|Der MFC-Anwendungs-Assistent erstellt Dateien und gibt die erforderlichen Includes an. Abhängig von den von Ihnen angegebenen Optionen können die Dateien eine Recordset-Klasse enthalten.|
|Entwerfen Sie das Datenbankformular oder die Formulare.|Verwenden Sie den Visual C++-Dialogeditor, um Steuerelemente in den Dialogvorlagenressourcen für Ihre Datensatzansichtsklassen zu platzieren.|Der MFC-Anwendungs-Assistent erstellt eine leere Dialogvorlagenressource, die Sie ausfüllen können.|
|Erstellen Sie bei Bedarf zusätzliche Datensatzansichts- und Recordsetklassen.|Verwenden Sie die Klassenansicht, um die Klassen und den Dialogeditor zum Entwerfen der Ansichten zu erstellen.|Die Klassenansicht erstellt zusätzliche Dateien für Ihre neuen Klassen.|
|Erstellen Sie Recordset-Objekte nach Bedarf in Ihrem Code. Verwenden Sie jedes Recordset, um Datensätze zu bearbeiten...|Ihre Recordsets basieren auf den Klassen, die von [CRecordset](../mfc/reference/crecordset-class.md) mit den Assistenten abgeleitet wurden.|ODBC verwendet Datensatzfeldaustausch (Record Field Exchange, RFX), um Daten zwischen der Datenbank und den Felddatenmembern Ihres Recordsets auszutauschen. Wenn Sie eine Datensatzansicht verwenden, tauscht der Dialogdatenaustausch (DDX) Daten zwischen dem Recordset und den Steuerelementen in der Datensatzansicht aus.|
|... oder erstellen Sie eine explizite [CDatabase](../mfc/reference/cdatabase-class.md) in Ihrem Code für jede Datenbank, die Sie öffnen möchten.|Legen Sie Ihre Recordset-Objekte auf den Datenbankobjekten ab.|Das Datenbankobjekt stellt eine Schnittstelle zur Datenquelle bereit.|
|Binden Sie Datenspalten dynamisch an Ihr Recordset.|Fügen Sie in ODBC der abgeleiteten Recordset-Klasse Code hinzu, um die Bindung zu verwalten. Siehe den Artikel [Recordset: Dynamically Binding Data Columns (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Siehe auch

[Erstellen im Framework](../mfc/building-on-the-framework.md)<br/>
[Reihenfolge der Operationen zur Erstellung von MFC-Anwendungen](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Reihenfolge der Operationen zur Erstellung von OLE-Anwendungen](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Operationssequenz zur Erstellung von ActiveX-Steuerelementen](../mfc/sequence-of-operations-for-creating-activex-controls.md)
