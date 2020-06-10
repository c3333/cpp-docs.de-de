---
title: Dokumentvorlagenklassen
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: dffde80093f98fc1c81a6c20dfaf92b82e3b4c78
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618983"
---
# <a name="document-template-classes"></a>Dokumentvorlagenklassen

Mit Dokumentvorlagen Objekten wird die Erstellung von Dokument-, Ansichts-und Rahmen Fenster Objekten koordiniert, wenn ein neues Dokument oder eine neue Sicht erstellt wird.

[CDocTemplate](reference/cdoctemplate-class.md)<br/>
Die Basisklasse für Dokumentvorlagen. Diese Klasse wird niemals direkt verwendet; Stattdessen verwenden Sie eine der anderen Dokumentvorlagen Klassen, die von dieser Klasse abgeleitet werden.

[CMultiDocTemplate](reference/cmultidoctemplate-class.md)<br/>
Eine Vorlage für Dokumente in der Multiple Document Interface (MDI). Für MDI-Anwendungen können mehrere Dokumente gleichzeitig geöffnet sein.

[CSingleDocTemplate](reference/csingledoctemplate-class.md)<br/>
Eine Vorlage für Dokumente in der Single Document Interface (SDI). Für SDI-Anwendungen ist jeweils nur ein Dokument geöffnet.

## <a name="related-class"></a>Verwandte Klasse

[Ckreatecontext](reference/ccreatecontext-structure.md)<br/>
Eine-Struktur, die von einer Dokument Vorlage an Fenster Erstellungs Funktionen übermittelt wird, um die Erstellung von Dokument-, Ansichts-und Rahmen Fenster Objekten zu koordinieren.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
