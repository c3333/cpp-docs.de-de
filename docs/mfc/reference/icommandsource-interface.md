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
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356982"
---
# <a name="icommandsource-interface"></a>ICommandSource-Schnittstelle

Verwaltet Befehle, die von einem Befehlsquellobjekt an ein Benutzersteuerelement gesendet werden.

## <a name="syntax"></a>Syntax

```cpp
interface class ICommandSource
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Fügt einem Befehlsquellobjekt einen Befehlshandler hinzu.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Fügt einem Befehlsquellobjekt eine Gruppe von Befehlshandlern hinzu.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Fügt einem Befehlsquellobjekt eine Gruppe von Befehlsnachrichtenhandlern der Benutzeroberfläche hinzu.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Fügt einem Befehlsquellobjekt einen Befehlsnachrichtenhandler für die Benutzeroberfläche hinzu.|
|[ICommandSource::PostCommand](#postcommand)|Sendet eine Nachricht, ohne darauf zu warten, dass sie verarbeitet wird.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Entfernt einen Befehlshandler aus einem Befehlsquellobjekt.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Entfernt eine Gruppe von Befehlshandlern aus einem Befehlsquellobjekt.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Entfernt eine Gruppe von Benutzeroberflächenbefehlsnachrichtenhandlern aus einem Befehlsquellobjekt.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Entfernt einen Benutzeroberflächenbefehlsnachrichtenhandler aus einem Befehlsquellobjekt.|
|[ICommandSource::SendCommand](#sendcommand)|Sendet eine Nachricht und wartet, bis sie verarbeitet wird, bevor sie zurückgegeben wird.|

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Benutzersteuerelement in einer MFC-Ansicht hosten, leitet [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) Befehle weiter und aktualisiert Befehlsbenutzer-UI-Meldungen an das Benutzersteuerelement, damit es MFC-Befehle verarbeiten kann (z. B. Framemenüelemente und Symbolleistenschaltflächen). Durch implementieren [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), geben Sie `ICommandSource` dem Benutzersteuerelement einen Verweis auf das Objekt.

Weitere Informationen [finden Sie unter Gewusst wie: Hinzufügen von Befehlsrouting zum Windows-Formularsteuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) für ein Beispiel für die Verwendung `ICommandTarget`von .

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommandSource::AddCommandHandler

Fügt einem Befehlsquellobjekt einen Befehlshandler hinzu.

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.
*cmdHandler*<br/>
Ein Handle für die Befehlshandlermethode.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Befehlsquellobjekt den Befehlshandler cmdHandler hinzu und ordnet den Handler cmdID zu.
Weitere Informationen finden [Sie unter Gewusst wie: Hinzufügen von Befehlsrouting zum Windows-Formularsteuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) für ein Beispiel für die Verwendung von AddCommandHandler.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Fügt einem Befehlsquellobjekt eine Gruppe von Befehlshandlern hinzu.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parameter

*cmdIDMin*<br/>
Der Anfangsindex des Befehls-ID-Bereichs.
*cmdIDMax*<br/>
Der Endindex des Befehls-ID-Bereichs.
*cmdHandler*<br/>
Ein Handle für die Nachrichtenhandlermethode, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Diese Methode ordnet einem einzelnen Nachrichtenhandler einen zusammenhängenden Bereich von Befehls-IDs zu und fügt ihn dem Befehlsquellobjekt hinzu. Dies wird für die Behandlung einer Gruppe verwandter Schaltflächen mit einer Methode verwendet.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler

Fügt einem Befehlsquellobjekt eine Gruppe von Befehlsnachrichtenhandlern der Benutzeroberfläche hinzu.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parameter

*cmdIDMin*<br/>
Der Anfangsindex des Befehls-ID-Bereichs.
*cmdIDMax*<br/>
Der Endindex des Befehls-ID-Bereichs.
*cmdHandler*<br/>
Ein Handle für die Nachrichtenhandlermethode, der die Befehle zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

Diese Methode ordnet einem befehlsoffenen Befehlsnachrichtenhandler einer einzigen Benutzeroberflächenbefehlsnachricht einen zusammenhängenden Bereich von Befehls-IDs zu und fügt ihn dem Befehlsquellobjekt hinzu. Dies wird für die Behandlung einer Gruppe verwandter Schaltflächen mit einer Methode verwendet.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler

Fügt einem Befehlsquellobjekt einen Befehlsnachrichtenhandler für die Benutzeroberfläche hinzu.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.
*cmdUIHandler*<br/>
Ein Handle für die Befehlshandlermethode der Benutzeroberfläche.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Befehlsquellobjekt den Befehlsbefehl smessage handler cmdHandler hinzu und ordnet den Handler cmdID zu.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommandSource::PostCommand

Sendet eine Nachricht, ohne darauf zu warten, dass sie verarbeitet wird.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parameter

*Befehl*<br/>
Die Befehls-ID der zu sendenden Nachricht.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die Nachricht asynchron der durch Befehl angegebenen ID zugeordnet. Es ruft CWnd::PostMessage auf, um die Nachricht in der Nachrichtenwarteschlange des Fensters zu platzieren, und kehrt dann zurück, ohne auf das entsprechende Fenster zu warten, um die Nachricht zu verarbeiten.

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler

Entfernt einen Befehlshandler aus einem Befehlsquellobjekt.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt den Befehlshandler, der cmdID zugeordnet ist, aus dem Befehlsquellobjekt.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommandSource::RemoveCommandRangeHandler

Entfernt eine Gruppe von Befehlshandlern aus einem Befehlsquellobjekt.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parameter

*cmdIDMin*<br/>
Der Anfangsindex des Befehls-ID-Bereichs.
*cmdIDMax*<br/>
Der Endindex des Befehls-ID-Bereichs.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Gruppe von Nachrichtenhandlern, die den von cmdIDMin und cmdIDMax angegebenen Befehls-IDs zugeordnet sind, aus dem Befehlsquellobjekt.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler

Entfernt eine Gruppe von Benutzeroberflächenbefehlsnachrichtenhandlern aus einem Befehlsquellobjekt.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parameter

*cmdIDMin*<br/>
Der Anfangsindex des Befehls-ID-Bereichs.
*cmdIDMax*<br/>
Der Endindex des Befehls-ID-Bereichs.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Gruppe von Benutzeroberflächenbefehls-Nachrichtenhandlern, die den von cmdIDMin und cmdIDMax angegebenen Befehls-IDs zugeordnet sind, aus dem Befehlsquellobjekt.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler

Entfernt einen Benutzeroberflächenbefehlsnachrichtenhandler aus einem Befehlsquellobjekt.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parameter

*cmdID*<br/>
Die Befehls-ID.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt den Befehlsbefehlshandler der Benutzeroberfläche, der cmdID zugeordnet ist, aus dem Befehlsquellobjekt.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommandSource::SendCommand

Sendet eine Nachricht und wartet, bis sie verarbeitet wird, bevor sie zurückgegeben wird.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parameter

*Befehl*<br/>
Die Befehls-ID der zu sendenden Nachricht.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die Nachricht synchron der durch Befehl angegebenen ID zugeordnet. Es ruft CWnd::SendMessage auf, um die Nachricht in der Nachrichtenwarteschlange des Fensters zu platzieren, und wartet, bis diese Fensterprozedur die Nachricht verarbeitet hat, bevor sie zurückkehrt.

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget-Schnittstelle](../../mfc/reference/icommandtarget-interface.md)
