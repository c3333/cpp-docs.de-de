---
title: Active Technology und DLLs
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: f67fb9548601ac705ceda08d20d3049f0bf1e0a5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220997"
---
# <a name="active-technology-and-dlls"></a>Active Technology und DLLs

Active Technology bietet die Möglichkeit, Objektserver vollständig innerhalb einer DLL zu implementieren. Dieser Servertyp wird In-Process-Server genannt. MFC unterstützt In-Process-Server nicht vollständig für alle Features der visuellen Bearbeitung. Der Hautgrund dafür ist, dass Active Technology keine Möglichkeit bietet, einen Server in die Hauptnachrichtenschleife des Containers einzuschließen. MFC benötigt den Zugriff auf die Nachrichtenschleife der Containeranwendung, um Zugriffstasten und die Leerlaufzeitverarbeitung zu verarbeiten.

Wenn Sie einen Automatisierungsserver schreiben und dieser Server keine Benutzeroberfläche besitzt, können Sie aus Ihrem Server einen In-Process-Server generieren und diesen vollständig in eine DLL einfügen.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Automatisierungsserver](../mfc/automation-servers.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
