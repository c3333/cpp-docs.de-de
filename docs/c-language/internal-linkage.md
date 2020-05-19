---
title: Interne Verknüpfung
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 79601af27f847a3afe7e8bdaefa926cd45459847
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325922"
---
# <a name="internal-linkage"></a>Interne Verknüpfung

Wenn die Deklaration eines Dateibereichsbezeichners für ein Objekt oder eine Funktion den *Speicherklassenspezifizierer* **static** enthält, weist der Bezeichner eine interne Bindung auf. Andernfalls hat der Bezeichner eine externe Bindung. Weitere Informationen erhalten Sie in der Erläuterung der *Speicherklassenspezifizierer*-Nichtterminale unter [Speicherklassen](../c-language/c-storage-classes.md).

Innerhalb einer Übersetzungseinheit kennzeichnet jede Instanz eines Bezeichners mit interner Bindung denselben Bezeichner bzw. dieselbe Funktion. Intern gebundene Bezeichner sind für eine Übersetzungseinheit eindeutig.

## <a name="see-also"></a>Siehe auch

[Verwenden von "extern" zur Angabe der Verknüpfung](../cpp/using-extern-to-specify-linkage.md)
