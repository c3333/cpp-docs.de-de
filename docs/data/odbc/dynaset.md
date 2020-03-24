---
title: Dynaset
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213238"
---
# <a name="dynaset"></a>Dynaset

In diesem Thema werden Dynasets beschrieben und Ihre [Verfügbarkeit](#_core_availability_of_dynasets)erörtert.

> [!NOTE]
>  Dieses Thema bezieht sich auf die MFC-ODBC-Klassen, einschließlich [CRecordset](../../mfc/reference/crecordset-class.md). Weitere Informationen zu Dynasets in den DAO-Klassen finden Sie unter [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Mit DAO können Sie Dynaset-Type-Recordsets öffnen.

Ein Dynaset ist ein Recordset mit dynamischen Eigenschaften. Während der Lebensdauer bleibt ein Recordset-Objekt im Dynaset-Modus (in der Regel als Dynaset bezeichnet) wie folgt mit der Datenquelle synchronisiert. In einer mehr Benutzerumgebung können andere Benutzerdaten Sätze bearbeiten oder löschen, die sich in Ihrem Dynaset befinden, oder der Tabelle, die ihr Dynaset darstellt, Datensätze hinzufügen. Datensätze, die von der Anwendung hinzugefügt oder aus dem Recordset gelöscht werden, werden in Ihrem Dynaset widergespiegelt. Datensätze, die von anderen Benutzern der Tabelle hinzugefügt werden, werden erst dann in Ihrem Dynaset reflektiert, wenn Sie das Dynaset durch Aufrufen seiner `Requery` Member-Funktion neu erstellen. Wenn andere Benutzerdaten Sätze löschen, überspringt MFC-Code die Löschungen in Ihrem Recordset. Änderungen an vorhandenen Datensätzen durch andere Benutzer werden in Ihrem Dynaset widergespiegelt, sobald Sie einen Bildlauf zum betroffenen Datensatz durchführen.

Ebenso werden Änderungen, die Sie an Datensätzen in einem Dynaset vornehmen, in Dynasets, die von anderen Benutzern verwendet werden, widergespiegelt. Datensätze, die Sie hinzufügen, werden nicht in den Dynasets anderer Benutzer widergespiegelt, bis Sie Ihre Dynasets anweisen. Datensätze, die Sie löschen, werden in den Recordsets anderer Benutzer als "gelöscht" markiert. Wenn Sie über mehrere Verbindungen mit derselben Datenbank (mehrere `CDatabase` Objekte) verfügen, haben Recordsets, die diesen Verbindungen zugeordnet sind, denselben Status wie die Recordsets anderer Benutzer.

Dynasets sind besonders wertvoll, wenn Daten dynamisch sein müssen, z. b. in einem Reservierungssystem für die Fluggesellschaft.

> [!NOTE]
> Um Dynasets verwenden zu können, müssen Sie über einen ODBC-Treiber für Ihre Datenquelle verfügen, der Dynasets unterstützt, und die ODBC-Cursor Bibliothek darf nicht geladen werden. Weitere Informationen finden Sie unter [Verfügbarkeit von Dynasets](#_core_availability_of_dynasets).

Um anzugeben, dass ein Recordset ein Dynaset ist, übergeben Sie `CRecordset::dynaset` als ersten Parameter an die `Open` Member-Funktion des Recordset-Objekts.

> [!NOTE]
> Bei aktualisierbaren Dynasets muss der ODBC-Treiber entweder positionierte UPDATE-Anweisungen oder die `::SQLSetPos` ODBC-API-Funktion unterstützen. Wenn beide unterstützt werden, verwendet MFC `::SQLSetPos` aus Gründen der Effizienz.

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Verfügbarkeit von Dynasets

Die MFC-Datenbankklassen unterstützen Dynasets, wenn die folgenden Anforderungen erfüllt sind:

- Die ODBC-Cursor Bibliotheks-DLL darf für diese Datenquelle nicht verwendet werden.

   Wenn die Cursor Bibliothek verwendet wird, werden einige Funktionen des zugrunde liegenden ODBC-Treibers maskiert, der für die Unterstützung von Dynaset erforderlich ist. Wenn Sie Dynasets verwenden möchten (und der ODBC-Treiber die für Dynasets erforderliche Funktionalität hat, wie im restlichen Teil dieses Abschnitts beschrieben), können Sie bewirken, dass MFC die Cursor Bibliothek nicht lädt, wenn Sie ein `CDatabase` Objekt erstellen. Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und [OpenEx](../../mfc/reference/cdatabase-class.md#openex) oder [Open](../../mfc/reference/cdatabase-class.md#open) Member-Funktion der-Klasse `CDatabase`.

   In der ODBC-Terminologie werden Dynasets und Momentaufnahmen als Cursor bezeichnet. Ein Cursor ist ein Mechanismus, der zum Nachverfolgen seiner Position in einem Recordset verwendet wird.

- Der ODBC-Treiber für Ihre Datenquelle muss keysetgesteuerte Cursor unterstützen.

   Keysetgesteuerte Cursor verwalten Daten aus einer Tabelle, indem Sie einen Satz von Schlüsseln erhalten und speichern. Die Schlüssel werden verwendet, um aktuelle Daten aus der Tabelle abzurufen, wenn der Benutzer einen Bildlauf zu einem bestimmten Datensatz ausführt. Um zu ermitteln, ob Ihr Treiber diese Unterstützung bietet, müssen Sie die `::SQLGetInfo` ODBC-API-Funktion mit dem Parameter *SQL_SCROLL_OPTIONS* aufrufen.

   Wenn Sie versuchen, ein Dynaset ohne Keysetunterstützung zu öffnen, erhalten Sie eine `CDBException` mit dem AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED Wert des Rückgabecodes.

- Der ODBC-Treiber für Ihre Datenquelle muss das erweiterte abrufen unterstützen.

   Das erweiterte abrufen ist die Möglichkeit, einen Bildlauf rückwärts durchführen und die resultierenden Datensätze der SQL-Abfrage weiterleiten zu können. Um zu ermitteln, ob Ihr Treiber diese Fähigkeit unterstützt, können Sie die `::SQLGetFunctions` ODBC-API-Funktion mit dem *SQL_API_SQLEXTENDEDFETCH* -Parameter aufrufen.

Wenn Sie für diese Aufgabe aktualisierbare Dynasets (oder Momentaufnahmen) möchten, muss der ODBC-Treiber auch die `::SQLSetPos` ODBC-API-Funktion oder positionierte Updates unterstützen. Die `::SQLSetPos`-Funktion ermöglicht es MFC, die Datenquelle zu aktualisieren, ohne SQL-Anweisungen zu senden. Wenn diese Unterstützung verfügbar ist, verwendet MFC Sie für die Aktualisierung mithilfe von SQL. Um zu ermitteln, ob der Treiber `::SQLSetPos`unterstützt, müssen Sie `::SQLGetInfo` mit dem *SQL_POS_OPERATIONS* -Parameter aufrufen.

Positionierte Updates verwenden die SQL-Syntax (in der Form, **in der Current of** \<Cursor Name >), um eine bestimmte Zeile in der Tabelle in der Datenquelle zu identifizieren. Um festzustellen, ob der Treiber positionierte Updates unterstützt, können Sie `::SQLGetInfo` mit dem *SQL_POSITIONED_STATEMENTS* -Parameter aufrufen.

Im Allgemeinen erfordern MFC-Dynasets (aber keine Vorwärts-Recordsets) einen ODBC-Treiber mit API-Konformität der Ebene 2. Wenn der Treiber für die Datenquelle mit dem API-Satz der Ebene 1 konform ist, können Sie weiterhin sowohl aktualisierbare als auch schreibgeschützte Momentaufnahmen und Vorwärts-Recordsets, aber keine Dynasets verwenden. Ein Treiber der Ebene 1 kann jedoch Dynasets unterstützen, wenn er erweiterte Abruf-und keysetgesteuerte Cursor unterstützt. Weitere Informationen zu ODBC-Konformitätsstufen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Wenn Sie sowohl Momentaufnahmen als auch Dynasets verwenden möchten, müssen Sie Sie auf zwei verschiedenen `CDatabase` Objekten (zwei unterschiedliche Verbindungen) aufbauen.

Im Gegensatz zu Momentaufnahmen, die Zwischenspeicher verwenden, der von der ODBC-Cursor Bibliothek verwaltet wird, rufen Dynasets einen Datensatz direkt aus der Datenquelle ab, sobald Sie einen Bildlauf zu diesem durchführen. Dadurch werden die Datensätze, die ursprünglich vom Dynaset ausgewählt wurden, mit der Datenquelle synchronisiert.

Eine Liste der in dieser Version von Visual C++ mitgelieferten ODBC-Treiber sowie Informationen über den Erwerb zusätzlicher Treiber finden Sie unter [Liste der ODBC-Treiber](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
