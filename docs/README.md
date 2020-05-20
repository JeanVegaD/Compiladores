# Gramática BNF
![Logo TEC](https://tecdigital.tec.ac.cr/servicios/capacitacion/guia_estudiantes/resources/images/tec.png)

Instituto Tecnológico de Costa Rica  
Centro Académico de Limón  
Escuela de Computación  
Compiladores e Intérpretes  
Tarea I  

**Estudiantes:**  
Jean Anthony Vega Díaz (2016009280)  
Joseph Cortes Arce  (2017164532)
Josue Cano García (2017100062)

**Profesor:**  
Allan Rodríguez Dávila



## Producciones 

### **Generales**

#### Símbolos y palabras reservadas

    <delimitador> ::= # 
    <apertura_b_codigo> ::= { 
    <cierre_b_codigo> ::= }
    <comentario_linea> ::= @
    <apertura_b_comentario> ::=  @*
    <cierre_b_comentario> ::= *@
    <asignacion> ::= =
    <simbolo_inicial> ::= main
    <retorno_valor> ::= return
    <_input> ::= input
    <simbolo_imput> ::= >>
    <_output> ::= print
    <signo_negativo> ::= -
    <simbolo_decimal> ::=  .
    <valor_nulo> ::= null
    <apertura_string> ::=  “
    <cierre_string> ::= ”
    <apertura_char> ::=  '
    <cierre_char> ::= '
    <apertura_arreglo> ::= [
    <cierre_arreglo> ::= ]
    <apertura_jeraquia> ::= (
    <cierre_jeraquia> ::= )
    <separador_lista> ::= ,
    <verdaro> ::= true
    <falso> ::= false
    <_if> ::= if
    <_else> ::= else
    <_do> ::= do
    <_while> ::= while 
    <_switch> ::= switch
    <_case> :: = case 
    <_break> ::= break
    <_default> ::= default
    <dos_puntos> ::= : 



#### Símbolos aritméticos unarios y binarios 

    <suma> ::= + 
    <resta> ::= - 
    <multiplicación> ::=  * 
    <división> ::=  / 
    <potencia> ::=  ^
    <módulo> ::=  %
    <tipos_aritmeticos> ::=   <suma> | <resta> | <multiplicación> | <división> | <potencia> | <módulo> 

    <positivo> ::= ++
    <negativo> ::= --


#### Símbolos relaciones 

    <menor_que> ::= < 
    <mayor_que> ::= > 
    <igual_que> ::= == 
    <diferente> ::= != 
    <menor_igual> ::= <= 
    <mayor_igual> ::= >=

    <tipos_relacionales> ::=   <menor_que> | <mayor_que> | <igual_que> | <diferente> | <menor_igual> | <mayor_igual> 



#### Símbolos lógicos

    <conjunción> ::= &
    <disyunción> ::= | 
    <negación> :: !

    <tipos_logicos> ::= <conjunción> | <disyunción>
    
    <variables_logicas> ::= <verdadero> | <falso> 





#### Numeros

    <cero> ::= 0
    <dígitos> ::= [0-9]
    <digLim> ::= [1-9]

    

#### Letras y simbolos
    
    <letras> := [a-zA-Z]+
    <char>::= [a-zA-Z]
    <símbolo> ::= [^<letras><dígitos>]+
    <todos_caracteres> ::= [<letras> | <dígitos> | <símbolo> ]+
    <identificador> :=   [ _ | <letras> ]  [ _ | <letras> <dígitos> ] *

  

#### Manejo de tipos de datos

    <t_int> ::= int 
    <t_float> ::= float 
    <t_bool> ::= bool 
    <t_char> ::= char 
    <t_string> ::= string
    <t_array> ::= array
    <t_void> ::= void 
    <tipos_var> ::= <t_int> | <t_float> | <t_char> | <t_string> | <t_bool> 
 



#### Tipos de datos

    <int> :: = <cero>
    <int> :: = <signo_negativo>? < digLim > < dígitos > *
    <int_positivo> :: = <digLim> < dígitos > *
    <float> := <int> <simbolo_decimal> <dígitos>+

    <string> ::= <apertura_string> <todos_caracteres> <cierre_string>
    <character> ::= <apertura_char> <char> <cierre_char>

    <bool> ::= <verdadero> | <falso> 

    <tipos_asig_var> ::= <valor_nulo> | <int> | <float> | <string> | <character> | <bool>


   

### **Declaración de variables**

- [x] Maneje los tipos de variables enteras, reales, booleanas, caracteres, cadenas de
caracteres (string), arreglo estático de enteros y valor nulo
- [X] Permite expresión para creación y asignación de variables tipadas 
- [X] Debe permitir el casteo explícito de string a entero

    
** **
    <dec_variable> ::= <tipos_var> <identificador> 
    <dec_variable> ::= <tipos_var> <identificador> <asignacion> [ <tipos_asig_var> | <exp_arimetica_bin> | <exp_arimetica_una> | <función> | <exp_logica> | <exp_logica_una> ]


    <parametros_arreglo> ::=   <int> | <función> ] <exp_arimetica_bin> | <exp_arimetica_una>
    <parametros_arreglo > ::= <parametros_arreglo> <separador_lista> <parametros_arreglo>

    <dec_variable> ::=  <t_int> <identificador> <apertura_arreglo> <int_positivo> <cierre_arreglo>
    <dec_variable> ::=  <t_int> <identificador> <apertura_arreglo> <int_positivo> <cierre_arreglo> <asignacion> <valor_nulo>
    <dec_variable> ::=  <enteros> <identificador> <apertura_arreglo> <int_positivo> <cierre_arreglo> <asignacion> <apertura_b_codigo> <parametros_arreglo> <cierre_b_codigo> 

    <asig_variable> ::=  <identificador> <asignacion> [ <tipos_asig_var> | <exp_arimetica_bin> | <exp_arimetica_una> | <función> | <exp_logica> | <exp_logica_una> ]

    <asig_variable> ::=  <identificador> <apertura_arreglo> <int_positivo> <cierre_arreglo> <asignacion> [ <int> | <función> ] <exp_arimetica_bin> | <exp_arimetica_una> ]
    
    <cast_string_int> ::= StringToInt <apertura_jeraquia> [<string> | <función>] <cierre_jeraquia>





