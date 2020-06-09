---
title: Anpassung für MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 3b7597c3709ed700e82af94c78450ee5aff2d99b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622960"
---
# <a name="customization-for-mfc"></a>Anpassung für MFC

Dieses Thema enthält Tipps zum Anpassen einer MFC-Anwendung.

## <a name="general-customizations"></a>Allgemeine Anpassungen

Sie können den Status der Anwendung speichern und in die Registrierung laden. Wenn Sie diese Option aktivieren, lädt Ihre Anwendung ihren ursprünglichen Zustand aus der Registrierung. Wenn Sie das anfängliche Andock Layout für Ihre Anwendung ändern, müssen Sie die Registrierungsdaten für die Anwendung löschen. Andernfalls überschreiben die Daten in der Registrierung alle Änderungen, die Sie am ursprünglichen Layout vorgenommen haben.

## <a name="class-specific-customizations"></a>Klassenspezifische Anpassungen

Weitere Anpassungs Tipps finden Sie in den folgenden Themen:

- [CBasePane-Klasse](reference/cbasepane-class.md)

- [CDockablePane-Klasse](reference/cdockablepane-class.md)

- [CDockingManager-Klasse](reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl Class](reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Weitere Tipps zur Anpassung

[Anpassung der Tastatur und Maus](keyboard-and-mouse-customization.md)

[Benutzerdefinierte Tools](user-defined-tools.md)

## <a name="see-also"></a>Siehe auch

[MFC-Desktopanwendungen](mfc-desktop-applications.md)<br/>
[Sicherheitsauswirkungen der Anpassung](security-implications-of-customization.md)
