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
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213108"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>ODBC-Treiberanforderungen für Dynasets

In den MFC-ODBC-Datenbankklassen sind Dynasets Recordsets mit dynamischen Eigenschaften. Sie bleiben auf bestimmte Weise mit der Datenquelle synchronisiert. MFC-Dynasets (aber keine vorwärts gerichteten Recordsets) erfordern einen ODBC-Treiber mit API-Konformität der Ebene 2. Wenn der Treiber für die [Datenquelle](../../data/odbc/data-source-odbc.md) mit dem API-Satz der Ebene 1 konform ist, können Sie weiterhin sowohl aktualisierbare als auch schreibgeschützte Momentaufnahmen und Vorwärts-Recordsets, aber keine Dynasets verwenden. Ein Treiber der Ebene 1 kann jedoch Dynasets unterstützen, wenn er erweiterte Abruf-und keysetgesteuerte Cursor unterstützt.

In der ODBC-Terminologie werden Dynasets und Momentaufnahmen als Cursor bezeichnet. Ein Cursor ist ein Mechanismus, der zum Nachverfolgen seiner Position in einem Recordset verwendet wird. Weitere Informationen zu Treiber Anforderungen für Dynasets finden Sie unter [Dynaset](../../data/odbc/dynaset.md). Weitere Informationen zu Cursorn finden Sie unter dem [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK in der MSDN-Dokumentation.

> [!NOTE]
>  Bei aktualisierbaren Recordsets muss der ODBC-Treiber entweder positionierte UPDATE-Anweisungen oder die `::SQLSetPos` ODBC-API-Funktion unterstützen. Wenn beide unterstützt werden, verwendet MFC `::SQLSetPos` aus Gründen der Effizienz. Für Momentaufnahmen können Sie alternativ die Cursor Bibliothek verwenden, die die erforderliche Unterstützung für aktualisierbare Momentaufnahmen (statische Cursor und positionierte UPDATE-Anweisungen) bereitstellt.

## <a name="see-also"></a>Weitere Informationen

[Grundlagen zu ODBC](../../data/odbc/odbc-basics.md)
