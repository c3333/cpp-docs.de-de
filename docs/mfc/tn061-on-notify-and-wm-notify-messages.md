---
title: 'TN061: ON_NOTIFY- und WM_NOTIFY-Meldungen'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366595"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: ON_NOTIFY- und WM_NOTIFY-Meldungen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser technische Hinweis enthält Hintergrundinformationen zur neuen WM_NOTIFY Nachricht und beschreibt die empfohlene (und häufigste) Methode zur Behandlung von WM_NOTIFY Nachrichten in Ihrer MFC-Anwendung.

**Benachrichtigungen in Windows 3.x**

In Windows 3.x benachrichtigen Steuerelemente ihre übergeordneten Elemente über Ereignisse wie Mausklicks, Änderungen an Inhalt und Auswahl, und steuern die Hintergrundmalerei, indem sie eine Nachricht an das übergeordnete Element senden. Einfache Benachrichtigungen werden als spezielle WM_COMMAND Nachrichten gesendet, wobei der Benachrichtigungscode (z. B. BN_CLICKED) und die Steuer-ID in *wParam* und das Handle des Steuerelements in *lParam*gepackt werden. Beachten Sie, dass, da *wParam* und *lParam* voll sind, es keine Möglichkeit gibt, zusätzliche Daten zu übergeben – diese Nachrichten können nur eine einfache Benachrichtigung sein. In der BN_CLICKED Benachrichtigung gibt es beispielsweise keine Möglichkeit, Informationen über die Position des Mauszeigers zu senden, wenn auf die Schaltfläche geklickt wurde.

Wenn Steuerelemente in Windows 3.x eine Benachrichtigung senden müssen, die zusätzliche Daten enthält, verwenden sie eine Vielzahl von speziellen Nachrichten, einschließlich WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM usw. Diese Meldungen können an das Steuerelement zurückgesendet werden, das sie gesendet hat. Weitere Informationen finden Sie unter [TN062: Nachrichtenreflexion für Windows-Steuerelemente](../mfc/tn062-message-reflection-for-windows-controls.md).

**Benachrichtigungen in Win32**

Bei Steuerelementen, die in Windows 3.1 vorhanden waren, verwendet die Win32-API die meisten Benachrichtigungen, die in Windows 3.x verwendet wurden. Win32 fügt jedoch auch eine Reihe von ausgeklügelten, komplexen Steuerelementen zu den in Windows 3.x unterstützten Steuerelementen hinzu. Häufig müssen diese Steuerelemente zusätzliche Daten mit ihren Benachrichtigungen senden. Anstatt für jede neue Benachrichtigung, die zusätzliche Daten benötigt, eine neue **WM_** <strong>\*</strong> Nachricht hinzuzufügen, haben die Designer der Win32-API nur eine Nachricht hinzugefügt, WM_NOTIFY, die eine beliebige Menge zusätzlicher Daten auf standardisierte Weise übergeben kann.

WM_NOTIFY Nachrichten enthalten die ID des Steuerelements, das die Nachricht in *wParam* sendet, und einen Zeiger auf eine Struktur in *lParam*. Diese Struktur ist entweder eine **NMHDR-Struktur** oder eine größere Struktur, die eine **NMHDR-Struktur** als erstes Element hat. Beachten Sie, dass, da das **NMHDR-Member** zuerst ist, ein Zeiger auf diese Struktur entweder als Zeiger auf eine **NMHDR** oder als Zeiger auf die größere Struktur verwendet werden kann, je nachdem, wie Sie sie umwerfen.

In den meisten Fällen weist der Zeiger auf eine größere Struktur hin, und Sie müssen ihn umwerfen, wenn Sie ihn verwenden. In nur wenigen Benachrichtigungen, wie z. B. den allgemeinen Benachrichtigungen (deren Namen mit **NM_** beginnen) und der TTN_SHOW- und TTN_POP Benachrichtigungen des Tooltipp-Steuerelements, wird tatsächlich eine **NMHDR-Struktur** verwendet.

Die **NMHDR-Struktur** oder das ursprüngliche Element enthält das Handle und die ID des Steuerelements, das die Nachricht sendet, und den Benachrichtigungscode (z. B. TTN_SHOW). Das Format der **NMHDR-Struktur** ist unten dargestellt:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Bei einer TTN_SHOW Nachricht wird der **Codemember** auf TTN_SHOW festgelegt.

