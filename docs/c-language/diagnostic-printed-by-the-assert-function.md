---
title: Diagnose von der assert-Funktion gedruckt
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234222"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnose von der assert-Funktion gedruckt

**ANSI 4.2** Die von der **assert**-Funktion ausgegebene Diagnose und das Abbruchverhalten dieser Funktion

Die **assert**-Funktion gibt eine Diagnosemeldung aus und ruft die **abort**-Routine auf, wenn der Ausdruck „false“ (0) ist. Die Diagnosemeldung hat die Form

> **Assertionsfehler**: <em>Ausdruck</em> **, file** <em>Dateiname</em> **, line** *Zeilennummer*

Dabei steht *filename* für den Namen der Quelldatei und *linenumber* für die Zeilennummer der Assertion, die in der Quelldatei einen Fehler aufweist. Es werden keine Aktionen ausgeführt, wenn der *Ausdruck* TRUE ist (ungleich Null).

## <a name="see-also"></a>Siehe auch

[Bibliotheksfunktionen](../c-language/library-functions.md)
