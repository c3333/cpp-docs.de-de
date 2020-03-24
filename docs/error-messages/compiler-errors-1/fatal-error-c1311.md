---
title: Schwerwiegender Fehler C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203267"
---
# <a name="fatal-error-c1311"></a>Schwerwiegender Fehler C1311

Das COFF-Format kann "var" mit den Nummern Byte (n) einer Adresse nicht statisch initialisieren.

Eine Adresse, deren Wert zum Zeitpunkt der Kompilierung nicht bekannt ist, kann nicht statisch einer Variablen zugewiesen werden, deren Typ eine Speichergröße von weniger als vier Bytes hat.

Dieser Fehler kann bei Code auftreten, der andernfalls gültig C++ist.

Das folgende Beispiel zeigt eine Bedingung, die C1311 verursachen kann.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