Die meisten Benachrichtigungen übergeben einen Zeiger an eine größere Struktur, die eine **NMHDR-Struktur** als erstes Element enthält. Betrachten Sie beispielsweise die Struktur, die vom LVN_KEYDOWN Benachrichtigungsmeldung des Listenansichtssteuerelements verwendet wird, die gesendet wird, wenn eine Taste in einem Listenansichtssteuerelement gedrückt wird. Der Zeiger zeigt auf eine **LV_KEYDOWN** Struktur, die wie unten dargestellt definiert ist:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Beachten Sie, dass der Zeiger, der in der Benachrichtigung übergeben wird, entweder in einen Zeiger auf einen **NMHDR** oder auf einen Zeiger auf eine **LV_KEYDOWN**, umzuwerfen, da das **NMHDR-Member** an erster Stelle in dieser Struktur steht.

**Alle neuen Windows-Steuerelemente gemeinsam**

Einige Benachrichtigungen sind allen neuen Windows-Steuerelementen gemeinsam. Diese Benachrichtigungen übergeben einen Zeiger auf eine **NMHDR-Struktur.**

|Benachrichtigungscode|Gesendet, weil|
|-----------------------|------------------|
|NM_CLICK|Benutzer klickte linke Maustaste im Steuerelement|
|NM_DBLCLK|Benutzer doppelgeklickt linke Maustaste im Steuerelement|
|NM_RCLICK|Benutzer klickte mit der rechten Maustaste im Steuerelement|
|NM_RDBLCLK|Benutzer doppelgeklickt rechte Maustaste im Steuerelement|
|NM_RETURN|Benutzer drückte die ENTER-Taste, während das Steuerelement Eingabefokus hat|
|NM_SETFOCUS|Die Steuerung wurde in den Eingangsfokus|
|NM_KILLFOCUS|Steuerung hat Deninfokus verloren|
|NM_OUTOFMEMORY|Die Steuerung konnte einen Vorgang nicht abschließen, da nicht genügend Arbeitsspeicher verfügbar war.|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: Umgang mit WM_NOTIFY Nachrichten in MFC-Anwendungen

Die `CWnd::OnNotify` Funktion verarbeitet Benachrichtigungen. Die Standardimplementierung überprüft die Nachrichtenzuordnung, damit Benachrichtigungshandler aufrufen. Im Allgemeinen überschreiben `OnNotify`Sie nicht . Stattdessen stellen Sie eine Handlerfunktion bereit und fügen der Nachrichtenzuordnungsklasse der Klasse des Besitzerfensters einen Nachrichtenzuordnungseintrag für diesen Handler hinzu.

ClassWizard kann über das ClassWizard-Eigenschaftenblatt den ON_NOTIFY Message-Map-Eintrag erstellen und Ihnen eine Skeletthandlerfunktion bereitstellen. Weitere Informationen zur Verwendung von ClassWizard, um dies zu vereinfachen, finden Sie unter [Zuordnen von Nachrichten zu Funktionen](../mfc/reference/mapping-messages-to-functions.md).

Das ON_NOTIFY Message-Map-Makro hat die folgende Syntax:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

mit folgenden Parametern:

*wNotifyCode*<br/>
Der Code für die zu behandelnde Benachrichtigung, z. B. LVN_KEYDOWN.

*id*<br/>
Der untergeordnete Bezeichner des Steuerelements, für das die Benachrichtigung gesendet wird.

*MemberFxn*<br/>
Die Memberfunktion, die aufgerufen werden soll, wenn diese Benachrichtigung gesendet wird.

Ihre Memberfunktion muss mit dem folgenden Prototyp deklariert werden:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

mit folgenden Parametern:

*pNotifyStruct*<br/>
Ein Zeiger auf die Benachrichtigungsstruktur, wie im obigen Abschnitt beschrieben.

*result*<br/>
Ein Zeiger auf den Ergebniscode, den Sie vor der Rückgabe festlegen.

## <a name="example"></a>Beispiel

