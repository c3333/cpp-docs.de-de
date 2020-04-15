---
title: Implementieren eines Dialogfelds
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319472"
---
# <a name="implementing-a-dialog-box"></a>Implementieren eines Dialogfelds

Es gibt zwei Möglichkeiten, Ihrem ATL-Projekt ein Dialogfeld hinzuzufügen: Verwenden Sie den ATL-Dialog-Assistenten oder fügen Sie ihn manuell hinzu.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Hinzufügen eines Dialogfelds mit dem ATL-Dialog-Assistenten

Wählen Sie im [Dialogfeld Klassen hinzufügen](../ide/add-class-dialog-box.md)das ATL-Dialogobjekt aus, um Ihrem ATL-Projekt ein Dialogfeld hinzuzufügen. Füllen Sie den ATL-Dialog-Assistenten entsprechend aus, und klicken Sie auf **Fertig stellen**. Der Assistent fügt Ihrem Projekt eine von [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) abgeleitete Klasse hinzu. Öffnen Sie die **Ressourcenansicht** im Menü **Ansicht,** suchen Sie das Dialogfeld, und doppelklicken Sie darauf, um es im Ressourcen-Editor zu öffnen.

> [!NOTE]
> Wenn Ihr Dialogfeld `CAxDialogImpl`von abgeleitet ist, kann es sowohl ActiveX- als auch Windows-Steuerelemente hosten. Wenn Sie den Overhead der ActiveX-Steuerelementunterstützung in Ihrer Dialogfeldklasse nicht benötigen, verwenden Sie stattdessen [CSimpleDialog](../atl/reference/csimpledialog-class.md) oder [CDialogImpl.](../atl/reference/cdialogimpl-class.md)

Nachrichten- und Ereignishandler können Ihrer Dialogklasse aus der Klassenansicht hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen eines ATL-Nachrichtenhandlers](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Manuelles Hinzufügen eines Dialogfelds

Das Implementieren eines Dialogfelds ähnelt dem Implementieren eines Fensters. Sie leiten eine Klasse entweder von [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)oder [CSimpleDialog](../atl/reference/csimpledialog-class.md) ab und deklarieren eine [Nachrichtenzuordnung](../atl/message-maps-atl.md) für die Verarbeitung von Nachrichten. Sie müssen jedoch auch eine Dialogfeldvorlagenressourcen-ID in der abgeleiteten Klasse angeben. Ihre Klasse muss über `IDD` einen Datenmember verfügen, der aufgerufen wird, um diesen Wert zu halten.

> [!NOTE]
> Wenn Sie ein Dialogfeld mit dem ATL-Dialog-Assistenten erstellen, fügt der Assistent das `IDD` Element automatisch als **Enumerattyp** hinzu.

`CDialogImpl`können Sie ein modales oder ein modusloses Dialogfeld implementieren, das Windows-Steuerelemente hostet. `CAxDialogImpl`ermöglicht das Implementieren eines modalen oder moduslosen Dialogfelds, das sowohl ActiveX- als auch Windows-Steuerelemente hostet.

Um ein modales Dialogfeld zu `CDialogImpl`erstellen, erstellen `CAxDialogImpl`Sie eine Instanz Ihrer -derived (oder -derived) Klasse und rufen Sie dann die [DoModal-Methode](../atl/reference/cdialogimpl-class.md#domodal) auf. Um ein modales Dialogfeld zu schließen, rufen Sie die [EndDialog-Methode](../atl/reference/cdialogimpl-class.md#enddialog) von einem Nachrichtenhandler auf. Um ein modusloses Dialogfeld zu erstellen, `DoModal`rufen Sie die [Create-Methode](../atl/reference/cdialogimpl-class.md#create) anstelle auf. Um ein modusloses Dialogfeld zu zerstören, rufen Sie [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)auf.

Sinkende Ereignisse werden automatisch in [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)durchgeführt. Implementieren Sie die Nachrichtenhandler des Dialogfelds wie `CWindowImpl`die Handler in einer -derived-Klasse. Wenn ein nachrichtenspezifischer Rückgabewert vorhanden ist, `LRESULT`geben Sie ihn als zurück. Die `LRESULT` zurückgegebenen Werte werden von ATL für die ordnungsgemäße Handhabung durch den Windows-Dialog-Manager zugeordnet. Weitere Informationen finden Sie im Quellcode für [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) in atlwin.h.

## <a name="example"></a>Beispiel

Die folgende Klasse implementiert ein Dialogfeld:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Siehe auch

[Fensterklassen](../atl/atl-window-classes.md)
