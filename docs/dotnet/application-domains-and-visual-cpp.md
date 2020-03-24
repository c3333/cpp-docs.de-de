---
title: Anwendungsdomänen und Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208799"
---
# <a name="application-domains-and-visual-c"></a>Anwendungsdomänen und Visual C++

Wenn Sie über eine `__clrcall` virtuelle Funktion verfügen, wird die Vtable pro Anwendungsdomäne (AppDomain) verwendet. Wenn Sie ein Objekt in einer AppDomain erstellen, können Sie die virtuelle Funktion nur innerhalb dieser AppDomain abrufen. Im gemischten Modus ( **/CLR**) verfügen Sie über prozessspezifische Vtables, wenn Ihr Typ keine `__clrcall` virtuellen Funktionen aufweist. Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Weitere Informationen finden Sie unter

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Weitere Informationen

- [Gemischte (native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)
