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
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356588"
---
# <a name="message-map-macros-mfc"></a>Meldungszuordnungsmakros (MFC)

Zur Unterstützung von Nachrichtenzuordnungen stellt MFC die folgenden Makros bereit:

### <a name="message-map-declaration-and-demarcation-macros"></a>Nachrichtenkartendeklaration und Demarkationsmakros

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklariert, dass eine Nachrichtenzuordnung in einer Klasse verwendet wird, um Nachrichten Funktionen zuzuordnen (muss in der Klassendeklaration verwendet werden).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Beginnt die Definition einer Nachrichtenzuordnung (muss in der Klassenimplementierung verwendet werden).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Beginnt die Definition einer Nachrichtenzuordnung für einen Klassentyp, der ein einzelnes Vorlagenargument enthält. |
|[END_MESSAGE_MAP](#end_message_map)|Beendet die Definition einer Nachrichtenzuordnung (muss in der Klassenimplementierung verwendet werden).|

### <a name="message-mapping-macros"></a>Message-Mapping-Makros

|||
|-|-|
|[ON_COMMAND](#on_command)|Gibt an, welche Funktion eine angegebene Befehlsnachricht verarbeitet.|
|[ON_COMMAND_EX](#on_command_ex)|Gibt an, welche Funktion eine angegebene Befehlsnachricht verarbeitet.|
|[ON_CONTROL](#on_control)|Gibt an, welche Funktion eine angegebene Steuerbenachrichtigung verarbeitet.|
|[ON_MESSAGE](#on_message)|Gibt an, welche Funktion eine benutzerdefinierte Nachricht verarbeitet.|
|[ON_OLECMD](#on_olecmd)|Gibt an, welche Funktion einen Menübefehl aus einem DocObject oder dessen Container verarbeitet.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Gibt an, welche Funktion eine registrierte benutzerdefinierte Nachricht verarbeitet.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Gibt an, welche Funktion eine registrierte benutzerdefinierte `CWinThread` Nachricht verarbeitet, wenn Sie über eine Klasse verfügen.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Gibt an, welche Funktion eine benutzerdefinierte `CWinThread` Nachricht verarbeitet, wenn Sie über eine Klasse verfügen.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Gibt an, welche Funktion eine angegebene Befehlsnachricht für die Benutzeroberflächenaktualisierung verarbeitet.|

### <a name="message-map-range-macros"></a>Message-Map-Bereichsmakros

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Gibt an, welche Funktion den Bereich der Befehls-IDs verarbeitet, die in den ersten beiden Parametern für das Makro angegeben sind.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Gibt an, welcher Aktualisierungshandler den Bereich der Befehls-IDs verarbeitet, der in den ersten beiden Parametern für das Makro angegeben ist.|
|[ON_CONTROL_RANGE](#on_control_range)|Gibt an, welche Funktion Benachrichtigungen aus dem Bereich der Steuer-IDs verarbeitet, die im zweiten und dritten Parameter für das Makro angegeben sind. Der erste Parameter ist eine Steuerbenachrichtigung, z. B. BN_CLICKED.|

Weitere Informationen zu Nachrichtenzuordnungen, den Nachrichtenzuordnungsdeklarationen und Abgrenzungsmakros sowie den Nachrichtenzuordnungsmakros finden Sie unter [Nachrichtenzuordnungen](../../mfc/reference/message-maps-mfc.md) und [Nachrichtenbehandlungs- und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md). Weitere Informationen zu Message-Map-Bereichen finden Sie unter [Handlers for Message-Map Ranges](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Beginnt die Definition der Nachrichtenzuordnung.

### <a name="syntax"></a>Syntax

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Klasse an, deren Meldungszuordnung dies ist.

*Baseclass*<br/>
Gibt den Namen der Basisklasse *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungsdatei (.cpp), die die Memberfunktionen für Ihre Klasse definiert, die Meldungszuordnung mit dem BEGIN_MESSAGE_MAP-Makro, fügen Sie dann Makroeinträge für jede Ihrer Message-Handler-Funktionen hinzu, und schließen Sie die Nachrichtenzuordnung mit dem END_MESSAGE_MAP-Makro ab.

Weitere Informationen zu Nachrichtenzuordnungen finden Sie unter [Nachrichtenzuordnungen](message-maps-mfc.md)

### <a name="example"></a>Beispiel

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Beginnt die Definition einer Nachrichtenzuordnung für einen Klassentyp, der ein einzelnes Vorlagenargument enthält.

### <a name="syntax"></a>Syntax

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Klasse an, deren Meldungszuordnung dies ist.

*Type_name*<br/>
Der Name des für die Klasse angegebenen Vorlagenparameters.

*Baseclass*<br/>
Gibt den Namen der Basisklasse *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

Dieses Makro ähnelt [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) dem BEGIN_MESSAGE_MAP-Makro. Dieses Makro ist jedoch für Klassen gedacht, die ein einzelnes Vorlagenargument enthalten.

Starten Sie im Abschnitt Methodenimplementierung Ihrer Klasse die Nachrichtenzuordnung mit dem BEGIN_TEMPLATE_MESSAGE_MAP-Makro. fügen Sie dann Makroeinträge für jede Ihrer Message-Handler-Methoden wie für eine Standard-Nachrichtenzuordnung hinzu. Vervollständigen Sie wie beim BEGIN_MESSAGE_MAP-Makro [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) die Vorlagen-Meldungszuordnung mit dem END_MESSAGE_MAP-Makro.

Weitere Informationen zum Implementieren von Nachrichtenzuordnungen für Vorlagenklassen finden Sie unter [Gewusst wie: Erstellen einer Nachrichtenzuordnung für eine Vorlagenklasse](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklariert, dass die Klasse eine Nachrichtenzuordnung definiert. Jede `CCmdTarget`-abgeleitete Klasse in Ihrem Programm muss eine Nachrichtenzuordnung bereitstellen, um Nachrichten zu verarbeiten.

### <a name="syntax"></a>Syntax

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_MESSAGE_MAP-Makro am Ende der Klassendeklaration. Verwenden Sie dann in der CPP-Datei, die die Memberfunktionen für die Klasse definiert, das BEGIN_MESSAGE_MAP Makro, Makroeinträge für jede Ihrer Message-Handler-Funktionen und das END_MESSAGE_MAP-Makro.

> [!NOTE]
> Wenn Sie ein Mitglied nach DECLARE_MESSAGE_MAP deklarieren, müssen Sie einen neuen Zugriffstyp (**öffentlich**, **privat**oder **geschützt**) für sie angeben.

Weitere Informationen zu Nachrichtenzuordnungen und dem DECLARE_MESSAGE_MAP-Makro finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Beendet die Definition der Nachrichtenzuordnung.

### <a name="syntax"></a>Syntax

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Nachrichtenzuordnungen und dem END_MESSAGE_MAP-Makro finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

Dieses Makro ordnet eine Befehlsnachricht einer Memberfunktion zu.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parameter

*Commandid*<br/>
Die Befehls-ID.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Es gibt an, welche Funktion eine Befehlsnachricht von einem Befehlsbenutzeroberflächenobjekt, z. B. einem Menüelement oder einer Symbolleistenschaltfläche, verarbeitet.

Wenn ein Befehlszielobjekt eine Windows-WM_COMMAND-Nachricht mit der angegebenen `memberFxn` ID empfängt, ruft ON_COMMAND die Memberfunktion auf, um die Nachricht zu behandeln.

Verwenden Sie ON_COMMAND, um einen einzelnen Befehl einer Memberfunktion zuzuordnen. Verwenden Sie [ON_COMMAND_RANGE,](#on_command_range) um einen Bereich von Befehls-IDs einer Memberfunktion zuzuordnen. Nur ein Nachrichtenzuordnungseintrag kann mit einer bestimmten Befehls-ID übereinstimmen. Das heißt, Sie können einen Befehl nicht mehr als einem Handler zuordnen. Weitere Informationen und Beispiele finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Erweiterte Befehlshandlermemberfunktion.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parameter

*Commandid*<br/>
Die Befehls-ID.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Für erweiterte Anwendungen steht eine erweiterte Form von Befehlsnachrichtenhandlern zur Verfügung. Das ON_COMMAND_EX Makro summiert sich zu solchen Nachrichtenhandlern und stellt eine Übermenge der [ON_COMMAND-Funktionalität](message-map-macros-mfc.md#on_command) bereit. Erweiterte Befehlshandlermemberfunktionen verwenden einen einzelnen Parameter, einen UINT, der die Befehls-ID enthält, und geben eine BOOL zurück. Der Rückgabewert sollte TRUE sein, um anzugeben, dass der Befehl behandelt wurde. Andernfalls wird das Routing mit anderen Befehlszielobjekten fortgesetzt.

Weitere Informationen finden Sie unter Technischer Hinweis [TN006: Message Maps]tm006-message-maps.md).

### <a name="requirements"></a>Anforderungen

Headerdatei: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Gibt an, welche Funktion eine benutzerdefinierte Steuerbenachrichtigung verarbeitet.

### <a name="syntax"></a>Syntax

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parameter

*wNotifyCode*<br/>
Der Benachrichtigungscode des Steuerelements.

*Commandid*<br/>
Die Befehls-ID.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der der Befehl zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Steuerbenachrichtigungen sind Benachrichtigungen, die von einem Steuerelement an das übergeordnete Fenster gesendet werden.

Es sollte genau eine ON_CONTROL Makroanweisung in der Nachrichtenzuordnung für jede Steuerbenachrichtigung vorhanden sein, die einer Nachrichtenhandlerfunktion zugeordnet werden muss.

Weitere Informationen und Beispiele finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Gibt an, welche Funktion eine benutzerdefinierte Nachricht verarbeitet.

### <a name="syntax"></a>Syntax

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Die Meldungs-ID.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der die Nachricht zugeordnet ist.

Der Typ der Funktion `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`muss .

### <a name="remarks"></a>Bemerkungen

Benutzerdefinierte Nachrichten sind alle Nachrichten, die keine Standardmäßigen Windows-WM_MESSAGE-Nachrichten sind. Bei der Auswahl einer Nachrichten-ID müssen Sie Werte im Bereich von WM_USER (0x0400) bis 0x7FFF oder WM_APP (0x8000) bis 0xBFFF verwenden. Weitere Informationen zu Nachrichten-IDs finden Sie [unter WM_APP](/windows/win32/winmsg/wm-app).

Es sollte genau eine ON_MESSAGE Makroanweisung in der Nachrichtenzuordnung für jede benutzerdefinierte Nachricht vorhanden sein, die einer Message-Handler-Funktion zugeordnet werden muss.

> [!NOTE]
> Zusätzlich zu benutzerdefinierten Nachrichten verarbeitet ON_MESSAGE weniger häufige Windows-Nachrichten. Weitere Informationen finden Sie unter [Nachrichtenzuordnungen](../../mfc/tn006-message-maps.md).

Weitere Informationen und Beispiele finden Sie unter [Nachrichtenbehandlungs- und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md) und [benutzerdefinierte Handler](user-defined-handlers.md)

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

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Leitet Befehle über die `IOleCommandTarget`Befehlsdispatchschnittstelle .

### <a name="syntax"></a>Syntax

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parameter

*pguid*<br/>
Bezeichner der Befehlsgruppe, zu der der Befehl gehört. Verwenden Sie NULL für die Standardgruppe.

*olecmdid*<br/>
Der Bezeichner des OLE-Befehls.

*Commandid*<br/>
Die Menü-ID, Symbolleisten-ID, Schaltflächen-ID oder eine andere ID der Ressource oder des Objekts, die den Befehl ausgibt.

### <a name="remarks"></a>Bemerkungen

`IOleCommandTarget`ermöglicht einem Container das Empfangen von Befehlen, die aus der Benutzeroberfläche eines DocObject stammen, und ermöglicht es dem Container, dieselben Befehle (z. B. Neu, Öffnen, Speichern und Drucken im Menü Datei) und Kopieren, Einfügen, Rückgängig machen usw. an ein DocObject zu senden.

`IOleCommandTarget`ist einfacher als die `IDispatch`von OLE Automation . `IOleCommandTarget`basiert vollständig auf einem Standardsatz von Befehlen, die selten Argumente enthalten, und es sind keine Typinformationen beteiligt (die Typsicherheit wird auch für Befehlsargumente verringert). Wenn Sie Befehle mit Argumenten ausgeben müssen, verwenden Sie [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Die `IOleCommandTarget` Standardmenübefehle wurden von MFC in den folgenden Makros implementiert:

**ON_OLECMD_CLEARSELECTION( )**

Löst den Befehl Clear bearbeiten aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Löst den Befehl Kopie bearbeiten aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Löst den Befehl Cut bearbeiten aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Löst den Befehl Datei neu aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Löst den Befehl Datei geöffnet aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Löst den Befehl Dateiseiteneinrichtung aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Löst den Befehl Einfügen bearbeiten aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Sendet den Befehl "Einfügen spezial bearbeiten" aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Löst den Befehl Dateidruck aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Löst den Befehl Dateidruckvorschau aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Sendet den Befehl Redo bearbeiten. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Löst den Befehl Dateispeichern aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Löst den Befehl Datei speichern unter aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Löst den Befehl Dateispeichern kopiere unter aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Löst den Befehl "Alle auswählen bearbeiten" aus. Implementiert als:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Sendet den Befehl "Rückgängig bearbeiten". Implementiert als:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Anforderungen

**Kopf:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Die `RegisterWindowMessage` Windows-Funktion wird verwendet, um eine neue Fensternachricht zu definieren, die im gesamten System eindeutig ist.

### <a name="syntax"></a>Syntax

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parameter

*nMessageVariable*<br/>
Die registrierte Fenster-Nachrichten-ID-Variable.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Dieses Makro gibt an, welche Funktion die registrierte Nachricht verarbeitet.

Weitere Informationen und Beispiele finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Beispiel

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Gibt an, welche Funktion die von der Windows RegisterWindowMessage-Funktion registrierte Nachricht verarbeitet.

### <a name="syntax"></a>Syntax

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parameter

*nMessageVariable*<br/>
Die registrierte Fenster-Nachrichten-ID-Variable.

*MemberFxn*<br/>
Der Name der CWinThread-message-handler-Funktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

RegisterWindowMessage wird verwendet, um eine neue Fensternachricht zu definieren, die garantiert im gesamten System eindeutig ist. ON_REGISTERED_THREAD_MESSAGE muss anstelle ON_REGISTERED_MESSAGE verwendet werden, wenn Sie über eine CWinThread-Klasse verfügen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Gibt an, welche Funktion eine benutzerdefinierte Nachricht verarbeitet.

### <a name="syntax"></a>Syntax

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Die Meldungs-ID.

*MemberFxn*<br/>
Der Name `CWinThread`der Funktion -message-handler, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

ON_THREAD_MESSAGE muss anstelle von ON_MESSAGE verwendet `CWinThread` werden, wenn Sie eine Klasse haben. Benutzerdefinierte Nachrichten sind alle Nachrichten, die keine Standardmäßigen Windows-WM_MESSAGE-Nachrichten sind. Es sollte genau eine ON_THREAD_MESSAGE Makroanweisung in der Nachrichtenzuordnung für jede benutzerdefinierte Nachricht vorhanden sein, die einer Message-Handler-Funktion zugeordnet werden muss.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Dieses Makro gibt an, welche Funktion eine Befehlsnachricht für die Benutzeroberflächenaktualisierung verarbeitet.

### <a name="syntax"></a>Syntax

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parameter

*messageId*<br/>
Die Meldungs-ID.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der die Nachricht zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Es sollte genau eine ON_UPDATE_COMMAND_UI Makroanweisung in der Nachrichtenzuordnung für jeden Benutzeroberflächenaktualisierungsbefehl vorhanden sein, der einer Message-Handler-Funktion zugeordnet werden muss.

Weitere Informationen und Beispiele finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

Verwenden Sie dieses Makro, um einen zusammenhängenden Bereich von Befehls-IDs einer einzelnen Nachrichtenhandlerfunktion zuzuordnen.

### <a name="syntax"></a>Syntax

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Befehls-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Befehls-IDs.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Der ID-Bereich beginnt mit *id1* und endet mit *id2*.

Verwenden Sie ON_COMMAND_RANGE, um einen Bereich von Befehls-IDs einer Memberfunktion zuzuordnen. Verwenden Sie [ON_COMMAND,](#on_command) um einen einzelnen Befehl einer Memberfunktion zuzuordnen. Nur ein Nachrichtenzuordnungseintrag kann mit einer bestimmten Befehls-ID übereinstimmen. Das heißt, Sie können einen Befehl nicht mehr als einem Handler zuordnen. Weitere Informationen zum Zuordnen von Nachrichtenbereichen finden Sie unter [Handler s for Message-Map Ranges](../../mfc/handlers-for-message-map-ranges.md).

Es gibt keine automatische Unterstützung für Meldungszuordnungsbereiche, daher müssen Sie das Makro selbst platzieren.

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

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Ordnet einen zusammenhängenden Bereich von Befehls-IDs einer einzelnen Aktualisierungsmeldungshandlerfunktion zu.

### <a name="syntax"></a>Syntax

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Befehls-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Befehls-IDs.

*MemberFxn*<br/>
Der Name der Update-Message-Handler-Funktion, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Aktualisierungsnachrichtenhandler aktualisieren den Status von Menüelementen und Symbolleistenschaltflächen, die dem Befehl zugeordnet sind. Der ID-Bereich beginnt mit *id1* und endet mit *id2*.

Es gibt keine automatische Unterstützung für Meldungszuordnungsbereiche, daher müssen Sie das Makro selbst platzieren.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

Verwenden Sie dieses Makro, um einen zusammenhängenden Bereich von Steuer-IDs einer einzelnen Nachrichtenhandlerfunktion für eine angegebene Windows-Benachrichtigung zuzuordnen, z. B. BN_CLICKED.

### <a name="syntax"></a>Syntax

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parameter

*wNotifyCode*<br/>
Der Benachrichtigungscode, auf den der Handler antwortet.

*id1*<br/>
Befehls-ID am Anfang eines zusammenhängenden Bereichs von Steuer-IDs.

*id2*<br/>
Befehls-ID am Ende eines zusammenhängenden Bereichs von Steuer-IDs.

*MemberFxn*<br/>
Der Name der Message-Handler-Funktion, der die Steuerelemente zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Der ID-Bereich beginnt mit *id1* und endet mit *id2*. Der Handler wird für die angegebene Benachrichtigung aufgerufen, die von einem der zugeordneten Steuerelemente stammt.

Es gibt keine automatische Unterstützung für Meldungszuordnungsbereiche, daher müssen Sie das Makro selbst platzieren.

Weitere Informationen zum Implementieren von Handlerfunktionen für einen Bereich von Steuerelement-IDs finden Sie unter [Handlers for Message-Map Ranges](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmsg_.h

## <a name="see-also"></a>Siehe auch

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Meldungszuordnungen](../tn006-message-maps.md)<br/>
[COleCmdUI-Klasse](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Benutzerdefinierte Handler](user-defined-handlers.md)<br/>
[CCmdUI-Klasse](ccmdui-class.md)
