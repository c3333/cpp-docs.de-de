---
title: '#<a name="ifdef-and-ifndef-directives-cc--microsoft-docs"></a>Ifdef- und #ifndef-Direktiven (C/C++) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs: C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79be90d474e9cedce34273b719a360276517ef51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef- und #ifndef-Anweisungen (C/C++)
Die **#ifdef** und **#ifndef** Anweisungen führen Sie die gleiche Aufgabe wie die `#if` Richtlinie wird bei der Verwendung mit **definiert**( *Bezeichner* ).  
  
## <a name="syntax"></a>Syntax  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>Hinweise  
 Sie können die **#ifdef** und **#ifndef** -Direktiven an einer beliebigen Stelle `#if` kann verwendet werden. Die **#ifdef** *Bezeichner* Anweisung entspricht `#if 1` Wenn *Bezeichner* definiert wurde, und dies ist äquivalent zum `#if 0` beim *Bezeichner* wurde nicht definiert oder definiert wurde, mit der `#undef` Richtlinie. Diese Direktiven überprüfen lediglich, ob die mit `#define` definierten Bezeichner vorhanden sind, und nicht, ob Bezeichner vorhanden sind, die im C- oder C++-Quellcode deklariert werden.  
  
 Diese Anweisungen werden nur bereitgestellt, um die Kompatibilität mit früheren Versionen der Sprache zu gewährleisten. Die **definiert (** *Bezeichner* **)** konstanter Ausdruck für die `#if` Richtlinie wird bevorzugt.  
  
 Die **#ifndef** -Direktive überprüft das Gegenteil der durch geprüften Bedingung **#ifdef**. Wenn der Bezeichner nicht definiert wurde (oder ihre Definition mit `#undef` entfernt wurde), ist die Bedingung "true" (ungleich 0). Andernfalls ist die Bedingung "false" (0).  
  
 **Microsoft-spezifisch**  
  
 Die *Bezeichner* über die Befehlszeile mit der Option/d übergeben werden kann. Bis zu 30 Makros können mit /D angegeben werden.  
  
 Dies ist hilfreich, wenn überprüft werden soll, ob eine Definition vorhanden ist, da diese von der Befehlszeile übergeben werden kann. Zum Beispiel:  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **Ende Microsoft-spezifisch**  
  
## <a name="see-also"></a>Siehe auch  
 [Präprozessordirektiven](../preprocessor/preprocessor-directives.md)