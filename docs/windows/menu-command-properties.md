---
title: Menübefehle (C++)
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: 972478923a7c4c60d8ff949c5532b00a1de1efc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075503"
---
# <a name="menu-commands-c"></a>Menübefehle (C++)

Die unten aufgeführten Informationen sind entsprechend den **Menü** Eigenschaften organisiert, die im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window) angezeigt werden, wenn Sie einen Menübefehl auswählen. Diese werden alphabetisch aufgelistet, obwohl das **Eigenschaften** Fenster auch das Anzeigen dieser Eigenschaften nach Kategorie ermöglicht.

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|**Break**|Einer der folgenden Werte ist möglich:<br/>  - **None**: keine Pause. Dies ist die Standardoption.<br/>  - **Spalte**: Bei statischen Menüs bewirkt dieser Wert, dass der Menübefehl in eine neue Zeile gesetzt wird.<br/>      Bei Popupmenüs bewirkt dieser Wert, dass der Menübefehl in eine neue Spalte gesetzt wird, ohne dass zwischen den Spalten eine Trennlinie angezeigt wird.<br/>      Diese Eigenschaft wirkt sich nicht im Menü-Editor, sondern erst zur Laufzeit auf die Darstellung des Menüs aus.<br />   - **Leiste**: identisch mit der **Spalte** , außer dass bei Popup Menüs der Wert die neue Spalte von der alten Spalte mit einer vertikalen Linie trennt.<br/>      Das Festlegen dieser Eigenschaft wirkt sich nicht im **Menü-Editor**, sondern nur zur Laufzeit auf die Darstellung des Menüs aus.|
|**Beschriftung**|Text zur Beschreibung des Menübefehls (der Menüname). Einem der Buchstaben in der Beschriftung eines Menübefehls kann eine Zugriffstaste zugeordnet werden, indem ihm ein kaufmännisches Und-Zeichen (&) vorangestellt wird.|
|**Aktiviert**|**True**gibt an, dass der Menübefehl anfänglich aktiviert ist. Typ: **bool**. Standardwert: **FALSE**.|
|**Aktiviert**|Wenn **FALSE**, ist das Menüelement deaktiviert.|
|**Grau**|**True**gibt an, dass der Menübefehl anfänglich ausgegraut und inaktiv ist. Typ: **bool**. Standardwert: **FALSE**.|
|**Hilfe**|Richtet das Menüelement rechtsbündig aus. Standardwert: **FALSE**.<br/><br/>Der Menübefehl für die **Hilfe** befindet sich beispielsweise in allen Windows-Anwendungen immer ganz rechts. Wenn Sie diese Eigenschaft für ein Menüelement festlegen, wird das Element ganz rechts am Ende des Menüs angezeigt. Bezieht sich auf Elemente des Hauptmenüs.|
|**ID**|Ein Symbol, das in der Headerdatei definiert ist. Typ: **Symbol**, **ganze**Zahl oder **Zeichenfolge**in Anführungszeichen.<br/><br/>Sie können ein beliebiges Symbol verwenden, das üblicherweise in den Editoren verfügbar ist. Dies gilt auch, wenn das [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) keine Dropdownliste enthält, aus der Sie auswählen können.|
|**Popup**|**True**gibt an, dass der Menübefehl ein Popup Menü ist. Typ: **bool**. Standard: **true** für Menüs der obersten Ebene in einer Menüleiste, andernfalls **false**.|
|**prompt**|Enthält Text, der in der Statusleiste angezeigt werden soll, wenn dieser Menübefehl markiert wird. Der Text wird mit dem Bezeichner des Menübefehls in der Zeichenfolgentabelle gespeichert.<br/><br/>Diese Eigenschaft ist für jeden Projekttyp verfügbar, wobei die Laufzeitfunktionalität jedoch MFC-spezifisch ist.|
|**Rechtsbündig**|Richtet den Menübefehl auf der Menüleiste zur Laufzeit rechtsbündig aus. Typ: **bool**. Standardwert: **FALSE**.|
|**Von rechts nach links**|Ermöglicht die Darstellung der Menübefehle von rechts nach links, wenn die Benutzeroberfläche in eine Sprache übertragen werden soll, die von rechts nach links geschrieben wird, z. B. Hebräisch oder Arabisch.|
|**Trennzeichen**|**True**gibt an, dass der Menübefehl ein Trennzeichen ist. Typ: **bool**. Standardwert: **FALSE**.|

