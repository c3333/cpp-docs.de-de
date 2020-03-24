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
ms.openlocfilehash: b84365461ce6d45fccdf1922974feff5af93f99f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212757"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset: Arbeiten mit großen Datenelementen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen und die MFC-DAO-Klassen.

> [!NOTE]
>  Wenn Sie die MFC-DAO-Klassen verwenden, verwalten Sie Ihre großen Datenelemente mit der Klasse [CByteArray](../../mfc/reference/cbytearray-class.md) anstelle der [CLongBinary](../../mfc/reference/clongbinary-class.md)-Klasse. Wenn Sie die MFC-ODBC-Klassen mit Massen Abruf von Zeilen verwenden, verwenden Sie `CLongBinary` statt `CByteArray`. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Angenommen, in der Datenbank können große Datenmengen gespeichert werden, z. b. Bitmaps (Mitarbeiter Fotos, Karten, Bilder von Produkten, OLE-Objekten usw.). Diese Art von Daten wird häufig als binäres Large Object (oder BLOB) bezeichnet, weil Folgendes gilt:

- Jeder Feldwert ist groß.

- Anders als Zahlen und andere einfache Datentypen hat Sie keine vorhersagbare Größe.

- Die Daten sind aus der Perspektive des Programms formlos.

In diesem Thema wird erläutert, welche Unterstützung der Datenbankklassen zum Arbeiten mit solchen Objekten bietet.

##  <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Verwalten von großen Objekten

Recordsets haben zwei Möglichkeiten, um die besondere Schwierigkeit der Verwaltung von binären großen Objekten zu beheben. Sie können die Klasse [CByteArray](../../mfc/reference/cbytearray-class.md) verwenden, oder Sie können die [CLongBinary](../../mfc/reference/clongbinary-class.md)-Klasse verwenden. Im Allgemeinen ist `CByteArray` die bevorzugte Methode zum Verwalten großer Binärdaten.

`CByteArray` erfordert mehr Aufwand als `CLongBinary`, ist jedoch leistungsfähiger, wie in [der CByteArray-Klasse](#_core_the_cbytearray_class)beschrieben. `CLongBinary` wird kurz in [der CLongBinary-Klasse](#_core_the_clongbinary_class)beschrieben.

Ausführliche Informationen zum Verwenden von `CByteArray` zum Arbeiten mit großen Datenelementen finden Sie im [technischen Hinweis 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>CByteArray-Klasse

`CByteArray` ist eine der MFC-Auflistungs Klassen. Ein `CByteArray`-Objekt speichert ein dynamisches Bytearray – das Array kann bei Bedarf vergrößert werden. Die-Klasse ermöglicht den schnellen Zugriff nach Index, wie bei integrierten C++ Arrays. `CByteArray` Objekte können zu Diagnose Zwecken serialisiert und entsorgt werden. Die-Klasse stellt Element Funktionen zum erhalten und festlegen angegebener bytes, einfügen und Anhängen von Bytes sowie zum Entfernen von einem Byte oder allen Bytes bereit. Diese Funktionen vereinfachen das Auswerten der Binärdaten. Wenn das binäre Objekt z. b. ein OLE-Objekt ist, müssen Sie möglicherweise einige Header Bytes durcharbeiten, um das tatsächliche Objekt zu erreichen.

##  <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Verwenden von CByteArray in Recordsets

Wenn Sie einem Feld Datenelement des Recordsets den Typ `CByteArray`geben, stellen Sie eine festgelegte Basis bereit, von der [RFX](../../data/odbc/record-field-exchange-rfx.md) die Übertragung eines solchen Objekts zwischen dem Recordset und der Datenquelle verwalten und über das Sie die Daten innerhalb des Objekts bearbeiten können. RFX benötigt eine bestimmte Site für abgerufene Daten, und Sie benötigen eine Möglichkeit, auf die zugrunde liegenden Daten zuzugreifen.

Ausführliche Informationen zum Verwenden von `CByteArray` zum Arbeiten mit großen Datenelementen finden Sie im [technischen Hinweis 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary-Klasse

Ein [CLongBinary](../../mfc/reference/clongbinary-class.md) -Objekt ist eine einfache Shell um ein `HGLOBAL` Handle für einen Speicherblock, der auf dem Heap zugeordnet ist. Wenn eine Tabellenspalte mit einer Binary Large Object gebunden wird, ordnet RFX das `HGLOBAL` Handle zu, wenn die Daten an das Recordset übertragen werden müssen, und speichert das Handle im `CLongBinary`-Feld des Recordsets.

Außerdem verwenden Sie das `HGLOBAL` handle, `m_hData`, um mit den Daten selbst zu arbeiten, wie Sie es bei beliebigen Handle-Daten tun würden. An dieser Stelle fügt [CByteArray](../../mfc/reference/cbytearray-class.md) Funktionen hinzu.

> [!CAUTION]
>  CLongBinary-Objekte können nicht als Parameter in Funktionsaufrufen verwendet werden. Außerdem verlangsamt die Implementierung, die `::SQLGetData`aufruft, die Bild Laufleistung für eine Bild lauffähige Momentaufnahme. Dies kann auch der Fall sein, wenn Sie einen `::SQLGetData` aufrufen, um dynamische Schema Spalten abzurufen.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)
