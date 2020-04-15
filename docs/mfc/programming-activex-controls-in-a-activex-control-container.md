---
title: 'ActiveX-Steuerelementcontainer: Programmieren von ActiveX-Steuerelementen in einem ActiveX-Steuerelementcontainer'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371187"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX-Steuerelementcontainer: Programmieren von ActiveX-Steuerelementen in einem ActiveX-Steuerelementcontainer

In diesem Artikel wird der Prozess für den Zugriff auf die verfügbar gemachten [Methoden](../mfc/mfc-activex-controls-methods.md) und [Eigenschaften](../mfc/mfc-activex-controls-properties.md) eingebetteter ActiveX-Steuerelemente beschrieben.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Grundsätzlich führen Sie die folgenden Schritte aus:

1. Fügen Sie mithilfe von Gallery [ein ActiveX-Steuerelement in das ActiveX-Containerprojekt](../mfc/inserting-a-control-into-a-control-container-application.md) ein.

1. [Definieren Sie eine Membervariable](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (oder eine andere Zugriffsform) desselben Typs wie die ActiveX-Steuerelement-Wrapperklasse.

1. [Programmieren Sie das ActiveX-Steuerelement](#_core_programming_the_activex_control) mithilfe vordefinierter Memberfunktionen der Wrapperklasse.

Angenommen, Sie haben ein dialogbasiertes Projekt (container) mit ActiveX-Steuerelementunterstützung erstellt. Das Circ-Beispielsteuerelement Circ wird dem resultierenden Projekt hinzugefügt.

Nachdem das Circ-Steuerelement in das Projekt eingefügt wurde (Schritt 1), fügen Sie eine Instanz des Circ-Steuerelements in das Hauptdialogfeld der Anwendung ein.

## <a name="procedures"></a>Prozeduren

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>So fügen Sie das Circ-Steuerelement zur Dialogfeldvorlage hinzu

1. Laden Sie das ActiveX-Steuerelementcontainerprojekt. Verwenden Sie in `Container` diesem Beispiel das Projekt.

1. Klicken Sie auf die Registerkarte Ressourcenansicht.

1. Öffnen Sie den **Dialogordner.**

1. Doppelklicken Sie auf die Vorlage für das Hauptdialogfeld. Verwenden Sie in diesem Beispiel **IDD_CONTAINER_DIALOG**.

1. Klicken Sie auf das Circ-Steuerelementsymbol in der Toolbox.

1. Klicken Sie auf einen Punkt im Dialogfeld, um das Circ-Steuerelement einzufügen.

1. Wählen Sie im Menü **Datei** **alle** speichern aus, um alle Änderungen an der Dialogfeldvorlage zu speichern.

## <a name="modifications-to-the-project"></a>Änderungen am Projekt

Damit die Container-Anwendung auf das Circ-Steuerelement zugreifen kann, fügt`CCirc`Visual C++ automatisch die Wrapperklasse ( ) -Implementierungsdatei (hinzu. CPP) an das Container-Projekt und den Wrapperklassenheader (. H) Datei in die Dialogfeld-Headerdatei:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>Der Wrapper-Klassenheader (. H) Datei

Um Eigenschaften (und Aufrufmethoden) für das Circ-Steuerelement abzurufen und festzulegen, stellt die `CCirc` Wrapperklasse eine Deklaration aller verfügbar gemachten Methoden und Eigenschaften bereit. Im Beispiel werden diese Deklarationen in CIRC gefunden. H. Das folgende Beispiel ist `CCirc` der Teil der Klasse, der die freiliegenden Schnittstellen des ActiveX-Steuerelements definiert:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Diese Funktionen können dann aus anderen Prozeduren der Anwendung mit der normalen C++-Syntax aufgerufen werden. Weitere Informationen zur Verwendung dieses Memberfunktionssatzes für den Zugriff auf die Methoden und Eigenschaften des Steuerelements finden Sie im Abschnitt [Programmieren des ActiveX-Steuerelements](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>Änderungen der Membervariablen am Projekt

Nachdem das ActiveX-Steuerelement dem Projekt hinzugefügt und in einen Dialogfeldcontainer eingebettet wurde, kann von anderen Teilen des Projekts darauf zugegriffen werden. Die einfachste Möglichkeit, auf das Steuerelement zuzugreifen, besteht `CContainerDlg` darin, eine Membervariable der Dialogklasse (Schritt 2) zu [erstellen,](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) die denselben Typ wie die Wrapperklasse hat, die dem Projekt von Visual C++ hinzugefügt wurde. Sie können dann die Membervariable verwenden, um jederzeit auf das eingebettete Steuerelement zuzugreifen.

Wenn das Dialogfeld **Elementvariable hinzufügen** die *m_circctl* Membervariable zum Projekt hinzufügt, werden der Headerdatei auch die folgenden Zeilen hinzugefügt (. H) der `CContainerDlg` Klasse:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Darüber hinaus wird **DDX_Control** ein Aufruf an `CContainerDlg`DDX_Control automatisch `DoDataExchange`zur Umsetzung von hinzugefügt:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>Programmierung der ActiveX-Steuerung

An diesem Punkt haben Sie das ActiveX-Steuerelement in die Dialogvorlage eingefügt und eine Membervariable dafür erstellt. Sie können jetzt die allgemeine C++-Syntax verwenden, um auf die Eigenschaften und Methoden des eingebetteten Steuerelements zuzugreifen.

Wie bereits erwähnt (in [The Wrapper Class Header (. H) Datei](#_core_the_wrapper_class_header_28h29_file)), die Headerdatei (. H) für `CCirc` die Wrapperklasse, in diesem Fall CIRC. H enthält eine Liste der Memberfunktionen, die Sie zum Abrufen und Festlegen eines beliebigen verfügbar gemachten Eigenschaftswerts verwenden können. Memberfunktionen für verfügbar gemachte Methoden sind ebenfalls verfügbar.

Ein häufiger Ort zum Ändern der Eigenschaften `OnInitDialog` des Steuerelements ist die Memberfunktion der Hauptdialogklasse. Diese Funktion wird kurz vor dem Erscheinen des Dialogfelds aufgerufen und zum Initialisieren des Inhalts, einschließlich aller Steuerelemente, verwendet.

Im folgenden Codebeispiel wird die *Membervariable m_circctl* verwendet, um die Beschriftungs- und CircleShape-Eigenschaften des eingebetteten Circ-Steuerelements zu ändern:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](../mfc/activex-control-containers.md)
