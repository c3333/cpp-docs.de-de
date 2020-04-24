---
title: ICommandUI-Schnittstelle
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751308"
---
# <a name="icommandui-interface"></a>ICommandUI-Schnittstelle

Verwaltet Benutzeroberflächenbefehle.

## <a name="syntax"></a>Syntax

```
interface class ICommandUI
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[icommandui__Check](#check)|Legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest.|
|[ICommandUI::Weiterrouting](#continuerouting)|Weist den Befehlsroutingmechanismus an, die aktuelle Nachricht weiterhin über die Kette der Handler weiterzuleiten.|
|[ICommandUI::Aktiviert](#enabled)|Aktiviert oder deaktiviert das Benutzeroberflächenelement für diesen Befehl.|
|[ICommandUI::ID](#id)|Ruft die ID des Benutzeroberflächenobjekts ab, das durch das Objekt dargestellt wird. `ICommandUI`|
|[ICommandUI::Index](#index)|Ruft den Index des Benutzeroberflächenobjekts ab, das durch das Objekt dargestellt wird. `ICommandUI`|
|[ICommandUI::Radio](#radio)|Legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest.|
|[ICommandUI::Text](#text)|Legt den Text des Benutzeroberflächenelements für diesen Befehl fest.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle stellt Methoden und Eigenschaften bereit, die Benutzeroberflächenbefehle verwalten. `ICommandUI`ist der [CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md) `ICommandUI` ähnlich, mit der Ausnahme, dass sie für MFC-Anwendungen verwendet wird, die mit .NET-Komponenten zusammenarbeiten.

`ICommandUI`wird in einem ON_UPDATE_COMMAND_UI-Handler in einer [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-derived-Klasse verwendet. Wenn ein Benutzer einer Anwendung ein Menü aktiviert (auswählt oder anklickt), wird jedes Menüelement als aktiviert oder deaktiviert angezeigt. Das Ziel jedes Menübefehls stellt diese Informationen bereit, indem ein ON_UPDATE_COMMAND_UI-Handler implementiert wird. Verwenden Sie für jedes der Benutzeroberflächenobjekte in Ihrer Anwendung den [Klassen-Assistenten,](mfc-class-wizard.md) um für jeden Handler einen Nachrichtenzuordnungseintrag und einen Funktionsprototyp zu erstellen.

Weitere Informationen zur `ICommandUI` Verwendung der Schnittstelle im Befehlsrouting finden Sie unter [Gewusst wie: Hinzufügen von Befehlsrouting zum Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Weitere Informationen dazu, wie Benutzeroberflächenbefehle in MFC verwaltet werden, finden Sie unter [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI::Überprüfen

Legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest.

```
property UICheckState Check;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest. Legen Sie Überprüfen auf die folgenden Werte fest:

- 0 Deaktivieren
- 1 Prüfung
- 2 Set unbestimmt

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI::Weiterrouting

Weist den Befehlsroutingmechanismus an, die aktuelle Nachricht weiterhin über die Kette der Handler weiterzuleiten.

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>Bemerkungen

Dies ist eine erweiterte Memberfunktion, die in Verbindung mit einem ON_COMMAND_EX-Handler verwendet werden sollte, der FALSE zurückgibt. Weitere Informationen finden Sie unter Technische Hinweise TN006: Nachrichtenzuordnungen.

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI::Aktiviert

Aktiviert oder deaktiviert das Benutzeroberflächenelement für diesen Befehl.

```
property bool Enabled;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft aktiviert oder deaktiviert das Benutzeroberflächenelement für diesen Befehl. Set Aktiviert auf TRUE, um das Element zu aktivieren, FALSE, um es zu deaktivieren.

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI::ID

Ruft die ID des Benutzeroberflächenobjekts ab, das durch das ICommandUI-Objekt dargestellt wird.

```
property unsigned int ID;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft ruft die ID (ein Handle) des Menüelements, der Symbolleistenschaltfläche oder eines anderen Benutzeroberflächenobjekts ab, das durch das ICommandUI-Objekt dargestellt wird.

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI::Index

Ruft den Index des Benutzeroberflächenobjekts ab, das durch das ICommandUI-Objekt dargestellt wird.

```
property unsigned int Index;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft ruft den Index (ein Handle) des Menüelements, der Symbolleistenschaltfläche oder eines anderen Benutzeroberflächenobjekts ab, das durch das ICommandUI-Objekt dargestellt wird.

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::Radio

Legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest.

```
property bool Radio;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft legt das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfstatus fest. Setzen Sie Radio auf TRUE, um das Element zu aktivieren; andernfalls FALSE.

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI::Text

Legt den Text des Benutzeroberflächenelements für diesen Befehl fest.

```
property String^ Text;
```

## <a name="remarks"></a>Bemerkungen

Diese Eigenschaft legt den Text des Benutzeroberflächenelements für diesen Befehl fest. Legen Sie Text auf einen Textzeichenfolgenhandle fest.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="see-also"></a>Weitere Informationen

[CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md)
