---
title: Änderungen an der Hilfsfunktion für das verzögerte Laden von DLLs seit Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320614"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Änderungen an der Hilfsfunktion für das verzögerte Laden von DLLs seit Visual C++ 6.0

Wenn Sie mehrere Versionen von Visual C++ auf Ihrem Computer haben oder wenn Sie Ihre eigene Hilfsfunktion definiert haben, sind Änderungen an der DLL-Hilfsfunktion für verzögertes Laden möglicherweise betroffen. Beispiel:

- **__delayLoadHelper** ist jetzt **__delayLoadHelper2**

- **__pfnDliNotifyHook** ist jetzt **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** ist jetzt **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** ist jetzt **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Wenn Sie die Standardhilfsfunktion verwenden, wirken sich diese Änderungen nicht auf Sie aus. Es gibt keine Änderungen in Bezug darauf, wie Sie den Linker aufrufen.

## <a name="multiple-versions-of-visual-c"></a>Mehrere Versionen von Visual C++

Wenn Sie mehrere Versionen von Visual C++ auf Ihrem Computer haben, stellen Sie sicher, dass der Linker mit delayimp.lib übereinstimmt. Wenn eine Nichtübereinstimmung vorliegt, erhalten Sie entweder `___delayLoadHelper2@8` `___delayLoadHelper@8` eine Linkerfehlermeldung oder als nicht aufgelöstes externes Symbol. Ersteres impliziert einen neuen Linker mit einem alten delayimp.lib, und letztere impliziert einen alten Linker mit einem neuen delayimp.lib.

Wenn Sie einen nicht behobenen Linkerfehler erhalten, führen Sie [dumpbin /linkermember](linkermember.md):1 auf der delayimp.lib aus, von der Sie erwarten, dass sie die Hilfsfunktion enthält, um zu sehen, welche Hilfsfunktion stattdessen definiert ist. Die Hilfsfunktion kann auch in einer Objektdatei definiert werden. dumpbin [/symbols](symbols.md) ausführen `delayLoadHelper(2)`und nach suchen.

Wenn Sie wissen, dass Sie über den Visual C++ 6.0-Linker verfügen, dann:

- Führen Sie dumpbin für die .lib- oder .obj-Datei des Delay load Helpers aus, um zu bestimmen, ob sie **__delayLoadHelper2**definiert. Ist dies nicht der Fall, schlägt die Verknüpfung fehl.

- Definieren Sie **__delayLoadHelper** in der Datei .lib oder .obj des Delay Load Helpers.

## <a name="user-defined-helper-function"></a>Benutzerdefinierte Hilfsfunktion

Wenn Sie Ihre eigene Hilfsfunktion definiert haben und die aktuelle Version von Visual C++ verwenden, gehen Sie wie folgt vor:

- Benennen Sie die Hilfsfunktion in **__delayLoadHelper2**um.

- Da die Zeiger im Verzögerungsdeskriptor (ImgDelayDescr in delayimp.h) von absoluten Adressen (VAs) in relative Adressen (RVAs) geändert wurden, um wie erwartet in 32- und 64-Bit-Programmen zu funktionieren, müssen Sie diese zurück in Zeiger konvertieren. Eine neue Funktion wurde eingeführt: PFromRva, gefunden in delayhlp.cpp. Sie können diese Funktion für jedes Feld im Deskriptor verwenden, um sie in 32- oder 64-Bit-Zeiger zurück zu konvertieren. Die standardmäßige Delay Load Helper-Funktion ist weiterhin eine gute Vorlage, die als Beispiel verwendet werden kann.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Laden aller Importe für eine verzögerte DLL

Der Linker kann alle Importe aus einer DLL laden, die Sie als verzögert geladen angegeben haben. Weitere Informationen finden Sie unter [Laden aller Importe für eine verzögerte DLL.](loading-all-imports-for-a-delay-loaded-dll.md)

## <a name="see-also"></a>Siehe auch

[Die Hilfsfunktion](understanding-the-helper-function.md)
