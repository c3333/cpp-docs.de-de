---
title: 'Gewusst wie: Bereitstellen von Arbeitsfunktionen für die call- und transformer-Klassen'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: b629d0e0e11388e212c56b8e1f6bea290368c884
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414346"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Gewusst wie: Bereitstellen von Arbeitsfunktionen für die call- und transformer-Klassen

In diesem Thema werden verschiedene Möglichkeiten zum Bereitstellen von Arbeitsfunktionen für die Klassen " [parallelcurrency:: Aufrufen](../../parallel/concrt/reference/call-class.md) " und " [parallelcurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) " erläutert.

Im ersten Beispiel wird gezeigt, wie ein Lambdaausdruck an ein `call`-Objekt übergeben wird. Im zweiten Beispiel wird gezeigt, wie ein Funktionsobjekt an ein `call`-Objekt übergeben wird. Im dritten Beispiel wird gezeigt, wie eine Klassenmethode an ein `call`-Objekt gebunden wird.

Zu Illustrationszwecken wird in allen Beispielen dieses Themas die `call`-Klasse verwendet. Ein Beispiel, in dem die- `transformer` Klasse verwendet wird, finden Sie unter Gewusst [wie: Verwenden von Transformer in einer Daten Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example-call-class"></a>Beispiel: callclass

Im folgenden Beispiel wird aufgezeigt, wie die `call`-Klasse häufig verwendet wird. In diesem Beispiel wird eine Lambda-Funktion an den `call`-Konstruktor übergeben.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
13 squared is 169.
```

## <a name="example-call-class-with-function-object"></a>Beispiel: "callclass" mit Funktions Objekt

Das folgende Beispiel ähnelt dem vorherigen mit der Ausnahme, dass die `call`-Klasse zusammen mit einem Funktionsobjekt (Funktionselement) verwendet wird.

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example-functions-to-bind-call-object"></a>Beispiel: Funktionen zum Binden des callobject

Das folgende Beispiel ähnelt dem vorherigen, mit der Ausnahme, dass es die Funktionen [Std:: bind1st](../../standard-library/functional-functions.md#bind1st) und [Std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) verwendet, um ein- `call` Objekt an eine Klassenmethode zu binden.

Verwenden Sie diese Technik anstatt des Funktionsaufrufoperators, `call`, wenn Sie ein `transformer`- oder `operator()`-Objekt an eine bestimmte Klassenmethode binden möchten.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Sie können das Ergebnis der `bind1st` Funktion auch einem [Std:: function](../../standard-library/function-class.md) -Objekt zuweisen oder das- **`auto`** Schlüsselwort verwenden, wie im folgenden Beispiel gezeigt.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `call.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc "Call. cpp"**

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Gewusst wie: Verwenden von Transformer in einer Daten Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[callclass](../../parallel/concrt/reference/call-class.md)<br/>
[Transformer-Klasse](../../parallel/concrt/reference/transformer-class.md)
