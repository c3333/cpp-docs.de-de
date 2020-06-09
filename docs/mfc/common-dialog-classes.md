---
title: Standarddialogfeld-Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 2efe095a6d5b71321cbbe56fdee662509baa4573
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619026"
---
# <a name="common-dialog-classes"></a>Standarddialogfeld-Klassen

Zusätzlich zur [CDialog](reference/cdialog-class.md)-Klasse stellt MFC mehrere von abgeleitete Klassen bereit `CDialog` , die häufig verwendete Dialogfelder Kapseln, wie in der folgenden Tabelle dargestellt. Die gekapselten Dialogfelder werden als "allgemeine Dialogfelder" bezeichnet und sind Teil der allgemeinen Windows-Dialogfeld Bibliothek (kommdlg). DLL). Die Dialogfeld Vorlagen-Ressourcen und der Code für diese Klassen werden in den allgemeinen Windows-Dialogfeldern bereitgestellt, die Teil der Windows-Versionen 3,1 und höher sind.

### <a name="common-dialog-classes"></a>Standarddialogfeld-Klassen

|Abgeleitete Dialogfeld Klasse|Zweck|
|--------------------------|-------------|
|[CColorDialog](reference/ccolordialog-class.md)|Ermöglicht Benutzern das Auswählen von Farben.|
|[CFileDialog](reference/cfiledialog-class.md)|Ermöglicht Benutzern das Auswählen eines Datei namens, der geöffnet oder gespeichert werden soll.|
|[CFindReplaceDialog](reference/cfindreplacedialog-class.md)|Ermöglicht Benutzern das Initiieren eines Such-oder Ersetzungs Vorgangs in einer Textdatei.|
|[CFontDialog](reference/cfontdialog-class.md)|Ermöglicht Benutzern das Angeben einer Schriftart.|
|[CPrintDialog](reference/cprintdialog-class.md)|Ermöglicht Benutzern das Angeben von Informationen für einen Druckauftrag.|
|[CPrintDialogEx](reference/cprintdialogex-class.md)|Eigenschaften Blatt für Windows-Druck.|

Weitere Informationen zu den allgemeinen Dialog Klassen finden Sie unter den einzelnen Klassennamen in der *MFC-Referenz*. MFC bietet auch eine Reihe von Standarddialog Klassen, die für OLE verwendet werden. Weitere Informationen zu diesen Klassen finden Sie in der *MFC-Referenz*in der Basisklasse [COleDialog](reference/coledialog-class.md).

Drei andere Klassen in MFC verfügen über Dialog ähnliche Merkmale. Informationen zu den Klassen [CFormView](reference/cformview-class.md), [CRecordView](reference/crecordview-class.md)und [CDaoRecordView](reference/cdaorecordview-class.md)finden Sie in den Klassen in der *MFC-Referenz*. Weitere Informationen über die [CDialogBar](reference/cdialogbar-class.md)-Klasse finden Sie unter [Dialog leisten](dialog-bars.md).

## <a name="see-also"></a>Siehe auch

[Dialog Felder](dialog-boxes.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)<br/>
[Dialogfelder in OLE](dialog-boxes-in-ole.md)
