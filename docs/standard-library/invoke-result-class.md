---
title: invoke_result-Klasse
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: e3e1a28310660ad1fbdae4dd58973de378ddf364
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233131"
---
# <a name="invoke_result-class"></a>invoke_result-Klasse

Bestimmt den Rückgabetyp des Aufruf baren Typs, der die angegebenen Argument Typen zur Kompilierzeit annimmt. Hinzugefügt in c++ 17.

## <a name="syntax"></a>Syntax

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parameter

*Callable*\
Der abzufragende, aufgerufene Typ.

*Args*\
Die Typen der Argumentliste für den aufrufbaren, abzufragenden Typ.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Vorlage, um den Ergebnistyp der *Aufruf baren*(*args*...) zur Kompilierzeit zu bestimmen, wobei *Callable* und alle Typen in *args* ein beliebiger vollständiger Typ, ein Array mit unbekannter Grenze oder eine möglicherweise CV qualifizierte sind **`void`** . Der `type` Member der Klassen Vorlage benennt den Rückgabetyp von *Callable* , wenn er mit den Argumenten *args*... aufgerufen wird. Der `type` Member wird nur definiert, wenn *Callable* aufgerufen werden kann, wenn er mithilfe *Args*der Argumente Argumente... in einem nicht ausgewerteten Kontext. Andernfalls hat die Klassen Vorlage keinen Member `type` , der sfinae-Tests für einen bestimmten Satz von Argument Typen zur Kompilierzeit zulässt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
