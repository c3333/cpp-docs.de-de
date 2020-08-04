---
title: loop-Pragma
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 83dc8753392f9177f810746fce641437ed0ffec8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520628"
---
# <a name="loop-pragma"></a>loop-Pragma

Steuert, wie Schleifen Code von der automatischen Parallelisierung berücksichtigt werden soll, oder schließt eine Schleife von der Überlegung durch die automatische Vektorisierung aus.

## <a name="syntax"></a>Syntax

> **#pragma-Schleife (hint_parallel (** *n* **))**\
> **#pragma-Schleife (no_vector)**\
> **#pragma-Schleife (ivdep)**

### <a name="parameters"></a>Parameter

**hint_parallel (** *n* **)**\
Ein Hinweis für den Compiler, dass diese Schleife über *n* Threads parallelisiert werden soll, wobei *n* ein positives Ganzzahlliteral oder NULL ist. Wenn *n* 0 (null) ist, wird die maximale Anzahl von Threads zur Laufzeit verwendet. Es ist ein Hinweis für den Compiler, nicht für einen Befehl. Es gibt keine Garantie, dass die Schleife parallelisiert wird. Wenn die Schleife Daten Abhängigkeiten oder Strukturprobleme aufweist, wird Sie nicht parallelisiert. Sie wird z. b. nicht parallelisiert, wenn Sie in einem Skalar gespeichert wird, der über den Schleifen Text hinaus verwendet wird.

Der Compiler ignoriert diese Option, es sei denn, der [/QPAR](../build/reference/qpar-auto-parallelizer.md) -Compilerschalter ist angegeben.

**no_vector**\
Standardmäßig versucht die automatische Vektorisierung, alle Schleifen, die ausgewertet werden, zu vektorisieren. Geben Sie dieses Pragma an, um die automatische Vektorisierung für die folgende Schleife zu deaktivieren.

**ivdep**\
Ein Hinweis für den Compiler, dass Vektor Abhängigkeiten für diese Schleife ignoriert werden sollen.

## <a name="remarks"></a>Bemerkungen

Um das **Schleifen** -Pragma zu verwenden, platzieren Sie es unmittelbar vor, nicht in, einer Schleifen Definition. Das Pragma gilt für den Gültigkeitsbereich der Schleife, die darauf folgt. Sie können mehrere Pragmas in beliebiger Reihenfolge auf eine Schleife anwenden, aber Sie müssen jedes in einer separaten Pragmaanweisung angeben.

## <a name="see-also"></a>Siehe auch

[Automatische Parallelisierung und automatische Vektorisierung](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Pragma-Anweisungen und das __pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
