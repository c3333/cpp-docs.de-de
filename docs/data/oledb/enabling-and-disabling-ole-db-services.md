---
title: Aktivieren und Deaktivieren von OLE DB-Diensten
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210963"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Aktivieren und Deaktivieren von OLE DB-Diensten

Der OLE DB-Dienst Komponenten-Manager vergleicht die vom Consumer angegebenen Eigenschaften mit den Eigenschaften, die vom Anbieter unterstützt werden, um zu bestimmen, ob einzelne Dienst Komponenten zum erfüllen erweiterter Funktionen verwendet werden können, die vom Consumer angefordert werden. Wenn eine Anwendung z. b. einen Bild lauffähigen Cursor anfordert und der Anbieter nur einen Vorwärts Cursor unterstützt, verwendet der Dienst Komponenten-Manager die Client Cursor-Engine-Dienst Komponente, um scrollfähige Funktionen bereitzustellen. Wenn sich die Anwendung auf Erweiterte Funktionen verlässt, die standardmäßig im Rowset des Anbieters unterstützt werden, und die Anwendung die Eigenschaften nicht explizit so festgelegt, dass diese Funktionalität angefordert wird, wird die Funktionalität möglicherweise nicht in dem vom Client zurückgegebenen Rowset angezeigt. Cursor-Engine. Um interoperabel zu sein, sollten Anwendungen immer Eigenschaften festlegen, um bei Bedarf erweiterte Funktionen explizit anzufordern.

In einigen Fällen kann es erforderlich sein, einzelne OLE DB Dienste zu deaktivieren, damit Sie gut mit vorhandenen Anwendungen funktionieren, die Annahmen über die Merkmale eines Anbieters treffen. OLE DB Dienste bieten die Möglichkeit, einzelne Dienste oder alle Dienste entweder auf Verbindungs Basis oder für alle Anwendungen, die einen einzelnen Anbieter verwenden, zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Ressourcenpooling und -Dienste](../../data/oledb/ole-db-resource-pooling-and-services.md)
