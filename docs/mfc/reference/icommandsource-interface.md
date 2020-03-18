---
title: ICommandSource-Schnittstelle
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: a57ca6f36546a17b9a35ebea875ff01b43de1332
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445715"
---
# <a name="icommandsource-interface"></a>ICommandSource-Schnittstelle

Verwaltet Befehle, die von einem Befehls Quell Objekt an ein Benutzer Steuerelement gesendet werden.

## <a name="syntax"></a>Syntax

```
interface class ICommandSource
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ICommandSource:: AddCommandHandler](#addcommandhandler)|Fügt einem Befehls Quell Objekt einen Befehls Handler hinzu.|
|[ICommandSource:: addcommandrangehandler](#addcommandrangehandler)|Fügt einem Befehls Quell Objekt eine Gruppe von Befehls Handlern hinzu.|
|[ICommandSource:: addcommandrangeuihandler](#addcommandrangeuihandler)|Fügt einem Befehls Quell Objekt eine Gruppe von Benutzeroberflächen-Befehls Meldungs Handlern hinzu.|
|[ICommandSource:: addcommanduihandler](#addcommandrangeuihandler)|Fügt einem Befehls Quell Objekt einen Benutzeroberflächen-Befehls Meldungs Handler hinzu.|
|[ICommandSource::P ostcommand](#postcommand)|Sendet eine Nachricht, ohne darauf zu warten, dass Sie verarbeitet wird.|
|[ICommandSource:: removecommandhandler](#removecommandhandler)|Entfernt einen Befehls Handler aus einem Befehls Quell Objekt.|
|[ICommandSource:: removecommandrangehandler](#removecommandrangehandler)|Entfernt eine Gruppe von Befehls Handlern aus einem Befehls Quell Objekt.|
|[ICommandSource:: removecommandrangeuihandler](#removecommandrangeuihandler)|Entfernt eine Gruppe von befehlsnachrichten Handlern für Benutzeroberflächen aus einem Befehls Quell Objekt.|
|[ICommandSource:: removecommanduihandler](#removecommandrangeuihandler)|Entfernt einen Benutzeroberflächen-befehlsnachrichten Handler aus einem Befehls Quell Objekt.|
|[ICommandSource:: Send Command](#sendcommand)|Sendet eine Nachricht und wartet darauf, dass Sie vor der Rückgabe verarbeitet wird.|

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Benutzer Steuerelement in einer MFC-Ansicht hosten, leitet die [CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md) Befehle und aktualisiert Befehls Benutzeroberflächen-Meldungen an das Benutzer Steuerelement, damit Sie MFC-Befehle (z. b. Frame Menü Elemente und Symbolleisten Schaltflächen) verarbeiten kann. Durch Implementieren der [ICommandTarget-Schnittstelle](../../mfc/reference/icommandtarget-interface.md)wird dem Benutzer Steuerelement ein Verweis auf das `ICommandSource` Objekt zugewiesen.

Ein Beispiel für die Verwendung von `ICommandTarget`finden Sie unter Gewusst [wie: Hinzufügen von Befehls Routing zum Windows Forms-Steuer](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Element.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms. h (definiert in Assembly atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>ICommandSource:: AddCommandHandler

Fügt einem Befehls Quell Objekt einen Befehls Handler hinzu.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID.
*CmdHandler*<br/>
Ein Handle für die Befehls Handlermethode.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Befehls Quell Objekt den Befehls Handler-CmdHandler hinzu und ordnet den Handler CMDID zu.
Ein Beispiel für die Verwendung von AddCommandHandler finden Sie unter Gewusst [wie: Hinzufügen von Befehls Routing zum Windows Forms-Steuer](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Element.

## <a name="addcommandrangehandler"></a>ICommandSource:: addcommandrangehandler

Fügt einem Befehls Quell Objekt eine Gruppe von Befehls Handlern hinzu.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parameter

*cmdidmin*<br/>
Der Anfangs Index des Befehls-ID-Bereichs.
*cmdidmax*<br/>
Der Endindex des Befehls-ID-Bereichs.
*CmdHandler*<br/>
Ein Handle für die nachrichtenhandlermethode, der die Befehle zugeordnet werden.
### <a name="remarks"></a>Bemerkungen

Diese Methode ordnet einen zusammenhängenden Bereich von Befehls-IDs einem einzelnen Nachrichten Handler zu und fügt ihn dem Befehls Quell Objekt hinzu. Diese wird verwendet, um eine Gruppe verwandter Schaltflächen mit einer Methode zu verarbeiten.

## <a name="addcommandrangeuihandler"></a>ICommandSource:: addcommandrangeuihandler

Fügt einem Befehls Quell Objekt eine Gruppe von Benutzeroberflächen-Befehls Meldungs Handlern hinzu.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parameter

*cmdidmin*<br/>
Der Anfangs Index des Befehls-ID-Bereichs.
*cmdidmax*<br/>
Der Endindex des Befehls-ID-Bereichs.
*CmdHandler*<br/>
Ein Handle für die nachrichtenhandlermethode, der die Befehle zugeordnet werden.

### <a name="remarks"></a>Bemerkungen

Diese Methode ordnet einen zusammenhängenden Bereich von Befehls-IDs einem einzelnen Benutzeroberflächen-befehlsnachrichten Handler zu und fügt ihn dem Befehls Quell Objekt hinzu. Diese wird verwendet, um eine Gruppe verwandter Schaltflächen mit einer Methode zu verarbeiten.

## <a name="addcommanduihandler"></a>ICommandSource:: addcommanduihandler

Fügt einem Befehls Quell Objekt einen Benutzeroberflächen-Befehls Meldungs Handler hinzu.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID.
*cmduihandler*<br/>
Ein Handle für die Handlermethode der Benutzeroberflächen-Befehls Meldung.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt den Befehlszeilen-CmdHandler für die Benutzeroberflächen Befehle zum Befehls Quell Objekt hinzu und ordnet den Handler CMDID zu.

## <a name="postcommand"></a>ICommandSource::P ostcommand

Sendet eine Nachricht, ohne darauf zu warten, dass Sie verarbeitet wird.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parameter

*command*<br/>
Die Befehls-ID der Nachricht, die gepostet werden soll.
### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die Nachricht, die der durch den Befehl angegebenen ID zugeordnet ist, asynchron. CWnd::P ostmessage wird aufgerufen, um die Nachricht in der Nachrichten Warteschlange des Fensters zu platzieren, und dann wird zurückgegeben, ohne darauf zu warten, dass das entsprechende Fenster die Nachricht verarbeitet.

## <a name="removecommandhandler"></a>ICommandSource:: removecommandhandler

Entfernt einen Befehls Handler aus einem Befehls Quell Objekt.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID.
### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt den Befehls Handler, der CMDID zugeordnet ist, aus dem Befehls Quell Objekt.

## <a name="removecommandrangehandler"></a>ICommandSource:: removecommandrangehandler

Entfernt eine Gruppe von Befehls Handlern aus einem Befehls Quell Objekt.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parameter

*cmdidmin*<br/>
Der Anfangs Index des Befehls-ID-Bereichs.
*cmdidmax*<br/>
Der Endindex des Befehls-ID-Bereichs.
### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Gruppe von Meldungs Handlern, die den von cmdidmin und cmdidmax angegebenen Befehls-IDs zugeordnet sind, aus dem Befehls Quell Objekt.

## <a name="removecommandrangeuihandler"></a>ICommandSource:: removecommandrangeuihandler

Entfernt eine Gruppe von befehlsnachrichten Handlern für Benutzeroberflächen aus einem Befehls Quell Objekt.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parameter

*cmdidmin*<br/>
Der Anfangs Index des Befehls-ID-Bereichs.
*cmdidmax*<br/>
Der Endindex des Befehls-ID-Bereichs.
### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Gruppe von Benutzeroberflächen-Befehls Meldungs Handlern, die den von cmdidmin und cmdidmax angegebenen Befehls-IDs zugeordnet sind, aus dem Befehls Quell Objekt.

## <a name="removecommanduihandler"></a>ICommandSource:: removecommanduihandler

Entfernt einen Benutzeroberflächen-befehlsnachrichten Handler aus einem Befehls Quell Objekt.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parameter

*CMDID*<br/>
Die Befehls-ID.
### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird der Benutzeroberflächen-Befehls Meldungs Handler, der CMDID zugeordnet ist, aus dem Befehls Quell Objekt entfernt.

## <a name="sendcommand"></a>ICommandSource:: Send Command

Sendet eine Nachricht und wartet darauf, dass Sie vor der Rückgabe verarbeitet wird.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parameter

*command*<br/>
Die Befehls-ID der zu sendenden Nachricht.
### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die Nachricht, die der durch den Befehl angegebenen ID zugeordnet ist, synchron. CWnd:: SendMessage wird aufgerufen, um die Nachricht in der Meldungs Warteschlange des Fensters zu platzieren, und wartet, bis die Fenster Prozedur die Nachricht vor der Rückgabe verarbeitet hat.
## <a name="see-also"></a>Weitere Informationen

[Vorgehensweise: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget-Schnittstelle](../../mfc/reference/icommandtarget-interface.md)
