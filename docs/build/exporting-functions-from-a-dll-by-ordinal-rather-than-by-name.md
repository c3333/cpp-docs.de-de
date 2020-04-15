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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328575"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen

Die einfachste Möglichkeit, Funktionen aus Ihrer DLL zu exportieren, besteht darin, sie nach Namen zu exportieren. Dies geschieht, wenn Sie beispielsweise **__declspec(dllexport)** verwenden. Sie können jedoch Funktionen nach Ordnung exportieren. Bei dieser Technik müssen Sie eine .def-Datei anstelle von **__declspec(dllexport)** verwenden. Um den Ordinalwert einer Funktion anzugeben, fügen Sie ihre Ordinalanalantum an den Funktionsnamen in der .def-Datei an. Informationen zum Angeben von Ordinals finden Sie unter [Exportieren aus einer DLL mit .def-Dateien](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Wenn Sie die Dateigröße Ihrer DLL optimieren möchten, verwenden Sie das **NONAME-Attribut** für jede exportierte Funktion. Mit dem **NONAME-Attribut** werden die Ordinals in der Exporttabelle der DLL und nicht in den Funktionsnamen gespeichert. Dies kann eine erhebliche Ersparnis sein, wenn Sie viele Funktionen exportieren.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Verwenden Sie eine .def-Datei, damit ich mit Ordinal exportieren kann](exporting-from-a-dll-using-def-files.md)

- [Verwenden von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
