---
title: Mathematischer Fehler M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361971"
---
# <a name="math-error-m6108"></a>Mathematischer Fehler M6108

Quadratwurzel

Der Operand in einer Quadratwurzeloperation war negativ.

Das Programm wird mit dem Exit-Code 136 beendet.

> [!NOTE]
> Die `sqrt` Funktion in der C-Laufzeitbibliothek und der INtrinsischen Funktion **FORTRAN SQRT** erzeugen diesen Fehler nicht. Die `sqrt` C-Funktion überprüft das Argument vor dem Ausführen des Vorgangs und gibt einen Fehlerwert zurück, wenn der Operand negativ ist. Die FORTRAN **SQRT-Funktion** generiert anstelle dieses Fehlers den DOMAIN-Fehler [M6201.](../../error-messages/tool-errors/math-error-m6201.md)
