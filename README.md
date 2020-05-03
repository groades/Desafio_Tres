## Desaf�o 3: Complemento valores UF

**Autor:** 
- Gabriel Roades Cavalieri
- gabrielroades@gmail.com
- Head Hunter: Leonardo Miranda Pavez - Tech Consult - LinkedIn

**Importante:** El archivo "valores.json" resultante se escribe en la raiz del proyecto y tambi�n se retorna en la respuesta http del servicio, ambos al realizar la peticion http GET.

**Formato elegido para el resultado:** Formato 3 - JSON.

###Tecnolog�a y librer�as utilizadas

La implementaci�n de los requerimientos la constru� mediante web service API Rest con Spring boot y estructura MVC para organizar el c�digo en el IDE Eclipse Version: 2020-03 (4.15.0).

Constru� el proyecto con Spring Boot 2.2.6 y gradle como administrador de dependencias.

###Descripci�n de la implementaci�n

El proyecto contiene dos capas, en el controlador UFontroller se encuentra la implementaci�n del endpoint mediante el cual se realiza la petici�n http GET desde el cliente y retorna un ResponseEntity con un arreglo de byte (archivo), el http header y el http status 200 , en el controlador se inyecta la dependencia a la clase de la capa de servicios que implementa mediante interfaz UFService la funci�n getUfs en donde se realizan llamadas a las funciones con el algoritmo solicitado haciendo las consultas mediante la librer�a indicada Generador_Datos_Desafio_Tres-1.0.0.

Para complementar los valores UF faltantes, llam� al m�todo getUfs de la clase DatosUf con los par�metros de Fecha de inicio y fin que retorna el metodo getRango de la clase Valores. Se debe garantizar que estas fechas son consistentes.

En UfUtil implement� dos funciones est�ticos, dateFormat (recibe un Date y un patr�n, devuelve un String con el formato indicado en el patr�n) y valueFormat (recibe un valor Double, retorna un String con el formato indicado en la expresi�n regular de la constante VALUEREGEX).

En UFConstant declar� constantes para centralizar algunos valores reutilizables.

Cree dos POJOS UF y UFSResult para crear los objetos con los datos recibidos desde la librer�a y escribirlos en el archivo enviado al cliente. En al clase UF ademas de los setter and getter, agregu� un Comparator donde implement� la funci�n compare para aplicar un sort con la clase de tipo Collections a la lista de UFs por el atributo fecha (String con el formato yyyy-MM-dd).

UFSResult contiene un arreglo de UF.

###Detalles de compilaci�n y ejecuci�n

El proyecto compila y se ejecuta mediante el motor de eclipse para Java aplications. Una vez ejecutado, el servicio utiliza el puerto 8080 para las peticiones http y el endpoint en el contexto api/v1. 

Para consultar el servicio, recomiendo utilizar el cliente API llamado Postman. crear una coleci�n con la petici�n GET al endpoint localhost:8080/api/v1/uf/download estableciendo como encabezado el Content-Type: application/json. El resultado JSON se mostrar� en el cuerpo de la respuesta http y se podr� guardar el archivo valores.json usando la opcion de salvar respuesta como un archivo.

Desde un cliente Web implementado en cualquier lenguaje se podr�a descargar automaticamente el archivo json indicando el MIME application/octet-stream.

**En el c�digo fuente no debe incluirse comentarios, pero s�lo para este caso, escrib� algunos de los requerimientos indicando la ubicaci�n de la implementaci�n.**
 