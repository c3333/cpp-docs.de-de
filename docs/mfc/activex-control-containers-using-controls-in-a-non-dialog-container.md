---
title: 'ActiveX-Steuerelementcontainer: Verwenden von Steuerelementen in Containern, die keine Dialogfelder sind'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: b010c35f32462810cbdb008e5688d4b41254fad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620772"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX-Steuerelementcontainer: Verwenden von Steuerelementen in Containern, die keine Dialogfelder sind

In einigen Anwendungen, wie z. b. einer SDI-oder MDI-Anwendung, empfiehlt es sich, ein-Steuerelement in ein Fenster der Anwendung einzubetten. Die **Create** Member-Funktion der Wrapper Klasse, die von Visual C++ eingefügt wird, kann eine Instanz des Steuer Elements dynamisch erstellen, ohne dass ein Dialogfeld erforderlich ist.

Die **Create** Member-Funktion verfügt über die folgenden Parameter:

*lpszWindowName*<br/>
Ein Zeiger auf den Text, der in der Text-oder Caption-Eigenschaft des Steuer Elements angezeigt werden soll (sofern vorhanden).

*dwstyle*<br/>
Windows-Stile. Eine vollständige Liste finden Sie unter [CWnd:: kreatecontrol](reference/cwnd-class.md#createcontrol).

*Rect*<br/>
Gibt die Größe und Position des Steuer Elements an.

*pparser*<br/>
Gibt das übergeordnete Fenster des Steuer Elements an, in der Regel ein `CDialog` . Er darf nicht **null**sein.

*nID*<br/>
Gibt die Steuerelement-ID an und kann vom Container verwendet werden, um auf das Steuerelement zu verweisen.

Ein Beispiel für die Verwendung dieser Funktion zum dynamischen Erstellen eines ActiveX-Steuer Elements wäre eine Formularansicht einer SDI-Anwendung. Anschließend können Sie eine Instanz des Steuer Elements im `WM_CREATE` Anwendungs Handler erstellen.

In diesem Beispiel `CMyView` ist die Haupt Ansichts Klasse, `CCirc` ist die Wrapper Klasse und Circ. H ist der-Header (. H) der Wrapper Klasse.

Das Implementieren dieses Features ist ein vierstufiger Prozess.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>So erstellen Sie ein ActiveX-Steuerelement in einem nicht-Dialogfenster dynamisch

1. Fügen Sie CIRC ein. H in CMyView. H, direkt vor der `CMyView` Klassendefinition:

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Fügen Sie `CCirc` dem geschützten Abschnitt der `CMyView` Klassendefinition in CMyView eine Element Variable (vom Typ) hinzu. Micha

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Fügen Sie der Klasse einen Meldungs `WM_CREATE` Handler hinzu `CMyView` .

1. Führen Sie in der Handlerfunktion `CMyView::OnCreate` einen Befehl an die-Funktion des-Steuer Elements aus, `Create` indem Sie den **this** -Zeiger als übergeordnetes Fenster verwenden:

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Erstellen Sie das Projekt neu. Wenn die Ansicht der Anwendung erstellt wird, wird automatisch ein CIRC-Steuerelement erstellt.

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](activex-control-containers.md)
