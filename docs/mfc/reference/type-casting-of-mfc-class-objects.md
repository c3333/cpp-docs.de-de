---
title: Typumwandlung von MFC-Klassenobjekten
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372896"
---
# <a name="type-casting-of-mfc-class-objects"></a>Typumwandlung von MFC-Klassenobjekten

Typumwandlungsmakros bieten eine Möglichkeit, einen bestimmten Zeiger auf einen Zeiger zu werfen, der auf ein Objekt einer bestimmten Klasse zeigt, mit oder ohne zu überprüfen, ob die Umwandlung legal ist.

In der folgenden Tabelle sind die MFC-Typumwandlungsmakros aufgeführt.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makros, die Zeiger auf MFC-Klassenobjekte umwerfen

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Gibt einen Zeiger auf einen Zeiger auf ein Klassenobjekt, während überprüft wird, ob die Umwandlung legal ist.|
|[STATIC_DOWNCAST](#static_downcast)|Gibt einen Zeiger auf ein Objekt von einer Klasse auf einen Zeiger eines verknüpften Typs um. Verursacht in einem Debugbuild einen ASSERT, wenn das Objekt keine "Art" des Zieltyps ist.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

Bietet eine praktische Möglichkeit, einen Zeiger auf einen Zeiger auf ein Klassenobjekt zu werfen, während überprüft wird, ob die Umwandlung legal ist.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parameter

*class*<br/>
Der Name einer Klasse.

*Zeiger*<br/>
Ein Zeiger, der auf einen Zeiger auf ein Objekt der *Typklasse*umgeworfen werden soll.

### <a name="remarks"></a>Bemerkungen

Das Makro wird den *Zeigerparameter* in einen Zeiger auf ein Objekt des *Klassenparameterstyps* umwerfen.

Wenn das Objekt, auf das vom Zeiger verwiesen wird, eine "Art" der identifizierten Klasse ist, gibt das Makro den entsprechenden Zeiger zurück. Wenn es sich nicht um eine legale Umwandlung handelt, gibt das Makro NULL zurück.

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

Gibt *pobject* auf einen Zeiger auf ein *class_name* Objekt.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Klasse, in die gecastet wird.

*pobject*<br/>
Der Zeiger, der auf einen Zeiger auf ein *class_name* Objekt s.

### <a name="remarks"></a>Bemerkungen

*pobject* muss entweder NULL sein oder auf ein Objekt einer Klasse verweisen, das direkt oder indirekt von *class_name*abgeleitet wird. In Builds Ihrer Anwendung mit dem _DEBUG Präprozessorsymbol definiert, wird das Makro ASSERT, wenn *pobject* nicht NULL ist, oder wenn es auf ein Objekt verweist, das keine "Art" der im *Parameter class_name* angegebenen Klasse ist (siehe [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). In nicht **_DEBUG-Builds** führt das Makro die Umwandlung ohne Typprüfung durch.

Die im *Parameter class_name* angegebene Klasse `CObject` muss von den DECLARE_DYNAMIC und IMPLEMENT_DYNAMIC, den DECLARE_DYNCREATE und IMPLEMENT_DYNCREATE oder den DECLARE_SERIAL- und IMPLEMENT_SERIAL-Makros abgeleitet werden und diese verwenden, wie im Artikel [CObject-Klasse: Ableiten einer Klasse von CObject](../../mfc/deriving-a-class-from-cobject.md)erläutert.

Sie können z. B. `CMyDoc`einen `pMyDoc`Zeiger auf , `CDocument` aufgerufen , auf einen Zeiger auf die Verwendung dieses Ausdrucks umsetzen:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Wenn `pMyDoc` nicht auf ein Objekt, das `CDocument`direkt oder indirekt von abgeleitet wird, weist das Makro ASSERT auf.

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
