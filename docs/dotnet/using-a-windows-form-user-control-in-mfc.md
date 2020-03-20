---
title: Verwenden eines Windows Form-Benutzersteuerelements in MFC
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: efabbf84778d925ec1de03f5f4ea0ca09185bd81
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2019
ms.locfileid: "79544747"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Verwenden eines Windows Form-Benutzersteuerelements in MFC

Mithilfe der MFC-Windows Forms Unterstützungs Klassen können Sie Windows Forms Steuerelemente innerhalb ihrer MFC-Anwendungen als ActiveX-Steuerelement in MFC-Dialogfeldern oder-Ansichten hosten. Außerdem können Windows Forms Formulare als MFC-Dialogfelder gehostet werden.

In den folgenden Abschnitten wird Folgendes beschrieben:

- Hosten Sie ein Windows Forms-Steuerelement in einem MFC-Dialogfeld.

- Hosten Sie ein Windows Forms Benutzer Steuer Elements als MFC-Ansicht.

- Hosten Sie ein Windows Forms Formular als MFC-Dialogfeld.

> [!NOTE]
> Die MFC-Windows Forms Integration funktioniert nur in Projekten, die dynamisch mit MFC verknüpft sind (Projekte, in denen `_AFXDLL` definiert ist).

> [!NOTE]
> Wenn Sie die Anwendung über eine private (geänderte) Kopie der mWindows Forms FC-dll (mfcmifc80. dll) erstellen, kann Sie nicht im GAC installiert werden, es sei denn, Sie ersetzen den Microsoft-Schlüssel durch ihren eigenen Anbieter Schlüssel. Weitere Informationen zum Signieren der Assembly finden Sie unter [Programmieren mit](/dotnet/framework/app-domains/programming-with-assemblies) Assemblys und Assemblys mit [starkem Namen (Assemblysignierung)C++(/CLI](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)

Wenn Ihre MFC-Anwendung Windows Forms verwendet, müssen Sie mfcmifc80. dll mit Ihrer Anwendung verteilen. Weitere Informationen finden Sie unter [weiterverteilen der MFC-Bibliothek](../windows/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Hosten eines Windows Form-Benutzersteuerelements in einem MFC-Dialogfeld](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hosten eines Windows Form-Benutzersteuerelements als MFC-Dialogfeld](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Verweis

[CWinFormsControl-Klasse](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog-Klasse](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView-Klasse](../mfc/reference/cwinformsview-class.md)

[ICommandSource-Schnittstelle](../mfc/reference/icommandsource-interface.md)

[ICommandTarget-Schnittstelle](../mfc/reference/icommandtarget-interface.md)

[ICommandUI-Schnittstelle](../mfc/reference/icommandui-interface.md)

[IView-Schnittstelle](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Verwandte Abschnitte

[Windows Forms](/dotnet/framework/winforms/index)

[Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](../mfc/user-interface-elements-mfc.md)<br/>
[Formular Ansichten](../mfc/form-views-mfc.md)
