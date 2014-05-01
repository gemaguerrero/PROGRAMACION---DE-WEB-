PROGRAMACION---DE-WEB-
======================
+HOLA-MUNDO
 +==========
 Desarrolle los siguientes ejercicios solo utilizando HTML5 y JavaScript:
 °Valide sin utilizar expresiones regulares que se ingrese correctamente en un input tipo texto lo siguiente
 °Solo números primos
 °Solo valores hexadecimales
 °Número de cedula correcto
 °Crear las siguientes funciones que reciban 2 parámetros 
 °Suma de parámetros siendo estos números binarios
 °Invertir texto del segundo parámetro encontrado en el  primero
 °Desarrollar totalmente en JavaScript una factura con los siguientes requerimientos: 
 °Ubicar los productos en un arreglo y permitir una búsqueda por índice desde la factura
 °Ubicar los clientes en un arreglo y permitir una búsqueda por índice desde la factura
 °Permitir ingresar N productos a la factura de manera dinámica
 °Sistemáticamente debe ir acumulando la suma de los productos, así como el IVA y el descuento al final de la factura


EJERCICIO 1


<!DOCTYPE html>

<html>
    <head>
        <title>TODO supply a title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function numPrimos() {
                var dato = document.getElementById("numero1").value;
                var divisoresEncontrados = 0;
                for (i = 0; i <= dato; i++) {
                    var residuo = dato % i;
                    if (residuo == 0) {
                        divisoresEncontrados++;
                    }
                }
                if (divisoresEncontrados == 2 || dato == 1) {
                    
                    document.getElementById("resultado").innerHTML = "Primo";
                } else {
                  document.getElementById("numero1").value= "";
                  document.getElementById("resultado").innerHTML = "No Primo";
                }
            }
        </script>
    </head>
    <body>
        <h3>Primos...</h3>
        <label for="numero1" >Ingrese un número:</label>
        <input type="text" name="numero1" id="numero1" />
        <input type="button" name="ok" value="ok" onclick="numPrimos()" id="ok"/>
        <p id="resultado" >Resultado...</p>

    </body>
</html>




EJERCICIO 2

NUMERO DE CEDULA

<!DOCTYPE html>

<html>
    <head>
        <title>Validar Cedula</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function verificarCedula()
            {
                var cedula = document.getElementById("cedulaIngresada").value;
                array = cedula.split("");
                num = array.length;
                if (num == 10)
                {
                    total = 0;
                    digito = (array[9] * 1);
                    for (i = 0; i < (num - 1); i++)
                    {
                        mult = 0;
                        if ((i % 2) != 0) {
                            total = total + (array[i] * 1);
                        }
                        else
                        {
                            mult = array[i] * 2;
                            if (mult > 9)
                                total = total + (mult - 9);
                            else
                                total = total + mult;
                        }
                    }
                    decena = total / 10;
                    decena = Math.floor(decena);
                    decena = (decena + 1) * 10;
                    final = (decena - total);
                    if ((final == 10 && digito == 0) || (final == digito)) {
                        alert("Cedula Valida");
                        return true;
                    }
                    else
                    {
                        alert("Cedula NO Valida");
                        return false;
                    }
                }
                else
                {
                    alert("La cedua no puede tener menos de 10 digitos");
                    return false;
                }
            }
        </script>
    </head>
    <body>
        <label>Ingresar el numero de cedula:</label>
        <input type="text" id="cedulaIngresada"  />
        <input type="button" id="ok" value="ok" onclick="verificarCedula()"/>
    </body>
</html>




EJERCICIO 3

SOLO VALORES HEXADECIMALES


<!DOCTYPE html>

<html>
    <head>
        <title>Gema</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function validarHexadecimal() {
                var dato = document.getElementById('hexadecimalIngresado').value;
                var letras = dato.split("");
                for (i = 0; i < letras.length; i++) {
                    if ((letras[i] != 1) && (letras[i] != 2)&&(letras[i] != 3) && (letras[i] != 4)&&(letras[i] != 5)&&
                        (letras[i] != 6) && (letras[i] != 7)&&(letras[i] != 8) && (letras[i] != 9)&&(letras[i] != "A")&&    
                        (letras[i] != "B") && (letras[i] != "C")&&(letras[i] != "D") && (letras[i] != "Ë")&&(letras[i] != "F")  
                    ) {
                        alert('No Valido');
                    }
                }
            }
        </script>
    </head>
    <body>
        <label>Ingresar un valor hexadecimal:</label>
        <input type="text" id="hexadecimalIngresado"/>
        <input type="button" id="ok" value="ok" onclick="validarHexadecimal()"/>
    </body>
