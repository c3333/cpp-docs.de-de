---
title: Meldungszuordnungsmakros (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: e0980a5c00459b9f166296b7436d013bb8a42319
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231779"
---
# <a name="message-map-macros-mfc"></a>Meldungszuordnungsmakros (MFC)

Um Nachrichten Zuordnungen zu unterstützen, stellt MFC die folgenden Makros bereit:

### <a name="message-map-declaration-and-demarcation-macros"></a>Message-Map-Deklaration und-Abgrenzungs Makros

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklariert, dass eine Meldungs Zuordnung in einer Klasse verwendet wird, um Nachrichten zu Funktionen zuzuordnen (muss in der Klassen Deklaration verwendet werden).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Beginnt die Definition einer Meldungs Zuordnung (muss in der Klassen Implementierung verwendet werden).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Beginnt die Definition einer Meldungs Zuordnung für einen Klassentyp, der ein einzelnes Vorlagen Argument enthält. |
|[END_MESSAGE_MAP](#end_message_map)|Beendet die Definition einer Meldungs Zuordnung (muss in der Klassen Implementierung verwendet werden).|

### <a name="message-mapping-macros"></a>Nachrichten Zuordnungs Makros

|||
|-|-|
|[ON_COMMAND](#on_command)|Gibt an, welche Funktion eine angegebene Befehls Meldung behandelt.|
|[ON_COMMAND_EX](#on_command_ex)|Gibt an, welche Funktion eine angegebene Befehls Meldung behandelt.|
|[ON_CONTROL](#on_control)|Gibt an, welche Funktion eine angegebene Steuerelement Benachrichtigungs Meldung behandelt.|
|[ON_MESSAGE](#on_message)|Gibt an, welche Funktion eine benutzerdefinierte Meldung behandelt.|
|[ON_OLECMD](#on_olecmd)|Gibt an, welche Funktion einen Menübefehl aus einem DocObject-Objekt oder dessen Container behandelt.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Gibt an, welche Funktion eine registrierte benutzerdefinierte Meldung behandelt.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Gibt an, welche Funktion eine registrierte benutzerdefinierte Meldung behandelt, wenn Sie über eine- `CWinThread` Klasse verfügen.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Gibt an, welche Funktion eine benutzerdefinierte Meldung behandelt, wenn Sie über eine- `CWinThread` Klasse verfügen.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Gibt an, welche Funktion eine angegebene Benutzeroberflächen-Aktualisierungs Befehls Meldung behandelt.|

### <a name="message-map-range-macros"></a>Nachrichten Zuordnungs Bereich-Makros

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Gibt an, welche Funktion den Bereich der Befehls-IDs behandelt, die in den ersten beiden Parametern für das Makro angegeben sind.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Gibt an, welcher Update Handler den Bereich der Befehls-IDs behandelt, die in den ersten beiden Parametern für das Makro angegeben sind.|
|[ON_CONTROL_RANGE](#on_control_range)|Gibt an, welche Funktion Benachrichtigungen aus dem Bereich von Steuerelement-IDs verarbeitet, die im zweiten und dritten Parameter für das Makro angegeben werden. Der erste Parameter ist eine Steuerelement Benachrichtigungs Meldung, wie z. b. BN_CLICKED.|

Weitere Informationen zu Meldungs Zuordnungen, der Nachrichten Zuordnungs Deklaration und den Abgrenzungs Makros sowie den Nachrichten Zuordnungs Makros finden Sie unter [Nachrichten](../../mfc/reference/message-maps-mfc.md) Zuordnungen und [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md). Weitere Informationen zu Nachrichten Zuordnungs Bereichen finden Sie unter [Handler für](../../mfc/handlers-for-message-map-ranges.md)Meldungs Zuordnungs Bereiche.

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Beginnt die Definition der Meldungs Zuordnung.

### <a name="syntax"></a>Syntax

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Klasse an, deren Meldungs Zuordnung ist.

*BaseClass*<br/>
Gibt den Namen der Basisklasse von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungs Datei (CPP-Datei), in der die Element Funktionen für die Klasse definiert sind, die Meldungs Zuordnung mit dem BEGIN_MESSAGE_MAP-Makro, fügen Sie anschließend Makro Einträge für jede Ihrer nachrichtenhandlerfunktionen hinzu, und vervollständigen Sie die Meldungs Zuordnung mit dem END_MESSAGE_MAP-Makro.

Weitere Informationen zu Meldungs Zuordnungen finden Sie unter [Message Maps](message-maps-mfc.md) .

### <a name="example"></a>Beispiel

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Beginnt die Definition einer Meldungs Zuordnung für einen Klassentyp, der ein einzelnes Vorlagen Argument enthält.

### <a name="syntax"></a>Syntax

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Klasse an, deren Meldungs Zuordnung ist.

*type_name*<br/>
Der Name des für die-Klasse angegebenen Vorlagen Parameters.

*BaseClass*<br/>
Gibt den Namen der Basisklasse von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

Dieses Makro ähnelt dem [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) -Makro. Dieses Makro ist jedoch für Klassen vorgesehen, die ein einzelnes Vorlagen Argument enthalten.

Starten Sie im Abschnitt zur Methoden Implementierung der-Klasse die Meldungs Zuordnung mit dem BEGIN_TEMPLATE_MESSAGE_MAP-Makro. Fügen Sie anschließend Makro Einträge für jede Ihrer nachrichtenhandlermethoden hinzu, wie dies für eine standardmäßige Meldungs Zuordnung der Fall wäre. Vervollständigen Sie wie beim BEGIN_MESSAGE_MAP-Makro die Vorlage für die Vorlagen Nachricht mit dem [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) -Makro.

Weitere Informationen zum Implementieren von Meldungs Zuordnungen für Vorlagen Klassen finden Sie unter Gewusst [wie: Erstellen einer Meldungs Zuordnung für eine Vorlagen Klasse](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklariert, dass die-Klasse eine Meldungs Zuordnung definiert. Jede `CCmdTarget` von abgeleitete Klasse in Ihrem Programm muss eine Meldungs Zuordnung für die Verarbeitung von Nachrichten bereitstellen.

### <a name="syntax"></a>Syntax

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_MESSAGE_MAP-Makro am Ende der Klassen Deklaration. Verwenden Sie dann in der CPP-Datei, die die-Member-Funktionen für die-Klasse definiert, das BEGIN_MESSAGE_MAP Makro, Makro Einträge für jede der Nachrichten Handler-Funktionen und das END_MESSAGE_MAP-Makro.

> [!NOTE]
> Wenn Sie nach DECLARE_MESSAGE_MAP einen Member deklarieren, müssen Sie einen neuen Zugriffstyp ( **`public`** , **`private`** oder **`protected`** ) für Sie angeben.

Weitere Informationen zu Meldungs Zuordnungen und zum DECLARE_MESSAGE_MAP-Makro finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Beendet die Definition der Meldungs Zuordnung.

### <a name="syntax"></a>Syntax

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Meldungs Zuordnungen und zum END_MESSAGE_MAP-Makro finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

Dieses Makro ordnet eine Befehls Meldung einer Member-Funktion zu.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parameter

*commandId*<br/>
Die Befehls-ID.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Gibt an, welche Funktion eine Befehls Meldung von einem Befehls Benutzeroberflächen Objekt behandelt, z. b. einem Menü Element oder einer Symbolleisten Schaltfläche.

Wenn ein Befehls Zielobjekt eine Windows WM_COMMAND-Nachricht mit der angegebenen ID empfängt, ruft ON_COMMAND die Member-Funktion `memberFxn` auf, um die Nachricht zu verarbeiten.

Verwenden Sie ON_COMMAND, um einer Element Funktion einen einzelnen Befehl zuzuordnen. Verwenden Sie [ON_COMMAND_RANGE](#on_command_range) , um einer Element Funktion einen Bereich von Befehls-IDs zuzuordnen. Nur ein Nachrichten Zuordnungs Eintrag kann mit einer angegebenen Befehls-ID verglichen werden. Das heißt, Sie können einen Befehl nicht mehreren Handlern zuordnen. Weitere Informationen und Beispiele finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Erweiterte befehlshandlermember-Funktion.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parameter

*commandId*<br/>
Die Befehls-ID.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Eine erweiterte Form von Befehls Meldungs Handlern ist für erweiterte Verwendungszwecke verfügbar. Das ON_COMMAND_EX-Makro wird für solche Meldungs Handler verwendet und stellt eine supermenge der [ON_COMMAND](message-map-macros-mfc.md#on_command) Funktionen bereit. Erweiterte befehlshandlermember-Funktionen akzeptieren einen einzelnen Parameter, einen uint, der die Befehls-ID enthält, und geben einen booleschen Wert zurück. Der Rückgabewert sollte true sein, um anzugeben, dass der Befehl behandelt wurde. Andernfalls wird das Routing mit anderen Befehls Ziel Objekten fortgesetzt.

Weitere Informationen finden Sie unter Technischer Hinweis [TN006: Message Maps] tm006-Message-Maps.MD).

### <a name="requirements"></a>Requirements (Anforderungen)

Header Datei: afxmsg_. h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Gibt an, welche Funktion eine benutzerdefinierte Benachrichtigungs Meldung behandelt.

### <a name="syntax"></a>Syntax

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parameter

*wnotifycode schalten*<br/>
Der Benachrichtigungs Code des Steuer Elements.

*commandId*<br/>
Die Befehls-ID.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Steuerelement-Benachrichtigungs Meldungen werden von einem Steuerelement an das übergeordnete Fenster gesendet.

Es sollte genau eine ON_CONTROL Makro-Anweisung in der Meldungs Zuordnung für jede Benachrichtigungs Meldung angezeigt werden, die einer nachrichtenhandlerfunktion zugeordnet werden muss.

Weitere Informationen und Beispiele finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Gibt an, welche Funktion eine benutzerdefinierte Meldung behandelt.

### <a name="syntax"></a>Syntax

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Die Meldungs-ID.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der die Nachricht zugeordnet ist.

Der Typ der Funktion muss sein `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)` .

### <a name="remarks"></a>Bemerkungen

Benutzerdefinierte Meldungen sind Meldungen, bei denen es sich nicht um standardmäßige Windows-WM_MESSAGE Meldungen handelt. Wenn Sie eine Nachrichten-ID auswählen, müssen Sie Werte innerhalb des Bereichs von WM_USER (0x0400) bis 0x7FFF oder WM_APP (0X8000) bis 0xbfff verwenden. Weitere Informationen zu Nachrichten-IDs finden Sie unter [WM_APP](/windows/win32/winmsg/wm-app).

Es sollte genau eine ON_MESSAGE Makro-Anweisung in der Meldungs Zuordnung für jede benutzerdefinierte Nachricht vorhanden sein, die einer nachrichtenhandlerfunktion zugeordnet werden muss.

> [!NOTE]
> Zusätzlich zu benutzerdefinierten Meldungen verarbeitet ON_MESSAGE weniger häufige Windows-Meldungen. Weitere Informationen finden Sie unter [Message Maps](../../mfc/tn006-message-maps.md).

Weitere Informationen und Beispiele finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md) und [benutzerdefinierte Handler](user-defined-handlers.md) .

### <a name="example"></a>Beispiel

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Leitet Befehle über die Befehls Dispatchschnittstelle weiter `IOleCommandTarget` .

### <a name="syntax"></a>Syntax

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parameter

*pguid*<br/>
Der Bezeichner der Befehlsgruppe, zu der der Befehl gehört. Verwenden Sie für die Standardgruppe den Wert NULL.

*olecmdid*<br/>
Der Bezeichner des OLE-Befehls.

*commandId*<br/>
Menü-ID, Symbolleisten-ID, Schaltflächen-ID oder andere ID der Ressource oder des Objekts, das den Befehl ausgibt.

### <a name="remarks"></a>Bemerkungen

`IOleCommandTarget`ermöglicht einem Container das Empfangen von Befehlen, die aus der Benutzeroberfläche eines DocObject stammen, und ermöglicht es dem Container, dieselben Befehle zu senden (z. b. New, Open, SaveAs und Print im Menü Datei) und in ein DocObject-Objekt zu kopieren, einzufügen, rückgängig zu machen usw.

`IOleCommandTarget`ist einfacher als OLE-Automatisierung `IDispatch` . `IOleCommandTarget`basiert vollständig auf einem Standardsatz von Befehlen, die nur selten Argumente aufweisen, und es sind keine Typinformationen beteiligt (die Typsicherheit wird auch für Befehlsargumente verringert). Wenn Sie Befehle mit Argumenten versenden müssen, verwenden Sie [COleServerDoc:: onexecolecmd](coleserverdoc-class.md#onexecolecmd).

Die `IOleCommandTarget` Standardmenü Befehle wurden in den folgenden Makros von MFC implementiert:

**ON_OLECMD_CLEARSELECTION ()**

Sendet den Befehl "Clear bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY ()**

Sendet den Befehl zum Bearbeiten von Kopien. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT ()**

Sendet den Befehl "Ausschneiden bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW ()**

Sendet den Datei neuen Befehl. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN ()**

Sendet den Befehl zum Öffnen von Dateien. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP ()**

Sendet den Befehl "Datei Seite einrichten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE ()**

Sendet den Befehl "einfügen bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL ()**

Sendet den speziellen Befehl zum Einfügen von "Einfügen". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT ()**

Sendet den File Print-Befehl. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW ()**

Sendet den Befehl Datei Druckvorschau. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO ()**

Sendet den Befehl "wiederholen bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE ()**

Sendet den Befehl zum Speichern von Dateien. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS ()**

Sendet den file-Befehl "Speichern unter". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS ()**

Sendet den Datei Kopiervorgang als Befehl. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL ()**

Sendet den Befehl Select All (alle auswählen). Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO ()**

Sendet den Befehl "rückgängig bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdocob. h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Die Windows- `RegisterWindowMessage` Funktion wird verwendet, um eine neue Fenster Meldung zu definieren, die im gesamten System eindeutig ist.

### <a name="syntax"></a>Syntax

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parameter

*nmessagevariable*<br/>
Die registrierte Window-Message-ID-Variable.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Dieses Makro gibt an, welche Funktion die registrierte Nachricht behandelt.

Weitere Informationen und Beispiele finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Gibt an, welche Funktion die von der Windows RegisterWindowMessage-Funktion registrierte Nachricht behandelt.

### <a name="syntax"></a>Syntax

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parameter

*nmessagevariable*<br/>
Die registrierte Window-Message-ID-Variable.

*Mitgliedschaft*<br/>
Der Name der CWinThread-Message-Handler-Funktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

RegisterWindowMessage wird verwendet, um eine neue Fenster Meldung zu definieren, die im gesamten System eindeutig ist. ON_REGISTERED_THREAD_MESSAGE müssen anstelle von ON_REGISTERED_MESSAGE verwendet werden, wenn Sie über eine CWinThread-Klasse verfügen.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Gibt an, welche Funktion eine benutzerdefinierte Meldung behandelt.

### <a name="syntax"></a>Syntax

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Die Meldungs-ID.

*Mitgliedschaft*<br/>
Der Name der `CWinThread` -Message-Handler-Funktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

ON_THREAD_MESSAGE müssen anstelle von ON_MESSAGE verwendet werden, wenn Sie über eine- `CWinThread` Klasse verfügen. Benutzerdefinierte Meldungen sind Meldungen, bei denen es sich nicht um standardmäßige Windows-WM_MESSAGE Meldungen handelt. Es sollte genau eine ON_THREAD_MESSAGE Makro-Anweisung in der Meldungs Zuordnung für jede benutzerdefinierte Nachricht vorhanden sein, die einer nachrichtenhandlerfunktion zugeordnet werden muss.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxole. h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Dieses Makro gibt an, welche Funktion eine Benutzeroberflächen-Aktualisierungs Befehlsnachricht behandelt.

### <a name="syntax"></a>Syntax

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parameter

*messageId*<br/>
Die Meldungs-ID.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Es sollte genau eine ON_UPDATE_COMMAND_UI Makro-Anweisung in der Meldungs Zuordnung für jeden Befehl zum Aktualisieren von Benutzeroberflächen vorhanden sein, der einer nachrichtenhandlerfunktion zugeordnet werden muss.

Weitere Informationen und Beispiele finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxole. h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

Verwenden Sie dieses Makro, um einen zusammenhängenden Bereich von Befehls-IDs einer einzelnen nachrichtenhandlerfunktion zuzuordnen.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Befehls-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Befehls-IDs.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Der Bereich der IDs beginnt mit *id1* und endet mit *id2*.

Verwenden Sie ON_COMMAND_RANGE, um einer Element Funktion einen Bereich von Befehls-IDs zuzuordnen. Verwenden Sie [ON_COMMAND](#on_command) , um einer Element Funktion einen einzelnen Befehl zuzuordnen. Nur ein Nachrichten Zuordnungs Eintrag kann mit einer angegebenen Befehls-ID verglichen werden. Das heißt, Sie können einen Befehl nicht mehreren Handlern zuordnen. Weitere Informationen zum Zuordnen von Nachrichten Bereichen finden Sie unter [Handler für](../../mfc/handlers-for-message-map-ranges.md)Meldungs Zuordnungs Bereiche.

Es gibt keine automatische Unterstützung für Meldungs Zuordnungs Bereiche, deshalb müssen Sie das Makro selbst platzieren.

### <a name="example"></a>Beispiel

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Ordnet einen zusammenhängenden Bereich von Befehls-IDs einer einzelnen Update-nachrichtenhandlerfunktion zu.

### <a name="syntax"></a>Syntax

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Befehls-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Befehls-IDs.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion für den Update, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Aktualisieren von Meldungs Handlern aktualisiert den Zustand von Menü Elementen und Symbolleisten-Schaltflächen, die dem Befehl zugeordnet sind. Der Bereich der IDs beginnt mit *id1* und endet mit *id2*.

Es gibt keine automatische Unterstützung für Meldungs Zuordnungs Bereiche, deshalb müssen Sie das Makro selbst platzieren.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

Verwenden Sie dieses Makro, um einen zusammenhängenden Bereich von Steuerelement-IDs einer einzelnen nachrichtenhandlerfunktion für eine angegebene Windows-Benachrichtigungs Meldung, wie z. b. BN_CLICKED, zuzuordnen.

### <a name="syntax"></a>Syntax

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*wnotifycode schalten*<br/>
Der Benachrichtigungs Code, auf den der Handler antwortet.

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Steuerelement-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Steuerelement-IDs.

*Mitgliedschaft*<br/>
Der Name der nachrichtenhandlerfunktion, der die Steuerelemente zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Der Bereich der IDs beginnt mit *id1* und endet mit *id2*. Der-Handler wird für die angegebene Benachrichtigung aufgerufen, die von einem der zugeordneten-Steuerelemente stammt.

Es gibt keine automatische Unterstützung für Meldungs Zuordnungs Bereiche, deshalb müssen Sie das Makro selbst platzieren.

Weitere Informationen zum Implementieren von Handlerfunktionen für einen Bereich von Steuerelement-IDs finden Sie unter [Handler für](../../mfc/handlers-for-message-map-ranges.md)Meldungs Zuordnungs Bereiche.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxmsg_. h

## <a name="see-also"></a>Weitere Informationen

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Meldungs Zuordnungen](../tn006-message-maps.md)<br/>
[COleCmdUI-Klasse](colecmdui-class.md)<br/>
[COleServerDoc:: onexecolecmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Benutzerdefinierte Handler](user-defined-handlers.md)<br/>
[CCmdUI-Klasse](ccmdui-class.md)
