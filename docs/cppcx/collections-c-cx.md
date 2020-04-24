---
title: Auflistungen (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032316"
---
# <a name="collections-ccx"></a>Auflistungen (C++/CX)

In einem C++/CX-Programm können Sie STL-Container (Standard Template Library) oder einen anderen benutzerdefinierten Sammlungstyp kostenlos verwenden. Wenn Sie jedoch Sammlungen über die Windows-Runtime-Anwendungsbinärschnittstelle (ABI) hin und her übergeben, z. B. an ein XAML-Steuerelement oder an einen JavaScript-Client, müssen Sie Windows-Runtime-Auflistungstypen verwenden.

Die Windows-Runtime definiert die Schnittstellen für Auflistungen und verwandte Typen, und C++/CX stellt die konkreten C++-Implementierungen in der Collection.h-Headerdatei bereit. Diese Abbildung zeigt die Beziehungen zwischen den Auflistungstypen:

![C&#43;&#43;&#47;CX-Vererbungsstruktur für Auflistungstypen](../cppcx/media/cppcxcollectionsinheritancetree.png "C&#43;&#43;&#47;CX-Vererbungsstruktur für Auflistungstypen")

- Die [Platform::Collections::Vector-Klasse](../cppcx/platform-collections-vector-class.md) ähnelt der [std::vector-Klasse](../standard-library/vector-class.md).

- Die [Platform::Collections::Map-Klasse](../cppcx/platform-collections-map-class.md) ähnelt der [std::map-Klasse](../standard-library/map-class.md).

- Die[Platform::Collections::VectorView-Klasse](../cppcx/platform-collections-vectorview-class.md) und[Platform::Collections::MapView-Klasse](../cppcx/platform-collections-mapview-class.md) sind schreibgeschützte Versionen von `Vector` und `Map`.

- Iteratoren werden im [Platform::Collections-Namespace](../cppcx/platform-collections-namespace.md)definiert. Diese Iteratoren erfüllen die Anforderungen für STL-Iteratoren und ermöglichen die Verwendung von [std::find](../standard-library/algorithm-functions.md#find),  [std::count_if](../standard-library/algorithm-functions.md#count_if)und anderen STL-Algorithmen für einen beliebigen [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) -Schnittstellentyp oder einen konkreten [Platform::Collections](../cppcx/platform-collections-namespace.md) -Typ. Dies bedeutet z. B., dass Sie eine Auflistung in einer Windows-Runtime-Komponente, die in C- erstellt wurde, iterieren und einen STL-Algorithmus darauf anwenden können.

   > [!IMPORTANT]
   > Die Proxyiteratoren `VectorIterator` und `VectorViewIterator` verwenden die Proxyobjekte `VectoryProxy<T>` und `ArrowProxy<T>` , um eine Verwendung mit STL-Containern zu ermöglichen. Weitere Informationen finden Sie unter "VectorProxy-Elemente" weiter unten in diesem Artikel.

- Die C++/CX-Auflistungstypen unterstützen die gleichen Threadsicherheitsgarantien, die STL-Container unterstützen.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) und [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) definieren Ereignisse, die ausgelöst werden, wenn sich die Auflistung auf unterschiedliche Weise ändert. Durch Implementierung dieser Schnittstellen unterstützen  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) und [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) eine Datenbindung mit XAML-Auflistungen. Wenn Sie beispielsweise einen `Vector` mit einer Datenbindung zu einem `Grid`haben und ein Element einer Auflistung hinzufügen, wird die Änderung in die Benutzeroberfläche des Rasters übernommen.

## <a name="vector-usage"></a>Verwendung von Vektoren

Wenn Ihre Klasse einen Sequenzcontainer an eine andere Windows-Runtime-Komponente übergeben muss, verwenden Sie [Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) als Parameter oder Rückgabetyp und [Platform::Collections::Vector\<T>](../cppcx/platform-collections-vector-class.md) als konkrete Implementierung. Wenn Sie versuchen, einen `Vector` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können das Problem beheben, indem Sie den `Vector` in einen `IVector`ändern.

> [!IMPORTANT]
> Wenn Sie eine Sequenz im eigenen Programm übergeben, verwenden Sie entweder `Vector` oder `std::vector` , da sie effizienter als `IVector`sind. Verwenden Sie `IVector` nur, wenn Sie den Container über die ABI übergeben.
>
> Das Windows-Runtime-Typsystem unterstützt nicht das Konzept von gezackten Arrays, und\<daher können Sie einen IVector<Platform::Array T>> als Rückgabewert oder Methodenparameter nicht übergeben. Um ein verzweigtes Array oder eine Sequenz von Sequenzen an die ABI zu übergeben, verwenden Sie `IVector<IVector<T>^>`.

`Vector<T>` stellt die Methoden bereit, die zum Hinzufügen, Entfernen und das Zugreifen auf Elemente in der Auflistung erforderlich sind, und kann implizit zu `IVector<T>`konvertiert werden. Sie können STL-Algorithmen auch bei Instanzen von `Vector<T>`verwenden. Das folgende Beispiel veranschaulicht die grundlegende Verwendung. Die [begin function](../cppcx/begin-function.md) und [end function](../cppcx/end-function.md) hier stammen vom Namespace `Platform::Collections` und nicht vom Namespace `std` .

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Wenn Sie über vorhandenen `std::vector` Code verfügen, der diesen verwendet und in einer Windows-Runtime-Komponente wiederverwenden möchte, verwenden Sie einfach einen der `Vector` Konstruktoren, der einen `std::vector` oder ein Paar Iteratoren benötigt, um an dem Punkt zu `Vector` erstellen, an dem Sie die Auflistung über die ABI übergeben. Im folgenden Beispiel wird gezeigt, wie der `Vector` -Bewegungskonstruktor zur effizienten Initialisierung von `std::vector`verwendet wird. Nach dem Verschiebungsvorgang ist die ursprüngliche `vec` -Variable nicht mehr gültig.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Wenn Sie einen Vektor von Zeichenfolgen haben, die Sie an einem zukünftigen Punkt über die ABI übergeben müssen, müssen Sie entscheiden, ob die Zeichenfolgen zuerst als `std::wstring` -Typen oder als `Platform::String^` -Typen erstellt werden sollen. Wenn die Zeichenfolgen einen hohen Verarbeitungsaufwand erfordern, verwenden Sie `wstring`. Erstellen Sie andernfalls die Zeichenfolgen als `Platform::String^` -Typen, und vermeiden Sie den Aufwand einer späteren Konvertierung. Außerdem müssen Sie festlegen, ob diese Zeichenfolgen intern in einem `std:vector` oder in einem `Platform::Collections::Vector` abgelegt werden sollen. Im Allgemeinen sollten Sie `std::vector` verwenden und nur dann einen `Platform::Vector` erstellen, wenn Sie den Container über die ABI übergeben.

## <a name="value-types-in-vector"></a>Werttypen im Vektor

Jedes in [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) gespeicherte Element muss einen Übereinstimmungsvergleich unterstützen, und zwar entweder implizit oder mithilfe eines benutzerdefinierten [std::equal_to](../standard-library/equal-to-struct.md) -Vergleichsoperators, den Sie bereitstellen. Alle Verweistypen und alle skalaren Typen unterstützen implizit Übereinstimmungsvergleiche. Für nicht skalare Werttypen wie [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)oder für benutzerdefinierte Vergleiche – z. B. `objA->UniqueID == objB->UniqueID`– müssen Sie ein benutzerdefiniertes Funktionsobjekt bereitstellen.

## <a name="vectorproxy-elements"></a>VectorProxy-Elemente

[Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) und [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) ermöglichen `range for` die Verwendung von Schleifen und Algorithmen wie [std::sort](../standard-library/algorithm-functions.md#sort) mit einem [IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) Container. `IVector` -Elemente können jedoch nicht über C++-Zeigerdereferenzierungen aufgerufen werden; auf sie kann nur durch die [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) - und [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) -Methode zugegriffen werden. Daher verwenden diese Iteratoren `Platform::Details::VectorProxy<T>` `Platform::Details::ArrowProxy<T>` die Proxyklassen und ermöglichen __\*__ __->__ den Zugriff auf die einzelnen Elemente über , und __ \[]__ Operatoren, wie von der Standardbibliothek gefordert. Streng genommen ist bei einer `IVector<Person^> vec`der Typ von `*begin(vec)``VectorProxy<Person^>`. Allerdings ist das Proxyobjekt fast immer für Ihren Code transparent. Diese Proxyobjekte werden nicht dokumentiert, da sie nur für die interne Verwendung durch Iteratoren bestimmt sind. Es ist jedoch hilfreich zu wissen, wie der Mechanismus funktioniert.

Wenn Sie eine `range for` -Schleife über `IVector` -Container verwenden, verwenden Sie `auto&&` , damit die Iteratorvariable korrekt an die `VectorProxy` -Elemente gebunden werden kann. Wenn Sie `auto` oder `auto&`verwenden, wird die Compilerwarnung C4239 ausgelöst und `VectoryProxy` wird im Text der Warnung erwähnt.

Die folgende Abbildung zeigt ein Beispiel für eine `range for` -Schleife über eine `IVector<Person^>`. Beachten Sie, dass die Ausführung am Haltepunkt in Zeile 64 beendet wird. Im Fenster **Schnellüberwachung** wird angezeigt, dass die Iteratorvariable `p` tatsächlich eine `VectorProxy<Person^>` ist, die die Membervariablen `m_v` und `m_i` aufweist. Wenn Sie jedoch `GetType` für diese Variable aufrufen, gibt sie den identischen Typ zur Instanz `Person``p2`zurück. Die Schlussfolgerung daraus: Obwohl möglicherweise `VectorProxy` und `ArrowProxy` in der **Schnellüberwachung**, in bestimmten Compilerfehlern des Debuggers oder an anderen Stellen angezeigt werden, müssen Sie sie in der Regel nicht explizit codieren.

![VectorProxy im Bereich&#45;basiert auf Schleife](../cppcx/media/vectorproxy-1.png "VectorProxy im Bereich&#45;basiert auf Schleife")

Ein Szenario, in dem Sie Code um das Proxyobjekt herum schreiben müssen, ist, wenn Sie eine `dynamic_cast` für die Elemente durchführen müssen, zum Beispiel, wenn Sie nach XAML-Objekte eines bestimmten Typs in einer `UIElement` -Elementauflistung suchen. In diesem Fall müssen Sie zuerst das Element in [Platform::Object](../cppcx/platform-object-class.md)^ umwandeln und dann die dynamische Umwandlung ausführen:

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>Verwendung von Zuordnungen

Dieses Beispiel zeigt, wie Elemente eingefügt und in einer [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)gesucht werden und wie die `Map` anschließend als schreibgeschützter [Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) -Typ zurückgegeben wird.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Im Allgemeinen sollten Sie für die interne Zuordnungsfunktionalität aus Leistungsgründen vorzugsweise den Typ `std::map` verwenden. Wenn Sie den Container über die ABI übergeben müssen, erstellen Sie eine [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) von der [std::map](../standard-library/map-class.md) , und geben Sie den `Map` als eine [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)zurück. Wenn Sie versuchen, einen `Map` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können das Problem beheben, indem Sie den `Map` in einen `IMap`ändern. In einigen Fällen, beispielsweise wenn Sie nur wenige Suchen oder Einfügungen ausführen und die Auflistung häufig über die ABI übergeben, ist es möglicherweise weniger Aufwand, gleich `Platform::Collections::Map` zu verwenden und die Konvertierung von `std::map`zu vermeiden. Vermeiden Sie in jedem Fall Such- und Einfügevorgänge bei einer `IMap` , da diese der am wenigsten leistungsfähige der drei Typen ist. Konvertieren Sie in `IMap` nur dann, wenn Sie den Container über die ABI übergeben.

## <a name="value-types-in-map"></a>Werttypen in der Zuordnung

Elemente in [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) werden sortiert. Jedes in `Map` zu speichernde Element muss den Kleiner-als-Vergleich in strenger, schwacher Reihenfolg unterstützen, und zwar entweder implizit oder mithilfe eines benutzerdefinierten [stl::less](../standard-library/less-struct.md) -Vergleichsoperators, den Sie bereitstellen. Skalare Typen unterstützen den Vergleich implizit. Für nicht skalare Werttypen wie `Windows::Foundation::DateTime`oder für benutzerdefinierte Vergleiche – z. B. `objA->UniqueID < objB->UniqueID`– müssen Sie einen benutzerdefinierten Vergleichsoperator bereitstellen.

## <a name="collection-types"></a>Auflistungstypen

Auflistungen sind in vier Kategorien unterteilt: änderbare Versionen und schreibgeschützte Versionen von Sequenzauflistungen und assoziativen Auflistungen. Darüber hinaus erweitert C++/CX Sammlungen durch die Bereitstellung von drei Iteratorklassen, die den Zugriff auf Sammlungen vereinfachen.

Elemente einer änderbaren Auflistung können geändert werden, aber Elemente einer schreibgeschützten Auflistung, die als *Ansicht*bekannt ist, können nur gelesen werden. Auf Elemente einer [Plattform::Collections::Vector](../cppcx/platform-collections-vector-class.md) oder[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) kann mithilfe eines Iterators oder [des Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) und eines Indexes der Auflistung zugegriffen werden. Auf Elemente einer assoziativen Auflistung kann mithilfe der [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) und eines Schlüssels der Auflistung zugegriffen werden.

[Platform::Collections::Map-Klasse](../cppcx/platform-collections-map-class.md)<br/>
Eine änderbare, assoziative Auflistung. Zuordnungselemente sind Schlüssel-Wert-Paare. Sowohl das Suchen nach einem Schlüssel, um den zugeordneten Wert abzurufen, als auch das Durchlaufen aller Schlüssel-Wert-Paare werden unterstützt.

`Map` und `MapView` sind als Vorlagen für `<K, V, C = std::less<K>>`vorhanden. Daher können Sie den Vergleichsoperator anpassen.  Darüber hinaus sind `Vector` und `VectorView` auf `<T, E = std::equal_to<T>>` vorlagenbasiert, damit Sie das Verhalten von `IndexOf()`anpassen können. Dies ist vor allem für `Vector` und `VectorView` von Wertstrukturen wichtig. Um beispielsweise einen Vector\<Windows::Foundation::DateTime> zu erstellen, müssen Sie einen benutzerdefinierten Vergleich bereitstellen, da DateTime den Operator ==nicht überlastet.

[Platform::Collections::MapView-Klasse](../cppcx/platform-collections-mapview-class.md)<br/>
Eine schreibgeschützte Version von `Map`.

[Platform::Collections::Vector-Klasse](../cppcx/platform-collections-vector-class.md)<br/>
Eine änderbare Sequenzauflistung. `Vector<T>` unterstützt stetige und amortisierte stetige [Append](../cppcx/platform-collections-vector-class.md#append) -Direktzugriffsvorgänge.

[Platform::Collections::VectorView-Klasse](../cppcx/platform-collections-vectorview-class.md)<br/>
Eine schreibgeschützte Version von `Vector`.

[Platform::Collections::InputIterator-Klasse](../cppcx/platform-collections-inputiterator-class.md)<br/>
Ein STL-Iterator, der die Anforderungen eines STL-Eingabeiterators erfüllt.

[Platform::Collections::VectorIterator-Klasse](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Ein STL-Iterator, der die Anforderungen eines änderbaren STL-Iterators mit Direktzugriff erfüllt.

[Platform::Collections::VectorViewIterator-Klasse](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Ein STL-Iterator, der die Anforderungen eines STL-  `const` -Iterators mit Direktzugriff erfüllt.

### <a name="begin-and-end-functions"></a>begin() und end() -Funktionen

Um die Verwendung der STL `Vector` `VectorView`zum `Map` `MapView`Verarbeiten von `Windows::Foundation::Collections` , , , und beliebigen Objekten zu vereinfachen, unterstützt C++/CX Überladungen der Nichtmemberfunktionen [begin Function](../cppcx/begin-function.md) und [end Function.](../cppcx/end-function.md)

Die folgende Tabelle zeigt die verfügbaren Iteratoren und Funktionen auf.

|Iterators|Functions|
|---------------|---------------|
|[Plattform::Sammlungen::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Intern speichert [Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1) und int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[Plattform::Sammlungen::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Intern speichert [IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)und int.)|[Anfang](../cppcx/begin-function.md)/ [(IVectorView\<T>) ](/uwp/api/windows.foundation.collections.ivectorview-1)[end](../cppcx/end-function.md)|
|[Plattform::Sammlungen::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Intern speichert [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)und T.)|[Anfang](../cppcx/begin-function.md)/ [(](../cppcx/end-function.md) [\<IIterable T>](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Plattform::Collections::InputIterator<IKeyValuePair\<K, V>>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Intern speichert [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)und T.)|[Anfang (](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) [IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[Plattform::Collections::InputIterator<IKeyValuePair\<K, V>>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Intern speichert [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)und T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Änderungsereignisse bei Auflistungen

`Vector` und `Map` unterstützen Datenbindung in XAML-Auflistungen durch Implementieren von Ereignissen, die auftreten, wenn ein Auflistungsobjekt geändert oder zurückgesetzt wird oder wenn ein Element in einer Auflistung eingefügt, aus dieser entfernt oder geändert wird. Sie können zwar eigene Typen schreiben, die Datenbindung unterstützen, können jedoch nicht von `Map` oder von `Vector` erben, da diese Typen versiegelt sind.

Die Delegaten [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) und [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) geben die Signaturen für Ereignishandler für Auflistungsänderungsereignisse an. Die öffentlichen Enumerationsklasse [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) und die Verweisklassen `Platform::Collection::Details::MapChangedEventArgs` und `Platform::Collections::Details::VectorChangedEventArgs` speichern die Ereignisargumente, um herauszufinden, wodurch das Ereignis ausgelöst wurde. Die `*EventArgs` Typen werden `Details` im Namespace definiert, da Sie sie bei der `Map` `Vector`Verwendung oder nicht explizit erstellen oder verwenden müssen.

## <a name="see-also"></a>Weitere Informationen

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++-/CX-Programmiersprachenreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
