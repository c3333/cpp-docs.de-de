---
title: Schwerwiegender Fehler C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 540febabc8f2947f11b58cf7eadee53d47f7bef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202877"
---
# <a name="fatal-error-c1852"></a>Schwerwiegender Fehler C1852

'Dateiname' ist keine gültige vorkompilierte Headerdatei.

Die Datei ist kein vorkompilierter Header.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Es wurde eine ungültige Datei mit **/Yu** oder **#pragma hdrstop**angegeben.

1. Wenn Sie keine andere Angabe vornehmen, nimmt der Compiler die Dateierweiterung PCH an.
