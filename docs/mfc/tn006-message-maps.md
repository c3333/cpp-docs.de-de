---
title: 'TN006: Meldungszuordnungen'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: 6b387b851f5a76cd0d11957a87e57307d624759e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228530"
---
# <a name="tn006-message-maps"></a>TN006: Meldungszuordnungen

In diesem Hinweis wird die MFC-Nachrichten Zuordnungs Funktion beschrieben.

## <a name="the-problem"></a>Problemstellung

Microsoft Windows implementiert virtuelle Funktionen in Fenster Klassen, die seine Messaging Funktion verwenden. Aufgrund der großen Anzahl von Nachrichten würde das Bereitstellen einer separaten virtuellen Funktion für jede Windows-Nachricht eine sehr große Vtable-Tabelle erstellen.

Da sich die Anzahl der System definierten Windows-Meldungen im Laufe der Zeit ändert, und da Anwendungen ihre eigenen Windows-Meldungen definieren können, stellen Meldungs Zuordnungen eine Dereferenzierungsebene dar, die verhindert, dass Schnittstellen Änderungen vorhandenen Code unterbrechen.

## <a name="overview"></a>Übersicht

MFC stellt eine Alternative zu der Switch-Anweisung dar, die in herkömmlichen Windows-basierten Programmen verwendet wurde, um an ein Fenster gesendete Nachrichten zu verarbeiten. Eine Zuordnung von Nachrichten zu Methoden kann so definiert werden, dass die entsprechende Methode automatisch aufgerufen wird, wenn eine Nachricht von einem Fenster empfangen wird. Diese Nachrichten Zuordnungs Funktion ist so konzipiert, dass Sie virtuellen Funktionen ähnelt, bietet jedoch zusätzliche Vorteile, die mit C++ Virtual Functions nicht möglich sind.

## <a name="defining-a-message-map"></a>Definieren einer Meldungs Zuordnung

Das [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) -Makro deklariert drei Member für eine Klasse.

- Ein privates Array von AFX_MSGMAP_ENTRY Einträgen, die *_messageEntries*genannt werden.

- Eine geschützte AFX_MSGMAP Struktur namens " *messagemap* ", die auf das *_messageEntries* Array zeigt.

- Eine geschützte virtuelle Funktion `GetMessageMap` mit dem Namen, die die Adresse von *messagemap*zurückgibt.

Dieses Makro sollte in der Deklaration einer beliebigen Klasse mithilfe von Meldungs Zuordnungen abgelegt werden. Gemäß der Konvention befindet er sich am Ende der Klassen Deklaration. Beispiel:

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

Dies ist das Format, das von AppWizard und ClassWizard bei der Erstellung neuer Klassen generiert wird. Die Klammern//{{und//}} sind für den Klassen-Assistenten erforderlich.

Die Tabelle der Meldungs Zuordnung wird mithilfe einer Reihe von Makros definiert, die zu Meldungs Zuordnungs Einträgen erweitert werden. Eine Tabelle beginnt mit einem [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) Makro-Befehl, der die von dieser Meldungs Zuordnung behandelte Klasse definiert, und die übergeordnete Klasse, an die nicht behandelte Nachrichten übermittelt werden. Die Tabelle endet mit dem [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) -Makro-Befehl.

Zwischen diesen beiden Makro aufrufen handelt es sich um einen Eintrag für jede Nachricht, die von dieser Meldungs Zuordnung behandelt werden soll. Jede standardmäßige Windows-Nachricht verfügt über ein Makro der Form ON_WM_*MESSAGE_NAME* , die einen Eintrag für diese Nachricht generiert.

Eine Standard Funktions Signatur wurde definiert, um die Parameter der einzelnen Windows-Meldungen zu entpacken und Typsicherheit bereitzustellen. Diese Signaturen befinden sich möglicherweise in der Datei "AFXWIN. h" in der Deklaration von [CWnd](../mfc/reference/cwnd-class.md). Jede ist mit dem Schlüsselwort **afx_msg** für die einfache Identifikation gekennzeichnet.

> [!NOTE]
> Der ClassWizard erfordert, dass Sie das **afx_msg** -Schlüsselwort in den Deklarationen der Message Map-Handler verwenden.

