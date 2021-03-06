---
title: Compileranweisungen (F#)
description: "Informationen Sie zu F#-Sprache Präprozessordirektiven, bedingten Kompilierungsdirektiven, Line-Direktiven und Compiler-Direktiven."
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: b4305d24163f9b23631d5efb6e838f55127cd9f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-directives"></a>Compileranweisungen

In diesem Thema werden Prozessor- und Compileranweisungen beschrieben.


## <a name="preprocessor-directives"></a>Präprozessordirektiven
Einer Präprozessordirektive wird das #-Symbol vorangestellt und wird für sich genommen in einer Zeile angezeigt. Sie wird durch den Präprozessor interpretiert, der vom Compiler ausgeführt wird.

In der folgenden Tabelle werden die Präprozessordirektiven aufgelistet, die in F# verfügbar sind.


|Direktive|Beschreibung|
|---------|-----------|
|`#if`*Symbol*|Unterstützt die bedingte Kompilierung. Code im Abschnitt nach der `#if` liegt vor, wenn die *Symbol* definiert ist.|
|`#else`|Unterstützt die bedingte Kompilierung. Markiert einen einzubeziehenden Codeabschnitt, wenn das mit dem vorherigen verwendeten `#if` nicht definiert ist.|
|`#endif`|Unterstützt die bedingte Kompilierung. Markiert das Ende eines bedingten Codeabschnitts.|
|`#`[Zeile] *Int*,<br/>`#`[Zeile] *Int* *Zeichenfolge*,<br/>`#`[Zeile] *Int* *wörtliche Zeichenfolge*|Gibt die ursprüngliche Quellcodezeile und den Dateinamen für das Debuggen an. Diese Funktion wird für Tools bereitgestellt, die F#-Quellcode generieren.|
|`#nowarn`*Warningcode*|Deaktiviert eine Compilerwarnung oder Warnungen. Suchen Sie zum Deaktivieren einer Warnung nach ihrer Nummer in der Compilerausgabe, und setzen Sie sie in Anführungszeichen. Lassen Sie das Präfix „FS“ weg. Zum Deaktivieren von mehreren Warnnummern in derselben Zeile müssen Sie jede Nummer in Anführungszeichen setzen und jede Zeichenfolge durch ein Leerzeichen abtrennen. Zum Beispiel:

`#nowarn "9" "40"`


Die Auswirkung der Deaktivierung einer Warnung wird angewendet, auf die gesamte Datei, einschließlich Teilmengen der Datei, die die Direktive vorausgehen. |

## <a name="conditional-compilation-directives"></a>Anweisungen für die bedingte Kompilierung
Code, der durch eine dieser Direktiven deaktivierte wird im Visual StudioCode Editor abgeblendet angezeigt.


>[!NOTE] 
Das Verhalten der Anweisungen für die bedingte Kompilierung entspricht nicht dem in anderen Sprachen. Beispielsweise können Sie keine booleschen Ausdrücke mit Symbolen verwenden, zudem verfügen `true` und `false` über keine besondere Bedeutung. In der `if`-Direktive von Ihnen verwendete Symbole müssen über die Befehlszeile oder in den Projekteinstellungen definiert werden. Es steht keine `define`-Präprozessordirektive zur Verfügung.


Im folgenden Code wird die Verwendung der Direktiven `#if`, `#else` und `#endif` veranschaulicht. In diesem Beispiel enthält der Code zwei Versionen der Definition von `function1`. Wenn `VERSION1` wird definiert, mit der [-define-Compileroption](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), den Code zwischen die `#if` Richtlinie und die `#else` Richtlinie aktiviert ist. Andernfalls wird der Code zwischen `#else` und `#endif` aktiviert.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Es gibt keine `#define`-Präprozessordirektive in F#. Sie müssen die Compileroption oder Projekteinstellungen verwenden, um die durch die `#if`-Direktive verwendeten Symbole zu definieren.

Direktiven für die bedingte Kompilierung können geschachtelt werden. Der Einzug ist für Präprozessordirektiven nicht entscheidend.


## <a name="line-directives"></a>Line-Direktiven
Beim Erstellen meldet der Compiler Fehler im F#-Code durch das Referenzieren von Zeilennummern, in denen die jeweiligen Fehler auftreten. Diese Zeilennummern beginnen bei 1 für die erste Zeile in einer Datei. Wenn Sie jedoch F#-Quellcode aus einem anderen Tool generieren, sind die Zeilennummern im generierten Code im Allgemeinen nicht relevant, da die Fehler im generierten F#-Code höchstwahrscheinlich auf eine andere Quelle zurückgehen. Mit der `#line`-Direktive können Autoren von Tools, die F#-Quellcode generieren, Informationen über die ursprünglichen Zeilennummern und Quelldateien an den generierten F#-Code weitergeben.

Beim Verwenden der `#line`-Direktive müssen Dateinamen in Anführungszeichen gesetzt werden. Sofern das verbatim-Token (`@`) nicht am Anfang der Zeichenfolge angezeigt wird, müssen Sie umgekehrte Schrägstriche durch die Verwendung von zwei (und nicht nur einem) umgekehrten Schrägstrichen escapen, um sie im Pfad zu verwenden. Im Folgenden finden Sie gültige Zeilentoken. In diesen Beispielen wird davon ausgegangen, dass die ursprüngliche `Script1`-Datei in einer automatisch generierten F#-Codedatei resultiert, wenn er über ein Tool ausgeführt wird, und dass der Code am Speicherort dieser Direktiven aus einigen Token in Zeile 25 in der Datei `Script1` generiert wird.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Diese Token geben an, dass der an diesem Speicherort generierte F#-Code aus einigen Konstrukten in oder in der Nähe der Zeile `25` in `Script1` abgeleitet ist.


## <a name="compiler-directives"></a>Compilerdirektiven
Compilerdirektiven ähneln Präprozessordirektiven, da ihnen ein #-Zeichen vorangestellt ist. Anstelle jedoch durch den Präprozessor interpretiert zu werden, werden sie durch den Compiler interpretiert und verarbeitet.

Die folgende Tabelle enthält die Compilerdirektive, die in F# verfügbar ist.


|Direktive|Beschreibung|
|---------|-----------|
|`#light`["on"|"off"]|Aktiviert oder deaktiviert die einfache Syntax für die Kompatibilität mit anderen MK-Versionen. Standardmäßig ist die einfache Syntax aktiviert. Die ausführliche Syntax ist immer aktiviert. Daher können Sie die einfache und ausführliche Syntax verwenden. Die Direktive `#light` an sich entspricht `#light "on"`. Beim Angeben von `#light "off"` müssen Sie die ausführliche Syntax für alle Sprachkonstrukte verwenden. Bei der in der Dokumentation für F# gezeigten Syntax wird davon ausgegangen, dass Sie die einfache Syntax verwenden. Weitere Informationen finden Sie unter [ausführliche Syntax](verbose-syntax.md).|
Interpreter (fsi.exe)-Anweisungen finden Sie unter [Interaktive Programmierung mit F#-](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Siehe auch
[F#-Sprachreferenz](index.md)

[Compileroptionen](compiler-options.md)

