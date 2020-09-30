---
title: Hinzufügen einer Eigenschaft
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 63985643973782ea2b4240a338d66cb5cc2195dc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504687"
---
# <a name="add-a-property"></a>Hinzufügen einer Eigenschaft

Sie können den [Assistenten zum Hinzufügen von Eigenschaften](#names-add-property-wizard) verwenden, um einer Schnittstelle in Ihrem Projekt eine Eigenschaft hinzuzufügen.

**So fügen Sie Ihrem Objekt eine Eigenschaft hinzu:**

1. Klicken Sie in der [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) mit der rechten Maustaste auf den Namen der Schnittstelle, der die Eigenschaft hinzugefügt werden soll.

   > [!NOTE]
   > Sie können Eigenschaften auch zu Disp-Schnittstellen hinzufügen, die im Bibliotheksknoten geschachtelt sind, sofern das Projekt nicht attributiert ist.

1. Wählen Sie im Kontextmenü **Hinzufügen** und dann **Eigenschaft hinzufügen** aus.

1. Geben Sie im [Assistenten zum Hinzufügen von Eigenschaften](#names-add-property-wizard) die Informationen zum Erstellen der Eigenschaft an.

1. Geben Sie alle Einstellungen der Interface Definition Language dieser Eigenschaft auf der Seite [IDL-Attribute](#idl-attributes-add-property-wizard) des Assistenten an.

1. Klicken Sie auf **Fertig stellen**, um die Eigenschaft hinzuzufügen.

Die Methoden `Get` und `Put` der Eigenschaft werden in der Klassenansicht als zwei Symbole unter der Schnittstelle angezeigt, in der sie definiert sind. Sie können eines der Symbole doppelklicken, um die Eigenschaftsdeklaration in der IDL-Datei anzuzeigen.

- Bei ATL-Schnittstellen werden die Funktionen `Get` und `Put` der CPP-Datei hinzugefügt, und Verweise auf diese Funktionen werden der H-Datei hinzugefügt.

- Wenn Sie bei MFC-Disp-Schnittstellen **Membervariable** als Implementierungstyp auswählen, werden der implementierenden Klasse eine Methode und eine Variable hinzugefügt. Wenn Sie die **Get/Set-Methoden** als Implementierungstyp auswählen, werden der implementierenden Klasse zwei Methoden hinzugefügt.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Namen, Assistent zum Hinzufügen von Eigenschaften](#names-add-property-wizard)
- [IDL-Attribute, Assistent zum Hinzufügen von Eigenschaften](#idl-attributes-add-property-wizard)
- [Basiseigenschaften](#stock-properties)

## <a name="names-add-property-wizard"></a>Namen, Assistent zum Hinzufügen von Eigenschaften

Verwenden Sie diesen Assistenten, um eine Eigenschaft zu einer Schnittstelle hinzuzufügen.

- **Eigenschaftentyp**

  Legt den Typ der Eigenschaft fest, die Sie hinzufügen. Geben Sie bei MFC-Disp-Schnittstellen einen eigenen Typ an, oder wählen Sie einen aus der vordefinierten Liste aus. Wenn Sie eine vordefinierte Implementierung einer Eigenschaft bereitstellen, wird **Eigenschaftentyp** auf den vordefinierten Typ festgelegt und kann nicht geändert werden.

- **Eigenschaftenname**

  Legt den Namen der Eigenschaft fest. Für MFC-Disp-Schnittstellen, die ActiveX-Steuerelementen zugeordnet sind, können Sie einen eigenen Namen angeben oder einen vordefinierten Eigenschaftennamen aus der Liste auswählen. Wenn Sie einen eigenen Eigenschaftennamen bereitstellen, ist der Implementierungstyp **Stock** (Vordefiniert) nicht verfügbar. Eine Beschreibung der Eigenschaften in der Liste finden Sie unter [Basiseigenschaften](#stock-properties).

  |Schnittstellentyp|Beschreibung|
  |--------------------|-----------------|
  |Duale ATL-Schnittstelle, benutzerdefinierte Schnittstelle, lokale benutzerdefinierte Schnittstelle|Geben Sie einen Eigenschaftennamen an.|
  |MFC-Disp-Schnittstelle, Disp-Schnittstelle des MFC-ActiveX-Steuerelements|Geben Sie einen Eigenschaftennamen an, oder wählen Sie eine Basiseigenschaft aus der Liste aus. Wenn Sie eine Eigenschaft aus der Liste auswählen, wird der entsprechende Wert im Feld **Eigenschaftentyp** angezeigt. Sie können diesen Typ abhängig von Ihrer Auswahl unter **Implementierungstyp** ändern.|

- **Rückgabetyp**

  Nur ATL-Schnittstellen Legt den Rückgabetyp der Eigenschaft fest. Bei dualen Schnittstellen ist der Rückgabetyp immer `HRESULT`, und das Feld ist nicht verfügbar. Bei benutzerdefinierten Schnittstellen können Sie einen Rückgabetyp aus der Liste auswählen. `HRESULT` wird dennoch empfohlen, da dadurch ein gängiges Verfahren zum Zurückgeben von Fehlern bereitgestellt wird.

- **Variablenname**

  Nur MFC-Schnittstellen Nur verfügbar, wenn Sie **Membervariable** unter **Implementierungstyp** festlegen. Legt den Namen der Membervariable fest, der die Eigenschaft zugeordnet ist. Der Variablenname ist standardmäßig auf `m_`*PropertyName* festgelegt. Sie können diesen Namen bearbeiten.

- **Benachrichtigungsfunktion**

  Nur MFC-Schnittstellen Nur verfügbar, wenn Sie **Membervariable** unter **Implementierungstyp** festlegen. Legt den Namen der Benachrichtigungsfunktion fest, die aufgerufen wird, wenn die Eigenschaft geändert wird. Der Name der Benachrichtigungsfunktion ist standardmäßig auf `On`*PropertyName*`Changed` festgelegt. Sie können diesen Namen bearbeiten.

- **Get-Funktion**

  Nur MFC-Disp-Schnittstellen Nur verfügbar, wenn Sie **Get/Set-Methoden** unter **Implementierungstyp** festlegen. Legt den Namen der Funktion fest, die die Eigenschaft abrufen soll. Der Name der `Get`-Funktion ist standardmäßig auf `Get`*PropertyName* festgelegt. Sie können diesen Namen bearbeiten. Wenn Sie den Namen löschen, wird die Funktion [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) in die Dispatchzuordnung der Schnittstelle eingefügt. Die Funktion `Get`*PropertyName* gibt an, dass die Eigenschaft lesbar ist.

- **Funktion festlegen**

  Nur MFC-Schnittstellen Nur verfügbar, wenn Sie **Get/Set-Methoden** unter **Implementierungstyp** festlegen. Legt den Namen der Funktion fest, die die Eigenschaft festlegen soll. Der Name der `Set`-Funktion ist standardmäßig auf `Set`*PropertyName* festgelegt. Sie können diesen Namen bearbeiten. Wenn Sie den Namen löschen, wird die Funktion [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) in die Dispatchzuordnung der Schnittstelle eingefügt. Die Funktion `Set`*PropertyName* gibt an, dass die Eigenschaft schreibbar ist.

- **Implementierungstyp**

  Nur MFC-Schnittstellen Gibt an, wie die hinzugefügten Eigenschaften implementiert werden sollen.

  |Implementierungstyp|Beschreibung|
  |-------------------------|-----------------|
  |**Stock**|Gibt eine vordefinierte Implementierung für die unter **Eigenschaftenname** ausgewählte Eigenschaft an. Der Standardwert. Weitere Informationen finden Sie unter [Basiseigenschaften](#stock-properties).<br /><br /> Wenn Sie **Stock** (Vordefiniert) angeben, werden **Eigenschaftentyp**, **Parametertyp** und **Parametername** abgeblendet.|
  |**Membervariable**|Gibt an, dass die Eigenschaft als Membervariable hinzugefügt wird. Sie können benutzerdefinierte Eigenschaften und die meisten Basiseigenschaften als Membervariablen hinzufügen. Sie können die **Membervariable** für die Eigenschaften `Caption`, `hWnd` und `Text` nicht angeben.<br /><br /> Gibt Standardnamen unter **Variablenname** und **Benachrichtigungsfunktion** an. Sie können diesen Namen bearbeiten.|
  |**Get/Set-Methoden**|Gibt an, dass die Eigenschaft standardmäßig als `Get`*PropertyName*- und `Set`*PropertyName*-Funktion hinzugefügt wird. Diese Namen werden unter **Get-Funktion** und **Set-Funktion** angezeigt.<br /><br /> Sie können den standardmäßig festgelegten **Eigenschaftentyp** ändern, wodurch ein Wert an die Get-Funktion übergeben wird. Sie können Parameter für die Funktionen `Get` und `Set` angeben.|

- **Get-Funktion**

  ATL-Schnittstellen Legt diese Eigenschaft als lesbar fest. Die `Get`-Methode wird also erstellt, um diese Eigenschaft aus dem Objekt abzurufen. Wählen Sie **Get** oder **Put** oder beide aus.

- **Put-Funktion**

  Nur ATL-Schnittstellen Legt die Eigenschaft als schreibbar fest. Die `Put`-Methode wird also für das Festlegen bzw. „Einfügen“ dieser Eigenschaft des Objekts erstellt. Wählen Sie **Get** oder **Put** oder beide aus. Wenn Sie diese Option auswählen, können Sie die Methode auf zwei Arten implementieren:

  |Option|Beschreibung|
  |------------|-----------------|
  |**PropPut**|Die [PropPut](../windows/attributes/propput.md)-Funktion gibt eine Kopie des Objekts zurück. Dies ist die Standardeinstellung und die gängigste Methode, um die Eigenschaft schreibbar zu machen.|
  |**PropPutRef**|Die [PropPutRef](../windows/attributes/propputref.md)-Funktion gibt einen Verweis auf das Objekt statt einer Kopie des Objekts zurück. Diese Option sollten Sie für Objekte (z.B. große Strukturen oder Arrays) verwenden, deren Initialisierung aufwändig sein kann.|

- **Parameterattribute**

  Nur ATL-Schnittstellen Legt fest, ob der Parameter, der durch **Parametername** festgelegt wurde, `in`, `out`, beides oder keines davon ist.

  |Option|Beschreibung|
  |------------|-----------------|
  |`in`|Gibt an, dass der Parameter von der aufrufenden Prozedur an die aufgerufene Prozedur übergeben wird.|
  |`out`|Gibt an, dass der Zeigerparameter an von der aufgerufenen Prozedur an die aufrufende Prozedur zurückgegeben wird (vom Server an den Client).|

- **Parametertyp**

  Legt den Datentyp des Parameters fest. Wählen Sie den Typ aus der Liste aus.

- **Parametername**

  Legt den Namen eines Parameters fest, den Sie zur Eigenschaft hinzufügen, sofern die Eigenschaft über Parameter verfügt. Wenn Sie **Hinzufügen** auswählen, wird der Parametername in der **Parameterliste** angezeigt.

- **Parameterliste**

  Zeigt die Liste der Attribute an, die zur Eigenschaft hinzugefügt werden sollen. Jedes Element in der Liste besteht aus dem Parameternamen, dem Parametertyp und den Attributen. Verwenden Sie **Hinzufügen** und **Entfernen**, um die Liste zu aktualisieren.

- **Add**

  Fügt den Parameter hinzu, den Sie in **Parametername** und **Parametertyp** eingeben, zur **Parameterliste** hinzu. Wählen Sie **Hinzufügen** aus, um der Liste einen Parameter hinzuzufügen.

- **Entfernen**

  Entfernt den ausgewählten Parameter aus der **Parameterliste**.

- **Standardeigenschaft**

  Nur MFC-Disp-Schnittstellen Legt diese Eigenschaft als Standard für die Schnittstelle fest. Eine Schnittstelle kann nur eine Standardeigenschaft besitzen. Sobald Sie die Standardeigenschaft angeben, ist dieses Feld für jede weitere Eigenschaft, die Sie zur Schnittstelle hinzufügen, nicht verfügbar.

## <a name="idl-attributes-add-property-wizard"></a>IDL-Attribute, Assistent zum Hinzufügen von Eigenschaften

Verwenden Sie diese Seite des Assistenten zum Hinzufügen von Eigenschaften, um IDL-Einstellungen (Interface Definiton Language) für die Eigenschaft anzugeben.

- `id`

  Legt die numerische ID fest, die die Eigenschaft identifiziert. Diese Option ist nicht für Eigenschaften von benutzerdefinierten Schnittstellen verfügbar. Informationen finden Sie in der *MIDL-Referenz* unter [id](/windows/win32/Midl/id).

- `helpcontext`

  Gibt eine Kontext-ID an, die das Anzeigen von Informationen über diese Eigenschaft in der Hilfedatei ermöglicht. Informationen finden Sie in der *MIDL-Referenz* unter [helpcontext](/windows/win32/Midl/helpcontext).

- `helpstring`

  Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird. Standardmäßig ist sie auf **`property`** &nbsp;*Name&nbsp;der Eigenschaft* festgelegt. Informationen finden Sie in der *MIDL-Referenz* unter [helpstring](/windows/win32/Midl/helpstring).

### <a name="other-options"></a>Weitere Optionen

Nicht alle Optionen sind für alle Eigenschaftentypen verfügbar.

|Option|Beschreibung|
|------------|-----------------|
|`bindable`|Gibt an, dass die Eigenschaft die Datenbindung unterstützt. Informationen finden Sie in der *MIDL-Referenz* unter [bindable](/windows/win32/Midl/bindable). Diese Option ist standardmäßig für die vordefinierte Implementierung der Eigenschaft festgelegt und kann nicht geändert werden.|
|`defaultbind`|Gibt an, dass diese einzelne bindbare Eigenschaft das Objekt am besten darstellt. Informationen finden Sie in der *MIDL-Referenz* unter [defaultbind](/windows/win32/Midl/defaultbind).|
|`displaybind`|Gibt an, dass diese Eigenschaft für den Benutzer als bindbar angezeigt werden soll. Informationen finden Sie in der *MIDL-Referenz* unter [displaybind](/windows/win32/Midl/displaybind).|
|`immediatebind`|Gibt an, dass die Datenbank umgehend von allen an dieser Eigenschaft eines datengebundenen Objekts vorgenommenen Änderungen benachrichtigt wird. Informationen finden Sie in der *MIDL-Referenz* unter [immediatebind](/windows/win32/Midl/immediatebind).|
|`defaultcollelem`|Gibt an, dass die Eigenschaft eine Accessorfunktion für ein Element der Standardsammlung ist. Informationen finden Sie in der *MIDL-Referenz* unter [defaultcollelem](/windows/win32/Midl/defaultcollelem).|
|`nonbrowsable`|Markiert einen Member einer Schnittstelle oder Disp-Schnittstelle, der nicht in einem Eigenschaftenbrowser angezeigt werden soll. Informationen finden Sie in der *MIDL-Referenz* unter [nonbrowsable](/windows/win32/Midl/nonbrowsable).|
|`requestedit`|Gibt an, dass die Eigenschaft die `OnRequestEdit`-Benachrichtigung unterstützt. Weitere Informationen finden Sie unter [requestedit](/windows/win32/Midl/requestedit) in der *MIDL-Referenz*. Diese Option ist standardmäßig für die vordefinierte Implementierung der Eigenschaft festgelegt und kann nicht geändert werden.|
|`source`|Gibt an, dass ein Member dieser Eigenschaft eine Ereignisquelle ist. Informationen finden Sie in der *MIDL-Referenz* unter [source](/windows/win32/Midl/source).|
|`hidden`|Gibt an, dass die Eigenschaft vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll. Informationen finden Sie in der *MIDL-Referenz* unter [hidden](/windows/win32/Midl/hidden).|
|`restricted`|Gibt an, dass die Eigenschaft nicht beliebig aufgerufen werden kann. Informationen finden Sie in der *MIDL-Referenz* unter [restricted](/windows/win32/Midl/restricted).|
|`local`|Gibt für den MIDL-Compiler an, dass die Eigenschaft lokal ist. Informationen finden Sie in der *MIDL-Referenz* unter [local](/windows/win32/Midl/local).|

## <a name="stock-properties"></a>Basiseigenschaften

Wenn Sie einer MFC-Disp-Schnittstelle mithilfe des [Assistenten zum Hinzufügen von Eigenschaften](#idl-attributes-add-property-wizard) eine Eigenschaft hinzufügen, können Sie auf der [Namen](#names-add-property-wizard)-Seite des Assistenten eine Basiseigenschaft aus der Liste **Eigenschaftennamen** auswählen. Dort stehen die folgenden Eigenschaften zur Auswahl:

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|`Appearance`|Ruft einen Wert ab, der die Darstellung des Steuerelements bestimmt, oder legt diesen fest. Die Eigenschaft `Appearance` des Steuerelements kann dreidimensionale Anzeigeeffekte anzeigen oder ausblenden. Dies ist eine Lese-/Schreibumgebungseigenschaft.|
|`BackColor`|Gibt die Ambient-Eigenschaft `BackColor` des Steuerelements zurück oder legt diese auf eine Palettenfarbe (RGB) oder eine vordefinierte Systemfarbe fest. Der Wert entspricht standardmäßig der Vordergrundfarbe des Containers des Steuerelements. Dies ist eine Lese-/Schreibumgebungseigenschaft.|
|`BorderStyle`|Gibt die Rahmenart eines Steuerelements zurück oder legt diese fest. Dies ist eine Lese-/Schreibeigenschaft.|
|`Caption`|Gibt die `Caption`-Eigenschaft des Steuerelements zurück oder legt diese fest. Die Beschriftung ist der Titel des Fensters. `Caption` verfügt nicht über den Implementierungstyp **Membervariable**.|
|`Enabled`|Gibt die `Enabled`-Eigenschaft des Steuerelements zurück oder legt diese fest. Ein aktiviertes Steuerelement kann auf vom Benutzer generierte Ereignisse reagieren.|
|`Font`|Gibt die Ambient-Schriftart des Steuerelements zurück oder legt diese fest. Wenn das Steuerelement über keine Schriftart verfügt, wird NULL zurückgegeben.|
|`ForeColor`|Gibt die Ambient-Eigenschaft `ForeColor` des Steuerelements zurück oder legt diese fest.|
|`hWnd`|Gibt die `hWnd`-Eigenschaft des Steuerelements zurück oder legt diese fest. `hWnd` verfügt nicht über den Implementierungstyp **Membervariable**.|
|`ReadyState`|Gibt die `ReadyState`-Eigenschaft des Steuerelements zurück oder legt diese fest. Ein Steuerelement kann folgenden Status aufweisen: nicht initialisiert, initialisiert, wird geladen, interaktiv und abgeschlossen. Weitere Informationen finden Sie unter [READYSTATE](/previous-versions/aa768362\(v=vs.85\)) im *Internet SDK*.|
|`Text`|Gibt den Text zurück, der in einem Steuerelement enthalten ist, oder legt diesen fest. `Text` verfügt nicht über den Implementierungstyp **Membervariable**.|
