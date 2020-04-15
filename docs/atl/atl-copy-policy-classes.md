---
title: ATL-Kopierrichtlinienklassen
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317382"
---
# <a name="atl-copy-policy-classes"></a>ATL-Kopierrichtlinienklassen

Kopierrichtlinienklassen sind [Dienstprogrammklassen,](../atl/utility-classes.md) die zum Initialisieren, Kopieren und Löschen von Daten verwendet werden. Mithilfe von Richtlinienklassen, die kopieren, können Sie die Kopierssemantik für jeden Datentyp definieren und Konvertierungen zwischen verschiedenen Datentypen definieren.

ATL verwendet In den Implementierungen der folgenden Vorlagen Kopierrichtlinienklassen:

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumonSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

Durch das Einkapseln der Informationen, die zum Kopieren oder Konvertieren von Daten in einer Kopierrichtlinienklasse erforderlich sind, die als Vorlagenargument übergeben werden können, haben die ATL-Entwickler eine extreme Wiederverwendbarkeit dieser Klassen bereitgestellt. Wenn Sie z. B. eine Auflistung mit einem beliebigen Datentyp implementieren müssen, müssen Sie lediglich die entsprechende Kopierrichtlinie bereitstellen. Sie müssen nie den Code berühren, der die Auflistung implementiert.

## <a name="definition"></a>Definition

Definitionsgemäß ist eine Klasse, die die folgenden statischen Funktionen bereitstellt, eine Kopierrichtlinienklasse:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

Sie können die `DestinationType` Typen und *SourceType* durch beliebige Datentypen für jede Kopierrichtlinie ersetzen.

> [!NOTE]
> Obwohl Sie Kopierrichtlinienklassen für beliebige Datentypen definieren können, sollte die Verwendung der Klassen im ATL-Code die sinnvollen Typen einschränken. Wenn Sie z. B. eine Kopierrichtlinienklasse mit ATL-Auflistungs- oder Enumeratorimplementierungen verwenden, muss es sich um einen Typ handelt, `DestinationType` der als Parameter in einer COM-Schnittstellenmethode verwendet werden kann.

Verwenden Sie **init,** um Daten zu initialisieren, zu **kopieren,** um Daten zu kopieren, und zu **zerstören,** um die Daten freizugeben. Die genaue Bedeutung von Initialisierung, Kopieren und Zerstörung ist die Domäne der Kopierrichtlinienklasse und variiert je nach datentyp.

Für die Verwendung und Implementierung einer Kopierrichtlinienklasse gelten zwei Anforderungen:

- Der erste zu **kopierende** Parameter darf nur einen Zeiger auf Daten erhalten, die Sie zuvor mit **init**initialisiert haben.

- **destroy** darf immer nur einen Zeiger auf Daten erhalten, die Sie zuvor mithilfe von **init** initialisiert oder per **Kopie**kopiert haben.

## <a name="standard-implementations"></a>Standardimplementierungen

ATL stellt zwei Kopierrichtlinienklassen `_Copy` in `_CopyInterface` Form der und der Vorlagenklassen bereit:

- Die `_Copy` Klasse erlaubt nur homogenes Kopieren (keine Konvertierung zwischen Datentypen), da `DestinationType` sie nur einen einzelnen Vorlagenparameter bietet, um sowohl SourceType als *auch SourceType*anzugeben. Die generische Implementierung dieser Vorlage enthält keinen Initialisierungs- oder Vernichtungscode und verwendet `memcpy` zum Kopieren der Daten. ATL bietet auch Spezialisierungen `_Copy` für VARIANT-, LPOLESTR-, OLEVERB- und CONNECTDATA-Datentypen.

- Die `_CopyInterface` Klasse stellt eine Implementierung zum Kopieren von Schnittstellenzeigern gemäß Standard-COM-Regeln bereit. Wieder einmal erlaubt diese Klasse nur homogenes Kopieren, so `AddRef` dass sie eine einfache Zuweisung und einen Aufruf verwendet, um die Kopie auszuführen.

## <a name="custom-implementations"></a>Benutzerdefinierte Implementierungen

In der Regel müssen Sie eigene Kopierrichtlinienklassen für heterogenes Kopieren (d. h. Konvertierung zwischen Datentypen) definieren. Einige Beispiele für benutzerdefinierte Kopierrichtlinienklassen finden Sie in den Dateien VCUE_Copy.h und VCUE_CopyString.h im [ATLCollections-Beispiel.](../overview/visual-cpp-samples.md) Diese Dateien enthalten zwei Vorlagenkopierrichtlinienklassen `GenericCopy` und `MapCopy`, sowie `GenericCopy` eine Reihe von Spezialisierungen für verschiedene Datentypen.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy`können Sie den *SourceType* und `DestinationType` als Vorlagenargumente angeben. Hier ist die allgemeinste `GenericCopy` Form der Klasse von VCUE_Copy.h:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h enthält auch die folgenden Spezialisierungen `GenericCopy<BSTR>` `GenericCopy<VARIANT, BSTR>`dieser `GenericCopy<BSTR, VARIANT>`Klasse: , , . VCUE_CopyString.h enthält Spezialisierungen zum Kopieren von **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, und `GenericCopy<BSTR, std::string>`. Sie können `GenericCopy` verbessern, indem Sie weitere Spezialisierungen Ihrer eigenen bieten.

### <a name="mapcopy"></a>MapCopy

`MapCopy`geht davon aus, dass die kopierten Daten in einer C++-Standardbibliothekszuordnung gespeichert werden, sodass Sie den Kartentyp angeben können, in dem die Daten gespeichert werden, und den Zieltyp angeben. Die Implementierung der Klasse verwendet nur die von der *MapType-Klasse* bereitgestellten typedefs, `GenericCopy` um den Typ der Quelldaten zu bestimmen und die entsprechende Klasse aufzurufen. Es sind keine Spezialisierungen dieser Klasse erforderlich.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>Siehe auch

[Implementieren einer C++-Standardbibliotheks-basierten Sammlung](../atl/implementing-an-stl-based-collection.md)<br/>
[ATLCollections-Beispiel](../overview/visual-cpp-samples.md)
