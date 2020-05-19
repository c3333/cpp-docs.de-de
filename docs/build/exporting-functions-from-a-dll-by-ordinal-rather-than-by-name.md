---
title: Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328575"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen

Die einfachste Methode zum Exportieren von Funktionen aus der DLL besteht darin, diese anhand des Namens zu exportieren. Dies geschieht, wenn Sie z B. **__declspec(dllexport)** verwenden. Alternativ können Sie Funktionen auch nach der Ordinalzahl exportieren. Bei dieser Vorgehensweise müssen Sie eine DEF-Datei anstelle von **__declspec(dllexport)** verwenden. Fügen Sie die Ordinalzahl an den Funktionsnamen in der DEF-Datei an, um den Ordinalwert einer Funktion anzugeben. Weitere Informationen zum Angeben von Ordinalzahlen finden Sie unter [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Wenn Sie die Dateigröße Ihrer DLL optimieren möchten, verwenden Sie für jede exportierte Funktion das **NONAME**-Attribut. Mit dem **NONAME**-Attribut werden die Ordinalzahlen anstelle der Funktionsnamen in der Exporttabelle der DLL gespeichert. Dies kann eine beträchtliche Einsparung darstellen, wenn Sie viele Funktionen exportieren.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Verwenden einer DEF-Datei, um nach Ordinalzahl zu exportieren](exporting-from-a-dll-using-def-files.md)

- [Verwenden von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
