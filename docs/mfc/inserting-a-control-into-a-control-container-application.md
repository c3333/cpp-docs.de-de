---
title: 'ActiveX-Steuerelementcontainer: Einfügen eines Steuerelements in eine Steuerelementcontainer-Anwendung'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: e8426fd7a420ef06650930e547d06c78cc094975
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503095"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX-Steuerelementcontainer: Einfügen eines Steuerelements in eine Steuerelementcontainer-Anwendung

Bevor Sie von einer ActiveX-Steuerelement Container-Anwendung aus auf ein ActiveX-Steuerelement zugreifen können, müssen Sie das ActiveX-Steuerelement mithilfe des Dialog Felds [ActiveX-Steuerelement einfügen](../windows/adding-editing-or-deleting-controls.md) zur Containeranwendung hinzufügen.

Informationen zum Hinzufügen eines ActiveX-Steuer Elements zum ActiveX-Steuerelement Container Projekt finden Sie unter [anzeigen und Hinzufügen von ActiveX-Steuerelementen zu einem Dialog Feld](../windows/adding-editing-or-deleting-controls.md)

Nachdem Sie das Steuerelement hinzugefügt haben, müssen Sie der Dialogfeld Klasse eine Element Variable (des ActiveX-Steuerelement Typs) hinzufügen. Weitere Informationen zu diesem Verfahren finden Sie unter [Hinzufügen einer Element Variablen](../ide/adding-a-member-variable-visual-cpp.md).

Nachdem Sie die Element Variable hinzugefügt haben, wird eine Klasse, die als Wrapper Klasse bezeichnet wird, automatisch generiert und Ihrem Projekt hinzugefügt. Diese Klasse wird als Schnittstelle zwischen dem Steuerelement Container und dem eingebetteten Steuerelement verwendet.

## <a name="see-also"></a>Weitere Informationen

[ActiveX-Steuerelement Container](activex-control-containers.md)
