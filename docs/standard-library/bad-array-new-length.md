---
title: bad_array_new_length-Klasse
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: c4f4f58f7b28960bbacf695a675fbe4f20a54192
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443707"
---
# <a name="bad_array_new_length-class"></a>bad_array_new_length-Klasse

Die Klasse beschreibt eine Ausnahme, die ausgelöst wurde, um anzugeben, dass eine Zuordnungs Anforderung aufgrund einer Array Größe kleiner als 0 (null) oder größer als der Grenzwert nicht erfolgreich war.

## <a name="syntax"></a>Syntax

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Bemerkungen

Der von `what` zurückgegebene Wert ist eine von der Implementierung definierte C-Zeichenfolge. Keine der Memberfunktionen löst irgendeine Ausnahme aus.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<neue >

## <a name="see-also"></a>Weitere Informationen

[Ausnahme Klasse](../standard-library/exception-class.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
