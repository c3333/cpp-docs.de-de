---
title: Compilerklassen für COM-Unterstützung
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444431"
---
# <a name="compiler-com-support-classes"></a>Compilerklassen für COM-Unterstützung

**Microsoft-spezifisch**

Standardklassen werden verwendet, um einige der COM-Typen zu unterstützen. Die Klassen werden in \<comdef. h-> und in den von der Typbibliothek generierten Header Dateien definiert.

|Klasse|Zweck|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|Umschließt den `BSTR`-Typ, um hilfreiche Operatoren und Methoden bereitzustellen.|
|[_com_error](../cpp/com-error-class.md)|Definiert das Fehler Objekt, das von [_com_raise_error](../cpp/com-raise-error.md) bei den meisten Fehlern ausgelöst wird.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Kapselt com-Schnittstellen Zeiger und automatisiert die erforderlichen Aufrufe für `AddRef`, `Release`und `QueryInterface`.|
|[_variant_t](../cpp/variant-t-class.md)|Umschließt den `VARIANT`-Typ, um hilfreiche Operatoren und Methoden bereitzustellen.|

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[COM-Unterstützung des Compilers](../cpp/compiler-com-support.md)<br/>
[Globale COM-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)<br/>
[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)