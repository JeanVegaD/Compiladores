# Gramática BNF
![Logo TEC](https://tecdigital.tec.ac.cr/servicios/capacitacion/guia_estudiantes/resources/images/tec.png)

Instituto Tecnológico de Costa Rica  
Centro Académico de Limón  
Escuela de Computación  
Compiladores e Intérpretes  
Tarea I  

**Estudiantes:**  
Jean Anthony Vega Díaz (2016009280)  
Joseph Cortes Arce  
Josue Cano García

**Profesor:**  
Allan Rodríguez Dávila



## Producciones 

### **Generales**

#### Símbolos y palabras reservadas

    <simbolo_inicial> ::= main
    <delimitador> ::= # 

    <apertura_b_bloque> ::= { 
    <cierre_b_bloque> ::= }

    <comentario_linea> ::= @
    <apertura_b_comentario> ::=  @*
    <cierre_b_comentario> ::= *@

    <asignacion> ::= =
    
    <retorno_valor> ::= return

    <leer> ::= input
    <escribir> ::= output

    <signo_negativo> ::= -
    <simbolo_decimal> ::= .
    <valor_nulo> ::= null

    <apertura_string> ::=  “
    <cierre_string> ::= ”
    <apertura_char> ::=  '
    <cierre_char> ::= '

    <apertura_arreglo> ::= [
    <cierre_arreglo>::= ]
    <separador_lista>::= ,

    <verdaro> ::= true
    <falso> ::= false

#### Manejo de tipos de datos

    <enteros> ::= int 
    <reales> ::= float 
    <booleanos> ::= bool 
    <caracteres> ::= char 
    <cadena_caracteres> ::= string
    <arreglo> ::= array
    <vacio> ::= void

    <tipos_var> ::= <enteros> | <reales> | <caracteres> | <cadena_caracteres> | <booleanos> 



#### Símbolos aritméticos unarios y binarios 

    <suma> ::= + 
    <resta> ::= - 
    <multiplicación> ::=  * 
    <división> ::=  / 
    <potencia> ::=  ^
    <módulo> ::=  %

    <positivo> ::= ++
    <negativo> ::= --

#### Símbolos relaciones 

    <menor_que> ::= < 
    <mayor_que> ::= > 
    <igual_que> ::= == 
    <diferente> ::= != 
    <menor_igual> ::= <= 
    <mayor_igual> ::= >=


#### Símbolos lógicos

    <conjunción> ::= &
    <disyunción> ::= | 
    <negación> :: !




#### Numeros

    <cero> ::= 0
    <dígitos> ::= [0-9]
    <digLim> ::= [1-9]

    

#### Letras y simbolos
    
    <letras> := [a-zA-Z]+
    <char>::= [a-zA-Z]
    <símbolo> ::= [^<letras><dígitos>]+
    <todos_caracteres> ::= [<letras> | <dígitos> | <símbolo> ]+
  

#### Tipos de datos

    <numero_entero> :: = <cero>
    <numero_entero> :: = <signo_negativo>? <digLim> <dígitos>*

    <numero_entero_positivo> :: = <digLim> <dígitos>*

    <numero_flotante> := <numero_entero> <simbolo_decimal> <dígitos>+

    <string> ::= <apertura_string> <todos_caracteres> <cierre_string>

    <character> ::= <apertura_char> <char> <cierre_char>

    <valores_bool> ::= <verdadero> | <false> 

    <tipos_asig_var> ::= <valor_nulo> | <numero_entero> | <numero_flotante> | <cadena_caracteres> | <booleanos> 

   

### Declaración de variables

- [x] Maneje los tipos de variables enteras, reales, booleanas, caracteres, cadenas de
caracteres (string), arreglo estático de enteros y valor nulo
- [X] Permite expresión para creación y asignación de variables tipadas 
    

** **

    <parámetros_arreglo>::=   <numero_entero> 
    <parámetros_arreglo>::=   <numero_entero> <separador_lista> <parámetros_arreglo>


** **

    <dec_variable> ::= <tipos_var> <identificador> <delimitador>
    <dec_variable> ::= <tipos_var> <identificador> <asignacion> <valor_nulo> <delimitador>

    <dec_variable> ::=  <enteros> <identificador> <asignacion> <numero_entero> <delimitador>
    <dec_variable> ::=  <reales> <identificador> <asignacion> <numero_flotante> <delimitador>
    <dec_variable> ::=  <caracteres> <identificador> <asignacion> <apertura_char> <char> <cierre_char> <delimitador>
    <dec_variable> ::=  <cadena_caracteres> <identificador> <asignacion> <apertura_string> <todos_caracteres> <cierre_string> <delimitador>
    <dec_variable> ::=  <booleanos> <identificador> <asignacion> <valores_bool> <delimitador>

    <dec_variable> ::=  <enteros> <apertura_arreglo> <numero_entero_positivo> <cierre_arreglo> <identificador> <delimitador>
    <dec_variable> ::=  <enteros> <apertura_arreglo> <numero_entero_positivo> <cierre_arreglo> <identificador> <asignacion> <valor_nulo> <delimitador>
    <dec_variable> ::=  <enteros> <apertura_arreglo> <numero_entero_positivo> <cierre_arreglo> <identificador> <asignacion> <apertura_b_bloque> <parámetros_arreglo> <cierre_b_bloque> <delimitador>

    <asig_variable>::=  <identificador> <asignacion> <tipos_asig_var> <delimitador>



### **Expresiones aritméticas** 

- [x] Permite expresiones aritméticas binarias de suma, resta, división, multiplicación,
módulo (%) y potencia (^)
- [X] Permite expresiones aritméticas unarias de negativo, ++, -- (antes del operando)

** **
    <tipos_aritmeticos> ::=   <suma> | <resta> | <multiplicación> | <división> | <potencia> | <módulo> 

** **

    <exp_arimetica_una> ::=  [ <positivo> | <negativo> ] [ <identificador> | <numero_entero> | <numero_flotante> ]
    <exp_arimetica_bin> ::=  [ <identificador> |<numero_entero>| <numero_flotante> | <exp_arimetica_una> ]    <tipos_aritmeticos>  [<identificador> |<numero_entero>| <numero_flotante>] <delimitador> 
    <exp_arimetica_bin > ::=  [<identificador> |<numero_entero>| <numero_flotante> | <exp_arimetica_una>]    <tipos_aritmeticos> <exp_arimetica_bin > 


### **Expresiones relacionales**

- [x] Permite expresiones relacionales (sobre enteros y reales) de menor, menor o igual,
mayor, mayor o igual, igual y diferente.

** ** 

    <tipos_relacionales> ::=   <menor_que> | <mayor_que> | <igual_que> | <diferente> | <menor_igual> | <mayor_igual> 

** ** 

    <exp_relacionales> ::=  [<identificador> |<numero_entero>| <numero_flotante> | <exp_arimetica_una> <tipos_relacionales> [<identificador> |<numero_entero>| <numero_flotante>] <delimitador> 
    <exp_relacionales> ::=  [<identificador> |<numero_entero>| <numero_flotante> | <exp_arimetica_una>] <tipos_relacionales> <exp_relacionales> 

