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
ms.openlocfilehash: 6ee4603f03ef8a95c218b0fe040e9606aab99ebb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620010"
---
# <a name="how-to-make-a-type-safe-collection"></a>Gewusst wie: Erstellen einer typsicheren Auflistung

In diesem Artikel wird erläutert, wie typsichere Auflistungen für eigene Datentypen durchführen werden. Dabei werden folgende Themen behandelt:

- [Verwenden von Vorlagen basierten Klassen für Typsicherheit](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementieren von Hilfsfunktionen](#_core_implementing_helper_functions)

- [Verwenden von nicht Vorlagen Auflistungs Klassen](#_core_using_nontemplate_collection_classes)

Der Microsoft Foundation Class-Bibliothek stellt vordefinierte typsichere Auflistungen basierend auf C++-Vorlagen bereit. Da es sich um Vorlagen handelt, helfen diese Klassen dabei, Typsicherheit und Benutzerfreundlichkeit zu bieten, ohne die Typumwandlung und andere zusätzliche Arbeitsschritte bei der Verwendung einer nicht-Vorlagen Klasse zu diesem Zweck. Die MFC- [Beispiel Sammlung](../overview/visual-cpp-samples.md) veranschaulicht die Verwendung von Vorlagen basierten Auflistungs Klassen in einer MFC-Anwendung. Im Allgemeinen verwenden Sie diese Klassen immer dann, wenn Sie neuen Auflistungs Code schreiben.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Verwenden von Vorlagen basierten Klassen für Typsicherheit

#### <a name="to-use-template-based-classes"></a>So verwenden Sie vorlagenbasierte Klassen

1. Deklarieren Sie eine Variable des Auflistungs Klassen Typs. Beispiel:

   [!code-cpp[NVC_MFCCollections#7](codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Ruft die Element Funktionen des Auflistungs Objekts auf. Beispiel:

   [!code-cpp[NVC_MFCCollections#8](codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. Implementieren Sie ggf. die [Hilfsfunktionen](reference/collection-class-helpers.md) und [SerializeElements](reference/collection-class-helpers.md#serializeelements). Weitere Informationen zum Implementieren dieser Funktionen finden Sie unter [Implementieren von Hilfsfunktionen](#_core_implementing_helper_functions).

Dieses Beispiel zeigt die Deklaration einer Liste von ganzen Zahlen. Der erste Parameter in Schritt 1 ist der Typ der Daten, die als Elemente der Liste gespeichert werden. Der zweite Parameter gibt an, wie die Daten an Element Funktionen der Auflistungs Klasse übergeben und von diesen zurückgegeben werden, z `Add` `GetAt` . b. und.

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementieren von Hilfsfunktionen

Die Vorlagen basierten Auflistungs Klassen `CArray` , `CList` und `CMap` verwenden fünf globale Hilfsfunktionen, die Sie nach Bedarf für Ihre abgeleitete Auflistungs Klasse anpassen können. Weitere Informationen zu diesen Hilfsfunktionen finden Sie unter Auflistungs [Klassen](reference/collection-class-helpers.md) -Hilfsprogramme in der *MFC-Referenz*. Die Implementierung der Serialisierungsfunktion ist für die meisten Verwendungen der Vorlagen basierten Auflistungs Klassen erforderlich.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serialisieren von Elementen

Die `CArray` `CList` Klassen, und werden `CMap` aufgerufen `SerializeElements` , um Auflistungs Elemente zu speichern oder aus einem Archiv zu lesen.

Die Standard Implementierung der `SerializeElements` Hilfsfunktion führt einen bitweisen Schreibvorgang aus den Objekten in das Archiv oder einen bitweisen Lesevorgang aus dem Archiv auf die Objekte aus, je nachdem, ob die Objekte in dem Archiv gespeichert oder aus dem Archiv abgerufen werden. Überschreiben, `SerializeElements` Wenn diese Aktion nicht geeignet ist.

Wenn Ihre Auflistung von abgeleitete Objekte speichert `CObject` und Sie das- `IMPLEMENT_SERIAL` Makro in der Implementierung der Auflistungs Element-Klasse verwenden, können Sie die in und integrierte serialisierungsfunktionalität nutzen. `CArchive` `CObject`

[!code-cpp[NVC_MFCCollections#9](codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Die überladenen einfügeoperatoren für den `CArchive` Rückruf `CObject::Serialize` (oder eine Überschreibung dieser Funktion) für jedes `CPerson` Objekt.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Verwenden von nicht Vorlagen Auflistungs Klassen

MFC unterstützt auch die Auflistungs Klassen, die mit MFC Version 1,0 eingeführt wurden. Diese Klassen basieren nicht auf Vorlagen. Sie können verwendet werden, um Daten der unterstützten Typen `CObject*` , `UINT` , `DWORD` und zu enthalten `CString` . Sie können diese vordefinierten Auflistungen (z. b.) verwenden, um Auflistungen `CObList` aller von abgeleiteten Objekte aufzunehmen `CObject` . MFC bietet auch andere vordefinierte Auflistungen, die primitive Typen wie `UINT` und void-Zeiger ( `void` *) enthalten. Im Allgemeinen ist es jedoch oft hilfreich, eigene typsichere Auflistungen zu definieren, die Objekte einer spezifischeren Klasse und ihrer Ableitungen enthalten. Beachten Sie, dass die Verwendung der Auflistungs Klassen, die nicht auf Vorlagen basieren, mehr Arbeit als die Verwendung der Vorlagen basierten Klassen ist.

Es gibt zwei Möglichkeiten, typsichere Auflistungen mit den nicht Vorlagen Auflistungen zu erstellen:

1. Verwenden Sie ggf. die Auflistungs-Auflistungen mit Typumwandlung. Dies ist der einfachere Ansatz.

1. Leiten Sie von ab, und erweitern Sie eine nicht Vorlagen-typsichere Auflistung.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>So verwenden Sie die Auflistungs-Auflistungen mit Typumwandlung

1. Verwenden Sie eine der nicht Vorlagen Klassen, z `CWordArray` . b. direkt.

   Beispielsweise können Sie einen erstellen `CWordArray` und ihm alle 32-Bit-Werte hinzufügen und diese dann abrufen. Es gibt nichts mehr zu tun. Sie verwenden einfach die vordefinierte Funktionalität.

   Sie können auch eine vordefinierte Auflistung, z `CObList` . b., verwenden, um alle von abgeleiteten Objekte zu speichern `CObject` . Eine Auflistung `CObList` ist so definiert, dass Zeiger auf gespeichert werden `CObject` . Wenn Sie ein Objekt aus der Liste abrufen, müssen Sie das Ergebnis möglicherweise in den richtigen Typ umwandeln, da die `CObList` Funktionen Zeiger auf zurückgeben `CObject` . Wenn Sie z. b `CPerson` . Objekte in einer Auflistung speichern `CObList` , müssen Sie ein abgerufenes Element in einen Zeiger auf ein- `CPerson` Objekt umwandeln. Im folgenden Beispiel wird eine Auflistung `CObList` zum Speichern von- `CPerson` Objekten verwendet:

   [!code-cpp[NVC_MFCCollections#10](codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Dieses Verfahren, bei dem ein vordefinierter Auflistungstyp und eine Umwandlung nach Bedarf verwendet werden, ist möglicherweise für viele ihrer Sammlungs Anforderungen geeignet. Wenn Sie weitere Funktionen oder mehr Typsicherheit benötigen, verwenden Sie eine vorlagenbasierte Klasse, oder führen Sie das nächste Verfahren aus.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>So leiten Sie eine typsichere Sammlung ohne Vorlagen ab und erweitern diese

1. Leiten Sie eine eigene Auflistungs Klasse von einer der vordefinierten nicht-Vorlagen Klassen ab.

   Wenn Sie die Klasse ableiten, können Sie typsichere Wrapper Funktionen hinzufügen, um eine typsichere Schnittstelle für vorhandene Funktionen bereitzustellen.

   Wenn Sie z. b. eine Liste von `CObList` für `CPerson` Objekte abgeleitet haben, können Sie die Wrapper Funktionen `AddHeadPerson` und hinzufügen `GetHeadPerson` , wie unten gezeigt.

   [!code-cpp[NVC_MFCCollections#11](codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Diese Wrapper Funktionen bieten eine typsichere Möglichkeit zum Hinzufügen und Abrufen `CPerson` von Objekten aus der abgeleiteten Liste. Sie können sehen, dass Sie für die `GetHeadPerson` Funktion einfach die Typumwandlung Kapseln.

   Sie können auch neue Funktionen hinzufügen, indem Sie neue Funktionen definieren, mit denen die Funktionen der Auflistung erweitert werden, anstatt nur vorhandene Funktionen in typsicheren Wrapper zu umwickeln. Der Artikel zum [Löschen aller Objekte in einer CObject](deleting-all-objects-in-a-cobject-collection.md) -Auflistung beschreibt z. b. eine Funktion, mit der alle in einer Liste enthaltenen Objekte gelöscht werden. Diese Funktion kann der abgeleiteten Klasse als Member-Funktion hinzugefügt werden.

## <a name="see-also"></a>Siehe auch

[Sammlungen](collections.md)
