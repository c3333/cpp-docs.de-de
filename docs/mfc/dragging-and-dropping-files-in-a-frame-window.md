---
title: Ziehen und Fallenlassen von Dateien in einem Rahmenfenster
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 42f21e2441f8ba3d2c6a13503c928880fe100f04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623155"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Ziehen und Fallenlassen von Dateien in einem Rahmenfenster

Das Rahmen Fenster verwaltet eine Beziehung mit dem Datei-Explorer oder Datei-Manager.

Durch das Hinzufügen einiger initialisierender Aufrufe in der Überschreibung der `CWinApp` Member `InitInstance` -Funktion, wie in [CWinApp: der Application-Klasse](cwinapp-the-application-class.md)beschrieben, kann Ihr Rahmen Fenster indirekt Dateien öffnen, die aus dem Datei-Explorer oder Datei-Manager gezogen und im Rahmen Fenster abgelegt werden. Siehe [Drag](special-cwinapp-services.md)& amp; Drop des Datei-Managers.

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
