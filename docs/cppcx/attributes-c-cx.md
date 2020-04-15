---
title: Attribute (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371872"
---
# <a name="attributes-ccx"></a>Attribute (C++/CX)

Ein Attribut ist eine spezielle Art von ref-Klasse, die windows-Runtime-Typen und -Methoden in eckigen Klammern vorangestellt werden kann, um bestimmte Verhaltensweisen bei der Metadatenerstellung anzugeben. Mehrere vordefinierte Attribute, z. B. [Windows::Foundation::Metadata::WebHostHidden,](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)werden häufig im C++/CX-Code verwendet. Dieses Beispiel zeigt, wie das Attribut auf eine Klasse angewendet wird:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Benutzerdefinierte Attribute

Sie können auch benutzerdefinierte Attribute definieren. Benutzerdefinierte Attribute müssen diesen Windows-Runtime-Regeln entsprechen:

- Benutzerdefinierte Attribute können nur öffentliche Felder enthalten.

- Benutzerdefinierte Attributfelder können initialisiert werden, wenn das Attribut auf eine Klasse angewendet wird.

- Ein Feld kann einer dieser Typen sein:

  - int32 (int)

  - uint32 (int ohne Vorzeichen)

  - bool

  - Platform::String^

  - Windows::Foundation::HResult

  - Platform::Type^

  - öffentliche Enumerationsklasse (enthält benutzerdefinierte Enumerationen)

Das nächste Beispiel zeigt, wie ein benutzerdefiniertes Attribut definiert und anschließend zur Verwendung initialisiert wird.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Siehe auch

[Typsystem (C++-CX)](../cppcx/type-system-c-cx.md)<br/>
[C++-/CX-Programmiersprachenreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
