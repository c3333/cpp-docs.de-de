---
title: Array und WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 1980fbcd1e2fa8cdaa48e00d2e7de9e45ac96a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231025"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array und WriteOnlyArray (C++/CX)

Sie können reguläre Arrays im c-Format oder [`std::array`](../standard-library/array-class-stl.md) in einem C++/CX-Programm frei verwenden (Obwohl [`std::vector`](../standard-library/vector-class.md) dies häufig eine bessere Wahl ist), aber in jeder API, die in den Metadaten veröffentlicht ist, müssen Sie ein Array oder einen Vektor im c-Format in einen-oder-Typ konvertieren, [`Platform::Array`](../cppcx/platform-array-class.md) [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) je nachdem, wie es verwendet wird. Der- [`Platform::Array`](../cppcx/platform-array-class.md) Typ ist weder so effizient noch so leistungsfähig wie. [`std::vector`](../standard-library/vector-class.md) als allgemeine Richtlinie sollten Sie daher die Verwendung im internen Code vermeiden, der viele Vorgänge an den Array Elementen ausführt.

Die folgenden Arraytypen können über die ABI übergeben werden:

1. `const Platform::Array^`

1. `Platform::Array^*`

1. `Platform::WriteOnlyArray`

1. Rückgabewert von`Platform::Array^`

Diese Array Typen werden verwendet, um die drei Typen von Array Mustern zu implementieren, die vom Windows-Runtime definiert werden.

Passarray bezeichnet
Wird verwendet, wenn vom Aufrufer ein Array an eine Methode übergeben wird. Der C++-Eingabe Parametertyp ist **`const`** [`Platform::Array`](../cppcx/platform-array-class.md) \<T> .

FillArray
Wird verwendet, wenn vom Aufrufer ein Array übergeben wird, um die Methode zu füllen. Der C++-Eingabe Parametertyp ist [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) \<T> .

ReceiveArray
Wird verwendet, wenn vom Aufrufer ein Array empfangen wird, das von der Methode zugeordnet wird. In C++/CX können Sie das Array im Rückgabewert als Array^ oder in Form eines out-Parameters als Array^*-Typ zurückgeben.

## <a name="passarray-pattern"></a>PassArray-Muster

Wenn Client Code ein Array an eine C++-Methode übergibt und die Methode Sie nicht ändert, akzeptiert die Methode das Array als `const Array^` . Auf der Ebene der Windows-Runtime Application Binary Interface (ABI) wird dies als *passarray*bezeichnet. Im nächsten Beispiel wird gezeigt, wie ein Array übergeben wird, das in JavaScript zu einer C++-Funktion zugeordnet ist, die aus dem Array liest.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Im folgenden Codeausschnitt wird die C++-Methode veranschaulicht:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>ReceiveArray-Muster

Im *receivearray* -Muster wird ein Array vom Client Code deklariert und an eine Methode weitergeleitet, die den Speicher für das Array zugeordnet und es initialisiert. Der C++-Eingabe Parametertyp ist ein Zeiger auf hat: `Array<T>^*` . Im folgenden Beispiel wird gezeigt, wie ein Arrayobjekt in JavaScript deklariert und an eine C++-Funktion übergeben wird, die Speicher zuordnet, Elemente initialisiert und das Arrayobjekt an JavaScript zurückgibt. Von JavaScript wird das zugeordnete Array als Rückgabewert interpretiert, von der C++-Funktion jedoch als out-Parameter.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Der folgende Codeausschnitt zeigt zwei Möglichkeiten zur Implementierung der C++-Methode:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Füllbereichsarrays

Wenn Sie ein Array im Aufrufer zuordnen und es im Aufgerufenen initialisieren oder ändern möchten, verwenden Sie `WriteOnlyArray`. Im nächsten Beispiel wird gezeigt, wie eine C++-Funktion, die `WriteOnlyArray` verwendet, implementiert und aus JavaScript aufgerufen wird.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Der folgende Codeausschnitt zeigt, wie die C++-Methode implementiert wird:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Arraykonvertierungen

In diesem Beispiel wird gezeigt, wie ein [`Platform::Array`](../cppcx/platform-array-class.md) zum Erstellen anderer Arten von Auflistungen verwendet wird:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

Im nächsten Beispiel wird gezeigt, wie ein [`Platform::Array`](../cppcx/platform-array-class.md) aus einem Array im C-Format erstellt und von einer öffentlichen Methode zurückgegeben wird.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Verzweigte Arrays

Das Windows Runtime-Typsystem unterstützt nicht das Konzept von verzweigten Arrays. Deshalb können Sie ein `IVector<Platform::Array<T>>` nicht als Rückgabewert oder Methodenparameter in einer öffentlichen Methode übergeben. Um ein verzweigtes Array oder eine Sequenz von Sequenzen an die ABI zu übergeben, verwenden Sie `IVector<IVector<T>^>`.

## <a name="use-arrayreference-to-avoid-copying-data"></a>Verwendung von ArrayReference, um das Kopieren von Daten zu vermeiden

In einigen Szenarien, in denen Daten über die ABI an einen übermittelt werden [`Platform::Array`](../cppcx/platform-array-class.md) und Sie diese Daten letztendlich in einem Array im C-Stil verarbeiten möchten, können Sie den zusätzlichen Kopiervorgang mithilfe von [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) vermeiden. Wenn Sie ein [`Platform::ArrayReference`](../cppcx/platform-arrayreference-class.md) als Argument an einen Parameter übergeben, der einen annimmt `Platform::Array` , `ArrayReference` speichert die Daten direkt in ein Array im C-Format, das Sie angeben. Beachten Sie, dass `ArrayReference` nicht über eine Sperre für die Quelldaten verfügt. Wenn diese Daten geändert oder in einem anderen Thread gelöscht werden, bevor der Aufruf abgeschlossen wird, sind die Ergebnisse nicht definiert.

Der folgende Code Ausschnitt zeigt, wie die Ergebnisse eines- [`DataReader`](/uwp/api/windows.storage.streams.datareader) Vorgangs in ein `Platform::Array` (das übliche Muster) kopiert werden und wie ersetzt wird, `ArrayReference` um die Daten direkt in ein Array im C-Format zu kopieren:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Vermeiden, ein Array als Eigenschaft verfügbar zu machen

Im Allgemeinen sollten Sie einen `Platform::Array` -Typ möglichst nicht als Eigenschaft in einer Verweisklasse verfügbar machen, da das gesamte Array zurückgegeben wird, auch wenn der Clientcode nur versucht, auf ein einzelnes Element zuzugreifen. Wenn Sie einen Sequenz Container als Eigenschaft in einer öffentlichen Verweis Klasse verfügbar machen müssen, [`Windows::Foundation::IVector`](/uwp/api/windows.foundation.collections.ivector-1) ist eine bessere Wahl. In privaten oder internen APIs (die nicht in Metadaten veröffentlicht werden) sollten Sie die Verwendung eines C++-Standard Containers wie z. b. in Erwägung gezogen [`std::vector`](../standard-library/vector-class.md) .

## <a name="see-also"></a>Siehe auch

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
