---
title: try-, throw- und catch-Anweisungen (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 4108d24b2c285b9d55d514dffae7b2efda1b3f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227061"
---
# <a name="try-throw-and-catch-statements-c"></a>try-, throw- und catch-Anweisungen (C++)

Um die Ausnahmebehandlung in C++ zu implementieren, verwenden Sie die **`try`** **`throw`** Ausdrücke, und **`catch`** .

Verwenden Sie zunächst einen- **`try`** Block, um eine oder mehrere-Anweisungen einzuschließen, die möglicherweise eine Ausnahme auslösen.

Ein- **`throw`** Ausdruck signalisiert, dass in einem-Block eine Ausnahme Bedingung – oft ein Fehler – aufgetreten ist **`try`** . Sie können ein Objekt eines beliebigen Typs als Operand eines-Ausdrucks verwenden **`throw`** . Normalerweise wird dieses Objekt verwendet, um Informationen über den Fehler zu kommunizieren. In den meisten Fällen wird empfohlen, die [Std:: Exception](../standard-library/exception-class.md) -Klasse oder eine der abgeleiteten Klassen zu verwenden, die in der Standardbibliothek definiert sind. Wenn eine davon nicht passend ist, wird empfohlen, dass Sie Ihre eigene Ausnahmeklasse von `std::exception` ableiten.

Um Ausnahmen zu behandeln, die möglicherweise ausgelöst werden, implementieren Sie einen oder mehrere **`catch`** Blöcke direkt nach einem- **`try`** Block. Jeder- **`catch`** Block gibt den Typ der Ausnahme an, die er verarbeiten kann.

Dieses Beispiel zeigt einen **`try`** -Block und seine Handler. Nehmen Sie an, dass `GetNetworkResource()` Daten über eine Netzwerkverbindung erhält und dass die beiden Ausnahmetypen benutzerdefinierte Klassen sind, die von `std::exception` abgeleitet sind. Beachten Sie, dass die Ausnahmen **`const`** als Verweis in der-Anweisung abgefangen werden **`catch`** . Es wird empfohlen, dass Sie die Ausnahmen nach Wert auslösen und sie durch einen const-Verweis abfangen.

## <a name="example"></a>Beispiel

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>Bemerkungen

Der Code nach der- **`try`** Klausel ist der geschützte Abschnitt des Codes. Der **`throw`** Ausdruck *throws*löst – aus, d. h. löst – eine Ausnahme aus. Der Codeblock nach der- **`catch`** Klausel ist der Ausnahmehandler. Dies ist der Handler, der die Ausnahme *abfängt* , die ausgelöst wird, wenn die Typen in den **`throw`** **`catch`** Ausdrücken und kompatibel sind. Eine Liste der Regeln, die die Typübereinstimmung in- **`catch`** Blöcken steuern, finden Sie unter [wie catch-Blöcke ausgewertet werden](../cpp/how-catch-blocks-are-evaluated-cpp.md). Wenn die **`catch`** Anweisung ein Auslassungs Zeichen (...) anstelle eines Typs angibt, verarbeitet der- **`catch`** Block jeden Ausnahmetyp. Wenn Sie mit der [/EHa](../build/reference/eh-exception-handling-model.md) -Option kompilieren, können diese C-strukturierte Ausnahmen und vom systemgenerierte oder von der Anwendung generierte asynchrone Ausnahmen wie z. b. Speicherschutz, Division durch 0 (null) und Gleit Komma Verletzungen enthalten. Da **`catch`** Blöcke in der Programm Reihenfolge verarbeitet werden, um einen übereinstimmenden Typ zu finden, muss ein Ellipsen Handler der letzte Handler für den zugeordneten- **`try`** Block sein. Verwenden Sie `catch(...)` mit Vorsicht. Lassen Sie nicht zu, dass ein Programm fortgesetzt wird, es sei denn der catch-Block kann die spezifische Ausnahme, die abgefangen wird, behandeln. Normalerweise wird ein `catch(...)`-Block verwendet, um Fehler zu protokollieren und eine spezielle Bereinigung vor dem Beenden der Programmausführung auszuführen.

Ein- **`throw`** Ausdruck, der über keinen Operanden verfügt, löst die derzeit behandelte Ausnahme erneut aus. Wir empfehlen diese Form, wenn die Ausnahme erneut ausgelöst wird, denn dadurch wird die originale polymorphe Typinformation der Ausnahme bewahrt. Ein solcher Ausdruck sollte nur in einem **`catch`** Handler oder einer Funktion verwendet werden, die von einem Handler aufgerufen wird **`catch`** . Das erneut ausgelöste Ausnahmeobjekt ist das ursprüngliche Ausnahmeobjekt (keine Kopie).

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>Siehe auch

[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Nicht behandelte C++-Ausnahmen](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
