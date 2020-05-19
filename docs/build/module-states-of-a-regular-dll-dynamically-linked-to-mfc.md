---
title: Modulzustände einer regulären, dynamisch mit MFC verknüpften MFC-DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220578"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Modulzustände einer regulären, dynamisch mit MFC verknüpften MFC-DLL

Das dynamische Verknüpfen einer regulären MFC-DLL mit der MFC-DLL ermöglicht bestimmte Konfigurationen, die sehr kompliziert sind. Beispielsweise können eine reguläre MFC-DLL und die ausführbare Datei, die diese verwendet, dynamisch mit der MFC-DLL und mit allen MFC-Erweiterungs-DLLs verknüpft werden.

Diese Konfiguration stellt ein Problem im Hinblick auf die globalen MFC-Daten dar, z. B. für den Zeiger auf das aktuelle `CWinApp`-Objekt und die Handlezuordnungen.

Vor MFC-Version 4.0 befanden sich diese globalen Daten in der MFC-DLL selbst und wurden von allen Modulen im Prozess gemeinsam verwendet. Da jeder Prozess, der eine Win32-DLL verwendet, eine eigene Kopie der DLL-Daten erhält, bietet dieses Schema eine einfache Möglichkeit, prozessbezogene Daten nachzuverfolgen. Da das AFXDLL-Modell davon ausgegangen ist, dass es nur ein `CWinApp`-Objekt und nur eine Reihe von Handlezuordnungen im Prozess gibt, können diese Elemente in der MFC-DLL selbst nachverfolgt werden.

Mit der Option, eine reguläre MFC-DLL dynamisch mit der MFC-DLL zu verknüpfen, ist es jetzt jedoch möglich, dass ein Prozess zwei oder mehr `CWinApp`-Objekte und zwei oder mehr Reihen von Handlezuordnungen enthält. Wie wird in MFC nachverfolgt, welche davon verwendet werden sollen?

Dazu muss jedes Modul (Anwendung oder reguläre MFC-DLL) eine eigene Kopie dieser globalen Zustandsinformationen erhalten. Folglich gibt ein Aufruf von **AfxGetApp** in der regulären MFC-DLL einen Zeiger auf das `CWinApp`-Objekt in der DLL zurück, nicht auf das in der ausführbaren Datei. Diese modulbezogene Kopie der globalen MFC-Daten wird als Modulzustand bezeichnet und in [TN058: Implementierung des MFC-Modulzustands](../mfc/tn058-mfc-module-state-implementation.md) beschrieben.

Die allgemeine MFC-Fensterprozedur wechselt automatisch in den richtigen Modulzustand, sodass Sie sich keine Gedanken über die in der regulären MFC-DLL implementierten Nachrichtenhandler machen müssen. Wenn Ihre ausführbare Datei jedoch die reguläre MFC-DLL aufruft, müssen Sie den aktuellen Modulzustand explizit auf den der DLL festlegen. Verwenden Sie dazu das Makro **AFX_MANAGE_STATE** in jeder Funktion, die aus der DLL exportiert wird. Dies erfolgt, indem die folgende Codezeile am Beginn der Funktionen hinzugefügt wird, die aus der DLL exportiert werden:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Verwalten der Zustandsdaten von MFC-Modulen](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC extension DLLs (MFC-Erweiterungs-DLLs)](extension-dlls-overview.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
