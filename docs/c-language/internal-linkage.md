---
title: Interne Verknüpfung
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 3709ca815877b98fe5dfe6e5b2eca6b5c627641b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229596"
---
# <a name="internal-linkage"></a>Interne Verknüpfung

Wenn die Deklaration eines Dateibereichsbezeichners für ein Objekt oder eine Funktion den *Speicherklassenspezifizierer* **`static`** enthält, weist der Bezeichner eine interne Bindung auf. Andernfalls hat der Bezeichner eine externe Bindung. Weitere Informationen erhalten Sie in der Erläuterung der *Speicherklassenspezifizierer*-Nichtterminale unter [Speicherklassen](../c-language/c-storage-classes.md).

Innerhalb einer Übersetzungseinheit kennzeichnet jede Instanz eines Bezeichners mit interner Bindung denselben Bezeichner bzw. dieselbe Funktion. Intern gebundene Bezeichner sind für eine Übersetzungseinheit eindeutig.

## <a name="see-also"></a>Siehe auch

[Verwenden von "extern" zur Angabe der Verknüpfung](../cpp/using-extern-to-specify-linkage.md)
