# Trabajo Práctico – Active Directory 

## Parte 1 – Exploración inicial
1. Nombre del dominio:
```powershell
Get-ADDomain
```
2. OUs por defecto:
```powershell
Get-ADOrganizationalUnit -Filter *
```
3. Rol principal del DC:
   ```Centralizar autenticación y aplicación de políticas.```
## Parte 2 – Gestión de usuarios
4. Crear usuario:
```powershell
New-ADUser -Name "alumno1" -SamAccountName "alumno1" -AccountPassword (ConvertTo-SecureString "Alumno123!" -AsPlainText -Force) -Enabled $true
```
5. Obligar cambio de contraseña:
```powershell
Set-ADUser -Identity "alumno1" -ChangePasswordAtLogon $true
```
6. Crear grupo y agregar usuario:
```powershell
New-ADGroup -Name "Estudiantes" -SamAccountName "Estudiantes" -GroupCategory Security -GroupScope Global -Path "CN=Users,DC=escuela,DC=local"
Add-ADGroupMember -Identity "Estudiantes" -Members "alumno1"
```
## Parte 3 – Políticas y permisos
7. GPO = conjunto de configuraciones de seguridad y políticas.
8. Crear GPO y enlazar:
```powershell
New-GPO -Name "MensajeBienvenida"
New-GPLink -Name "MensajeBienvenida" -Target "DC=escuela,DC=local"
```
Ruta para configurar mensaje:
Configuración del equipo > Configuración de Windows > Configuración de seguridad > Políticas locales > Opciones de seguridad > Interactive logon: Message text...

9. Diferencia:
Dominio = afecta a todos.
OU = solo afecta a objetos dentro de esa unidad.

## Parte 4 – Administración avanzada
10. FSMO = roles únicos de AD. Ejemplos: Schema Master, RID Master, PDC Emulator.
Ver roles:
```powershell
netdom query fsmo
```
11. Listar usuarios:
```powershell
Get-ADUser -Filter * | Select SamAccountName, Name
```
12. Restablecer contraseña:
```powershell
Set-ADAccountPassword -Identity "alumno1" -Reset -NewPassword (ConvertTo-SecureString "NuevaPass123!" -AsPlainText -Force)
Unlock-ADAccount -Identity "alumno1"
```

## Parte 5 – Reflexión
13. Ventajas de AD: administración centralizada, seguridad, SSO, escalabilidad.
14. Riesgo de único DC: si falla, se pierde autenticación. Solución: tener al menos 2 DCs replicados.


# Tabla de comandos PowerShell en Active Directory 

| Comando PowerShell | ¿Qué hace? | Ejemplo de uso | ¿Cuándo lo usarías? |
|--------------------|------------|----------------|---------------------|
| Get-ADDomain       | Muestra información sobre el dominio actual (nombre, controladores, políticas, etc.) | `Get-ADDomain` | Para verificar el nombre del dominio y sus propiedades. |
| Get-ADOrganizationalUnit -Filter * | Lista todas las Unidades Organizativas (OUs) del dominio | `Get-ADOrganizationalUnit -Filter *` | Para conocer las OUs creadas y gestionar objetos dentro de ellas. |
| New-ADUser         | Crea un nuevo usuario en Active Directory | `New-ADUser -Name "Juan Perez" -SamAccountName "jperez" -AccountPassword (ConvertTo-SecureString "Clave123!" -AsPlainText -Force) -Enabled $true` | Cuando se incorpora un nuevo usuario a la organización. |
| Set-ADUser         | Modifica atributos de un usuario existente | `Set-ADUser -Identity "jperez" -ChangePasswordAtLogon $true` | Para forzar que un usuario cambie su contraseña en el próximo inicio de sesión. |
| Get-ADUser         | Obtiene información de uno o varios usuarios | `Get-ADUser -Filter * | Select Name, SamAccountName` | Para listar usuarios del dominio o verificar propiedades de uno en particular. |
| New-ADGroup        | Crea un grupo en Active Directory | `New-ADGroup -Name "Docentes" -GroupCategory Security -GroupScope Global -Path "CN=Users,DC=escuela,DC=local"` | Para organizar usuarios con permisos comunes (ej. docentes, alumnos). |
| Add-ADGroupMember  | Agrega usuarios u objetos a un grupo existente | `Add-ADGroupMember -Identity "Docentes" -Members "jperez"` | Cuando se debe asignar un usuario a un grupo con permisos específicos. |
| Get-ADGroupMember  | Muestra los miembros de un grupo | `Get-ADGroupMember "Docentes"` | Para verificar qué usuarios pertenecen a un grupo. |
| New-GPO            | Crea un nuevo objeto de política de grupo (GPO) | `New-GPO -Name "PoliticaSeguridad"` | Para definir una nueva política de seguridad en el dominio. |
| New-GPLink         | Enlaza una GPO a un dominio u OU | `New-GPLink -Name "PoliticaSeguridad" -Target "DC=escuela,DC=local"` | Para aplicar una GPO a todo el dominio o a una OU específica. |
| netdom query fsmo  | Muestra qué servidor posee los roles FSMO | `netdom query fsmo` | Para identificar los roles maestros de operación en el dominio. |
| Set-ADAccountPassword | Cambia o restablece la contraseña de un usuario | `Set-ADAccountPassword -Identity "jperez" -Reset -NewPassword (ConvertTo-SecureString "NuevaClave123!" -AsPlainText -Force)` | Cuando un usuario olvidó su contraseña. |
| Unlock-ADAccount   | Desbloquea una cuenta de usuario bloqueada | `Unlock-ADAccount -Identity "jperez"` | Cuando un usuario quedó bloqueado por intentos fallidos de inicio de sesión. |

