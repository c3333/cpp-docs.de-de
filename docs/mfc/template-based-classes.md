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
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370457"
---
# <a name="template-based-classes"></a>Vorlagenbasierte Klassen

In diesem Artikel werden die typsicheren vorlagenbasierten Auflistungsklassen in MFC-Version 3.0 und höher erläutert. Die Verwendung dieser Vorlagen zum Erstellen typsicherer Sammlungen ist bequemer und hilft, die Typsicherheit effektiver zu bieten als die Verwendung der Auflistungsklassen, die nicht auf Vorlagen basieren.

MFC definiert zwei Kategorien vorlagenbasierter Sammlungen vor:

- [Einfache Array-, Listen- und Kartenklassen](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Arrays, Listen und Karten von typisierten Zeigern](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Die einfachen Auflistungsklassen werden `CObject`alle von der Klasse abgeleitet, sodass sie `CObject`die Serialisierung, die dynamische Erstellung und andere Eigenschaften von erben. Die typisierten Zeigerauflistungsklassen erfordern, dass Sie die Klasse angeben, von der Sie ableiten – eine `CPtrList` der `CPtrArray`nicht vorlagendefinierten Zeigerauflistungen, die von MFC vordefiniert sind, z. B. oder . Die neue Auflistungsklasse erbt von der angegebenen Basisklasse, und die Memberfunktionen der neuen Klasse verwenden gekapselte Aufrufe an die Basisklassenmember, um die Typsicherheit zu erzwingen.

Weitere Informationen zu C++-Vorlagen finden Sie unter [Vorlagen](../cpp/templates-cpp.md) in der *C++-Sprachreferenz*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Verwenden einfacher Array-, Listen- und Kartenvorlagen

Um die einfachen Sammlungsvorlagen zu verwenden, müssen Sie wissen, welche Art von Daten Sie in diesen Sammlungen speichern können und welche Parameter in Ihren Sammlungsdeklarationen verwendet werden sollen.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Einfache Array- und Listenverwendung

Die einfachen Array- und Listenklassen [CArray](../mfc/reference/carray-class.md) und [CList](../mfc/reference/clist-class.md)verwenden zwei Parameter: *TYPE* und `ARG_TYPE`. Diese Klassen können jeden Datentyp speichern, den Sie im *Type-Parameter* angeben:

- Grundlegende C++-Datentypen, z. B. **int**, **char**und **float**

- C++-Strukturen und -Klassen

- Andere Typen, die Sie definieren

Aus Gründen der Benutzerfreundlichkeit und Effizienz können Sie den *Parameter ARG_TYPE* verwenden, um den Typ der Funktionsargumente anzugeben. In der Regel geben Sie *ARG_TYPE* als Verweis auf den Typ an, den Sie im *Type-Parameter* angegeben haben. Beispiel:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Im ersten Beispiel wird `myArray`eine Arrayauflistung deklariert, die **int**s enthält. Im zweiten Beispiel wird `myList`eine Listenauflistung deklariert, die Objekte speichert. `CPerson` Bestimmte Memberfunktionen der Auflistungsklassen verwenden Argumente, *ARG_TYPE* deren Typ durch den ARG_TYPE-Vorlagenparameter angegeben wird. Die `Add` Memberfunktion der Klasse `CArray` nimmt z. B. ein *ARG_TYPE* Argument an:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Einfache Kartennutzung

Die einfache Kartenklasse [CMap](../mfc/reference/cmap-class.md)nimmt vier Parameter: *KEY*, *ARG_KEY*, *VALUE*und *ARG_VALUE*. Wie die Array- und Listenklassen können die Kartenklassen jeden Datentyp speichern. Im Gegensatz zu Arrays und Listen, die die gespeicherten Daten indizieren und ordnen, werden Schlüssel und Werte zugeordnet: Sie greifen auf einen in einer Zuordnung gespeicherten Wert zu, indem Sie den zugeordneten Schlüssel des Werts angeben. Der *Key-Parameter* gibt den Datentyp der Schlüssel an, die für den Zugriff auf in der Karte gespeicherte Daten verwendet werden. Wenn der Typ von *KEY* eine Struktur oder Klasse ist, ist der *parameter ARG_KEY* in der Regel ein Verweis auf den in *KEY*angegebenen Typ. Der Parameter *VALUE* gibt den Typ der in der Karte gespeicherten Elemente an. Wenn der Typ *ARG_VALUE* eine Struktur oder Klasse ist, ist der Parameter *ARG_VALUE* in der Regel ein Verweis auf den in *WERT*angegebenen Typ. Beispiel:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Im ersten `MY_STRUCT` Beispiel werden Werte gespeichert, sie über `MY_STRUCT` **int-Schlüssel** aufgerufen und Elemente zurückgegeben, auf die zugegriffen wird, indem sie referenziert werden. Im zweiten `CPerson` Beispiel werden Werte `CString` gespeichert, sie über Schlüssel abgerufen und Verweise auf Elemente zurückgegeben, auf die zugegriffen wird. Dieses Beispiel kann ein einfaches Adressbuch darstellen, in dem Sie Personen nach Demondat suchen.

Da der *KEY-Parameter* `CString` vom Typ ist und der parameter *KEY_TYPE* vom Typ `LPCSTR` `CString` ist, werden die Schlüssel in der Karte als Elemente vom Typ gespeichert, aber in Funktionen wie `SetAt` durch Zeiger vom Typ `LPCSTR`referenziert. Beispiel:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Verwenden von Typd-Pointer-Sammlungsvorlagen

Um die Typd-Zeiger-Auflistungsvorlagen zu verwenden, müssen Sie wissen, welche Arten von Daten Sie in diesen Auflistungen speichern können und welche Parameter in Ihren Auflistungsdeklarationen verwendet werden sollen.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Typisiertes Zeiger-Array und Listenverwendung

Die typd-pointer array und list klassen, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) und [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), nehmen zwei Parameter: *BASE_CLASS* und *TYPE*. Diese Klassen können jeden Datentyp speichern, den Sie im *Type-Parameter* angeben. Sie werden von einer der Nichtvorlagenauflistungsklassen abgeleitet, in denen Zeiger gespeichert werden. Sie geben diese Basisklasse in *BASE_CLASS an.* Verwenden Sie für `CObArray` Arrays entweder oder `CPtrArray`. Verwenden Sie für `CObList` `CPtrList`Listen entweder oder .

