---
title: Icommandui-Schnittstelle
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
ms.openlocfilehash: a7bb3ab5ed292cef8108e937e67bc9e2ccc1ebce
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426660"
---
# <a name="icommandui-interface"></a>Icommandui-Schnittstelle

Verwaltet Befehle der Benutzeroberfläche.

## <a name="syntax"></a>Syntax

```
interface class ICommandUI
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[icommandui__Check](#check)|Legt das Element der Benutzeroberfläche für diesen Befehl auf den entsprechenden Prüf Zustand fest.|
|[Icommandui:: continuerouting](#continuerouting)|Weist den Befehls Routing Mechanismus an, das Routing der aktuellen Nachricht weiter nach unten in der Kette von Handlern durchzuführen.|
|[Icommandui:: aktiviert](#enabled)|Aktiviert oder deaktiviert das Benutzeroberflächen Element für diesen Befehl.|
|[Icommandui:: ID](#id)|Ruft die ID des Benutzeroberflächen Objekts ab, das durch das `ICommandUI`-Objekt dargestellt wird.|
|[Icommandui:: Index](#index)|Ruft den Index des Benutzeroberflächen Objekts ab, das durch das `ICommandUI`-Objekt dargestellt wird.|
|[Icommandui:: Radio](#radio)|Legt das Element der Benutzeroberfläche für diesen Befehl auf den entsprechenden Prüf Zustand fest.|
|[Icommandui:: Text](#text)|Legt den Text des Benutzeroberflächen Elements für diesen Befehl fest.|

## <a name="remarks"></a>Hinweise

Diese Schnittstelle stellt Methoden und Eigenschaften bereit, mit denen Benutzeroberflächen Befehle verwaltet werden. `ICommandUI` ähnelt der [CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md), mit der Ausnahme, dass `ICommandUI` für MFC-Anwendungen verwendet wird, die mit .NET-Komponenten zusammenarbeiten.

`ICommandUI` wird innerhalb eines ON_UPDATE_COMMAND_UI Handlers in einer von [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)abgeleiteten Klasse verwendet. Wenn ein Benutzer einer Anwendung ein Menü aktiviert (auswählt oder klickt), wird jedes Menü Element als aktiviert oder deaktiviert angezeigt. Das Ziel der einzelnen Menübefehle bietet diese Informationen durch Implementieren eines ON_UPDATE_COMMAND_UI Handlers. Verwenden Sie für jedes Befehls Benutzeroberflächen Objekt in der Anwendung den Klassen- [Assistenten](mfc-class-wizard.md) , um einen Meldungs Zuordnungs Eintrag und einen Funktionsprototyp für jeden Handler zu erstellen.

Weitere Informationen zur Verwendung der `ICommandUI`-Schnittstelle im Befehls Routing finden Sie unter Gewusst [wie: Hinzufügen von Befehls Routing zum Windows Forms-Steuer](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)Element.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Weitere Informationen zur Verwaltung von Benutzeroberflächen Befehlen in MFC finden Sie unter [CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md).

## <a name="check"></a>Icommandui:: Check

Legt das Element der Benutzeroberfläche für diesen Befehl auf den entsprechenden Prüf Zustand fest.
```
property UICheckState Check;
```

## <a name="remarks"></a>Hinweise

Mit dieser Eigenschaft wird das Benutzeroberflächen Element für diesen Befehl auf den entsprechenden Prüf Zustand festgelegt. Legen Sie die Option auf die folgenden Werte fest:
- 0 deaktivieren
- 1 Überprüfung
- 2 Festlegen von unbestimmtem

## <a name="continuerouting"></a>Icommandui:: continuerouting

Weist den Befehls Routing Mechanismus an, das Weiterleiten der aktuellen Nachricht an die Kette von Handlern weiterzuleiten.
```
void ContinueRouting();
```

## <a name="remarks"></a>Hinweise

Dabei handelt es sich um eine erweiterte Member-Funktion, die in Verbindung mit einem ON_COMMAND_EX Handler verwendet werden sollte, der false zurückgibt. Weitere Informationen finden Sie unter Technical Note TN006: Message Maps.

## <a name="enabled"></a>Icommandui:: aktiviert

Aktiviert oder deaktiviert das Benutzeroberflächen Element für diesen Befehl.
```
property bool Enabled;
```

## <a name="remarks"></a>Hinweise

Diese Eigenschaft aktiviert oder deaktiviert das Benutzeroberflächen Element für diesen Befehl. Legen Sie "aktiviert" auf "true" fest, um das Element zu aktivieren.

## <a name="id"></a>Icommandui:: ID

Ruft die ID des Benutzeroberflächen Objekts ab, das durch das icommandui-Objekt dargestellt wird.
```
property unsigned int ID;
```

## <a name="remarks"></a>Hinweise

Diese Eigenschaft ruft die ID (ein Handle) des Menü Elements, der Symbolleisten-Schaltfläche oder eines anderen Benutzeroberflächen Objekts ab, das durch das icommandui-Objekt dargestellt wird.

## <a name="index"></a>Icommandui:: Index

Ruft den Index des Benutzeroberflächen Objekts ab, das durch das icommandui-Objekt dargestellt wird.
```
property unsigned int Index;
```

## <a name="remarks"></a>Hinweise

Diese Eigenschaft ruft den Index (ein Handle) des Menü Elements, der Symbolleisten-Schaltfläche oder eines anderen Benutzeroberflächen Objekts ab, das durch das icommandui-Objekt dargestellt wird.

## <a name="radio"></a>Icommandui:: Radio

Legt das Element der Benutzeroberfläche für diesen Befehl auf den entsprechenden Prüf Zustand fest.
```
property bool Radio;
```

## <a name="remarks"></a>Hinweise

Mit dieser Eigenschaft wird das Benutzeroberflächen Element für diesen Befehl auf den entsprechenden Prüf Zustand festgelegt. Legen Sie Radio auf true fest, um das Element zu aktivieren. andernfalls false.

## <a name="text"></a>Icommandui:: Text

Legt den Text des Benutzeroberflächen Elements für diesen Befehl fest.
```
property String^ Text;
```

## <a name="remarks"></a>Hinweise

Diese Eigenschaft legt den Text des Benutzeroberflächen Elements für diesen Befehl fest. Legen Sie Text auf ein Textzeichen folgen Handle fest.

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwinforms. h (definiert in Assembly atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Siehe auch

[CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md)
