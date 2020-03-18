---
title: Überschreibbare CWinApp-Memberfunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447264"
---
# <a name="overridable-cwinapp-member-functions"></a>Überschreibbare CWinApp-Memberfunktionen

[CWinApp](../mfc/reference/cwinapp-class.md) stellt mehrere wichtige über schreibbare Element Funktionen bereit (`CWinApp` diese Member von der Klasse [CWinThread](../mfc/reference/cwinthread-class.md)überschreibt, von der `CWinApp` abgeleitet ist):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Ausführen](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

Die einzige `CWinApp` Member-Funktion, die Sie überschreiben müssen, ist `InitInstance`.

## <a name="see-also"></a>Weitere Informationen

[CWinApp: Die Anwendungsklasse](../mfc/cwinapp-the-application-class.md)
