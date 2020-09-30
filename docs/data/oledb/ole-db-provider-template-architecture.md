---
title: Architektur von OLE DB-Anbietervorlagen
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 89e07f95853c3611b7cceaef3f247c220c630add
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509545"
---
# <a name="ole-db-provider-template-architecture"></a>Architektur von OLE DB-Anbietervorlagen

## <a name="data-sources-and-sessions"></a>Datenquellen und Sitzungen

Die OLE DB Anbieter Architektur enthält ein Datenquellen Objekt und eine oder mehrere Sitzungen. Das Datenquellen Objekt ist das erste Objekt, das von jedem Anbieter instanziiert werden muss. Wenn eine Consumeranwendung Daten benötigt, erstellt Sie das Datenquellen Objekt, um den Anbieter zu starten. Das Datenquellen Objekt erstellt ein Sitzungs Objekt (mithilfe der- `IDBCreateSession` Schnittstelle), über das der Consumer eine Verbindung mit dem Datenquellen Objekt herstellt. ODBC-Programmierer können sich das Datenquellen Objekt als gleichwertig mit dem `HENV` -Objekt und dem Session-Objekt vorstellen `HDBC` .

![Anbieterarchitektur](../../data/oledb/media/vc4twb1.gif "Anbieterarchitektur")

In Verbindung mit den vom **Assistenten für OLE DB Anbieter**erstellten Quelldateien implementieren die OLE DB Vorlagen ein Datenquellen Objekt. Eine Sitzung ist ein Objekt, das der OLE DB entspricht `TSession` .

## <a name="mandatory-and-optional-interfaces"></a>Obligatorische und optionale Schnittstellen

Die OLE DB-Anbieter Vorlagen enthalten vorab gepackte Implementierungen für alle erforderlichen Schnittstellen. Erforderliche und optionale Schnittstellen werden durch OLE DB für verschiedene Typen von Objekten definiert:

- [Datenquelle](../../data/oledb/data-source-object-interfaces.md)

- [Sitzungskonsistenz](../../data/oledb/session-object-interfaces.md)

- [Rowset](../../data/oledb/rowset-object-interfaces.md)

- [Befehl](../../data/oledb/command-object-interfaces.md)

- [Transaktion](../../data/oledb/transaction-object-interfaces.md)

In den OLE DB Anbieter Vorlagen werden die Zeilen-und Speicher Objekte nicht implementiert.

In der folgenden Tabelle sind erforderliche und optionale Schnittstellen für die oben aufgeführten Objekte entsprechend der [OLE DB 2,6 SDK-Dokumentation](/previous-versions/windows/desktop/ms722784(v=vs.85))aufgelistet.

