---
title: Boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 03304b902ced2c1e9776eeec90142380b984ee45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230908"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

Beim Boxing handelt es sich um den Prozess der Konvertierung eines Werttyps in den Typ `object` oder in einen beliebigen Schnittstellentyp, der vom Werttyp implementiert wird. Wenn die Common Language Runtime (CLR) einen Werttyp eingibt, wird der Wert in einem umschlossen `System.Object` und im verwalteten Heap gespeichert. Durch Unboxing wird der Werttyp aus dem Objekt extrahiert. Boxing ist implizit, Unboxing ist explizit.

## <a name="related-articles"></a>Verwandte Artikel

|Titel|Beschreibung|
|-----------|-----------------|
|[Gewusst wie: Explizites anfordern von Boxing](../dotnet/how-to-explicitly-request-boxing.md)|Beschreibt das explizite anfordern von Boxing für eine Variable.|
|[Gewusst wie: Verwenden von gcnew zum Erstellen von Werttypen und Verwenden von implizitem Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Zeigt, wie verwendet **`gcnew`** wird, um einen geachtelten Werttyp zu erstellen, der auf dem verwalteten Heap mit Garbage Collection abgelegt werden kann.|
|[Vorgehensweise: Unboxing](../dotnet/how-to-unbox.md)|Zeigt, wie Sie einen Wert aus dem Feld ein-und ändern können.|
|[Standard Konvertierungen und implizites Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Zeigt, dass vom Compiler eine Standard Konvertierung für eine Konvertierung ausgewählt wird, die Boxing erfordert.|
|[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Der Artikel der obersten Ebene für die .NET-Programmierung in der Visual C++-Dokumentation.|
