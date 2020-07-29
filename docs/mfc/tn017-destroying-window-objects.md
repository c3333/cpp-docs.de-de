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
ms.openlocfilehash: 2448a2661851f14fc6fe8747ca19495925442436
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226814"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Zerstören von Fensterobjekten

In diesem Hinweis wird die Verwendung der [CWnd::P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy) -Methode beschrieben. Verwenden Sie diese Methode, wenn Sie eine angepasste Zuordnung von von `CWnd` abgeleiteten Objekten durchführen möchten. Außerdem wird in diesem Hinweis erläutert, warum Sie [CWnd::D estroywindow](../mfc/reference/cwnd-class.md#destroywindow) verwenden sollten, um ein C++-Windows-Objekt anstelle des-Operators zu zerstören **`delete`** .

Wenn Sie die Richtlinien in diesem Thema befolgen, treten nur wenige Bereinigungs Probleme auf. Diese Probleme können aus Problemen wie dem vergessen des Lösch-/Freihand-C++ Speichers, dem vergessen, Systemressourcen wie z `HWND` . b. oder der Freigabe von Objekten zu oft verursacht werden.

## <a name="the-problem"></a>Problemstellung

Jedes Windows-Objekt (Objekt einer Klasse, die von abgeleitet `CWnd` ist) stellt sowohl ein C++-Objekt als auch ein dar `HWND` . C++-Objekte werden im Heap der Anwendung zugeordnet, und `HWND` e werden durch den Fenster-Manager in Systemressourcen zugeordnet. Da es mehrere Möglichkeiten gibt, ein Fenster Objekt zu zerstören, müssen wir einen Satz von Regeln bereitstellen, die die Systemressourcen oder Speicher Verluste verhindern. Diese Regeln müssen außerdem verhindern, dass Objekte und Windows-Handles mehrmals zerstört werden.

## <a name="destroying-windows"></a>Zerstören von Fenstern

Im folgenden sind die beiden zulässigen Möglichkeiten zum Zerstören eines Windows-Objekts aufgeführt:

- Aufrufen von `CWnd::DestroyWindow` oder der Windows-API `DestroyWindow` .

- Explizites löschen mit dem- **`delete`** Operator.

Der erste Fall ist bei weitem die häufigste. Dieser Fall gilt auch, wenn der Code nicht `DestroyWindow` direkt aufruft. Wenn der Benutzer ein Rahmen Fenster direkt schließt, generiert diese Aktion die WM_CLOSE Meldung, und die Standardantwort auf diese Meldung besteht darin, aufzurufen, `DestroyWindow.` Wenn ein übergeordnetes Fenster zerstört wird, Windows für alle untergeordneten Elemente aufruft `DestroyWindow` .

Der zweite Fall, die Verwendung des- **`delete`** Operators für Windows-Objekte, sollte selten vorkommen. Im folgenden finden Sie einige Fälle, in denen **`delete`** die Verwendung der richtigen Wahl ist.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatische Bereinigung mit CWnd::P ostncdestroy

Wenn das System ein Windows-Fenster zerstört, wird die letzte an das Fenster gesendete Windows-Meldung WM_NCDESTROY. Der Standard `CWnd` Handler für diese Nachricht ist [CWnd:: onncdestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`trennt den `HWND` vom C++-Objekt und ruft die virtuelle Funktion auf `PostNcDestroy` . Einige Klassen überschreiben diese Funktion, um das C++-Objekt zu löschen.

Die Standard Implementierung von `CWnd::PostNcDestroy` führt keine Aktion aus, was für Fenster Objekte geeignet ist, die auf dem Stapel Rahmen zugeordnet oder in andere Objekte eingebettet sind. Dies ist für Fenster Objekte nicht geeignet, die so entworfen wurden, dass Sie auf dem Heap ohne andere Objekte zugeordnet werden. Das heißt, es ist nicht für Fenster Objekte geeignet, die nicht in andere C++-Objekte eingebettet sind.

Die Klassen, die ausschließlich auf dem Heap zugeordnet werden sollen, überschreiben die- `PostNcDestroy` Methode, um **diese zu löschen**. Mit dieser Anweisung wird der dem C++-Objekt zugeordnete Arbeitsspeicher freigegeben. Obwohl der `CWnd` standarddekonstruktor aufruft `DestroyWindow` , wenn *m_hWnd* nicht NULL ist, führt dies nicht zu einer unendlichen Rekursion, da das Handle während der Bereinigungs Phase getrennt und NULL ist.

> [!NOTE]
> Das System ruft in der Regel auf, `CWnd::PostNcDestroy` nachdem die Windows-WM_NCDESTROY Meldung verarbeitet wurde, und das `HWND` C++-Fenster Objekt ist nicht mehr verbunden. Das System ruft auch `CWnd::PostNcDestroy` in der Implementierung der meisten [CWnd:: Create](../mfc/reference/cwnd-class.md#create) -Aufrufe auf, wenn ein Fehler auftritt. Die Regeln für die automatische Bereinigung werden weiter unten in diesem Thema beschrieben.

## <a name="auto-cleanup-classes"></a>Automatische Bereinigungs Klassen

Die folgenden Klassen sind nicht für die automatische Bereinigung konzipiert. Sie sind in der Regel in andere C++-Objekte oder auf dem Stapel eingebettet:

- Alle standardmäßigen Windows-Steuerelemente ( `CStatic` , `CEdit` , `CListBox` usw.).

- Alle untergeordneten Fenster, die direkt von abgeleitet `CWnd` werden (z. b. benutzerdefinierte Steuerelemente)

- Splitter Fenster ( `CSplitterWnd` ).

- Standard Steuer leisten (von abgeleitete Klassen `CControlBar` ) finden [Sie unter Technical Note 31](../mfc/tn031-control-bars.md) zum Aktivieren der automatischen Löschung für Steuer leisten Objekte.

- Dialogfelder ( `CDialog` ), die für modale Dialogfelder im Stapel Rahmen entwickelt wurden.

- Alle Standard Dialogfelder außer `CFindReplaceDialog` .

- Die von ClassWizard erstellten Standard Dialogfelder.

Die folgenden Klassen sind für die automatische Bereinigung konzipiert. Sie werden in der Regel von sich selbst auf dem Heap zugewiesen:

- Hauptrahmen Fenster (direkt oder indirekt von abgeleitet `CFrameWnd` ).

- Fenster anzeigen (direkt oder indirekt von abgeleitet `CView` ).

Wenn Sie diese Regeln unterbrechen möchten, müssen Sie die- `PostNcDestroy` Methode in der abgeleiteten Klasse überschreiben. Wenn Sie der Klasse eine automatische Bereinigung hinzufügen möchten, können Sie die Basisklasse aufzurufen und **diese dann löschen**. Um die automatische Bereinigung aus der Klasse zu entfernen, müssen `CWnd::PostNcDestroy` Sie direkt anstelle der- `PostNcDestroy` Methode ihrer direkten Basisklasse aufzurufen.

Die häufigste Verwendung der Änderung des automatischen Bereinigungs Verhaltens ist das Erstellen eines nicht modalem Dialog Felds, das auf dem Heap zugewiesen werden kann.

## <a name="when-to-call-delete"></a>Zeitpunkt des Aufrufens von DELETE

Es wird empfohlen, dass Sie `DestroyWindow` zum Zerstören eines Windows-Objekts, entweder der C++-Methode oder der globalen API, aufruft `DestroyWindow` .

Verwenden Sie nicht die globale `DestroyWindow` API, um ein untergeordnetes MDI-Fenster zu zerstören. Verwenden Sie stattdessen die virtuelle-Methode `CWnd::DestroyWindow` .

Für C++ Window-Objekte, die keine automatische Bereinigung ausführen, kann die Verwendung des- **`delete`** Operators zu einem Speicherfehler führen, wenn Sie versuchen, im debugtor aufzurufen, `DestroyWindow` `CWnd::~CWnd` Wenn der VTBL nicht auf die ordnungsgemäß abgeleitete Klasse zeigt. Dies liegt daran, dass das System nicht die geeignete zerstörungsmethode finden kann, die aufgerufen werden kann. `DestroyWindow`Die Verwendung von anstelle von **`delete`** vermeidet diese Probleme. Da dies ein feiner Fehler sein kann, generiert die Kompilierung im Debugmodus die folgende Warnung, wenn Sie ein Risiko haben.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

Im Fall von C++-Windows-Objekten, die eine automatische Bereinigung ausführen, müssen Sie den Befehl ausführen `DestroyWindow` . Wenn Sie den- **`delete`** Operator direkt verwenden, werden Sie von der MFC-Diagnose Speicherzuweisung benachrichtigt, dass Sie den Speicher zweimal freigeben. Die beiden Vorkommen sind der erste explizite-Rückruf und der indirekte-Befehl, diesen in der automatischen Bereinigungs Implementierung von zu **Löschen** `PostNcDestroy` .

Nach `DestroyWindow` dem Aufruf von für ein nicht automatisch Bereinigungs Objekt ist das C++-Objekt immer noch um, *m_hWnd* jedoch NULL sein. Nach dem Aufruf von `DestroyWindow` für ein Objekt für die automatische Bereinigung wird das C++-Objekt entfernt und vom C++ Delete-Operator in der automatischen Bereinigungs Implementierung von freigegeben `PostNcDestroy` .

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
