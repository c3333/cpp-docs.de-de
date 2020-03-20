---
title: Referenz der OLE DB-Anbietervorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: f0200f0cff5292a75ec853496a644c148c8356a3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545792"
---
# <a name="ole-db-provider-templates-reference"></a>Referenz der OLE DB-Anbietervorlagen

Die Klassen und Schnittstellen für die OLE DB-Anbieter Vorlagen können in die folgenden Kategorien eingeteilt werden. Das Referenzmaterial enthält auch Informationen zu den [Makros für OLE DB Anbieter Vorlagen](../../data/oledb/macros-for-ole-db-provider-templates.md).

Die Klassen verwenden die folgende Benennungs Konvention: eine Klasse mit dem Namen mit dem Muster `IWidgetImpl` würde eine Implementierung der-Schnittstelle `IWidget`bereitstellen.

## <a name="session-classes"></a>Sitzungs Klassen

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Erstellt eine neue Sitzung aus dem Datenquellen Objekt und gibt die angeforderte Schnittstelle für die neu erstellte Sitzung zurück. Verbindliche Schnittstelle für Datenquellen Objekte.

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implementiert Sitzungs Eigenschaften durch Aufrufen einer statischen Funktion, die durch die Eigenschaften Satz Zuordnung definiert ist. Die Eigenschaften Satz Zuordnung sollte in ihrer Sitzungs Klasse angegeben werden. Erforderliche Schnittstelle für Sitzungen.

## <a name="rowset-classes"></a>Rowset-Klassen

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Stellt eine standardmäßige OLE DB-rowsetimplementierung bereit, ohne dass eine mehrfache Vererbung vieler Implementierungs Schnittstellen erforderlich ist. Die einzige Methode, für die Sie die Implementierung bereitstellen müssen, ist `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Stellt eine Standard Implementierung für das Zeilen Handle bereit, das in der `IRowsetImpl`-Klasse verwendet wird. Ein Zeilen Handle ist logisch ein eindeutiges Tag für eine Ergebniszeile. `IRowsetImpl` erstellt eine neue `CSimpleRow` für jede in `IRowsetImpl::GetNextRows`angeforderte Zeile.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB erfordert, dass Anbieter eine `HACCESSOR`implementieren, bei der es sich um ein Tag für ein Array von `DBBINDING` Strukturen handelt. Stellt `HACCESSOR`en bereit, die Adressen der `BindType` Strukturen sind. Obligatorisch für Rowsets und Befehle.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Delegiert an eine statische Funktion, die durch die Anbieter Spalten Zuordnung definiert ist. Verbindliche Schnittstelle für Rowsets und Befehle.

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
Enthält Informationen zur Verfügbarkeit von Typkonvertierungen in einem Befehl oder einem Rowset. Obligatorisch für Befehle, Rowsets und Indexrowsets. Implementiert die `IConvertType`-Schnittstelle durch Delegieren an das von OLE DB bereitgestellte Konvertierungs Objekt.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementiert die `IDBSchemaRowset`-Schnittstelle und die vorlagenbasierte erstellerfunktion `CreateSchemaRowset`.

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält, und gibt es zurück. Erforderliche Schnittstelle für ein Sitzungs Objekt.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementiert die [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) -Schnittstelle OLE DB, die das Aktualisieren der Werte von Spalten in vorhandenen Zeilen, das Löschen von Zeilen und das Einfügen neuer Zeilen ermöglicht.

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Diese Klasse erbt von [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) und überschreibt [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` führt dieselben Funktionen wie `IObjectWithSite` aus, aktiviert jedoch auch die OLE DB Eigenschaften `DBPROPCANSCROLLBACKWARDS` und `DBPROPCANFETCHBACKWARDS`.

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implementiert die `IRowsetIdentity`-Schnittstelle, mit der Sie vergleichen können, ob zwei Daten Zeilen identisch sind oder nicht.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Stellt eine Implementierung der `IRowset`-Schnittstelle bereit, die die basisrowsetschnittstelle darstellt.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementiert die Rowseteigenschaften mithilfe der in der Befehls Klasse definierten Eigenschaften Satz Zuordnung. Verbindliche Schnittstelle für Rowsets.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementiert die [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) -Schnittstelle OLE DB, die beliebige Zeilen aus einem Rowset abruft. Damit OLE DB Lesezeichen in einem Rowset unterstützt werden, müssen Sie das Rowset von dieser Klasse erben.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementiert Broadcast Funktionen, um Listener auf dem Verbindungspunkt `IID_IRowsetNotify` Änderungen am Inhalt des Rowsets zu empfehlen. Consumer, die Benachrichtigungen verarbeiten, implementieren [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) und registrieren Sie an diesem Verbindungspunkt.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementiert die [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) -Schnittstelle OLE DB, mit der Consumer die Übertragung von Änderungen, die mit [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) vorgenommen wurden, an die Datenquelle verzögern und Änderungen vor der Übertragung rückgängig machen können.

## <a name="command-classes"></a>Befehls Klassen

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Stellt eine Implementierung der `ICommand`-Schnittstelle bereit. Diese Schnittstelle ist nicht sichtbar, wird jedoch von `ICommandTextImpl`behandelt. Eine erforderliche Schnittstelle für das Befehls Objekt.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Diese Implementierung der `ICommandProperties`-Schnittstelle wird von einer statischen Funktion bereitgestellt, die durch das `BEGIN_PROPSET_MAP`-Makro definiert wird. Obligatorisch für Befehle.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Legt den Befehls Text fest, speichert ihn und gibt ihn zurück. Obligatorisch für Befehle.

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Erstellt einen neuen Befehl aus dem Sitzungs Objekt und gibt die angeforderte Schnittstelle für den neu erstellten Befehl zurück. Optionale Schnittstelle für Sitzungs Objekte.

Andere Befehls Klassen sind `IColumnsInfoImpl` und `IAccessorImpl`, die im obigen Abschnitt "Rowset Classes" beschrieben werden.

## <a name="data-source-classes"></a>Datenquellen Klassen

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Erstellt und löscht die Verbindung mit dem Consumer. Verbindliche Schnittstelle für Datenquellen Objekte und optionale Schnittstelle für Enumeratoren.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` ist eine erforderliche Schnittstelle für Datenquellen Objekte und eine optionale Schnittstelle für Enumeratoren. Wenn ein Enumerator jedoch `IDBInitialize`verfügbar macht, muss er `IDBProperties` (Eigenschaften in der Datenquelle) verfügbar machen.

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Ruft einen Schnittstellen Zeiger auf das Datenquellen Objekt ab. Erforderliche Schnittstelle für die Sitzung.

## <a name="other-classes"></a>Andere Klassen

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implementiert Eigenschaften für eine Reihe von OLE DB Eigenschaften Schnittstellen (z. b. `IDBProperties`, `ISessionProperties`und `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implementiert die [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstelle OLE DB, fügt Datensätze zu einem Datenmember hinzu und ruft Sie ab.

## <a name="see-also"></a>Siehe auch

[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB-Vorlagen](../../data/oledb/ole-db-templates.md)