---
title: Schwerwiegender Fehler C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 9ea97bef16bebb8fc0e765ed708e54baee9a64de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220339"
---
# <a name="fatal-error-c1026"></a>Schwerwiegender Fehler C1026

Stapelüberlauf im Parser, Programm zu komplex

Der Speicherplatz, der zum Analysieren des Programms erforderlich ist, verursachte einen compilerstapel Überlauf.

Verringern Sie die Komplexität von Ausdrücken wie folgt:

- Verringern der Schachtelung in **`for`** -und- **`switch`** Anweisungen Fügen Sie tiefer geschachtelte-Anweisungen in separaten Funktionen ein.

- Aufteilen von langen Ausdrücken, die Komma Operatoren oder Funktionsaufrufe einschließen.
