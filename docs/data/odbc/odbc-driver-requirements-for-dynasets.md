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
ms.openlocfilehash: 4c436764649a1aa418e12300809482b45224dd46
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403841"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>ODBC-Treiberanforderungen für Dynasets

In den MFC-ODBC-Datenbankklassen sind Dynasets Recordsets mit dynamischen Eigenschaften. Sie bleiben auf bestimmte Weise mit der Datenquelle synchronisiert. MFC-Dynasets (aber keine vorwärts gerichteten Recordsets) erfordern einen ODBC-Treiber mit API-Konformität der Ebene 2. Wenn der Treiber für die [Datenquelle](../../data/odbc/data-source-odbc.md) mit dem API-Satz der Ebene 1 konform ist, können Sie weiterhin sowohl aktualisierbare als auch schreibgeschützte Momentaufnahmen und Vorwärts-Recordsets, aber keine Dynasets verwenden. Ein Treiber der Ebene 1 kann jedoch Dynasets unterstützen, wenn er erweiterte Abruf-und keysetgesteuerte Cursor unterstützt.

In der ODBC-Terminologie werden Dynasets und Momentaufnahmen als Cursor bezeichnet. Ein Cursor ist ein Mechanismus, der zum Nachverfolgen seiner Position in einem Recordset verwendet wird. Weitere Informationen zu Treiber Anforderungen für Dynasets finden Sie unter [Dynaset](../../data/odbc/dynaset.md). Weitere Informationen zu Cursorn finden Sie in der Open Database Connectivity-Dokumentation [(ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) .

> [!NOTE]
> Bei aktualisierbaren Recordsets muss der ODBC-Treiber entweder positionierte UPDATE-Anweisungen oder die `::SQLSetPos` ODBC-API-Funktion unterstützen. Wenn beide unterstützt werden, verwendet MFC `::SQLSetPos` aus Effizienzgründen. Für Momentaufnahmen können Sie alternativ die Cursor Bibliothek verwenden, die die erforderliche Unterstützung für aktualisierbare Momentaufnahmen (statische Cursor und positionierte UPDATE-Anweisungen) bereitstellt.

## <a name="see-also"></a>Weitere Informationen

[ODBC-Grundlagen](../../data/odbc/odbc-basics.md)
