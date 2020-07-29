---
title: Vorlagenbasierte Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: eceee4421b43515b9b246f4af26a1a3741c6b25b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230453"
---
# <a name="template-based-classes"></a>Vorlagenbasierte Klassen

In diesem Artikel werden die typsicheren Vorlagen basierten Auflistungs Klassen in MFC, Version 3,0 und höher, erläutert. Die Verwendung dieser Vorlagen, um typsichere Auflistungen zu erstellen, ist bequemer und bietet eine effektivere Typsicherheit als die Verwendung der Auflistungs Klassen, die nicht auf Vorlagen basieren.

MFC definiert zwei Kategorien von Vorlagen basierten Sammlungen:

- [Einfache Array-, Listen-und Zuordnungs Klassen](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Arrays, Listen und Zuordnungen von typisierten Zeigern](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Die einfachen Auflistungs Klassen werden alle von der-Klasse abgeleitet `CObject` . Sie erben daher die Serialisierung, die dynamische Erstellung und andere Eigenschaften von `CObject` . Die Klassen für typisierte Zeiger Auflistungen erfordern, dass Sie die von abgeleitete Klasse angeben – die eine der nicht Vorlagen Zeiger Auflistungen sein muss, die von MFC vordefiniert sind, z `CPtrList` `CPtrArray` . b. oder Die neue Auflistungs Klasse erbt von der angegebenen Basisklasse, und die Member-Funktionen der neuen Klasse verwenden gekapselte Aufrufe der Basisklassenmember, um Typsicherheit zu erzwingen.

Weitere Informationen zu C++-Vorlagen finden Sie unter [Vorlagen](../cpp/templates-cpp.md) in der *C++-Sprachreferenz*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Verwenden von einfachen Array-, Listen-und Karten Vorlagen

Wenn Sie die einfachen sammlungsvorlagen verwenden möchten, müssen Sie wissen, welche Art von Daten Sie in diesen Auflistungen speichern können und welche Parameter in ihren Sammlungs Deklarationen verwendet werden sollen.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Einfache Array-und Listen Verwendung

Die einfachen Array-und Listen Klassen, [CArray](../mfc/reference/carray-class.md) und [CLIST](../mfc/reference/clist-class.md), nehmen zwei Parameter an: *Type* und `ARG_TYPE` . Diese Klassen können jeden beliebigen Datentyp speichern, den Sie im *Typparameter* angeben:

- Grundlegende C++-Datentypen, z. b. **`int`** , **`char`** und**`float`**

- C++-Strukturen und-Klassen

- Andere von Ihnen definierte Typen

Aus Gründen der Effektivität und Effizienz können Sie den *arg_type* -Parameter verwenden, um den Typ der Funktionsargumente anzugeben. In der Regel geben Sie *arg_type* als Verweis auf den Typ an, den Sie im *Typparameter* benannt haben. Beispiel:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Im ersten Beispiel wird eine Array Auflistung deklariert, die `myArray` **`int`** s enthält. Im zweiten Beispiel wird eine Listen Auflistung deklariert, `myList` die- `CPerson` Objekte speichert. Bestimmte Member-Funktionen der Auflistungs Klassen akzeptieren Argumente, deren Typ durch den *arg_type* Template-Parameter angegeben wird. Die Member-Funktion der-Klasse nimmt z. b. `Add` `CArray` ein *arg_type* -Argument an:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Einfache Karten Verwendung

Die einfache Zuordnungs Klasse [(cmap](../mfc/reference/cmap-class.md)) benötigt vier Parameter *: Key*, *ARG_KEY*, *value*und *ARG_VALUE*. Wie die Array-und Listen Klassen können die Map-Klassen beliebige Datentypen speichern. Anders als Arrays und Listen, die die gespeicherten Daten indizieren und sortieren, ordnet Maps Schlüssel und Werte zu: Sie greifen auf einen Wert zu, der in einer Zuordnung gespeichert ist, indem Sie den dem Wert zugeordneten Schlüssel angeben. Der *Key* -Parameter gibt den Datentyp der Schlüssel an, die für den Zugriff auf die in der Zuordnung gespeicherten Daten verwendet werden. Wenn der Schlüsseltyp eine Struktur oder *Klasse ist,* ist der *ARG_KEY* -Parameter in der Regel ein Verweis auf den in *Key*angegebenen Typ. Der *value* -Parameter gibt den Typ der Elemente an, die in der Zuordnung gespeichert werden. Wenn der Typ *ARG_VALUE* eine Struktur oder Klasse ist, ist der *ARG_VALUE* Parameter in der Regel ein Verweis auf den Typ, der unter *Wert*angegeben ist. Beispiel:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Im ersten Beispiel werden `MY_STRUCT` Werte gespeichert, auf diese nach **`int`** Schlüsseln zugegriffen, und es werden `MY_STRUCT` Verweise auf Elemente als Verweis zurückgegeben. Im zweiten Beispiel werden `CPerson` Werte gespeichert, von `CString` Schlüsseln abgerufen und Verweise auf Elemente zurückgegeben, auf die zugegriffen wird. Dieses Beispiel kann ein einfaches Adressbuch darstellen, in dem Sie nach Nachnamen suchen.

Da der *Key* -Parameter vom Typ ist `CString` und der *KEY_TYPE* -Parameter vom Typ ist `LPCSTR` , werden die Schlüssel in der Zuordnung als Elemente des Typs gespeichert, auf Sie wird `CString` jedoch in Funktionen wie z `SetAt` . b. durch Zeiger vom Typ verwiesen `LPCSTR` . Beispiel:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Verwenden von Vorlagen für typisierte Zeiger Auflistungen

Um die sammlungsvorlagen für typisierte Zeiger zu verwenden, müssen Sie wissen, welche Arten von Daten Sie in diesen Auflistungen speichern können und welche Parameter in ihren Sammlungs Deklarationen verwendet werden sollen.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Typisiertes Zeiger Array und Listen Verwendung

Die Array-und Listen Klassen für typisierte Zeiger, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) und [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), nehmen zwei Parameter an: *BASE_CLASS* und *Type*. Diese Klassen können jeden Datentyp speichern, den Sie im *Typparameter* angeben. Sie werden von einer der nicht-Vorlagen Auflistungs Klassen abgeleitet, die Zeiger speichern. Sie geben diese Basisklasse in *BASE_CLASS*an. Verwenden Sie für Arrays entweder `CObArray` oder `CPtrArray` . Verwenden Sie für Listen entweder `CObList` oder `CPtrList` .

