---
title: Hosten eines Windows Form-Benutzersteuerelements in einem MFC-Dialogfeld
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 8925b86a5920df6a53a2625b782cf41e1a7fe32c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544790"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hosten eines Windows Form-Benutzersteuerelements in einem MFC-Dialogfeld

MFC hostet ein Windows Forms-Steuerelement als spezielle Art des ActiveX-Steuer Elements und kommuniziert mit dem-Steuerelement mithilfe von ActiveX-Schnittstellen und Eigenschaften und Methoden der <xref:System.Windows.Forms.Control>-Klasse. Es wird empfohlen, dass Sie .NET Framework Eigenschaften und-Methoden verwenden, um auf dem Steuerelement zu arbeiten.

Eine Beispielanwendung, die Windows Forms anzeigt, die mit MFC verwendet werden, finden Sie unter [MFC-und Windows Forms-Integration](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
>  In der aktuellen Version kann ein `CDialogBar`-Objekt keine Windows Forms Steuerelemente hosten.

## <a name="in-this-section"></a>In diesem Abschnitt

[Vorgehensweise: Erstellen des Benutzersteuerelements und des Hosts in einem Dialogfeld](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Gewusst wie: DDX/DDV-Datenbindung mit Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Vorgehensweise: Auffangen von Windows Forms-Ereignissen aus nativen C++-Klassen](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Verweis

[CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; -Klasse der [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd-Klasse](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Siehe auch

[Verwenden eines Windows Form-Benutzersteuerelements in MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Unterschiede beim Programmieren mit Windows Forms und MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hosten eines Windows Form-Benutzersteuerelements als MFC-Dialogfeld](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
