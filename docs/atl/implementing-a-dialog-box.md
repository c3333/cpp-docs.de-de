---
title: Implementieren eines Dialog Felds
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: fa7b4122b513d48194dedeb39daecd1dfd7223eb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499575"
---
# <a name="implementing-a-dialog-box"></a>Implementieren eines Dialog Felds

Es gibt zwei Möglichkeiten, Ihrem ATL-Projekt ein Dialogfeld hinzuzufügen: Verwenden Sie den ATL-Dialog-Assistenten, oder fügen Sie ihn manuell hinzu.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Hinzufügen eines Dialog Felds mit dem ATL-Dialogfeld-Assistenten

Wählen Sie im [Dialogfeld Klasse hinzufügen](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)das ATL-Dialogfeld Objekt aus, um dem ATL-Projekt ein Dialogfeld hinzuzufügen. Füllen Sie den ATL-Dialog Feld-Assistenten aus, und klicken Sie auf **Fertig**stellen. Der Assistent fügt dem Projekt eine Klasse hinzu, die von [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) abgeleitet wurde. Öffnen Sie **Ressourcenansicht** im Menü Ansicht, suchen Sie das Dialog **Feld** , und doppelklicken Sie darauf, um es im Ressourcen-Editor zu öffnen.

> [!NOTE]
> Wenn das Dialogfeld von abgeleitet ist `CAxDialogImpl` , kann es sowohl ActiveX-als auch Windows-Steuerelemente hosten. Wenn Sie den Aufwand für die Unterstützung von ActiveX-Steuerelementen in der Dialogfeld Klasse nicht benötigen, verwenden Sie stattdessen [CSimpleDialog](../atl/reference/csimpledialog-class.md) oder [CDialogImpl](../atl/reference/cdialogimpl-class.md) .

Nachrichten-und Ereignishandler können aus Klassenansicht zu ihrer Dialogfeld Klasse hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen eines ATL-Nachrichten Handlers](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Manuelles Hinzufügen eines Dialog Felds

Das Implementieren eines Dialog Felds ähnelt dem Implementieren eines Fensters. Sie [leiten eine Klasse](../atl/message-maps-atl.md) von [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)oder [CSimpleDialog](../atl/reference/csimpledialog-class.md) ab und deklarieren eine Meldungs Zuordnung, um Nachrichten zu verarbeiten. Sie müssen jedoch auch eine Ressourcen-ID für die Dialogfeld Vorlage in der abgeleiteten Klasse angeben. Die Klasse muss über einen Datenmember mit dem Namen verfügen `IDD` , um diesen Wert zu speichern.

> [!NOTE]
> Wenn Sie ein Dialogfeld mit dem ATL-Dialogfeld-Assistenten erstellen, fügt der Assistent den `IDD` Member automatisch als **`enum`** Typ hinzu.

`CDialogImpl` ermöglicht es Ihnen, ein modales oder nicht modales Dialogfeld zu implementieren, das Windows-Steuerelemente hostet. `CAxDialogImpl` ermöglicht die Implementierung eines modalen oder nicht modalen Dialog Felds, das sowohl ActiveX-als auch Windows-Steuerelemente hostet.

Um ein modales Dialogfeld zu erstellen, erstellen Sie eine Instanz der von `CDialogImpl` abgeleiteten (oder `CAxDialogImpl` abgeleiteten) Klasse, und rufen Sie dann die [DoModal](../atl/reference/cdialogimpl-class.md#domodal) -Methode auf. Um ein modales Dialogfeld zu schließen, müssen Sie die [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) -Methode von einem Nachrichten Handler aus abrufen. Um ein nicht modalem Dialogfeld zu erstellen, rufen Sie die [Create](../atl/reference/cdialogimpl-class.md#create) -Methode anstelle von auf `DoModal` . Um ein nicht modalem Dialogfeld zu zerstören, nennen Sie [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Sink-Ereignisse werden automatisch in [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)ausgeführt. Implementieren Sie die Meldungs Handler des Dialog Felds wie die Handler in einer von `CWindowImpl` abgeleiteten Klasse. Wenn ein Nachrichten spezifischer Rückgabewert vorhanden ist, geben Sie ihn als zurück `LRESULT` . Die zurückgegebenen `LRESULT` Werte werden von ATL für die ordnungsgemäße Handhabung durch den Windows-Dialog-Manager zugeordnet. Weitere Informationen finden Sie im Quellcode für [cdialogimplbaset::D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) in atlwin. h.

## <a name="example"></a>Beispiel

Die folgende Klasse implementiert ein Dialogfeld:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Weitere Informationen

[Fenster Klassen](../atl/atl-window-classes.md)
