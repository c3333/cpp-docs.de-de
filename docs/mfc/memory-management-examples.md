---
title: 'Speicherverwaltung: Beispiele'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367852"
---
# <a name="memory-management-examples"></a>Speicherverwaltung: Beispiele

In diesem Artikel wird beschrieben, wie MFC Framezuweisungen und Heapzuordnungen für jede der drei typischen Arten von Speicherzuweisungen durchführt:

- [Ein Array von Bytes](#_core_allocation_of_an_array_of_bytes)

- [Eine Datenstruktur](#_core_allocation_of_a_data_structure)

- [Ein Objekt](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Zuweisung eines Arrays von Bytes

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>So weisen Sie ein Array von Bytes auf dem Frame zu

1. Definieren Sie das Array wie im folgenden Code dargestellt. Das Array wird automatisch gelöscht und sein Speicher freigegeben, wenn die Arrayvariable ihren Bereich beendet.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>So weisen Sie ein Array von Bytes (oder einen beliebigen primitiven Datentyp) auf dem Heap zu

1. Verwenden Sie den **neuen** Operator mit der in diesem Beispiel gezeigten Arraysyntax:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>So deallocateen Sie die Arrays aus dem Heap

1. Verwenden Sie den **Löschoperator** wie folgt:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Zuweisung einer Datenstruktur

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>So weisen Sie eine Datenstruktur auf dem Frame zu

1. Definieren Sie die Strukturvariable wie folgt:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   Der von der Struktur belegte Speicher wird freigegeben, wenn der Gültigkeitsbereich beendet wird.

#### <a name="to-allocate-data-structures-on-the-heap"></a>So weisen Sie Datenstrukturen auf dem Heap zu

1. Verwenden Sie **neu,** um Datenstrukturen auf dem Heap zuzuweisen und zu **löschen,** um sie zu verteilen, wie in den folgenden Beispielen gezeigt:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Zuordnung eines Objekts

#### <a name="to-allocate-an-object-on-the-frame"></a>So weisen Sie ein Objekt auf dem Frame zu

1. Deklarieren Sie das Objekt wie folgt:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Der Destruktor für das Objekt wird automatisch aufgerufen, wenn das Objekt seinen Bereich verlässt.

#### <a name="to-allocate-an-object-on-the-heap"></a>So weisen Sie ein Objekt auf dem Heap zu

1. Verwenden Sie den **neuen** Operator, der einen Zeiger auf das Objekt zurückgibt, um Objekte auf dem Heap zuzuweisen. Verwenden Sie den **Löschoperator,** um sie zu löschen.

   In den folgenden Heap- `CPerson` und Framebeispielen wird davon ausgegangen, dass der Konstruktor keine Argumente verwendet.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Wenn das Argument `CPerson` für den Konstruktor ein Zeiger auf **char**ist, lautet die Anweisung für die Framezuordnung:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   Die Anweisung für die Heapzuordnung lautet:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung: Heapbelegung](../mfc/memory-management-heap-allocation.md)
