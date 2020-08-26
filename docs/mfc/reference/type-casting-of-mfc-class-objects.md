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
ms.openlocfilehash: e3702ced83021e42ac6bf71a78efc51fa07b8be9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840491"
---
# <a name="type-casting-of-mfc-class-objects"></a>Typumwandlung von MFC-Klassenobjekten

Typumwandlungs Makros bieten eine Möglichkeit, einen bestimmten Zeiger auf einen Zeiger umzuwandeln, der auf ein Objekt einer bestimmten Klasse zeigt, mit oder ohne zu überprüfen, ob die Umwandlung zulässig ist.

In der folgenden Tabelle sind die MFC-Typumwandlungs Makros aufgeführt.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makros, die Zeiger auf MFC-Klassen Objekte umwandeln

|Name|Beschreibung|
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Wandelt einen Zeiger auf einen Zeiger auf ein Klassenobjekt um, während überprüft wird, ob die Umwandlung zulässig ist.|
|[STATIC_DOWNCAST](#static_downcast)|Wandelt einen Zeiger auf ein Objekt von einer Klasse in einen Zeiger eines verknüpften Typs um. In einem Debugbuild bewirkt eine Assert-Bestätigung, wenn das Objekt kein "Art" des Zieltyps ist.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a> DYNAMIC_DOWNCAST

Bietet eine praktische Möglichkeit, einen Zeiger auf einen Zeiger auf ein Klassenobjekt umzuwandeln, während überprüft wird, ob die Umwandlung zulässig ist.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parameter

*class*<br/>
Der Name einer Klasse.

*Zeichner*<br/>
Ein Zeiger, der in einen Zeiger auf ein Objekt der Type- *Klasse*umgewandelt werden soll.

### <a name="remarks"></a>Bemerkungen

Das Makro wandelt den *Zeiger* Parameter in einen Zeiger auf ein Objekt des *Klassen* Parameter Typs um.

Wenn das Objekt, auf das der Zeiger verweist, eine "Art" der identifizierten Klasse ist, gibt das Makro den entsprechenden Zeiger zurück. Wenn es sich nicht um eine gültige Umwandlung handelt, gibt das Makro NULL zurück.

## <a name="static_downcast"></a><a name="static_downcast"></a> STATIC_DOWNCAST

Wandelt *pObject* in einen Zeiger auf ein *class_name* Objekt um.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Klasse, in die umgewandelt wird.

*pObject*<br/>
Der Zeiger, der in einen Zeiger auf ein *class_name* Objekt umgewandelt werden soll.

### <a name="remarks"></a>Bemerkungen

*pObject* muss entweder NULL sein oder auf ein Objekt einer Klasse verweisen, das direkt oder indirekt von *class_name*abgeleitet ist. In Builds Ihrer Anwendung, bei der das _DEBUG Präprozessorsymbol definiert ist, wird das Makro bestätigt, wenn *pObject* nicht NULL ist, oder wenn es auf ein Objekt verweist, das keine "Art" der im Parameter *class_name* angegebenen Klasse ist (siehe [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). In nicht **_DEBUG** Builds führt das Makro die Umwandlung ohne Typüberprüfung durch.

Die im *class_name* -Parameter angegebene Klasse muss von abgeleitet werden `CObject` und die DECLARE_DYNAMIC und IMPLEMENT_DYNAMIC, die DECLARE_DYNCREATE und IMPLEMENT_DYNCREATE oder die DECLARE_SERIAL-und IMPLEMENT_SERIAL-Makros verwenden, wie im Artikel [CObject-Klasse: Ableiten einer Klasse von CObject](../../mfc/deriving-a-class-from-cobject.md)erläutert.

Sie können z. b. einen Zeiger auf `CMyDoc` , aufgerufen `pMyDoc` , in einen Zeiger auf umwandeln, indem Sie den folgenden `CDocument` Ausdruck verwenden:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Wenn `pMyDoc` nicht auf ein Objekt verweist, das direkt oder indirekt von abgeleitet `CDocument` ist, wird das Makro von bestätigt.

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