</html>



EJERCICIO 4

INVERTIR TEXTO DEL SEGUNDO PARAMETRO ENCONTRADO EN EL PRIMERO

<!DOCTYPE html>

<html>
    <head>
        <title>Gema</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function sumaDeBinarios(fraseRecivida, palabraRecivida) {
                var palabras = fraseRecivida.split(" ");
                for (i = 0; i < palabras.length; i++) {
                    if (palabras[i] == palabraRecivida) {
                        alert(invertir(palabras[i]));
                    }
                }
            }
            function invertir(cadena) {
                var x = cadena.length;
                var cadenaInvertida = "";
                while (x >= 0) {
                    cadenaInvertida = cadenaInvertida + cadena.charAt(x);
                    x--;
                }
                return cadenaInvertida;
            }

        </script>
    </head>
    <body>
        <label>Frase:</label>
        <input type="text" id="frase"/>
        <label>Palabra a invertir:</label>
        <input type="text" id="palabra"/>
        <input type="button" id="invertir" value="invertir" onclick="sumaDeBinarios(document.getElementById('frase').value, document.getElementById('palabra').value)"/>
        <br>
        Ejemplo: <br>
        Frase : Hola mundo <br>
        Palabra: mundo<br>
        Resultado: odnum 
    </body>
</html>



EJERCICIO 5

SOLO NUMEROS PRIMOS

<!DOCTYPE html>

<html>
    <head>
        <title>TODO supply a title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function numPrimos() {
                var dato = document.getElementById("numero1").value;
                var divisoresEncontrados = 0;
                for (i = 0; i <= dato; i++) {
                    var residuo = dato % i;
                    if (residuo == 0) {
                        divisoresEncontrados++;
                    }
                }
                if (divisoresEncontrados == 2 || dato == 1) {
                    
                    document.getElementById("resultado").innerHTML = "Primo";
                } else {
                  document.getElementById("numero1").value= "";
                  document.getElementById("resultado").innerHTML = "No Primo";
                }
            }
        </script>
    </head>
    <body>
        <h3>Primos...</h3>
        <label for="numero1" >Ingrese un número:</label>
        <input type="text" name="numero1" id="numero1" />
        <input type="button" name="ok" value="ok" onclick="numPrimos()" id="ok"/>
        <p id="resultado" >Resultado...</p>

    </body>
</html>


EJERCICIO 6
FACTURA

CREAR LAS SIGUIENTES FUNCIONES QUE RECIBAN 2 PARAMETROS
SUMA DE PARAMETROS SIENDO ESTOS NUMEROS BINARIOS

<!DOCTYPE html>

<html>
    <head>
        <title>Gema</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function sumaDeBinarios(bUno, bDos) {
                var primeroEnDecimal = parseInt(bUno, 2);
                var segundoEnDecimal = parseInt(bDos, 2);
                var sumaDecimal = primeroEnDecimal + segundoEnDecimal;
                var sumaBinario = deciToBin(sumaDecimal);
                alert('Resultado en decimal: ' + sumaDecimal + 'Resultado en Binario: ' + sumaBinario);
            }

            function deciToBin(arg)
            {
                res1 = 999;
                args = arg;
                while (args > 1)
                {
                    arg1 = parseInt(args / 2);
                    arg2 = args % 2;
                    args = arg1;
                    if (res1 == 999)
                    {
                        res1 = arg2.toString();
                    }
                    else
                    {
                        res1 = arg2.toString() + res1.toString();
                    }
                }
                if (args == 1 && res1 != 999)
                {
                    res1 = args.toString() + res1.toString();
                }
                else if (args == 0 && res1 == 999)
                {
                    res1 = 0;
                }
                else if (res1 == 999)
                {
                    res1 = 1;
                }
                var ll = res1.length;
                while (ll % 4 != 0)
                {
                    res1 = "0" + res1;
                    ll = res1.length;
                }
                return res1;
            }
        </script>
    </head>
    <body>
        <label>Ingresar un binario:</label>
        <input type="text" id="binarioUno"/>
        <label>Ingresar otro binario:</label>
        <input type="text" id="binarioDos"/>
        <input type="button" id="Sumar" value="Sumar" onclick="sumaDeBinarios(document.getElementById('binarioUno').value, document.getElementById('binarioDos').value)"/>
    </body>
