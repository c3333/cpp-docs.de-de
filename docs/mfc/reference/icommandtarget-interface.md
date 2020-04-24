---
title: ICommandTarget-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: be64f4e0367b9ecc1b24fa96f067f4acd45a9978
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751456"
---
# <a name="icommandtarget-interface"></a>ICommandTarget-Schnittstelle

Stellt ein Benutzersteuerelement mit einer Schnittstelle zum Empfangen von Befehlen von einem Befehlsquellobjekt bereit.

## <a name="syntax"></a>Syntax

```
interface class ICommandTarget
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ICommandTarget::Initialisieren](#initialize)|Initialisiert das Befehlszielobjekt.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie ein Benutzersteuerelement in einer MFC-Ansicht hosten, leitet [CWinFormsView](../../mfc/reference/cwinformsview-class.md) Befehle weiter und aktualisiert Befehlsbenutzer-UI-Meldungen an das Benutzersteuerelement, damit es MFC-Befehle verarbeiten kann (z. B. Framemenüelemente und Symbolleistenschaltflächen). Durch `ICommandTarget`implementieren sie , geben Sie dem Benutzersteuerelement einen Verweis auf das [ICommandSource-Objekt.](../../mfc/reference/icommandsource-interface.md)

Weitere Informationen [finden Sie unter Gewusst wie: Hinzufügen von Befehlsrouting zum Windows-Formularsteuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) für ein Beispiel für die Verwendung `ICommandTarget`von .

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommandTarget::Initialisieren

Initialisiert das Befehlszielobjekt.

```cpp
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parameter

*cmdQuelle*<br/>
Ein Handle für das Befehlsquellobjekt.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Benutzersteuerelement in einer MFC-Ansicht hosten, leitet CWinFormsView Befehle weiter und aktualisiert Befehlsbenutzer-UI-Meldungen an das Benutzersteuerelement, damit es MFC-Befehle verarbeiten kann.

Diese Methode initialisiert das Befehlszielobjekt und ordnet es dem angegebenen Befehlsquellobjekt cmdSource zu. Sie sollte in der Implementierung der Benutzersteuerungsklasse aufgerufen werden. Bei der Initialisierung sollten Sie Befehlshandler beim Befehlsquellobjekt registrieren, indem Sie ICommandSource::AddCommandHandler in der Initialize-Implementierung aufrufen. Weitere Informationen finden Sie unter Gewusst wie: Hinzufügen von Befehlsrouting zum Windows-Formularsteuerelement, um ein Beispiel dafür zu finden, wie Sie initialisieren verwenden.

## <a name="see-also"></a>Weitere Informationen

[Vorgehensweise: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource-Schnittstelle](../../mfc/reference/icommandsource-interface.md)