Diese Funktions Signaturen wurden mithilfe einer einfachen Konvention abgeleitet. Der Name der Funktion beginnt immer mit `"On` ". Danach folgt der Name der Windows-Meldung mit dem "WM_" entfernt und der erste Buchstabe jedes Worts in Großbuchstaben. Die Reihenfolge der Parameter ist *wParam* , gefolgt von `LOWORD` (*LPARAM*) und dann `HIWORD` (*LPARAM*). Nicht verwendete Parameter werden nicht übermittelt. Alle Handles, die von MFC-Klassen umschließt werden, werden in Zeiger auf die entsprechenden MFC-Objekte konvertiert. Im folgenden Beispiel wird gezeigt, wie die WM_PAINT Nachricht behandelt und bewirkt `CMyWnd::OnPaint` wird, dass die Funktion aufgerufen wird:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Die Nachrichten Zuordnungs Tabelle muss außerhalb des Gültigkeits Bereichs einer beliebigen Funktions-oder Klassendefinition definiert werden. Er sollte nicht in einem externen "C"-Block abgelegt werden.

> [!NOTE]
> Der Klassen-Assistent ändert die Meldungs Zuordnungs Einträge, die zwischen der Kommentar Klammer//{{und//}} auftreten.

## <a name="user-defined-windows-messages"></a>Benutzerdefinierte Windows-Meldungen

Benutzerdefinierte Meldungen können mithilfe des [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) -Makros in einer Meldungs Zuordnung enthalten sein. Dieses Makro akzeptiert eine Nachrichtennummer und eine Methode in der folgenden Form:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

In diesem Beispiel erstellen wir einen Handler für eine benutzerdefinierte Nachricht, die über eine aus der Standard WM_USER Basis für benutzerdefinierte Nachrichten abgeleitete Windows-Meldungs-ID verfügt. Im folgenden Beispiel wird gezeigt, wie dieser Handler aufgerufen wird:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Der Bereich von benutzerdefinierten Nachrichten, die diesen Ansatz verwenden, muss im Bereich von WM_USER bis 0x7FFF liegen.

> [!NOTE]
> Der Klassen-Assistent unterstützt nicht die Eingabe von ON_MESSAGE Handlerroutinen von der ClassWizard-Benutzeroberfläche. Sie müssen Sie manuell aus dem Visual C++-Editor eingeben. Der Klassen Assistent analysiert diese Einträge und ermöglicht Ihnen, Sie wie alle anderen Meldungs Zuordnungs Einträge zu durchsuchen.

## <a name="registered-windows-messages"></a>Registrierte Windows-Meldungen

Die [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) -Funktion wird verwendet, um eine neue Fenster Meldung zu definieren, die im gesamten System eindeutig ist. Das Makro ON_REGISTERED_MESSAGE wird verwendet, um diese Nachrichten zu verarbeiten. Dieses Makro akzeptiert den Namen einer *uint-near* -Variablen, die die registrierte Windows-Nachrichten-ID enthält. Beispiel:

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Die registrierte Variablen der Windows-Meldungs-ID (in diesem Beispiel WM_FIND) muss eine *near* -Variable sein, da ON_REGISTERED_MESSAGE implementiert ist.

Der Bereich von benutzerdefinierten Nachrichten, die diesen Ansatz verwenden, liegt im Bereich von 0xc000 bis 0xFFFF.

> [!NOTE]
> Der Klassen-Assistent unterstützt nicht die Eingabe von ON_REGISTERED_MESSAGE Handlerroutinen von der ClassWizard-Benutzeroberfläche. Sie müssen Sie manuell aus dem Text-Editor eingeben. Der Klassen Assistent analysiert diese Einträge und ermöglicht Ihnen, Sie wie alle anderen Meldungs Zuordnungs Einträge zu durchsuchen.

## <a name="command-messages"></a>Befehlsmeldungen

Befehls Meldungen aus Menüs und Acceleratoren werden in Meldungs Zuordnungen mit dem ON_COMMAND-Makro behandelt. Dieses Makro akzeptiert eine Befehls-ID und eine-Methode. Nur die spezifische WM_COMMAND Nachricht, die einen *wParam* -Wert aufweist, der der angegebenen Befehls-ID entspricht, wird von der im Message Map-Eintrag angegebenen Methode behandelt. Befehlshandlermember-Funktionen akzeptieren keine Parameter und geben zurück **`void`** . Das-Makro hat die folgende Form:

