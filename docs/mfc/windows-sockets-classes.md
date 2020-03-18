---
title: Windows Sockets-Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445984"
---
# <a name="windows-sockets-classes"></a>Windows Sockets-Klassen

Windows Sockets bieten eine Netzwerkprotokoll unabhängige Methode für die Kommunikation zwischen zwei Computern. Diese Sockets können synchron sein (Ihr Programm wartet, bis die Kommunikation erfolgt) oder asynchron (das Programm wird weiter ausgeführt, während die Kommunikation erfolgt).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Kapselt die Windows Sockets-API in einem Thin Wrapper.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Eine Abstraktion auf höherer Ebene, die von `CAsyncSocket`abgeleitet ist. Er arbeitet synchron.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Stellt eine `CFile`-Schnittstelle für einen Windows-Socket bereit.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
