---
title: Boxing (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 59c7f8ec56a912ed993316fba093b87bd85e16b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233534"
---
# <a name="boxing-ccx"></a>Boxing (C++/CX)

Beim *Boxing* wird eine Werttyp Variable wie [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime)– oder ein grundlegender Skalartyp wie **`int`** – in einer Verweis Klasse umwickelt, wenn die Variable an eine Methode, die [Platform:: Object ^](../cppcx/platform-object-class.md) als Eingabetyp annimmt, übermittelt wird.

## <a name="passing-a-value-type-to-an-object-parameter"></a>Übergeben eines Werttyps an einen Object^-Parameter

Obwohl Sie für eine Variable nicht explizit Boxing anwenden müssen, um sie an einen Methodenparameter des Typs [Platform::Object^](../cppcx/platform-object-class.md)zu übergeben, müssen Sie eine Umwandlung zum ursprünglichen Typ explizit vornehmen, wenn Sie Werte abrufen, die zuvor geschachtelt wurden.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Verwenden von Platform:: iBox \<T> zur Unterstützung von Werte zulässt-Werttypen

C# und Visual Basic unterstützen das Konzept von Typen, die NULL-Werte zulassen. In C++/CX können Sie den- `Platform::IBox<T>` Typ verwenden, um öffentliche Methoden verfügbar zu machen, die Werte zulässt-Werttyp Parameter unterstützen. Das folgende Beispiel zeigt eine öffentliche C++/CX-Methode, die NULL zurückgibt, wenn ein c#-Aufrufer für eines der Argumente NULL übergibt.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

In einem C#-XAML-Client können Sie diese Methode wie folgt verwenden:

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>Siehe auch

[Typsystem (C++-CX)](../cppcx/type-system-c-cx.md)<br/>
[Umwandlung von Typen (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
