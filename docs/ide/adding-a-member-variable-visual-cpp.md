---
title: Hinzufügen einer Membervariable
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: e7fd5bd93198c494f18fe18755d13d40fe7fbf96
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845132"
---
# <a name="add-a-member-variable"></a>Hinzufügen einer Membervariable

Mithilfe der Klassenansicht können Sie einer Klasse eine Membervariable hinzufügen. Membervariablen können generisch sein oder für [Datenaustausch und Datenvalidierung](../mfc/dialog-data-exchange-and-validation.md) verwendet werden. Der Assistent für Datenmembervariablen ist dafür ausgelegt, die relevanten Informationen zu verwenden, um Elemente an den entsprechenden Stellen in Quelldateien einzufügen. Sie können eine Membervariable aus dem [Dialog-Editor](../windows/dialog-editor.md) oder der [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) der [Ressourcenansicht](../windows/how-to-create-a-resource-script-file.md#create-resources) hinzufügen.

> [!NOTE]
> Wenn Sie ein Dialogfeld entwerfen und implementieren, kann es sich als effizienter erweisen, den Dialog-Editor zum Hinzufügen der Dialogfeld-Steuerelemente zu verwenden und dann die Membervariablen der Steuerelemente zu implementieren.

**So fügen Sie einem Dialogfeld-Steuerelement in der Ressourcenansicht eine Membervariable mithilfe des Assistenten zum Hinzufügen von Membervariablen hinzu**:

1. Erweitern Sie den Projektknoten und den Dialogknoten in der Ressourcenansicht, um die Liste der Dialogfelder des Projekts anzuzeigen.

1. Doppelklicken Sie auf das Dialogfeld, dem Sie die Membervariable hinzufügen möchten, um es im Dialog-Editor zu öffnen.

1. Klicken Sie mit der rechten Maustaste auf das Steuerelement im Dialogfeld, das im Dialog-Editor angezeigt wird, das der Membervariable hinzugefügt werden soll.

1. Klicken Sie im Kontextmenü auf **Variable hinzufügen**, um den [Assistenten zum Hinzufügen von Membervariablen](#add-member-variable-wizard) anzuzeigen.

   > [!NOTE]
   > In der **Steuerelement-ID** wird bereits ein Standardwert angegeben.

1. Geben Sie die Informationen in den entsprechenden Feldern des Assistenten an. Weitere Informationen finden Sie unter [Dialog Box Controls and Variable Types (Steuerelemente für Dialogfelder und Variablentypen)](#dialog-box-controls-and-variable-types).

1. Klicken Sie auf **Fertig stellen**, um dem Projekt die Definition und den Implementierungscode hinzuzufügen und den Assistenten zu schließen.

**So fügen Sie eine Membervariable aus der Klassenansicht mithilfe des Assistenten zum Hinzufügen von Membervariablen hinzu**:

1. Erweitern Sie in der [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) den Projektknoten, um die Projektklassen anzuzeigen.

1. Klicken Sie mit der rechten Maustaste auf die Klasse, der eine Variable hinzugefügt werden soll.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Variable hinzufügen**, um den Assistenten zum Hinzufügen von Membervariablen anzuzeigen.

1. Geben Sie die Informationen in den entsprechenden Feldern des Assistenten an. Weitere Informationen finden Sie unter [Add Member Variable Wizard (Assistent zum Hinzufügen von Membervariablen)](#add-member-variable-wizard).

1. Klicken Sie auf **Fertig stellen**, um dem Projekt die Definition und den Implementierungscode hinzuzufügen und den Assistenten zu schließen.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Assistent zum Hinzufügen von Membervariablen](#add-member-variable-wizard)
- [Dialogfeld-Steuerelemente und Variablentypen](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Assistent zum Hinzufügen von Membervariablen

Dieser Assistent fügt der Headerdatei eine Membervariablendeklaration hinzu. Abhängig von den Optionen können sie der CPP-Datei Code hinzufügen. Sobald Sie eine Membervariable mithilfe des Assistenten hinzugefügt haben, können Sie den Code in der Entwicklungsumgebung bearbeiten.

- **Zugriff**

  Legt den Zugriff auf die Membervariable fest. Bei Zugriffsmodifizierern handelt es sich um Schlüsselwörter, die den Zugriff festlegen, den andere Klassen auf die Membervariable haben. Weitere Informationen zum Festlegen des Zugriffs finden Sie unter [Member-Access Control (Steuerung des Memberzugriffs)](../cpp/member-access-control-cpp.md). Standardmäßig ist die Zugriffsebene von Membervariablen auf **`public`** festgelegt.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Variablentyp**

  Legt den Rückgabetyp für die hinzugefügte Membervariable fest.

  - Wenn Sie eine Membervariable hinzufügen, bei der es sich nicht um ein Steuerelement für Dialogfelder handelt, wählen Sie den Typ aus der Liste der verfügbaren Typen aus.

    Weitere Informationen zu Typen finden Sie unter [Grundlegende Typen](../cpp/fundamental-types-cpp.md).

    - **`char`**
    - **`double`**
    - **`float`**
    - **`int`**
    - **`long`**
    - **`short`**
    - **`unsigned char`**
    - **`unsigned int`**
    - **`unsigned long`**

  - Wenn Sie eine Membervariable für ein Steuerelement für Dialogfelder hinzufügen, wird dieses Feld mit dem Typ des Objekts aufgefüllt, das für ein Steuerelement oder einen Wert zurückgegeben wird. Wenn Sie **Steuerelement** auswählen, gibt der **Variablentyp** die Basisklasse des Steuerelements an, das Sie im Feld **Steuerelement-ID** ausgewählt haben. Wenn das Steuerelement für ein Dialogfeld einen Wert enthalten kann und Sie **Wert** ausgewählt haben, gibt der **Variablentyp** den geeigneten Typ für den Wert an, den das Steuerelement enthalten kann. Weitere Informationen finden Sie unter [Dialog Box Controls and Variable Types (Steuerelemente für Dialogfelder und Variablentypen)](#dialog-box-controls-and-variable-types).

    Dieser Wert hängt von der Auswahl in **Steuerelement-ID** ab und kann nicht geändert werden.

- **Variablenname**

  Legt den Namen der hinzugefügten Membervariable fest. Membervariablen beginnen üblicherweise mit der Identifizierungszeichenfolge `m_`, die in der Regel standardmäßig bereitgestellt wird.

- **Steuerelementvariable**

  Gibt an, dass die Membervariable ein Steuerelement innerhalb eines Dialogfelds mit Unterstützung für [Datenaustausch und Datenvalidierung](../mfc/dialog-data-exchange-and-validation.md) verwaltet. Weitere Informationen finden Sie unter [DoDataExchange (Datenaustausch durchführen)](../mfc/reference/cwnd-class.md#dodataexchange). Diese Option ist nur für Membervariablen verfügbar, die zu Klassen hinzugefügt wurden, die von [CDialog](../mfc/reference/cdialog-class.md) abgeleitet wurden. Aktivieren Sie dieses Kontrollkästchen, um die Optionen **Steuerelement-ID** und **Steuerelementtyp** zu aktivieren.

- **Steuerelement-ID**

  Legt die ID für die hinzugefügte Steuerelementvariable fest. Wählen Sie die ID für den Typ des Steuerelements, für den Sie die Membervariable hinzufügen, aus der Liste aus. Diese Liste ist nur aktiv, wenn das Kontrollkästchen **Steuerelementvariable** aktiviert und auf die Steuerelement-IDs beschränkt ist, die bereits zum Dialogfeld hinzugefügt wurden. Für die Standardschaltfläche **OK** entspricht die Steuerelement-ID beispielsweise **IDOK**.

  |Option|Beschreibung|
  |------------|-----------------|
  |**Steuerelement**|Diese Option ist standardmäßig für den Steuerelementtyp festgelegt. Sie verwaltet das Steuerelement, nicht dessen Status oder Inhalte (wie es bei einem Listenfeld, einem Kombinationsfeld oder einem Bearbeitungsfeld möglicherweise gewünscht ist).|
  |**Wert**|Diese Option ist für Steuerelementtypen verfügbar, die einen Wert enthalten oder einen Status anzeigen können, z.B. ein Eingabefeld oder ein Kontrollkästchen. Sie ist auch verfügbar für Steuerelementtypen, für die Bereich, Inhalt oder Zustand verwaltet werden kann. Weitere Informationen finden Sie unter [Dialog Box Controls and Variable Types (Steuerelemente für Dialogfelder und Variablentypen)](#dialog-box-controls-and-variable-types).|

- **Kategorie**

  Gibt an, ob die Variable auf einem Steuerelementtyp oder auf dem Wert des Steuerelements basiert.

- **Steuerelementtyp**

  Legt den Typ des Steuerelements fest, das hinzugefügt wird. Dieses Feld kann nicht geändert werden. Eine Schaltfläche hat beispielsweise den Steuerelementtyp **BUTTON**, und ein Kombinationsfeld hat den Steuerelementtyp **COMBOBOX**. Weitere Informationen finden Sie unter [Dialog Box Controls and Variable Types (Steuerelemente für Dialogfelder und Variablentypen)](#dialog-box-controls-and-variable-types).

- **Maximale Zeichenanzahl**

  Nur verfügbar, wenn der **Variablentyp** auf [CString](../atl-mfc-shared/reference/cstringt-class.md) festgelegt ist. Gibt die maximale Anzahl von Zeichen an, die das Steuerelement enthalten kann.

- **Mindestwert**

  Nur verfügbar, wenn der Variablentyp `BOOL`, **`int`** , `UINT`, **`long`** , `DWORD`, **`float`** , **`double`** , `BYTE`, **`short`** , [COLECurrency](../mfc/reference/colecurrency-class.md) oder [CTime](../atl-mfc-shared/reference/ctime-class.md) lautet. Gibt den niedrigsten Wert an, der für eine Skalierung oder einen Datenbereich akzeptiert wird.

- **Höchstwert**

  Nur verfügbar, wenn der Variablentyp `BOOL`, **`int`** , `UINT`, **`long`** , `DWORD`, **`float`** , **`double`** , `BYTE`, **`short`** , `COLECurrency` oder `CTime` lautet. Gibt den höchsten Wert an, der für eine Skalierung oder einen Datenbereich akzeptiert wird.

- **H-Datei**

  Gibt für ActiveX-Steuerelemente an, welche Membervariablen einer Wrapperklasse erfordern. Legt den Namen der Headerdatei fest, die zur Klassendeklaration hinzugefügt werden soll.

- **CPP-Datei**

  Gibt für ActiveX-Steuerelemente an, welche Membervariablen einer Wrapperklasse erfordern. Legt den Namen der Implementierungsdatei fest, die zur Klassendefinition hinzugefügt werden soll.

- **Kommentar**

  Fügt einen Kommentar zur Headerdatei der Membervariable hinzu.

## <a name="dialog-box-controls-and-variable-types"></a>Dialogfeld-Steuerelemente und Variablentypen

Sie können den [Assistenten zum Hinzufügen von Membervariablen](#add-member-variable-wizard) verwenden, um einem mit MFC erstellten Dialogfeld-Steuerelement eine Membervariable hinzuzufügen. Der Typ des Steuerelements, dem Sie die Membervariable hinzufügen, bestimmt die Optionen, die im Dialogfeld angezeigt werden.

In der folgenden Tabelle werden alle Steuerelementtypen der Dialogfelder beschrieben, die in MFC und dem [Dialog-Editor](../windows/dialog-editor.md) unterstützt werden. Außerdem werden die verfügbaren Typen und Werte angezeigt.

|Steuerelement|Steuerelementtyp|Variable für den Steuerelementtyp|Variable für den Werttyp|Min/Max-Werte (nur der Werttyp)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Animationssteuerelement|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Schaltfläche|SCHALTFLÄCHE|[CButton](../mfc/reference/cbutton-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Kontrollkästchen|KONTROLLKÄSTCHEN|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Minimalwert/Maximalwert|
|Kombinationsfeld|KOMBINATIONSFELD|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Maximale Zeichenanzahl|
|Datums-/Zeitauswahl-Steuerelement|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Minimalwert/Maximalwert|
|Bearbeitungsfeld|BEARBEITEN|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` oder `COleCurrency`|Minimalwert/Maximalwert, einige unterstützen die maximale Zeichenanzahl|
|Hotkey-Steuerelement|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Listenfeld|LISTENFELD|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Maximale Zeichenanzahl|
|Listensteuerelement|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Monatskalender-Steuerelement|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Minimalwert/Maximalwert|
|Statuskontrolle|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Rich Edit 2-Steuerelement|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Maximale Zeichenanzahl|
|Rich Edit-Steuerelement|RICHEDIT|`CRichEditCtrl`|`CString`|Maximale Zeichenanzahl|
|Scrollleiste (vertikal oder horizontal)|SCROLLLEISTE|[CScrollBar](../mfc/reference/cscrollbar-class.md)|**`int`**|Minimalwert/Maximalwert|
|Schieberegler-Steuerelement|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|**`int`**|Minimalwert/Maximalwert|
|Drehfeld-Steuerelement|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Registersteuerelement|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
|Baumsteuerelement|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Keiner, nur Steuerelement|Nicht zutreffend|
