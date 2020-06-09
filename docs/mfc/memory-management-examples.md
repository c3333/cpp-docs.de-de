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
ms.openlocfilehash: ca5056303f77f112e18ef09d606789a5b1c92acd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626317"
---
# <a name="memory-management-examples"></a>Speicherverwaltung: Beispiele

In diesem Artikel wird beschrieben, wie MFC Frame Belegungen und Heap Zuweisungen für jede der drei typischen Arten von Speicher Belegungen durchführt:

- [Ein Bytearray](#_core_allocation_of_an_array_of_bytes)

- [Eine Datenstruktur](#_core_allocation_of_a_data_structure)

- [Ein Objekt](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Zuordnung eines Bytearrays

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>So weisen Sie ein Array von Bytes im Frame zu

1. Definieren Sie das Array wie im folgenden Code gezeigt. Das Array wird automatisch gelöscht, und sein Speicher wird freigegeben, wenn die Array Variable den Gültigkeitsbereich verlässt.

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>So weisen Sie ein Bytearray (oder einen beliebigen primitiven Datentyp) auf dem Heap zu

1. Verwenden Sie den **New** -Operator mit der in diesem Beispiel gezeigten Array Syntax:

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>So setzen Sie die Zuteilung der Arrays aus dem Heap um

1. Verwenden Sie den **Delete** -Operator wie folgt:

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Zuordnung einer Datenstruktur

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>So weisen Sie dem Frame eine Datenstruktur zu

1. Definieren Sie die Struktur Variable wie folgt:

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   Der von der Struktur belegte Arbeitsspeicher wird freigegeben, wenn er seinen Gültigkeitsbereich verlässt.

#### <a name="to-allocate-data-structures-on-the-heap"></a>So weisen Sie Datenstrukturen auf dem Heap zu

1. Verwenden Sie **neu** , um Datenstrukturen auf dem Heap zuzuordnen, und löschen Sie Sie, um deren Zuteilung zu **Entfernen** , wie in den folgenden Beispielen gezeigt:

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Zuordnung eines Objekts

#### <a name="to-allocate-an-object-on-the-frame"></a>So weisen Sie ein Objekt im Frame zu

1. Deklarieren Sie das Objekt wie folgt:

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   Der Dekonstruktor für das-Objekt wird automatisch aufgerufen, wenn das-Objekt den Gültigkeitsbereich verlässt.

#### <a name="to-allocate-an-object-on-the-heap"></a>So weisen Sie ein Objekt auf dem Heap zu

1. Verwenden Sie den **New** -Operator, der einen Zeiger auf das-Objekt zurückgibt, um Objekte auf dem Heap zuzuordnen. Verwenden Sie den **Delete** -Operator, um Sie zu löschen.

   In den folgenden Heap-und Frame Beispielen wird davon ausgegangen, dass der `CPerson` Konstruktor keine Argumente annimmt.

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   Wenn das Argument für den `CPerson` Konstruktor ein Zeiger auf **char**ist, lautet die Anweisung für die Frame Zuordnung wie folgt:

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   Die-Anweisung für die Heap Zuordnung lautet:

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung: Heapbelegung](memory-management-heap-allocation.md)
