---
title: seed_seq-Klasse | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs: C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de741e8e36f6358b0b0f100eaa266336c0338ca2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="seedseq-class"></a>seed_seq-Klasse
Speichert einen Vektor ganzzahliger Werte ohne Vorzeichen, die einen zufällig festgelegten Startwert für ein Zufallszahlenmodul angeben können.  
  
## <a name="syntax"></a>Syntax  
```  
class seed_seq  
   {  
public:  
   // types  
   typedef unsigned int result_type;  

   // constructors  
   seed_seq();
   template <class T>  
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>  
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions  
   template <class RandomAccessIterator>  
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions  
   size_t size() const;
   template <class OutputIterator>  
      void param(OutputIterator dest) const;

   // no copy functions  
   seed_seq(const seed_seq&) = delete;  
   void operator=(const seed_seq&) = delete;  
   };  
```  
## <a name="types"></a>Typen  
 `typedef unsigned int result_type;`   
Der Typ der Elemente der seed-Sequenz. Eine 32-Bit-Ganzzahl ohne Vorzeichen  
  
## <a name="constructors"></a>Konstruktoren  
 `seed_seq();`   
Standardkonstruktor, initialisiert für eine leere interne Sequenz.  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
Verwendet `initlist`, um die interne Sequenz festzulegen.                   
`T` muss ein Ganzzahltyp sein.  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
Initialisiert die interne Sequenz mithilfe aller Elemente im bereitgestellten Eingabeiteratorbereich.                  
`iterator_traits<InputIterator>::value_type` muss ein Ganzzahltyp sein.  
  
## <a name="members"></a>Mitglieder  
  
### <a name="generating-functions"></a>Erstellen von Funktionen  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);`   
Trägt die Elemente der bereitgestellten Sequenz mithilfe eines internen Algorithmus ein. Dieser Algorithmus wird von der internen Sequenz beeinflusst, mit der `seed_seq` initialisiert wurde.                          
Bleibt untätig, wenn `begin == end` ist.  
  
### <a name="property-functions"></a>Eigenschaftenfunktionen  
 `size_t size() const;`   
Gibt die Anzahl von Elementen in der `seed_seq` zurück.  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
Kopiert die interne Sequenz in den Eingabeiterator `dest`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel führt die drei Konstruktoren aus und erzeugt eine Ausgabe aus den resultierenden `seed_seq`-Instanzen, wenn sie einem Array zugeordnet sind. Ein Beispiel, das `seed_seq` mit einem Zufallszahlengenerator verwendet, finden Sie unter [\<random>](../standard-library/random.md).  
  
```cpp  
#include <iostream>  
#include <random>  
#include <string>  
#include <array>  
  
using namespace std;  
  
void test(const seed_seq& sseq) {  
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;  
  
    cout << "seed_seq::param(): ";  
    ostream_iterator<unsigned int> out(cout, " ");  
    sseq.param(out);  
    cout << endl;  
  
    cout << "Generating a sequence of 5 elements into an array: " << endl;  
    array<unsigned int, 5> seq;  
    sseq.generate(seq.begin(), seq.end());  
    for (unsigned x : seq) { cout << x << endl; }  
}  
  
int main()  
{  
    seed_seq seed1;  
    test(seed1);  
  
    seed_seq seed2 = { 1701, 1729, 1791 };  
    test(seed2);  
  
    string sstr = "A B C D"; // seed string  
    seed_seq seed3(sstr.begin(), sstr.end());  
    test(seed3);  
}  
```  
  
```Output  
seed_seq::size(): 0  
seed_seq::param():  
Generating a sequence of 5 elements into an array:  
505382999  
163489202  
3932644188  
763126080  
73937346  
  
seed_seq::size(): 3  
seed_seq::param(): 1701 1729 1791  
Generating a sequence of 5 elements into an array:  
1730669648  
1954224479  
2809786021  
1172893117  
2393473414  
  
seed_seq::size(): 7  
seed_seq::param(): 65 32 66 32 67 32 68  
Generating a sequence of 5 elements into an array:  
3139879222  
3775111734  
1084804564  
2485037668  
1985355432  
```  
  
## <a name="remarks"></a>Hinweise  
 Memberfunktionen dieser Klasse lösen keine Ausnahmen aus.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<random>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Siehe auch  
 [\<random>](../standard-library/random.md)