|Komponente|Schnittstelle|Kommentar|
|---------------|---------------|-------------|
|[Datenquelle](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|Verpflich `IDBCreateSession`<br /><br /> Verpflich `IDBInitialize`<br /><br /> Verpflich `IDBProperties`<br /><br /> Verpflich `IPersist`<br /><br /> optionale `IConnectionPointContainer`<br /><br /> optionale `IDBAsynchStatus`<br /><br /> optionale `IDBDataSourceAdmin`<br /><br /> optionale `IDBInfo`<br /><br /> optionale `IPersistFile`<br /><br /> optionale `ISupportErrorInfo`|Verbindung zwischen dem Consumer und dem Anbieter. Das-Objekt wird verwendet, um Eigenschaften für die Verbindung anzugeben, z. b. Benutzer-ID, Kennwort und Datenquellen Name. Das-Objekt kann auch verwendet werden, um eine Datenquelle (Create, Update, DELETE, Tables usw.) zu verwalten.|
|[Sitzung](../../data/oledb/session-object-interfaces.md) ([CSession](./cdataconnection-class.md#op_csession_amp))|Verpflich `IGetDataSource`<br /><br /> Verpflich `IOpenRowset`<br /><br /> Verpflich `ISessionProperties`<br /><br /> optionale `IAlterIndex`<br /><br /> optionale `IAlterTable`<br /><br /> optionale `IBindResource`<br /><br /> optionale `ICreateRow`<br /><br /> optionale `IDBCreateCommand`<br /><br /> optionale `IDBSchemaRowset`<br /><br /> optionale `IIndexDefinition`<br /><br /> optionale `ISupportErrorInfo`<br /><br /> optionale `ITableCreation`<br /><br /> optionale `ITableDefinition`<br /><br /> optionale `ITableDefinitionWithConstraints`<br /><br /> optionale `ITransaction`<br /><br /> optionale `ITransactionJoin`<br /><br /> optionale `ITransactionLocal`<br /><br /> optionale `ITransactionObject`|Das Sitzungs Objekt ist eine einzelne Konversation zwischen einem Consumer und einem Anbieter. Es ähnelt dem ODBC darin `HSTMT` , dass viele gleichzeitige Sitzungen aktiv sein können.<br /><br /> Das Sitzungs Objekt ist der primäre Link, um OLE DB Funktionalität zu erhalten. Um zu einem Befehls-, Transaktions-oder Rowsetobjekt zu gelangen, durchlaufen Sie das Session-Objekt.|
|[Rowset](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|Verpflich `IAccessor`<br /><br /> Verpflich `IColumnsInfo`<br /><br /> Verpflich `IConvertType`<br /><br /> Verpflich `IRowset`<br /><br /> Verpflich `IRowsetInfo`<br /><br /> optionale `IChapteredRowset`<br /><br /> optionale `IColumnsInfo2`<br /><br /> optionale `IColumnsRowset`<br /><br /> optionale `IConnectionPointContainer`<br /><br /> optionale `IDBAsynchStatus`<br /><br /> optionale `IGetRow`<br /><br /> optionale `IRowsetChange`<br /><br /> optionale `IRowsetChapterMember`<br /><br /> optionale `IRowsetCurrentIndex`<br /><br /> optionale `IRowsetFind`<br /><br /> optionale `IRowsetIdentity`<br /><br /> optionale `IRowsetIndex`<br /><br /> optionale `IRowsetLocate`<br /><br /> optionale `IRowsetRefresh`<br /><br /> optionale `IRowsetScroll`<br /><br /> optionale `IRowsetUpdate`<br /><br /> optionale `IRowsetView`<br /><br /> optionale `ISupportErrorInfo`<br /><br /> optionale `IRowsetBookmark`|Das Rowsetobjekt ist die Daten aus der Datenquelle. Das-Objekt wird für die Bindungen dieser Daten und aller grundlegenden Vorgänge (Update, FETCH, Movement usw.) für die Daten verwendet. Sie verfügen immer über ein Rowsetobjekt, um Daten beizubehalten und zu bearbeiten.|
|[Befehl](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|Verpflich `IAccessor`<br /><br /> Verpflich `IColumnsInfo`<br /><br /> Verpflich `ICommand`<br /><br /> Verpflich `ICommandProperties`<br /><br /> Verpflich `ICommandText`<br /><br /> Verpflich `IConvertType`<br /><br /> optionale `IColumnsRowset`<br /><br /> optionale `ICommandPersist`<br /><br /> optionale `ICommandPrepare`<br /><br /> optionale `ICommandWithParameters`<br /><br /> optionale `ISupportErrorInfo`<br /><br /> optionale `ICommandStream`|Das Command-Objekt verarbeitet Vorgänge für Daten, z. b. Abfragen. Parametrisierte oder nicht parametrisierte Anweisungen können verarbeitet werden.<br /><br /> Das Command-Objekt ist auch für die Behandlung von Bindungen für Parameter und Ausgabespalten verantwortlich. Eine Bindung ist eine Struktur, die Informationen darüber enthält, wie eine Spalte in einem Rowset abgerufen werden soll. Sie enthält Informationen wie Ordinalzahl, Datentyp, Länge und Status.|
|[Transaktion](../../data/oledb/transaction-object-interfaces.md) (optional)|Verpflich `IConnectionPointContainer`<br /><br /> Verpflich `ITransaction`<br /><br /> optionale `ISupportErrorInfo`|Das Transaction-Objekt definiert eine unteilbare Arbeitseinheit in einer Datenquelle und bestimmt, wie diese Arbeitseinheiten zueinander zueinander stehen. Dieses Objekt wird nicht direkt von den OLE DB Anbieter Vorlagen unterstützt (d. h., Sie erstellen Ihr eigenes Objekt).|

Weitere Informationen finden Sie unter den folgenden Themen:

- [Eigenschaften Zuordnungen](../../data/oledb/property-maps.md)

- [Der Benutzerdaten Satz](../../data/oledb/user-record.md)

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB Schnittstellen](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
