---
title: Schnittstellen für Rowset-Objekte
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544543"
---
# <a name="rowset-object-interfaces"></a>Schnittstellen für Rowset-Objekte

Die folgende Tabelle zeigt die obligatorischen und optionalen Schnittstellen, die durch OLE DB für ein Rowsetobjekt definiert werden.

|Schnittstelle|Erforderlich?|Implementiert durch OLE DB Vorlagen?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|Obligatorisch.|Ja|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obligatorisch.|Ja|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|Obligatorisch.|Ja|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|Obligatorisch.|Ja|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obligatorisch.|Ja|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Optional|Nein|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Optional|Nein|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Optional|Nein|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Ja (durch ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Optional|Nein|
|[Igetrow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Optional|Nein|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Optional|Ja|
|[Irowsetchaptermember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Optional|Nein|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Optional|Nein|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Optional|Nein|
|[Irowdie tidentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|Optional (ist jedoch für Anbieter der Ebene 0 erforderlich)|Ja|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Optional|Nein|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Optional|Ja|
|[Irowsee trefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Optional|Nein|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Optional|Nein|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Optional|Ja|
|[Irowsetview](/previous-versions/windows/desktop/ms709755(v=vs.85))|Optional|Nein|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Ja|
|[Irowsetbookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Optional|Nein|

Das vom Assistenten generierte Rowsetobjekt implementiert `IAccessor`, `IRowset`und `IRowsetInfo` durch Vererbung. Der `IAccessorImpl` bindet beide Ausgabespalten. Die `IRowset`-Schnittstelle übernimmt das Abrufen von Zeilen und Daten. Die `IRowsetInfo`-Schnittstelle verarbeitet die Rowseteigenschaften.

## <a name="see-also"></a>Siehe auch

[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