Wenn Sie eine Auflistung auf der `CObList`Grundlage von z. B. deklarieren, erbt die neue Klasse nicht nur die Member ihrer Basisklasse, sondern deklariert auch eine Reihe zusätzlicher typsicherer Memberfunktionen und Operatoren, die durch das Einkapseln von Aufrufen an die Basisklassenmember zur Typsicherheit beitragen. Diese Kapselungen verwalten alle erforderlichen Typkonvertierungen. Beispiel:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Im ersten Beispiel wird ein typisiertes Zeigerarray `myArray`, abgeleitet von `CObArray`deklariert. Das Array speichert und gibt `CPerson` Zeiger `CPerson` auf Objekte zurück `CObject`(wobei es sich um eine von ) abgeleitete Klasse handelt. Sie können `CObArray` jede Memberfunktion aufrufen, oder Sie `GetAt` können `ElementAt` die neue Typsicherheit und Funktionen aufrufen oder den typsicheren **[ ]** Operator verwenden.

Im zweiten Beispiel wird eine typisierte `myList`Zeigerliste `CPtrList`, abgeleitet von deklariert. In der Liste werden Zeiger `MY_STRUCT` auf Objekte gespeichert und zurückgegeben. Eine Klasse, `CPtrList` die auf dem Wert basiert, `CObject`wird zum Speichern von Zeigern auf Objekte verwendet, die nicht von abgeleitet sind. `CTypedPtrList`hat eine Reihe typsicherer `GetHead`Memberfunktionen: `RemoveHead` `RemoveTail`, `GetNext` `GetTail` `GetPrev`, `GetAt`, , , , und .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Typd-Pointer-Map-Nutzung

Die typd-pointer map-Klasse, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), verwendet drei Parameter: *BASE_CLASS*, *KEY*und *VALUE*. Der *Parameter BASE_CLASS* gibt die Klasse an, von `CMapPtrToWord` `CMapPtrToPtr`der `CMapStringToPtr`die neue Klasse ableitung: , , , `CMapWordToPtr`, `CMapStringToOb`usw. *KEY* ist analog *KEY* zu `CMap`KEY in : Es gibt den Typ des Schlüssels an, der für Suchungen verwendet wird. *VALUE* ist analog *VALUE* zu `CMap`VALUE in : Es gibt den Typ des in der Karte gespeicherten Objekts an. Beispiel:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Das erste Beispiel ist `CMapPtrToPtr` eine Karte, die auf einer Karte basiert – sie verwendet `CString` Schlüssel, die Zeigern zugeordnet sind. `MY_STRUCT` Sie können einen gespeicherten Zeiger suchen, `Lookup` indem Sie eine typsichere Memberfunktion aufrufen. Sie können den **Operator [ ]** verwenden, um einen gespeicherten Zeiger nachzuschlagen und ihn hinzuzufügen, wenn er nicht gefunden wurde. Und Sie können die Karte mit der `GetNextAssoc` typsicheren Funktion iterieren. Sie können auch andere Memberfunktionen der Klasse `CMapPtrToPtr`aufrufen.

Das zweite Beispiel ist `CMapStringToOb` eine Karte, die auf einer Zuordnung `CMyObject` basiert – sie verwendet Zeichenfolgenschlüssel, die gespeicherten Zeigern zu Objekten zugeordnet sind. Sie können dieselben typsicheren Member verwenden, die im vorherigen Absatz `CMapStringToOb`beschrieben wurden, oder Sie können Member der Klasse aufrufen.

> [!NOTE]
> Wenn Sie einen **Klassen-** oder **Strukturtyp** für den *PARAMETER VALUE* anstelle eines Zeigers oder Verweises auf den Typ angeben, muss die Klasse oder Struktur über einen Kopierkonstruktor verfügen.

Weitere Informationen finden Sie unter [Erstellen einer typsicheren Sammlung](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Siehe auch

[Sammlungen](../mfc/collections.md)
