---
title: Erstellen des Registersteuerelements
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619607"
---
# <a name="creating-the-tab-control"></a>Erstellen des Registersteuerelements

Wie das Registerkarten-Steuerelement erstellt wird, hängt davon ab, ob Sie das Steuerelement in einem Dialogfeld verwenden oder es in einem nicht Dialogfeld erstellen.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>So verwenden Sie CTabCtrl direkt in einem Dialogfeld

1. Fügen Sie im Dialog-Editor der Dialogfeld Vorlagen-Ressource ein Registerkarten-Steuerelement hinzu. Gibt die Steuerelement-ID an.

1. Verwenden Sie den [Assistenten zum Hinzufügen](../ide/adding-a-member-variable-visual-cpp.md) von Element Variablen, um eine Member-Variable vom Typ [CTabCtrl](reference/ctabctrl-class.md) mit der Control-Eigenschaft hinzuzufügen. Sie können diesen Member verwenden, um `CTabCtrl` Member-Funktionen aufzurufen.

1. Zuordnungs Handler-Funktionen in der Dialogfeld Klasse für alle Tabstopps-Benachrichtigungs Meldungen, die Sie behandeln müssen. Weitere Informationen finden Sie unter [Mapping von Nachrichten zu Funktionen](reference/mapping-messages-to-functions.md).

1. Legen Sie in [OnInitDialog](reference/cdialog-class.md#oninitdialog)die Stile für das fest `CTabCtrl` .

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>So verwenden Sie CTabCtrl in einem nicht-Dialogfenster

1. Definieren Sie das Steuerelement in der Ansicht oder in der Fenster Klasse.

1. Rufen Sie die [Create](reference/ctabctrl-class.md#create) Member-Funktion des Steuer Elements (möglicherweise in [OnInitialUpdate](reference/cview-class.md#oninitialupdate)) auf, möglicherweise so früh wie die [OnCreate](reference/cwnd-class.md#oncreate) -Handlerfunktion des übergeordneten Fensters (wenn Sie das Steuerelement Unterklassen). Legen Sie die Stile für das-Steuerelement fest.

Nachdem das `CTabCtrl` Objekt erstellt wurde, können Sie die folgenden erweiterten Stile festlegen oder löschen:

- **TCS_EX_FLATSEPARATORS** Das Registerkarten-Steuerelement zeichnet Trennzeichen zwischen den Registerkarten Elementen. Dieser erweiterte Stil wirkt sich nur auf Registerkarten-Steuerelemente aus, die die Stile **TCS_BUTTONS** und **TCS_FLATBUTTONS** haben. Standardmäßig wird durch das Erstellen des Registerkarten-Steuer Elements mit dem **TCS_FLATBUTTONS** Stil dieser erweiterte Stil festgelegt.

- **TCS_EX_REGISTERDROP** Das Registerkarten-Steuerelement generiert **TCN_GETOBJECT** Benachrichtigungs Meldungen, um ein Ablage Zielobjekt anzufordern, wenn ein Objekt über die Registerkarten Elemente im Steuerelement gezogen wird.

    > [!NOTE]
    >  Um die **TCN_GETOBJECT** Benachrichtigung zu erhalten, müssen Sie die OLE-Bibliotheken mit einem Befehl von [AfxOLEInit](reference/ole-initialization.md#afxoleinit)initialisieren.

Diese Stile können abgerufen und festgelegt werden, nachdem das Steuerelement erstellt wurde, mit den jeweiligen Aufrufen der Element Funktionen [GetExtendedStyle](reference/ctabctrl-class.md#getextendedstyle) und [SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle) .

Legen Sie den **TCS_EX_FLATSEPARATORS** Stil beispielsweise mit den folgenden Codezeilen fest:

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

Löschen Sie den **TCS_EX_FLATSEPARATORS** Stil aus einem- `CTabCtrl` Objekt mit den folgenden Codezeilen:

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

Hierdurch werden die Trennzeichen entfernt, die zwischen den Schaltflächen des Objekts angezeigt werden `CTabCtrl` .

## <a name="see-also"></a>Siehe auch

[Verwenden von CTabCtrl](using-ctabctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