```cpp
ON_COMMAND(id, memberFxn)
```

Befehls Aktualisierungs Meldungen werden durch denselben Mechanismus weitergeleitet, verwenden jedoch stattdessen das ON_UPDATE_COMMAND_UI-Makro. Member des Befehls Aktualisierungs Handlers akzeptieren einen einzelnen Parameter, einen Zeiger auf ein [CCmdUI](../mfc/reference/ccmdui-class.md) -Objekt und geben zurück **`void`** . Das Makro hat das Formular.

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Erweiterte Benutzer können das ON_COMMAND_EX-Makro verwenden, bei dem es sich um eine erweiterte Form von befehlsnachrichten Handlern handelt. Das-Makro stellt eine supermenge der ON_COMMAND Funktionen bereit. Erweiterte befehlshandlermember-Funktionen akzeptieren einen einzelnen Parameter, einen **uint** , der die Befehls-ID enthält, und geben einen **booleschen**Wert zurück. Der Rückgabewert sollte **true** sein, um anzugeben, dass der Befehl behandelt wurde. Andernfalls wird das Routing mit anderen Befehls Ziel Objekten fortgesetzt.

Beispiele für diese Formen:

- In Resource. h (in der Regel durch Visual C++ generiert)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- Innerhalb der Klassen Deklaration

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- Innerhalb der Nachrichten Zuordnungs Definition

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- In der Implementierungs Datei

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

Erweiterte Benutzer können eine Reihe von Befehlen mithilfe eines einzelnen Befehls Handlers verarbeiten: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) oder ON_COMMAND_RANGE_EX. Weitere Informationen zu diesen Makros finden Sie in der Produktdokumentation.

> [!NOTE]
> Der Klassen-Assistent unterstützt das Erstellen von ON_COMMAND-und ON_UPDATE_COMMAND_UI Handlern, aber das Erstellen von ON_COMMAND_EX oder ON_COMMAND_RANGE Handlern wird nicht unterstützt. Der Klassen-Assistent analysiert jedoch alle vier befehlshandlervarianten und lässt Sie durchsuchen.

## <a name="control-notification-messages"></a>Steuern von Benachrichtigungs Meldungen

Nachrichten, die von untergeordneten Steuerelementen an ein Fenster gesendet werden, haben in Ihrem Meldungs Zuordnungs Eintrag zusätzliche Informationen: die ID des Steuer Elements. Der in einem Meldungs Zuordnungs Eintrag angegebene Nachrichten Handler wird nur aufgerufen, wenn die folgenden Bedingungen zutreffen:

- Der Steuerelement Benachrichtigungs Code (hohes Wort von *LPARAM*), wie z. b. BN_CLICKED, entspricht dem im Meldungs Zuordnungs Eintrag angegebenen Benachrichtigungs Code.

- Die Steuerelement-ID (*wParam*) entspricht der im Message-Map-Eintrag angegebenen Steuerelement-ID.

Benutzerdefinierte Steuerelement-Benachrichtigungs Meldungen können mithilfe des [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) -Makros einen Meldungs Zuordnungs Eintrag mit einem benutzerdefinierten Benachrichtigungs Code definieren. Dieses Makro hat das Formular.

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Für erweiterte Verwendungs [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) kann verwendet werden, um eine bestimmte Steuerelement Benachrichtigung von einem Bereich von Steuerelementen mit demselben Handler zu verarbeiten.

> [!NOTE]
> Der Klassen-Assistent unterstützt nicht das Erstellen eines ON_CONTROL oder ON_CONTROL_RANGE Handlers in der Benutzeroberfläche. Sie müssen Sie manuell mit dem Text-Editor eingeben. Der Klassen-Assistent analysiert diese Einträge und ermöglicht Ihnen, Sie wie alle anderen Zuordnungs Einträge in der Nachricht zu durchsuchen.

Die allgemeinen Windows-Steuerelemente verwenden die leistungsfähigere [WM_NOTIFY](/windows/win32/controls/wm-notify) für komplexe Steuerelement Benachrichtigungen. Diese MFC-Version bietet direkte Unterstützung für diese neue Nachricht mithilfe der ON_NOTIFY-und ON_NOTIFY_RANGE-Makros. Weitere Informationen zu diesen Makros finden Sie in der Produktdokumentation.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
