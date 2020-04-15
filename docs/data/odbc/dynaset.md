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
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371838"
---
# <a name="dynaset"></a>Dynaset

In diesem Thema werden Dynasets beschrieben und deren [Verfügbarkeit](#_core_availability_of_dynasets)erläutert.

> [!NOTE]
> Dieses Thema gilt für die MFC ODBC-Klassen, einschließlich [CRecordset](../../mfc/reference/crecordset-class.md). Informationen zu Dynasets in den DAO-Klassen finden Sie unter [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Mit DAO können Sie Recordsets vom Typ Dynaset öffnen.

Ein Dynaset ist ein Recordset mit dynamischen Eigenschaften. Während seiner Lebensdauer wird ein Recordset-Objekt im Dynaset-Modus (in der Regel als Dynaset bezeichnet) wie folgt mit der Datenquelle synchronisiert. In einer Mehrbenutzerumgebung können andere Benutzer Datensätze in Ihrem Dynaset bearbeiten oder löschen oder der Tabelle, die Ihr Dynaset darstellt, Datensätze hinzufügen. Datensätze, die Ihre Anwendung dem Recordset hinzufügt oder aus dem Recordset gelöscht wird, werden in Ihrem Dynaset widergespiegelt. Datensätze, die andere Benutzer der Tabelle hinzufügen, werden erst in Ihrem Dynaset widergespiegelt, wenn Sie das Dynaset neu erstellen, indem Sie seine `Requery` Memberfunktion aufrufen. Wenn andere Benutzer Datensätze löschen, überspringt MFC-Code die Löschungen in Ihrem Recordset. Die Bearbeitungsänderungen anderer Benutzer an vorhandenen Datensätzen werden in Ihrem Dynaset widergespiegelt, sobald Sie zum betroffenen Datensatz scrollen.

Ebenso spiegeln sich Bearbeitungen, die Sie an Datensätzen in einem Dynaset vornehmen, in Dynasets wider, die von anderen Benutzern verwendet werden. Die von Ihnen hinzugefügten Datensätze werden erst in den Dynasets anderer Benutzer angezeigt, wenn sie ihre Dynasets erneut abfragen. Datensätze, die Sie löschen, werden in den Recordsets anderer Benutzer als "gelöscht" markiert. Wenn Sie über mehrere Verbindungen mit `CDatabase` derselben Datenbank (mehrere Objekte) verfügen, haben Recordsets, die diesen Verbindungen zugeordnet sind, denselben Status wie die Recordsets anderer Benutzer.

Dynasets sind am wertvollsten, wenn Daten dynamisch sein müssen, wie z. B. in einem Flugbuchungssystem.

> [!NOTE]
> Um Dynasets verwenden zu können, benötigen Sie einen ODBC-Treiber für Ihre Datenquelle, der Dynasets unterstützt, und die ODBC-Cursorbibliothek darf nicht geladen werden. Weitere Informationen finden Sie unter [Verfügbarkeit von Dynasets](#_core_availability_of_dynasets).

Um anzugeben, dass ein Recordset `CRecordset::dynaset` ein Dynaset ist, übergeben Sie als ersten Parameter an die `Open` Memberfunktion Ihres Recordset-Objekts.

> [!NOTE]
> Bei aktualisierbaren Dynasets muss Ihr ODBC-Treiber `::SQLSetPos` entweder positionierte Update-Anweisungen oder die ODBC-API-Funktion unterstützen. Wenn beide unterstützt werden, `::SQLSetPos` verwendet MFC für effizienz.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Verfügbarkeit von Dynasets

Die MFC-Datenbankklassen unterstützen Dynasets, wenn die folgenden Anforderungen erfüllt sind:

- Die ODBC-Cursorbibliotheks-DLL darf für diese Datenquelle nicht verwendet werden.

   Wenn die Cursorbibliothek verwendet wird, maskiert sie einige Funktionen des zugrunde liegenden ODBC-Treibers, die für die Dynaset-Unterstützung erforderlich sind. Wenn Sie Dynasets verwenden möchten (und Ihr ODBC-Treiber verfügt über die für Dynasets erforderliche Funktionalität, wie im Rest dieses `CDatabase` Abschnitts beschrieben), können Sie dazu führen, dass MFC die Cursorbibliothek beim Erstellen eines Objekts nicht lädt. Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und die `CDatabase` [OpenEx-](../../mfc/reference/cdatabase-class.md#openex) oder Open-Memberfunktion der Klasse . [Open](../../mfc/reference/cdatabase-class.md#open)

   In der ODBC-Terminologie werden Dynasets und Snapshots als Cursor bezeichnet. Ein Cursor ist ein Mechanismus, der verwendet wird, um seine Position in einem Recordset nachzuverfolgen.

- Der ODBC-Treiber für Ihre Datenquelle muss Keyset-gesteuerte Cursor unterstützen.

   Keyset-gesteuerte Cursor verwalten Daten aus einer Tabelle, indem sie eine Reihe von Schlüsseln abrufen und speichern. Die Schlüssel werden verwendet, um aktuelle Daten aus der Tabelle abzubekommen, wenn der Benutzer auf einen bestimmten Datensatz scrollt. Um zu ermitteln, ob Ihr `::SQLGetInfo` Treiber diese Unterstützung bereitstellt, rufen Sie die ODBC-API-Funktion mit dem *Parameter SQL_SCROLL_OPTIONS* auf.

   Wenn Sie versuchen, ein Dynaset ohne Keyset-Unterstützung zu öffnen, erhalten Sie einen `CDBException` mit dem Rückgabecodewert AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Der ODBC-Treiber für Ihre Datenquelle muss erweitertes Abrufen unterstützen.

   Erweitertes Abrufen ist die Möglichkeit, über die resultierenden Datensätze Ihrer SQL-Abfrage rückwärts und vorwärts zu scrollen. Um zu ermitteln, ob Ihr `::SQLGetFunctions` Treiber diese Fähigkeit unterstützt, rufen Sie die ODBC-API-Funktion mit dem *Parameter SQL_API_SQLEXTENDEDFETCH* auf.

Wenn Sie aktualisierbare Dynasets (oder Snapshots) wünschen, muss `::SQLSetPos` Ihr ODBC-Treiber auch die ODBC-API-Funktion oder positionierte Updates unterstützen. Die `::SQLSetPos` Funktion ermöglicht es MFC, die Datenquelle zu aktualisieren, ohne SQL-Anweisungen zu senden. Wenn diese Unterstützung verfügbar ist, verwendet MFC sie anstelle von Aktualisierungen mit SQL. Um zu bestimmen, `::SQLSetPos`ob `::SQLGetInfo` Ihr Treiber unterstützt, rufen Sie mit dem *Parameter SQL_POS_OPERATIONS* auf.

Positionierte Aktualisierungen verwenden die SQL-Syntax (in der Form **WHERE CURRENT OF** \<cursorname>), um eine bestimmte Zeile in der Tabelle in der Datenquelle zu identifizieren. Um zu bestimmen, ob Ihr `::SQLGetInfo` Treiber positionierte Aktualisierungen unterstützt, rufen Sie mit dem *Parameter SQL_POSITIONED_STATEMENTS* an.

Im Allgemeinen erfordern MFC-Dynasets (aber nicht vorwärtsgerichtete Recordsets) einen ODBC-Treiber mit API-Konformität der Stufe 2. Wenn der Treiber für Ihre Datenquelle dem API-Satz der Ebene 1 entspricht, können Sie weiterhin sowohl aktualisierbare als auch schreibgeschützte Snapshots und Nur-Forward-Recordsets verwenden, jedoch keine Dynasets. Ein Treiber der Ebene 1 kann jedoch Dynasets unterstützen, wenn er erweitertes Abrufen und Keyset-gesteuerte Cursor unterstützt. Weitere Informationen zu ODBC-Konformitätsstufen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Wenn Sie sowohl Snapshots als auch Dynasets verwenden möchten, müssen Sie sie auf zwei verschiedenen `CDatabase` Objekten (zwei verschiedene Verbindungen) basieren.

Im Gegensatz zu Snapshots, die Zwischenspeicher verwenden, der von der ODBC-Cursorbibliothek verwaltet wird, rufen Dynasets einen Datensatz direkt aus der Datenquelle ab, sobald Sie zu diesem Scrollen scrollen. Dadurch werden die Datensätze, die ursprünglich vom Dynaset ausgewählt wurden, mit der Datenquelle synchronisiert.

Eine Liste der in dieser Version von Visual C++ mitgelieferten ODBC-Treiber sowie Informationen über den Erwerb zusätzlicher Treiber finden Sie unter [Liste der ODBC-Treiber](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
