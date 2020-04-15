---
title: Hosten eines Windows Form-Benutzersteuerelements in einem MFC-Dialogfeld
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374486"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hosten eines Windows Form-Benutzersteuerelements in einem MFC-Dialogfeld

MFC hostet ein Windows Forms-Steuerelement als eine spezielle Art von ActiveX-Steuerelement und kommuniziert mit <xref:System.Windows.Forms.Control> dem Steuerelement mithilfe von ActiveX-Schnittstellen sowie Eigenschaften und Methoden der Klasse. Es wird empfohlen, .NET Framework-Eigenschaften und -Methoden für den Betrieb des Steuerelements zu verwenden.

Eine Beispielanwendung, die Windows Forms zeigt, die mit MFC verwendet wird, finden Sie unter [MFC- und Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
> In der aktuellen `CDialogBar` Version kann ein Objekt keine Windows Forms-Steuerelemente hosten.

## <a name="in-this-section"></a>In diesem Abschnitt

[Vorgehensweise: Erstellen des Benutzersteuerelements und des Hosts in einem Dialogfeld](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Gewusst wie: DDX-/DDV-Datenbindung mit Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Gewusst wie: Auffangen von Windows Forms-Ereignissen aus systemeigenen C++-Klassen](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Verweis

[CWinFormsControl-Klasse](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog-Klasse](../mfc/reference/cdialog-class.md) &#124; [CWnd-Klasse](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Siehe auch

[Verwenden eines Windows Form-Benutzersteuerelements in MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Unterschiede bei Windows Forms/MFC-Programmierung](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hosten einer Windows Form-Benutzersteuerung als MFC-Dialogfeld](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