### **Expresiones aritméticas** 

- [x] Permite expresiones aritméticas binarias de suma, resta, división, multiplicación,
módulo (%) y potencia (^)
- [X] Permite expresiones aritméticas unarias de negativo, ++, -- (antes del operando)

** **
    <exp_arimetica_una> ::=  [ <positivo> | <negativo> ] [ <identificador> | <int> | <float> ]
    <parm_exp_arimetica> ::=  <identificador> | <int> | <float> | <exp_arimetica_una> | <función>

    <exp_arimetica_bin> ::=  <parm_exp_arimetica> <tipos_aritmeticos>   <parm_exp_arimetica> 
    <exp_arimetica_bin> ::= <parm_exp_arimetica> <tipos_aritmetico> <exp_arimetica_bin> 
    <exp_arimetica_bin> ::= <apertura_jeraquia> <exp_arimetica_bin> <cierre_jeraquia> [ <tipos_aritmeticos> [<parm_exp_arimetica> | <exp_arimetica_bin>] ]?




### **Expresiones relacionales**

- [x] Permite expresiones relacionales (sobre enteros y reales) de menor, menor o igual,
mayor, mayor o igual, igual y diferente.


** ** 
    <parm_exp_relacional> ::=  <identificador> | <int> | <float> | <string> | <función> | <exp_arimetica_una> | <exp_arimetica_bin> | <función>

    <exp_relacional> ::=  <parm_exp_relacional> <tipos_relacionales> <parm_exp_relacional>
    <exp_relacional> ::=  <parm_exp_relacional> <tipos_relacionales> <exp_relacionales> 
    <exp_relacional> ::= <apertura_jeraquia> <exp_relacional> <cierre_jeraquia> [ <tipos_relacionales> [ <parm_exp_relacional > | <exp_relacionales>] ]?


### **Expresiones lógicas**

- [x] Permitir expresiones lógicas de conjunción, disyunción y negación.

**  ** 

    <exp_logica_una> :: = [ <negación> ]? <identificador> | <función> | <exp_relacional> 	| <variables_logicas> | <función>
    <exp_logica_bin> :: = <exp_logica_una> <tipos_logicos> <exp_logica_una>
    <exp_logica > :: = <exp_logica_bin> <tipos_logicos> <exp_logica_bin>
    <exp_logica> ::= <exp_logica_bin > <tipos_logicos> <exp_logica>
    <exp_logica> ::= < apertura_jeraquia > [<exp_logica> | <exp_logica_una> | <exp_logica_bin> ] <cierre_jeraquia>  [<exp_logica>]?


### **Sentencias**

