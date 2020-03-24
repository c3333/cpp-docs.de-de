---
title: Konvertieren von Daten, die nicht vom Anbieter unterstützt werden
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211496"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konvertieren von Daten, die nicht vom Anbieter unterstützt werden

Wenn der Consumer einen Datentyp anfordert, der vom Anbieter nicht unterstützt wird, ruft der OLE DB Anbieter-Vorlagen Code für `IRowsetImpl::GetData` msdadc. dll auf, um den Datentyp zu konvertieren.

Wenn Sie eine Schnittstelle wie `IRowsetChange` implementieren, für die eine Datenkonvertierung erforderlich ist, können Sie für die Konvertierung msdaenum. dll ausführen. Verwenden Sie `GetData`, die in "Atldb. h" definiert sind, als Beispiel.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Anbietervorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
