---
title: 'ODBC: Die ODBC-Cursorbibliothek'
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367182"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Die ODBC-Cursorbibliothek

In diesem Thema wird die ODBC-Cursorbibliothek beschrieben und die Verwendung erläutert. Weitere Informationen finden Sie unter

- [Cursorbibliothek und ODBC-Treiber der Ebene 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Positionierte Updates und Timestamp-Spalten](#_core_positioned_updates_and_timestamp_columns)

- [Verwenden der Cursorbibliothek](#_core_using_the_cursor_library)

Die ODBC-Cursorbibliothek ist eine Dynamic-Link-Bibliothek (DLL), die sich zwischen dem ODBC-Treiber-Manager und dem Treiber befindet. In ODBC-Begriffen behält ein Treiber einen Cursor bei, um seine Position im Recordset zu verfolgen. Der Cursor markiert die Position im Recordset, zu der Sie bereits gescrollt haben – der aktuelle Datensatz.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Cursorbibliothek und ODBC-Treiber der Ebene 1

Die ODBC-Cursorbibliothek bietet Treibern der Ebene 1 die folgenden neuen Funktionen:

- Vorwärts- und Rückwärts-Scrollen. Treiber der Ebene 2 benötigen die Cursorbibliothek nicht, da sie bereits scrollbar sind.

- Unterstützung für Snapshots. Die Cursorbibliothek verwaltet einen Puffer, der die Datensätze des Snapshots enthält. Dieser Puffer spiegelt die Löschungen und Bearbeitungen Ihres Programms an Datensätzen wider, nicht jedoch die Hinzufügungen, Löschungen oder Bearbeitungen anderer Benutzer. Daher ist der Snapshot nur so aktuell wie der Puffer der Cursorbibliothek. Der Puffer spiegelt auch ihre eigenen Ergänzungen erst wider, wenn Sie aufrufen. `Requery` Dynasets verwenden die Cursorbibliothek nicht.

Die Cursorbibliothek gibt Ihnen Snapshots (statische Cursor), auch wenn sie normalerweise nicht von Ihrem Treiber unterstützt werden. Wenn Ihr Treiber bereits statische Cursor unterstützt, müssen Sie die Cursorbibliothek nicht laden, um Snapshot-Unterstützung zu erhalten. Wenn Sie die Cursorbibliothek verwenden, können Sie nur Snapshots und Forward-Only-Recordsets verwenden. Wenn Ihr Treiber Dynasets (KEYSET_DRIVEN Cursor) unterstützt und Sie sie verwenden möchten, dürfen Sie die Cursorbibliothek nicht verwenden. Wenn Sie sowohl Snapshots als auch Dynasets verwenden möchten, müssen Sie sie auf zwei verschiedenen `CDatabase` Objekten (zwei verschiedene Verbindungen) basieren, es sei denn, der Treiber unterstützt beides.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Positionierte Updates und Timestamp-Spalten

> [!NOTE]
> Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

> [!NOTE]
> Wenn Ihr ODBC-Treiber unterstützt, `SQLSetPos`die MFC verwendet, falls verfügbar, gilt dieses Thema nicht für Sie.

Die meisten Level 1-Treiber unterstützen keine positionierten Updates. Solche Treiber verlassen sich auf die Cursorbibliothek, um die Funktionen von Level 2-Treibern in dieser Hinsicht zu emulieren. Die Cursorbibliothek emuliert die Unterstützung für positionierte Aktualisierungen, indem sie eine suchende Aktualisierung der unveränderlichen Felder durchnimmt.

In einigen Fällen kann ein Recordset eine Zeitstempelspalte als eines dieser unveränderlichen Felder enthalten. Bei der Verwendung von MFC-Recordsets mit Tabellen, die Zeitstempelspalten enthalten, treten zwei Probleme auf.

Das erste Problem betrifft aktualisierbare Snapshots für Tabellen mit Zeitstempelspalten. Wenn die Tabelle, an die Der Snapshot gebunden ist, eine `Edit` `Update`Zeitstempelspalte enthält, sollten Sie nach dem Aufruf und aufrufen. `Requery` Wenn dies nicht der Fall ist, können Sie denselben Datensatz möglicherweise nicht erneut bearbeiten. Wenn Sie `Edit` aufrufen `Update`und dann , wird der Datensatz in die Datenquelle geschrieben und die Zeitstempelspalte aktualisiert. Wenn Sie nicht `Requery`aufrufen, stimmt der Zeitstempelwert für den Datensatz in Ihrem Snapshot nicht mehr mit dem entsprechenden Zeitstempel in der Datenquelle überein. Wenn Sie versuchen, den Datensatz erneut zu aktualisieren, kann die Datenquelle die Aktualisierung aufgrund der Nichtübereinstimmung nicht zulassen.

Das zweite Problem betrifft Einschränkungen der Klasse `RFX_Date` [CTime,](../../atl-mfc-shared/reference/ctime-class.md) wenn sie mit der Funktion zum Übertragen von Zeit- und Datumsinformationen in oder aus einer Tabelle verwendet wird. Die `CTime` Verarbeitung des Objekts verursacht einen gewissen Overhead in Form einer zusätzlichen Zwischenverarbeitung während der Datenübertragung. Der Datumsbereich von `CTime` Objekten ist für einige Anwendungen möglicherweise auch zu einschränkend. Eine neue Version `RFX_Date` der Funktion nimmt einen ODBC-TIMESTAMP_STRUCT-Parameter anstelle eines Objekts. *TIMESTAMP_STRUCT* `CTime` Weitere Informationen finden `RFX_Date` Sie unter [Makros und Globale in](../../mfc/reference/mfc-macros-and-globals.md) der *MFC-Referenz*.

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Verwenden der Cursorbibliothek

Wenn Sie eine Verbindung zu einer Datenquelle herstellen – indem Sie [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) oder [CDatabase::Open aufrufen](../../mfc/reference/cdatabase-class.md#open) – können Sie angeben, ob die Cursorbibliothek für die Datenquelle verwendet werden soll. Wenn Sie Snapshots für diese Datenquelle erstellen, geben `CDatabase::useCursorLib` Sie die Option im `dwOptions` Parameter true an `OpenEx` oder geben Sie TRUE für den Parameter *bUseCursorLib* an `Open` (der Standardwert ist TRUE). Wenn Ihr ODBC-Treiber Dynasets unterstützt und Sie Dynasets in der Datenquelle öffnen möchten, verwenden Sie nicht die Cursorbibliothek (sie maskiert einige Treiberfunktionen, die für Dynasets erforderlich sind). Geben `OpenEx` Sie in nicht `CDatabase::useCursorLib` false für den Parameter *bUseCursorLib* in `Open`an oder geben Sie es nicht an.

## <a name="see-also"></a>Siehe auch

[ODBC Grundlagen](../../data/odbc/odbc-basics.md)
