---
title: Schwerwiegender Fehler C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204463"
---
# <a name="fatal-error-c1054"></a>Schwerwiegender Fehler C1054

Compilerlimit: zu tiefe Schachtelung von Initialisierern

Der Code überschreitet den Schachtelungs Grenzwert für Initialisierer (10-15 Ebenen, abhängig von der Kombination von Typen, die initialisiert werden).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Vereinfachen der zu initialisierenden Datentypen, um die Schachtelung zu reduzieren

1. Initialisieren Sie Variablen in separaten Anweisungen nach der Deklaration.
