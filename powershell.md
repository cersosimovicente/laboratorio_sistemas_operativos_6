# Ejercicios en PowerShell
## 1. Crea un script que reciba como parámetros Nombre, Apellido y Departamento, y cree un usuario en la OU Usuarios.
- Pensa qué cmdlet se usa para crear un usuario en AD.
- Necesitas construir el SamAccountName a partir del nombre y apellido.
- Recorda que las contraseñas deben estar en formato SecureString.

## 2. Prepara un archivo usuarios.csv con columnas Nombre,Apellido,Departamento y crea todos los usuarios de una sola vez.
- Usa Import-Csv para leer datos externos.
- Dentro de un foreach, repite el proceso de creación de usuario.
- El nombre de usuario puede generarse de forma parecida al ejercicio 1.


## 3. Lista los usuarios que no han iniciado sesión en los últimos 90 días.
## 4. Restaura la contraseña de todos los usuarios de un grupo a Temp2024! y fuerza cambio en el próximo logon.
## 5. Genera un reporte con nombre de usuario y sus grupos, y expórtalo a CSV.
## 6. Crea una OU llamada Pruebas y mueve allí todos los usuarios cuyo Departamento sea Testing.
## 7. Deshabilita automáticamente usuarios que no han iniciado sesión en 180 días.
