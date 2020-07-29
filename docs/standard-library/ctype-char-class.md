---
title: ctype&lt;char&gt;-Klasse
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: d2c74ef46babe388cfa6d649e8b4501b7c235bb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220963"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt;-Klasse

Bei der-Klasse handelt es sich um eine explizite Spezialisierung der Klassen Vorlage `ctype\<CharType>` zum Eingeben von **`char`** , die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um verschiedene Eigenschaften eines Zeichens vom Typ zu bezeichnen **`char`** .

## <a name="syntax"></a>Syntax

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Bemerkungen

Die explizite Spezialisierung unterscheidet sich auf verschiedene Arten von der Klassen Vorlage:

- Ein Objekt der Klasse `ctype<char>` speichert einen Zeiger auf das erste Element einer CType-Masken Tabelle, ein Array von UCHAR_MAX + 1 Elementen vom Typ `ctype_base::mask` . Außerdem wird ein boolesches Objekt gespeichert, das angibt, ob das Array gelöscht werden soll (mithilfe von `operator delete[]` ), wenn das CType- \< **Elem**> Objekt zerstört wird.

- Mit dem einzigen öffentlichen Konstruktor können Sie `tab` , die CType Mask-Tabelle und `del` , das boolesche Objekt, das true ist, wenn das Array gelöscht werden soll, wenn das- `ctype<char>` Objekt zerstört wird, sowie den Verweis Zähler-Parameter Refs angeben.

- Die geschützte Member-Funktion `table` gibt die gespeicherte CType Mask-Tabelle zurück.

- Das statische Member-Objekt `table_size` gibt die Mindestanzahl von Elementen in einer CType Mask-Tabelle an.

- Die geschützte statische Member-Funktion `classic_table` (gibt die CType-Masken Tabelle zurück, die für das Gebiets Schema "C" geeignet ist.

- Die geschützten virtuellen Memberfunktionen [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is) bzw. [do_scan_not](../standard-library/ctype-class.md#do_scan_not) werden nicht verwendet. Die entsprechenden öffentlichen Memberfunktionen führen die jeweiligen Vorgänge selbst aus.

Die Memberfunktionen [do_narrow](../standard-library/ctype-class.md#do_narrow) und [do_widen](../standard-library/ctype-class.md#do_widen) kopieren Elemente unverändert.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[facetklasse](locale-class.md#facet_class)\
[Ctype_base-Klasse](../standard-library/ctype-base-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