Wenn Sie z. b. eine Auflistung auf der Grundlage von deklarieren, `CObList` erbt die neue Klasse nicht nur die Member der Basisklasse, sondern deklariert auch eine Reihe zusätzlicher typsicherer Element Funktionen und-Operatoren, die die Typsicherheit bereitstellen, indem Aufrufe der Basisklassenmember gekapselt werden. Diese kaptypkonvertierungen verwalten alle erforderlichen Typkonvertierungen. Beispiel:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Im ersten Beispiel wird ein Array mit typisiertem Zeiger deklariert, das `myArray` von abgeleitet wird `CObArray` . Das Array speichert und gibt Zeiger auf- `CPerson` Objekte zurück (wobei `CPerson` eine von abgeleitete Klasse ist `CObject` ). Sie können jede `CObArray` Member-Funktion oder die neuen typsicheren `GetAt` `ElementAt` Funktionen und verwenden oder den typsicheren **[]** -Operator verwenden.

Im zweiten Beispiel wird eine von abgeleitete typisierte Zeiger Liste deklariert `myList` `CPtrList` . Die Liste speichert und gibt Zeiger auf- `MY_STRUCT` Objekte zurück. Eine auf basierende Klasse `CPtrList` wird zum Speichern von Zeigern auf Objekte verwendet, die nicht von abgeleitet sind `CObject` . `CTypedPtrList`verfügt über eine Reihe typsicherer Member-Funktionen: `GetHead` , `GetTail` , `RemoveHead` , `RemoveTail` , `GetNext` , `GetPrev` und `GetAt` .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Verwendung von typisierten Zeiger Zuordnungen

Die typisierte Zuordnungs Klasse " [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)" erfordert drei Parameter: *BASE_CLASS*, *Key*und *value*. Der *BASE_CLASS* -Parameter gibt die Klasse an, von der die neue Klasse abgeleitet werden soll: `CMapPtrToWord` , `CMapPtrToPtr` , `CMapStringToPtr` , `CMapWordToPtr` , `CMapStringToOb` usw. *Key* ist analog zu *Key* in `CMap` : er gibt den Typ des Schlüssels an, der für Suchvorgänge verwendet wird. Der *Wert* ist analog zum *Wert* in `CMap` : er gibt den Typ des Objekts an, das in der Zuordnung gespeichert ist. Beispiel:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Das erste Beispiel ist eine Karte, die auf – basiert und `CMapPtrToPtr` `CString` Schlüssel verwendet, die Zeiger auf zugeordnet sind `MY_STRUCT` . Sie können einen gespeicherten Zeiger suchen, indem Sie eine typsichere `Lookup` Member-Funktion aufrufen. Sie können den **[]** -Operator verwenden, um einen gespeicherten Zeiger zu suchen und ihn hinzuzufügen, wenn er nicht gefunden wurde. Und Sie können die Zuordnung mithilfe der typsicheren Funktion durchlaufen `GetNextAssoc` . Sie können auch andere Member-Funktionen der-Klasse aufzurufen `CMapPtrToPtr` .

Das zweite Beispiel ist eine Karte, die auf `CMapStringToOb` – basiert und Zeichen folgen Schlüssel verwendet, die gespeicherten Zeigern auf-Objekten zugeordnet sind `CMyObject` . Sie können die gleichen typsicheren Member verwenden, die im vorherigen Absatz beschrieben werden, oder Sie können Member der-Klasse aufzurufen `CMapStringToOb` .

> [!NOTE]
> Wenn Sie einen- **`class`** oder- **`struct`** Typ für den *value* -Parameter anstelle eines Zeigers oder Verweises auf den Typ angeben, muss die Klasse oder Struktur über einen Kopierkonstruktor verfügen.

Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer typsicheren](../mfc/how-to-make-a-type-safe-collection.md)Auflistung.

## <a name="see-also"></a>Weitere Informationen

[Sammlungen](../mfc/collections.md)
