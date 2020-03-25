---
title: Boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: df0e220c4f744e78aa5bedce4f956b726f524ff4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208831"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

Boxing ist der Prozess der Konvertierung eines Werttyps in den Typ `object` oder eines beliebigen Schnittstellen Typs, der durch den Werttyp implementiert wird. Wenn die Common Language Runtime (CLR) einen Werttyp einbindet, wird der Wert in einem `System.Object` umschlossen und im verwalteten Heap gespeichert. Durch Unboxing wird der Werttyp aus dem Objekt extrahiert. Boxing ist implizit, Unboxing ist explizit.

## <a name="related-articles"></a>Verwandte Artikel

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Vorgehensweise: Explizites Anfordern von Boxing](../dotnet/how-to-explicitly-request-boxing.md)|Beschreibt das explizite anfordern von Boxing für eine Variable.|
|[Vorgehensweise: Verwenden von gcnew zum Erstellen von Werttypen und für implizites Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Zeigt, wie `gcnew` verwendet wird, um einen geachtelten Werttyp zu erstellen, der auf dem verwalteten Heap mit Garbage Collection abgelegt werden kann.|
|[Vorgehensweise: Unboxing](../dotnet/how-to-unbox.md)|Zeigt, wie Sie einen Wert aus dem Feld ein-und ändern können.|
|[Standardumwandlungen und implizites Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Zeigt, dass vom Compiler eine Standard Konvertierung für eine Konvertierung ausgewählt wird, die Boxing erfordert.|
|[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Der Artikel der obersten Ebene für die .NET-Programmierung in C++ der visuellen Dokumentation.|
