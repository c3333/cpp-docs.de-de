---
title: Implementieren einer Eigenschaftenseite (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: dd74dd4562a3c4a8bff2c58d5f1d801f5dd06fd8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499611"
---
# <a name="example-implementing-a-property-page"></a>Beispiel: Implementieren einer Eigenschaften Seite

::: moniker range="vs-2019"

Der ATL-Eigenschaftenseiten-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=vs-2017"

Dieses Beispiel zeigt, wie Sie eine Eigenschaftenseite erstellen, auf der Eigenschaften der [Document Classes](../mfc/document-classes.md)-Schnittstelle angezeigt werden (und auf der Sie die Eigenschaften ändern können).

Das Beispiel basiert auf dem [ATLPages-Beispiel](../overview/visual-cpp-samples.md).

In diesem Beispiel führen Sie folgende Aktionen aus:

- [Hinzufügen der Klasse für ATL-Eigenschaftenseiten](#vcconusing_the_atl_object_wizard) mithilfe des Dialogfelds „Klasse hinzufügen“ und des ATL-Eigenschaftenseiten-Assistenten.

- [Bearbeiten der Dialogfeldressource](#vcconediting_the_dialog_resource) durch Hinzufügen neuer Steuerelemente für interessante Eigenschaften der `Document`-Schnittstelle.

- [Hinzufügen von Meldungshandlern](#vcconadding_message_handlers), um die Eigenschaftenseite über Änderungen zu informieren, die von Benutzern vorgenommen wurden.

- Hinzufügen einiger `#import`-Anweisungen und einer typedef im Abschnitt [Housekeeping](#vcconhousekeeping).

- [Überschreiben von „IPropertyPageImpl::SetObjects“](#vcconoverriding_ipropertypageimpl_setobjects), um die Objekte zu überprüfen, die an die Eigenschaftenseite übergeben werden.

- [Überschreiben von „IPropertyPageImpl::Activate“](#vcconoverriding_ipropertypageimpl_activate), um die Schnittstelle der Eigenschaftenseite zu initialisieren.

- [Überschreiben von IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply), um das Objekt mit den neuesten Eigenschaftswerten zu aktualisieren.

- [Anzeigen der Eigenschaftenseite](#vccontesting_the_property_page) durch Erstellen eines einfachen Hilfsobjekts.

- [Erstellen eines Makros](#vcconcreating_a_macro), das die Eigenschaftenseite testet.

## <a name="adding-the-atl-property-page-class"></a><a name="vcconusing_the_atl_object_wizard"></a> Hinzufügen einer Klasse für ATL-Eigenschaftenseiten

Zunächst erstellen Sie ein neues ATL-Projekt für einen DLL-Server namens `ATLPages7`. Danach verwenden Sie den [ATL-Eigenschaftenseiten-Assistenten](../atl/reference/atl-property-page-wizard.md), um eine Eigenschaftenseite zu generieren. Weisen Sie der Eigenschaftenseite den **Kurznamen****DocProperties** zu, und wechseln Sie dann zur Seite **Zeichenfolgen**, um für die Eigenschaftenseite spezifische Elemente festzulegen, wie in der unten stehenden Tabelle gezeigt.

|Element|Wert|
|----------|-----------|
|Titel|TextDocument|
|Dokumentzeichenfolge|VCUE TextDocument Properties|
|Hilfedatei|*\<blank>*|

Die Werte, die Sie auf dieser Seite des Assistenten festlegen, werden an den Container der Eigenschaftenseite zurückgegeben, wenn dieser `IPropertyPage::GetPageInfo` aufruft. Was danach mit den Zeichenfolgen geschieht, hängt vom Container ab, aber in der Regel werden sie verwendet, um Ihre Seite für den Benutzer zu identifizieren. Der Titel wird üblicherweise auf einer Registerkarte über Ihrer Seite angezeigt, die Dokumentzeichenfolge in einer Statusleiste oder QuickInfo (allerdings verwendet der Frame für Standardeigenschaften diese Zeichenfolge gar nicht).

> [!NOTE]
> Die Zeichenfolgen, die Sie hier festlegen, werden vom Assistenten als Zeichenfolgenressourcen in Ihrem Projekt gespeichert. Sie können diese Zeichenfolgen ganz einfach mit dem Ressourcen-Editor bearbeiten, wenn Sie diese Informationen ändern müssen, nachdem der Code für Ihre Seite generiert wurde.

Klicken Sie auf **OK**, damit der Assistent Ihre Eigenschaftenseite generiert.

## <a name="editing-the-dialog-resource"></a><a name="vcconediting_the_dialog_resource"></a> Bearbeiten der Dialogfeldressource

Nach dem Generieren der Eigenschaftenseite müssen Sie der Dialogfeldressource, die Ihre Seite repräsentiert, einige Steuerelemente hinzufügen. Fügen Sie ein Bearbeitungsfeld, ein statisches Textsteuerelement und ein Kontrollkästchen hinzu, und legen Sie die IDs wie im Folgenden gezeigt fest:

![Dialogfeldressource bearbeiten](../atl/media/ppgresourcelabeled.gif "Dialogfeldressource bearbeiten")

Mit diesen Steuerelementen werden der Dateiname und der schreibgeschützte Status des Dokuments angezeigt.

> [!NOTE]
> Die Dialogfeldressource enthält weder einen Frame noch Befehlsschaltflächen und weist auch nicht Registerkartenformat auf, das Sie möglicherweise erwartet haben. Diese Features werden durch einen Eigenschaftenseitenframe bereitgestellt, z.B. durch den, der durch den Aufruf von [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe) erstellt wird.

## <a name="adding-message-handlers"></a><a name="vcconadding_message_handlers"></a> Hinzufügen von Meldungshandlern

Wenn die Steuerelemente vorhanden sind, können Sie Meldungshandler hinzufügen, um den geänderten Status der Seite zu aktualisieren, wenn sich der Wert eines der Steuerelemente ändert:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Dieser Code reagiert auf Änderungen am Bearbeitungssteuerelement oder Kontrollkästchen durch Aufruf von [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), wodurch die Site der Seite darüber informiert wird, dass die Seite sich geändert hat. In der Regel reagiert die Site der Seite durch Aktivieren oder Deaktivieren einer **Anwenden**-Schaltfläche im Frame der Eigenschaftenseite.

> [!NOTE]
> Auf Ihren eigenen Eigenschaftenseiten müssen Sie möglicherweise nachverfolgen, welche Eigenschaften genau vom Benutzer geändert wurden, um zu vermeiden, dass Eigenschaften aktualisiert werden, die sich nicht geändert haben. Dieses Beispiel implementiert diesen Code, indem die ursprünglichen Eigenschaftswerte nachverfolgt und mit den aktuellen Werten der Benutzeroberfläche verglichen werden, wenn die Änderungen angewendet werden sollen.

## <a name="housekeeping"></a><a name="vcconhousekeeping"></a> Housekeeping

Fügen Sie jetzt einige `#import`-Anweisungen zu „DocProperties.h“ hinzu, sodass der Compiler die `Document`-Schnittstelle kennt:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Sie müssen auch auf die- `IPropertyPageImpl` Basisklasse verweisen. Fügen Sie der- **`typedef`** Klasse Folgendes hinzu `CDocProperties` :

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

## <a name="overriding-ipropertypageimplsetobjects"></a><a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Überschreiben von „IPropertyPageImpl::SetObjects“

Die erste `IPropertyPageImpl`-Methode, die Sie überschreiben müssen, ist [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Hier fügen Sie Code hinzu, um zu überprüfen, ob nur ein einzelnes Objekt übergeben wurde und dass es die `Document`-Schnittstelle unterstützt, die Sie erwarten:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
> Es ist sinnvoll, für diese Seite nur ein einzelnes Objekt zu unterstützen, da Sie dem Benutzer erlauben, den Dateinamen des Objekts festzulegen – und an jedem Speicherort kann nur eine einzige Daten vorhanden sein.

## <a name="overriding-ipropertypageimplactivate"></a><a name="vcconoverriding_ipropertypageimpl_activate"></a> Überschreiben von „IPropertyPageImpl::Activate“

Der nächste Schritt besteht darin, die Eigenschaftenseite mit den Eigenschaftswerten des zugrunde liegenden Objekts zu initialisieren, wenn die erste Seite erstellt wird.

In diesem Fall sollten Sie die folgenden Member zur Klasse hinzufügen, da Sie auch die anfänglichen Eigenschaftswerte verwenden, um Vergleiche durchzuführen, wenn Benutzer der Seite ihre Änderungen anwenden:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Die Implementierung der Basisklasse der [Activate](../atl/reference/ipropertypageimpl-class.md#activate)-Methode ist für das Erstellen des Dialogfelds und der zugehörigen Steuerelemente zuständig, daher können Sie diese Methode überschreiben und nach dem Aufruf der Basisklasse Ihre eigene Initialisierung hinzufügen:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Dieser Code verwendet die COM-Methoden der `Document`-Schnittstelle, um die Eigenschaften abzurufen, die Sie interessieren. Dann verwendet der Code die Win32-API-Wrapper, die von [CDialogImpl](../atl/reference/cdialogimpl-class.md) und den zugehörigen Basisklassen bereitgestellt werden, um dem Benutzer die Eigenschaftswerte anzuzeigen.

## <a name="overriding-ipropertypageimplapply"></a><a name="vcconoverride_ipropertypageimpl_apply"></a> Überschreiben von „IPropertyPageImpl::Apply“

Wenn Benutzer ihre Änderungen an den Objekten anwenden möchten, ruft die Site der Eigenschaftenseite die Methode [Apply](../atl/reference/ipropertypageimpl-class.md#apply) auf. Hier erfolgt jetzt das Gegenteil des Codes in `Activate`: Während `Activate` Werte aus dem Objekt akzeptiert und an die Steuerelemente auf der Eigenschaftenseite übermittelt hat, akzeptiert `Apply` Werte aus den Steuerelementen auf der Eigenschaftenseite und übermittelt sie an das Objekt.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
> Die Prüfung auf [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) am Anfang dieser Implementierung ist eine anfängliche Prüfung, um unnötige Aktualisierungen der Objekte zu vermeiden, wenn `Apply` mehr als einmal aufgerufen wird. Es gibt auch Prüfungen für jeden der Eigenschaftswerte, um sicherzustellen, dass nur Änderungen zu einem Methodenaufruf von `Document` führen.

> [!NOTE]
> `Document` macht `FullName` als schreibgeschützte Eigenschaft verfügbar. Um den Dateinamen des Dokuments basierend auf Änderungen zu aktualisieren, die an der Eigenschaftenseite vorgenommen wurden, müssen Sie die `Save`-Methode verwenden, um die Datei unter einem anderen Namen zu speichern. Daher sollte sich der Code auf einer Eigenschaftenseite nicht auf das Abrufen und Festlegen von Eigenschaften beschränken.

## <a name="displaying-the-property-page"></a><a name="vccontesting_the_property_page"></a> Anzeigen der Eigenschaftenseite

Um diese Seite anzuzeigen, müssen Sie ein einfaches Hilfsobjekt erstellen. Das Hilfsobjekt bietet eine Methode, die die `OleCreatePropertyFrame`-API zum Anzeigen einer einzelnen Seite vereinfacht, die mit einem einzelnen Objekt verknüpft ist. Dieses Hilfsobjekt ist so konzipiert, dass es mit Visual Basic verwendet werden kann.

Verwenden Sie das [Dialogfeld „Klasse hinzufügen“](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) und den [ATL-Assistenten für einfache Objekte](../atl/reference/atl-simple-object-wizard.md), um eine neue Klasse zu generieren, und verwenden Sie `Helper` als Kurznamen. Nach dem Erstellen fügen Sie eine Methode hinzu, wie in der unten stehenden Tabelle gezeigt.

|Element|Wert|
|----------|-----------|
|Methodenname|`ShowPage`|
|Parameter|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Der *bstrCaption*-Parameter ist die Beschriftung, die als Titel des Dialogfelds angezeigt werden soll. Der *bstrID*-Parameter ist eine Zeichenfolge, die entweder eine CLSID oder eine ProgID der anzuzeigenden Eigenschaftenseite repräsentiert. Der *pUnk*-Parameter ist der `IUnknown`-Zeiger des Objekts, dessen Eigenschaften durch die Eigenschaftenseite konfiguriert werden.

Implementieren Sie die unten gezeigte Methode:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

## <a name="creating-a-macro"></a><a name="vcconcreating_a_macro"></a> Erstellen eines Makros

Nachdem Sie das Projekt erstellt haben, können Sie die Eigenschaftenseite und das Hilfsobjekt mit einem einfachen Makro testen, das Sie in der Visual Studio-Entwicklungsumgebung erstellen und ausführen. Dieses Makro erstellt ein Hilfsobjekt, und ruft dann die `ShowPage`-Methode auf; dabei verwendet das Makro die ProgID der Eigenschaftenseite **DocProperties** und den `IUnknown`-Zeiger des derzeit im Visual Studio-Editor aktiven Dokuments. Hier sehen Sie den für dieses Makro erforderlichen Code:

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

Wenn Sie dieses Makro ausführen, wird die Eigenschaftenseite mit dem Dateinamen und dem schreibgeschützten Status des derzeit aktiven Textdokuments angezeigt. Der schreibgeschützte Status des Dokuments spiegelt nur die Möglichkeit wider, in der Entwicklungsumgebung in das Dokument zu schreiben, und wirkt sich nicht auf das Schreibschutzattribut der Datei auf dem Datenträger aus.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[Eigenschaftenseiten](../atl/atl-com-property-pages.md)<br/>
[ATLPages-Beispiel](../overview/visual-cpp-samples.md)
