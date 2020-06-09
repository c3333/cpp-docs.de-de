---
title: ExitInstance-Memberfunktion
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622693"
---
# <a name="exitinstance-member-function"></a>ExitInstance-Memberfunktion

Die [ExitInstance](reference/cwinapp-class.md#exitinstance) -Member-Funktion der [CWinApp](reference/cwinapp-class.md) -Klasse wird jedes Mal aufgerufen, wenn eine Kopie der Anwendung beendet wird. Dies geschieht normalerweise, wenn der Benutzer die Anwendung beendet.

Überschreiben `ExitInstance` Sie, wenn Sie eine besondere Bereinigungs Verarbeitung benötigen, z. b. das Freigeben von GDI-Ressourcen (Graphics Device Interface) oder die Aufhebung der Zuordnung von Arbeitsspeicher, Das Bereinigen von Standardelementen, wie z. b. Dokumenten und Sichten, wird jedoch durch das Framework bereitgestellt, wobei andere über schreibbare Funktionen für spezielle Bereinigung speziell für diese Objekte bereitgestellt werden.

## <a name="see-also"></a>Siehe auch

[CWinApp: Die Anwendungsklasse](cwinapp-the-application-class.md)
