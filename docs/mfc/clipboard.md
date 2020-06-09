---
title: Zwischenablage
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 5f4a17bedaa50913dce1f6388dfb6b8d9ecd38da
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617289"
---
# <a name="clipboard"></a>Zwischenablage

In dieser Artikel Familie wird erläutert, wie die Unterstützung für die Windows-Zwischenablage in MFC-Anwendungen implementiert wird. Die Windows-Zwischenablage wird auf zweierlei Weise verwendet:

- Implementieren von Standard Befehlen zum Bearbeiten von Menüs, z. b. Ausschneiden, kopieren und einfügen.

- Implementieren von einheitlicher Datenübertragung mit OLE Drag & Drop.

Die Zwischenablage ist die standardmäßige Windows-Methode zum Übertragen von Daten zwischen einer Quelle und einem Ziel. Dies kann auch bei OLE-Vorgängen sehr nützlich sein. Mit der Einführung von OLE gibt es zwei Zwischenablage Mechanismen in Windows. Die standardmäßige Windows-Zwischenablage-API ist weiterhin verfügbar, wurde jedoch mit dem OLE-Datenübertragungsmechanismus ergänzt. OLE Uniform Data Transfer (UDT) unterstützt Ausschneiden, kopieren und Einfügen mit der Zwischenablage und Drag & Drop.

Die Zwischenablage ist ein Systemdienst, der von der gesamten Windows-Sitzung gemeinsam verwendet wird, sodass Sie nicht über ein Handle oder eine eigene Klasse verfügt. Sie verwalten die Zwischenablage mithilfe von Element Funktionen der [CWnd](reference/cwnd-class.md)-Klasse.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Verwendung der einzelnen Zwischenablage Mechanismen](clipboard-when-to-use-each-clipboard-mechanism.md)

- [Verwenden der herkömmlichen Windows-Zwischenablage-API](clipboard-using-the-windows-clipboard.md)

- [Verwenden des OLE-Zwischenablage Mechanismus](clipboard-using-the-ole-clipboard-mechanism.md)

- [Kopieren und Einfügen von Daten](clipboard-copying-and-pasting-data.md)

- [Hinzufügen anderer Formate](clipboard-adding-other-formats.md)

- [Die Windows-Zwischenablage](/windows/win32/dataxchg/clipboard)

- [Drag &amp; Drop (OLE)](drag-and-drop-ole.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)
