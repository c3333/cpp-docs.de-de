---
title: Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: bf91730f98685935d50ee0076739b436e8d9da60
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544784"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht

MFC verwendet die CWinFormsView-Klasse, um ein Windows Forms Benutzer Steuerelement in einer MFC-Ansicht zu hosten. MFC-Windows Forms Ansichten sind ActiveX-Steuerelemente. Das Benutzer Steuerelement wird als untergeordnetes Element der nativen Ansicht gehostet und belegt den gesamten Client Bereich der systemeigenen Ansicht.

Das Endergebnis ähnelt dem Modell, das von der [CFormView-Klasse](../mfc/reference/cformview-class.md)verwendet wird. Auf diese Weise können Sie den Windows Forms-Designer und die Laufzeit nutzen, um umfangreiche Formular basierte Sichten zu erstellen.

Da MFC-Windows Forms Ansichten ActiveX-Steuerelemente sind, haben Sie nicht denselben `hwnd` wie MFC-Sichten. Außerdem können Sie nicht als Zeiger auf eine [CView](../mfc/reference/cview-class.md) -Ansicht übergeben werden. Verwenden Sie im Allgemeinen .NET Framework Methoden, um mit Windows Forms Sichten zu arbeiten und sich weniger auf Win32 zu verlassen.

Eine Beispielanwendung, die Windows Forms anzeigt, die mit MFC verwendet werden, finden Sie unter [MFC-und Windows Forms-Integration](https://www.microsoft.com/download/details.aspx?id=2113).

## <a name="in-this-section"></a>In diesem Abschnitt

[Vorgehensweise: Erstellen des Benutzersteuerelements und Hosten der MDI-Ansicht](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Vorgehensweise: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Vorgehensweise: Aufrufen von Ereignissen und Methoden des Windows Forms-Steuerelements](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Siehe auch

[Verwenden eines Windows Form-Benutzersteuerelements in MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Gewusst wie: Erstellen von zusammengesetzten Steuerelementen](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
