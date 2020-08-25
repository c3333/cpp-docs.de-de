---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: f3f6c4886d22c7cd12b29950c114fbcde8905c28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845743"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Beziehen Sie den `iostreams`-Standardheader \<iomanip> mit ein, um verschiedene Manipulatoren zu definieren, die jeweils ein einzelnes Argument verwenden.

## <a name="syntax"></a>Syntax

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Bemerkungen

Jeder dieser Manipulatoren gibt einen nicht angegebenen Typ zurück, der `T1` durch aufgerufen `T10` wird, der sowohl `basic_istream` \<**Elem**, **Tr**> `::` [Operator>>](../standard-library/istream-operators.md#op_gt_gt) als auch `basic_ostream` \<**Elem**, **Tr**> `::` [Operator<<](../standard-library/ostream-operators.md#op_lt_lt)überlädt.

### <a name="manipulators"></a>Manipulatoren

|Name|Beschreibung|
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Ruft einen Geldbetrag ab, optional in einem internationalen Format.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Ruft eine Uhrzeit in einer Zeitstruktur mithilfe eines angegebenen Formats ab.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Stellt einen Geldbetrag bereit, optional in einem internationalen Format.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Stellt eine Uhrzeit in einer Zeitstruktur und eine Formatzeichenfolge für die Verwendung bereit.|
|[notiert](../standard-library/iomanip-functions.md#quoted)|Ermöglicht praktische Roundtrips von Zeichenfolgen mit „insertion“ und „extraction“-Operatoren.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Löscht die angegebenen Flags.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Legt die Basis für Ganzzahlen fest.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Legt das zum Auffüllen in einer rechts ausgerichteten Anzeige verwendete Zeichen fest.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Legt die angegebenen Flags fest.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Legt die Genauigkeit für Gleitkommawerte fest.|
|[setw](../standard-library/iomanip-functions.md#setw)|Gibt die Breite des Anzeigefelds an.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
