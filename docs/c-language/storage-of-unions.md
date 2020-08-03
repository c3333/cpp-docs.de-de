---
title: Speicherung von Unions
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 64e8b5184eeccd4de6d196e40ec464807bec93e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211657"
---
# <a name="storage-of-unions"></a>Speicherung von Unions

Der Speicher, der einer Union-Variable zugeordnet wird, ist der Speicher, der für den größten Member der Union erforderlich ist. Wenn ein kleinerer Member gespeichert wird, kann die Union-Variable nicht verwendeten Speicherbereich enthalten. Alle Member werden im gleichen Speicherbereich gespeichert und beginnen an derselben Adresse. Der gespeicherte Wert wird jedes Mal überschrieben, wenn einem anderen Member ein Wert zugewiesen wird. Zum Beispiel:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Die Elemente der `x`-Union fungieren in der Reihenfolge ihrer Deklaration als Zeiger auf einen **`char`** -Wert, einen **`char`** -Wert und ein Array von **`float`** -Werten. Der `x` zugeordnete Speicher ist der Speicher, der für das `f`-Array mit 20 Elementen erforderlich ist, da `f` der längste Union-Member ist. Da kein Tag der Union zugeordnet ist, ist ihr Typ unbenannt oder „anonym“.

## <a name="see-also"></a>Siehe auch

[Union-Deklarationen](../c-language/union-declarations.md)
