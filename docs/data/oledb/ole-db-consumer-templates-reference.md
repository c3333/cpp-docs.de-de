---
title: Referenz der OLE DB-Consumervorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 13805ab1dc2c2b4792fd05c9140006c610b42f75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210105"
---
# <a name="ole-db-consumer-templates-reference"></a>Referenz der OLE DB-Consumervorlagen

Die OLE DB Consumer-Vorlagen enthalten die folgenden Klassen. Das Referenzmaterial enthält auch Themen zu den [Makros für OLE DB Consumer-Vorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Sitzungs Klassen

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Verwaltet die Verbindung mit der Datenquelle. Dies ist eine nützliche Klasse zum Erstellen von Clients, da Sie erforderliche Objekte (Datenquelle und Sitzung) und einige der Aufgaben kapselt, die Sie beim Herstellen einer Verbindung mit einer Datenquelle ausführen müssen.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Entspricht einem OLE DB-Datenquellen Objekt, das eine Verbindung über einen Anbieter mit einer Datenquelle darstellt. Eine oder mehrere Daten Bank Sitzungen, die jeweils durch ein `CSession` Objekt dargestellt werden, können auf einer einzelnen Verbindung stattfinden.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Entspricht einem OLE DB Enumeratorobjekt, das Rowsetinformationen zu verfügbaren Datenquellen abruft.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Wird von `CEnumerator` verwendet, um auf die Daten aus dem enumeratorrowset zuzugreifen. Dieses Rowset besteht aus den Datenquellen und Enumeratoren, die im aktuellen Enumerator sichtbar sind.

[CSession](../../data/oledb/csession-class.md)<br/>
Stellt eine einzelne Datenbankzugriffs Sitzung dar. Jeder `CDataSource` Objekt kann eine oder mehrere Sitzungen zugeordnet werden.

## <a name="accessor-classes"></a>Accessor-Klassen

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Wird für Datensätze verwendet, die statisch an eine Datenquelle gebunden sind. Verwenden Sie diese Accessor-Klasse, wenn Sie die Struktur der Datenquelle kennen.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Basisklasse für alle Accessor-Klassen.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Ein Accessor, der zur Laufzeit basierend auf den Spalten Informationen des Rowsets erstellt werden kann. Verwenden Sie diese Klasse zum Abrufen von Daten, wenn Sie die Struktur der Datenquelle nicht kennen.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Ein Accessor, der verwendet werden kann, wenn Befehls Typen unbekannt sind. Ruft die Parameterinformationen durch Aufrufen der `ICommandWithParameters`-Schnittstelle ab, wenn der Anbieter die-Schnittstelle unterstützt.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Ermöglicht den Zugriff auf eine Datenquelle, wenn Sie nicht über die zugrunde liegende Struktur der Datenbank wissen.

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Vergleichbar mit `CDynamicStringAccessor`, mit der Ausnahme, dass diese Klasse Daten anfordert, auf die aus dem Datenspeicher als ANSI-Zeichen folgen Daten

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Vergleichbar mit `CDynamicStringAccessor`, mit der Ausnahme, dass diese Klasse Daten anfordert, auf die aus dem Datenspeicher als Unicode-Zeichen folgen Daten

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Ein Accessor mit Methoden zum Verarbeiten von Spalten und Befehlsparametern. Mit dieser Klasse können Sie beliebige Datentypen verwenden, sofern der Anbieter den Typ konvertieren kann.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Kann als Vorlagen Argument verwendet werden, wenn Sie nicht möchten, dass die Klasse Parameter oder Ausgabespalten unterstützt.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Ähnlich wie `CDynamicStringAccessor`, mit der Ausnahme, dass diese Klasse alle Daten konvertiert, auf die aus dem Datenspeicher als XML-formatierte (markierte) Daten zugegriffen wird.

## <a name="rowset-classes"></a>Rowset-Klassen

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
Kapselt ein Rowset und die zugeordneten Accessoren.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Wird verwendet, um mithilfe der Array Syntax auf Elemente eines Rowsets zuzugreifen.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Wird verwendet, um Zeilen per Massen Abruf abzurufen und zu bearbeiten, indem mehrere Zeilen Handles mit einem einzigen-Befehl abgerufen werden.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
Kann als Vorlagen Argument verwendet werden, wenn der Befehl kein Rowset zurückgibt.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Wird verwendet, um Einschränkungen für Schemarowsets anzugeben.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Wird verwendet, um Rowsetdaten zu bearbeiten, festzulegen und abzurufen.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Gibt ein `ISequentialStream` Objekt anstelle eines Rowsets zurück. Anschließend verwenden Sie die `Read`-Methode zum Abrufen von Daten im XML-Format. (SQL Server 2000 führt die Formatierung aus. Beachten Sie, dass diese Funktion nur mit SQL Server 2000 funktioniert.)

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Stellt eine Pseudo Implementierung für `IRowsetNotify`mit leeren Funktionen für die `IRowsetNotify` Methoden `OnFieldChange`, `OnRowChange`und `OnRowsetChange`bereit.

[Schemarowset-Klassen und Typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Die OLE DB Vorlagen stellen eine Reihe von Klassen bereit, die den OLE DB Schemarowsets entsprechen.

## <a name="command-classes"></a>Befehls Klassen

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Wird verwendet, um einen Parameter basierten OLE DB Befehl festzulegen und auszuführen. Um nur ein einfaches Rowset zu öffnen, verwenden Sie stattdessen `CTable`.

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
Wird als Vorlagen Argument für die `CCommand` Vorlage verwendet, wenn der Befehl mehrere Resultsets verarbeiten soll.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Wird als Vorlagen Argument für Vorlagen Klassen wie `CCommand` und `CTable`verwendet, die ein Accessor-Klassen Argument akzeptieren. Verwenden Sie `CNoAccessor`, wenn Sie nicht möchten, dass die Klasse Parameter oder Ausgabespalten unterstützt.

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
Wird als Vorlagen Argument für die `CCommand` Vorlage verwendet, wenn Sie möchten, dass der Befehl ein einzelnes Rowset behandelt. `CNoMultipleResults` ist der Standardwert für das Vorlagen Argument.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
Wird als Vorlagen Argument für `CCommand` oder `CTable` verwendet, wenn der Befehl oder die Tabelle kein Rowset zurückgibt.

[CTable](../../data/oledb/ctable-class.md)<br/>
Wird verwendet, um auf ein einfaches Rowset ohne Parameter zuzugreifen.

## <a name="property-classes"></a>Eigenschaften Klassen

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Wird verwendet, um ein Array von Eigenschaften-IDs zu übergeben, für die der Consumer Eigenschafts Informationen anfordert. Die Eigenschaften gehören zu einem Eigenschaften Satz.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Wird verwendet, um Eigenschaften für einen Anbieter festzulegen.

## <a name="bookmark-class"></a>Bookmark-Klasse

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Wird als Index für den Zugriff auf Daten in einem Rowset verwendet.

## <a name="error-class"></a>Error-Klasse

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Wird verwendet, um OLE DB Fehlerinformationen abzurufen.

## <a name="see-also"></a>Weitere Informationen

[Referenz der OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB-Vorlagen](../../data/oledb/ole-db-templates.md)