- [ ]  Debe permitir sentencias de código para las diferentes expresiones mencionadas anteriormente y su combinación (incluyendo funciones), el delimitador de final de expresión será el carácter numeral (#).

** ** 

    <sentencia> ::=   <comentario> <delimitador>
    <sentencia> ::=   <cometario_bloque> delimitador>
    <sentencia> ::=  <dec_variable> <delimitador>
    <sentencia> ::=  <asig_variable> <delimitador>
    <sentencia> ::=  <cast_string_int> <delimitador>
    <sentencia> ::=  <if_else> <delimitador>
    <sentencia> ::=  <while> <delimitador>
    <sentencia> ::=  <do_while> <delimitador>
    <sentencia> ::=  <switch> <delimitador> 
    <sentencia> ::=  <función> <delimitador>
    <sentencia> ::=  <leer> <delimitador>
    <sentencia> ::=  <escribir> <delimitador>



### **Estructuras de control**

- [X]  Debe permitir sentencias de código para las diferentes expresiones mencionadas anteriormente y su combinación (incluyendo funciones), el delimitador de final de expresión será el carácter numeral (#).

** ** 

    <condicion> ::= <exp_logica>
    <bloque> ::=  <sentencia>+ 

    <if_else> ::=   <_if> <apertura_jeraquia> <condicion> <cierre_jeraquia> <apertura_b_codigo> <bloque> <cierre_b_codigo> [ <_else> <apertura_b_codigo> <bloque> <cierre_b_codigo> ]?
    <while> :: = <_while> <apertura_jeraquia> <condicion> <cierre_jeraquia> <apertura_b_codigo> <bloque> <cierre_b_codigo>
    <do_while> ::= <_do> <apertura_b_codigo> <bloque> <cierre_b_codigo> <_while> <apertura_jeraquia> <condicion> <cierre_jeraquia>  
    <switch> ::= <_switch> <apertura_jeraquia> <identificador> <cierre_jeraquia> <apertura_b_codigo> [ <_case> [identificador | int | float | string | char ] <dos_puntos> <bloque> <_break> <delimitador> ]+ [<_default> < dos_puntos> <bloque>]? <cierre_b_codigo>




### **Funciones**

- [x]  Debe permitir la creación y utilización de funciones, estos pueden retornar valores
y recibir parámetros (con tipo).


** ** 

    <tipos_retorno_funcion> ::=  <t_void> | <tipos_var>
    <tipo_parametro_funcion> ::=   <tipos_var> <identificador>
    <tipo_parametro_funcion > ::=  <tipos_var> <identificador> <separador_lista> <tipo_parametro_funcion>

    <dec_funcion> ::= <tipos_retorno_func> <identificador> <apertura_jeraquia> [ <tipo_parametro_func> ]? <cierre_jeraquia> <apertura_b_codigo> <bloque> [<retorno_valor> [ <tipos_asig_var> | <identificador> | <exp_arimetica_bin> | <exp_arimetica_una> | <función> | <exp_logica> | <exp_logica_una> ] <delimitador> ]?  <cierre_b_codigo>

    <parametros_funcion> ::=   [ <tipos_asig_var> | <identificador> | <exp_arimetica_bin> | <exp_arimetica_una> | <función> | <exp_logica> ]
    <parametros_funcion> ::=   [ <tipos_asig_var> | <exp_arimetica_bin> | <exp_arimetica_una> | <función> | <exp_logica> | <exp_logica_una> ] <separador_lista> <parametros_funcion>

    <función> ::=  <identificador> <apertura_jeraquia> [ <parametros_funcion> ]? <cierre_jeraquia>


### **Lectura y escritura**

- [x] Debe permitir las funciones de leer y escribir en la salida estándar (cadena carácter,
enteros y flotantes).

** ** 

    <leer> ::= <_input> <simbolo_imput> <identificador>
    <escribir> ::= <_output > <apertura_jeraquia>[ <tipos_asig_var> | <identificador> | <exp_arimetica_bin> | <exp_logica> <función> ] <cierre_jeraquia> 


### **Comentarios**

- [x] Además, debe permitir comentarios de una línea o múltiples líneas

** ** 

    <comentario> ::= <comentario_linea> <todos_caracteres>
    <cometario_bloque> ::= <apertura_b_comentario> <todos_caracteres> <cierre_b_comentario>



### **Simbolo inicial**

- [x] Debe definir un procedimiento inicial main, por medio de la cual se inicia la ejecución
de los programas

** ** 

    <main> ::= <int> <simbolo_inicial> <apertura_b_codigo> <bloque> return 0 <delimitador> <cierre_b_codigo>



