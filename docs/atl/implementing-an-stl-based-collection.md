---
title: Implementieren einer C++-Standardbibliotheks-basierten Sammlung
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319441"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementieren einer C++-Standardbibliotheks-basierten Sammlung

ATL stellt `ICollectionOnSTLImpl` die Schnittstelle bereit, mit der Sie C++ Standard Library-basierte Auflistungsschnittstellen für Ihre Objekte schnell implementieren können. Um zu verstehen, wie diese Klasse funktioniert, arbeiten Sie sich ein einfaches Beispiel (unten) an, das diese Klasse zum Implementieren einer schreibgeschützten Auflistung für Automation-Clients verwendet.

Der Beispielcode stammt aus dem [ATLCollections-Beispiel](../overview/visual-cpp-samples.md).

Um dieses Verfahren abzuschließen, werden Sie:

- [Generieren Sie ein neues einfaches Objekt](#vccongenerating_an_object).

- [Bearbeiten Sie die IDL-Datei](#vcconedit_the_idl) für die generierte Schnittstelle.

- [Erstellen Sie fünf typedefs,](#vcconstorage_and_exposure_typedefs) die beschreiben, wie die Auflistungselemente gespeichert werden und wie sie über COM-Schnittstellen für Clients verfügbar gemacht werden.

- [Erstellen Sie zwei typedefs für Kopierrichtlinienklassen](#vcconcopy_classes).

- [Erstellen Sie typedefs für die Enumerator- und Auflistungsimplementierungen](#vcconenumeration_and_collection).

- [Bearbeiten Sie den vom Assistenten generierten C++-Code, um den Auflistungstypdef zu verwenden.](#vcconedit_the_generated_code)

- [Fügen Sie Code hinzu, um die Auflistung aufzufüllen.](#vcconpopulate_the_collection)

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>Generieren eines neuen einfachen Objekts

Erstellen Sie ein neues Projekt, um sicherzustellen, dass das Feld Attribute unter Anwendungseinstellungen deaktiviert ist. Verwenden Sie das Dialogfeld ATL-Klasse hinzufügen und den `Words`Assistenten zum Hinzufügen einfacher Objekte, um ein einfaches Objekt mit dem Namen zu generieren. Stellen Sie sicher, `IWords` dass eine duale Schnittstelle generiert wird, die aufgerufen wird. Objekte der generierten Klasse werden verwendet, um eine Auflistung von Wörtern (d. h. Zeichenfolgen) darzustellen.

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>Bearbeiten der IDL-Datei

Öffnen Sie nun die IDL-Datei, und `IWords` fügen Sie die drei Eigenschaften hinzu, die erforderlich sind, um in eine schreibgeschützte Auflistungsschnittstelle umzuwandeln, wie unten gezeigt:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Dies ist das Standardformular für eine schreibgeschützte Sammlungsschnittstelle, die unter Berücksichtigung von Automation-Clients entwickelt wurde. Die nummerierten Kommentare in dieser Schnittstellendefinition entsprechen den folgenden Kommentaren:

1. Auflistungsschnittstellen sind in der Regel `_NewEnum` dual, `IDispatch::Invoke`da Automatisierungsclients über auf die Eigenschaft zugreifen. Automatisierungsclients können jedoch über die vtable auf die verbleibenden Methoden zugreifen, sodass duale Schnittstellen Dispinterfaces vorzuziehen sind.

1. Wenn eine duale Schnittstelle oder Dispinterface zur Laufzeit nicht erweitert wird (d. `IDispatch::Invoke`h., Sie stellen keine zusätzlichen Methoden oder Eigenschaften über zur Verfügung ), sollten Sie das **Nonextensible-Attribut** auf Ihre Definition anwenden. Dieses Attribut ermöglicht es Automation-Clients, die vollständige Codeüberprüfung zur Kompilierungszeit durchzuführen. In diesem Fall sollte die Schnittstelle nicht erweitert werden.

1. Die richtige DISPID ist wichtig, wenn Sie möchten, dass Automation-Clients diese Eigenschaft verwenden können. (Beachten Sie, dass es nur einen Unterstrich in DISPID_NEWENUM gibt.)

1. Sie können einen beliebigen Wert als `Item` DISPID der Eigenschaft angeben. Verwendet `Item` jedoch in der Regel DISPID_VALUE, um sie zur Standardeigenschaft der Auflistung zu machen. Dadurch können Automation-Clients auf die Eigenschaft verweisen, ohne sie explizit zu benennen.

1. Der Datentyp, der für `Item` den Rückgabewert der Eigenschaft verwendet wird, ist der Typ des Elements, das in der Auflistung gespeichert ist, was COM-Clients betrifft. Die Schnittstelle gibt Zeichenfolgen zurück, daher sollten Sie den standardmäßigen COM-Zeichenfolgentyp BSTR verwenden. Sie können die Daten intern in einem anderen Format speichern, wie Sie in Kürze sehen werden.

1. Der für die DISPID `Count` der Eigenschaft verwendete Wert ist völlig willkürlich. Es gibt keine Standard-DISPID für diese Eigenschaft.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>Erstellen von Typedefs für Lagerung und Belichtung

Sobald die Erfassungsschnittstelle definiert ist, müssen Sie entscheiden, wie die Daten gespeichert werden und wie die Daten über den Enumerator verfügbar gemacht werden.

Die Antworten auf diese Fragen können in Form einer Reihe von typedefs bereitgestellt werden, die Sie am oberen Rand der Headerdatei für Ihre neu erstellte Klasse hinzufügen können:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

In diesem Fall speichern Sie die Daten als **std::vector** von **std::string**s. **std::vector** ist eine C++-Standardbibliothekscontainerklasse, die sich wie ein verwaltetes Array verhält. **std::string** ist die Zeichenfolgenklasse der C++ Standardbibliothek. Diese Klassen erleichtern die Arbeit mit einer Auflistung von Zeichenfolgen.

Da die Visual Basic-Unterstützung für den Erfolg dieser Schnittstelle von `_NewEnum` entscheidender Bedeutung `IEnumVARIANT` ist, muss der von der Eigenschaft zurückgegebene Enumerator die Schnittstelle unterstützen. Dies ist die einzige Enumeratorschnittstelle, die von Visual Basic verstanden wird.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>Erstellen von Typedefs für Kopierrichtlinienklassen

Die typedefs, die Sie bisher erstellt haben, stellen alle Informationen bereit, die Sie zum Erstellen weiterer typedefs für die Kopierklassen benötigen, die vom Enumerator und der Auflistung verwendet werden:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

In diesem Beispiel können Sie `GenericCopy` die benutzerdefinierte Klasse verwenden, die in VCUE_Copy.h und VCUE_CopyString.h aus dem [ATLCollections-Beispiel](../overview/visual-cpp-samples.md) definiert ist. Sie können diese Klasse in anderem Code verwenden, müssen jedoch `GenericCopy` möglicherweise weitere Spezialisierungen definieren, um Datentypen zu unterstützen, die in Ihren eigenen Sammlungen verwendet werden. Weitere Informationen finden Sie unter [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md).

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>Erstellen von Typedefs für Enumeration und Auflistung

Jetzt wurden alle Vorlagenparameter bereitgestellt, die für die Spezialisierung der `CComEnumOnSTL` und `ICollectionOnSTLImpl` Klassen für diese Situation erforderlich sind, und wurden in Form von typedefs bereitgestellt. Um die Verwendung der Spezialisierungen zu vereinfachen, erstellen Sie zwei weitere typedefs, wie unten gezeigt:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Jetzt `CollectionType` ist ein Synonym für `ICollectionOnSTLImpl` eine Spezialisierung, die die `IWords` zuvor definierte Schnittstelle implementiert `IEnumVARIANT`und einen Enumerator bereitstellt, der unterstützt.

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>Bearbeiten des vom Assistenten generierten Codes

Nun müssen Sie `CWords` von der Schnittstellenimplementierung `CollectionType` ableiten, `IWords`die durch die typedef und nicht von dargestellt wird, wie unten gezeigt:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>Hinzufügen von Code zum Auffüllen der Sammlung

Das einzige, was bleibt, ist, den Vektor mit Daten zu füllen. In diesem einfachen Beispiel können Sie der Auflistung im Konstruktor für die Klasse einige Wörter hinzufügen:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Jetzt können Sie den Code mit dem Client Ihrer Wahl testen.

## <a name="see-also"></a>Siehe auch

[Auflistungen und Enumerationen](../atl/atl-collections-and-enumerators.md)<br/>
[ATLCollections-Beispiel](../overview/visual-cpp-samples.md)<br/>
[ATL-Kopierrichtlinienklassen](../atl/atl-copy-policy-classes.md)
