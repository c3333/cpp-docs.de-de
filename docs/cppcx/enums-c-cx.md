---
title: Enumerationen (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 54e413e65b3130b9b83e6d1ed56b5ee87b84e0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225760"
---
# <a name="enums-ccx"></a>Enumerationen (C++/CX)

C++/CX unterstützt das- `public enum class` Schlüsselwort, das Analog zu einem Standard-C++ ist `scoped  enum` . Wenn Sie einen Enumerator verwenden, der durch das Schlüsselwort `public enum class` deklariert ist, müssen Sie den Enumerationsbezeichner dazu benutzen, den Umfang jedes Enumeratorwerts festzulegen.

### <a name="remarks"></a>Bemerkungen

Ein, `public enum class` der keinen Zugriffsspezifizierer hat, z **`public`** . b., wird [scoped enum](../cpp/enumerations-cpp.md)als standardmäßige Enumeration mit C++-Bereichs Einschränkung behandelt.

Eine- `public enum class` oder- `public enum struct` Deklaration kann einen zugrunde liegenden Typ eines beliebigen ganzzahligen Typs aufweisen, obwohl der Windows-Runtime selbst erfordert, dass der Typ Int32 oder UInt32 für eine Flags-Enum ist. Die folgende Syntax beschreibt die Teile einer `public enum class` oder `public enum struct`.

Dieses Beispiel zeigt, wie eine öffentliche Enumerationsklasse definiert wird:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

In diesem folgenden Beispiel wird zeigt, wie sie verwendet wird:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Beispiele

In den folgenden Beispielen wird veranschaulicht, wie eine Enumeration deklariert wird.

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

Im nächsten Beispiel wird gezeigt, wie Sie eine Enumeration in numerische Werte umwandeln und Vergleiche durchführen. Beachten Sie, dass die Verwendung des Enumerators `One` vom Enumerationsbezeichner `Enum1` beschränkt wird, und der Enumerator `First` wird durch `Enum2`beschränkt.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Siehe auch

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
