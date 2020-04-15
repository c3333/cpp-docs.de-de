---
title: 'Gewusst wie: Erstellen einer typsicheren Auflistung'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 1901100996a776244b57efe0951795ceec3c630a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377262"
---
# <a name="how-to-make-a-type-safe-collection"></a>Gewusst wie: Erstellen einer typsicheren Auflistung

In diesem Artikel wird erläutert, wie Sie typsichere Sammlungen für Ihre eigenen Datentypen erstellen. Dabei werden folgende Themen behandelt:

- [Verwenden von vorlagenbasierten Klassen für die Typsicherheit](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementieren von Hilfsfunktionen](#_core_implementing_helper_functions)

- [Verwenden von Nichtvorlagenauflistungsklassen](#_core_using_nontemplate_collection_classes)

Die Microsoft Foundation-Klassenbibliothek stellt vordefinierte typsichere Sammlungen basierend auf C++-Vorlagen bereit. Da es sich um Vorlagen handelt, bieten diese Klassen typsicher und benutzerfreundlich, ohne dass die Typumwandlung und andere zusätzliche Arbeiten für die Verwendung einer Nichtvorlagenklasse für diesen Zweck zu erledigen sind. Das MFC-Beispiel [COLLECT](../overview/visual-cpp-samples.md) veranschaulicht die Verwendung vorlagenbasierter Auflistungsklassen in einer MFC-Anwendung. Verwenden Sie diese Klassen im Allgemeinen jedes Mal, wenn Sie neuen Sammlungscode schreiben.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Verwenden von vorlagenbasierten Klassen für die Typsicherheit

#### <a name="to-use-template-based-classes"></a>So verwenden Sie vorlagenbasierte Klassen

1. Deklarieren Sie eine Variable des Auflistungsklassentyps. Beispiel:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Rufen Sie die Memberfunktionen des Auflistungsobjekts auf. Beispiel:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. Implementieren Sie bei Bedarf die [Hilfsfunktionen](../mfc/reference/collection-class-helpers.md) und [SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements). Informationen zum Implementieren dieser Funktionen finden Sie unter [Implementieren von Hilfsfunktionen](#_core_implementing_helper_functions).

Dieses Beispiel zeigt die Deklaration einer Liste ganzer Zahlen. Der erste Parameter in Schritt 1 ist der Typ der Daten, die als Elemente der Liste gespeichert werden. Der zweite Parameter gibt an, wie die Daten an Memberfunktionen der Auflistungsklasse übergeben und von diesen zurückgegeben werden sollen, z. `Add` B. und `GetAt`.

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementieren von Hilfsfunktionen

Die vorlagenbasierten Auflistungsklassen `CArray`, `CList`und `CMap` verwenden fünf globale Hilfsfunktionen, die Sie bei Bedarf für Ihre abgeleitete Auflistungsklasse anpassen können. Informationen zu diesen Hilfsfunktionen finden Sie unter [Auflistungsklassenhelfer](../mfc/reference/collection-class-helpers.md) in der *MFC-Referenz*. Die Implementierung der Serialisierungsfunktion ist für die meisten Verwendungen der vorlagenbasierten Auflistungsklassen erforderlich.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serialisieren von Elementen

Die `CArray` `CList`, `CMap` und `SerializeElements` Klassen rufen Auflistungselemente auf, um sie in einem Archiv zu speichern oder aus einem Archiv zu lesen.

Die Standardimplementierung `SerializeElements` der Hilfsfunktion schreibt bitweise von den Objekten in das Archiv oder liest ein Bitweises aus dem Archiv in die Objekte, je nachdem, ob die Objekte im Archiv gespeichert oder aus dem Archiv abgerufen werden. Überschreiben, `SerializeElements` wenn diese Aktion nicht geeignet ist.

Wenn Ihre Sammlung Objekte `CObject` speichert, `IMPLEMENT_SERIAL` die von der Sammlung abgeleitet wurden, und Sie das Makro `CArchive` in `CObject`der Implementierung der Auflistungselementklasse verwenden, können Sie die Vorteile der Serialisierungsfunktionalität nutzen, die in und: integriert ist:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Die überladenen `CArchive` Einfügeoperatoren für den Aufruf `CObject::Serialize` (oder eine Außerkraftsetzung dieser Funktion) für jedes `CPerson` Objekt.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Verwenden von Nontemplate-Auflistungsklassen

MFC unterstützt auch die Mitminadenklassen, die mit MFC-Version 1.0 eingeführt wurden. Diese Klassen basieren nicht auf Vorlagen. Sie können verwendet werden, um `CObject*`Daten `UINT` `DWORD`der `CString`unterstützten Typen , , und zu enthalten. Sie können diese vordefinierten Auflistungen (z. B. `CObList` `CObject`) verwenden, um Auflistungen von Objekten zu enthalten, die von abgeleitet wurden. MFC stellt auch andere vordefinierte Auflistungen `UINT` bereit, um`void`primitive Typen wie und void-Zeiger ( *) zu halten. Im Allgemeinen ist es jedoch häufig nützlich, eigene typsichere Sammlungen zu definieren, um Objekte einer spezifischeren Klasse und ihrer Derivate zu enthalten. Beachten Sie, dass dies mit den Auflistungsklassen, die nicht auf Vorlagen basieren, mehr Arbeit ist als die Verwendung der vorlagenbasierten Klassen.

Es gibt zwei Möglichkeiten, typsichere Sammlungen mit den Nichtvorlagensammlungen zu erstellen:

1. Verwenden Sie die Nichtvorlagensammlungen, bei Bedarf mit Typumwandlung. Dies ist der einfachere Ansatz.

1. Ableiten und Erweitern einer nicht-vorlagentypsicheren Auflistung.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>So verwenden Sie die Nichtvorlagensammlungen mit Typumwandlung

1. Verwenden Sie eine der Nichtvorlagenklassen, z. `CWordArray`B. direkt .

   Sie können z. `CWordArray` B. einen erstellen und beliebige 32-Bit-Werte hinzufügen und diese dann abrufen. Es gibt nichts mehr zu tun. Sie verwenden nur die vordefinierte Funktionalität.

   Sie können auch eine vordefinierte `CObList`Auflistung verwenden, z. `CObject`B. , um alle von abgeleiteten Objekte zu halten. Eine `CObList` Auflistung ist definiert, um `CObject`Zeiger auf zu halten. Wenn Sie ein Objekt aus der Liste abrufen, müssen Sie das `CObList` Ergebnis möglicherweise in `CObject`den richtigen Typ umsetzen, da die Funktionen Zeiger auf zurückgeben. Wenn Sie beispielsweise `CPerson` Objekte in `CObList` einer Auflistung speichern, müssen Sie ein abgerufenes `CPerson` Element als Zeiger auf ein Objekt umsetzen. Im folgenden Beispiel `CObList` wird `CPerson` eine Auflistung zum Aufnehmen von Objekten verwendet:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Diese Technik der Verwendung eines vordefinierten Sammlungstyps und Ggf. des Gießens kann für viele Ihrer Sammlungsanforderungen geeignet sein. Wenn Sie weitere Funktionen oder mehr Typsicherheit benötigen, verwenden Sie eine vorlagenbasierte Klasse, oder führen Sie das nächste Verfahren aus.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Ableiten und Erweitern einer nicht-vorlagensicheren Auflistung

1. Leiten Sie Ihre eigene Auflistungsklasse von einer der vordefinierten Nichtvorlagenklassen ab.

   Wenn Sie Ihre Klasse ableiten, können Sie typsichere Wrapperfunktionen hinzufügen, um eine typsichere Schnittstelle zu vorhandenen Funktionen bereitzustellen.

   Wenn Sie z. B. `CObList` eine `CPerson` Liste abgeleitet haben, aus `AddHeadPerson` `GetHeadPerson`der Objekte enthalten sind, können Sie die Wrapperfunktionen und , wie unten gezeigt, hinzufügen.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Diese Wrapperfunktionen bieten eine typsichere Möglichkeit `CPerson` zum Hinzufügen und Abrufen von Objekten aus der abgeleiteten Liste. Sie können sehen, `GetHeadPerson` dass Sie für die Funktion einfach die Typumwandlung kapseln.

   Sie können auch neue Funktionen hinzufügen, indem Sie neue Funktionen definieren, die die Funktionen der Auflistung erweitern, anstatt nur vorhandene Funktionen in typsichere Wrapper umzuschließen. Der Artikel [Löschen aller Objekte in einer CObject-Auflistung](../mfc/deleting-all-objects-in-a-cobject-collection.md) beschreibt beispielsweise eine Funktion zum Löschen aller in einer Liste enthaltenen Objekte. Diese Funktion könnte der abgeleiteten Klasse als Memberfunktion hinzugefügt werden.

## <a name="see-also"></a>Siehe auch

[Sammlungen](../mfc/collections.md)
