---
title: Compilerklassen für COM-Unterstützung
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: a8b0845fdfa96c1cb4b8b67e9d39169d9f4d3737
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189701"
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
