---
title: 'TN070: MFC-Fensterklassennamen'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373485"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC-Fensterklassennamen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

MFC-Fenster verwenden einen dynamisch erstellten Klassennamen, der die Features des Fensters wiedergibt. MFC generiert Klassennamen dynamisch für Rahmenfenster, Ansichten und Popupfenster, die von der Anwendung erstellt werden. Dialogfelder und Steuerelemente, die von einer MFC-Anwendung erstellt werden, haben den von Windows bereitgestellten Namen für die betreffende Fensterklasse.

Sie können den dynamisch bereitgestellten Klassennamen ersetzen, indem Sie eine eigene Fensterklasse registrieren und in einer Außerkraftsetzung von [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)verwenden. Ihre von MFC bereitgestellten Klassennamen passen zu einem der beiden folgenden Formen:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Die Hex-Ziffern, `%x` die die Zeichen ersetzen, werden aus Daten aus der [WNDCLASS-Struktur](/windows/win32/api/winuser/ns-winuser-wndclassw) ausgefüllt. MFC verwendet diese Technik, sodass mehrere C++-Klassen, die identische **WNDCLASS-Strukturen** erfordern, dieselbe registrierte Fensterklasse gemeinsam nutzen können. Im Gegensatz zu den meisten einfachen Win32-Anwendungen verfügen MFC-Anwendungen nur über eine **WNDPROC**, sodass Sie **WNDCLASS-Strukturen** einfach freigeben können, um Zeit und Arbeitsspeicher zu sparen. Die ersetzbaren Werte für die `%x` oben gezeigten Zeichen lauten wie folgt:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrHintergrund**

- **WNDCLASS.hIcon**

Das erste`Afx:%x:%x`Formular ( ) wird verwendet, wenn **hCursor**, **hbrBackground**und **hIcon** alle **NULL**sind.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)<br/>
[TN020: ID-Benennungs- und Nummerierungskonventionen](../mfc/tn020-id-naming-and-numbering-conventions.md)
