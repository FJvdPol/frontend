# Codenotes

## You don't know JS - 3. Scopes & Closures

### 1. What is Scope?
> Vertaling Scope: bereik

Scope gaat in javascript vooral over de omgeving waarin variables leven en waar ze te vinden zijn.
Drie stappen van compileren:
1. Tokenizing/ Lexing: 
Het breken van de code in chunks van betekenisvolle data (`var a = 2` breekt in `var`, `a`, `=`, `2`)
2. Parsing: 
Alle losse chunks orderen in een tree vieuw
(AST oftewel Abstract Syntax Tree)
3. Code-generation: 
De AST in uitvoerbare code omzetten  

Deelnemers bij compileren:
1. Engine: zorgt voor het a-z proces
2. Compiler: parsed code
3. Scope: onthoud leefomgeving en waardes van variables

LHS & RHS: left-hand side & right-hand side  
```js
var a = b
```  
Het gedeelte `var a` gaat over het opslaan van data in a, LHS  
Het gedeelte `b` gaat over het ophalen van de data van b, RHS  

### 2. Lexical Scope
> Vertaling Lexical: gerelateerd aan de taal

Dus lexical scope is het spreken van een bepaald bereik binnen de context van de (code)taal


### 3. Function vs Block Scope


### 4.  Hoisting
> Vertaling Hoisting: Het omhoog halen van iets.


### 5. Scope Closures
> Vertaling Closures: De leefomgeving van een function
