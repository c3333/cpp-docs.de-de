---
title: 'Recordset: Arbeiten mit großen Datenelementen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360606"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset: Arbeiten mit großen Datenelementen (ODBC)

Dieses Thema gilt sowohl für die MFC ODBC-Klassen als auch für die MFC DAO-Klassen.

> [!NOTE]
> Wenn Sie die MFC DAO-Klassen verwenden, verwalten Sie Ihre großen Datenelemente mit der Klasse [CByteArray](../../mfc/reference/cbytearray-class.md) und nicht mit der Klasse [CLongBinary](../../mfc/reference/clongbinary-class.md). Wenn Sie die MFC ODBC-Klassen mit Massenzeilenabruf verwenden, verwenden Sie `CLongBinary` anstelle von `CByteArray`. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Angenommen, Ihre Datenbank kann große Datenmengen speichern, z. B. Bitmaps (Mitarbeiterfotos, Karten, Bilder von Produkten, OLE-Objekte usw.). Diese Art von Daten wird oft als Binary Large Object (oder BLOB) bezeichnet, weil:

- Jeder Feldwert ist groß.

- Im Gegensatz zu Zahlen und anderen einfachen Datentypen hat es keine vorhersagbare Größe.

- Die Daten sind aus Der Sicht Ihres Programms formlos.

In diesem Thema wird erläutert, welche Unterstützung die Datenbankklassen für die Arbeit mit solchen Objekten bereitstellen.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Verwalten großer Objekte

Recordsets haben zwei Möglichkeiten, die besondere Schwierigkeit der Verwaltung von binären großen Objekten zu lösen. Sie können die Klasse [CByteArray](../../mfc/reference/cbytearray-class.md) oder die Klasse [CLongBinary](../../mfc/reference/clongbinary-class.md)verwenden. Im Allgemeinen `CByteArray` ist der bevorzugte Weg, um große binäre Daten zu verwalten.

`CByteArray`erfordert mehr `CLongBinary` Overhead als, ist aber leistungsfähiger, wie in [der CByteArray-Klasse](#_core_the_cbytearray_class)beschrieben. `CLongBinary`wird kurz in [The CLongBinary Class](#_core_the_clongbinary_class)beschrieben.

Ausführliche Informationen zur `CByteArray` Verwendung zum Arbeiten mit großen Datenelementen finden Sie unter [Technische Anmerkung 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>CByteArray-Klasse

`CByteArray`ist eine der MFC-Auflistungsklassen. Ein `CByteArray` Objekt speichert ein dynamisches Array von Bytes – das Array kann bei Bedarf wachsen. Die Klasse bietet schnellen Zugriff nach Index, wie bei integrierten C++-Arrays. `CByteArray`Objekte können zu Diagnosezwecken serialisiert und gedumpt werden. Die Klasse stellt Memberfunktionen zum Abrufen und Festlegen bestimmter Bytes, Einfügen und Anfügen von Bytes und Entfernen eines Bytes oder aller Bytes bereit. Diese Funktionen erleichtern das Analysieren der Binärdaten. Wenn es sich bei dem Binärobjekt beispielsweise um ein OLE-Objekt handelt, müssen Sie möglicherweise einige Headerbytes durcharbeiten, um das eigentliche Objekt zu erreichen.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Verwenden von CByteArray in Recordsets

Indem Sie einem Felddatenelement Ihres `CByteArray`Recordsets den Typ geben, stellen Sie eine feste Basis bereit, von der aus [RFX](../../data/odbc/record-field-exchange-rfx.md) die Übertragung eines solchen Objekts zwischen Ihrem Recordset und der Datenquelle verwalten kann und über die Sie die Daten innerhalb des Objekts bearbeiten können. RFX benötigt eine bestimmte Site für abgerufene Daten, und Sie benötigen eine Möglichkeit, auf die zugrunde liegenden Daten zuzugreifen.

Ausführliche Informationen zur `CByteArray` Verwendung zum Arbeiten mit großen Datenelementen finden Sie unter [Technische Anmerkung 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary-Klasse

Ein [CLongBinary-Objekt](../../mfc/reference/clongbinary-class.md) ist eine `HGLOBAL` einfache Shell um ein Handle für einen Speicherblock, der auf dem Heap zugewiesen ist. Wenn eine Tabellenspalte mit einem binären großen Objekt `HGLOBAL` gebunden wird, weist RFX das Handle zu, wenn `CLongBinary` es die Daten an das Recordset übertragen muss, und speichert das Handle im Feld des Recordsets.

Im Gegenzug verwenden `HGLOBAL` Sie `m_hData`das Handle , , um mit den Daten selbst zu arbeiten, und arbeiten wie bei allen Handledaten. Hier fügt [CByteArray](../../mfc/reference/cbytearray-class.md) Funktionen hinzu.

> [!CAUTION]
> CLongBinary-Objekte können nicht als Parameter in Funktionsaufrufen verwendet werden. Darüber hinaus verlangsamt ihre `::SQLGetData`Implementierung, die aufruft, notwendigerweise die Bildlaufleistung für einen scrollbaren Snapshot. Dies kann auch der `::SQLGetData` Fall sein, wenn Sie selbst einen Aufruf verwenden, um dynamische Schemaspalten abzurufen.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)
