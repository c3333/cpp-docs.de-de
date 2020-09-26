---
title: 'Visual C++: Neuerungen von 2003 bis 2015'
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: eb76e5455f053717859d0ac571b9d1110d11c33b
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352634"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++: Neuerungen von 2003 bis 2015

Auf dieser Seite werden alle Neuerungen für sämtliche Versionen von Visual C++ zusammengefasst – angefangen bei Visual Studio 2003 bis hin zu 2015. Diese Informationen werden bereitgestellt, um Sie zu unterstützen, falls Sie ein Upgrade von früheren Versionen von Visual Studio durchführen möchten.

> [!NOTE]
> Informationen zur aktuellen Version von Visual Studio finden Sie unter [What's new for Visual C++ in Visual Studio (Neuerungen bei Visual C++ in Visual Studio)](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) und [Conformance Improvements in Visual C++ in Visual Studio (Verbesserungen bei der Übereinstimmung mit Visual C++-Standards in Visual Studio)](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Neuerungen bei C++ in Visual Studio 2015

In Visual Studio 2015 und höher können sich fortlaufende Verbesserungen der Konformität des Compilers mit Standards möglicherweise darauf auswirken, wie der Compiler den vorhandenen Quellcode versteht. In diesem Fall treten während Ihres Builds ggf. neue oder andere Fehler oder sogar Verhaltensunterschiede im Code auf, für den zuvor Builds erstellt wurden und die Ausführung ordnungsgemäß schien.

Glücklicherweise haben diese Unterschiede wenig oder keinen Einfluss auf den Großteil Ihres Quellcodes. Sollten Quellcode- oder andere Änderungen zum Ausgleichen dieser Unterschiede erforderlich sein, sind Korrekturen in der Regel klein und einfach. Wir haben zahlreiche Beispiele für zuvor zulässigen Quellcode, die möglicherweise geändert werden müssen *(vorher)*, und die Updates zur Korrektur *(nachher)* hinzugefügt.

Obwohl diese Unterschiede sich auf Ihren Quellcode oder andere Buildartefakte auswirken können, wirken sie sich nicht auf die Binärkompatibilität zwischen Updates für Visual C++-Versionen aus. Eine schwerwiegendere Art der Änderung, die *bedeutende Änderung*, kann die Binärkompatibilität beeinträchtigen. Doch diese Arten von Unterbrechung der Binärkompatibilität treten nur zwischen Hauptversionen von Visual C++ auf. Beispielsweise zwischen Visual C++ 2013 und Visual C++ 2015. Informationen zu bedeutenden Änderungen, die zwischen Visual C++ 2013 und Visual C++ 2015 vorgenommen wurden, finden Sie unter [Änderungsverlauf von Visual C++ von 2003 bis 2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Verbesserungen bei der Übereinstimmung mit Standards in Visual Studio 2015](#VS_RTM)

- [Verbesserungen bei der Übereinstimmung mit Standards in Visual Studio 2015 Update 1](#VS_Update1)

- [Verbesserungen bei der Übereinstimmung mit Standards in Visual Studio 2015 Update 2](#VS_Update2)

- [Verbesserungen bei der Übereinstimmung mit Standards in Visual Studio 2015 Update 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a> Verbesserungen der Konformität in Visual Studio 2015

- **/Zc:forScope-Option**

   Die Compileroption `/Zc:forScope-` ist veraltet und wird in einem der nächsten Releases entfernt.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Die Option wurde in der Regel für nicht dem Standard entsprechenden Code verwendet, der Schleifenvariablen gemäß dem Standard nach dem Punkt verwendet, an dem diese den Gültigkeitsbereich verlassen sollten. Dies war nur dann erforderlich, wenn die Kompilierung mit der `/Za`-Option erfolgte. Ohne die `/Za`-Option war eine Schleifenvariable nach dem Ende der Schleife immer zulässig. Wenn die Einhaltung von Standards keine Rolle spielt (z.B. wenn der Code nicht auf andere Compiler übertragbar ist), können Sie die `/Za`-Option deaktivieren (oder die Eigenschaft **Spracherweiterungen deaktivieren** auf **Nein** festlegen). Wenn Sie übertragbaren Code schreiben möchten, der den Standards entspricht, sollten Sie den Code umschreiben, indem Sie die Deklaration der Variablen an eine Stelle außerhalb der Schleifen verschieben.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **Zg-Compileroption**

   Die `/Zg`-Compileroption (Funktionsprototypen generieren) ist nicht mehr verfügbar. Diese Compileroption wurde zuvor als veraltet markiert.

- Sie können Komponententests nicht mehr mit C++/CLI über die Befehlszeile mit mstest.exe ausführen. Verwenden Sie stattdessen „vstest.console.exe“.

- **Schlüsselwort mutable**

   Der **`mutable`** Speicherklassenspezifizierer ist an Orten, an denen er zuvor ohne Fehler kompiliert wurde, nicht mehr zulässig. Der Compiler generiert nun den Fehler C2071 (Ungültige Speicherklasse). Gemäß dem Standard kann der mutable-Spezifizierer nur auf Namen von Klassendatenmembern angewendet werden und kann nicht auf als konstant oder statisch deklarierte Namen sowie nicht auf Verweismember angewendet werden.

   Beachten Sie z. B. folgenden Code:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   In früheren Versionen des Microsoft Visual C++-Compilers war dies zulässig, jetzt generiert der Compiler jedoch den folgenden Fehler:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Entfernen Sie einfach das redundante Schlüsselwort, um den Fehler zu beheben **`mutable`** .

- **char_16_t und char32_t**

   Sie können nicht mehr **`char16_t`** oder **`char32_t`** als Aliase in einer typedef verwenden, da diese Typen nun als integriert behandelt werden. Es war üblich, dass Benutzer und Bibliotheks Autoren und **`char16_t`** **`char32_t`** als Aliase von `uint16_t` `uint32_t` bzw. definieren.

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   Um den Code zu aktualisieren, entfernen Sie die **`typedef`** Deklarationen und benennen alle anderen Bezeichner um, die mit diesen Namen in Konflikt stehen.

- **Nichttyp-Vorlagenparameter**

   Bestimmter Code mit Nichttyp-Vorlagenparametern wird auf Typkompatibilität korrekt geprüft, wenn Sie explizite Vorlagenargumente bereitstellen. Der folgende Code wurde z. B. ohne Fehler in früheren Versionen von Visual C++ kompiliert.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   Der aktuelle Compiler generiert ordnungsgemäß einen Fehler, da der Typ des Vorlagenparameters nicht mit dem Vorlagenargument übereinstimmt (der Parameter ist ein Zeiger auf einen konstanten Member, die f-Funktion ist jedoch nicht konstant):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Stellen Sie zum Beheben dieses Fehlers im Code sicher, dass der Typ des verwendeten Vorlagenarguments mit dem deklarierten Typ des Vorlagenparameters übereinstimmt.

- **`__declspec(align)`**

   Der Compiler lässt `__declspec(align)` in Funktionen nicht mehr zu. Dies wurde bisher ignoriert, nun wird jedoch ein Compilerfehler generiert.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Entfernen Sie zum Beheben dieses Problems `__declspec(align)` aus der Funktionsdeklaration. Da dies keine Auswirkungen hatte, ändert sich durch das Entfernen nichts.

- **Ausnahmebehandlung**

   Es gibt eine Reihe von Änderungen bei der Ausnahmebehandlung. Ausnahmeobjekte müssen kopiert oder verschoben werden können. Der folgende Code wird zwar in Visual Studio 2013 kompiliert, aber nicht in Visual Studio 2015:

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Das Problem besteht darin, dass der Kopierkonstruktor privat ist. Somit kann das Objekt nicht während des normalen Betriebs der Ausnahmebehandlung kopiert werden. Dasselbe gilt, wenn der Kopierkonstruktor deklariert wird **`explicit`** .

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Stellen Sie zum Aktualisieren des Codes sicher, dass der Kopierkonstruktor für Ihr Ausnahme Objekt öffentlich und nicht als gekennzeichnet ist **`explicit`** .

   Beim Abfangen einer Ausnahme nach Wert muss das Ausnahmeobjekt ebenfalls kopiert werden können. Der folgende Code wird zwar in Visual Studio 2013 kompiliert, aber nicht in Visual Studio 2015:

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   Sie können dieses Problem beheben, indem Sie den Parametertyp für **`catch`** auf einen Verweis ändern.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Zeichenfolgenliterale gefolgt von Makros**

   Der Compiler unterstützt nun benutzerdefinierte Literale. Folglich werden Zeichenfolgenliterale, auf die Makros ohne dazwischenliegende Leerzeichen folgen, als benutzerdefinierte Literale interpretiert, was zu Fehlern oder unerwarteten Ergebnissen führen kann. In vorherigen Compilern wurde der beispielsweise der folgende Code erfolgreich kompiliert:

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   Der Compiler interpretierte dies als ein Zeichenfolgenliteral „Hello“ gefolgt von einem Makro, das um „there“ erweitert wird, und führte die zwei Zeichenfolgenliterale zu einer verketteten Zeichenfolge zusammen. In Visual Studio 2015 interpretiert der Compiler dies als ein benutzerdefiniertes Literal. Da kein entsprechendes benutzerdefiniertes _x-Literal definiert ist, wird jedoch ein Fehler generiert.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Fügen Sie zur Behebung dieses Problems ein Leerzeichen zwischen das Zeichenfolgenliteral und das Makro ein.

- **Angrenzende Zeichenfolgenliterale**

   Auf ähnliche Weise wurden angrenzende Zeichenfolgenliterale ohne Leerzeichen aufgrund von zugehörigen Änderungen in der Zeichenfolgenanalyse als eine verkettete Zeichenfolge in den vorherigen Versionen von Visual C++ interpretiert. In Visual Studio 2015 müssen Sie ein Leerzeichen zwischen den beiden Zeichenfolgen hinzufügen. Der folgende Code muss z. B. geändert werden:

   ```cpp
    char * str = "abc""def";
   ```

   Fügen Sie einfach ein Leerzeichen zwischen den beiden Zeichenfolgen hinzu.

   ```cpp
    char * str = "abc" "def";
   ```

- **Platzierungsoperatoren „new“ und „delete“**

   Der Operator hat eine Änderung vorgenommen, um eine **`delete`** Übereinstimmung mit dem c++ 14-Standard zu erzielen. Detaillierte Informationen zur Standardänderung finden Sie unter [Aufhebung der Zuordnung mit C++-Größeninformationen](https://isocpp.org/files/papers/n3778.html). Die Änderungen fügen eine Form des globalen **`delete`** Operators hinzu, der einen size-Parameter annimmt. Wenn Sie zuvor einen Operator **`delete`** mit derselben Signatur verwendet haben (um einem **Platzierungs Operator new** zu entsprechen), erhalten Sie einen Compilerfehler (nämlich c2956, der an dem Punkt auftritt, an dem die **Platzierung New** verwendet wird, da dies die Position im Code ist, an der der Compiler versucht, einen entsprechenden übereinstimmenden **`delete`** Operator zu identifizieren). Breaking Change

   Bei der Funktion `void operator delete(void *, size_t)` hat es sich um einen **delete**-Platzierungsoperator gehandelt, der der Funktion `void * operator new(size_t, size_t)` des Platzierungsoperators **new** in C++11 entspricht. Bei der Aufhebung der Zuordnung von c++ 14 entspricht diese **`delete`** Funktion nun der *üblichen Zuordnungs Funktion* (globaler **`delete`** Operator). Der Standard erfordert, dass das Programm nicht ordnungsgemäß formatiert ist, wenn die Verwendung einer **Platzierungs neuen Platzierung** eine entsprechende **`delete`** Funktion sucht und eine übliche Funktion zum Aufheben der Zuordnung findet.

   Nehmen Sie beispielsweise an, dass Ihr Code sowohl eine **Platzierung New** als auch eine **Platzierungs Löschung**definiert:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   Das Problem tritt aufgrund der Entsprechung in den Funktions Signaturen zwischen einem von Ihnen definierten **Platzierungs Lösch** Operator und dem neuen globalen Größen **`delete`** Operator auf. Stellen Sie sich vor, ob Sie einen anderen Typ als `size_t` für die **Platzierung neuer** -und- **`delete`** Operatoren verwenden können.  Beachten Sie, dass der Typ der vom `size_t` **`typedef`** Compiler abhängigen ist, d **`typedef`** . h. ein für **`unsigned int`** in Visual C++. Eine gute Lösung hierfür stellt die Verwendung eines enumerierten Typs wie die des folgenden dar:

   ```cpp
    enum class my_type : size_t {};
   ```

   Ändern Sie dann die Definition der Platzierung, **`new`** und **`delete`** verwenden Sie diesen Typ als zweites Argument anstelle von `size_t` . Sie müssen auch die Aufrufe von **Platzierung New** aktualisieren, um den neuen Typ zu übergeben (z. b. mithilfe von `static_cast<my_type>` , um den ganzzahligen Wert zu konvertieren) und die Definition von und aktualisieren, **`new`** **`delete`** um Sie wieder in den ganzzahligen Typ umzuwandeln. Hierfür müssen Sie keinen verwenden **`enum`** . ein Klassentyp mit einem `size_t` Member würde ebenfalls funktionieren.

   Eine alternative Lösung besteht darin, dass Sie möglicherweise die **Platzierung der neuen Platzierung** vollständig ausschließen können. Wenn Ihr Code die **Platzierung New** verwendet, um einen Speicherpool zu implementieren, bei dem das Platzierungs Argument die Größe des zugeordneten oder gelöschten Objekts ist, kann das Feature zum Aufheben der Speicher Belegung geeignet sein, um den eigenen benutzerdefinierten Speicherpool Code zu ersetzen, und Sie können die Platzierungsfunktionen entfernen und einfach einen eigenen Operator mit zwei Argumenten **`delete`** anstelle der Platzierungsfunktionen verwenden.

   Wenn Sie Ihren Code nicht sofort aktualisieren möchten, können Sie mit der Compileroption `/Zc:sizedDealloc-` das alte Verhalten wiederherstellen. Wenn Sie diese Option verwenden, sind die **`delete`** Funktionen mit zwei Argumenten nicht vorhanden und führen nicht zu einem Konflikt mit dem **Platzierungs Lösch** Operator.

- **Union-Datenmember**

   Union-Datenmember dürfen über keine Verweistypen verfügen. Der folgende Code kompiliert zwar in Visual Studio 2013 erfolgreich, aber erzeugt in Visual Studio 2015 einen Fehler.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   Der oben genannte Code geniert die folgenden Fehler:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Ändern Sie zur Behebung dieses Fehlers die Verweistypen in einen Zeiger oder einen Wert. Für die Änderung des Typs in einen Zeiger sind Änderungen im Code erforderlich, der das Union-Feld verwendet. Durch die Änderung des Codes in einen Wert werden die in der Union gespeicherten Daten geändert, was Auswirkungen auf andere Felder hat, da Felder in Uniontypen den gleichen Speicher gemeinsam verwenden. Je nach Wertgröße kann dies ggf. auch die Größe der Union ändern.

- **Anonyme Unions**

   weisen nun eine höhere Standardkonformität auf. Frühere Versionen des Compilers haben einen expliziten Konstruktor und Destruktor für anonyme Unions generiert. Diese sind in Visual Studio 2015 nicht mehr vorhanden.

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   Der oben genannte Code geniert in Visual Studio 2015 den folgenden Fehler:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Geben Sie zur Behebung dieses Fehlers eigene Definitionen des Konstruktors und/oder des Destruktors an.

   ```cpp
    struct S {
       // Provide a default constructor by adding an empty function body.
       S() {}
    };

    union {
       struct {
          S s;
       };
    } u;
   ```

- **Unions mit anonymen Strukturen**

   Zur Einhaltung des Standards wurde das Laufzeitverhalten für Member anonymer Strukturen in Unions geändert. Der Konstruktor für anonyme Strukturmember in einer Union wird nicht mehr implizit aufgerufen, wenn eine solche Union erstellt wird. Der Destruktor für anonyme Strukturmember in einer Union wird nicht mehr implizit aufgerufen, wenn die Union den Gültigkeitsbereich verlässt. Betrachten Sie den folgenden Code, in dem eine Union U eine anonyme Struktur mit einem Member enthält, der die Struktur S mit einem Destruktor darstellt.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Der Konstruktor für S wird in Visual Studio 2013 immer dann aufgerufen, wenn die Union erstellt wird, und der Destruktor für S wird immer dann aufgerufen, wenn der Stapel für Funktion f bereinigt wird. In Visual Studio 2015 werden jedoch weder der Konstruktor noch der Destruktor aufgerufen. Der Compiler gibt eine Warnung zu dieser Verhaltensänderung aus.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Benennen Sie zum Wiederherstellen des ursprünglichen Verhaltens die anonyme Struktur. Das Laufzeitverhalten von nicht anonymen Strukturen ist von der Compilerversion unabhängig.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Verschieben Sie alternativ den Konstruktor- und Destruktorcode in die neuen Funktionen, und fügen Sie diesen Funktionen aus der Konstruktor- und Destruktorunion Aufrufe hinzu.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **Vorlagenauflösung**

   Es wurden Änderungen an der Namensauflösung für Vorlagen vorgenommen. Bei Berücksichtigung der Kandidaten für eine Namensauflösung können potenzielle Namen in C++ ggf. eine ungültige Vorlageninstanziierung erzeugen. Diese ungültigen Instanziierungen generieren in der Regel keine Comilerfehler – das SFINAE-Prinzip (Ersetzungsfehler sind keine Fehler).

   Wenn der Compiler jetzt von SFINAE zum Instanziieren der Spezialisierung einer Klassenvorlage aufgefordert wird, handelt es sich bei allen während dieses Prozesses aufgetretenen Fehler um Compilerfehler. In früheren Versionen hat der Compiler diese Fehler ignoriert. Beachten Sie z. B. folgenden Code:

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   Beim Kompilieren mit dem aktuellen Compiler tritt der folgende Fehler auf:

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   Dies liegt daran, dass die D-Klasse zum Zeitpunkt des ersten Aufrufs von is_base_of noch nicht definiert war.

   In diesem Fall besteht die Lösung darin, diese Typmerkmale nicht zu verwenden, bis die Klasse definiert wurde. Wenn Sie die Definitionen von B und D an den Anfang der Codedatei verschieben, wird der Fehler behoben. Überprüfen Sie, wenn sich die Definitionen in Headerdateien befinden, die Reihenfolge der Include-Anweisungen für die Headerdateien, um sicherzustellen, dass alle Klassendefinitionen kompiliert werden, bevor die problematischen Vorlagen verwendet werden.

- **Kopierkonstruktoren**

   Sowohl in Visual Studio 2013 als auch in Visual Studio 2015 generiert der Compiler einen Kopierkonstruktor für eine Klasse, die über einen benutzerdefinierten Bewegungskonstruktor verfügt, jedoch über keinen benutzerdefinierten Kopierkonstruktor. In Dev14 wird dieser implizit generierte Kopierkonstruktor ebenfalls als „= delete“ gekennzeichnet.

### <a name="conformance-improvements-in-visual-studio-2015-update-1"></a><a name="VS_Update1"></a> Verbesserungen der Konformität in Visual Studio 2015 Update 1

- **Private virtuelle Basisklassen und indirekte Vererbung**

   In früheren Versionen des Compilers war es abgeleiteten Klassen möglich, Member ihrer *indirekt abgeleiteten* `private virtual` Basisklassen aufzurufen. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2280 als Ergebnis aus.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   Beispiel (vorher)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   Beispiel (nachher)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  \- oder -

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Überladener Operator „new“ und „delete“**

   In früheren Versionen des Compilers konnte ein **new**-Platzierungsoperator, der kein Member war, und ein **delete**-Platzierungsoperator, der kein Member war, statisch deklariert werden und in anderen Namespaces als dem globalen deklariert werden.  Dieses alte Verhalten hat das Risiko verursacht, dass das Programm nicht die **`new`** Implementierung des Operators oder des **`delete`** Operators aufruft, die der Programmierer beabsichtigt hat, was zu einem stillen ungültigen Laufzeitverhalten führt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2323 als Ergebnis aus.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   Beispiel (vorher)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   Beispiel (nachher)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

   Außerdem, auch wenn dazu keine spezifische Diagnose ausgegeben wird, wird ein Inlineoperator „new“ als nicht wohlgeformt angesehen.

- **Aufrufen von „operator *type*()“ (Benutzerdefinierter Wechsel für Nichtklassentypen)** Frühere Versionen des Compilers haben den Aufruf von „operator *type*()“ für Nichtklassentypen zugelassen und den Aufruf still ignoriert. Durch dieses alte Verhalten entstand die Gefahr der stummen Erzeugung von ungültigem Code, was zu unvorhersehbarem Laufzeitverhalten führt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2228 als Ergebnis aus.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   Beispiel (vorher)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   Beispiel (nachher)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **Redundanter Typname in ausführlichen Typspezifizierern**  In früheren Versionen des Compilers waren **`typename`** in einem ausführlichen Typspezifizierer zulässig. in dieser Weise geschriebener Code ist semantisch falsch. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C3406 als Ergebnis aus.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   Beispiel (vorher)

   ```cpp
    template <typename class T>
    class container;
   ```

   Beispiel (nachher)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **Typableitung von Arrays aus einer Initialisiererliste** In früheren Versionen des Compilers wurde die Typableitung von Arrays aus einer Initialisiererliste nicht unterstützt. Der Compiler unterstützt jetzt diese Form der Typableitung. Das kann zur Folge haben, dass Aufrufe an Funktionsvorlagen mithilfe von Initialisiererlisten jetzt möglicherweise nicht mehr eindeutig sind, oder es wird eine andere Überladung gewählt als in früheren Versionen des Compilers. Um diese Probleme zu beheben, muss das Programm jetzt die vom Programmierer beabsichtigte Überladung explizit angeben.

   Wenn dieses neue Verhalten dazu führt, dass bei der Überladungsauflösung ein weitere Kandidat als ebenso gut wie der historische Kandidat angesehen wird, ist der Aufruf nicht mehr eindeutig, und der Compiler gibt den Compilerfehler C2668 als Ergebnis aus.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion (vorher)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion (nachher)

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   Wenn dieses neue Verhalten bewirkt, dass ein anderer Kandidat bei der Überladungsauflösung als bessere Übereinstimmung als der historische Kandidat angesehen wird, wird der Aufruf unzweideutig zum neuen Kandidaten aufgelöst, was eine Änderung im Verhalten des Programms bewirkt, das vermutlich von den Absichten des Programmierers abweicht.

   Beispiel 2: Änderung an der Überladungsauflösung (vorher)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   Beispiel 2: Änderung an der Überladungsauflösung (nachher)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **Wiederherstellung von Warnungen der switch-Anweisung**

   Von einer früheren Version des Compilers wurden bereits vorhandene Warnungen im Zusammenhang mit- **`switch`** Anweisungen entfernt; diese Warnungen wurden jetzt wieder hergestellt. Der Compiler gibt jetzt die wiederhergestellten Warnungen aus, und Warnungen, die sich auf bestimmte Fälle (einschließlich des Standardfalls) bezogen, werden jetzt in der Zeile ausgegeben, die den Verstoß enthält, statt in der letzten Zeile der switch-Anweisung. Die Ausgabe dieser Warnungen in anderen Zeilen als bisher kann zur Folge haben, dass Warnungen, die früher mithilfe von `#pragma warning(disable:####)` unterdrückt wurden, möglicherweise nicht mehr wie beabsichtigt unterdrückt werden. Um diese Warnungen wie beabsichtigt zu unterdrücken, kann es erforderlich sein, die `#pragma warning(disable:####)` -Anweisung in eine Zeile oberhalb des ersten möglichen Verstoßes zu verschieben. Die wiederhergestellten Warnungen folgen hier:

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   Beispiel für C4063 (vorher)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   Beispiel für C4063 (nachher)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   Beispiele für die anderen wiederhergestellten Warnungen stehen in deren Dokumentation zur Verfügung.

- **#include: Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers haben die Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen von  `#include` -Anweisungen nicht erkannt. Bei in dieser Weise erstelltem Code wird normalerweise die Absicht verfolgt, Header einzuschließen, die sich außerhalb des Projekts befinden, und dazu werden fälschlicherweise projektrelative Pfade verwendet. Bei diesem alten Verhalten ergab sich die Gefahr, dass das Programm möglicherweise mit Einschluss einer anderen als der vom Programmierer beabsichtigten Quelldatei compiliert wurde oder dass diese relativen Pfade nicht auf andere Buildumgebungen portiert werden konnten. Der Compiler erkennt jetzt in dieser Weise erstellten Code und benachrichtigt den Programmierer mit der optionalen Compilerwarnung C4464, sofern diese aktiviert ist.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   Beispiel (vorher)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   Beispiel (nachher)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   Darüber hinaus empfehlen wir, auch wenn der Compiler dazu keine spezifischen Diagnosemeldungen ausgibt, den Bezeichner ".." für das übergeordnete Verzeichnis beim Angeben der Includeverzeichnisse des Projekts nicht zu verwenden.

- **#pragma optimize() erstreckt sich über das Ende der Headerdatei hinaus** (betrifft nur `/Wall` `/WX`)

   In früheren Versionen wurden Änderungen an den Optimierungseinstellungen nicht erkannt, die zum Escapen einer in einer Übersetzungseinheit eingeschlossenen Headerddatei dienen. Der Compiler erkennt jetzt in dieser Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C4426 von der Position des `#include`-Verstoßes in Kenntnis, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn die Änderungen im Konflikt mit den Optimierungseinstellungen stehen, die durch die Befehlszeilenargumente für den Compiler festgelegt wurden.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   Beispiel (vorher)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   Beispiel (nachher)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **Nicht übereinstimmende Festlegung von „#pragma warning(push)“** und **#pragma warning(pop)** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers konnten keine `#pragma warning(push)`-Statusänderungen erkennen, die in Kombination mit `#pragma warning(pop)`-Statusänderungen in einer anderen Quelldatei auftraten, was selten beabsichtigt ist. Dieses alte Verhalten brachte die Gefahr mit sich, dass das Programm mit anderen Warnungseinstellungen als den vom Programmierer vorgesehenen kompiliert wurde, was möglicherweise zu einem schlechten Laufzeitverhalten führt. Der Compiler erkennt jetzt auf diese Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C5031 von der Position der `#pragma warning(pop)`-Übereinstimmung in Kenntnis, sofern diese aktiviert ist. Diese Warnung enthält einen Hinweis, der auf den Speicherort der entsprechenden `#pragma warning(push)`-Warnung verweist.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   Beispiel (vorher)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   Beispiel (nachher)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   Wenngleich ungewöhnlich, wird Code mitunter absichtlich auf diese Weise geschrieben. Auf diese Weise erstellter Code ist empfindlich gegenüber Änderungen an der `#include`-Reihenfolge. Wir empfehlen, dass Quellcodedateien den Warnungsstatus nach Möglichkeit eigenständig verwalten sollten.

- **Nicht zugeordnete „#pragma warning“ (push)** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers haben nicht zugeordnete `#pragma warning(push)` -Statusänderungen am Ende einer Übersetzungseinheit nicht erkannt. Der Compiler erkennt jetzt auf diese Weise erstellten Code und informiert den Programmierer mit der optionalen Compilerwarnung C5032 über die Position der fehlenden `#pragma warning(push)`-Übereinstimmung, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn in der Übersetzungseinheit keine Kompilierfehler auftreten.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   Beispiel (vorher)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   Beispiel (nachher)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **Möglicherweise werden weitere Warnungen als Folge der verbesserten Statusnachverfolgung bei „#pragma warning“ angezeigt**

   In früheren Versionen des Compilers wurden Statusänderungen bei `#pragma warning` nicht hinreichend gut nachverfolgt, um alle beabsichtigten Warnungen auszugeben. Durch dieses Verhalten bestand die Gefahr, dass bestimmte Warnungen unter anderen als den vom Programmierer beabsichtigten Umständen effektiv unterdrückt wurden. Die Nachverfolgung des Status von `#pragma warning` erfolgt nun auf stabilere Weise – insbesondere im Zusammenhang mit `#pragma warning`-Statusänderungen in Vorlagen – und gibt optional die neuen Warnungen C5031 und C5032 aus, die den Programmierer bei der Suche nach unbeabsichtigter Verwendung von `#pragma warning(push)` und `#pragma warning(pop)` unterstützen sollen.

   Als Ergebnis der verbesserten Nachverfolgung des Status von `#pragma warning` können jetzt Warnungen ausgegeben werden, die früher fälschlicherweise unterdrückt wurden oder mit falsch identifizierten Problemen zusammenhingen.

- **Verbesserte Erkennung von unerreichbarem Code**

   Änderungen an der C++-Standardbibliothek und eine im Vergleich mit früheren Versionen des Compilers verbesserte Möglichkeit zur Inlineausführung von Funktionsaufrufen ermöglichen dem Compiler jetzt unter Umständen den Nachweis, dass bestimmter Code unerreichbar ist. Dieses neue Verhalten kann zu neuen und häufiger ausgegebenen Instanzen von Warnung C4720 führen.

   ```Output
    warning C4720: unreachable code
   ```

   In vielen Fällen wird diese Warnung nur beim Kompilieren mit aktivierten Optimierungen ausgegeben, da bei den Optimierungen mehr Funktionsaufrufe inline erfolgen, redundanter Code eliminiert wird oder auf andere Weise die Möglichkeit geschaffen wird, bestimmten Code als unerreichbar zu erkennen. Wir haben festgestellt, dass neue Instanzen von Warning C4720 häufig in **try/catch-** Blöcken aufgetreten sind, insbesondere in Bezug auf die Verwendung von [Std:: Find](../standard-library/algorithm-functions.md#find).

   Beispiel (vorher)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   Beispiel (nachher)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="conformance-improvements-in-visual-studio-2015-update-2"></a><a name="VS_Update2"></a> Verbesserungen der Konformität in Visual Studio 2015 Update 2

- **Zusätzliche Warnungen und Fehler können als Ergebnis der Teilunterstützung für den Ausdruck SFINAE ausgegeben werden**

   Frühere Versionen des Compilers haben bestimmte Arten von Ausdrücken innerhalb von Bezeichners nicht analysiert **`decltype`** , weil der Ausdruck sfinae nicht unterstützt wird. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler analysiert diese Ausdrücke jetzt und hat aufgrund kontinuierlicher Konformitätsverbesserungen eine Teilunterstützung für den Ausdruck SFINAE. Daher gibt der Compiler jetzt Warnungen und Fehler aus, die er in Ausdrücken findet, die von früheren Versionen des Compilers nicht analysiert werden.

   Wenn dieses neue Verhalten einen- **`decltype`** Ausdruck analysiert, der einen Typ enthält, der noch nicht deklariert wurde, gibt der Compiler den Compilerfehler C2039 als Ergebnis aus.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Beispiel 1: Verwendung eines nicht deklarierten Typs (vorher)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   Beispiel 1 (nachher)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   Wenn dieses neue Verhalten einen- **`decltype`** Ausdruck analysiert, dem eine erforderliche Verwendung des- **`typename`** Schlüssel Worts fehlt, um anzugeben, dass ein abhängiger Name ein-Typ ist, gibt der Compiler die Compilerwarnung C4346 in Verbindung mit dem Compilerfehler C2923 aus.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Beispiel 2: Abhängiger Name ist kein Typ (vorher)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   Beispiel 2 (nachher)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- **`volatile`****Member-Variablen verhindern implizit definierte Konstruktoren und Zuweisungs Operatoren** Frühere Versionen des Compilers ermöglichten, dass eine Klasse mit Element **`volatile`** Variablen standardmäßige Kopier-/bewegungskonstruktoren und standardmäßige Kopier-/verschiebezuweisungsoperatoren automatisch generiert werden. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler geht bei einer Klasse mit volatilen Membervariablen davon aus, dass sie nicht triviale Konstruktions- und Zuweisungsoperatoren hat. Dies verhindert, dass Standardimplementierungen dieser Operatoren automatisch generiert werden. Ist eine solche Klasse ein Member einer Union (oder einer anonymen Union innerhalb einer Klasse), werden Kopier-/Verschiebekonstruktoren und Kopier-/Verschiebezuweisungsoperatoren der Union (oder die Klasse, die die anonyme Union enthält) implizit als gelöscht definiert. Wird versucht, die Union (oder die Klasse, die die anonyme Union enthält) zu erstellen oder zu kopieren, ohne sie explizit zu definieren, tritt ein Fehler auf, und der Compiler gibt den Compilerfehler C2280 aus.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   Beispiel (vorher)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   Beispiel (nachher)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **Statische Memberfunktionen unterstützen keine cv-Qualifizierer**

   In früheren Versionen von Visual C++ 2015 ist es zulässig, dass statische Memberfunktionen CV-Qualifizierer haben. Dieses Verhalten ist durch einen Rückschritt in Visual C++ 2015 und Visual C++ 2015 Update 1 begründet. Visual C++ 2013 und frühere Versionen von Visual C++ weisen Code zurück, der in dieser Weise geschrieben ist. Das Verhalten von Visual C++ 2015 und Visual C++ 2015 Update 1 ist falsch und entspricht nicht dem C++-Standard.  Visual Studio 2015 Update 2 weist Code, der in dieser Weise geschrieben ist, zurück und gibt stattdessen den Compilerfehler C2511 aus.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   Beispiel (vorher)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   Beispiel (nachher)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **Vorwärtsdeklaration einer Enumeration ist in WinRT-Code nicht zulässig** (betrifft nur `/ZW`)

   Code, der für die Windows-Runtime (WinRT) kompiliert **`enum`** wurde, lässt nicht zu, dass Typen als deklariert werden, ähnlich wie bei der Kompilierung von verwaltetem C++-Code für .NET Framework mit dem `/clr` Compilerschalter. Dieses Verhalten stellt sicher, dass die Größe einer Enumeration immer bekannt ist und richtig in das WinRT-Typsystem projiziert werden kann. Der Compiler lehnt in dieser Weise geschriebenen Code ab und gibt den Compilerfehler C2599 zusammen mit dem Compilerfehler C3197 aus.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   Beispiel (vorher)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   Beispiel (nachher)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **new- oder delete-Funktionen eines überladenen Nicht-Memberoperators dürfen nicht inline deklariert werden** (Level 1 (`/W1`) standardmäßig aktiviert)

   Frühere Versionen des Compilers geben keine Warnung aus, wenn nicht Member **Operator new** und **Operator Delete** -Funktionen als Inline deklariert werden. Auf diese Weise geschriebener Code ist nicht ordnungsgemäß formatiert (keine Diagnose erforderlich). Dies kann zu Arbeitsspeicherproblemen führen, die sich aus nicht zusammengehörigen new- und delete-Operatoren ergeben (insbesondere bei Verwendung von Zuordnungsaufhebung mit Größenangabe), die sich nur schwer diagnostizieren lassen. Der Compiler gibt jetzt die Warnung C4595 aus, um Code erkennen zu können, der in dieser Weise geschrieben ist.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   Beispiel (vorher)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   Beispiel (nachher)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   Ein Korrigieren von Code, der in dieser Weise geschrieben ist, kann erfordern, dass die Operatordefinitionen aus einer Headerdatei in eine entsprechende Quelldatei verschoben werden.

### <a name="conformance-improvements-in-visual-studio-2015-update-3"></a><a name="VS_Update3"></a> Verbesserungen der Konformität in Visual Studio 2015 Update 3

- **std::is_convertable erkennt jetzt Selbstzuweisung** (Standardbibliothek) Frühere Versionen des Typmerkmals `std::is_convertable` haben die Selbstzuweisung eines Klassentyps nicht ordnungsgemäß anerkannt, wenn der Kopierkonstruktor gelöscht wurde oder privat war. Nun `std::is_convertable<>::value` ist ordnungsgemäß auf festgelegt, **`false`** Wenn Sie auf einen Klassentyp mit einem gelöschten oder privaten Kopierkonstruktor angewendet wird.

   Dieser Änderung ist keine Compilerdiagnose zugeordnet.

   Beispiel

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   In früheren Versionen von Visual C++ wurden die statischen Assertionen unten in diesem Beispiel übergeben, da `std::is_convertable<>::value` fälschlicherweise auf festgelegt wurde **`true`** . Nun `std::is_convertable<>::value` ist richtig auf festgelegt **`false`** , sodass die statischen Assertionen fehlschlagen.

- **Standardmäßig verwendete und gelöschte triviale Kopier- und Verschiebekonstruktoren beachten Zugriffsspezifizierer**

   In früheren Versionen des Compilers wurden die Zugriffsspezifizierer von als Standard festgelegten und gelöschten trivialen Kopier- und Verschiebekonstruktoren nicht geprüft, ehe ihr Aufrufen erlaubt wurde. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Durch dieses alte Verhalten entstand in einigen Fällen die Gefahr der stummen Erzeugung von ungültigem Code, was zu unvorhersehbarem Laufzeitverhalten führt. Der Compiler prüft jetzt den Zugriffsspezifizierer von als Standard festgelegten und gelöschten trivialen Kopier- und Verschiebekonstruktoren, um zu bestimmen, ob diese aufgerufen werden können. Falls nicht, gibt der Compiler die Warnung C2248 aus.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   Beispiel (vorher)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   Beispiel (nachher)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **Attributierter ATL-Code veraltet** (Level 1 (`/W1`) standardmäßig EIN)

   Frühere Versionen des Compilers haben attributierten ATL-Code unterstützt. In der nächsten Phase der Aufhebung der Unterstützung von attributiertem ATL-Code, die [in Visual C++ 2008 begann](#whats-new-for-c-in-visual-studio-2008), gilt attributierter ATL-Code nun als veraltet. Der Compiler gibt jetzt die Warnung C4467 aus, um diese Art von veraltetem Code erkennen zu können.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Wenn Sie attributierten ATL-Code bis zur Aufhebung der Unterstützung durch den Compiler weiter nutzen möchten, können Sie diese Warnung deaktivieren, indem Sie das Befehlszeilenargument `/Wv:18` oder `/wd4467` an den Compiler übergeben oder `#pragma warning(disable:4467)` Ihrem Quellcode hinzufügen.

   Beispiel 1 (vorher)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Beispiel 1 (nachher)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Mitunter müssen oder möchten Sie ggf. eine IDL-Datei erstellen, um die Nutzung veralteter ATL-Attribute zu vermeiden (siehe den folgenden Beispielcode).

   Beispiel 2 (vorher)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   Erstellen Sie zunächst die *idl-Datei. Die generierte Datei vc140.idl kann zum Abrufen einer \*.idl-Datei verwendet werden, die die Schnittstellen und Anmerkungen enthält.

   Fügen Sie als Nächstes Ihrem Build einen MIDL-Schritt hinzu, um sicherzustellen, dass die C++-Schnittstellendefinitionen generiert werden.

   Beispiel 2: IDL (nachher)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   Verwenden Sie dann ATL direkt in der Implementierungsdatei (siehe den folgenden Beispielcode).

   Beispiel 2: Implementierung (nachher)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **Vorkompilierte Headerdateien (PCH) und nicht übereinstimmende #include-Anweisungen** (wirkt sich nur auf `/Wall` `/WX` aus)

   Frühere Version des Compilers haben bei Verwendung vorkompilierter Headerdateien (PCH) nicht übereinstimmende `#include`-Direktiven in Quelldateien zwischen `-Yc`- und `-Yu`-Kompilierungen akzeptiert. Auf diese Weise geschriebener Code wird vom Compiler nicht mehr akzeptiert. Der Compiler gibt nun die Compilerwarnung CC4598 aus, um bei Verwenden von PCH-Dateien nicht übereinstimmende `#include`-Direktiven zu bestimmen.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Beispiel (vorher):

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Beispiel (nachher)

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Vorkompilierte Headerdateien (PCH) und nicht übereinstimmende include-Anweisungen** (wirkt sich nur auf `/Wall` `/WX` aus)

   Frühere Version des Compilers haben bei Verwendung vorkompilierter Headerdateien (PCH) nicht übereinstimmende Befehlszeilenargumente des Typs „include-Verzeichnis“ (`-I`) für den Compiler zwischen `-Yc`- und `-Yu`-Kompilierungen akzeptiert. Auf diese Weise geschriebener Code wird vom Compiler nicht mehr akzeptiert.   Der Compiler gibt nun die Compilerwarnung CC4599 aus, um bei Verwenden von PCH-Dateien nicht übereinstimmende Befehlszeilenargumente des Typs „include-Verzeichnis“ (`-I`) zu bestimmen.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   Beispiel (vorher)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   Beispiel (nachher)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Neuerungen bei C++ in Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Verbesserte Unterstützung der ISO-C/C++-Standards

#### <a name="compiler"></a>Compiler

Microsoft Visual C++ unterstützt diese ISO C++11-Sprachfeatures:

- Standardvorlagenargumente für Funktionsvorlagen.
- Delegierende Konstruktoren
- Explizite Konvertierungsoperatoren.
- Initialisierungslisten und einheitliche Initialisierung.
- Unformatierten Zeichenfolgenliterale.
- Variadic-Vorlagen.
- Aliasvorlagen
- Gelöschte Funktionen
- Nicht statische Datenmemberinitialisierer (NSDMIs)
- Standardfunktionen \*
- Unterstützte ISO C99-Sprachfunktionen:
- _Bool
- Verbundliterale
- Festgelegte Initialisierer
- Mischen von Deklarationen mit Code
- Zeichenfolgenliteralkonvertierung an änderbaren Werten kann durch Verwendung der neuen Compileroption `/Zc:strictStrings` als unzulässig bezeichnet werden. In c++ 98 ist die Konvertierung von Zeichenfolgenliteralen in **`char*`** (und Breite Zeichen folgen Literale in `wchar_t*` ) veraltet. In C++11 wurde die Konvertierung vollständig entfernt. Obwohl der Compiler dem Standard strikt entsprechen könnte, wird stattdessen die Option `/Zc:strictStrings` bereitgestellt, mit der die Konvertierung gesteuert werden kann. Standardmäßig ist die Option deaktiviert. Beachten Sie, dass bei Verwendung dieser Option im Debugmodus STL nicht kompiliert.
- rvalue/lvalue-Verweisumwandlungen. Mit rvalu-Verweisen kann C++11 eindeutig zwischen lvalues und rvalues unterscheiden. Zuvor war das mit dem Compiler in bestimmten Umwandlungsszenarios nicht möglich. Die neue Compileroption `/Zc:rvalueCast` wurde hinzugefügt, damit der Compiler mit dem C++ Language Working Paper (siehe Abschnitt 5.4, [expr.cast]/1) kompatibel ist. Wenn diese Option nicht angegeben wird, entspricht das Standardverhalten dem von Visual Studio 2012.

> [!NOTE]
> Für Standardwertfunktionen wird die Verwendung von „=default“ nicht unterstützt, um memberspezifische Bewegungskonstruktoren und Bewegungszuweisungsoperatoren anzufordern.

### <a name="c99-libraries"></a>C99-Bibliotheken

Deklarationen und Implementierungen werden für fehlende Funktionen zu den folgenden Headern hinzugefügt: „math.h“, „ctype.h“, „wctype.h“, „stdio.h“, „stdlib.h“ und „wchar.h“. Außerdem wurden die neuen Header „complex.h“, „stdbool.h“, „fenv.h“ und „inttypes.h“ sowie Implementierungen für alle Funktionen hinzugefügt, die darin deklariert werden. Es gibt neue Wrapperheader für C++ („ccomplex“, „cfenv“, „cinttypes“, „ctgmath“) und eine Reihe von weiteren aktualisierten Headern („ccomplex“, „cctype“, „clocale“, „cmath“, „cstdint“, „cstdio“, „cstring“, „cwchar“ und „cwctype“).

### <a name="standard-template-library"></a>Standard Template Library

Unterstützung für explizite Konvertierungsoperatoren, Initialisierungslisten, bewertete Enumerationen und variadic Vorlagen von C++11.
Alle Container unterstützen jetzt die differenzierten C++11-Elementanforderungen.
Unterstützung für diese C++14-Funktionen:

- Die transparenten Operatorfunktionselemente less<>, greater<>, plus<>, multiplies<> usw.
- make_unique\<T>(Args) und make_unique<T[]>(n)
- Die Nicht-Memberfunktionen cbegin()/cend(), rbegin()/rend() und crbegin()/crend().
- \<atomic> Es wurden zahlreiche Leistungsverbesserungen erhalten.
- \<type_traits> Es wurden wichtige Stabilisierungs-und Code Fehlerbehebungen erhalten.

### <a name="breaking-changes"></a>Aktuelle Änderungen

Diese verbesserte Unterstützung für ISO-C/C++-Standards erfordert möglicherweise Änderungen am vorhandenen Code, sodass er C++11 entspricht und ordnungsgemäß in Visual C++ in Visual Studio 2013 kompiliert wird.

### <a name="visual-c-library-enhancements"></a>Verbesserungen bei Visual C++-Bibliotheken

- C++-REST SDK wird hinzugefügt. Es verfügt über eine moderne C++-Implementierung von REST-Diensten.
- Die C++-AMP-Texturunterstützung wurde verbessert. Sie umfasst jetzt Unterstützung für Mipmaps und neue Samplingsmodi.
- PPL-Aufgaben unterstützen mehrere Planungstechnologien und asynchrones Debuggen. Neue APIs ermöglichen die Erstellung von PPL-Aufgaben für Normalbefunde und Ausnahmebedingungen.

### <a name="c-application-performance"></a>C++-Anwendungsleistung

- Automatische Vektorisierung erkennt und optimiert jetzt mehrere C++-Muster, damit der Code schneller ausgeführt wird.
- Verbesserungen bei der Codequalität der ARM-Plattform- und Atom-Mikroarchitektur.
- Die __vectorcall-Aufrufkonvention wurde hinzugefügt. Übergeben Sie Vektortypargumente mithilfe der __vectorcall-Aufrufkonvention, um Vektorregister zu verwenden.
- Neue Linkeroptionen. Die Schalter `/Gw` (Compiler) und `/Gy` (Assembler) aktivieren Linkeroptimierungen, um schlankere Binärdateien zu erzeugen.
- C++ AMP hat Arbeitsspeicherunterstützung freigegeben, um das Kopieren von Daten zwischen CPU und GPU zu reduzieren oder auszuschließen.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Verbesserungen der profilgesteuerten Optimierung (PGO)

- Leistungsverbesserungen durch eine Reduzierung der Arbeitsseiten von Apps, die durch die Verwendung von PGO optimiert werden.
- Neue profilgesteuerte Optimierung für die Entwicklung von Windows-Runtime-Apps.

### <a name="windows-runtime-app-development-support"></a>Unterstützung für die Entwicklung von Windows-Runtime-Apps

- **Unterstützung für Wertstrukturtypen, für die ein Boxing durchgeführt wurde**

   Sie können jetzt Werttypen definieren, indem Sie Felder verwenden, die NULL sein können – z `IBox<int>^` . b. im Gegensatz zu **`int`** . Dies bedeutet, dass die Felder entweder einen Wert haben können oder gleich sind **`nullptr`** .

- **Umfangreichere Ausnahmeinformationen**

   C++/CX unterstützt das neue Windows-Fehlermodell, das die Erfassung und die Weitergabe von umfangreichen Ausnahmeinformationen über der Anwendungsbinärdateischnittstelle (ABI) aktiviert. Dies schließt auch Aufruflisten und benutzerdefinierte Meldungs- ein.

- **Object::ToString() ist jetzt virtuell**

   Sie können „ToString“ in benutzerdefinierten Windows-Runtime-Referenztypen überschreiben.

- **Unterstützung für veraltete APIs**

   Öffentliche Windows-Runtime-APIs können jetzt als veraltet markiert und ihnen kann eine benutzerdefinierte Meldung zugewiesen werden, die als Buildwarnung angezeigt werden und Migrationsanleitungen bereitstellen kann.

- **Debugger-Verbesserungen.**

   Unterstützung für systemeigenes/JavaScript-Interop-Debuggen, Windows Runtime-Ausnahmediagnose und asynchrones Debuggen von Code (Windows Runtime und PPL).

> [!NOTE]
> Zusätzlich zu den C++-spezifischen Features und Erweiterungen, die in diesem Abschnitt beschrieben werden, können Sie mithilfe anderer Erweiterungen in Visual Studio bessere Apps für Windows-Runtime schreiben.

### <a name="diagnostics-enhancements"></a>Verbesserungen bei Diagnosen

- Debugger-Verbesserungen. Unterstützung für asynchrones Debuggen und „Nur mein Code“-Debuggen.
- Kategorien für die Codeanalyse. Sie können nun die kategorisierte Ausgabe des Code-Analyzer anzeigen, anhand derer Sie Codefehler finden und beheben können.
- XAML-Diagnose. Sie können nun die UI-Reaktionsfähigkeit sowie Akkuverwendungsprobleme im XAML-Code diagnostizieren.
- Verbesserungen beim Grafik- und GPU-Debugging.
- Remote-Erfassung und -Wiedergabe auf realen Geräten.
- Simultanes C++-AMP- und -CPU-Debugging.
- Verbesserte C++-AMP-Laufzeitdiagnose.
- HLSL-Compute-Shader-Ablaufverfolgungsdebugging.

### <a name="3-d-graphics-enhancements"></a>Verbesserungen bei der 3D-Grafik

- Unterstützung der Pipeline für Bildinhalte für vorab multipliziertes Alpha-DDS-Format.
- Die Bildbearbeitung verwendet intern vorab multipliziertes Alpha zum Rendern und vermeidet somit das Rendern von Artefakten wie dunklen Halos.
- Bild- und Modell-Editors. Benutzerdefinierte Filtererstellung wird jetzt im Shader-Designer im Bild- und im Modell-Editor unterstützt.

### <a name="ide-and-productivity"></a>IDE und Produktivität

**Verbesserte Codeformatierung.** Sie können mehr Formatierungseinstellungen auf den C++-Code anwenden. Wenn Sie diese Einstellungen verwenden, können Sie die Platzierung neuer Zeilen von geschweiften Klammern und Schlüsselwörtern, Einzügen, Abständen und Zeilenumbrüchen steuern. Code wird automatisch formatiert, wenn Sie Anweisungen und Blöcke abschließen und wenn Sie Code in eine Datei einfügen.

**Klammerabschluss.** C++-Code vervollständigt die Schlusszeichen, die diesen Öffnungszeichen entsprechen, jetzt automatisch:

- { (geschweifte Klammer)
- [ (eckige Klammer)
- ( (runde Klammer)
- ' (Einfaches Anführungszeichen)
- " (doppeltes Anführungszeichen)

**Zusätzliche C++-Features für die automatische Vervollständigung**

- Fügt Semikolon für Klassentypen hinzu.
- Vervollständigt Klammern für unformatierte Zeichenfolgenliterale.
- Vervollständigt Mehrzeilige Kommentare (/ \* \* /)

**Alle Verweise suchen** löst jetzt Verweise auf und filtert sie im Hintergrund, nachdem die Liste der Textabgleichungen angezeigt wurde.

**Kontextbasierte Memberlistenfilterung.** Member, auf die nicht zugegriffen werden kann, werden aus den IntelliSense-Memberlisten herausgefiltert. Beispielsweise werden private Member nicht in der Memberliste angezeigt, es sei denn, Sie ändern den Code, der den Typ implementiert. Wenn die Mitgliederliste geöffnet ist, können Sie **STRG** + **J** drücken, um eine Ebene der Filterung zu entfernen (gilt nur für das Fenster aktuelle Elementliste). Sie können erneut **STRG** + **J** drücken, um die Text Filterung zu entfernen und alle Member anzuzeigen.

**Scrollfeature für Parameterhilfe.** Die angezeigte Funktionssignatur in der QuickInfo der Parameter Hilfe ändert sich jetzt je nach Anzahl der Parameter, die Sie wirklich eingegeben haben, anstatt nur eine beliebige Signatur anzuzeigen, die nicht auf Grundlage des aktuellen Kontextes aktualisiert wird. Parameterhilfe funktioniert auch ordnungsgemäß, wenn sie in geschachtelten Funktionen angezeigt wird.

**Header-/Codedatei umschalten.** Sie können nun zwischen einem Header und der zugehörigen Codedatei umschalten, indem Sie einen Befehl im Kontextmenü oder eine Tastenkombination verwenden.

**In der Größe veränderbares C++-Projekteigenschaftenfenster**

**Automatisches Generieren des Ereignishandlercodes in C++/CX und C++/CLI.**  Wenn Sie Code eingeben, um einen Ereignishandler in einer C++/CX- oder C++/CLI-Codedatei hinzuzufügen, kann der Editor die Delegatinstanz und die Ereignishandlerdefinition automatisch generieren. Ein QuickInfo-Fenster wird angezeigt, wenn Ereignishandlercode automatisch generiert werden kann.

**Verbesserung der DPI-Berücksichtigung.** Die DPI-Einstellung für Anwendungsmanifestdateien unterstützt jetzt die Einstellung "Hohe DPI-Werte pro Monitor".

**Schnellere Konfigurationsumschaltung.** Für große Anwendungen werden Konfigurationen, insbesondere nachfolgende Umschaltvorgänge, viel schneller ausgeführt.

**Effizienz der Buildzeit.** Zahlreiche Optimierungen und Multikernauslastung machen Builds schneller, insbesondere für umfangreiche Projekte. Inkrementelle Builds für C++-Anwendungen, die Verweise auf C++ WinMD aufweisen, sind ebenfalls viel schneller.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Neuerungen bei C++ in Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Verbesserte Unterstützung von C++11-Standards

#### <a name="standard-template-library"></a>Standard Template Library

- Unterstützung für neue STL-Header: \<atomic> , \<chrono> , \<condition_variable> , \<filesystem> , \<future> , \<mutex> , \<ratio> und \<thread> .
- Container sind jetzt kleiner, damit die Speicherauslastung durch die Ressourcen optimiert wird. Beispielsweise wurde `std::vector` im Releasemodus x86 mit Standardeinstellungen von 16 Bytes in Visual Studio 2010 auf 12 Bytes in Visual Studio 2012 reduziert, und `std::map`wurde von 16 Bytes in Visual Studio 2010 auf 8 Bytes in Visual Studio 2012 reduziert.
- SCARY-Iteratoren wurden implementiert. Dies wird in C++11-Standard zugelassen, ist aber nicht erforderlich.

#### <a name="other-c11-enhancements"></a>Weitere Erweiterungen für C++11

- Bereichsbasierte For-Schleifen. Sie können jetzt stabile Schleifen schreiben, die mit Arrays, STL-Containern und Windows-Runtime-Auflistungen in For-Form zusammenarbeiten (for-range-declaration : expression). Dies ist ein Bestandteil der Kernsprachunterstützung.
- Zustandslose Lambdas (Codeblöcke, die mit der leeren Lambdaeinführung [] beginnen und keine lokalen Variablen erfassen) können jetzt implizit in Funktionszeiger konvertiert werden, wie für C++ 11-Standard erforderlich.
- Unterstützung für bereichsbezogene Enumerationen. Der Enumerationsschlüssel der C++-Enumerationsklasse wird jetzt unterstützt. Folgender Code stellt dar, wie dieser Enumerationsschlüssel vom vorherigen Enumerationsverhalten abweicht.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Unterstützung für die Entwicklung von Windows-Runtime-Apps

- **Natives XAML-basiertes Benutzeroberflächenmodell.** Sie können jetzt für Windows Runtime-Apps das neue native XAML-basierte Benutzeroberflächenmodell verwenden.
- **Visual C++ Komponenten Erweiterungen**. Diese Erweiterungen vereinfachen die Verarbeitung von Windows-Runtime-Objekten, die ein wichtiger Bestandteil von Windows Runtime-Apps sind. Weitere Informationen finden Sie unter [Roadmap for Windows Runtime apps using C++ (Übersicht zur Verwendung von C++ für Windows-Runtime-Apps)](../cppcx/universal-windows-apps-cpp.md) und in der [Sprachreferenz zu Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md).
- **DirectX-Spiele.** Sie können spannende Spiele entwickeln, indem Sie die neue DirectX-Unterstützung für Windows-Runtime-Apps verwenden.
- **XAML/DirectX-Interop.** Windows-Runtime-Apps, die XAML und DirectX verwenden, arbeiten jetzt auf effiziente Weise zusammen.
- **Komponente für die Windows-Runtime für die DLL-Entwicklung.** Durch die Komponente für die DLL-Entwicklung wird die Windows-Runtime-Umgebung erweiterbar.

### <a name="compiler-and-linker"></a>Compiler und Linker

- **Automatische Vektorisierung**. Der Compiler analysiert Schleifen in Ihrem Code und gibt wenn möglich Anweisungen aus, die die Vektorregister und-anweisungen verwendet, die in allen modernen Prozessoren vorhanden sind. Dadurch werden die Schleifen schneller ausgeführt. (Die Anweisungen des Prozessors werden als Streaming SIMD Extensions (SSE) bezeichnet.) Sie müssen diese Optimierung nicht aktivieren oder anfordern, da sie automatisch angewendet wird.
- **Automatische Parallelisierung**. Der Compiler kann Schleifen in Ihrem Code analysieren und Anweisungen ausgeben, die die Berechnungen auf mehrere Kerne und Prozessoren ausweiten. Dadurch können die Schleifen schneller ausgeführt werden. Sie müssen diese Optimierung anfordern, da sie nicht standardmäßig aktiviert ist. Häufig ist es hilfreich, `#pragma loop(hint_parallel(N))` vor den Schleifen in Ihren Code einzufügen, die parallel verlaufen sollen.
- Die automatische Vektorisierung und die automatische Parallelisierung können zusammenarbeiten, sodass Berechnungen auf mehrere Kerne ausgeweitet werden können und der Code auf jedem Kern seine jeweiligen Vektorregister verwendet.

### <a name="new-in-visual-studio-2012-update-1"></a>Neuerungen in Visual Studio 2012 Update 1

Verwenden Sie Windows XP als Ziel, wenn Sie C++-Code erstellen.
Sie können den Microsoft Visual C++-Compiler und die Microsoft Visual C++-Bibliotheken verwenden, um Windows XP und Windows Server 2003 als Ziel zu verwenden.

#### <a name="parallel-programming-support"></a>Unterstützung der parallelen Programmierung

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP beschleunigt die Ausführung von C++-Code, indem die Vorteile datenparalleler Hardware genutzt werden, beispielsweise ein Grafikprozessor (Graphics Processing Unit, GPU) auf einer separaten Grafikkarte. Das C++ AMP-Programmiermodell umfasst mehrdimensionale Arrays, Indizierung, Arbeitsspeicherübertragung, Kacheln und eine Bibliothek mathematischer Funktionen. Mithilfe von C++ AMP-Spracherweiterungen und Compilerbeschränkungen können Sie steuern, wie Daten von der CPU auf die GPU bzw. wieder zurück verschoben werden.

**Suche.** Das Debuggen von Apps, die C++ AMP verwenden, um die GPU als Ziel zu verwenden, entspricht dem Debugvorgang für andere C++-Apps. Dies umfasst die neuen Funktionen zum parallelen Debuggen, die zuvor genannt wurden.

**Liert.** Die Profilerstellungen für GPI-Aktivitäten, die auf C++ AMP und anderen Direct3D-basierten Programmierungsmodellen aufbauen, wird jetzt unterstützt.

#### <a name="general-parallel-programming-enhancements"></a>Allgemeine Verbesserungen des parallelen Programmierens

Entwickler können sich nicht mehr darauf verlassen, dass die Taktfrequenzen einzelner Kerne immer weiter erhöht werden, denn die Hardware wird derzeit eher auf die Arbeit mit mehreren Kernen und Architekturen ausgerichtet. Mithilfe der Unterstützung der parallelen Programmierung in Concurrency Time können Entwickler diese neuen Architekturen nutzen.
In Visual Studio 2010 wurden neben Funktionen, die die Parallelität nutzen, indem sie optimierte Datenflusspipelines erstellen, auch leistungsstarke C++-Parallelisierungen wie die Parallel Patterns Library eingeführt. In Visual Studio 2012 wurden diese Bibliotheken erweitert, um die Leistung zu verbessern, die Kontrolle zu erhöhen und eine bessere Unterstützung für die wichtigsten Parallelmuster für die Entwickler bereitzustellen. Folgendes ist jetzt in dem Angebot enthalten:

- Ein umfassendes aufgabenbasiertes Programmierungsmodell, das Asynchronität und Fortsetzungen unterstützt.
- Parallele Algorithmen, die fork/join-Parallelität unterstützen („parallel_for“, „parallel_for“ mit Affinität, „parallel_for_each“, „parallel_sort“, „parallel_reduce“, „parallel_transform“).
- Parallelitätssichere Container, die threadsichere Versionen von std-Datenstrukturen wie „priority_queue“, „queue“, „vector“ und „map“ bereitstellen.
- Die Bibliothek des asynchronen Agents, die Entwickler nutzen können, um Datenflusspipelines zu erstellen, die automatisch in parallele Einheiten zerlegt werden.
- Ein anpassbarer Scheduler und Ressourcen-Manager zur Vereinfachung der problemlosen Zusammensetzung der Muster in dieser Liste.

##### <a name="general-parallel-debugging-enhancements"></a>Allgemeine Verbesserungen des parallelen Debuggens

Zusätzlich zum Fenster **parallele Aufgaben** und **parallele Stapel** bietet Visual Studio 2012 ein neues Fenster für **parallele Überwachung** , sodass Sie die Werte eines Ausdrucks für alle Threads und Prozesse überprüfen und das Sortieren und Filtern für das Ergebnis durchführen können. Sie können jetzt außerdem Ihre eigenen visuellen Elemente verwenden, um das Fenster zu erweitern und die Vorteile der neuen Unterstützung von mehreren Prozessen toolfensterübergreifend nutzen.

### <a name="ide"></a>IDE

**Unterstützung von Visual Studio-Vorlagen.** Sie können jetzt die Technologie der Visual Studio-Vorlagen verwenden, um C++-Projekte und Elementvorlagen zu erstellen.

**Asynchrones Laden von Projektmappen.** Projekte werden jetzt auf asynchrone Weise geladen, d.h. die wichtigsten Bestandteile der Projektmappe zuerst, sodass Sie schneller mit der Arbeit beginnen können.

**Automatisierte Bereitstellung für das Remotedebuggen.** Die Bereitstellung von Dateien für das Remotedebuggen in Visual C++ wurde vereinfacht. Die Option **Bereitstellen** im Kontextmenü des Projekts kopiert die Dateien, die in den Eigenschaften für die Debugkonfiguration angegeben sind, automatisch auf den Remotecomputer. Es ist nicht mehr erforderlich, die Dateien manuell auf den Remotecomputer zu kopieren.

**IntelliSense für C++/CLI.** IntelliSense wird für C++/CLI nun vollständig unterstützt. IntelliSense-Features wie QuickInfo, die Parameterhilfe, Listenmembers und die automatische Vervollständigung funktionieren jetzt für C++/CLI. Zudem funktionieren die anderen in diesem Dokument aufgeführten IntelliSense- und IDE-Erweiterungen ebenfalls für C++/CLI.

**Umfangreichere IntelliSense-QuickInfos.** Die IntelliSense-QuickInfo für C++ zeigt jetzt XML-Dokumentationskommentare mit Informationen zum Stil an. Wenn Sie eine API für eine Bibliothek verwenden, die über XML-Dokumentationskommentare verfügt, z.B. C++ AMP, zeigt die InteliSense-QuickInfo neben der Deklaration auch weitere Informationen an. Wenn Ihr Code außerdem XML-Dokumentationskommentare enthält, zeigt die IntelliSense-QuickInfo umfangreichere Informationen an.

**C++-Codekonstrukte.** Für Codekonstrukte wie u.a. „switch“, „if-else“ oder „for loop“ ist Skelettcode in der Dropdownliste der Listenmembers verfügbar. Wählen Sie aus der Liste ein Codefragment aus, das Sie in Ihren Code einfügen, und fügen Sie dann die erforderliche Logik ein. Sie können auch Ihre eigenen Codefragmente erstellen, um sie im Editor zu verwenden.

**Verbesserungen bei „Member auflisten“.** Die Dropdownliste mit den **Listenmembers** wird automatisch angezeigt, wenn Sie Code in den Code-Editor eingeben. Ergebnisse werden gefiltert, sodass beim Tippen nur relevante Members angezeigt werden. Sie können im Dialogfeld **Optionen** unter **Text-Editor** > **C/C++** > **Erweitert** steuern, welche Filterlogik von der Memberliste verwendet werden soll.

**Semantische Farbgebung.** Für Typen, Aufzählungen, Makros sowie andere C++-Tokens ist jetzt standardmäßig die Farbgebung aktiviert.

**Verweismarkierung.** Wenn Sie ein Symbol auswählen, werden jetzt alle Instanzen des Symbols in der aktuellen Datei angezeigt. Drücken Sie **STRG** + **UMSCHALT**Taste + nach**oben** oder **STRG** + **UMSCHALT**nach + **unten** , um zwischen den hervorgehobenen verweisen zu wechseln. Sie können diese Funktion im Dialogfeld **Optionen** unter **Text-Editor** > **C/C++** > **Erweitert** deaktivieren.

### <a name="application-lifecycle-management-tools"></a>Anwendungslebenszyklus-Verwaltungstools

#### <a name="static-code-analysis"></a>Statische Codeanalyse

Die statische Analyse für C++ wurde aktualisiert, damit umfangreichere Informationen zu Fehlerkontexten, mehr Analyseregeln sowie bessere Analyseergebnisse bereitgestellt werden. Im neuen Fenster „Codeanalyse“ können Sie Meldungen nach Schlüsselwort, Projekt und Schweregrad filtern. Beim Auswählen einer Meldung in diesem Fenster wird die entsprechende Zeile, in der die Meldung ausgelöst wurde, im Quellcode-Editor hervorgehoben. Für bestimmte C++-Warnungen führt die Meldung Quellzeilen auf, die den Ausführungspfad zu der Warnung anzeigen. Entscheidungspunkte und die Gründe,warum dieser bestimmte Pfad ausgewählt wurde, werden hervorgehoben.
Die Codeanalyse ist in allen Editionen von Visual Studio 2012 enthalten. In den Editionen Professional, Premium und Ultimate sind alle Regeln enthalten. In den Express-Editionen für Windows 8 und Windows Phone sind nur die wichtigsten Warnungen enthalten. Die Codeanalyse ist nicht in der Express-Edition für Web enthalten.
Im Folgenden werden einige andere Erweiterungen der Codeanalyse aufgeführt:

- Mithilfe neuer Parallelitätswarnungen können Sie Fehler mit der Parallelität vermeiden, indem Sie darauf achten, dass Sie die richtigen Sperrdisziplinen in C/C++-Multithreadprogrammen verwenden. Der Analyzer erkennt verschiedene mögliche Racebedingungen, Sperrreihenfolgenumstellungen, Aufrufer-/Aufgerufener-Sperrenvertragsverletzungen, nicht übereinstimmende Synchronisierungsvorgänge sowie weitere Fehler bei der Parallelität.
- Sie können die C++-Regeln angeben, die Sie auf Ausführungen der Codeanalyse anwenden möchten, indem Sie Regelsätze verwenden.
- Sie können im **Codeanalysefenster** ein Pragma in den Quellcode einfügen, das eine ausgewählte Warnung unterdrückt.
- Sie können die Genauigkeit und Vollständigkeit der statischen Codeanalyse verbessern, indem Sie die neue Version der Quellcodeanmerkungssprache von Microsoft (Microsoft Source-Code Annotation Language, SAL) verwenden, um zu beschreiben, wie eine Funktion ihre jeweiligen Parameter verwendet, welche Annahmen sie zu diesen Parametern trifft und welche Garantien sie gewährleistet, wenn sie abgeschlossen wird.
- Unterstützung von 64-Bit-C++-Projekten.

#### <a name="updated-unit-test-framework"></a>Aktualisiertes Komponententestframework

Verwenden Sie das neue Komponententestframework für C++ in Visual Studio, um Komponententests für C++ zu schreiben. Fügen Sie ein neues Komponententestprojekt zu Ihrer bereits vorhandenen C++-Projektmappe hinzu, indem Sie in der Kategorie „Visual C++“ im Dialogfeld „Neues Projekt“ die Vorlage für das C++-Komponententestprojekt suchen. Beginnen Sie damit, Ihre Komponententests in der Datei „Unittest1.cpp“ in den generierten Rumpfcode „TEST_METHOD“ zu schreiben. Erstellen Sie die Projektmappe, nachdem Sie den Testcode geschrieben haben. Öffnen Sie zum Ausführen der Tests das Fenster **Komponententest-Explorer**, indem Sie erst auf **Ansicht** > **Weitere Fenster** > **Komponentest-Explorer** und anschließend im Kontextmenü für die gewünschte Testsituation auf **Ausgewählten Test ausführen** klicken. Nach Abschluss des Testlaufs können Sie in demselben Fenster die Testergebnisse und zusätzliche Überwachungsinformationen abrufen.

#### <a name="architecture-dependency-graphs"></a>Architektur der Abhängigkeitsdiagramme

Damit Sie Ihren Code besser verstehen können, können Sie jetzt Abhängigkeitsdiagramme für die Binärdatei, die Klasse und den Namespace generieren und Dateien in eine Projektmappe einfügen. Wählen Sie in der Menüleiste **Architektur**  >  **Abhängigkeits Diagramm generieren**und dann **für** Projekt **Mappe oder für Includedatei** aus, um ein Abhängigkeits Diagramm zu generieren. Wenn die Generierung des Diagramms beendet ist, können Sie es durchsuchen, indem Sie die einzelnen Knoten erweitern, die Abhängigkeitsbeziehungen durch Verschieben zwischen Knoten ermitteln und Quellcode durchsuchen, indem Sie im Kontextmenü für einen Knoten **Inhalt anzeigen** auswählen. Wenn Sie ein Abhängigkeits Diagramm für Includedateien generieren möchten, wählen Sie im Kontextmenü für eine \* cpp-Quell Code Datei oder \* . h-Header Datei **Diagramm der Includedateien generieren aus**.

#### <a name="architecture-explorer"></a>Architektur-Explorer

Wenn Sie den **Architektur-Explorer** verwenden, können Sie das Objekt in Ihrer C++-Projektmappe, in ihren Projekten oder in ihren Dateien durchsuchen. Wählen Sie in der Menüleiste **Architektur**  >  **Windows**-  >  **Architektur-Explorer**aus. Sie können einen Knoten auswählen, an dem Sie interessiert sind, z. b. **Klassenansicht**. Bei diesem Beispiel wird die rechte Seite des Toolfensters mit einer Liste von Namespaces erweitert. Wenn Sie einen Namespace auswählen, wird in einer neuen Spalte eine Liste von Klassen, Strukturen und Aufzählungen in diesem Namespace angezeigt. Sie können die Objekte weiter durchsuchen oder zurück zur linken Spalte wechseln, um eine weitere Abfrage zu starten. Weitere Informationen finden Sie unter **Suchen von Code im Architektur-Explorer**.

#### <a name="code-coverage"></a>Code Coverage

Die Code Coverage wurde aktualisiert, um Binärdateien zur Runtime dynamisch zu instrumentieren. Dadurch wird der Mehraufwand für die Konfiguration reduziert und die Leistung verbessert. Außerdem können Sie Daten zur Code Coverage aus Komponententests für C++-Apps erfassen. Wenn Sie C++-Komponententests erstellt haben, können Sie den Komponenten **Test-Explorer** verwenden, um Tests in der Projekt Mappe zu ermitteln. Um die Komponententests auszuführen und Code Coverage Daten für diese zu erfassen, wählen Sie im Komponenten **Test-Explorer** **Code Coverage analysieren**aus. Sie können sich die Ergebnisse der Code Coverage im Fenster **Code Coverage-Ergebnisse** ansehen, indem Sie in der Menüleiste auf **Test** > **Fenster** > **Code Coverage-Ergebnisse** klicken.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Neuerungen bei C++ in Visual Studio 2010

### <a name="c-compiler-and-linker"></a>C++-Compiler und -Linker

**Auto-Schlüsselwort.** Das **`auto`** Schlüsselwort hat einen neuen Zweck. Verwenden Sie die Standardbedeutung des- **`auto`** Schlüssel Worts, um eine Variable zu deklarieren, deren Typ aus dem Initialisierungs Ausdruck in der Deklaration der Variablen abgeleitet wird. Die- `/Zc:auto` Compileroption ruft entweder die neue oder die vorherige Bedeutung des **`auto`** Schlüssel Worts auf.

**Typspezifizierer decltype.** Der **`decltype`** Typspezifizierer gibt den Typ eines angegebenen Ausdrucks zurück. Verwenden **`decltype`** Sie den Typspezifizierer in Kombination mit dem- **`auto`** Schlüsselwort, um einen Typ zu deklarieren, der entweder komplex oder nur dem Compiler bekannt ist. Verwenden Sie z.B. diese Kombination, um eine Vorlagenfunktion zu deklarieren, deren Rückgabetyp von den Typen seiner Vorlagenargumente abhängt. Stattdessen können Sie auch eine Vorlagenfunktion deklarieren, die einen Aufruf einer anderen Funktion aufruft und anschließend den Rückgabetyp der aufgerufenen Funktion zurückgibt.

**Lambda-Ausdrücke.** Die Lambdafunktionen verfügen über einen Funktionstext, aber nicht über einen Namen. Sie vereinen in sich die besten Eigenschaften von Funktionszeigern und Funktionsobjekten. Verwenden Sie eine Lambda-Funktion eigenständig als Vorlagen Funktionsparameter anstelle eines Funktions Objekts, oder verwenden **`auto`** Sie das Schlüsselwort, um eine Variable zu deklarieren, deren Typ ein Lambda ist.

**R-Wert-Verweis.** Der R-Wert-Verweisdeklarator (&&) deklariert einen Verweis auf einen R-Wert. Mit dem R-Wert-Verweis können Sie zusätzliche Semantik und die perfekte Weiterleitung nutzen, um effizientere Konstruktoren, Funktionen und Vorlagen in Code zu schreiben.

**static_assert-Deklaration.** Eine- **`static_assert`** Deklaration testet eine Software-Assertion zur Kompilierzeit, im Gegensatz zu anderen Durchsetzungsmechanismen, die zur Laufzeit testen. Schlägt die Assertion fehl, kann auch die Kompilierung nicht erfolgreich abgeschlossen werden. Das System gibt dann eine Fehlermeldung aus.

**Die Schlüsselwörter „nullptr“ und „__nullptr“.** Mit MSVC können Sie das **`nullptr`** Schlüsselwort mit nativem Code oder mit verwaltetem Code verwenden. Das **`nullptr`** Schlüsselwort gibt an, dass ein Objekt Handle, ein innerer Zeiger oder ein System eigener Zeigertyp nicht auf ein Objekt verweist. Der Compiler interpretiert **`nullptr`** als verwalteten Code, wenn Sie die `/clr` -Compileroption verwenden, und systemeigenen Code, wenn Sie die-Option nicht verwenden `/clr` .
Das Microsoft-spezifische **__nullptr** -Schlüsselwort hat dieselbe Bedeutung wie **`nullptr`** , es gilt jedoch nur für nativen Code. Wenn Sie systemeigenen C/C++-Code mit der- `/clr` Compileroption kompilieren, kann der Compiler nicht bestimmen, ob das **`nullptr`** Schlüsselwort ein System eigener oder ein verwalteter Begriff ist. Verwenden Sie das nullptr-Schlüsselwort, um den verwalteten Begriff anzugeben, und **__nullptr** , um den systemeigenen Begriff anzugeben, um die Absicht für den Compiler klar zu machen.

**`/Zc:trigraphs` Compileroption.** Standardmäßig ist die Unterstützung von Trigraphen deaktiviert. Verwenden Sie die- **`/Zc:trigraphs`** Compileroption zum Aktivieren der Unterstützung von Unterstützung
Ein Trigraph besteht aus zwei aufeinander folgenden Fragezeichen (??) gefolgt von einem eindeutigen dritten Zeichen. Der Compiler ersetzt einen Trigraphen durch ein entsprechendes Interpunktionszeichen. Der Compiler ersetzt z.B. den Trigraphen ??= durch das Nummernzeichen #. Verwenden Sie Trigraphen in C-Quelldateien, die einen Zeichensatz aufweisen, der einige Interpunktionszeichen nicht enthält.

**Neue Option „Profilgesteuerte Optimierung“.** Bei PogoSafeMode handelt es sich um eine neue Option zur profilgesteuerten Optimierung, über die Sie angeben können, ob der abgesicherte oder der schnelle Modus bei der Optimierung der Anwendung verwendet werden soll. Der abgesicherte Modus ist zwar threadsicher, aber langsamer als der schnelle Modus. Der schnelle Modus stellt das Standardverhalten dar.

**Neue Common Language Runtime-Option /clr:nostdlib.** Für `/clr` wurde eine neue Option hinzugefügt (Common Language Runtime-Kompilierung). Wenn verschiedene Versionen derselben Bibliotheken enthalten sind, wird ein Compilerfehler zurückgegeben. Mithilfe der neuen Option können Sie die CLR-Standardbibliotheken ausschließen, damit Ihr Programm eine festgelegte Version verwenden kann.

**Die neue pragma-Anweisung „detect_mismatch“** Mithilfe der pragma-Anweisung „detect_mismatch“ können Sie Ihren Dateien eine Markierung hinzufügen, die mit anderen Markierungen mit demselben Namen verglichen wird. Wenn es mehrere Werte für denselben Namen gibt, wird vom Linker ein Fehler zurückgegeben.

**Intrinsische XOP-Funktionen, intrinsische FMA4-Funktionen und intrinsische LWP-Funktionen.** Neue intrinsische Funktionen wurden hinzugefügt, um Prozessortechnologien für intrinsische XOP-Funktionen (für Visual Studio 2010 SP1 hinzugefügt), intrinsische FMA4-Funktionen (für Visual Studio 2010 SP1 hinzugefügt) und intrinsische LWP-Funktionen (für Visual Studio 2010 SP1 hinzugefügt) zu unterstützen. Verwenden Sie „__cpuid“ und „__cpuidex“, um zu bestimmen, welche Prozessortechnologien auf den einzelnen Computern unterstützt werden.

### <a name="visual-studio-c-projects-and-the-build-system"></a>C++-Projekte in Visual Studio und das Buildsystem

**MSBuild.** Visual C++-Projektmappen und -Projekte werden jetzt mithilfe von „MSBuild.exe“ erstellt. Diese Datei ersetzt die Datei „VCBuild.exe“. Bei MSBuild handelt es sich um das flexible, erweiterbare, XML-basierte Buildtool, das auch von den anderen Visual Studio-Sprachen und -Projekttypen verwendet wird. Aufgrund dieser Änderung verwenden C++-Projektdateien in Visual Studio jetzt das XML-Dateiformat und haben die Erweiterung „vcxproj“. C++-Projektdateien in Visual Studio aus früheren Versionen von Visual Studio werden automatisch in das neue Dateiformat konvertiert.

**VC++-Verzeichnisse.** Die Einstellung „VC++-Verzeichnisse“ befindet sich jetzt an zwei verschiedenen Orten. Verwenden Sie die Projekteigenschaftenseiten, um Werte projektbasiert für VC++-Verzeichnisse festzulegen. Verwenden Sie den **Eigenschaften-Manager** und ein Eigenschaftenblatt, um globale Werte für jede Konfiguration von VC++-Verzeichnissen festzulegen.

**Abhängigkeiten zwischen Projekten.** In früheren Releases wurden definierte Abhängigkeiten von Projekten in der Projektmappendatei gespeichert. Wenn diese Projektmappen in das neue Projektdateiformat konvertiert werden, werden Abhängigkeiten in Verweise zwischen Projekten konvertiert. Diese Änderung kann Anwendungen beeinflussen, da sich Konzepte von Projektmappenabhängigkeiten und Abhängigkeiten zwischen Projekten voneinander unterscheiden.

**Makros und Umgebungsvariablen.** Das neue Makro „_ITERATOR_DEBUG_LEVEL“ ruft die Unterstützung des Debuggens für Iteratoren auf. Verwenden Sie dieses Makro anstelle der älteren Makros „_SECURE_SCL“ und „_HAS_ITERATOR_DEBUGGING“.

### <a name="visual-c-libraries"></a>Visual C++-Bibliotheken

**Concurrency Runtime-Bibliotheken.** Das Framework „Concurrency Runtime“ unterstützt Anwendungen und Komponenten, die gleichzeitig ausgeführt werden. Außerdem handelt es sich dabei um das Framework, das zum Programmieren von gleichzeitigen Anwendungen in Visual C++ verwendet wird. Die Parallel Patterns Library (PPL) bietet zur Unterstützung der Programmierung von parallelen Anwendungen allgemeine Container und Algorithmen zum Ausführen der differenzierten Parallelität. Die Bibliothek der asynchronen Agents ist ein akteurbasiertes Programmiermodell und stellt Schnittstellen zum Übergeben von Meldungen für simple Datenfluss- und Pipelineaufgaben bereit.

**C++-Standardbibliothek.** In der folgenden Liste werden viele der Änderungen beschrieben, die an der C++-Standardbibliothek vorgenommen wurden.

- Die neue C++-Sprachfunktion des R-Wert-Verweises wurde verwendet, um Move-Semantiken und die perfekte Weiterleitung für zahlreiche Funktionen in der Standardvorlagenbibliothek zu implementieren. Mithilfe der Move-Semantiken und der perfekten Weiterleitung wird die Leistung der Vorgänge enorm verbessert, in denen Variablen oder Parameter zugeordnet oder zugewiesen werden.
- Außerdem werden Rvalue-Verweise verwendet, um die neue `unique_ptr`-Klasse zu implementieren. Diese Klasse ist im Vergleich zur `auto_ptr`-Klasse ein sichererer intelligenter Zeigertyp. Die `unique_ptr`-Klasse ist zwar verschiebbar, kann jedoch nicht kopiert werden. Sie implementiert eine strenge Besitzsemantik ohne Auswirkungen auf die Sicherheit und funktioniert gut mit Containern zusammen, die rvalue-Verweise beachten. Die `auto_ptr`-Klasse ist veraltet.
- 15 neue Funktionen, z. b `find_if_not` `copy_if` ., und `is_sorted` , wurden dem-Header hinzugefügt \<algorithm> .
- In der \<memory> Kopfzeile ist die neue make_shared-Funktion eine bequeme, robuste und effiziente Möglichkeit, einen freigegebenen Zeiger auf ein Objekt zu erstellen, wenn das Objekt erstellt wird.
- Durch den-Header werden einzeln verknüpfte Listen unterstützt \<forward_list> .
- Die neuen Memberfunktionen `cbegin`, `cend`, `crbegin` und `crend` stellen einen `const_iterator`-Objekt bereit, das sich im Container vorwärts und rückwärts bewegt.
- Der \<system_error> -Header und verwandte Vorlagen unterstützen die Verarbeitung von Systemfehlern auf niedriger Ebene. Member der `exception_ptr`-Klasse können verwendet werden, um Ausnahmen zwischen den Threads zu transportieren.
- Der- \<codecvt> Header unterstützt das umrechnen verschiedener Codierungen von Unicode-Zeichen in andere Codierungen.
- Der- \<allocators> Header definiert mehrere Vorlagen, die dabei helfen, Speicherblöcke für Knoten basierte Container zuzuordnen und freizugeben.
- Der-Header enthält zahlreiche Updates \<random> .

### <a name="microsoft-foundation-class-mfc-library"></a>Microsoft Foundation Class-Bibliotheken

**Windows 7-Features.** MFC unterstützt zahlreiche Features für Windows 7, z.B. die Menüband-Benutzeroberfläche, die Taskleiste, Sprunglisten, Miniaturansichten mit Registerkarten, Miniaturansichten, die Statusanzeige, Symbolüberlagerung und die Suchindizierung. Da MFC automatisch einige Funktionen für Windows 7 unterstützt, müssen Sie Ihre bereits vorhandene Anwendung nicht mehr verändern. Verwenden Sie zur Unterstützung von anderen Features in neuen Anwendungen den MFS-Anwendungsassistenten, um die gewünschte Funktionalität anzugeben.

**Multitouchunterstützung.** MFC unterstützt Anwendungen mit Multitouch-Benutzeroberflächen, also z.B. Anwendungen, die für das Betriebssystem Microsoft Surface geschrieben wurden. Eine Multitouch-Anwendung kann Windows Touch-Nachrichten und Bewegungsnachrichten verarbeiten, die eine Kombination aus verschiedenen Touch-Nachrichten darstellen. Registrieren Sie Ihre Anwendung für Touch- und Bewegungsereignisse. Dann leitet Ihr Betriebssystem Multitouch-Ereignisse an Ihre Ereignishandler weiter.

**Berücksichtigung hoher DPI-Werte.** Standardmäßig unterstützen MFC-Anwendungen jetzt High-DPI. Wenn eine Anwendung High-DPI (Dots per Inch = Punkte pro Zoll) unterstützt, kann das Betriebssystem Fenster, Text und andere Benutzeroberflächenelemente für die aktuelle Bildschirmauflösung skalieren. Das bedeutet, dass bei einem skalierten Bild die Chance größer ist, dass es richtig ausgerichtet und weder beschnitten noch verpixelt dargestellt wird.

**Neustart-Manager.** Der Neustart-Manager speichert Dokumente automatisch ab und startet die Anwendung neu, falls diese unerwartet geschlossen oder neu gestartet wird. Sie können den Neustart-Manager beispielsweise verwenden, um die Anwendung erneut zu starten, nachdem sie durch ein automatisches Update geschlossen wurde. Weitere Informationen zum Konfigurieren der Anwendung für die Verwendung des Neustart-Managers finden Sie **unter Gewusst wie: Hinzufügen der Unterstützung**für den Neustart-Manager.

**CTaskDialog.** Die `CTaskDialog`-Klasse kann anstelle des Standardmeldungsfelds `AfxMessageBox` verwendet werden. Die `CTaskDialog`-Klasse erfasst und mehr Informationen als das Standardmeldungsfeld und zeigt diese an.

#### <a name="safeint-library"></a>SafeInt-Bibliothek

Die neue SafeInt-Bibliothek führt sichere arithmetische Operationen aus, die den Ganzzahlüberlauf berücksichtigen. Diese Bibliothek vergleicht außerdem verschiedene Arten von ganzen Zahlen.

#### <a name="new-active-template-library-atl-macros"></a>Neue Active Template Library-Makros

Der Active Template Library (ATL) wurden neue Makros hinzugefügt, um die Funkionen von „PROP_ENTRY_TYPE“ und „PROP_ENTRY_TYPE_EX“ zu erweitern. Mithilfe von „PROP_ENTRY_INTERFACE“ und „PROP_ENTRY_INTERFACE_EX“ können Sie eine Liste von gültigen CLSIDs hinzufügen. Mithilfe von „PROP_ENTRY_INTERFACE_CALLBACK“ und „PROP_ENTRY_INTERFACE_CALLBACK_EX“ können Sie eine Rückruffunktion angeben, um zu ermitteln, ob eine CLSID gültig ist.

#### <a name="analyze-warnings"></a>/analyze-Warnungen

Die meisten **`/analyze`** Warnungen (Enterprise-Code Analyse) wurden aus den C-Laufzeitbibliotheken (CRT), MFC-und ATL-Bibliotheken entfernt.

#### <a name="animation-and-d2d-support"></a>Animation und D2D-Unterstützung

MFC unterstützt jetzt die Animation und Direct2D-Grafiken. Die MFC-Bibliothek verfügt über einige neue MFC-Klassen und -Funktionen, um diese Funktion zu unterstützen. Es gibt außerdem zwei neue exemplarische Vorgehensweisen, in denen dargestellt wird, wie Sie einem Projekt ein D2D-Objekt und ein Animationsobjekt hinzufügen. **Exemplarische Vorgehensweise: Hinzufügen eines D2D-Objekts zu einem MFC-Projekt** und **Exemplarische Vorgehensweise: Hinzufügen von Animationen zu einem MFC-Projekt**.

### <a name="ide"></a>IDE

**Verbesserung von IntelliSense** IntelliSense für Visual C++ wurde vollständig umgestaltet und ist jetzt schneller, genauer und kann größere Projekte verarbeiten. Damit diese Verbesserungen erzielt werden können, unterscheidet die IDE zwischen der Weise, auf die ein Entwickler Quellcode abruft und verändert, und der, auf die die IDE Quellcode und Projekteinstellungen verwendet, um eine Projektmappe zu erstellen.
Aufgrund dieser Trennung von Aufgaben werden das Durchsuchen von Features wie **Klassenansicht** und das neue Dialogfeld " **Navigieren zu** " von einem System behandelt, das auf einer neuen SQL Server Desktop-Datenbankdatei (. sdf) basiert, die die alte Datei No compile Browse (. NCB) ersetzt. IntelliSense-Features wie QuickInfo, automatische Vervollständigung und die Parameterhilfe analysieren Übersetzungseinheiten nur falls erforderlich. Hybridfunktionen wie das neue Fenster **Aufrufhierarchie** verwenden eine Kombination aus Suchfunktionen und IntelliSense-Features.
Da IntelliSense nur die Informationen verarbeitet, die zum jeweiligen Zeitpunkt erforderlich sind, ist die IDE reaktionsfähiger. Außerdem werden IDE-Ansichten und -Fenster genauer dargestellt, da die Informationen aktueller sind. Zudem können größere Projekte verarbeitet werden, da die IDE-Infrastruktur besser organisiert, leistungsfähiger und skalierbarer ist.

**Verbesserte IntelliSense-Fehlererkennung.** Die IDE kann besser Fehler ermitteln, die einen Verlust von IntelliSense zur Folge hätten, und zeigt rote Wellenlinien unter diesen Fehlern an. Außerdem sendet die IDE IntelliSense-Fehler an das Fenster **Fehlerliste**. Um den Code anzuzeigen, der das Problem verursacht, doppelklicken Sie auf den Fehler im **Fenster Fehlerliste**.

**Feature zur automatischen Vervollständigung für #include-Anweisungen.** Die IDE unterstützt die automatische Vervollständigung für das Schlüsselwort `#include`. Wenn Sie `#include` eingeben, erstellt die IDE ein Dropdown-Listenfeld mit gültigen Headerdateien. Wenn Sie dann den Dateinamen eingeben, filtert die IDE die Liste anhand Ihres Eintrags. Sie können jederzeit die Datei aus der Liste auswählen, die Sie hinzufügen möchten. Dadurch können Sie Dateien schnell hinzufügen, ohne den genauen Dateinamen kennen zu müssen.

**Navigieren Sie zu.** Über das Dialogfeld **Navigieren zu** können Sie alle Symbole und Dateien in Ihrem Projekt suchen, die einer bestimmten Zeichenfolge entsprechen. Es wird nach Suchergebnissen gesucht, während Sie zusätzliche Zeichen in Ihre Suchzeichenfolge eingeben. Im Feedbackfeld **Ergebnisse** sehen Sie die Anzahl der gefundenen Elemente. Darüber können Sie entscheiden, ob Sie Ihre Suche einschränken möchten. Mithilfe der Felder **Art/Bereich**, **Speicherort**und **Vorschau** Feedback können Sie Elemente mit ähnlichen Namen unterscheiden. Ebenso können Sie diese Funktion erweitern, sodass andere Programmiersprachen unterstützt werden.

**Paralleles Debuggen und Profilerstellung.** Der Visual Studio-Debugger beachtet die Concurrency Runtime und unterstützt Sie bei der Behandlung von Problemen mit der Parallelverarbeitung von Anwendungen. Sie können das neue Concurrency-Profilerstellungstool verwenden, um das allgemeine Verhalten Ihrer Anwendung zu visualisieren. Außerdem können Sie neue Toolfenster verwenden, um den Status der Aufgaben und deren Aufruflisten zu visualisieren.

**Menüband-Designer.** Bei dem **Menüband-Designer** handelt es sich um einen grafischen Editor, über den Sie eine MFC-Menübandbenutzeroberfläche erstellen und bearbeiten können. Die endgültige Menüband-Benutzeroberfläche wird von einer XML-basierten Ressourcendatei dargestellt (.mfcribbon-ms). Für vorhandene Anwendungen können Sie die aktuelle Multifunktionsleisten-Benutzeroberfläche erfassen, indem Sie vorübergehend einige Codezeilen hinzufügen und dann den **Menüband-Designer**aufrufen. Nach der Erstellung der Ressourcendatei für das Menüband können Sie Ihren handgeschriebenen Code für die Menüband-Benutzeroberfläche durch einige Anweisungen ersetzen, die die Menübandressource laden.

**Aufrufhierarchie.** Im Fenster **Aufrufhierarchie** können Sie zu allen Funktionen navigieren, die von einer bestimmten Funktion aufgerufen werden, oder zu allen Funktionen, die eine bestimmte Funktion aufrufen.

### <a name="tools"></a>Tools

**MFC-Klassen-Assistent.** Mit Visual C++ 2010 wird das praktische Tool „MFC-Klassenassistent“ wieder eingeführt. Der MFC-Klassenassistent stellt eine praktische Möglichkeit dar, um einem Projekt Klassen, Meldungen und Variablen hinzuzufügen, ohne Quelldateien manuell verändern zu müssen.

**ATL-Steuerelement-Assistent.** Der ATL-Steuerelement-Assistent füllt das Feld `ProgID` nicht mehr automatisch auf. Wenn ein ATL-Steuerelement keine `ProgID` besitzt, können andere Tools möglicherweise nicht damit arbeiten. Beispielsweise verlangt das Dialogfeld **Insert Active Control** (Aktives Steuerelement einfügen), dass Steuerelemente eine `ProgID` aufweisen. Weitere Informationen zum Dialogfeld finden Sie unter [Einfügen von ActiveX](../windows/adding-editing-or-deleting-controls.md#insert-activex-controls)-Steuerelementen.

### <a name="microsoft-macro-assembler-reference"></a>Referenz zum Microsoft Macro Assembler

Neben dem Datentyp „YMMWORD“ werden die 256-Bit-Multimediaoperanden unterstützt, die in den Anweisungen zu den Intel Advanced Vector Extensions (AVX) enthalten sind.

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Neuerungen bei C++ in Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Integrierte Entwicklungsumgebung (IDE) von Visual C++

- Dialogfelder, die in ATL-, MFC- und Win32-Anwendungen erstellt werden, sind jetzt mit den Stilrichtlinien für Windows Vista konform. Wenn Sie mithilfe von Visual Studio 2008 ein neues Projekt erstellen, sind alle Dialogfelder, die Sie in Ihre Anwendung einfügen, konform mit den Stilrichtlinien für Windows Vista. Wenn Sie ein Projekt erneut kompilieren wollen, das Sie mit einer früheren Version von Visual Studio erstellt haben, werden alle bereits vorhandenen Dialogfelder genauso dargestellt wie in früheren Versionen. Weitere Informationen zum Einfügen von Dialogfeldern in Ihre Anwendungen finden Sie unter **Dialog-Editor**.

- Der **ATL-Projekt-Assistent** verfügt jetzt über eine Option zum Registrieren von Komponenten für alle Benutzer. Ab Visual Studio 2008 werden die COM-Komponenten und Typbibliotheken, die vom **ATL-Projekt** -Assistenten erstellt werden, im Knoten "HKEY_CURRENT_USER" der Registrierung registriert, es sei denn, Sie wählen die Option " **Komponente für alle Benutzer registrieren" aus**.
- Der **ATL-Projekt-Assistent **stellt keine Option mehr bereit, um attributierte ATL-Projekte zu erstellen. Ab Visual Studio 2008 bietet der **ATL-Projekt-Assistent** keine Option mehr zum Ändern des attributierten Status eines neuen Projekts. Alle ATL-Projekte, die der Assistent neu erstellt, sind jetzt nicht mehr attributiert.
- Das Schreiben in die Registrierung kann umgeleitet werden. Ab der Einführung von Windows Vista musste ein Programm im Modus mit erhöhten Rechten ausgeführt werden, damit in bestimmte Bereiche der Registrierung geschrieben werden konnte. Visual Studio sollte nicht permanent im Modus mit erhöhten Rechten ausgeführt werden. Über die Umleitung pro Benutzer werden Registrierungsschreibvorgänge automatisch ohne Änderungen der Programmierung von „HKEY_CLASSES_ROOT“ an „HKEY_CURRENT_USER“ weitergeleitet.
- Der **Klassen-Designer** verfügt jetzt über die eingeschränkte Unterstützung für nativen C++-Code. In früheren Versionen von Visual Studio funktionierte der **Klassen-Designer** nur mit Visual c# und Visual Basic. C++-Benutzer können jetzt zwar den **Klassen-Designer** verwenden, jedoch nur im schreibgeschützten Modus. Weitere Informationen zum Verwenden der **Klassen-Designer** mit C++ finden Sie unter **Arbeiten mit Visual C++ Code in Klassen-Designer**.
- Im Projektassistenten ist keine Option mehr enthalten, mit der Sie ein SQL Server-Projekt in C++ erstellen können. Ab Visual Studio 2008 bietet der Assistent für neue Projekte keine Option zum Erstellen eines C++ SQL Server-Projekts. SQL Server-Projekte, die mit einer früheren Version von Visual Studio erstellt wurde, werden dennoch kompiliert und funktionieren ordnungsgemäß.

### <a name="visual-c-libraries"></a>Visual C++-Bibliotheken

#### <a name="general"></a>Allgemein

- Anwendungen können an bestimmte Versionen von C++-Bibliotheken gebunden sein. In einigen Fällen sind Anwendungen von Updates abhängig, die für die Visual C++-Bibliotheken nach einem Release veröffentlicht wurden. Dann kann ein unerwartetes Verhalten auftreten, wenn eine Anwendung auf einem Computer ausgeführt wird, auf dem frühere Versionen der Bibliotheken gespeichert sind. Sie können jetzt Anwendungen an eine bestimmte Bibliotheksversion bilden, sodass diese nicht auf Computern ausgeführt wird, auf denen frühere Versionen der Bibliotheken gespeichert sind.

#### <a name="stlclr-library"></a>STL/CLR-Bibliothek

- Visual C++ enthält jetzt die STL/CLR-Bibliothek. Die STL/CLR-Bibliothek ist ein Paket der Standard Template Library (STL), einer Teilmenge der C++-Standardbibliothek, die mit C++ und der Common Language Runtime (CLR) von .NET Framework eingesetzt werden kann. Mit STL/CLR können Sie jetzt alle Container, Iteratoren und Algorithmen der STL in einer verwalteten Umgebung verwenden.

#### <a name="mfc-library"></a>MFC-Bibliothek

- Unter Windows Vista werden allgemeine Steuerelemente unterstützt. Mehr als 150 Methoden in 18 neuen oder vorhandenen Klassen wurden hinzugefügt, um Features unter Windows Vista hinzuzufügen oder die Features in aktuellen MFC-Klassen zu verbessern.
- Mithilfe der neuen `CNetAddressCtrl`-Klasse können Sie IPv4- und IPv6-Adressen oder DNS-Namen eingeben und überprüfen.
- Mithilfe der neuen `CPagerCtrl`-Klasse wird die Verwendung des Windows-Pagersteuerelements vereinfacht.
- Mithilfe der neuen `CSplitButton`-Klasse wird die Verwendung des SplitButton-Steuerelements vereinfacht, über das Sie eine Standardaktion oder eine optionale Option auswählen.

#### <a name="c-support-library"></a>C++-Unterstützungsbibliothek

- Mit C++ werden Marshallingbibliotheken eingeführt. Die Marshallingbibliothek bietet eine einfache und optimierte Möglichkeit, Daten zwischen nativen und verwalteten Umgebungen zu marshallen. Die Bibliothek stellt eine Alternative zu komplexeren und weniger effizienten Ansätzen wie PInvoke dar. Weitere Informationen finden Sie **unter Übersicht über** das Marshalling in C++.

#### <a name="atl-server"></a>ATL-Server

- ATL-Server wird als freigegebenes Quellprojekt veröffentlicht.
- Ein großer Bestandteil der Codebasis von ATL-Server wurde als freigegebenes Quellcodeprojekt auf CodePlex veröffentlicht und wird nicht als Teil von Visual Studio 2008 installiert. Mehrere Dateien, die mit ATL-Server verknüpft sind, gehören nicht mehr zu Visual Studio. Die Liste der entfernten Dateien finden Sie unter **entfernte ATL-Server Dateien**.
- Die Klassen zur Datencodierung und -decodierung „atlenc.h“ und die Hilfsfunktionen und -klassen in „atlutil.h“ und „atlpath.h“ sind jetzt Bestandteil der ATL-Bibliothek.
- Microsoft unterstützt weiterhin ATL-Server-Versionen, die in älteren Releases von Visual Studio enthalten sind, solange diese Visual Studio-Versionen unterstützt werden. CodePlex entwickelt weiterhin ATL-Server-Code als Communityprojekt. Microsoft unterstützt keine CodePlex-Version von ATL-Server mehr.

### <a name="visual-c-compiler-and-linker"></a>Visual C++-Compiler und -Linker

#### <a name="compiler-changes"></a>Compileränderungen

- Der Compiler unterstützt verwaltete inkrementelle Builds. Wenn Sie diese Option angeben, kompiliert der Compiler keinen Code erneut, wenn eine Referenzassembly verändert wird. Stattdessen wird ein inkrementeller Build durchgeführt. Dateien werden nur erneut kompiliert, wenn Änderungen Auswirkungen auf den abhängigen Code haben.
- Attribute, die im Zusammenhang mit dem ATL-Server stehen, werden nicht mehr unterstützt. Der Compiler unterstützt einige Attribute nicht mehr, die direkt mit dem ATL-Server im Zusammenhang stehen. Weitere Informationen zu einer vollständigen Liste der entfernten Attribute finden Sie unter „Breaking Changes (Fehler verursachende Änderungen)“.
- Der Compiler unterstützt die Mikroarchitektur „Intel Core“. Der Compiler optimiert die Mikroarchitektur „Intel Core“ bei der Codegenerierung. Standardmäßig ist diese Optimierung aktiviert und kann nicht deaktiviert werden, da sie Pentium 4 und andere Prozessoren unterstützt.
- Intrinsische Funktionen unterstützen neue AMD- und Intel-Prozessoren. Einige neue intrinsische Anweisungen unterstützen ein höheres Maß an Funktionalität in aktuelleren AMD- und Intel-Prozessoren. Weitere Informationen zu den neuen systeminternen Funktionen finden Sie unter **Ergänzende Streaming SIMD Extensions 3-Anweisungen**, **Streaming SIMD Extensions 4-Anweisungen**, systeminterne Funktionen für **SSE4A und erweiterte Bitmanipulation**, systeminterne **AES**-Funktionen, **_mm_clmulepi64_si128**und **__rdtscp**.
- Die `__cpuid`-Funktion wurde aktualisiert. Die Funktionen `__cpuid` und `__cpuidex` unterstützen jetzt einige neue Features der letzten Überarbeitungen von AMD- und Intel-Prozessoren. Das intrinsische Funktion `__cpuidex` ist neu und erfasst weitere Informationen von neueren Prozessoren.
- Die Compileroption `/MP` reduzierte die Gesamtdauer des Buildvorgangs. Die Option `/MP` kann die Gesamtzeit deutlich reduzieren, damit mehrere Quelldateien kompiliert werden können, indem mehrere Prozesse erstellt werden, in denen Dateien gleichzeitig kompiliert werden. Diese Option ist besonders auf Computern nützlich, die das Hyperthreading, mehrere Prozessoren oder mehrere Kerne unterstützen.
- Die `/Wp64` Compileroption und das- **`__w64`** Schlüsselwort sind veraltet. Die `/Wp64` Compileroption und das- **`__w64`** Schlüsselwort, die 64-Bit-Portabilitäts Probleme erkennen, sind veraltet und werden in einer zukünftigen Version des Compilers entfernt. Verwenden Sie anstelle dieser Compileroption und des Schlüsselworts einen Microsoft Visual C++-Compiler, der eine 64-Bit-Plattform als Ziel verwendet.
- `/Qfast_transcendentals` generiert Inlinecode für transzendentale Funktionen.
- `/Qimprecise_fwaits` entfernt die internen fwait-Befehle, um Blöcke zu testen, wenn Sie die Compileroption `/fp:except` verwenden.

### <a name="linker-changes"></a>Änderungen am Linker

- Informationen zur Benutzerkontensteuerung sind jetzt über den Visual C++-Linker („link.exe“) in Manifestdateien für ausführbare Dateien eingebettet. Dieses Feature ist standardmäßig aktiviert. Weitere Informationen zum Deaktivieren dieser Funktion oder zum Ändern des Standardverhaltens finden Sie unter `/MANIFESTUAC` (Einbetten von UAC-Informationen in Manifeste).
- Der Linker verfügt jetzt über die Option `/DYNAMICBASE` zur Aktivierung der Windows Vista-Funktion „Address Space Layout Randomization“ (Zufällige Anordnung des Layouts des Adressraums). Diese Option ändert den Header einer ausführbaren Datei, um anzugeben, ob für die Anwendung nach dem Zufallsprinzip zur Ladezeit ein Rebase ausgeführt werden soll.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Neuerungen bei C++ in Visual Studio 2005

Die folgenden Features wurden in Visual C++ 2005 Service Pack 1 neu hinzugefügt:

### <a name="intrinsics-for-x86-and-x64"></a>Intrinsische Funktionen für x86 und x64

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>Intrinsische Funktionen ausschließlich für x64

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Neue Sprachschlüsselwörter

__sptr, __uptr

### <a name="new-compiler-features"></a>Neue Compilerfeatures

In diesem Release sind bedeutende Änderungen des Compilers enthalten.

- Native 64-Bit-Compiler und Cross-Compiler.
- Die `/analyze`-Compileroption (Enterprise-Codeanalyse) wurde hinzugefügt.
- Die `/bigobj`-Compileroption wurde hinzugefügt.
- `/clr:pure`, `/clr:safe` und `/clr:oldSyntax` wurden hinzugefügt. (Dies wurde später in Visual Studio 2015 als veraltet markiert und in Visual Studio 2017 entfernt.)
- Veraltete Compileroptionen: Viele Compileroptionen wurden in diesem Release als veraltet gekennzeichnet. Weitere Informationen finden Sie unter **Deprecated Compiler Options (Veraltete Compileroptionen)**.
- Das doppelte Thunking in `/clr`-Code wurde reduziert. Weitere Informationen finden Sie unter **Doppeltes Thunking (C++)**.
- `/EH` (Ausnahmebehandlungsmodell) oder `/EHs` können nicht mehr verwendet werden, um eine Ausnahme zu erfassen, die mit einer anderen Funktion als mit „Throw“ ausgelöst wird. Verwenden Sie stattdessen `/EHa`.
- Die `/errorReport`-Compileroption (Interne Compilerfehler melden) wurde hinzugefügt.
- Die `/favor`-Compileroption (Optimierung für 64) wurde hinzugefügt.
- Die Compileroptionen `/FA` und `/Fa` (Listendatei) wurden hinzugefügt.
- Die `/FC`-Compileroption (Vollständiger Pfad der Quellcodedatei in Diagnose) wurde hinzugefügt.
- Die `/fp`-Compileroption (Festlegen des Gleitkommaverhaltens) wurde hinzugefügt.
- Die `/G`-Compileroption (Optionen zum Optimieren für Prozessoren) wurde hinzugefügt.
- Die `/G`-Compileroption (Optionen zum Optimieren für Prozessoren) wurde hinzugefügt.
- Die Compileroptionen `/G3`, `/G4`, `/G5`, `/G6`, `/G7`, und `/GB` wurden entfernt. Der Compiler verwendet eine Füllmethode, die versucht, die beste Ausgabedatei für alle Architekturen zu erstellen.
- `/Gf` wurde entfernt. Verwenden Sie stattdessen `/GF` (Doppelte Zeichenfolgen beseitigen).
- `/GL` (Optimierung des gesamten Programms) ist jetzt mit `/CLRHEADER` kompatibel.
- `/GR` ist jetzt standardmäßig aktiviert.
- `/GS` (Puffer-Sicherheitsüberprüfung) stellt jetzt einen Sicherheitsschutz für anfällige Zeigerparameter dar. `/GS` ist jetzt standardmäßig aktiviert. `/GS` funktioniert jetzt auch für Funktionen, die für MSIL mit `/clr` (Common Language Runtime-Kompilierung) kompiliert werden.
- Die `/homeparams`-Compilerfunktion (Registerparameter in den Stapel kopieren) wurde hinzugefügt.
- Die `/hotpatch`-Compilerfunktion (Hotpatchfähiges Image erstellen) wurde hinzugefügt.
- Die Heuristik der Inline Funktion wurde aktualisiert. **`inline`** Weitere Informationen finden Sie unter, **`__inline`** **`__forceinline`** und **inline_depth** .
- Viele neue intrinsische Funktionen wurden hinzugefügt, und viele zuvor nicht dokumentierte intrinsische Funktionen werden jetzt dokumentiert.
- Standardmäßig löst jeder fehlgeschlagene Aufruf von „New“ (Neu) eine Ausnahme aus.
- Die Compileroptionen `/ML` und `/MLd` wurden entfernt. Visual C++ unterstützt nicht mehr die statisch verknüpfte Singlethread-CRT-Bibliothek.
- Mit dem Compiler wird die Optimierung von benannten Rückgabewerten implementiert, die aktiviert wird, wenn Sie mit `/O1`, `/O2` (Größe minimieren, Geschwindigkeit maximieren), `/Og` (globale Optimierung) und `/Ox` (Komplette Optimierung) kompiliert werden.
- Die `/Oa`-Compileroption wurde entfernt und wird stillschweigend ignoriert. Verwenden Sie die Modifizierer `noalias` oder `restrict__declspec`, um anzugeben, wie der Compiler beim Aliasing vorgeht.
- Die `/Op`-Compileroption wurde entfernt. Verwenden Sie stattdessen `/fp` (Gleitkommaverhalten festlegen).
- „OpenMP“ wird jetzt von Visual C++ unterstützt.
- Die `/openmp`-Compileroption (Aktivieren der OpenMP 2.0-Unterstützung) wurde hinzugefügt.
- Die `/Ow`-Compileroption wurde entfernt und wird stillschweigend ignoriert. Verwenden Sie die Modifizierer `noalias` oder `restrict__declspec`, um festzulegen, wie der Compiler beim Aliasing vorgehen soll.

### <a name="profile-guided-optimizations"></a>Profilgesteuerte Optimierungen (PGO)

- `/QI0f` wurde entfernt.
- `/QIfdiv` wurde entfernt.
- Die `/QIPF_B`-Compileroption (Errata für B-CPU-Stepping) wurde hinzugefügt.
- Die `/QIPF_C`-Compileroption (Errata für C-CPU-Stepping) wurde hinzugefügt.
- Die `/QIPF_fr32`-Compileroption (Obere 96 Gleitkommaregister nicht verwenden) wurde hinzugefügt.
- Die `/QIPF_noPIC`-Compileroption (Erzeugen von positionsabhängigem Code) wurde hinzugefügt.
- Die `/QIPF_restrict_plabels`-Compileroption (Annahme, dass keine Funktionen während der Laufzeit erstellt werden) wurde hinzugefügt.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Unicode-Unterstützung im Compiler und Linker

- Mithilfe von `/vd` (Konstruktionsverschiebungen deaktivieren) können Sie jetzt den dynamic_cast-Operator beim Erstellen eines Objekts hinzufügen (/vd2).
- Die `/YX`-Compileroption wurde entfernt. Verwenden Sie stattdessen `/Yc` (Vorkompilierte Headerdatei erstellen) oder `/Yu` (Vorkompilierte Headerdatei verwenden). Wenn Sie `/YX` aus Ihren Buildkonfigurationen entfernen und nicht ersetzen, können dadurch die Buildvorgänge beschleunigt werden.
- `/Zc:forScope` ist jetzt standardmäßig aktiviert.
- `/Zc:wchar_t` ist jetzt standardmäßig aktiviert.
- Die `/Zd`-Compileroption wurde entfernt. Debugginginformationen für ausschließlich Zeilennummern werden nicht mehr unterstützt. Verwenden Sie stattdessen `/Zi`. Weitere Informationen finden Sie unter **/Z7, /Zi, /ZI (Debuginformationsformat)**.
- `/Zg` ist jetzt nur noch für C-Quellcodedateien und nicht für C++-Quellcodedateien verfügbar.
- Die `/Zx`-Compileroption (Optimierten Itaniumcode debuggen) wurde hinzugefügt.

### <a name="new-language-features"></a>Neue Sprachfeatures

- Das attribute-Attribut ist jetzt als veraltet markiert.
- Der `appdomain__declspec`-Modifizierer wurde hinzugefügt.
- Die `__clrcall`-Aufrufkonvention wurde hinzugefügt.
- Mithilfe des veralteten (C++) **declspec**-Modifizierers können Sie jetzt eine Zeichenfolge angeben, die zur Kompilierzeit angezeigt wird, wenn ein Benutzer auf eine veraltete Klasse oder Funktion zugreifen will.
- **`dynamic_cast`** Der Operator weist wichtige Änderungen auf.
- Mithilfe von nativen Enumerationen können Sie jetzt den zugrunde liegenden Typ angeben.
- Der `jitintrinsicdeclspec`-Modifizierer wurde hinzugefügt.
- Der `noaliasdeclspec`-Modifizierer wurde hinzugefügt.
- Der `process__declspec`-Modifizierer wurde hinzugefügt.
- **abstract**, **override** und **sealed** können für die native Kompilierung verwendet werden.
- **`__restrict`** Das Schlüsselwort wurde hinzugefügt.
- Der `restrictdeclspec`-Modifizierer wurde hinzugefügt.
- **`__thiscall`** ist jetzt ein Schlüsselwort.
- **`__unaligned`** Das Schlüsselwort ist jetzt dokumentiert.
- **`volatile`** (C++) hat in Bezug auf Optimierungen ein aktualisiertes Verhalten.

### <a name="new-preprocessor-features"></a>Neue Präprozessorfeatures

- Das vordefinierte __CLR_VER-Makro wurde hinzugefügt.
- Das comment-Pragma (C/C++) akzeptiert jetzt `/MANIFESTDEPENDENCY` als Linkerkommentar. Die exestr-Kommentarfunktion wurde als veraltet markiert.
- Das `embedded_idl`-Attribut (`#import`-Anweisung) verwendet jetzt einen optionalen Parameter.
- `fenv_access`-Pragma
- `float_control`-Pragma
- `fp_contract`-Pragma
- Globale Variablen werden nicht in der Reihenfolge initialisiert, in der sie deklariert werden, wenn Sie über globale Variablen in von Pragma verwalteten bzw nicht von Pragma verwalteten und nicht verwalteten Abschnitten verfügen. Dabei handelt es sich um eine möglicherweise bedeutungsvolle Änderung. Beispielsweise wird eine nicht verwaltete globale Variable mit verwalteten globalen Variablen initialisiert und ein vollständig konstruiertes verwaltetes Objekt ist erforderlich.
- Mit „init_seg“ festgelegte Abschnitte sind jetzt schreibgeschützt und können nicht wie in den Vorgängerversionen bearbeitet werden.
- Der inline_depth-Standard ist jetzt 16. Der Standard von 16 galt auch in Visual C++ .NET 2003.
- Das vordefinierte _INTEGRAL_MAX_BITS-Makro wurde hinzugefügt. Weitere Informationen finden Sie unter „Predefined Macros (Vordefinierte Makros)“.
- Die vordefinierten Makros „_M_CEE“, „_M_CEE_PURE“ und „_M_CEE_SAFE“ wurden hinzugefügt. Weitere Informationen finden Sie unter „Predefined Macros (Vordefinierte Makros)“.
- Das vordefinierte _M_IX86_FP-Makro wurde hinzugefügt.
- Das vordefinierte _M_X64-Makro wurde hinzugefügt.
- `make_public`-Pragma
- Die Pragmasyntax `managed`,`unmanaged` wurde aktualisiert und verfügt jetzt über `push` und `pop`.
- Auf „mscorlib.dll“ wird jetzt implizit von der `#using`-Anweisung in sämtlichen `/clr`-Kompilierungen verwiesen.
- Das vordefinierte _OPENMP-Makro wurde hinzugefügt.
- „optimize“-Pragma wurde aktualisiert, „a“ und „w“ gelten nicht mehr als gültige Parameter.
- Das no_registry#import-Attribut wurde hinzugefügt.
- Die Pragmas `region` und `endregion` wurden hinzugefügt.
- Das vordefinierte _VC_NODEFAULTLIB-Makro wurde hinzugefügt.
- Variadic-Makros sind jetzt implementiert.
- `vtordisp` ist veraltet und wird in einem der nächsten Releases von Visual C++ entfernt.
- Das `warning`-Pragma verfügt jetzt über den suppress-Spezifizierer.

### <a name="new-linker-features"></a>Neue Linker-Features

- Module (MSIL-Ausgabedateien, die keiner Assembly angehören) sind jetzt als Eingabe für den Linker zulässig.
- Die `/ALLOWISOLATION`-Linkeroption (Manifestsuche) wurde hinzugefügt.
- `/ASSEMBLYRESOURCE` (Verwaltete Ressource einbetten) wurde aktualisiert, und Sie können jetzt den Namen der Ressource in der Assembly angeben und angeben, dass die Ressource privat ist.
- Die `/CLRIMAGETYPE`-Linkeroption (Angeben des CLR-Bildtyps) wurde hinzugefügt.
- Die `/CLRSUPPORTLASTERROR`-Linkeroption (Letzten Fehlercode für PInvoke-Aufrufe beibehalten) wurde hinzugefügt.
- Die `/CLRTHREADATTRIBUTE`-Linkeroption (Festlegen des CLR-Threadattributs) wurde hinzugefügt.
- Die `/CLRUNMANAGEDCODECHECK`-Linkeroption (SuppressUnmanagedCodeSecurityAttribute hinzufügen) wurde hinzugefügt.
- Die `/ERRORREPORT`-Linkeroption (Weiterleiten von internen Linkerfehlern) wurde hinzugefügt.
- Die `/EXETYPE`-Linkeroption wurde entfernt. Der Linker unterstützt das Erstellen von Gerätetreibern für Windows 95 und Windows 98 nicht mehr. Verwenden Sie eine geeignete DDK zum Erstellen dieser Gerätetreiber. Das EXETYPE-Schlüsselwort ist für Moduldefinitionsdateien nicht mehr gültig.
- Die `/FUNCTIONPADMIN`-Linkeroption (Erstellen eines Hotpatch-fähigen Images) wurde hinzugefügt.
- Die `/LTCG`-Linkeroption wird jetzt für mit `/clr` kompilierten Modulen unterstützt. `/LTCG` wurde außerdem aktualisiert, um die profilgesteuerte Optimierung zu unterstützen.
- Die `/MANIFEST`-Linkeroption (Paralleles Assemblymanifest erstellen) wurde hinzugefügt.
- Die `/MANIFESTDEPENDENCY`-Linkeroption (Manifestabhängigkeiten angeben) wurde hinzugefügt.
- Die `/MANIFESTFILE`-Linkeroption (Benennen der Manifestdatei) wurde hinzugefügt.
- Die `/MAPINFO:LINES`-Linkeroption wurde entfernt.
- Die `/NXCOMPAT`-Linkeroption (Kompatibel mit der Datenausführungsverhinderung) wurde hinzugefügt.
- Die `/PGD`-Linkeroption (Datenbank für profilgesteuerte Optimierungen festlegen) wurde hinzugefügt.
- Die `/PROFILE`-Linkeroption (Leistungstoolsprofiler) wurde hinzugefügt.
- Die `/SECTION`-Linkeroption (Abschnittsattribute festlegen) unterstützt jetzt zwar die Attributnegation, aber die Attribute „L“ oder „D“ (VxD-bezogen) werden nicht mehr unterstützt.
- Unicode-Unterstützung im Compiler und Linker
- Die `/VERBOSE`-Linkeroption (Meldungen zum Ausgabefortschritt) akzeptiert jetzt auch ICF und REF.
- Die `/VXD`-Linkeroption wurde entfernt. Der Linker unterstützt das Erstellen von Gerätetreibern für Windows 95 und Windows 98 nicht mehr. Verwenden Sie eine geeignete DDK zum Erstellen dieser Gerätetreiber. Das VXD-Schlüsselwort ist für Moduldefinitionsdateien nicht mehr gültig.
- Die `/WS`-Linkeroption wurde entfernt. `/WS` wurde verwendet, um Images zu verändern, die von Windows NT 4.0 als Ziel verwendet werden. „IMAGECFG.exe“: Anstelle von `/WS` können jetzt R-Dateinamen verwendet werden. „IMAGECFG.exe“ befindet sich jetzt auf der Windows NT 4.0 CD-ROM in „SUPPORT\DEBUG\I386\IMAGECFG.EXE“.
- Die `/WX`-Linkeroption (Linkerwarnungen als Fehler behandeln) wird jetzt dokumentiert.

### <a name="new-linker-utility-features"></a>Neue Features des Linker-Hilfsprogramms

- Die `/ALLOWISOLATION`-editbin-Option wurde hinzugefügt.
- Die DESCRIPTION-Moduldefinitionsanweisungen für Dateien wurde entfernt. Der Linker unterstützt das Erstellen von virtuellen Gerätetreibern nicht mehr.
- Die `/ERRORREPORT`-Option wurde zu „bscmake.exe“, „dumpbin.exe“, „editbin.exe“ und „lib.exe“ hinzugefügt.
- Die `/LTCG`-Liboption wurde hinzugefügt.
- Die `/NXCOMPAT`-editbin-Liboption wurde hinzugefügt.
- Die `/RANGE`-dumpbin-Option wurde hinzugefügt.
- Die `/TLS`-dumpbin-Option wurde hinzugefügt.
- Die `/WS`-editbin-Option wurde entfernt. `/WS` wurde verwendet, um Images zu verändern, die von Windows NT 4.0 als Ziel verwendet werden. „IMAGECFG.exe“: Anstelle von `/WS` können jetzt R-Dateinamen verwendet werden. „IMAGECFG.exe“ befindet sich jetzt auf der Windows NT 4.0 CD-ROM in „SUPPORT\DEBUG\I386\IMAGECFG.EXE“.
- Die /WX[:NO]-lib-Option wurde hinzugefügt.

### <a name="new-nmake-features"></a>Neue NMAKE-Features

- `/ERRORREPORT` wurde hinzugefügt.
- `/G` wurde hinzugefügt.
- Die vordefinierten Regeln wurden aktualisiert.
- Das $(MAKE)-Makro, das in Rekursionsmakros dokumentiert wird, gibt jetzt den vollständigen Pfad zu „nmake.exe“ an.

### <a name="new-masm-features"></a>Neue MASM-Features

- MASM-Ausdrücke sind jetzt 64-Bit-Werte. In Vorgängerversionen hat es sich bei den MASM-Ausdrücken um 32-Bit-Werte gehandelt.
- Die Anweisung „__asm int 3“ bewirkt jetzt, dass eine Funktion in nativen Code kompiliert wird.
- ALIAS (MASM) wird jetzt dokumentiert.
- Die `/ERRORREPORT`-Optionen „ml.exe“ und „ml64.exe“ wurden hinzugefügt.
- .FPO wird jetzt dokumentiert.
- „H2INC.exe“ wird in Visual C++ 2005 nicht veröffentlicht. Wenn Sie „H2INC“ weiterhin verwenden müssen, verwenden Sie „H2INC.exe“ aus einer Vorgängerversion von Visual C++.
- Operator IMAGEREL wurde hinzugefügt.
- Operator HIGH32 wurde hinzugefügt.
- Operator LOW32 wurde hinzugefügt.
- „ml64.exe“ ist eine Version von MASM für die x64-Architektur. Die Datei fasst x64-ASM-Dateien in x64-Objektdateien zusammen. Die Inlineassemblysprache wird im x64-Compiler nicht unterstützt. Die folgenden MASM-Anweisung wurden für „ml64.exe“ (x64) hinzugefügt.
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- Neben .SETFRAME wurde auch die PROC-Anweisung mit einer Syntax aktualisiert, die sich nur auf x64 bezieht.
- Die MMWORD-Anweisung wurde hinzugefügt.
- `/omf` (Befehlszeilenoption „ML.exe“) impliziert jetzt `/c`. „ML.exe“ unterstützt nicht die Verknüpfung von OMF-Formatobjekten.
- Die SEGMENT-Anweisung unterstützt jetzt zusätzliche Attribute.
- Der Operator SECTIONREL wurde hinzugefügt.
- Die XMMWORD-Anweisung wurde hinzugefügt.

### <a name="new-crt-features"></a>Neue CRT-Features

- Sichere Versionen verschiedener Funktionen wurden hinzugefügt. Diese Funktionen bieten eine verbesserte Möglichkeit zur Verarbeitung von Fehlern und erzwingen strenge Kontrollen für Puffer, um häufig auftretende Sicherheitsmängel zu vermeiden. Die neuen sicheren Versionen werden durch das Suffix **_s** markiert.
- Vorhandene Versionen vieler Funktionen mit geringerer Sicherheit wurden als veraltet gekennzeichnet. Definieren Sie „_CRT_SECURE_NO_WARNINGS“, um die Ablaufwarnungen zu deaktivieren.
- Viele bereits vorhandene Funktionen überprüfen jetzt ihre jeweiligen Parameter und rufen den ungültigen Parameterhandler auf, wenn ein ungültiger Parameter übergeben wird.
- Viele bereits vorhandene Funktionen legen jetzt an neuen Stellen `errno` fest.
- Die Typdefinition `errno_t` wurde zusammen mit einem Typinteger hinzugefügt. `errno_t` wird immer dann verwendet, wenn ein Rückgabetyp oder ein Parameter einer Funktion Fehlercodes von `errno` verarbeitet. `errno_t` ersetzt `errcode`.
- Es gibt jetzt Versionen von gebietsschemaabhängigen Funktionen, die das Gebietsschema als Parameter anstelle des aktuellen Gebietsschemas verwenden. Diese neuen Funktionen haben das Suffix **_l**. Es wurden einige neue Funktionen hinzugefügt, die mit Gebietsschemaobjekten zusammenarbeiten. Die neuen Funktionen `_get_current_locale`, `_create_locale` und `_free_locale` wurden hinzugefügt.
- Neue Funktionen wurden hinzugefügt, um das Sperren und Entsperren von Dateihandles zu unterstützen.
- Die `_spawn`-Familie der Funktionen setzt „errno“ nicht wie in früheren Versionen erfolgreich auf 0 (null) zurück.
- Versionen der `printf`-Familie der Funktionen sind verfügbar, mit deren Hilfe Sie die Reihenfolge festlegen können, in der die Argumente verwendet werden sollen.
- Das Textformat „Unicode“ wird jetzt unterstützt. Die Funktion `_open` unterstützt die Attribute „_O_TEXTW“, „_O_UTF8“ und „_O_UTF16“. Die `fopen`-Funktion unterstützt die Methode „ccs=ENCODING“ zum Angeben eines Unicode-Formats.
- Eine neue Version der CRT-Bibliotheken, die in verwaltetem Code erstellt werden, ist jetzt verfügbar und wird verwendet, wenn mit der`/clr`-Option (Common Language Runtime-Kompilierung) ein Kompilierungsvorgang durchgeführt wird.
- „_fileinfo“ wurde entfernt.
- `time_t` hat jetzt standardmäßig eine Größe von 64 Bit. Dadurch wird der Bereich von `time_t`und einigen weiteren Zeitfunktionen bis ins Jahr 3000 ausgeweitet.
- CRT unterstützt jetzt das Festlegen eines Gebietsschemas auf Threadbasis. Die `_configthreadlocale`-Funktion wurde hinzugefügt, um dieses Feature zu unterstützten.
- Die Funktionen `_statusfp2` und `__control87_2` wurden hinzugefügt, um Zugriff auf und Kontrolle über das Gleitkommasteuerwort auf dem x87- und SSE2-Gleitkommaprozessor zu gewähren.
- Die Funktionen `_mkgmtime` und `_mkgmtime64` wurden hinzugefügt, um Unterstützung für die Konvertierung der Zeitangaben (tm-Struktur) in Greenwich Mean Time (GMT) bereitzustellen.
- An `swprintf` und `vswprintf` wurden Änderungen vorgenommen, um die Standards einzuhalten.
- Über eine neue Headerdatei (INTRIN.H) werden Prototypen für einige intrinsische Funktionen bereitgestellt.
- Die `fopen`-Funktion verfügt jetzt über ein N-Attribut.
- Die `_open`-Funktion verfügt jetzt über ein _O_NOINHERIT-Attribut.
- Die `atoi`-Funktion gibt jetzt „INT_MAX“ zurück und legt im Falle eines Überlaufs `errno` auf „ERANGE“ fest. In früheren Versionen war das Überlaufverhalten nicht definiert.
- Die `printf`-Familie unterstützt die Ausgabe von Hexadezimalgleitkommawerten, die gemäß dem ANSI C99-Standard mithilfe der Formattypspezifizierer „%a“ und „%A“ implementiert wurden.
- Die `printf`-Familie unterstützt jetzt das Größenpräfix „ll“ (long long).
- Die `_controlfp`-Funktion wurde optimiert, um die Leistung zu verbessern.
- Debugversionen einiger Funktionen wurden hinzugefügt.
- `_chgsignl` und `_cpysignl`wurden hinzugefügt (long double-Versionen).
- Der `_locale_t`-Typ wurde der Typtabelle hinzugefügt.
- Das neue `_countof`-Makro wurde zur Berechnungen der Anzahl der Elemente in einem Array hinzugefügt.
- Zu jedem Funktionsthema wurde ein Abschnitt zu .NET Framework-Äquivalenten hinzugefügt.
- Mehrere Zeichen folgen Funktionen haben jetzt die Möglichkeit, Zeichen folgen zu kürzen, anstatt einen Fehler zu haben, wenn Ausgabepuffer zu klein sind. siehe **_TRUNCATE**.
- `_set_se_translator` erfordert jetzt die Verwendung der `/EHa`-Compileroption.
- `fpos_t` befindet sich jetzt **`__int64`** unter `/Za` (für C-Code) und wenn __stdc__ manuell festgelegt wird (für C++-Code). Dabei handelt es sich um eine **`struct`** .
- „_CRT_DISABLE_PERFCRIT_LOCKS“ kann die E/A-Leistung von Programmen mit einem Thread verbessern.
- POSIX-Namen wurden als veraltet markiert und durch ISO-konforme C++-Namen ersetzt (verwenden Sie z.B. `_getch` anstelle von `getch`).
- Neue Linkoptionen für OBJ-Dateien sind im reinen Modus verfügbar.
- `_recalloc` kombiniert Features von `realloc` und `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Neuerungen bei C++ in Visual Studio 2003

### <a name="compiler"></a>Compiler

- Informationen zum Ausführen einer Managed Extensions for C++-Anwendung, die mit dem Compiler der aktuellen Version für eine Vorgängerversion der Runtime erstellt wird.
- Häufig gestellte Fragen: Managed Extensions for C++
- Eine exemplarische Vorgehensweise wurde hinzugefügt, um darzustellen, wie eine bereits vorhandene native Anwendung für die Verwendung von Managed Extensions for C++ portiert wird (Walkthrough: Porting an Existing Native C++ Application to Interoperate with .NET Framework Components (Exemplarische Vorgehensweise: Portieren einer bereits vorhandenen nativen C++-Anwendung zur Zusammenarbeit mit .NET Framework-Komponenten)).
- Sie können jetzt einen Delegat für eine Methode eines Werttypen erstellen.
- Die Konformität des Compilers mit dem C++-Standard wurde für Visual C++ .NET 2003 deutlich verbessert.
- Die `/arch`-Compileroption wurde hinzugefügt.
- `/Gf` ist als veraltet markiert und wird mit der nächsten Visual C++-Version entfernt.
- Die `/G7`-Compileroption wurde hinzugefügt.
- Die `/GS`-Compileroption wurde erweitert, um die lokalen Variablen vor direkten Pufferüberläufen zu schützen.
- Die `/noBool`-Compileroption wurde entfernt. Der Compiler erlaubt jetzt **`bool`** , nur als Schlüsselwort (und nicht als Bezeichner) in einer C++-Quell Code Datei zu erscheinen.
- Der- **`long long`** Typ ist nun als verfügbar **`typedef`** **`__int64`** . Beachten Sie, dass **`long long`** in der CRT noch keine Unterstützung für vorhanden ist.
- Die `/Zm`-Compileroption legt jetzt die maximale Speicherbelegung für den vorkompilierten Header fest.
- Die intrinsische _InterlockedCompareExchange-Funktion wird jetzt dokumentiert.
- Die intrinsische _InterlockedDecrement-Funktion wird jetzt dokumentiert.
- Die intrinsische _InterlockedExchange-Funktion wird jetzt dokumentiert.
- Die intrinsische _InterlockedExchangeAdd-Funktion wird jetzt dokumentiert.
- Die intrinsische _InterlockedIncrement-Funktion wird jetzt dokumentiert.
- Die intrinsische _ReadWriteBarrier-Funktion wurde hinzugefügt.

### <a name="attributes"></a>Attribute

- Das Attribut `implements` wird jetzt dokumentiert.

### <a name="linker-features"></a>Linker-Features

Die folgenden Linkerparameter wurden hinzugefügt:

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Das .SAFESEH-Verzeichnis und die `/safeseh`-ml.exe-Option wurden hinzugefügt.

## <a name="see-also"></a>Weitere Informationen

[Visual C++-Handbuch: Portieren und Aktualisieren](visual-cpp-porting-and-upgrading-guide.md)
