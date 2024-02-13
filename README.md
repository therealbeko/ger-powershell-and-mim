# PowerShell CookBook

## Einleitung
<p>Dieses Cookbook enthält Dokumentationen, Erklärungen zu Funktionen und nützliche Tipps zu PowerShell welche von mir persönlich geschrieben wurden. Dokumentiert wird im Sinne alles was ich brauche um das Wissen zu einem späteren Zeitpunkt erneut auf einfache Art und Weise zugänglich zu machen und unter anderem meinen Fortschritt und das neu gewonnene Wissen zu tracken.</p>

### Was genau wird dokumentiert?
<li>Wie eine bestimme Funktion verwendet wird oder verwendet werden kann </li>
<li>Tipps und Tricks die ich im Laufe der Zeit gelernt habe</li>
<li>Der Umgang mit PowerShell und MIM</li>
<li>...</li>

<hr>

### Inhaltsverzeichnis
<strong>PowerShell</strong>
- [Write-Host](#write-host)
- [User Input](#user-input-read-host)
- [Basic Commands](#basic-commands)
- [Command History](#command-history)
- [Variablen](#variablen)
- - [Variablentypen](#variablentypen) 
- - [Constrained Variables](#constrained-variables)
- - [Mehrere Variablen erstellen](#mehrere-variablen-erstellen)
- - [Environment Variablen](#environment-variablen)

<strong>MIM</strong>
 - [MPR deaktivieren](#mpr-deaktivieren-disable-mpr)

<hr>

### Write-Host
Um im Terminal etwas auszugeben, kann Write-Host verwendet werden:

```
Write-Host "Hello World"
```

Der Output lautet dann:
```
Hello World
```
<hr>

### User Input (Read-Host)
Wir können über das Terminal auch User Input speichern.
```
$my_input = Read-Host -Prompt "Enter a number: "
```
Diese Zeile verlangt vom User einen Prompt bevor es im Script weitergeht. Der Wert welcher eingegeben wird, wird in diesem Falle in der Variable ```$my_input``` gespeichert
<hr>


### Basic Commands
```
Get-Date
```
Das Get ist das Verb und Date das "noun/Substantiv". Übersetzt heisst das insofern das Get das aktuelle Datum liest und uns im Terminal ausgibt.
```
Get-Command
```
Mit Get-Command sehen wir weitere Commands die uns zur Verfügung stehen.
```
Get-Command -Verb Get
```
Ohne Argument liefert Get-Command alle verfügbaren Commands. Mit dem Parameter -Verb und dem Argument "Get" zeigt es uns nur alle Commands an die mit "Get-" beginnen.
```
Get-Command -Noun Host
```
Das ganze funktioniert auch mit dem Parameter -Noun. Dieser zeigt in diesem Beispiel alle Commands welche "*-Host" beinhalten.

<hr>

### Command History
Mit dem Command: ```Get-History``` sehen wir alle Commands welche wir in dieser Session benutzt haben. Dies ist eine gesamte Übersicht. Bei sehr vielen Commands ist es nützlicher als mit den Pfeilen nach unten und oben zu gehen weil wir somit alle auf einmal sehen und nicht den Pfeil drückend suchen müssen.

<hr>

### Variablen
Um eine Variable zu erstellen, müssen wir dieser einen Wert zuweisen. In PowerShell werden Variablen mit einem $-Zeichen referenziert gefolgt vom Variablennamen. Nach der Variabelreferenz benutzten wir das Gleichheitszeichen (=) mit dem Wert welcher wir der Variable zuweisen möchten.
```
$my_string_variable = "This is my string!"
```

Es wird empfohlen der Namenskonvention zu folgen in welcher Wörter in den Variablen mit einem Unterstrich ( _ ) wie im obigen Beispiel getrennt werden. 

Wenn wir nun die Variable in der Konsole ausgeben mit Write-Host oder auch nur die Variable angeben ```$my_string_variable``` wird dieser in der Konsole ausgegeben.

<hr>

### Variablentypen
Es gibt verschiedene Variablentypen, unter anderem:

|Datentyp|Wert|
|-----------|-----------|
|Integer|2, -5, 99|
|String|"A", "Hallo", "Wie geht’s?"|
|Boolean|$true / $false|
|Array|25, "rot", $False, 16.5|


PowerShell überweist der Variable automatisch den Datentypen anhand dem Wert welchen wir zuweisen. Das nennt sich "dynamic typing".

Der Standarttyp einer uninitialisierten Variable ist $null.

Mit dem Command ```.GetType().Name``` erhalten wir den Datentyp der Variable in einer Konsole ausgegeben. In folgendem Beispiel gehen wir davon aus das $name den Wert "Tobias" hat.

|Beispiel|Output|
|-----------|-----------|
|$name.GetType().Name|String|

<hr>

### Constrained Variables
Wenn wir den Datentypen der Variable bestimmen möchten, können wir eine "constrained Variable" mittels "type casting" erstellen.
```
[Int]$age = 25
```
Während wir die Variable initialisieren bestimmen wir in den eckigen Klammern den Datentypen der Variable.
Nun ist es auch nicht mehr möglich andere Typen wie z.B einen String dieser Variable zuzuweisen.
<hr>

### Mehrere Variablen erstellen
Mehrere Variablen können auch in einer Zeile erstellt werden. Nachfolgend zwei Beispiele.

Beispiel 1: Mehrere Variablen mit dem selben Wert erstellen:
```
$i = $j = $k = 0
```
Beispiel 2: Mehrere Variablen mit verschiedenen Werten erstellen:
```
$number, $color, $bool = 25, "red", $false
```
<hr>

### Environment Variablen
Environment Variablen speichern Informationen welche relevant für unsere aktuelle Umgebung sind wie z.B das Betriebssystem oder die Session des Users. Sie sind globale Variablen auf welche wir über weitere Commands und Programme zugreifen können.

Environment Variablen werden als Strings gespeichert. Wir können mit Get-ChildItem eine gesamte Liste der Environment Variablen erhalten welche bereits existieren:
```
Get-ChildItem Env:
```
Output:
```
Name Value
---- -----
ALLUSERSPROFILE  C:\ProgramData  
APPDATA          C:\Users\xxx\AppData\Roaming  
...
```
Um einen spezifischen Wert einer Environment Variable zu erhalten,  können wir folgenden Command nutzen:
```
(Get-ChildItem Env:APPDATA).Value
```
Output:
```
C:\Users\xxx\AppData\Roaming
```
Zwei beliebte Environment Variablen sind HOME und PATH. Die HOME Variable definiert den Home Pfad des aktuellen Benutzers. PATH inkludiert alle Pfade welche Applikationen nach ausführbaren Anwendungen schauen.

#### Environment Variable erstellen:
```
$Env:EXAMPLE_ENV_VAR = "custom value"
```
<strong>Wichig:</strong> Environment Variablen werden immer gross geschrieben.

Der Vorteil von diesen ist das über die ganze Terminal-Session und in den Scripts darauf zugegriffen werden kann. 

Environment Variablen welche mehrere Werte enthalten separieren sich durch ein Semikolon z.B:
```
Custom value; Another value
```
<hr>

### Operatoren

Operatoren werden benötigt um verschiedene Berechnugnen mit Variablen durchzuführen.

Es gibt die folgenden Operatoren in PowerShell:
- Arithmetische Operatoren
- Assignment Operatoren
- Unary Operatoren
- Comparison Operatoren
- Logical Operatoren

#### Die Arithmetischen Operatoren:

|Operator|Beschreibung|
|-----------|-----------|
|+|(Addition) Addiert Zahlen und führt Strings zusammen|
|-|(Substraktion) Subtrahiert Zahlen|
|/|(Division) Dividiert Zahlen|
|%|(Modulo) Gibt den Restwert einer Division zurück|

Wir können mit Zahlen direkt rechnen z.B: 5 + 5 oder auch mit Variablen z.B: ```$x + $y```.

Strings können ebenfalls mit Arithmetischen Operatoren manipuliert werden. z.B: $name = "Tom"
```$name + $name``` ergibt = ```TomTom```.

<hr>

### Assignment und Unary Operatoren
Assignment Operatoren können verwendet werden um Werte zu vergeben, verändern oder ergänzen.

Der Standart Syntax hierbei wäre: ```<Variable>``` = ```<Wert>```.

Es gibt auch andere Assignment Operatoren welche compund assignment operators gennant werden. Beispiele:


|Operator|
|-|
|+=|
|-=|
|*=|
|/=|
|%=|


Compound assignment operators führen zu erst die Aktion aus und weisen dann erst den Wert der Variable zu.

Zum Beispiel:

```
$x = 5
$x += 1
Output: 6
```
Zu erst wird die 5 mit der 1 addiert und erst dann der Variable $x zugewiesen. 

Diese Operatoren können auch mit den Environment Variablen verwendet werden, da Strings addiert und kopiert werden können.

#### Unary Operatoren
Unary Operators können den Wert der Variable erhöhen oder verringen, z.B:
```
$x = 5
$x++
$x
Output: 6
```

<hr>

### Equality Comparison Operatoren
Comparison Operator werden genutzt um Werte zu vergleichen. Testkonditionen zu erstellen oder Elemente einer Kollektion z.B eines Arrays zu filtern. Sie geben uns die Werte True oder False als Resultat zurück.

Beschreibung der Equality Comparison Operatoren:

|Operator|Beschreibung|
|-----------|-----------|
|-eq|Prüft ob zwei Werte den selben Wert enthalten|
|-ne|Prüft ob zwei Werte nicht den selben Wert enthalten|
|-gt|Prüft ob der Wert links grösser ist als der Wert rechts|
|-lt|Prüft ob der Wert links kleiner ist als der Wert rechts|
|-ge|Prüft ob der Wert links grösser oder gleich gross ist wie der Wert rechts|
|-le|Prüft ob der Wert links kleiner oder gleich gross ist wie der Wert rechts|

Beispiel:
```
5 -eq 4
Output: False
```
#### Logische Operatoren
Logische Operatoren erlauben es uns mehrere Wahrheitswerte in einer komplexeren Kondition zu prüfen.

|Operator|Beschreibung|
|-----------|-----------|
|-and|Prüft ob Wert 1 und Wert 2 die Kondition erfüllen|
|-or|Prüft ob Wert 1 oder Wert 2 die Kondition erfüllt|
|-or|Prüft ob Wert 1 oder Wert 2 die Kondition erfüllt|
|-xor|Kondition erfüllt wenn nur eine davon stimmt|
|-not|Kondition erfüllt wenn der Wert nicht enthalten ist|

Grafische Tabellen ansicht (T = true, F = false):

|x|y|x -and y|x -or y|x -xor y|-not x|
|-----------|-----------|-----------|-----------|-----------|-----------|
|T|T|T|T|F|F|
|T|F|F|T|T|F|
|F|T|F|T|T|T|
|F|F|F|F|F|T|

<hr>

### MPR deaktivieren (Disable MPR)

```
$MPR = Get-Resource -AttributeName "DisplayName" -AttributeValue "Display Name of the MPR" -ObjectType "ManagementPolicyRule"
$MPR.Disabled = $true
Save-Resource $MPR
```
