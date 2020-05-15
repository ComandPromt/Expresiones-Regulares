# Expresiones-Regulares

## Regular Expresions

# Comprobar URL

~~~js

let url = /^(http|ftp|https)\:\/\/[a-z0-9\_-]+(\.[a-z0-9\_-]+)*(\:[0-9]{2,4})?$/;

document.write(url.test ('https://google.es:8080')+"<br/>"); //ok            
document.write(url.test ('ftp://ftp.com.es')+"<br/>"); //ok          
document.write(url.test ('file:///bin/bash')+"<br/>");  //fail            
document.write(url.test ('https://google.es/index.html')+"<br/>");//fail

~~~

# Validación de teléfono

~~~js
let telefono = /^[6789][0-9]{8}$/;

telefono.test ('123456789');  // fail
telefono.test ( '95566622');  // fail
telefono.test ('95566622a');  // fail
telefono.test ('609123456');  // ok

~~~
# Ejemplo de validación de código postal

~~~js

let codigoPostal = /^[0-9]{4,5}$/;

codigoPostal.test ( '14500');  // ok
codigoPostal.test (  '9500');  // ok
codigoPostal.test ('A11450');  // fail
codigoPostal.test (     '1');  // fail

~~~

## Ejemplo comprobar email

~~~js
    let email = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;

    email.test ('j.amj2000@gmail.com');            // ok
    email.test ('pepe_lopez@ventas.tienda.com');  // ok
    email.test ('pepe#lopez@tienda.com');         // fail
    email.test ('pepe_lopez@ventas/tienda.com');  // fail
~~~

# Contraseña segura

Crea un programa que pida al usuario una propuesta de contraseña y compruebe si cumple con los siguientes requisitos.

Tiene entre 8 y 16 caracteres.

Tiene una letra mayúscula.

Tiene una letra minúscula.

Tiene un número.

Tiene uno de los siguientes valores: guión alto, guión bajo, arroba, almohadilla, dólar, tanto por ciento o ampersand.

Si cumple con todos los requisitos se considera una contraseña segura, de lo contrario mostrará que es una contraseña no segura.

~~~js
<script type="text/javascript">

var pass=prompt("Introduce la contraseña");

if(pass.length>8 && pass.length<16 && pass.match(/[A-Z]/g)
&& pass.match(/[a-z]/g)&& pass.match(/[0-9]/g)&&
pass.match(/[-||_||@||#||$||%||&]/g)){
	document.write("Contraseña segura");
}
else{
	document.write("Contraseña no segura");
}

</script>
~~~

# Comprobar Matricula

## Matricula de 5 números. El primer numero debe ser o 1,3,5,7 o 9 seguido de cuatro numeros y la letra P ó la S

~~~js
  <script>
        function comprobar_matricula(matricula){
        
          var patron=/^[1|3|5|7|9]{1}[0-9]{4}[P|S]{1}$/;
          
          if(matricula.match(new RegExp(patron))){
            document.write("Matrícula válida<hr/>");
          }
          
          else{
            document.write("Matrícula inválida<hr/>");
          }
          
        }
        
        comprobar_matricula("12345P"); // ok
        
        comprobar_matricula("12345S"); // ok
        
        comprobar_matricula("123455P"); // fail
        
        comprobar_matricula("123455A"); // fail
        
   </script>
~~~

## Matricula de 4 números seguido de una o varias letras en mayúscula

~~~js

<script>

    function comprobar_matricula(matricula){
    
        var patron=/^[0-9]{4}[A-Z]/;

        if(patron.test(matricula)){
            document.write("Matrícula válida<hr/>");
        }
        
        else{
            document.write("Matrícula inválida<hr/>");
        }
     }
     
    comprobar_matricula('1455ADB'); //ok
    
		comprobar_matricula('1455A'); //ok
    
		comprobar_matricula('14B'); //fail
    
</script>
~~~
