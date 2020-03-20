---
title: Serialisierung (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545162"
---
# <a name="serialization-ccli"></a>Serialisierung (C++/CLI)

Die Serialisierung (der Vorgang zum Speichern des Zustands eines Objekts oder eines Members in einem permanenten Medium) der verwalteten Klassen (einschließlich einzelner Felder oder Eigenschaften) wird von den Klassen <xref:System.SerializableAttribute> und <xref:System.NonSerializedAttribute> unterstützt.

## <a name="remarks"></a>Hinweise

Wenden Sie das benutzerdefinierte **SerializableAttribute** -Attribut auf eine verwaltete Klasse an, um die gesamte Klasse zu serialisieren, oder wenden Sie Sie nur auf bestimmte Felder oder Eigenschaften an, um Teile der verwalteten Klasse zu serialisieren. Verwenden Sie das benutzerdefinierte **NonSerializedAttribute** -Attribut, um die Felder oder Eigenschaften einer verwalteten Klasse von der Serialisierung auszuschließen.

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Im folgenden Beispiel wird die-Klasse `MyClass` (und die-Eigenschaft `m_nCount`) als serialisierbar markiert. Die `m_nData`-Eigenschaft wird jedoch nicht so serialisiert, wie durch das **nicht serialisierte** benutzerdefinierte Attribut angegeben:

### <a name="code"></a>Code

```cpp
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>Comments

Beachten Sie, dass auf beide Attribute mit Ihrem "Kurznamen" verwiesen werden kann (**serialisierbar** und **nicht serialisiert**). Dies wird in Anwenden von [Attributen](/dotnet/standard/attributes/applying-attributes)ausführlicher erläutert.

## <a name="see-also"></a>Siehe auch

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
