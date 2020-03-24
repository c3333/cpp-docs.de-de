---
title: Ausdrucksauswertungsfehler CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195499"
---
# <a name="expression-evaluator-error-cxx0036"></a>Ausdrucksauswertungsfehler CXX0036

Ungültiger Kontext {...} specification

Diese Meldung kann von einem von mehreren Fehlern bei der Verwendung des Kontext Operators ( **{}** ) generiert werden.

- Die Syntax des Kontext Operators ( **{}** ) wurde falsch angegeben.

   Die Syntax des Kontext Operators lautet wie folgt:

     {*Function*,*Module*,*dll*} *Ausdruck*

   Gibt den Kontext des *Ausdrucks*an. Der Kontext Operator hat die gleiche Rangfolge und Verwendung wie eine Typumwandlung.

   Nachfolgende Kommas können ausgelassen werden. Wenn eine der *Funktionen*, *Module*oder *dll* ein literales Komma enthält, müssen Sie den gesamten Namen in Klammern einschließen.

- Der Funktionsname wurde falsch geschrieben oder ist nicht im angegebenen Modul oder in der Dynamic Link Library vorhanden.

   Da C eine Sprache mit Berücksichtigung von Groß-/Kleinschreibung ist, muss die *Funktion* in genau dem Fall angegeben werden, wie Sie in der Quelle definiert ist.

- Das Modul oder die dll konnte nicht gefunden werden.

   Überprüfen Sie den vollständigen Pfadnamen des angegebenen Moduls oder der dll.

Dieser Fehler ist mit CAN0036 identisch.
