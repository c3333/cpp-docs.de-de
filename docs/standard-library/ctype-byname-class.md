---
title: ctype_byname-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: dcaaff45fb33155710f788af4ceb657eff97464e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689732"
---
# <a name="ctype_byname-class"></a>ctype_byname-Klasse

In der abgeleiteten Klassen Vorlage wird ein Objekt beschrieben, das als CType-Facette eines bestimmten Gebiets Schemas fungieren kann und die Klassifizierung von Zeichen und die Konvertierung von Zeichen zwischen Groß-/Kleinschreibung und systemeigenen und Gebiets Schema spezifischen Zeichensätzen ermöglicht

## <a name="syntax"></a>Syntax

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>Hinweise

Das Verhalten wird durch das benannte Gebietsschema `_Locname` bestimmt. Jeder Konstruktor initialisiert sein Basisobjekt mit [ctype](../standard-library/ctype-class.md)\<CharType>( `_Refs`) oder der jeweiligen Entsprechung für die Basisklasse `ctype<char>`.

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Thread Safety in the C++ Standard Library (Threadsicherheit in der C++-Standardbibliothek)](../standard-library/thread-safety-in-the-cpp-standard-library.md)
