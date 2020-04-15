---
title: Delegate- und Schnittstellenzuordnungsmakros (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365833"
---
# <a name="delegate-and-interface-map-macros"></a>Zuordnungsmakros von Delegaten und Schnittstellen

MFC unterstützt diese Makros für Delegat- und Schnittstellenzuordnungen:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Beginnt eine Delegatenzuordnung.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Beginnt die Definition der begabten Karte.|
|[CommandHandler-Delegat](#commandhandler)|Registriert Rückrufmethoden mit einer Befehlsquelle.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Beendet eine Delegatenzuordnung.|
|[END_INTERFACE_MAP](#end_interface_map)|Beendet die Schnittstellenzuordnung in der Implementierungsdatei. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Erstellt einen Eintrag in der Delegatzuordnung.|
|[INTERFACE_PART](#interface_part)|Wird zwischen dem BEGIN_INTERFACE_MAP Makro und dem END_INTERFACE_MAP Makro für jede Schnittstelle verwendet, die Ihr Objekt unterstützt.|
|[MAKE_DELEGATE](#make_delegate)|Fügt einen Ereignishandler an ein verwaltetes Steuerelement an.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Beginnt eine Delegatenzuordnung.

### <a name="syntax"></a>Syntax

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parameter

*Klasse*<br/>
Die Klasse, in der das verwaltete Steuerelement gehostet wird.

### <a name="remarks"></a>Bemerkungen

Dieses Makro markiert den Anfang einer Liste von Delegierteneinträgen, aus denen eine Delegiertenzuordnung besteht. Ein Beispiel für die Verwendung dieses Makros finden Sie unter [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** msclr-event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Beginnt die Definition der begabten Zuordnung, wenn sie in der Implementierungsdatei verwendet wird.

### <a name="syntax"></a>Syntax

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, in der die Schnittstellenzuordnung definiert werden soll

*Baseclass*<br/>
Die Klasse, von *der die Klasse* abstammt.

### <a name="remarks"></a>Bemerkungen

Für jede implementierte Schnittstelle gibt es eine oder mehrere INTERFACE_PART Makroaufrufe. Für jedes Aggregat, das die Klasse verwendet, gibt es eine INTERFACE_AGGREGATE Makroaufruf.

Weitere Informationen zu Schnittstellenkarten finden Sie unter [Technische Anmerkung 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>CommandHandler-Delegat

Registriert Rückrufmethoden mit einer Befehlsquelle.

### <a name="syntax"></a>Syntax

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Dieser Delegat registriert Rückrufmethoden mit einer Befehlsquelle. Wenn Sie dem Befehlsquellobjekt einen Delegaten hinzufügen, wird die Rückrufmethode zu einem Handler für Befehle, die von der angegebenen Quelle stammen.

Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Befehlsrouting zum Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>CommandUIHandler

Registriert Rückrufmethoden mit einer Befehlsnachricht für die Benutzeroberflächenaktualisierung.

### <a name="syntax"></a>Syntax

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.

*cmdUI*<br/>
Die Befehlsnachrichten-ID.

### <a name="remarks"></a>Bemerkungen

Dieser Delegat registriert Rückrufmethoden mit einer Befehlsnachricht für die Benutzeroberflächenaktualisierung. `CommandUIHandler`ist ähnlich wie [CommandHandler,](#commandhandler) mit der Ausnahme, dass dieser Delegat mit Befehlen zur Objektaktualisierung der Benutzeroberfläche verwendet wird. Benutzeroberflächenaktualisierungsbefehle sollten eins zu eins mit Nachrichtenhandlermethoden zugeordnet werden.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

Beendet eine Delegatenzuordnung.

### <a name="syntax"></a>Syntax

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Bemerkungen

Dieses Makro markiert das Ende einer Liste von Delegierteneinträgen, aus denen eine Delegiertenzuordnung besteht. Ein Beispiel für die Verwendung dieses Makros finden Sie unter [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** msclr-event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

Beendet die Schnittstellenzuordnung in der Implementierungsdatei.

### <a name="syntax"></a>Syntax

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Schnittstellenkarten finden Sie unter [Technische Anmerkung 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Erstellt einen Eintrag in der Delegatzuordnung.

### <a name="syntax"></a>Syntax

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parameter

*Mitglied*<br/>
Die Ereignishandlermethode, die dem Steuerelement angefügt werden soll.

*ARG0*<br/>
Das erste Argument der verwalteten Ereignishandlermethode, z. `Object^`B. .

*ARG1*<br/>
Das zweite Argument der verwalteten Ereignishandlermethode, z. `EventArgs^`B. .

### <a name="remarks"></a>Bemerkungen

Jeder Eintrag in der Delegatzuordnung entspricht einem verwalteten Ereignishandlerdelegat, der von [MAKE_DELEGATE](#make_delegate)erstellt wurde.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, wie EVENT_DELEGATE_ENTRY verwendet wird, `OnClick` um einen Eintrag in der Delegatzuordnung für den Ereignishandler zu erstellen. siehe auch das Codebeispiel in MAKE_DELEGATE. Weitere Informationen finden Sie unter [Gewusst wie: Versenken von Windows Forms-Ereignissen aus systemeigenen C++-Klassen](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** msclr-event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

Wird zwischen dem BEGIN_INTERFACE_MAP Makro und dem END_INTERFACE_MAP Makro für jede Schnittstelle verwendet, die Ihr Objekt unterstützt.

### <a name="syntax"></a>Syntax

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Der Name der Klasse, die die Schnittstellenzuordnung enthält.
*Iid*<br/>
Die IID, die der eingebetteten Klasse zugeordnet werden soll.
*localClass*<br/>
Der Name der lokalen Klasse.

### <a name="remarks"></a>Bemerkungen

Sie können eine IID einem Member der Klasse zuordnen, die von *derClass* und *localClass*angegeben wird.

Weitere Informationen zu Schnittstellenkarten finden Sie unter [Technische Anmerkung 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

Fügt einen Ereignishandler an ein verwaltetes Steuerelement an.

### <a name="syntax"></a>Syntax

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parameter

*delegieren*<br/>
Der Typ des verwalteten Ereignishandlerdelegaten, z. B. [EventHandler](/dotnet/api/system.eventhandler).

*Mitglied*<br/>
Der Name der Ereignishandlermethode, die dem Steuerelement angefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Dieses Makro erstellt einen verwalteten Ereignishandlerdelegat vom Typ *DELEGATE* und den Namen *MEMBER*. Der verwaltete Ereignishandlerdelegat ermöglicht es einer systemeigenen Klasse, verwaltete Ereignisse zu verarbeiten.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, wie `OnClick` Sie aufrufen, um `MyControl`einen Ereignishandler an ein MFC-Steuerelement anzufügen. `MAKE_DELEGATE` Eine ausführlichere Erläuterung der Funktionsweise dieses Makros in einer MFC-Anwendung finden Sie unter [Gewusst wie: Versenken von Windows Forms-Ereignissen aus systemeigenen C++-Klassen](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** msclr-event.h

## <a name="see-also"></a>Siehe auch

[Gewusst wie: Auffangen von Windows Forms-Ereignissen aus systemeigenen C++-Klassen](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Vorgehensweise: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
