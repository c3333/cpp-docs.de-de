---
title: Erstellen von nicht modalen Dialogfeldern
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7a6125e84438b0ef2ad541c26bda33051d483c8d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619640"
---
# <a name="creating-modeless-dialog-boxes"></a>Erstellen von nicht modalen Dialogfeldern

Für ein nicht modalem Dialogfeld müssen Sie in der Dialogfeld Klasse einen eigenen öffentlichen Konstruktor angeben. Um ein nicht modalem Dialogfeld zu erstellen, rufen Sie Ihren öffentlichen Konstruktor auf, und rufen Sie dann die [Create](reference/cdialog-class.md#create) Member-Funktion des Dialog Objekts auf, um die Dialog Ressource zu laden. Sie können **Create** entweder während oder nach dem konstruktorbefehl aufzurufen. Wenn die Dialogfeld Ressource die-Eigenschaft **WS_VISIBLE**, wird das Dialogfeld sofort angezeigt. Andernfalls müssen Sie die zugehörige [ShowWindow](reference/cwnd-class.md#showwindow) -Member-Funktion aufzurufen.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
