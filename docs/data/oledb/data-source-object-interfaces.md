---
title: Datenquellenobjekt-Schnittstellen
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544603"
---
# <a name="data-source-object-interfaces"></a>Datenquellenobjekt-Schnittstellen

Die folgende Tabelle zeigt die obligatorischen und optionalen Schnittstellen, die durch OLE DB für ein Datenquellen Objekt definiert werden.

|Schnittstelle|Erforderlich?|Implementiert durch OLE DB Vorlagen?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obligatorisch.|Ja|
|`IDBInitialize`|Obligatorisch.|Ja|
|`IDBProperties`|Obligatorisch.|Ja|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Obligatorisch.|Ja|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Nein|
|`IDBDataSourceAdmin`|Optional|Nein|
|`IDBInfo`|Optional|Nein|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|Optional|Nein|
|`ISupportErrorInfo`|Optional|Nein|

Das Datenquellen Objekt implementiert die Schnittstellen `IDBProperties`, `IDBInitialize`und `IDBCreateSession` durch Vererbung. Sie können zusätzliche Funktionen unterstützen, indem Sie von einer dieser Implementierungsklassen erben oder nicht erben. Wenn Sie die `IDBDataSourceAdmin`-Schnittstelle unterstützen möchten, müssen Sie von der `IDBDataSourceAdminImpl`-Klasse erben.

## <a name="see-also"></a>Siehe auch

[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
