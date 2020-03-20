---
title: Aktivieren und Deaktivieren von Diensten für einen Anbieter
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: a74f8a8b099a30cf25007547e8059c77728435f9
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "79544459"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Aktivieren und Deaktivieren von Diensten für einen Anbieter

Einzelne OLE DB Dienste können standardmäßig für alle Anwendungen aktiviert oder deaktiviert werden, die auf einen einzelnen Anbieter zugreifen. Dies erfolgt durch Hinzufügen eines OLEDB_SERVICES Registrierungs Eintrags unter der CLSID des Anbieters mit einem DWORD-Wert, der die zu aktivierenden oder zu deaktivierenden Dienste angibt, wie in der folgenden Tabelle dargestellt.

|Aktivierte Standarddienste|DWORD-Wert|
|------------------------------|-------------------|
|Alle Dienste außer Client Cursor und Pooling|0xfffffffa|
|Alle Dienste außer Client Cursor|0xfffffffb|
|Alle Dienste außer Pooling und automatische Eintragung|0xfffffffc|
|Alle Dienste außer Pooling|0xfffffffe|
|Alle Dienste (Standard)|0xFFFFFFFF|
|Keine Dienste|0x00000000|
|Keine Aggregation, alle Dienste deaktiviert|Kein OLEDB_Services Registrierungs Eintrag|

## <a name="see-also"></a>Siehe auch

[Aktivieren und Deaktivieren von OLE DB-Diensten](../../data/oledb/enabling-and-disabling-ole-db-services.md)