## <a name="associate-menu-commands"></a>Menübefehle zuordnen

Häufig ist es wünschenswert, dass ein Menübefehl und eine Tastenkombination den gleichen Programmbefehl ausgeben. Identische Befehle werden mit dem Menü- **Editor** ausgegeben, um dem Menübefehl und einem Eintrag in der Zugriffstasten Tabelle Ihrer Anwendung denselben Ressourcen Bezeichner zuzuweisen. Anschließend bearbeiten Sie die [Beschriftung](../windows/menu-command-properties.md) des Menübefehls so, dass sie den Namen der Zugriffstaste anzeigt.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>So ordnen Sie einen Menübefehl einer Zugriffstaste zu

1. Wählen Sie im **Menü-Editor**den gewünschten Menübefehl aus.

1. Fügen Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)der Eigenschaft **Caption** den Namen der Zugriffstaste hinzu:

   - Geben Sie im Anschluss an die Menübeschriftung die Escapesequenz für einen Tabulator (\t) ein, damit alle Zugriffstasten des Menüs links ausgerichtet sind.

   - Geben Sie den Namen der Modifizierertaste (**STRG**, **alt**oder **UMSCHALT**) ein, gefolgt von einem Pluszeichen ( **+** ) und dem Namen, Buchstaben oder Symbol der zusätzlichen Taste.

   Wenn Sie z. b. dem Befehl **Öffnen** im Menü **Datei** die Tastenkombination **STRG**+**O** zuweisen möchten, ändern Sie die **Beschriftung** des Menübefehls so, dass Sie wie der folgende Text aussieht:

   ```
   &Open...\tCtrl+O
   ```

   Der Menübefehl im **Menü-Editor** wird aktualisiert, um die neue Beschriftung bei der Eingabe widerzuspiegeln.

1. [Erstellen Sie den Zugriffstastentabellen-Eintrag](../windows/adding-an-entry-to-an-accelerator-table.md) im **Zugriffstasten** -Editor, und weisen Sie ihm den gleichen Bezeichner wie dem Menübefehl zu. Verwenden Sie eine Tastenkombination, die Ihrer Ansicht nach leicht zu merken ist.

Die MFC-Anwendung kann beschreibenden Text für jeden Menübefehl anzeigen, den ein Benutzer auswählen kann. Zeigen Sie beschreibenden Text an, indem Sie jedem Menübefehl mithilfe der Eigenschaft **prompt** im Fenster **Eigenschaften** eine Text Zeichenfolge zuweisen. Wenn eine Zeichenfolge in der [Zeichenfolgentabelle](../windows/string-editor.md) die gleiche ID wie der Befehl aufweist, zeigt eine MFC-Anwendung automatisch diese Zeichenfolgenressource in der Statusleiste der ausgeführten Anwendung an, wenn ein Benutzer auf ein Menüelement zeigt.

- Wählen Sie im **Menü-Editor**den Menübefehl aus, um einem Menübefehl eine Text Zeichenfolge für eine Statusleiste in MFC-Anwendungen zuzuordnen. Geben Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)den zugeordneten Statusleistentext im Feld **Eingabeaufforderung** ein.

In einem C++ Projekt können Sie eine Zugriffstaste (ein mnetmonisches, mit dem der Benutzer das Menü mit der Tastatur auswählen kann) zu Ihren Menüs und Menübefehlen zuweisen.

- Wenn Sie einem Menübefehl eine Zugriffstaste (Tastenkombination) zuweisen möchten, geben Sie ein kaufmännisches und-(`&`) vor einem Buchstaben im Menü Namen oder Befehlsnamen ein, um diesen Buchstaben als entsprechenden Zugriffsschlüssel anzugeben.

   Beispiel: "& Datei" legt **alt**+**F** als Tastenkombination für das Menü **Datei** in Anwendungen fest, die für Microsoft Windows geschrieben wurden.

   Das Menüelement gibt einen sichtbaren Hinweis darauf, dass einem der Buchstaben eine Zugriffstaste zugeordnet ist. Der Buchstabe, der auf das kaufmännische Und-Zeichen folgt, wird unterstrichen dargestellt (abhängig vom Betriebssystem).

> [!NOTE]
> Stellen Sie sicher, dass alle Zugriffstasten in einem Menü eindeutig sind, indem Sie mit der rechten Maustaste auf das Menü klicken und **mnetmonics überprüfen**auswählen.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Menü-Editor](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->