</html>




EJERCICIO 7

FACTURA

Desarrollar totalmente en JavaScript una factura con los siguientes requerimientos: 
 °Ubicar los productos en un arreglo y permitir una búsqueda por índice desde la factura
 °Ubicar los clientes en un arreglo y permitir una búsqueda por índice desde la factura
 °Permitir ingresar N productos a la factura de manera dinámica
 °Sistemáticamente debe ir acumulando la suma de los productos, así como el IVA y el descuento al final de la factura

<!DOCTYPE html>

<html>
    <head>
        <title>TODO supply a title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script>
            function datos() {
                var clientes = ["Gema", "Luiggi", "Pedro", "Evelin"];
                var productos = ["Arroz", "Azucar", "Leche", "Manteca"];
                var listaClientesDatos = document.getElementById('listaClientes');
                for (var i = 0; i < clientes.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = clientes[i];
                    opt.value = clientes[i];
                    listaClientesDatos.appendChild(opt);
                }
                var listaProductosDatos = document.getElementById('listaProducto');
                for (var i = 0; i < productos.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = productos[i];
                    opt.value = productos[i];
                    listaProductosDatos.appendChild(opt);
                }

            }
            function total() {
                var unitario = document.getElementById('precioUnit').value;
                var cantidad = document.getElementById('cantidad').value;
                var total = parseFloat(unitario) * parseFloat(cantidad);
                document.getElementById('total').value = total;
            }
            function crearFilaProductoIngresado() {
                var subtotal = document.getElementById('subtotal').value;
                document.getElementById('subtotal').value = parseFloat(subtotal) + parseFloat(document.getElementById('total').value);
                var subtotalNuevo = document.getElementById('subtotal').value;
                document.getElementById('iva').value = parseFloat(subtotalNuevo) * 0.12;
                var ivaNuevo = document.getElementById('iva').value;
                document.getElementById('descuento').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) * 0.05;
                var descuentoNuevo = document.getElementById('descuento').value;
                document.getElementById('totalFinal').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) - parseFloat(descuentoNuevo);
                capotTexto = document.createElement('input');
                capotTexto.type = "text";
                capotTexto.name = "producto";
                capotTexto.id = "produc";
                capotTexto.value = document.getElementById('listaProducto').value + '     -     ' + document.getElementById('precioUnit').value + '     -     ' + document.getElementById('cantidad').value + '     -     ' + document.getElementById('total').value;
                capotTexto.size = "50";
                document.getElementById('contenido').appendChild(capotTexto);
                salto = document.createElement('br');
                document.getElementById('contenido').appendChild(salto);
            }

        </script>
    </head>
    <body onload="datos()">
        Escoja cliente: <select id="listaClientes"></select><br>
        <hr>
        Producto:  <select id="listaProducto"></select>
        Precio Unitario: <input type="text" id="precioUnit" />
        Cantidad: <input type="text" id="cantidad" onchange="total()"/>

        Total: <input type="text" id="total"/>
        <input type="button" id="agregar" value="Agregar" onclick="crearFilaProductoIngresado()"/><br>
        <hr><hr>

        Resumen de compra: <br>
        Producto - Precio - Cantidad - Total
        <div id="contenido">

        </div>
        <hr>
        Subtotal : <input type="text" id="subtotal" value="0"/>
        IVA 12%: <input type="text" id="iva"/>
        Descuento 5%: <input type="text" id="descuento"/>
        Total Final: <input type="text" id="totalFinal"/>
    </body>
</html>
 ATT GEMA GUERRERO
