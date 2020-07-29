---
title: Compilerfehler C2592
ms.date: 11/04/2016
f1_keywords:
- C2592
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
ms.openlocfilehash: bcb65addd95364d0755408a96c859182703768ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206834"
---
# <a name="compiler-error-c2592"></a>Compilerfehler C2592

„Klasse“: „base_class_2“ wird von „base_class_1“ geerbt und kann nicht erneut angegeben werden.

Sie können nur Basisklassen angeben, die nicht von anderen Basisklassen erben. In diesem Fall ist nur `base_class_1` in der Spezifikation von erforderlich, **`class`** da `base_class_1` bereits erbt `base_class_2` .
