---
title: _com_ptr_t-Extraktoren
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190026"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t-Extraktoren

**Microsoft-spezifisch**

Extrahieren Sie den gekapselten COM-Schnittstellenzeiger.

## <a name="syntax"></a>Syntax

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Bemerkungen

- die **Operator Schnittstelle** <strong>\*</strong> gibt den gekapselten Schnittstellen Zeiger zurück, der möglicherweise NULL ist.

- **& der Operator Schnittstelle** Gibt einen Verweis auf den gekapselten Schnittstellen Zeiger zurück und gibt einen Fehler aus, wenn der Zeiger NULL ist.

- der **Operator** <strong>\*</strong> ermöglicht, dass ein intelligentes Zeiger Objekt so verhält, als wäre es die tatsächliche gekapselte Schnittstelle beim dereferenzieren.

- **Operator->** Ermöglicht es einem intelligenten Zeiger Objekt, so zu agieren, als wäre es die tatsächliche gekapselte Schnittstelle beim dereferenzieren.

- **Operator &** Gibt jeden gekapselten Schnittstellen Zeiger frei, ersetzt ihn durch Null und gibt die Adresse des gekapselten Zeigers zurück. Dadurch kann der intelligente Zeiger über eine Adresse an eine Funktion übergeben werden, die über einen *out* -Parameter verfügt, über den ein Schnittstellen Zeiger zurückgegeben wird.

- **Operator bool** Ermöglicht die Verwendung eines intelligenten Zeiger Objekts in einem bedingten Ausdruck. Dieser Operator gibt true zurück, wenn der Zeiger nicht NULL ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
