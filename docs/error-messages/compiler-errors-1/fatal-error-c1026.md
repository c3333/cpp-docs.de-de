---
title: Schwerwiegender Fehler C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204652"
---
# <a name="fatal-error-c1026"></a>Schwerwiegender Fehler C1026

Stapelüberlauf im Parser, Programm zu komplex

Der Speicherplatz, der zum Analysieren des Programms erforderlich ist, verursachte einen compilerstapel Überlauf.

Verringern Sie die Komplexität von Ausdrücken wie folgt:

- Verringern der Schachtelung in `for`-und `switch`-Anweisungen Fügen Sie tiefer geschachtelte-Anweisungen in separaten Funktionen ein.

- Aufteilen von langen Ausdrücken, die Komma Operatoren oder Funktionsaufrufe einschließen.
