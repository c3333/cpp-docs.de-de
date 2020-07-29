---
title: Explizite Instantiierung
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 4b1808791110c4eed237d18436897dac59170206
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232299"
---
# <a name="explicit-instantiation"></a>Explizite Instantiierung

Mit expliziter Instanziierung können Sie eine Instanziierung einer auf Vorlagen basierenden Klasse oder Funktion erstellen, ohne sie tatsächlich im Code zu verwenden. Da dies nützlich ist, wenn Sie Bibliotheksdateien (LIB-Dateien) erstellen, die Vorlagen zur Verteilung verwenden, werden nicht instanziierte Vorlagendefinitionen nicht in Objektdateien (OBJ-Dateien) abgelegt.

Dieser Code instanziiert explizit `MyStack` für **`int`** Variablen und sechs Elemente:

```cpp
template class MyStack<int, 6>;
```

Diese Anweisung erstellt eine Instanziierung von `MyStack`, ohne Speicher für ein Objekt zu reservieren. Code wird für alle Member generiert.

Die nächste Zeile instanziiert explizit nur die Konstruktormemberfunktion:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Sie können Funktions Vorlagen explizit instanziieren, indem Sie ein bestimmtes Typargument verwenden, um Sie erneut zu deklarieren, wie im Beispiel unter [Funktions Vorlagen Instanziierung](../cpp/function-template-instantiation.md)gezeigt.

Sie können das **`extern`** Schlüsselwort verwenden, um die automatische Instanziierung von Membern zu verhindern. Beispiel:

```cpp
extern template class MyStack<int, 6>;
```

Entsprechend können Sie bestimmte Member als nicht instanziiert und extern kennzeichnen:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Sie können das **`extern`** Schlüsselwort verwenden, um zu verhindern, dass der Compiler denselben instanziationcode in mehr als einem Objekt Modul erzeugt. Sie müssen die Vorlagenfunktion instanziieren, indem Sie die angegebenen expliziten Vorlagenparameter in mindestens einem verknüpften Modul verwenden, wenn die Funktion aufgerufen wird. Andernfalls erhalten Sie einen Linkerfehler, wenn das Programm erstellt wird.

> [!NOTE]
> Das **`extern`** Schlüsselwort in der Spezialisierung gilt nur für Member-Funktionen, die außerhalb des Texts der Klasse definiert sind. Die Funktionen, die in der Klassendeklaration definiert werden, gelten als Inlinefunktionen und werden immer instanziiert.

## <a name="see-also"></a>Weitere Informationen

[Funktions Vorlagen](../cpp/function-templates.md)
