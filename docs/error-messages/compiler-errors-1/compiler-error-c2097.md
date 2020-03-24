---
title: Compilerfehler C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: cdb14aeef61d136a6992a05a72f382e589e88770
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207494"
---
# <a name="compiler-error-c2097"></a>Compilerfehler C2097

Ungültige Initialisierung

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Initialisierung einer Variablen mit einem nicht konstanten Wert.

1. Initialisierung einer kurzen Adresse mit einer langen Adresse.

1. Initialisierung einer lokalen Struktur, Union oder eines Arrays mit einem nicht konstanten Ausdruck beim Kompilieren mit **/Za**.

1. Initialisierung mit einem Ausdruck, der einen Komma Operator enthält.

1. Initialisierung mit einem Ausdruck, der weder konstant noch symbolisch ist.
