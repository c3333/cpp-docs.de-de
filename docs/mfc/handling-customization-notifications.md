---
title: Behandeln von Anpassungsbenachrichtigungen
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: d88e1efe12fd5b31a9f78b8fe439ba1aefa72d1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625726"
---
# <a name="handling-customization-notifications"></a>Behandeln von Anpassungsbenachrichtigungen

Ein allgemeine Windows-Symbolleisten-Steuerelement verfügt über integrierte Funktionen zur Anpassung, einschließlich eines vom System definierten Anpassungsdialogfelds, das dem Benutzer das Einfügen, Löschen oder erneute Anordnen von Schaltflächen auf der Symbolleiste ermöglicht. Die Anwendung bestimmt, ob die Anpassungsfunktionen verfügbar sind und steuert das Ausmaß, bis zu dem der Benutzer die Symbolleiste anpassen kann.

Sie können diese Anpassungs Features für den Benutzer verfügbar machen, indem Sie der Symbolleiste die **CCS_ADJUSTABLE** -Formatvorlage erteilen. Die Anpassungsfunktionen ermöglichen es dem Benutzer, eine Schaltfläche an eine neue Position zu ziehen oder eine Schaltfläche zu entfernen, indem er sie von der Symbolleiste zieht. Darüber hinaus kann der Benutzer auf die Symbolleiste doppelklicken, um das Dialogfeld **Symbolleiste anpassen** anzuzeigen, in dem der Benutzer Symbolleistenschaltflächen hinzufügen, löschen und neu anordnen kann. Die Anwendung kann das Dialogfeld mithilfe der Memberfunktion [Customize](reference/ctoolbarctrl-class.md#customize) anzeigen.

Das Symbolleistensteuerelement sendet bei jedem Schritt im Anpassungsvorgang Benachrichtigungsmeldungen an das übergeordnete Fenster. Wenn der Benutzer die UMSCHALT-Taste gedrückt hält und beginnt, eine Schaltfläche zu ziehen, übernimmt die Symbolleiste automatisch die Verarbeitung des Ziehvorgangs. Die Symbolleiste sendet die Benachrichtigungsmeldung **TBN_QUERYDELETE** an das übergeordnete Fenster, um zu bestimmen, ob die Schaltfläche gelöscht werden darf. Der Ziehvorgang endet, wenn das übergeordnete Fenster **FALSE**zurückgibt. Andernfalls erfasst die Symbolleiste die Mauseingabe und wartet darauf, dass der Benutzer die Maustaste freigibt.

Wenn der Benutzer die Maustaste freigibt, bestimmt die Symbolleiste die Position des Mauszeigers. Wenn der Zeiger sich außerhalb der Symbolleiste befindet, wird die Schaltfläche gelöscht. Wenn der Cursor sich auf einer anderen Symbolleistenschaltfläche befindet, sendet die Symbolleiste die Benachrichtigungsmeldung **TBN_QUERYINSERT** an das übergeordnete Fenster, um zu bestimmen, ob links neben der angegebenen Schaltfläche eine Schaltfläche eingefügt werden darf. Die Schaltfläche wird eingefügt, wenn das übergeordnete Fenster **TRUE**zurückgibt, andernfalls nicht. Die Symbolleiste sendet die Benachrichtigungsmeldung **TBN_TOOLBARCHANGE** , um das Ende des Ziehvorgangs anzuzeigen.

Wenn der Benutzer einen Ziehvorgang beginnt, ohne die UMSCHALT-Taste gedrückt zu halten, sendet das Symbolleistensteuerelement die Benachrichtigungsmeldung **TBN_BEGINDRAG** an das besitzende Fenster. Eine Anwendung, die eigenen Code zum Ziehen von Schaltflächen implementiert, kann diese Nachricht als Signal zum Einleiten eines Ziehvorgangs verwenden. Die Symbolleiste sendet die Benachrichtigungsmeldung **TBN_ENDDRAG** , um das Ende des Ziehvorgangs anzuzeigen.

Ein Symbolleistensteuerelement sendet Benachrichtigungsmeldungen, wenn der Benutzer eine Symbolleiste mithilfe des Dialogfelds **Symbolleiste anpassen** konfiguriert. Die Symbolleiste sendet die Benachrichtigungsmeldung **TBN_BEGINADJUST** , nachdem der Benutzer auf die Symbolleiste doppelgeklickt hat, aber bevor das Dialogfeld erstellt wird. Als Nächstes beginnt die Symbolleiste, eine Reihe von **TBN_QUERYINSERT** -Benachrichtigungsmeldungen zu senden, um zu bestimmen, ob die Symbolleiste das Einfügen von Schaltflächen zulässt. Wenn das übergeordnete Fenster **TRUE**zurückgibt, hört die Symbolleiste mit dem Senden von **TBN_QUERYINSERT** -Benachrichtigungsmeldungen auf. Wenn das übergeordnete Fenster für keine der Schaltflächen **TRUE** zurückgibt, zerstört die Symbolleiste das Dialogfeld.

Als Nächstes bestimmt das Symbolleistensteuerelement, ob Schaltflächen von der Symbolleiste gelöscht werden können, indem es eine **TBN_QUERYDELETE** -Benachrichtigungsmeldung für jede Schaltfläche auf der Symbolleiste sendet. Das übergeordnete Fenster gibt **TRUE** zurück, um anzuzeigen, dass eine Schaltfläche gelöscht werden kann; andernfalls gibt es **FALSE**zurück. Die Symbolleiste fügt dem Dialogfeld alle Symbolleistenschaltflächen hinzu, stellt aber die nicht löschbaren grau dar.

Immer, wenn die Symbolleiste Informationen über eine Schaltfläche im Dialogfeld „Symbolleiste anpassen“ benötigt, sendet sie die **TBN_GETBUTTONINFO** -Benachrichtigungsmeldung und gibt dabei den Index der Schaltfläche, für die sie Informationen benötigt, sowie die Adresse einer **TBNOTIFY** -Struktur an. Das übergeordnete Fenster muss die Struktur mit den relevanten Informationen füllen.

Das Dialogfeld **Symbolleiste anpassen** enthält eine Schaltfläche „Hilfe“ und eine Schaltfläche „Zurücksetzen“. Wenn der Benutzer die Schaltfläche „Hilfe“ auswählt, sendet das Symbolleistensteuerelement die Benachrichtigungsmeldung **TBN_CUSTHELP** . Das übergeordnete Fenster sollte darauf mit dem Anzeigen von Hilfeinformationen reagieren. Das Dialogfeld sendet die Benachrichtigungsmeldung **TBN_RESET** , wenn der Benutzer die Schaltfläche „Zurücksetzen“ auswählt. Diese Nachricht zeigt an, dass die Symbolleiste unmittelbar davor steht, das Dialogfeld erneut zu initialisieren.

Alle diese Nachrichten sind **WM_NOTIFY** -Nachrichten, und sie können in Ihrem Besitzerfenster durch das Hinzufügen von Meldungszuordnungseinträgen der folgenden Form zur Meldungszuordnung Ihres Besitzerfensters verarbeitet werden:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wnotifycode schalten**

   ID-Code der Benachrichtigungsmeldung, wie etwa **TBN_BEGINADJUST**.

- **idcontrol**

   Der Bezeichner des Steuerelements, das die Benachrichtigung gesendet.

- **Mitgliedschaft**

   Die Memberfunktion die aufgerufen werden soll, wenn diese Benachrichtigung empfangen wird.

Ihre Memberfunktion sollte mit dem folgenden Prototyp deklariert sein:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Wenn der Benachrichtigungsmeldungshandler einen Wert zurückgibt, sollte er ihn in das **LRESULT** einfügen, auf das *result*verweist.

Für jede Meldung verweist `pNotifyStruct` entweder auf eine **NMHDR** - oder auf eine **TBNOTIFY** -Struktur. Diese Strukturen sind unten beschrieben:

Die **NMHDR** -Struktur enthält die folgenden Member:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Das Fensterhandle des Steuerelements, das die Benachrichtigung sendet. Um dieses Handle in einen `CWnd` -Zeiger zu konvertieren, verwenden Sie [CWnd::FromHandle](reference/cwnd-class.md#fromhandle).

- **idFrom**

   ID des Steuerelements, das die Benachrichtigung sendet.

- **code**

   Benachrichtigungscode. Dieser Member kann ein für einen Steuerelementtyp spezifischer Wert sein, wie etwa **TBN_BEGINADJUST** oder **TTN_NEEDTEXT**, oder es kann einer der allgemeinen Benachrichtigungswerte sein, die unten aufgelistet sind:

  - **NM_CLICK** Der Benutzer hat innerhalb des Steuerelements mit der linken Maustaste geklickt.

  - **NM_DBLCLK** Der Benutzer hat innerhalb des Steuerelements mit der linken Maustaste doppelgeklickt.

  - **NM_KILLFOCUS** Das Steuerelement hat den Eingabefokus verloren.

  - **NM_OUTOFMEMORY** Das Steuerelement konnte einen Vorgang nicht abschließen, weil nicht genügend Arbeitsspeicher verfügbar ist.

  - **NM_RCLICK** Der Benutzer hat innerhalb des Steuerelements mit der rechten Maustaste geklickt.

  - **NM_RDBLCLK** Der Benutzer hat innerhalb des Steuerelement mit der rechten Maustaste doppelgeklickt.

  - **NM_RETURN** Das Steuerelement hat den Eingabefokus, und der Benutzer hat die EINGABETASTE gedrückt.

  - **NM_SETFOCUS** Das Steuerelement hat den Eingabefokus erhalten.

Die **TBNOTIFY** -Struktur enthält die folgenden Member:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   Gemeinsame Informationen für alle **WM_NOTIFY** -Nachrichten.

- **iItem**

   Index der Schaltfläche, die der Benachrichtigung zugeordnet ist.

- **tbButton**

   **TBBUTTON** -Struktur, die Informationen über die Symbolleisten-Schaltfläche enthält, die der Benachrichtigung zugeordnet ist.

- **cchText**

   Anzahl der Zeichen im Schaltflächentext.

- **lpszText**

   Zeiger auf den Schaltflächentext.

Die Benachrichtigungen, die die Symbolleiste sendet, sind wie folgt:

- **TBN_BEGINADJUST**

   Wird gesendet, wenn der Benutzer mit dem Anpassen eines Symbolleisten Steuer Elements beginnt. Der Zeiger verweist auf eine **NMHDR** -Struktur, die Informationen zur Benachrichtigung enthält. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_BEGINDRAG**

   Wird gesendet, wenn der Benutzer beginnt, eine Schaltfläche in einem ToolBar-Steuerelement zu ziehen Der Zeiger verweist auf eine **TBNOTIFY** -Struktur. Das **iItem** -Member enthält den nullbasierten Index der gezogenen Schaltfläche. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_CUSTHELP**

   Wird gesendet, wenn der Benutzer die Schaltfläche Hilfe im Dialogfeld Symbolleiste anpassen auswählt. Kein Rückgabewert. Der Zeiger verweist auf eine **NMHDR** -Struktur, die Informationen über die Benachrichtigungsmeldung enthält. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_ENDADJUST**

   Wird gesendet, wenn der Benutzer das Anpassen eines Symbolleisten-Steuer Elements beendet. Der Zeiger verweist auf eine **NMHDR** -Struktur, die Informationen über die Benachrichtigungsmeldung enthält. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_ENDDRAG**

   Wird gesendet, wenn der Benutzer das Ziehen einer Schaltfläche in einem ToolBar-Steuerelement beendet. Der Zeiger verweist auf eine **TBNOTIFY** -Struktur. Das **iItem** -Member enthält den nullbasierten Index der gezogenen Schaltfläche. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_GETBUTTONINFO**

   Wird gesendet, wenn der Benutzer ein Symbolleisten-Steuerelement anpasst. Die Symbolleiste verwendet diese Benachrichtigungsmeldung zum Abrufen von Informationen, die vom Dialogfeld „Symbolleiste anpassen“ benötigt werden. Der Zeiger verweist auf eine **TBNOTIFY** -Struktur. Das **iItem** -Member gibt den nullbasierten Index einer Schaltfläche an. Die Member **pszText** und **cchText** geben die Adresse und die Länge des aktuellen Schaltflächentexts in Zeichen an. Eine Anwendung sollte die Struktur mit Informationen über die Schaltfläche auffüllen. Gibt **TRUE** zurück, wenn Schaltflächeninformationen in die Struktur kopiert wurden, andernfalls **FALSE** .

- **TBN_QUERYDELETE**

   Wird gesendet, während der Benutzer eine Symbolleiste anpasst, um zu bestimmen, ob eine Schaltfläche aus einem Symbolleisten-Steuerelement gelöscht werden kann. Der Zeiger verweist auf eine **TBNOTIFY** -Struktur. Das **iItem** -Member enthält den nullbasierten Index der zu löschenden Schaltfläche. Gibt **TRUE** zurück, um das Löschen der Schaltfläche zu erlauben oder **FALSE** , um das Löschen der Schaltfläche zu verhindern.

- **TBN_QUERYINSERT**

   Wird gesendet, während der Benutzer ein ToolBar-Steuerelement anpasst, um zu bestimmen, ob links neben der angegebenen Schaltfläche eine Schaltfläche eingefügt werden kann. Der Zeiger verweist auf eine **TBNOTIFY** -Struktur. Das **iItem** -Member enthält den nullbasierten Index der einzufügenden Schaltfläche. Gibt **TRUE** zurück, um das Einfügen einer Schaltfläche vor der vorhandenen Schaltfläche zu erlauben oder **FALSE** , um das Einfügen der Schaltfläche zu verhindern.

- **TBN_RESET**

   Wird gesendet, wenn der Benutzer den Inhalt des Dialog Felds Symbolleiste anpassen zurücksetzt. Der Zeiger verweist auf eine **NMHDR** -Struktur, die Informationen über die Benachrichtigungsmeldung enthält. Der Handler muss keinen bestimmten Wert zurückgeben.

- **TBN_TOOLBARCHANGE**

   Wird gesendet, nachdem der Benutzer ein Symbolleisten-Steuerelement angepasst hat. Der Zeiger verweist auf eine **NMHDR** -Struktur, die Informationen über die Benachrichtigungsmeldung enthält. Der Handler muss keinen bestimmten Wert zurückgeben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
