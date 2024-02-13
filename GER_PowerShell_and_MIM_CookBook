
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
- Eintrag

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


<hr>

### User Input (Read-Host)
Wir können über das Terminal auch User Input speichern.
```
$my_input = Read-Host -Prompt "Enter a number: "
```
Diese Zeile verlangt vom User einen Prompt bevor es im Script weitergeht. Der Wert welcher eingegeben wird, wird in diesem Falle in der Variable ```$my_input``` gespeichert
<hr>

### MPR deaktivieren (Disable MPR)

```
$MPR = Get-Resource -AttributeName "DisplayName" -AttributeValue "Display Name of the MPR" -ObjectType "ManagementPolicyRule"
$MPR.Disabled = $true
Save-Resource $MPR
```
