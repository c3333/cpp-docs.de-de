---
title: Basierte Zeiger (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: e5d8c529adfb92c9db1fdcc5a38f688853606d5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327430"
---
# <a name="based-pointers-c"></a>Basierte Zeiger (C)

**Microsoft-spezifisch**

[__based (C++-Verweis)](../cpp/based-pointers-cpp.md)

Für die 32-Bit- und 64-Bit-C-Compiler von Microsoft ist ein basierter Zeiger ein 32-Bit- oder 64-Bit-Offset einer 32-Bit- oder 64-Bit-Zeigerbasis. Die basierende Adressierung eignet sich zur Ausübung der Kontrolle über Abschnitte, denen Objekte zugeordnet sind; dadurch werden die Größe der ausführbaren Datei verringert und die Ausführungsgeschwindigkeit erhöht. Im Allgemeinen ist die Form zum Angeben eines basierten Zeigers

> *Typ* **__based(** *Basis* **)** *Deklarator*

Die "basierend auf Zeiger"-Variante der basierenden Adressierung ermöglicht die Angabe eines Zeigers als Basis. Der basierte Zeiger ist dann ein Offset im Arbeitsspeicherbereich, der am Anfang des Zeigers beginnt, auf dem er basiert. Zeiger, die auf Zeigeradressen basieren, sind die einzige Form des `__based`-Schlüsselworts, das in 32-Bit- und 64-Bit-Kompilierungen gültig ist. In solchen Kompilierungen sind sie 32-Bit- oder 64-Bit-Verschiebungen von einer 32-Bit- oder 64-Bit-Basis.

Eine Verwendung von Zeigern, die auf Zeigern basieren, ist für dauerhafte Bezeichner, die Zeiger enthalten. Eine verknüpfte Liste, die aus Zeigern auf Grundlage eines Zeigers besteht, kann auf Datenträger gespeichert werden, dann an eine andere Stelle im Arbeitsspeicher neu geladen werden, wobei die Zeiger weiterhin gültig bleiben.

Das folgende Beispiel zeigt einen Zeiger, der auf einem Zeiger basiert.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Dem Zeiger `vpBuffer` wird die Adresse des später im Programm zugewiesenen Arbeitsspeichers zugeteilt. Die verknüpfte Liste wird relativ zum Wert von `vpBuffer` verschoben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
