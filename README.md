# Expresiones-Regulares

## Regular Expresions

# (JS) Comprobar URL

~~~js

let url = /^(http|ftp|https)\:\/\/[a-z0-9\_-]+(\.[a-z0-9\_-]+)*(\:[0-9]{2,4})?$/;

document.write(url.test ('https://google.es:8080')+"<br/>"); //ok            

document.write(url.test ('ftp://ftp.com.es')+"<br/>"); //ok          

document.write(url.test ('file:///bin/bash')+"<br/>");  //fail            

document.write(url.test ('https://google.es/index.html')+"<br/>");//fail

~~~

# (JS) Validación de teléfono

~~~js

let telefono = /^[6789][0-9]{8}$/;

telefono.test ('123456789');  // fail

telefono.test ( '95566622');  // fail

telefono.test ('95566622a');  // fail

telefono.test ('609123456');  // ok

~~~

# (JS) Ejemplo de validación de código postal

~~~js

	let codigoPostal = /^[0-9]{4,5}$/;

	codigoPostal.test ( '14500');  // ok

	codigoPostal.test (  '9500');  // ok

	codigoPostal.test ('A11450');  // fail

	codigoPostal.test (     '1');  // fail

~~~

## (JS) Ejemplo comprobar email

~~~js

	let email = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

    	email.test ('j.amj2000@gmail.com');            // ok
    
    	email.test ('pepe_lopez@ventas.tienda.com');  // ok
    
    	email.test ('pepe#lopez@tienda.com');         // fail
    
    	email.test ('pepe_lopez@ventas/tienda.com');  // fail
    
~~~

# (JS) Contraseña segura

~~~js

^((?=(.*[\d0-9\@\&#\$\?\%!\|(){}[\]]){2,})(?=(.*[a-zA-Z]){2,}).{8,})$

~~~

Crea un programa que pida al usuario una propuesta de contraseña y compruebe si cumple con los siguientes requisitos.

Tiene entre 8 y 16 caracteres.

Tiene una letra mayúscula.

Tiene una letra minúscula.

Tiene un número.

Tiene uno de los siguientes valores: guión alto, guión bajo, arroba, almohadilla, dólar, tanto por ciento o ampersand.

Si cumple con todos los requisitos se considera una contraseña segura, de lo contrario mostrará que es una contraseña no segura.

~~~js

<script>

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

# (JS) Comprobar Matricula

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

## (JS) Matricula de 4 números seguido de una o varias letras en mayúscula

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

# Java

~~~java

import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Prueba {
	
    public static boolean comprobarEmail(String email){


        Pattern pattern = Pattern.compile("^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$", Pattern.CASE_INSENSITIVE);


        Matcher matcher = pattern.matcher(email);


        return matcher.find();


    }
	
	public static void main(String[] args) {
	
		String texto = "En un lugggar de La Mancha de cuyo nombre no quiero acordarme";
		
		String texto1 = "shdfklashfklshgksdlghañl.";
		
		String patron;

		patron = "mancha";
		
		busqueda(texto, patron);

		// cualquiera de las palabras
		patron = "lugar|ubicacion|sitio";
		busqueda(texto, patron);

		// una sola aparición
		patron = ".dos";
		busqueda(texto, patron);

		// empieza por
		patron = "^en";
		busqueda(texto, patron);

		// termina en
		patron = "rdarme$";
		busqueda(texto, patron);

		// contiene dígito
		patron = "\\d";
		busqueda(texto, patron);

		// contiene espacios
		patron = "\\s";
		busqueda(texto1, patron);

		// empieza por
		patron = "\\bnom";
		busqueda(texto, patron);

		// contine conjunto de caracteres
		patron = "[x-z]";
		busqueda(texto, patron);

		// contine digitos del conjunto
		patron = "[5-8]";
		busqueda(texto, patron);

		// contiene luggg
		patron = "lug{3}";
		busqueda(texto, patron);

		// password
		patron = "(?=.*[0-9])(?=.*[A-Z])(?=.*[a-z])(?=.*[@#%$&-]).{8,}";
		texto = "3Az&23dt";
		busquedaCase(texto, patron);

		// email
		patron = "^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$";
		texto = "test@gmail.com";
		busquedaCase(texto, patron);
	}

	public static void busqueda(String texto, String patron) {
		
		Pattern miPatron = Pattern.compile(patron, Pattern.CASE_INSENSITIVE);
		
		Matcher miMatcher = miPatron.matcher(texto);
		
		System.out.println("Búsqueda (" + patron + ")-> " + miMatcher.find());
	
	}

	public static void busquedaCase(String texto, String patron) {
	
		Pattern miPatron = Pattern.compile(patron);
		
		Matcher miMatcher = miPatron.matcher(texto);
		
		System.out.println("Búsqueda (" + patron + ")-> " + miMatcher.find());
	
	}

}
    
~~~
