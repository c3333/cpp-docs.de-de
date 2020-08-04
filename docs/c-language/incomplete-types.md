---
title: Unvollständige Typen
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: 192a6556fd8a5d3039598b883ed7c870fc01ad12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229648"
---
# <a name="incomplete-types"></a>Unvollständige Typen

Ein *unvollständiger Typ* ist ein Typ, der einen Bezeichner beschreibt, dem jedoch die Informationen fehlen, die erforderlich sind, um die Größe des Bezeichners zu bestimmen. Ein unvollständiger Typ kann Folgendes sein:

- Ein Strukturtyp, dessen Member noch nicht angegeben wurden.

- Ein Union-Typ, dessen Member noch nicht angegeben wurden.

- Ein Arraytyp, dessen Dimension noch nicht angegeben wurde.

Der **`void`** -Typ ist ein unvollständiger Typ, der nicht abgeschlossen werden kann. Um einen unvollständigen Typ abzuschließen, müssen Sie die fehlenden Informationen angeben. Die folgenden Beispiele zeigen, wie Sie die unvollständigen Typen erstellen und abschließen.

- Um einen unvollständigen Strukturtyp zu erstellen, müssen Sie einen Strukturtyp ohne Angabe seiner Member deklarieren. In diesem Beispiel zeigt der `ps`-Zeiger auf einen unvollständigen Strukturtyp mit der Bezeichnung `student`.

    ```C
    struct student *ps;
    ```

- Um einen unvollständigen Strukturtyp abzuschließen, müssen Sie denselben Strukturtyp später im gleichen Bereich mit den angegebenen Membern deklarieren, wie in

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- Um einen unvollständigen Arraytyp zu erstellen, müssen Sie einen Arraytyp ohne Angabe der Wiederholungsanzahl deklarieren. Zum Beispiel:

    ```C
    char a[];  /* a has incomplete type */
    ```

- Um einen unvollständigen Arraytyp abzuschließen, müssen Sie den gleichen Namen später im gleichen Bereich mit der angegebenen Wiederholungsanzahl deklarieren, wie in

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>Siehe auch

[Deklarationen und Typen](../c-language/declarations-and-types.md)
