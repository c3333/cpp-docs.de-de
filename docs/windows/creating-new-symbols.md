---
title: 'Gewusst wie: Erstellen von SymbolenC++()'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 1c69e8878885acd80c285691fb0861a476af03ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160514"
---
# <a name="how-to-create-symbols-c"></a>Gewusst wie: Erstellen von SymbolenC++()

Wenn Sie ein neues Projekt beginnen, ist es möglicherweise bequem, die erforderlichen Symbolnamen zuzuordnen, bevor Sie die Ressourcen erstellen, denen Sie zugewiesen werden.

> [!NOTE]
> Wenn das Projekt noch keine RC-Datei enthält, finden Sie weitere Informationen unter Gewusst [wie: Erstellen von Ressourcen](../windows/how-to-create-a-resource-script-file.md).

Im Dialogfeld **Ressourcen Symbole** können Sie neue Ressourcen Symbole hinzufügen, die angezeigten Symbole ändern oder die Position im Quellcode überspringen, an der ein Symbol verwendet wird.

Das Dialogfeld enthält die folgenden Eigenschaften:

|Eigenschaft|BESCHREIBUNG|
|--------------------------|------------------------------------------|
|**Name**|Zeigt den Namen des Symbols an.<br/><br/>Weitere Informationen finden Sie unter [Einschränkungen für Symbol Namen](../windows/symbol-name-restrictions.md).|
|**Wert**|Zeigt den numerischen Wert des Symbols an.<br/><br/>Weitere Informationen finden Sie unter [Einschränkungen bei Symbol Werten](../windows/symbol-value-restrictions.md).|
|**Wird verwendet**|Bei Auswahl dieser Option wird angegeben, dass das Symbol von einer oder mehreren Ressourcen verwendet wird.<br/><br/>Die Ressource oder Ressourcen sind im Feld **verwendet von** aufgeführt.|
|**Schreibgeschützte Symbole anzeigen**|Bei Auswahl dieser Option werden schreibgeschützte Ressourcen angezeigt.<br/><br/>Standardmäßig werden im Dialogfeld " **Ressourcen Symbol** " nur die änderbaren Ressourcen in der Ressourcen Skriptdatei angezeigt. wenn diese Option aktiviert ist, werden änderbare Ressourcen in fettem Text angezeigt, und schreibgeschützte Ressourcen werden als nur-Text angezeigt.|
|**Verwendet von**|Zeigt die Ressource bzw. Ressourcen an, in der/denen das in der Symbolliste markierte Symbol verwendet wird.<br/><br/>Um zum Editor für eine bestimmte Ressource zu wechseln, wählen Sie die Ressource im Feld **verwendet von** aus, und wählen Sie die Option **Verwendung anzeigen**aus.|
|**Neu**|Öffnet das Dialogfeld **Neues Symbol** , in dem Sie den Namen und ggf. einen Wert für einen neuen symbolischen Ressourcen Bezeichner definieren können.|
|**Änderung**|Öffnet das Dialogfeld **Symbol ändern** , in dem Sie den Namen oder den Wert eines Symbols ändern können.<br/><br/>Wenn das Symbol für ein Steuerelement oder eine Ressource in Gebrauch ist, kann das Symbol nur im entsprechenden Ressourcen-Editor geändert werden. Weitere Informationen finden Sie unter [Verwalten von Symbolen](../windows/changing-unassigned-symbols.md).|
|**Verwendung anzeigen**|Öffnet die Ressource, die das Symbol enthält, im entsprechenden Ressourcen-Editor.|

## <a name="create-symbols"></a>Symbole erstellen

### <a name="to-create-a-new-symbol"></a>So erstellen Sie ein neues Symbol

1. Wählen Sie im Dialogfeld **Ressourcen Symbole** die Option **neu**aus.

1. Geben Sie im Feld **Name** einen Symbolnamen ein.

1. Akzeptieren Sie den zugewiesenen Symbolwert, oder geben Sie im Feld **Wert** einen neuen Wert ein.

1. Wählen Sie **OK** aus, um das neue Symbol der Symbolliste hinzuzufügen.

> [!NOTE]
> Wenn Sie einen bereits vorhandenen Symbolnamen eingeben, wird eine Meldung angezeigt, aus der hervorgeht, dass ein Symbol mit diesem Namen bereits definiert ist. Sie können nicht zwei oder mehr Symbole mit dem gleichen Namen definieren, Sie können jedoch unterschiedliche Symbole mit demselben numerischen Wert definieren.

## <a name="to-view-resource-symbols"></a>So zeigen Sie Ressourcensymbole an

Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Ressourcen Symbole** aus, um im Dialogfeld **Ressourcen Symbole** eine Ressourcen Symboltabelle anzuzeigen.

> [!NOTE]
> Aktivieren Sie das Kontrollkästchen schreibgeschützte **Symbole anzeigen** , um vordefinierte Symbole anzuzeigen.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>So öffnen Sie den Ressourcen-Editor für ein bestimmtes Symbol

Wenn Sie Symbole in den **Ressourcen Symbolen**durchsuchen, benötigen Sie möglicherweise weitere Informationen zur Verwendung eines bestimmten Symbols. Die Schaltfläche **Verwendung anzeigen** bietet eine schnelle Möglichkeit, diese Informationen zu erhalten.

1. Wählen Sie im Dialogfeld **Ressourcen Symbole** im Feld **Name** ein Symbol aus.

1. Wählen Sie im Feld **verwendet von** den gewünschten Ressourcentyp aus.

1. Wählen Sie die Schaltfläche **Verwendung anzeigen** aus.

   Die Ressource wird im geeigneten Editor-Fenster geöffnet.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcenbezeichner (Symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Gewusst wie: Verwalten von Symbolen](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Vordefinierte Symbol-IDs](../windows/predefined-symbol-ids.md)<br/>
