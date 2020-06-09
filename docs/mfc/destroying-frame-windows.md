---
title: Zerstören von Rahmenfenstern
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
ms.openlocfilehash: 4bc7945ecd9aee9021ce97fa3ea05f512c58fe20
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621924"
---
# <a name="destroying-frame-windows"></a>Zerstören von Rahmenfenstern

Das MFC-Framework verwaltet die Fenster Zerstörung sowie die Erstellung für die Fenster, die frameworkdokumenten und-Ansichten zugeordnet sind. Wenn Sie zusätzliche Fenster erstellen, sind Sie dafür verantwortlich, Sie zu zerstören.

Wenn der Benutzer das Rahmen Fenster schließt, ruft der standardmäßige [OnClose](reference/cwnd-class.md#onclose) -Handler des Fensters das Fenster " [DestroyWindow](reference/cwnd-class.md#destroywindow)" auf. Die letzte Member-Funktion, die aufgerufen wird, wenn das Windows-Fenster zerstört wird, ist " [onncdestroy](reference/cwnd-class.md#onncdestroy)", der eine Bereinigung durchführt, die [Standard](reference/cwnd-class.md#default) Element Funktion zum Ausführen der Windows-Bereinigung aufruft und schließlich die Funktion " [PostNcDestroy](reference/cwnd-class.md#postncdestroy)" des virtuellen Members aufruft Die [CFrameWnd](reference/cframewnd-class.md) -Implementierung von `PostNcDestroy` Löscht das C++ Window-Objekt. Sie sollten niemals den C++ **Delete** -Operator in einem Rahmen Fenster verwenden. Verwenden Sie stattdessen `DestroyWindow`.

Wenn das Hauptfenster geschlossen wird, wird die Anwendung geschlossen. Wenn nicht gespeicherte Dokumente geändert werden, zeigt das Framework ein Meldungs Feld an, um zu Fragen, ob die Dokumente gespeichert werden sollen, und stellt sicher, dass die entsprechenden Dokumente ggf. gespeichert werden.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Erstellen von Dokument Rahmen Fenstern](creating-document-frame-windows.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
