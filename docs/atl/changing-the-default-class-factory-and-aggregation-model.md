---
title: Ändern der Standardklassenfactory und des Aggregations Modells
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 1c97d8f63a441fab2b76c6e0509e4b3f384308ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220885"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Ändern der Standardklassenfactory und des Aggregations Modells

ATL verwendet [CComCoClass](../atl/reference/ccomcoclass-class.md) , um die Standardklassenfactory und das Aggregations Modell für Ihr Objekt zu definieren. `CComCoClass`Gibt die folgenden beiden Makros an:

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) Deklariert die Klassenfactory als [CComClassFactory](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) Deklariert, dass das Objekt aggregiert werden kann.

Sie können diese Standardeinstellungen überschreiben, indem Sie in der Klassendefinition ein anderes Makro angeben. Wenn Sie z. b. [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) anstelle von verwenden möchten `CComClassFactory` , geben Sie das [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) -Makro an:

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Zwei weitere Makros, die eine Klassenfactory definieren, sind [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) und [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

ATL verwendet auch den **`typedef`** Mechanismus, um das Standardverhalten zu implementieren. Das DECLARE_AGGREGATABLE-Makro verwendet beispielsweise, **`typedef`** um einen Typ mit dem Namen zu definieren `_CreatorClass` , auf den dann in der ATL verwiesen wird. Beachten Sie, dass in einer abgeleiteten Klasse ein **`typedef`** mit dem gleichen Namen wie die Basisklasse **`typedef`** Ergebnisse in ATL verwendet, die ihre Definition verwendet und das Standardverhalten überschreiben.

## <a name="see-also"></a>Weitere Informationen

[Grundlagen von ATL-COM-Objekten](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Aggregation und klassenfactorymakros](../atl/reference/aggregation-and-class-factory-macros.md)