Um anzugeben, dass die `OnKeydownList1` Memberfunktion LVN_KEYDOWN `CListCtrl` Nachrichten behandeln `IDC_LIST1`soll, deren ID lautet , verwenden Sie ClassWizard, um der Nachrichtenzuordnung Folgendes hinzuzufügen:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Im obigen Beispiel lautet die von ClassWizard bereitgestellte Funktion:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Beachten Sie, dass ClassWizard automatisch einen Zeiger des richtigen Typs bereitstellt. Sie können auf die Benachrichtigungsstruktur entweder über *pNMHDR* oder *pLVKeyDow*zugreifen.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Wenn Sie dieselbe WM_NOTIFY Nachricht für eine Reihe von Steuerelementen verarbeiten müssen, können Sie ON_NOTIFY_RANGE anstelle ON_NOTIFY verwenden. Sie verfügen beispielsweise über eine Reihe von Schaltflächen, für die Sie dieselbe Aktion für eine bestimmte Benachrichtigung ausführen möchten.

Wenn Sie ON_NOTIFY_RANGE verwenden, geben Sie einen zusammenhängenden Bereich von untergeordneten Bezeichnern an, für die die Benachrichtigung behandelt werden soll, indem Sie den Anfangs- und Endbezeichner des Bereichs angeben.

ClassWizard behandelt ON_NOTIFY_RANGE nicht. Um sie verwenden zu können, müssen Sie Ihre Nachrichtenzuordnung selbst bearbeiten.

Der Nachrichtenkarteneintrag und der Funktionsprototyp für ON_NOTIFY_RANGE lauten wie folgt:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

mit folgenden Parametern:

*wNotifyCode*<br/>
Der Code für die zu behandelnde Benachrichtigung, z. B. LVN_KEYDOWN.

*id*<br/>
Der erste Bezeichner im zusammenhängenden Bezeichnerbereich.

*idLast*<br/>
Der letzte Bezeichner im zusammenhängenden Bezeichnerbereich.

*MemberFxn*<br/>
Die Memberfunktion, die aufgerufen werden soll, wenn diese Benachrichtigung gesendet wird.

Ihre Memberfunktion muss mit dem folgenden Prototyp deklariert werden:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

mit folgenden Parametern:

*id*<br/>
Der untergeordnete Bezeichner des Steuerelements, das die Benachrichtigung gesendet hat.

*pNotifyStruct*<br/>
Ein Zeiger auf die Benachrichtigungsstruktur, wie oben beschrieben.

*result*<br/>
Ein Zeiger auf den Ergebniscode, den Sie vor der Rückgabe festlegen.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Wenn mehr als ein Objekt im Benachrichtigungsrouting eine Nachricht verarbeiten soll, können Sie ON_NOTIFY_EX (oder ON_NOTIFY_EX_RANGE) anstelle von ON_NOTIFY (oder ON_NOTIFY_RANGE) verwenden. Der einzige Unterschied zwischen der **EX-Version** und der regulären Version besteht darin, dass die für die **EX-Version** aufgerufene Memberfunktion eine **BOOL** zurückgibt, die angibt, ob die Nachrichtenverarbeitung fortgesetzt werden soll. Wenn Sie **FALSE** von dieser Funktion zurückgeben, können Sie dieselbe Nachricht in mehr als einem Objekt verarbeiten.

ClassWizard verarbeitet ON_NOTIFY_EX oder ON_NOTIFY_EX_RANGE nicht. Wenn Sie eine der beiden Verwenden möchten, müssen Sie Ihre Nachrichtenzuordnung selbst bearbeiten.

Der Message-Map-Eintrag und der Funktionsprototyp für ON_NOTIFY_EX und ON_NOTIFY_EX_RANGE sind wie folgt. Die Bedeutungen der Parameter sind die gleichen**EX** wie bei den Nicht-EX-Versionen.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Der Prototyp für beide oben ist derselbe:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

In beiden Fällen enthält *id* den untergeordneten Bezeichner des Steuerelements, das die Benachrichtigung gesendet hat.

Ihre Funktion muss **TRUE** zurückgeben, wenn die Benachrichtigung vollständig verarbeitet wurde, oder **FALSE,** wenn andere Objekte im Befehlsrouting die Möglichkeit haben sollten, die Nachricht zu verarbeiten.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
