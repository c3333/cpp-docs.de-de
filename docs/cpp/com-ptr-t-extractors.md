---
title: _com_ptr_t-Extraktoren
description: Beschreibt die Extraktions Operatoren für die _com_ptr_t-Klasse.
ms.date: 07/07/2020
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
ms.openlocfilehash: fb5441d87dc35ec6fbb495bc38d9041c1f2d2f33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220573"
---
# <a name="_com_ptr_t-extractors"></a>`_com_ptr_t`Extraktoren

**Microsoft-spezifisch**

Extrahieren Sie den gekapselten COM-Schnittstellenzeiger.

## <a name="syntax"></a>Syntax

```c++
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Bemerkungen

- **`operator Interface*`** Gibt den gekapselten Schnittstellen Zeiger zurück, der möglicherweise NULL ist.

- **`operator Interface&`** Gibt einen Verweis auf den gekapselten Schnittstellen Zeiger zurück und gibt einen Fehler aus, wenn der Zeiger NULL ist.

- **`operator*`** Ermöglicht es einem intelligenten Zeiger Objekt, so zu agieren, als wäre es die tatsächliche gekapselte Schnittstelle beim dereferenzieren.

- **`operator->`** Ermöglicht es einem intelligenten Zeiger Objekt, so zu agieren, als wäre es die tatsächliche gekapselte Schnittstelle beim dereferenzieren.

- **`operator&`** Gibt jeden gekapselten Schnittstellen Zeiger frei, ersetzt ihn durch Null und gibt die Adresse des gekapselten Zeigers zurück. Mit diesem Operator können Sie den intelligenten Zeiger per Adresse an eine Funktion übergeben, die über einen *out* -Parameter verfügt, über den ein Schnittstellen Zeiger zurückgegeben wird.

- **`operator bool`** Ermöglicht die Verwendung eines intelligenten Zeiger Objekts in einem bedingten Ausdruck. Dieser Operator gibt zurück, **`true`** Wenn der Zeiger nicht NULL ist.

  > [!NOTE]
  > Da **`operator bool`** nicht als deklariert ist **`explicit`** , kann `_com_ptr_t` implizit in konvertierbar sein **`bool`** , was in einen beliebigen skalaren Typ konvertiert werden kann. Dies kann in Ihrem Code unerwartete Folgen haben. Aktivieren Sie [Compilerwarnung (Stufe 4) C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) , um eine unbeabsichtigte Verwendung dieser Konvertierung zu verhindern.

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
