---
title: 'TN017: Zerstören von Fensterobjekten'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370420"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Zerstören von Fensterobjekten

Dieser Hinweis beschreibt die Verwendung der [CWnd::PostNcDestroy-Methode.](../mfc/reference/cwnd-class.md#postncdestroy) Verwenden Sie diese Methode, wenn `CWnd`Sie eine benutzerdefinierte Zuordnung von -abgeleiteten Objekten erstellen möchten. In diesem Hinweis wird auch erläutert, warum Sie [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) verwenden sollten, um ein C++-Windows-Objekt anstelle des **Delete-Operators** zu zerstören.

Wenn Sie die Richtlinien in diesem Thema befolgen, werden Sie nur wenige Bereinigungsprobleme haben. Diese Probleme können durch das Vergessen des Löschens/Freiens von C++-Speicher, das Vergessen, Systemressourcen wie `HWND`s freizugeben, oder das Zulösen von Objekten zu oft entstehen.

## <a name="the-problem"></a>Problemstellung

Jedes Windows-Objekt (Objekt einer `CWnd`von abgeleiteten Klasse) stellt `HWND`sowohl ein C++-Objekt als auch eine dar. C++-Objekte werden im Heap der `HWND`Anwendung und s vom Fenstermanager in Systemressourcen zugewiesen. Da es mehrere Möglichkeiten zum Zerstören eines Fensterobjekts gibt, müssen wir eine Reihe von Regeln bereitstellen, die Systemressourcen- oder Speicherverluste verhindern. Diese Regeln müssen auch verhindern, dass Objekte und Windows-Handles mehr als einmal zerstört werden.

## <a name="destroying-windows"></a>Zerstören von Windows

Im Folgenden sind die beiden zulässigen Möglichkeiten zum Zerstören eines Windows-Objekts:

- Aufrufen `CWnd::DestroyWindow` oder die `DestroyWindow`Windows-API .

- Explizites Löschen mit dem **Löschoperator.**

Der erste Fall ist bei weitem der häufigste. Dieser Fall gilt auch dann, `DestroyWindow` wenn Ihr Code nicht direkt aufruft. Wenn der Benutzer ein Rahmenfenster direkt schließt, generiert diese Aktion die WM_CLOSE Nachricht, und die Standardantwort auf diese Nachricht lautet, `DestroyWindow.` wenn ein übergeordnetes Fenster zerstört wird, ruft `DestroyWindow` Windows alle untergeordneten Elemente auf.

Der zweite Fall, die Verwendung des **Delete-Operators** für Windows-Objekte, sollte selten sein. Im Folgenden finden Sie einige Fälle, in denen die Verwendung von **Delete** die richtige Wahl ist.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatische Bereinigung mit CWnd::PostNcDestroy

Wenn das System ein Windows-Fenster zerstört, wird die letzte an das Fenster gesendete Windows-Nachricht WM_NCDESTROY. Der `CWnd` Standardhandler für diese Nachricht ist [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`trennt sich `HWND` vom C++-Objekt und ruft `PostNcDestroy`die virtuelle Funktion auf. Einige Klassen überschreiben diese Funktion, um das C++-Objekt zu löschen.

Die Standardimplementierung `CWnd::PostNcDestroy` von bewirkt nichts, was für Fensterobjekte geeignet ist, die auf dem Stapelrahmen zugeordnet oder in andere Objekte eingebettet sind. Dies ist nicht für Fensterobjekte geeignet, die so konzipiert sind, dass sie ohne andere Objekte auf dem Heap zugewiesen werden. Mit anderen Worten, es ist nicht für Fensterobjekte geeignet, die nicht in andere C++-Objekte eingebettet sind.

Die Klassen, die so konzipiert sind, dass `PostNcDestroy` sie allein auf dem Heap zugewiesen werden, überschreiben die Methode, um diese zu **löschen.** Mit dieser Anweisung wird der speicher, der dem C++-Objekt zugeordnet ist, frei. Obwohl der `CWnd` Standarddestruktor aufruft, `DestroyWindow` wenn *m_hWnd* nicht NULL ist, führt dies nicht zu einer unendlichen Rekursion, da das Handle während der Bereinigungsphase getrennt und NULL wird.

> [!NOTE]
> Das System `CWnd::PostNcDestroy` ruft in der Regel auf, nachdem es die Windows-WM_NCDESTROY Nachricht verarbeitet hat, und das `HWND` und das C++-Fensterobjekt sind nicht mehr verbunden. Das System ruft `CWnd::PostNcDestroy` auch die Implementierung der meisten [CWnd::Create-Aufrufe](../mfc/reference/cwnd-class.md#create) auf, wenn ein Fehler auftritt. Die Regeln für die automatische Bereinigung werden weiter unten in diesem Thema beschrieben.

## <a name="auto-cleanup-classes"></a>Automatische Bereinigungsklassen

Die folgenden Klassen sind nicht für die automatische Bereinigung vorgesehen. Sie sind in der Regel in andere C++-Objekte oder auf dem Stapel eingebettet:

- Alle Standardmäßigen`CStatic`Windows-Steuerelemente ( , `CEdit`, `CListBox`usw.).

- Alle untergeordneten Fenster, die direkt von `CWnd` (z. B. benutzerdefinierten Steuerelementen) abgeleitet werden.

- Splitterfenster`CSplitterWnd`( ).

- Standardsteuerungsleisten (von `CControlBar`abgeleitete Klassen finden Sie unter [Technical Note 31](../mfc/tn031-control-bars.md) zum Aktivieren des automatischen Löschens für Steuerelementleistenobjekte).

- Dialogfelder`CDialog`( ) für modale Dialoge auf dem Stapelrahmen.

- Alle Standarddialoge `CFindReplaceDialog`außer .

- Die von ClassWizard erstellten Standarddialogfelder.

Die folgenden Klassen sind für die automatische Bereinigung konzipiert. Sie werden in der Regel selbst auf dem Heap zugewiesen:

- Hauptrahmenfenster (direkt oder indirekt von `CFrameWnd`abgeleitet).

- Fenster anzeigen (direkt oder `CView`indirekt von abgeleitet).

Wenn Sie diese Regeln brechen möchten, `PostNcDestroy` müssen Sie die Methode in der abgeleiteten Klasse überschreiben. Um Ihrer Klasse eine automatische Bereinigung hinzuzufügen, rufen Sie Ihre Basisklasse auf, und **löschen**Sie diese . Um die automatische Bereinigung aus `CWnd::PostNcDestroy` Ihrer Klasse `PostNcDestroy` zu entfernen, rufen Sie direkt anstelle der Methode Ihrer direkten Basisklasse auf.

Die häufigste Verwendung des Änderns des Verhaltens der automatischen Bereinigung besteht darin, ein modusloses Dialogfeld zu erstellen, das auf dem Heap zugewiesen werden kann.

## <a name="when-to-call-delete"></a>Wann Aufruf löschen

Es wird empfohlen, ein Windows-Objekt, entweder die C++-Methode oder die globale `DestroyWindow` `DestroyWindow` API, aufzurufen.

Rufen Sie die `DestroyWindow` globale API nicht auf, um ein MDI-Child-Fenster zu zerstören. Sie sollten stattdessen `CWnd::DestroyWindow` die virtuelle Methode verwenden.

Bei C++-Fensterobjekten, die keine automatische Bereinigung durchführen, kann die Verwendung des `DestroyWindow` **Delete-Operators** einen Speicherverlust verursachen, wenn Sie versuchen, den `CWnd::~CWnd` Destruktor aufzurufen, wenn die VTBL nicht auf die korrekt abgeleitete Klasse zeigt. Dies liegt daran, dass das System die geeignete Zerstörungsmethode zum Aufrufen nicht finden kann. Durch `DestroyWindow` Verwenden statt **Löschen** werden diese Probleme vermieden. Da dies ein subtiler Fehler sein kann, generiert das Kompilieren im Debugmodus die folgende Warnung, wenn Sie gefährdet sind.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

Bei C++-Windows-Objekten, die eine automatische Bereinigung `DestroyWindow`durchführen, müssen Sie aufrufen. Wenn Sie den **Löschoperator** direkt verwenden, benachrichtigt Sie der MFC-Diagnosespeicherzunokator, dass Sie den Speicher zweimal freigibt. Die beiden Vorkommen sind Ihr erster expliziter Aufruf und der indirekte Aufruf, diesen in der Auto-Cleanup-Implementierung von `PostNcDestroy`zu **löschen.**

Nach `DestroyWindow` dem Aufruf eines Nicht-Auto-Bereinigungsobjekts befindet sich das C++-Objekt weiterhin, *aber m_hWnd* null ist. Nach `DestroyWindow` dem Aufruf eines Auto-Cleanup-Objekts wird das C++-Objekt nicht mehr verwendet, und `PostNcDestroy`es wird vom C++-Löschoperator in der Auto-Cleanup-Implementierung von freigegeben.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
