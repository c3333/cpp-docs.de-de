---
title: Explizite Instantiierung
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361958"
---
# <a name="explicit-instantiation"></a>Explizite Instantiierung

Mit expliziter Instanziierung können Sie eine Instanziierung einer auf Vorlagen basierenden Klasse oder Funktion erstellen, ohne sie tatsächlich im Code zu verwenden. Da dies nützlich ist, wenn Sie Bibliotheksdateien (LIB-Dateien) erstellen, die Vorlagen zur Verteilung verwenden, werden nicht instanziierte Vorlagendefinitionen nicht in Objektdateien (OBJ-Dateien) abgelegt.

Dieser Code instanziiert `MyStack` explizit für **int-Variablen** und sechs Elemente:

```cpp
template class MyStack<int, 6>;
```

Diese Anweisung erstellt eine Instanziierung von `MyStack`, ohne Speicher für ein Objekt zu reservieren. Code wird für alle Member generiert.

Die nächste Zeile instanziiert explizit nur die Konstruktormemberfunktion:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Sie können Funktionsvorlagen explizit instanziieren, indem Sie ein bestimmtes Typargument verwenden, um sie erneut zu deklarieren, wie im Beispiel unter [Funktionsvorlageninstanziierung](../cpp/function-template-instantiation.md)gezeigt.

Sie können das **Schlüsselwort extern** verwenden, um die automatische Instanziierung von Mitgliedern zu verhindern. Beispiel:

```cpp
extern template class MyStack<int, 6>;
```

Entsprechend können Sie bestimmte Member als nicht instanziiert und extern kennzeichnen:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Sie können das schlüsselwortbesagte **Schlüsselwort extern** verwenden, um zu verhindern, dass der Compiler denselben Instanziierungscode in mehr als einem Objektmodul generiert. Sie müssen die Vorlagenfunktion instanziieren, indem Sie die angegebenen expliziten Vorlagenparameter in mindestens einem verknüpften Modul verwenden, wenn die Funktion aufgerufen wird. Andernfalls erhalten Sie einen Linkerfehler, wenn das Programm erstellt wird.

> [!NOTE]
> Das **externe** Schlüsselwort in der Spezialisierung gilt nur für Memberfunktionen, die außerhalb des Hauptteils der Klasse definiert sind. Die Funktionen, die in der Klassendeklaration definiert werden, gelten als Inlinefunktionen und werden immer instanziiert.

## <a name="see-also"></a>Siehe auch

[Funktionsvorlagen](../cpp/function-templates.md)
