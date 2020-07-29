---
title: Prozess
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: f684c9c2ddfcb0aa166e1240c5f928ee52218f45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227204"
---
# `process`

Gibt an, dass der verwaltete Anwendungsprozess eine einzelne Kopie einer bestimmten globalen Variablen, einer statischen Membervariablen oder einer statischen lokalen Variablen haben soll, die von allen Anwendungsdomänen im Prozess verwendet wird. Dies war in erster Linie für die Verwendung beim Kompilieren mit vorgesehen **`/clr:pure`** , das in Visual Studio 2015 veraltet ist und in Visual Studio 2017 nicht unterstützt wird. Beim Kompilieren mit **`/clr`** werden globale und statische Variablen standardmäßig pro Prozess verwendet und müssen nicht verwendet werden **`__declspec(process)`** .

Nur eine globale Variable, eine statische Element Variable oder eine statische lokale Variable des systemeigenen Typs kann mit markiert werden **`__declspec(process)`** .

**`process`** ist nur gültig, wenn mit kompiliert wird [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) .

Wenn Sie möchten, dass jede Anwendungsdomäne eine eigene Kopie einer globalen Variablen hat, verwenden Sie [AppDomain](../cpp/appdomain.md).

Weitere Informationen finden Sie unter [Anwendungs Domänen und Visual C++](../dotnet/application-domains-and-visual-cpp.md) .

## <a name="see-also"></a>Siehe auch

[`__declspec`](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
