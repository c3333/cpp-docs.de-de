---
title: ODBC-Treiberanforderungen für Dynasets
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367206"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>ODBC-Treiberanforderungen für Dynasets

In den MFC ODBC-Datenbankklassen sind Dynasets Recordsets mit dynamischen Eigenschaften. sie bleiben auf bestimmte Weise mit der Datenquelle synchronisiert. MFC-Dynasets (aber nicht vorwärtsgerichtete Recordsets) erfordern einen ODBC-Treiber mit Level 2-API-Konformität. Wenn der Treiber für Ihre [Datenquelle](../../data/odbc/data-source-odbc.md) dem API-Satz der Ebene 1 entspricht, können Sie weiterhin sowohl aktualisierbare als auch schreibgeschützte Snapshots und Nur-Forward-Recordsets verwenden, jedoch keine Dynasets. Ein Level 1-Treiber kann dynasets jedoch unterstützen, wenn er erweiterte Abruf- und Keyset-gesteuerte Cursor unterstützt.

In der ODBC-Terminologie werden Dynasets und Snapshots als Cursor bezeichnet. Ein Cursor ist ein Mechanismus, der verwendet wird, um seine Position in einem Recordset nachzuverfolgen. Weitere Informationen zu den Treiberanforderungen für Dynasets finden Sie unter [Dynaset](../../data/odbc/dynaset.md). Weitere Informationen zu Cursorn finden Sie im [ODBC-SDK (Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc) in der MSDN-Dokumentation.

> [!NOTE]
> Bei aktualisierbaren Recordsets muss Ihr ODBC-Treiber entweder positionierte Updateanweisungen oder die `::SQLSetPos` ODBC-API-Funktion unterstützen. Wenn beide unterstützt werden, `::SQLSetPos` verwendet MFC für effizienz. Alternativ können Sie für Snapshots die Cursorbibliothek verwenden, die die erforderliche Unterstützung für aktualisierbare Snapshots (statische Cursor und positionierte Aktualisierungsanweisungen) bereitstellt.

## <a name="see-also"></a>Siehe auch

[ODBC Grundlagen](../../data/odbc/odbc-basics.md)
