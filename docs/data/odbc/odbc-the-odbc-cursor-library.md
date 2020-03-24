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
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213095"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Die ODBC-Cursorbibliothek

In diesem Thema wird die ODBC-Cursor Bibliothek beschrieben und erläutert, wie Sie verwendet wird. Weitere Informationen finden Sie unter

- [Cursor Bibliothek und ODBC-Treiber der Ebene 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Positionierte Updates und timestamp-Spalten](#_core_positioned_updates_and_timestamp_columns)

- [Verwenden der Cursor Bibliothek](#_core_using_the_cursor_library)

Bei der ODBC-Cursor Bibliothek handelt es sich um eine DLL (Dynamic Link Library), die sich zwischen dem ODBC-Treiber-Manager und dem Treiber befindet. In ODBC-Begriffen verwaltet ein Treiber einen Cursor, um seine Position im Recordset nachzuverfolgen. Der Cursor markiert die Position im Recordset, für die Sie bereits einen Rollup durchgeführt haben – den aktuellen Datensatz.

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Cursor Bibliothek und ODBC-Treiber der Ebene 1

Die ODBC-Cursor Bibliothek gibt den Treibern der Ebene 1 die folgenden neuen Funktionen:

- Vorwärts-und Rückwärtsscrollen. Treiber der Ebene 2 benötigen die Cursor Bibliothek nicht, da Sie bereits scrollfähig sind.

- Unterstützung für Momentaufnahmen. Die Cursor Bibliothek verwaltet einen Puffer, der die Datensätze der Momentaufnahmen enthält. Dieser Puffer reflektiert die Löschungen und Änderungen an den Datensätzen des Programms, aber nicht an den Ergänzungen, Löschungen oder Änderungen anderer Benutzer. Daher ist die Momentaufnahme nur so aktuell wie der Puffer der Cursor Bibliothek. Der Puffer spiegelt auch keine eigenen Ergänzungen wider, bis Sie `Requery`aufgerufen haben. Die Cursor Bibliothek wird von Dynasets nicht verwendet.

Die Cursor Bibliothek gibt Ihnen Momentaufnahmen (statische Cursor), auch wenn Sie von Ihrem Treiber normalerweise nicht unterstützt werden. Wenn der Treiber bereits statische Cursor unterstützt, müssen Sie die Cursor Bibliothek nicht laden, um die Momentaufnahme Unterstützung zu erhalten. Wenn Sie die Cursor Bibliothek verwenden, können Sie nur Momentaufnahmen und Vorwärts-Recordsets verwenden. Wenn Ihr Treiber Dynasets (KEYSET_DRIVEN Cursor) unterstützt und Sie diese verwenden möchten, dürfen Sie die Cursor Bibliothek nicht verwenden. Wenn Sie sowohl Momentaufnahmen als auch Dynasets verwenden möchten, müssen Sie diese auf zwei verschiedenen `CDatabase` Objekten (zwei verschiedene Verbindungen) aufbauen, es sei denn, der Treiber unterstützt beides.

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Positionierte Updates und timestamp-Spalten

> [!NOTE]
>  Auf ODBC-Datenquellen können Sie über die MFC-ODBC-Klassen zugreifen, wie in diesem Thema beschrieben, oder über die MFC-Datenzugriffsobjekt-Klassen (DAO-Klassen).

> [!NOTE]
>  Wenn Ihr ODBC-Treiber `SQLSetPos`unterstützt, den MFC ggf. verwendet, gilt dieses Thema nicht für Sie.

Die meisten Treiber der Ebene 1 unterstützen keine positionierten Updates. Diese Treiber basieren auf der Cursor Bibliothek, um die Funktionen der Treiber der Ebene 2 in dieser Hinsicht zu emulieren. Die Cursor Bibliothek emuliert die Unterstützung für positionierte Updates durch eine durchsuchte Aktualisierung der nicht ändernden Felder.

In einigen Fällen kann ein Recordset eine Zeitstempel-Spalte als eines dieser nicht ändernden Felder enthalten. Bei der Verwendung von MFC-Recordsets mit Tabellen, die Zeitstempel-Spalten enthalten, treten zwei Probleme auf.

Das erste Problem betrifft aktualisierbare Momentaufnahmen für Tabellen mit Zeitstempel-Spalten. Wenn die Tabelle, an die die Momentaufnahme gebunden ist, eine Zeitstempel-Spalte enthält, sollten Sie `Requery` abrufen, nachdem Sie `Edit` und `Update`aufgerufen haben. Andernfalls können Sie den gleichen Datensatz möglicherweise nicht mehr bearbeiten. Wenn Sie `Edit` aufzurufen und dann `Update`, wird der Datensatz in die Datenquelle geschrieben, und die Zeitstempel-Spalte wird aktualisiert. Wenn Sie `Requery`nicht aufzurufen, stimmt der Zeitstempelwert für den Datensatz in der Momentaufnahme nicht mehr mit dem entsprechenden Zeitstempel in der Datenquelle überein. Wenn Sie versuchen, den Datensatz erneut zu aktualisieren, kann die Datenquelle die Aktualisierung aufgrund des Konflikts nicht zulassen.

Das zweite Problem bezieht sich auf die Einschränkungen der [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Klasse, wenn Sie mit der `RFX_Date`-Funktion verwendet wird, um Zeit-und Datumsangaben in eine oder aus einer Tabelle Die Verarbeitung des `CTime` Objekts führt bei der Datenübertragung zu einem gewissen Aufwand in Form einer zusätzlichen zwischen Verarbeitung. Der Datumsbereich von `CTime` Objekten kann für einige Anwendungen ebenfalls zu eingeschränkt sein. Eine neue Version der `RFX_Date` Funktion nimmt einen ODBC- *TIMESTAMP_STRUCT* Parameter anstelle eines `CTime` Objekts an. Weitere Informationen finden Sie unter `RFX_Date` in [Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md) in der *MFC-Referenz*.

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Verwenden der Cursor Bibliothek

Beim Herstellen einer Verbindung mit einer Datenquelle – durch Aufrufen von [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) oder [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) – können Sie angeben, ob die Cursor Bibliothek für die Datenquelle verwendet werden soll. Wenn Sie Momentaufnahmen für diese Datenquelle erstellen, geben Sie die Option `CDatabase::useCursorLib` im `dwOptions`-Parameter an, um `OpenEx`, oder geben Sie true für den Parameter " *bUseCursorLib* " an `Open` (der Standardwert ist "true"). Wenn Ihr ODBC-Treiber Dynasets unterstützt und Sie Dynasets in der Datenquelle öffnen möchten, verwenden Sie die Cursor Bibliothek nicht (Sie maskiert einige für Dynasets erforderliche Treiberfunktionen). Geben Sie in diesem Fall keine `CDatabase::useCursorLib` in `OpenEx` an, oder geben Sie false für den Parameter " *bUseCursorLib* " in `Open`an.

## <a name="see-also"></a>Weitere Informationen

[Grundlagen zu ODBC](../../data/odbc/odbc-basics.md)
