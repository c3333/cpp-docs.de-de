---
title: Dokumentvorlagenklassen
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446913"
---
# <a name="document-template-classes"></a>Dokumentvorlagenklassen

Mit Dokumentvorlagen Objekten wird die Erstellung von Dokument-, Ansichts-und Rahmen Fenster Objekten koordiniert, wenn ein neues Dokument oder eine neue Sicht erstellt wird.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
Die Basisklasse für Dokumentvorlagen. Diese Klasse wird niemals direkt verwendet; Stattdessen verwenden Sie eine der anderen Dokumentvorlagen Klassen, die von dieser Klasse abgeleitet werden.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Eine Vorlage für Dokumente in der Multiple Document Interface (MDI). Für MDI-Anwendungen können mehrere Dokumente gleichzeitig geöffnet sein.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Eine Vorlage für Dokumente in der Single Document Interface (SDI). Für SDI-Anwendungen ist jeweils nur ein Dokument geöffnet.

## <a name="related-class"></a>Verwandte Klasse

[Ckreatecontext](../mfc/reference/ccreatecontext-structure.md)<br/>
Eine-Struktur, die von einer Dokument Vorlage an Fenster Erstellungs Funktionen übermittelt wird, um die Erstellung von Dokument-, Ansichts-und Rahmen Fenster Objekten zu koordinieren.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
