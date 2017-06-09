---
title: "String-Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 338f0c26-8aee-43eb-bd1a-ec0849a376b9
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# String-Funktionen
Der .NET Framework-Datenanbieter für SQL Server (SqlClient) stellt `String`-Funktionen zur Verfügung, die einen eingegebenen `String` verarbeiten und als Ergebnis einen `String` oder einen numerischen Wert zurückgeben. Diese Funktionen befinden sich im SQLServer-Namespace, der bei der Verwendung von SqlClient verfügbar ist. Anhand der Namespaceigenschaft des Anbieters kann Entity Framework ermitteln, welches Präfix von diesem Anbieter für spezifische Konstrukte, wie Typen und Funktionen, verwendet wird.  
  
 In der folgenden Tabelle sind die SqlClient-`String`-Funktionen aufgeführt.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|`ASCII(` `expression` `)`|Gibt den ASCII-Codewert für das erste Zeichen eines Zeichenfolgeausdrucks zurück.<br /><br /> **Argumente**<br /><br /> `expression`: Jeder gültige Ausdruck eines ASCII-`String`-Typs.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.ASCII('A')`|  
|`CHAR(` `expression` `)`|Konvertiert einen `Int32`-Code in eine ASCII-Zeichenfolge.<br /><br /> **Argumente**<br /><br /> `expression`: Ein `Int32`.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.char(97)`|  
|`CHARINDEX(` `expression1, expression2` [, `start_location`]`)`|Gibt die Anfangsposition des angegebenen Ausdrucks in einer Zeichenfolge zurück.<br /><br /> **Argumente**<br /><br /> `expression1`: Ein Ausdruck, der die Zeichenfolge enthält, nach der gesucht werden soll. Der Ausdruck kann eine Zeichenfolge (ASCII oder Unicode) oder binär sein.<br /><br /> `expression2`: Ein Ausdruck, typischerweise eine Spalte, der nach der angegebenen Zeichenfolge durchsucht werden soll. Der Ausdruck kann eine Zeichenfolge (ASCII oder Unicode) oder binär sein.<br /><br /> `start_location`: (Optional) ein Int64 (nicht zurückgegeben in SQL Server 2000) oder Int32, der die Zeichenposition in expression2 nach expression1 darstellt. Wird die Startposition nicht angegeben oder ist sie ein negative Zahl bzw. null (0), wird die Suche am Anfang von expression2 gestartet.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.CHARINDEX('h', 'habcdefgh', 2)`|  
|`DIFFERENCE(` `expression, expression` `)`|Vergleicht die `SOUNDEX`-Werte von zwei Zeichenfolgen und wertet die Ähnlichkeit zwischen ihnen aus.<br /><br /> **Argumente**<br /><br /> Ein ASCII- oder Unicode-`String`-Typ. `expression` kann eine Konstante, eine Variable oder eine Spalte sein.<br /><br /> **Rückgabewert**<br /><br /> Gibt einen `Int32`-Wert zurück, der die Differenz zwischen den SOUNDEX-Werten zweier Zeichenausdrücke angibt. Der Wertebereich liegt zwischen 0 und 4. 0 gibt an, dass keine oder nur eine geringe Ähnlichkeit besteht, 4 weist auf eine starke Ähnlichkeit oder identische Werte hin.<br /><br /> **Beispiel**<br /><br /> `// The following example returns a DIFFERENCE value of 4,`<br /><br /> `//the least possible difference or the best match.`<br /><br /> `SqlServer.DIFFERENCE('Green','Greene');`|  
|`LEFT(` `expression, count` `)`|Gibt den linken Teil einer Zeichenfolge mit der angegebenen Anzahl von Zeichen zurück.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Unicode- oder ASCII-Zeichenfolgentyp. Verwenden Sie die CAST-Funktion, um character_expression explizit zu ändern.<br /><br /> `count`: Ein `Int64`-Typ (wird in SQL Server 2000 nicht zurückgegeben) oder ein `Int32`-Typ, der festlegt, wie viele Zeichen von character_expression zurückgegeben werden.<br /><br /> **Rückgabewert**<br /><br /> Ein Unicode- oder ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.LEFT('SQL Server', 4)`|  
|`LEN(` `expression` `)`|Gibt die Anzahl von Zeichen im angegebenen Zeichenfolgenausdruck zurück, wobei nachfolgende Leerzeichen ausgeschlossen werden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Ausdruck eines `String`-Typs (Unicode oder ASCII) oder eines `Binary`-Typs.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.LEN('abcd')`|  
|`LOWER(` `expression` `)`|Gibt einen `String`-Ausdruck zurück, nachdem groß geschriebene Zeichendaten in klein geschriebene konvertiert wurden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein gültiger Ausdruck des `String`-Typs.<br /><br /> **Rückgabewert**<br /><br /> Ein `String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.LOWER('AbB')`|  
|`LTRIM(` `expression` `)`|Gibt einen `String`-Ausdruck zurück, nachdem führende Leerzeichen entfernt wurden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein gültiger Ausdruck des `String`-Typs.<br /><br /> **Rückgabewert**<br /><br /> Ein `String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.LTRIM('   d')`|  
|`NCHAR(` `expression` `)`|Gibt einen `String` (Unicode) mit dem angegebenen ganzzahligen Code gemäß der Definition durch den Unicode-Standard zurück.<br /><br /> **Argumente**<br /><br /> `expression`: Ein `Int32`.<br /><br /> **Rückgabewert**<br /><br /> Ein `String` (Unicode).<br /><br /> **Beispiel**<br /><br /> `SqlServer.NCHAR(65)`|  
|`PATINDEX(` `'%pattern%'`, `expression``)`|Gibt die Anfangsposition des ersten Vorkommens eines Musters in einem angegebenen `String`-Ausdruck zurück.<br /><br /> **Argumente**<br /><br /> `'%pattern%'`: Ein `String`-Typ (ASCII oder Unicode). Platzhalterzeichen können verwendet werden. Das Zeichen "%" muss jedoch vor und nach dem Muster eingegeben werden (außer bei der Suche nach den ersten oder letzten Zeichen).<br /><br /> `expression`: Ein ASCII- oder Unicode-`String` für die Suche nach dem angegebenen Muster.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.PATINDEX('abc', 'ab')`|  
|`QUOTENAME(` `'char_string'` [, '`quote_char'`]`)`|Gibt einen `String` (Unicode) mit hinzugefügten Trennzeichen zurück, um die Eingabezeichenfolge als gültigen Bezeichner mit Trennzeichen für SQL Server 2005 festzulegen.<br /><br /> **Argumente**<br /><br /> `char_string`: Ein Unicode-`String`.<br /><br /> `quote_char`: Eine Zeichenfolge mit einem Zeichen, das als Trennzeichen verwendet wird. Hierbei kann es sich um ein einfaches Anführungszeichen ('), eine linke oder rechte Klammer ([ ]) oder ein doppeltes Anführungszeichen (") handeln. Wenn `quote_char` nicht angegeben wird, werden eckige Klammern verwendet.<br /><br /> **Rückgabewert**<br /><br /> Ein `String` (Unicode).<br /><br /> **Beispiel**<br /><br /> `SqlServer.QUOTENAME('abc[]def')`|  
|`REPLACE(` `expression1`, `expression2, expression3``)`|Wiederholt einen Zeichenausdruck so oft wie angegeben.<br /><br /> **Argumente**<br /><br /> `expression1`: Der Zeichenfolgenausdruck für die Suche. string_expression1 kann eine Unicode- oder ASCII-Zeichenfolge sein.<br /><br /> `expression2`: Die zu suchende Teilzeichenfolge. string_expression2 kann eine Unicode- oder ASCII-Zeichenfolge sein.<br /><br /> `expression3`: Die Ersatzzeichenfolge. string_expression3 kann eine Unicode- oder ASCII-Zeichenfolge sein.<br /><br /> **Beispiel**<br /><br /> `SqlServer.REPLACE('aabbcc', 'bc', 'zz')`|  
|`REPLICATE(``char_expression`, int_`expression``)`|Wiederholt einen Zeichenausdruck so oft wie angegeben.<br /><br /> **Argumente**<br /><br /> `char_expression`: Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> `int_expression`: `Int64` (wird in SQL Server 2000 nicht unterstützt) oder `Int32`.<br /><br /> **Rückgabewert**<br /><br /> Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> **Beispiel**<br /><br /> `SqlServer.REPLICATE('aa',2)`|  
|`REVERSE(` `expression` `)`|Gibt eine Unicode- oder ASCII-Zeichenfolge zurück, bei der die Zeichenpositionen gegenüber der Eingabezeichenfolge umgekehrt wurden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> **Rückgabewert**<br /><br /> Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> **Beispiel**<br /><br /> `SqlServer.REVERSE('abcd')`|  
|`RIGHT(` `char_expression`, `count``)`|Gibt den rechten Teil einer Zeichenfolge mit der angegebenen Anzahl von Zeichen zurück.<br /><br /> **Argumente**<br /><br /> `char_expression`: Ein Unicode- oder ASCII-Zeichenfolge-Typ. Verwenden Sie die CAST-Funktion, um character_expression explizit zu ändern.<br /><br /> `count`: Ein `Int64`-Typ (wird in SQL Server 2000 nicht zurückgegeben) oder ein `Int32`-Typ, der festlegt, wie viele Zeichen von character_expression zurückgegeben werden.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`-Typ.<br /><br /> **Beispiel**<br /><br /> `SqlServer.RIGHT('SQL Server', 6)`|  
|`RTRIM(` `expression` `)`|Gibt eine Unicode- oder ASCII-Zeichenfolge zurück, nachdem nachfolgende Leerzeichen entfernt wurden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> **Rückgabewert**<br /><br /> Ein Unicode- oder ASCII-`String`-Typ.<br /><br /> **Beispiel**<br /><br /> `SqlServer.RTRIM('   d   e      ')`|  
|`SOUNDEX(` `expression` `)`|Gibt einen aus vier Zeichen (bestehender SOUNDEX) Code zur Bewertung der Ähnlichkeit von zwei Zeichenfolgen zurück. **Argumente**<br /><br /> `expression`: Ein Unicode- oder ASCII-Zeichenfolgentyp.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`. Ein aus vier Zeichen bestehender (SOUNDEX) Code ist eine Zeichenfolge, die zur Bewertung der Ähnlichkeit von zwei Zeichenfolgen verwendet wird.<br /><br /> **Beispiel**<br /><br /> `Select SqlServer.SOUNDEX('Smith'), SqlServer.SOUNDEX('Smythe') FROM {1}`<br /><br /> **Gibt**<br /><br /> `----- -----  S530  S530`|  
|`SPACE(` `int_expression` `)`|Gibt einen ASCII-`String` aus mehreren Leerzeichen zurück.<br /><br /> **Argumente**<br /><br /> `int_expression`: Ein `Int64`-Wert (wird in SQL Server 2000 nicht zurückgegeben) oder ein `Int32`-Wert, der die Anzahl der Leerzeichen angibt.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.SPACE(2)`|  
|`STR(` `float_expression` [, `length` [, `decimal`]]`)`|Gibt einen ASCII-`String` zurück, der aus numerischen Daten konvertiert wurde.<br /><br /> **Argumente**<br /><br /> `float _expression`: Ein Ausdruck der ungefähren numerischen Datentypkategorie (`Double`) mit einem Dezimaltrennzeichen.<br /><br /> (`length`: optional) Ein `Int32`-Wert, der die Gesamtlänge darstellt. Dazu gehören Dezimaltrennzeichen, Vorzeichen, Ziffern und Leerzeichen. Der Standard ist 10.<br /><br /> `decimal`: (optional) eine `Int32` , die die Anzahl der Stellen rechts neben dem Dezimalzeichen darstellt. Der Wert für "decimal" muss kleiner oder gleich 16 sein. Wenn der Wert für "decimal" höher als 16 ist, wird das Ergebnis bei sechzehn Stellen nach dem Dezimaltrennzeichen abgeschnitten.<br /><br /> **Rückgabewert**<br /><br /> Ein ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.STR(212.0)`|  
|`STUFF(` `str_expression`, `start, length`, `str_expression_to_insert``)`|Löscht eine angegebene Anzahl von Zeichen und fügt andere Zeichen am angegebenen Anfangspunkt in einen Zeichenfolgenausdruck ein.<br /><br /> **Argumente**<br /><br /> `str_expression`: Ein Unicode- oder ASCII-`String`.<br /><br /> `start:`Ein `Int64` (nicht zurückgegeben in SQL Server 2000) oder `Int32` -Wert, der die Position der Löschung und Einfügung angibt.<br /><br /> `length`: Ein `Int64`-Wert (nicht zurückgegeben in SQL Server 2000) oder ein `Int32`-Wert, der die Anzahl von Zeichen angibt, die gelöscht werden sollen.<br /><br /> `str_expression_to_insert`: Ein Unicode- oder ASCII-`String`.<br /><br /> **Rückgabewert**<br /><br /> Ein Unicode- oder ASCII-`String`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.STUFF('abcd', 2, 2, 'zz')`|  
|`SUBSTRING(` `str_expression`, `start, length``)`|Gibt einen Teil eines `String`-Ausdrucks zurück.<br /><br /> **Argumente**<br /><br /> `str_expression`: Ein Ausdruck eines `String`-Typs (Unicode oder ASCII) oder eines `Binary`-Typs.<br /><br /> `start`: Ein `Int64` (nicht zurückgegeben in SQL Server 2000) oder ein `Int32`, das angibt, an welcher Position die untergeordnete Zeichenfolge beginnt. 1 bezieht sich auf das erste Zeichen in der Zeichenfolge.<br /><br /> `length`: Ein `Int64`-Wert (wird in SQL Server 2000 nicht zurückgegeben) oder ein `Int32`-Wert, der festlegt, wie viele Zeichen des Ausdrucks zurückgegeben werden.<br /><br /> **Rückgabewert**<br /><br /> Ein `String`-Typ (ASCII oder Unicode) oder ein `Binary`-Typ.<br /><br /> **Beispiel**<br /><br /> `SqlServer.SUBSTRING('abcd', 2, 2)`|  
|`UNICODE(` `expression` `)`|Gibt für das erste Zeichen des Eingabeausdrucks den im Unicode-Standard entsprechenden ganzzahligen Wert zurück.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Unicode-`String`.<br /><br /> **Rückgabewert**<br /><br /> Eine `Int32`.<br /><br /> **Beispiel**<br /><br /> `SqlServer.UNICODE('a')`|  
|`UPPER(` `expression` `)`|Gibt einen `String`-Ausdruck zurück, nachdem klein geschriebene Zeichen in groß geschriebene konvertiert wurden.<br /><br /> **Argumente**<br /><br /> `expression`: Ein Ausdruck eines Unicode- oder ASCII-Zeichenfolgentyps.<br /><br /> **Rückgabewert**<br /><br /> Ein `String`-Typ (ASCII oder Unicode).<br /><br /> **Beispiel**<br /><br /> `SqlServer.UPPER('AbB')`|  
  
 Weitere Informationen zu den von SqlClient unterstützten `String`-Funktionen finden Sie in der Dokumentation für die SQL Server-Version, die im SqlClient-Anbietermanifest angegeben wurde:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Zeichenfolgenfunktionen (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115915)|[Zeichenfolgenfunktionen (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115916)|[Zeichenfolgenfunktionen (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115914)|  
  
## <a name="see-also"></a>Siehe auch  
 [SqlClient für Entity Framework-Funktionen](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)   
 [Bekannte Probleme in SqlClient für Entitätsframework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)