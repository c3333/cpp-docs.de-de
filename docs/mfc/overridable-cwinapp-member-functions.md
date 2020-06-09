---
title: Überschreibbare CWinApp-Memberfunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624016"
---
# <a name="overridable-cwinapp-member-functions"></a>Überschreibbare CWinApp-Memberfunktionen

[CWinApp](reference/cwinapp-class.md) bietet mehrere wichtige über schreibbare Element Funktionen ( `CWinApp` überschreibt diese Member von der Klasse [CWinThread](reference/cwinthread-class.md), von der `CWinApp` abgeleitet wird):

- [InitInstance](initinstance-member-function.md)

- [Ausführen](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

Die einzige `CWinApp` Member-Funktion, die Sie überschreiben müssen, ist `InitInstance` .

## <a name="see-also"></a>Siehe auch

[CWinApp: Die Anwendungsklasse](cwinapp-the-application-class.md)
