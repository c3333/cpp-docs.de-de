---
title: Transaktionsobjekt-Schnittstellen
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: b86064c162dcacfbbc5877614c63d92d0f2bd347
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544531"
---
# <a name="transaction-object-interfaces"></a>Transaktionsobjekt-Schnittstellen

Das Transaction-Objekt definiert eine unteilbare Arbeitseinheit in einer Datenquelle und bestimmt, wie diese Arbeitseinheiten zueinander zueinander stehen. Dieses Objekt wird nicht direkt von den OLE DB Anbieter Vorlagen unterstützt (d. h., Sie müssen ein eigenes-Objekt erstellen).

Die folgende Tabelle zeigt die obligatorischen und optionalen Schnittstellen, die durch OLE DB für ein Transaktions Objekt definiert werden.

|Schnittstelle|Erforderlich?|Implementiert durch OLE DB Vorlagen?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatorisch.|Nein|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Obligatorisch.|Nein|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Nein|

## <a name="see-also"></a>Siehe auch

[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
